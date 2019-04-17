---
title: Lokale Anchor-Übertragungen in DirectX
description: Erläutert, wie zwei HoloLens-Geräte zu synchronisieren, durch die Übertragung von räumlichen Anker.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, zu synchronisieren, räumliche Anker, Übertragung, Multiplayer-Spiele, anzuzeigen, Szenario, exemplarische Vorgehensweise, Beispielcode, Übertragung, lokalen Anchor-Übertragung, Anchor-Export, Anker importieren
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605065"
---
# <a name="local-anchor-transfers-in-directx"></a>Lokale Anchor-Übertragungen in DirectX

In Situationen, in dem können keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, die Übertragung von lokalen Anker ermöglichen ein HoloLens-Gerät so exportieren Sie einen Anker, die durch ein zweites Gerät mit HoloLens importiert werden.

>[!NOTE]
>Lokale Anker Übertragungen bieten weniger stabil Anchor-Rückruf als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, und IOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="transferring-spatial-anchors"></a>Räumliche Anker übertragen

Sie können räumliche Anker übertragen, zwischen Windows Mixed Reality-Geräte mithilfe der [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Dieser API können Sie bei der paketerstellung eines Ankers alle unterstützenden Sensordaten, die erforderlich sind, genau zu der Stelle in der ganzen Welt zu finden, und importieren Sie dieses Paket auf einem anderen Gerät. Sobald die app auf dem zweiten Gerät diese Anker importiert hat, kann jede app mit Hologramme rendern, die räumliche Anker das Koordinatensystem, gemeinsam genutzt, die dann in der Praxis am gleichen Ort angezeigt wird.

Beachten Sie, dass räumliche Anker können nicht zwischen verschiedenen Gerätetypen zu übertragen, z. B. ein räumlicher HoloLens-Anker möglicherweise nicht auffindbaren eine immersive Kopfhörer verwenden.  Übertragene verankert sind auch nicht kompatibel mit iOS oder Android-Geräte.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Richten Sie Ihre app, um die SpatialPerception-Funktion verwenden

Ihre app Berechtigung erteilt werden, um die SpatialPerception-Funktion verwenden, bevor er verwendet werden kann die [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Dies ist erforderlich, da einen räumlichen Anker übertragen umfasst Freigabe Sensor-Images, die im Laufe der Zeit gesammelt werden, in der Nähe des, Anker, d. h. die vertraulichen Informationen enthalten sein.

Deklarieren Sie diese Funktion wird in der Datei "Package.appxmanifest" für Ihre app ein. Im Folgenden ein Beispiel:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Die Funktion stammt aus dem **uap2** Namespace. Um Zugriff auf diesen Namespace in Ihrem Manifest zu erhalten, fügen Sie ihn als einen *Xlmns* -Attribut in der &lt;Paket > Element. Im Folgenden ein Beispiel:

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**HINWEIS:** Ihre app benötigt die Funktion zur Laufzeit anfordern, bevor es SpatialAnchor Import-/APIs zugreifen kann. Finden Sie unter ["requestaccessasync"](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in den folgenden Beispielen.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serialisieren von Anchor-Daten durch einen Export mit dem SpatialAnchorTransferManager

Befindet sich eine Hilfsfunktion im Codebeispiel exportieren (serialisieren) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) Daten. Diese API Export serialisiert alle Anker in eine Auflistung von Schlüssel-Wert-Paaren, die Anker Zeichenfolgen zugeordnet.

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

Zunächst müssen wir den Datenstrom einrichten. Uns dadurch 1.) Verwenden Sie TryExportAnchorsAsync versetzen Sie die Daten in einem Puffer im Besitz der app und 2.) Lesen von Daten aus der exportierten Puffer Bytestream - handelt es sich einen Datenstrom von WinRT - in unserer eigenen Speicherpuffers, d.h. eine Std:: vector&lt;Byte >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Wir bitten Sie die Berechtigung zum Zugriff auf räumliche Daten, einschließlich der Anker, die vom System exportiert werden müssen.

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

Wenn wir Berechtigung erhalte und Anker exportiert werden, können wir den Datenstream lesen. Hier zeigen wir Ihnen außerdem das Erstellen der DataReader und InputStream, die wir zum Lesen der Daten verwenden.

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

Nachdem wir Bytes aus dem Stream gelesen haben, können wir sie auf unserer eigenen Datenpuffer speichern wie folgt.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserialisieren von Anchor-Daten durch Importieren in das System mithilfe der SpatialAnchorTransferManager

Eine Hilfsfunktion ist im Codebeispiel zum Laden von zuvor exportierter Daten enthalten. Diese Funktion für die Deserialisierung stellt eine Auflistung von Schlüssel-Wert-Paare ähnelt, was die SpatialAnchorStore bietet - bereit, mit der Ausnahme, dass wir diese Daten aus einer anderen Quelle, z. B. ein Netzwerksocket haben. Sie verarbeiten können und diese Daten vor dem Speichern offline, mit in-app-Speicher, oder (falls zutreffend) Ihrer app SpatialAnchorStore.

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

Zunächst müssen wir Streamobjekte für den Zugriff auf die Anker-Daten zu erstellen. Wird schreiben wir werden die Daten aus unsere Puffer in einen Systempuffer, damit wir eine DataWriter, die in ein in-Memory-Datenstrom zu schreiben erstellen, um die erste der Anker aus einem Bytepuffer in das System als SpatialAnchors unser Ziel zu erreichen.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Auch hier müssen wir sicherstellen, dass die app verfügt über die Berechtigung zum Anker der räumlichen Daten, exportieren, die private Informationen über die Umgebung des Benutzers enthalten, werden.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Wenn der Zugriff zugelassen wird, können wir Bytes aus dem Puffer in einen Datenstream System schreiben.

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

Wenn es sich im Speichern der Bytes in den Datenstrom erfolgreich ausgeführt wurden, können wir versuchen zum Importieren von Daten unter Verwendung der SpatialAnchorTransferManager.

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

Wenn die Daten importiert werden können, erhalten wir eine Kartenansicht für Schlüssel-Wert-Paare, die Anker Zeichenfolgen zugeordnet. Wir können laden das in unseren in-Memory-Daten-Auflistung, und verwenden diese Sammlung Anker gesucht werden soll, wir verwenden möchten.

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

**HINWEIS:** Nur weil Sie einen Anker importieren können, bedeutet nicht unbedingt, dass Sie es sofort verwenden können. Der Anker möglicherweise vollständig in einen anderen Raum oder einen anderen physischen Speicherort; der Anker nicht gefunden werden, bis das Gerät, das sie empfangen über ausreichende visual Informationen über die Umgebung verfügt, die der Anker des Ankers Position relativ zu der bekannten aktuellen Umgebung wiederherstellen, erstellt wurde. Die Clientimplementierung sollten versuchen, suchen den Anker relativ zu Ihrer lokalen Koordinatensystem oder der Zielframe, Verweis, vor dem Fortfahren auf, um zu versuchen, die für live-Inhalte verwenden. Versuchen Sie z. B. den Anker relativ zu einem aktuellen Koordinatensystem suchen, in regelmäßigen Abständen, bis der Anker beginnt auffindbar sein.

## <a name="special-considerations"></a>Besondere Überlegungen

Die [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) -API ermöglicht es mehreren [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) in das gleiche nicht transparente binäre Blob exportiert werden. Es ist jedoch auch ein feinen Unterschied in das Blob enthalten wird, je nachdem, ob eine einzelne SpatialAnchor oder mehrere SpatialAnchors in einem einzigen Aufruf exportiert werden, Daten.

### <a name="export-of-a-single-spatialanchor"></a>Exportieren von einem einzelnen SpatialAnchor

Das Blob enthält eine Darstellung der Umgebung ausgetreten ist, die SpatialAnchor, damit die Umgebung auf dem Gerät erkannt werden kann, die die SpatialAnchor importiert. Nachdem der Import abgeschlossen ist, wird die neue SpatialAnchor auf dem Gerät verfügbar sein. Vorausgesetzt, dass der Benutzer wurde vor kurzem in der Nähe der Anker, es werden gebietsschemabezogene und Hologramme angefügt, um die SpatialAnchor gerendert werden können. Diese Hologramme werden in demselben physischen Standort angezeigt, die sie auf dem ursprünglichen Gerät haben, die die SpatialAnchor exportiert.

![Exportieren von einem einzelnen SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Exportieren von mehreren SpatialAnchors

Wie der Export von einer einzelnen SpatialAnchor enthält das Blob eine Darstellung der Umgebung ausgetreten ist, die alle angegebenen SpatialAnchors. Darüber hinaus enthält das Blob Informationen zu den Verbindungen zwischen den SpatialAnchors enthalten, wenn sie in der gleichen physischen Adressraum befinden. Dies bedeutet, dass zwei in der Nähe SpatialAnchors importiert werden, klicken Sie dann ggf. ein Hologramm angefügt der *zweite* SpatialAnchor würde lokalisierbar sein, selbst wenn das Gerät nur die Umgebung aus, um erkennt die *erste* SpatialAnchor, war da ausreichend Daten zum Berechnen zwischen den zwei SpatialAnchors transformieren enthalten im Blob. Wenn die zwei SpatialAnchors einzeln exportiert wurden (zwei separate Aufrufe TryExportSpatialAnchors) und dann möglicherweise nicht genügend Daten im Blob enthalten, für die Hologramme der zweiten SpatialAnchor zu auffindbar sein, wenn das erste Abonnement angefügt befindet.

![Mehrere Anker mit einem einzigen Aufruf der TryExportAnchorsAsync exportiert](images/multipleanchors.png) ![Mehrere Anker exportiert einen separaten TryExportAnchorsAsync-Aufruf für jede Anker verwenden](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Beispiel: Senden von Anchor-Daten, die mithilfe einer Windows::Networking::StreamSocket

Hier bieten wir ein Beispiel dafür, wie exportierte Anker-Daten verwenden, indem Sie ihn in einem TCP-Netzwerk zu senden. Dies ist von der HolographicSpatialAnchorTransferSample.

Die WinRT-StreamSocket-Klasse verwendet die PPL-Aufgabe-Bibliothek. Im Fall von Netzwerkfehler auftreten wird der Fehler zurückgegeben, mit der nächsten Aufgabe in der Kette mit einer Ausnahme, die erneut ausgelöst wird. Die Ausnahme enthält einen HRESULT, der angibt, den Status "Fehler".

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Verwenden Sie zum Senden von Daten der exportierten Anker ein Windows::Networking::StreamSocketListener mit TCP

Erstellen Sie eine Server-Instanz, die für eine Verbindung überwacht.

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

Wenn eine Verbindung empfangen wird, verwenden Sie die Client-Socket-Verbindung zum Senden von Daten der Anker aus.

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

Jetzt können wir jetzt einen Datenstrom zu senden, der die exportierten Anchor-Daten enthält.

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

Bevor wir den Datenstrom selbst senden können, müssen wir zunächst ein Paket Header senden. Dieses Paket Header muss mit fester Länge, und es muss auch angeben, die Länge des Variablenarray von Bytes, die der Anker-Datenstrom ist; In diesem Beispiel benötigen wir keine anderen zu sendenden Headerdaten also unsere Header ist 4 Bytes lang und enthält eine 32-Bit-Ganzzahl ohne Vorzeichen.

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

Wenn die Länge des Streams in Bytes an den Client gesendet wurde, können Sie den Datenstrom selbst in der Socket-Stream zu schreibende fortfahren. Dies bewirkt, dass die Premium-Shop-Bytes, die an den Client gesendet werden können.

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

Wie weiter oben in diesem Thema erwähnt, müssen wir auf die Behandlung von Ausnahmen, die mit der Netzwerk-fehlerstatusmeldungen vorbereitet sein. Für Fehler, die nicht erwartet werden, können wir die Ausnahmeinformationen in die Debugging-Konsole schreiben wie folgt. Dadurch erhalten wir einen Hinweis darauf sein, was passiert, wenn unsere Codebeispiel zum Herstellen die Verbindung nicht möglich ist oder sie senden die Daten der Anker abschließen kann.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Verwenden Sie eine Windows::Networking::StreamSocket mit TCP zum Empfangen von Daten der exportierten Anker

Zunächst müssen wir mit dem Server herzustellen. In diesem Codebeispiel wird veranschaulicht das Erstellen und Konfigurieren einer StreamSocket und erstellen ein DataReader-Ziel, die Sie zum Abrufen von Netzwerkdaten, die mithilfe der Socketverbindung verwenden können.

**HINWEIS:** Wenn Sie diesen Beispielcode ausführen, stellen Sie sicher, dass Sie konfigurieren und starten den Server vor dem Starten des Clients.

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

Sobald wir eine Verbindung haben, können wir den Server zum Senden von Daten warten. Hierzu müssen wir LoadAsync für den Datenreader Stream aufrufen.

Die erste Gruppe von Bytes, die wir erhalten sollte immer das Paket Header gibt an, dass der Anker Bytelänge Datenstrom wie im vorherigen Abschnitt beschrieben.

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

Nachdem wir das Header-Paket erhalten haben, wissen wir wie viele Bytes der Anker-Daten, die es erwarten. Wir können fortfahren, und diese Bytes aus dem Stream gelesen werden soll.

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

Hier ist unser Code für den Empfang von des Anker-Datenstrom. In diesem Fall werden wir zunächst die Bytes aus dem Stream laden; Dieser Vorgang dauert einige Zeit in Anspruch, während die StreamSocket wartet, um die Menge an Bytes aus dem Netzwerk empfangen.

Wenn der Ladevorgang abgeschlossen ist, können wir diese Anzahl von Bytes lesen. Wenn wir die Anzahl der Bytes, die wir für den Datenstream Anker zu erwarten empfangen, können wir fortfahren, und importieren Sie die Daten der Anker; Wenn dies nicht der Fall ist, es wurde eine Art von Fehler. Dies kann z. B. der Fall sein, wenn die Server-Instanz beendet wird, bevor können den Datenstrom abzuschließen, oder das Netzwerk ausfällt, bevor der gesamte Datenstrom vom Client empfangen werden kann.

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

In diesem Fall müssen wir auf die Behandlung Unbekannter Netzwerkfehler vorbereitet sein.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Das ist alles! Jetzt sollten Sie genügend Informationen, um zu versuchen, suchen die Anker, der über das Netzwerk empfangen haben. In diesem Fall Beachten Sie, dass der Client genügend visual Überwachungsdaten für den Speicherplatz den Anker erfolgreich gefunden; Wenn sie nicht sofort funktioniert, versuchen Sie es für eine Weile durchlaufen. Wenn es weiterhin nicht funktioniert, müssen Sie des Servers mehr Anker zu senden, und verwenden die Netzwerkkommunikation auf einem zustimmen, die für den Client geeignet. Sie können dies testen der HolographicSpatialAnchorTransferSample herunterladen und Konfigurieren von Client und Server IP-Adressen in Client- und HoloLens-Geräte bereitstellen.

## <a name="see-also"></a>Siehe auch
* [Parallel Patterns Library (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
