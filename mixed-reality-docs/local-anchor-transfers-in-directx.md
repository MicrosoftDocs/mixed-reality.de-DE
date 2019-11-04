---
title: Lokale Anker Übertragungen in DirectX
description: Erläutert das Synchronisieren von zwei hololens-Geräten durch die Übertragung räumlicher Anker.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, synchronisieren, räumlicher Anker, Übertragung, Multiplayer, Ansicht, Szenario, Exemplarische Vorgehensweise, Beispielcode, Übertragung, lokale Anker Übertragung, Anker Export, Anker Import
ms.openlocfilehash: f961862c3c49872484683e264fb9c62b5d0b60ee
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437958"
---
# <a name="local-anchor-transfers-in-directx"></a>Lokale Anker Übertragungen in DirectX

In Fällen, in denen Sie keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumlichen Anker von Azure</a>verwenden können, ermöglichen lokale Anker Übertragungen einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.

>[!NOTE]
>Lokale Anker Übertragungen bieten weniger robusten Anker als Anker als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumliche Azure-Anker</a>, und IOS-und Android-Geräte werden von diesem Ansatz nicht unterstützt.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

## <a name="transferring-spatial-anchors"></a>Übertragen räumlicher Anker

Räumliche Anker können mithilfe von [spatialanchortransfermanager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)zwischen Windows Mixed Reality-Geräten übertragen werden. Mit dieser API können Sie einen Anker mit allen unterstützenden Sensordaten bündeln, die erforderlich sind, um den genauen Ort auf der Welt zu finden und dann dieses Paket auf ein anderes Gerät zu importieren. Nachdem die APP auf dem zweiten Gerät diesen Anker importiert hat, kann jede APP Hologramme mithilfe des Koordinatensystems des freigegebenen räumlichen Ankers Rendering erzeugen, das dann an derselben Stelle in der realen Welt angezeigt wird.

Beachten Sie, dass räumliche Anker nicht zwischen verschiedenen Gerätetypen übertragen werden können, z. b. kann ein räumlicher hololens-Anker nicht mithilfe eines immersiven Headsets verwendet werden.  Übertragene Anker sind ebenfalls nicht mit IOS-oder Android-Geräten kompatibel.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Einrichten Ihrer APP für die Verwendung der spatialperception-Funktion

Ihrer APP muss die Berechtigung zum Verwenden der spatialperception-Funktion erteilt werden, bevor Sie den [spatialanchortransfermanager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)verwenden kann. Dies ist erforderlich, da das übertragen eines räumlichen Ankers das Freigeben von Sensor Bildern im Laufe der Zeit in der Nähe dieses Ankers beinhaltet, die vertrauliche Informationen enthalten können.

Deklarieren Sie diese Funktion in der Datei "Package. appxmanifest" für Ihre APP. Beispiel:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Die Funktion stammt aus dem **uap2** -Namespace. Um Zugriff auf diesen Namespace in ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns* -Attribut in das &lt;Package >-Elements ein. Beispiel:

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**Hinweis:** Ihre APP muss die Funktion zur Laufzeit anfordern, bevor Sie auf die APIs für den Zugriff auf spatialanchor exportieren/importieren zugreifen kann. Weitere Informationen finden Sie in den folgenden Beispielen unter [requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) .

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serialisieren von Anker Daten durch Exportieren mit spatialanchortransfermanager

Eine Hilfsfunktion ist im Codebeispiel zum Exportieren (Serialisieren) der [spatialanchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) -Daten enthalten. Diese Export-API serialisiert alle Anker in einer Auflistung von Schlüssel-Wert-Paaren, die Zeichen folgen mit Ankern zuordnen.

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

Zuerst müssen wir den Datenstream einrichten. Dies ermöglicht uns 1.) Verwenden Sie tryexportanchorsasync, um die Daten in einem Puffer zu platzieren, der der APP gehört, und 2.) Lesen von Daten aus dem exportierten Byte-Puffer Datenstrom, bei dem es sich um einen WinRT-Datenstrom handelt, in unseren eigenen Speicherpuffer, bei dem es sich um eine Std:: Vector-&lt;> Byte

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Wir müssen die Berechtigung für den Zugriff auf räumliche Daten, einschließlich Anker, die vom System exportiert werden, anfordern.

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

Wenn wir die Get-Berechtigung erhalten und Anker exportiert werden, können wir den Datenstrom lesen. Hier erfahren Sie auch, wie Sie den DataReader und den InputStream erstellen, die zum Lesen der Daten verwendet werden.

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

Nachdem wir Bytes aus dem Stream gelesen haben, können wir diese wie folgt in unserem eigenen Datenpuffer speichern.

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserialisieren von Anker Daten durch Importieren in das System mithilfe von spatialanchortransfermanager

Eine Hilfsfunktion ist im Codebeispiel enthalten, um zuvor exportierte Daten zu laden. Diese deserialisierungssoftware stellt eine Auflistung von Schlüssel-Wert-Paaren bereit, ähnlich wie im spatialanchorstore, mit dem Unterschied, dass diese Daten aus einer anderen Quelle, z. b. einem Netzwerk Socket, erhalten wurden. Sie können diese Daten vor der Offline Speicherung, bei Verwendung von in-App-Arbeitsspeicher oder (falls zutreffend) in den spatialanchorstore Ihrer APP verarbeiten.

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

Zuerst müssen wir Streamobjekte erstellen, um auf die Anker Daten zuzugreifen. Wir werden die Daten aus dem Puffer in einen System Puffer schreiben. Daher erstellen wir einen DataWriter, der in einen Datenstrom im Arbeitsspeicher schreibt, um das Ziel zu erreichen, die Anker von einem Byte Puffer in das System als spatialanchor zu bringen.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Auch hier müssen wir sicherstellen, dass die APP über die Berechtigung zum Exportieren räumlicher Anker Daten verfügt. Dies kann private Informationen über die Benutzerumgebung beinhalten.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Wenn der Zugriff zulässig ist, können wir Bytes aus dem Puffer in einen Systemdaten Strom schreiben.

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

Wenn die Speicherung von Bytes im Datenstrom erfolgreich war, können Sie versuchen, diese Daten mit dem spatialanchortransfermanager zu importieren.

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

Wenn die Daten importiert werden können, erhalten Sie eine Kartenansicht von Schlüssel-Wert-Paaren, die Zeichen folgen mit Ankern zuordnen. Wir können dies in unsere eigene in-Memory-Datensammlung laden und diese Sammlung verwenden, um nach Anker zu suchen, die wir verwenden möchten.

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**Hinweis:** Nur weil Sie einen Anker importieren können, bedeutet nicht notwendigerweise, dass Sie ihn sofort verwenden können. Der Anker befindet sich möglicherweise in einem anderen Raum oder an einem anderen physischen Standort. der Anker kann erst nach dem Gerät, das es empfangen hat, genug visuelle Informationen über die Umgebung haben, in der der Anker erstellt wurde, um die Position des Ankers relativ zur bekannten aktuellen Umgebung wiederherzustellen. Die Client Implementierung sollte versuchen, den Anker relativ zum lokalen Koordinatensystem oder Referenzrahmen zu finden, bevor Sie mit dem Versuch fortfahren, ihn für Live-Inhalte zu verwenden. Versuchen Sie z. b., den Anker in regelmäßigen Abständen relativ zu einem aktuellen Koordinatensystem zu suchen, bis der Anker als zu verwendbar festgelegt ist.

## <a name="special-considerations"></a>Besondere Überlegungen

Die [tryexportanchorsasync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) -API ermöglicht das Exportieren mehrerer [spatialanchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) -Werte in dasselbe nicht transparente binäre Blob. Es gibt jedoch einen geringfügigen Unterschied, welche Daten das BLOB enthält, abhängig davon, ob ein einzelner spatialanchor oder mehrere spatialanchor-Elemente in einem einzelnen-Befehl exportiert werden.

### <a name="export-of-a-single-spatialanchor"></a>Exportieren eines einzelnen spatialanchor

Das BLOB enthält eine Darstellung der Umgebung in der Nähe des spatialanchors, sodass die Umgebung auf dem Gerät erkannt werden kann, das den spatialanchor importiert. Nachdem der Import abgeschlossen wurde, ist der neue spatialanchor für das Gerät verfügbar. Vorausgesetzt, dass sich der Benutzer vor kurzem in der Nähe des Ankers befand, ist er möglich und kann gerendert werden. Diese Hologramme werden am gleichen physischen Speicherort angezeigt, den Sie auf dem ursprünglichen Gerät erstellt haben, das den spatialanchor exportiert hat.

![Exportieren eines einzelnen spatialanchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Exportieren von mehreren spatialanchor-

Wie beim Export eines einzelnen spatialanchor enthält das BLOB eine Darstellung der Umgebung in der Nähe aller angegebenen spatialanchor. Außerdem enthält das BLOB Informationen zu den Verbindungen zwischen den enthaltenen spatialanchor-Daten, wenn Sie sich im gleichen physischen Raum befinden. Dies bedeutet, dass, wenn zwei in der Nähe gelegene räumliche Anker importiert werden, ein – Hologramm, das an den *zweiten* spatialanchor angefügt ist, auch dann einstellbar ist, wenn das Gerät nur die Umgebung um den *ersten* spatialanchor erkennt, weil genügend Daten für Die COMPUTE-Transformation zwischen den beiden spatialanchor-Einheiten war im BLOB enthalten. Wenn die beiden spatialanchor einzeln exportiert wurden (zwei separate Aufrufe von tryexportspatialanchor), sind möglicherweise nicht genügend Daten im BLOB für holograms enthalten, die an den zweiten spatialanchor angefügt sind, damit Sie bei der ersten gefunden werden können.

![Mehrere Anker werden mithilfe eines einzelnen tryexportanchorsasync-Aufrufes exportiert.](images/multipleanchors.png) ![Mehrere Anker, die mithilfe eines separaten tryexportanchorsasync-Aufrufes für jeden Anker exportiert wurden.](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Beispiel: Senden von Anker Daten mithilfe von Windows:: Networking:: Streamsocket

Hier geben wir ein Beispiel für die Verwendung von exportierten Anker Daten an, indem Sie Sie über ein TCP-Netzwerk senden. Dies erfolgt aus dem holographicspatialanchortransfersample.

Die WinRT-Streamsocket-Klasse verwendet die ppl-Aufgaben Bibliothek. Im Fall von Netzwerkfehlern wird der Fehler an die nächste Aufgabe in der Kette zurückgegeben, wobei eine Ausnahme erneut ausgelöst wird. Die Ausnahme enthält ein HRESULT, das den Fehlerstatus angibt.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Verwenden eines Windows:: Networking:: streamsocketlistener mit TCP zum Senden von exportierten Anker Daten

Erstellen Sie eine Serverinstanz, die auf eine Verbindung lauscht.

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

Wenn eine Verbindung empfangen wird, verwenden Sie die Clientsocket-Verbindung, um Anker Daten zu senden.

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

Nun können wir beginnen, einen Datenstrom zu senden, der die exportierten Anker Daten enthält.

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

Bevor wir den Datenstrom selbst senden können, müssen wir zuerst ein Header Paket senden. Dieses Header Paket muss eine festgelegte Länge aufweisen, und es muss auch die Länge des Variablen Arrays von Bytes angeben, das der Anker Datenstrom ist. im Fall dieses Beispiels sind keine anderen Header Daten zum Senden vorhanden, daher ist der Header 4 Bytes lang und enthält eine 32-Bit-Ganzzahl ohne Vorzeichen.

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

Nachdem die Streamlänge in Bytes an den Client gesendet wurde, können wir mit dem Schreiben des Datenstroms selbst in den socketstream fortfahren. Dies bewirkt, dass die Anker Speicher Bytes an den Client gesendet werden.

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

Wie bereits weiter oben in diesem Thema erwähnt, müssen wir auf die Behandlung von Ausnahmen vorbereitet sein, die Netzwerkfehler Statusmeldungen enthalten. Bei nicht erwarteten Fehlern können wir die Ausnahme Informationen wie folgt in die Debugkonsole schreiben. Dadurch erhalten Sie einen Anhaltspunkt, was passiert, wenn das Codebeispiel die Verbindung nicht abschließen kann, oder wenn das Senden der Anker Daten nicht abgeschlossen werden kann.

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Verwenden Sie Windows:: Networking:: Streamsocket mit TCP, um exportierte Anker Daten zu empfangen.

Zuerst müssen wir eine Verbindung mit dem Server herstellen. Dieses Codebeispiel veranschaulicht das Erstellen und Konfigurieren eines Streamsockets und das Erstellen eines DataReader, den Sie zum Abrufen von Netzwerkdaten mithilfe der Socketverbindung verwenden können.

**Hinweis:** Wenn Sie diesen Beispielcode ausführen, stellen Sie sicher, dass Sie den Server konfigurieren und starten, bevor Sie den Client starten.

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

Nachdem eine Verbindung hergestellt wurde, können wir warten, bis der Serverdaten sendet. Dies geschieht durch Aufrufen von LoadAsync für den Daten Leser des Datenstroms.

Der erste Satz von Bytes, den wir empfangen, sollte immer das Header Paket sein, das die Byte Länge des Anker Datenstroms angibt, wie im vorherigen Abschnitt beschrieben.

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

Nachdem wir das Header Paket erhalten haben, wissen wir, wie viele Bytes an Anker Daten erwartet werden. Wir können fortfahren, um die Bytes aus dem Stream zu lesen.

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

Hier ist unser Code zum Empfangen des Anker Datenstroms. Die Bytes werden zuerst aus dem Datenstrom geladen. Dieser Vorgang kann einige Zeit in Anspruch nehmen, da der Streamsocket darauf wartet, diese Menge von Bytes aus dem Netzwerk zu empfangen.

Nachdem der Ladevorgang beendet wurde, können wir diese Anzahl von Bytes lesen. Wenn wir die Anzahl der Bytes erhalten haben, die für den Anker Datenstrom erwartet werden, können wir die Anker Daten importieren. Wenn dies nicht der Fall ist, muss ein Fehler aufgetreten sein. Dies kann z. b. der Fall sein, wenn die Serverinstanz beendet wird, bevor Sie das Senden des Datenstroms abschließen kann, oder wenn das Netzwerk ausfällt, bevor der gesamte Datenstrom vom Client empfangen werden kann.

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

Auch hier müssen wir darauf vorbereitet sein, unbekannte Netzwerkfehler zu behandeln.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Das war's. Nun sollten Sie über genügend Informationen verfügen, um zu versuchen, die Anker zu suchen, die über das Netzwerk empfangen werden. Beachten Sie, dass der Client über ausreichend visuelle Überwachungsdaten verfügen muss, damit der-Platz gefunden werden kann. Wenn es nicht sofort funktioniert, versuchen Sie es für eine Weile. Wenn dies immer noch nicht funktioniert, lassen Sie den Server weitere Anker senden, und verwenden Sie die Netzwerkkommunikation, um eine Zustimmung für den Client zu erhalten. Sie können dies ausprobieren, indem Sie das holographicspatialanchortransfersample herunterladen, die Client-und Server-IPS konfigurieren und Sie auf Client-und Server-hololens-Geräten bereitstellen.

## <a name="see-also"></a>Weitere Informationen:
* [Parallel Patterns Library (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows. Networking. Streamsocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows. Networking. streamsocketlistener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
