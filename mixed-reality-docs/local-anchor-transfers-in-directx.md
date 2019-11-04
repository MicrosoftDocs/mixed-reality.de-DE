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
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="c2680-104">Lokale Anker Übertragungen in DirectX</span><span class="sxs-lookup"><span data-stu-id="c2680-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="c2680-105">In Fällen, in denen Sie keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumlichen Anker von Azure</a>verwenden können, ermöglichen lokale Anker Übertragungen einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2680-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="c2680-106">Lokale Anker Übertragungen bieten weniger robusten Anker als Anker als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumliche Azure-Anker</a>, und IOS-und Android-Geräte werden von diesem Ansatz nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2680-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="c2680-107">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c2680-108">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="c2680-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="c2680-109">Übertragen räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="c2680-109">Transferring spatial anchors</span></span>

<span data-ttu-id="c2680-110">Räumliche Anker können mithilfe von [spatialanchortransfermanager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)zwischen Windows Mixed Reality-Geräten übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="c2680-111">Mit dieser API können Sie einen Anker mit allen unterstützenden Sensordaten bündeln, die erforderlich sind, um den genauen Ort auf der Welt zu finden und dann dieses Paket auf ein anderes Gerät zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c2680-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="c2680-112">Nachdem die APP auf dem zweiten Gerät diesen Anker importiert hat, kann jede APP Hologramme mithilfe des Koordinatensystems des freigegebenen räumlichen Ankers Rendering erzeugen, das dann an derselben Stelle in der realen Welt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c2680-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="c2680-113">Beachten Sie, dass räumliche Anker nicht zwischen verschiedenen Gerätetypen übertragen werden können, z. b. kann ein räumlicher hololens-Anker nicht mithilfe eines immersiven Headsets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="c2680-114">Übertragene Anker sind ebenfalls nicht mit IOS-oder Android-Geräten kompatibel.</span><span class="sxs-lookup"><span data-stu-id="c2680-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="c2680-115">Einrichten Ihrer APP für die Verwendung der spatialperception-Funktion</span><span class="sxs-lookup"><span data-stu-id="c2680-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="c2680-116">Ihrer APP muss die Berechtigung zum Verwenden der spatialperception-Funktion erteilt werden, bevor Sie den [spatialanchortransfermanager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="c2680-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="c2680-117">Dies ist erforderlich, da das übertragen eines räumlichen Ankers das Freigeben von Sensor Bildern im Laufe der Zeit in der Nähe dieses Ankers beinhaltet, die vertrauliche Informationen enthalten können.</span><span class="sxs-lookup"><span data-stu-id="c2680-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="c2680-118">Deklarieren Sie diese Funktion in der Datei "Package. appxmanifest" für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="c2680-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="c2680-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c2680-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="c2680-120">Die Funktion stammt aus dem **uap2** -Namespace.</span><span class="sxs-lookup"><span data-stu-id="c2680-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="c2680-121">Um Zugriff auf diesen Namespace in ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns* -Attribut in das &lt;Package >-Elements ein.</span><span class="sxs-lookup"><span data-stu-id="c2680-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="c2680-122">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c2680-122">Here's an example:</span></span>

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="c2680-123">**Hinweis:** Ihre APP muss die Funktion zur Laufzeit anfordern, bevor Sie auf die APIs für den Zugriff auf spatialanchor exportieren/importieren zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="c2680-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="c2680-124">Weitere Informationen finden Sie in den folgenden Beispielen unter [requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) .</span><span class="sxs-lookup"><span data-stu-id="c2680-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="c2680-125">Serialisieren von Anker Daten durch Exportieren mit spatialanchortransfermanager</span><span class="sxs-lookup"><span data-stu-id="c2680-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="c2680-126">Eine Hilfsfunktion ist im Codebeispiel zum Exportieren (Serialisieren) der [spatialanchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) -Daten enthalten.</span><span class="sxs-lookup"><span data-stu-id="c2680-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="c2680-127">Diese Export-API serialisiert alle Anker in einer Auflistung von Schlüssel-Wert-Paaren, die Zeichen folgen mit Ankern zuordnen.</span><span class="sxs-lookup"><span data-stu-id="c2680-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="c2680-128">Zuerst müssen wir den Datenstream einrichten.</span><span class="sxs-lookup"><span data-stu-id="c2680-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="c2680-129">Dies ermöglicht uns 1.) Verwenden Sie tryexportanchorsasync, um die Daten in einem Puffer zu platzieren, der der APP gehört, und 2.) Lesen von Daten aus dem exportierten Byte-Puffer Datenstrom, bei dem es sich um einen WinRT-Datenstrom handelt, in unseren eigenen Speicherpuffer, bei dem es sich um eine Std:: Vector-&lt;> Byte</span><span class="sxs-lookup"><span data-stu-id="c2680-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="c2680-130">Wir müssen die Berechtigung für den Zugriff auf räumliche Daten, einschließlich Anker, die vom System exportiert werden, anfordern.</span><span class="sxs-lookup"><span data-stu-id="c2680-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="c2680-131">Wenn wir die Get-Berechtigung erhalten und Anker exportiert werden, können wir den Datenstrom lesen.</span><span class="sxs-lookup"><span data-stu-id="c2680-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="c2680-132">Hier erfahren Sie auch, wie Sie den DataReader und den InputStream erstellen, die zum Lesen der Daten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="c2680-133">Nachdem wir Bytes aus dem Stream gelesen haben, können wir diese wie folgt in unserem eigenen Datenpuffer speichern.</span><span class="sxs-lookup"><span data-stu-id="c2680-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="c2680-134">Deserialisieren von Anker Daten durch Importieren in das System mithilfe von spatialanchortransfermanager</span><span class="sxs-lookup"><span data-stu-id="c2680-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="c2680-135">Eine Hilfsfunktion ist im Codebeispiel enthalten, um zuvor exportierte Daten zu laden.</span><span class="sxs-lookup"><span data-stu-id="c2680-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="c2680-136">Diese deserialisierungssoftware stellt eine Auflistung von Schlüssel-Wert-Paaren bereit, ähnlich wie im spatialanchorstore, mit dem Unterschied, dass diese Daten aus einer anderen Quelle, z. b. einem Netzwerk Socket, erhalten wurden.</span><span class="sxs-lookup"><span data-stu-id="c2680-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="c2680-137">Sie können diese Daten vor der Offline Speicherung, bei Verwendung von in-App-Arbeitsspeicher oder (falls zutreffend) in den spatialanchorstore Ihrer APP verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c2680-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="c2680-138">Zuerst müssen wir Streamobjekte erstellen, um auf die Anker Daten zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="c2680-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="c2680-139">Wir werden die Daten aus dem Puffer in einen System Puffer schreiben. Daher erstellen wir einen DataWriter, der in einen Datenstrom im Arbeitsspeicher schreibt, um das Ziel zu erreichen, die Anker von einem Byte Puffer in das System als spatialanchor zu bringen.</span><span class="sxs-lookup"><span data-stu-id="c2680-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="c2680-140">Auch hier müssen wir sicherstellen, dass die APP über die Berechtigung zum Exportieren räumlicher Anker Daten verfügt. Dies kann private Informationen über die Benutzerumgebung beinhalten.</span><span class="sxs-lookup"><span data-stu-id="c2680-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="c2680-141">Wenn der Zugriff zulässig ist, können wir Bytes aus dem Puffer in einen Systemdaten Strom schreiben.</span><span class="sxs-lookup"><span data-stu-id="c2680-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="c2680-142">Wenn die Speicherung von Bytes im Datenstrom erfolgreich war, können Sie versuchen, diese Daten mit dem spatialanchortransfermanager zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c2680-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="c2680-143">Wenn die Daten importiert werden können, erhalten Sie eine Kartenansicht von Schlüssel-Wert-Paaren, die Zeichen folgen mit Ankern zuordnen.</span><span class="sxs-lookup"><span data-stu-id="c2680-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="c2680-144">Wir können dies in unsere eigene in-Memory-Datensammlung laden und diese Sammlung verwenden, um nach Anker zu suchen, die wir verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="c2680-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="c2680-145">**Hinweis:** Nur weil Sie einen Anker importieren können, bedeutet nicht notwendigerweise, dass Sie ihn sofort verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c2680-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="c2680-146">Der Anker befindet sich möglicherweise in einem anderen Raum oder an einem anderen physischen Standort. der Anker kann erst nach dem Gerät, das es empfangen hat, genug visuelle Informationen über die Umgebung haben, in der der Anker erstellt wurde, um die Position des Ankers relativ zur bekannten aktuellen Umgebung wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="c2680-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="c2680-147">Die Client Implementierung sollte versuchen, den Anker relativ zum lokalen Koordinatensystem oder Referenzrahmen zu finden, bevor Sie mit dem Versuch fortfahren, ihn für Live-Inhalte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c2680-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="c2680-148">Versuchen Sie z. b., den Anker in regelmäßigen Abständen relativ zu einem aktuellen Koordinatensystem zu suchen, bis der Anker als zu verwendbar festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c2680-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="c2680-149">Besondere Überlegungen</span><span class="sxs-lookup"><span data-stu-id="c2680-149">Special Considerations</span></span>

<span data-ttu-id="c2680-150">Die [tryexportanchorsasync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) -API ermöglicht das Exportieren mehrerer [spatialanchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) -Werte in dasselbe nicht transparente binäre Blob.</span><span class="sxs-lookup"><span data-stu-id="c2680-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="c2680-151">Es gibt jedoch einen geringfügigen Unterschied, welche Daten das BLOB enthält, abhängig davon, ob ein einzelner spatialanchor oder mehrere spatialanchor-Elemente in einem einzelnen-Befehl exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="c2680-152">Exportieren eines einzelnen spatialanchor</span><span class="sxs-lookup"><span data-stu-id="c2680-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="c2680-153">Das BLOB enthält eine Darstellung der Umgebung in der Nähe des spatialanchors, sodass die Umgebung auf dem Gerät erkannt werden kann, das den spatialanchor importiert.</span><span class="sxs-lookup"><span data-stu-id="c2680-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="c2680-154">Nachdem der Import abgeschlossen wurde, ist der neue spatialanchor für das Gerät verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c2680-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="c2680-155">Vorausgesetzt, dass sich der Benutzer vor kurzem in der Nähe des Ankers befand, ist er möglich und kann gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="c2680-156">Diese Hologramme werden am gleichen physischen Speicherort angezeigt, den Sie auf dem ursprünglichen Gerät erstellt haben, das den spatialanchor exportiert hat.</span><span class="sxs-lookup"><span data-stu-id="c2680-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![Exportieren eines einzelnen spatialanchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="c2680-158">Exportieren von mehreren spatialanchor-</span><span class="sxs-lookup"><span data-stu-id="c2680-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="c2680-159">Wie beim Export eines einzelnen spatialanchor enthält das BLOB eine Darstellung der Umgebung in der Nähe aller angegebenen spatialanchor.</span><span class="sxs-lookup"><span data-stu-id="c2680-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="c2680-160">Außerdem enthält das BLOB Informationen zu den Verbindungen zwischen den enthaltenen spatialanchor-Daten, wenn Sie sich im gleichen physischen Raum befinden.</span><span class="sxs-lookup"><span data-stu-id="c2680-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="c2680-161">Dies bedeutet, dass, wenn zwei in der Nähe gelegene räumliche Anker importiert werden, ein – Hologramm, das an den *zweiten* spatialanchor angefügt ist, auch dann einstellbar ist, wenn das Gerät nur die Umgebung um den *ersten* spatialanchor erkennt, weil genügend Daten für Die COMPUTE-Transformation zwischen den beiden spatialanchor-Einheiten war im BLOB enthalten.</span><span class="sxs-lookup"><span data-stu-id="c2680-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="c2680-162">Wenn die beiden spatialanchor einzeln exportiert wurden (zwei separate Aufrufe von tryexportspatialanchor), sind möglicherweise nicht genügend Daten im BLOB für holograms enthalten, die an den zweiten spatialanchor angefügt sind, damit Sie bei der ersten gefunden werden können.</span><span class="sxs-lookup"><span data-stu-id="c2680-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![Mehrere Anker werden mithilfe eines einzelnen tryexportanchorsasync-Aufrufes exportiert.](images/multipleanchors.png) ![Mehrere Anker, die mithilfe eines separaten tryexportanchorsasync-Aufrufes für jeden Anker exportiert wurden.](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="c2680-165">Beispiel: Senden von Anker Daten mithilfe von Windows:: Networking:: Streamsocket</span><span class="sxs-lookup"><span data-stu-id="c2680-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="c2680-166">Hier geben wir ein Beispiel für die Verwendung von exportierten Anker Daten an, indem Sie Sie über ein TCP-Netzwerk senden.</span><span class="sxs-lookup"><span data-stu-id="c2680-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="c2680-167">Dies erfolgt aus dem holographicspatialanchortransfersample.</span><span class="sxs-lookup"><span data-stu-id="c2680-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="c2680-168">Die WinRT-Streamsocket-Klasse verwendet die ppl-Aufgaben Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="c2680-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="c2680-169">Im Fall von Netzwerkfehlern wird der Fehler an die nächste Aufgabe in der Kette zurückgegeben, wobei eine Ausnahme erneut ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="c2680-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="c2680-170">Die Ausnahme enthält ein HRESULT, das den Fehlerstatus angibt.</span><span class="sxs-lookup"><span data-stu-id="c2680-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="c2680-171">Verwenden eines Windows:: Networking:: streamsocketlistener mit TCP zum Senden von exportierten Anker Daten</span><span class="sxs-lookup"><span data-stu-id="c2680-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="c2680-172">Erstellen Sie eine Serverinstanz, die auf eine Verbindung lauscht.</span><span class="sxs-lookup"><span data-stu-id="c2680-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="c2680-173">Wenn eine Verbindung empfangen wird, verwenden Sie die Clientsocket-Verbindung, um Anker Daten zu senden.</span><span class="sxs-lookup"><span data-stu-id="c2680-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="c2680-174">Nun können wir beginnen, einen Datenstrom zu senden, der die exportierten Anker Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="c2680-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="c2680-175">Bevor wir den Datenstrom selbst senden können, müssen wir zuerst ein Header Paket senden.</span><span class="sxs-lookup"><span data-stu-id="c2680-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="c2680-176">Dieses Header Paket muss eine festgelegte Länge aufweisen, und es muss auch die Länge des Variablen Arrays von Bytes angeben, das der Anker Datenstrom ist. im Fall dieses Beispiels sind keine anderen Header Daten zum Senden vorhanden, daher ist der Header 4 Bytes lang und enthält eine 32-Bit-Ganzzahl ohne Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="c2680-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="c2680-177">Nachdem die Streamlänge in Bytes an den Client gesendet wurde, können wir mit dem Schreiben des Datenstroms selbst in den socketstream fortfahren.</span><span class="sxs-lookup"><span data-stu-id="c2680-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="c2680-178">Dies bewirkt, dass die Anker Speicher Bytes an den Client gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="c2680-179">Wie bereits weiter oben in diesem Thema erwähnt, müssen wir auf die Behandlung von Ausnahmen vorbereitet sein, die Netzwerkfehler Statusmeldungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="c2680-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="c2680-180">Bei nicht erwarteten Fehlern können wir die Ausnahme Informationen wie folgt in die Debugkonsole schreiben.</span><span class="sxs-lookup"><span data-stu-id="c2680-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="c2680-181">Dadurch erhalten Sie einen Anhaltspunkt, was passiert, wenn das Codebeispiel die Verbindung nicht abschließen kann, oder wenn das Senden der Anker Daten nicht abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c2680-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="c2680-182">Verwenden Sie Windows:: Networking:: Streamsocket mit TCP, um exportierte Anker Daten zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="c2680-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="c2680-183">Zuerst müssen wir eine Verbindung mit dem Server herstellen.</span><span class="sxs-lookup"><span data-stu-id="c2680-183">First, we have to connect to the server.</span></span> <span data-ttu-id="c2680-184">Dieses Codebeispiel veranschaulicht das Erstellen und Konfigurieren eines Streamsockets und das Erstellen eines DataReader, den Sie zum Abrufen von Netzwerkdaten mithilfe der Socketverbindung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c2680-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="c2680-185">**Hinweis:** Wenn Sie diesen Beispielcode ausführen, stellen Sie sicher, dass Sie den Server konfigurieren und starten, bevor Sie den Client starten.</span><span class="sxs-lookup"><span data-stu-id="c2680-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="c2680-186">Nachdem eine Verbindung hergestellt wurde, können wir warten, bis der Serverdaten sendet.</span><span class="sxs-lookup"><span data-stu-id="c2680-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="c2680-187">Dies geschieht durch Aufrufen von LoadAsync für den Daten Leser des Datenstroms.</span><span class="sxs-lookup"><span data-stu-id="c2680-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="c2680-188">Der erste Satz von Bytes, den wir empfangen, sollte immer das Header Paket sein, das die Byte Länge des Anker Datenstroms angibt, wie im vorherigen Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c2680-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="c2680-189">...</span><span class="sxs-lookup"><span data-stu-id="c2680-189">...</span></span>

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

<span data-ttu-id="c2680-190">Nachdem wir das Header Paket erhalten haben, wissen wir, wie viele Bytes an Anker Daten erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="c2680-191">Wir können fortfahren, um die Bytes aus dem Stream zu lesen.</span><span class="sxs-lookup"><span data-stu-id="c2680-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="c2680-192">Hier ist unser Code zum Empfangen des Anker Datenstroms.</span><span class="sxs-lookup"><span data-stu-id="c2680-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="c2680-193">Die Bytes werden zuerst aus dem Datenstrom geladen. Dieser Vorgang kann einige Zeit in Anspruch nehmen, da der Streamsocket darauf wartet, diese Menge von Bytes aus dem Netzwerk zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="c2680-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="c2680-194">Nachdem der Ladevorgang beendet wurde, können wir diese Anzahl von Bytes lesen.</span><span class="sxs-lookup"><span data-stu-id="c2680-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="c2680-195">Wenn wir die Anzahl der Bytes erhalten haben, die für den Anker Datenstrom erwartet werden, können wir die Anker Daten importieren. Wenn dies nicht der Fall ist, muss ein Fehler aufgetreten sein.</span><span class="sxs-lookup"><span data-stu-id="c2680-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="c2680-196">Dies kann z. b. der Fall sein, wenn die Serverinstanz beendet wird, bevor Sie das Senden des Datenstroms abschließen kann, oder wenn das Netzwerk ausfällt, bevor der gesamte Datenstrom vom Client empfangen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c2680-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="c2680-197">Auch hier müssen wir darauf vorbereitet sein, unbekannte Netzwerkfehler zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="c2680-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="c2680-198">Das war's.</span><span class="sxs-lookup"><span data-stu-id="c2680-198">That's it!</span></span> <span data-ttu-id="c2680-199">Nun sollten Sie über genügend Informationen verfügen, um zu versuchen, die Anker zu suchen, die über das Netzwerk empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="c2680-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="c2680-200">Beachten Sie, dass der Client über ausreichend visuelle Überwachungsdaten verfügen muss, damit der-Platz gefunden werden kann. Wenn es nicht sofort funktioniert, versuchen Sie es für eine Weile.</span><span class="sxs-lookup"><span data-stu-id="c2680-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="c2680-201">Wenn dies immer noch nicht funktioniert, lassen Sie den Server weitere Anker senden, und verwenden Sie die Netzwerkkommunikation, um eine Zustimmung für den Client zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c2680-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="c2680-202">Sie können dies ausprobieren, indem Sie das holographicspatialanchortransfersample herunterladen, die Client-und Server-IPS konfigurieren und Sie auf Client-und Server-hololens-Geräten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c2680-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2680-203">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="c2680-203">See also</span></span>
* [<span data-ttu-id="c2680-204">Parallel Patterns Library (PPL)</span><span class="sxs-lookup"><span data-stu-id="c2680-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="c2680-205">Windows. Networking. Streamsocket</span><span class="sxs-lookup"><span data-stu-id="c2680-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="c2680-206">Windows. Networking. streamsocketlistener</span><span class="sxs-lookup"><span data-stu-id="c2680-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
