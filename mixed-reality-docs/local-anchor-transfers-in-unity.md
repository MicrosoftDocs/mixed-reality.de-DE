---
title: Lokale Anchor-Übertragungen in Unity
description: Übertragen Sie Anker zwischen mehreren HoloLens-Geräte in einer Unity-Anwendung.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Freigabe, Anker, WorldAnchor, MR Freigabe 250, WorldAnchorTransferBatch, SpatialPerception, Übertragung, lokalen Anchor-Übertragung, Anchor-Export, Anker importieren
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605055"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="3950b-104">Lokale Anchor-Übertragungen in Unity</span><span class="sxs-lookup"><span data-stu-id="3950b-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="3950b-105">In Situationen, in dem können keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, die Übertragung von lokalen Anker ermöglichen ein HoloLens-Gerät so exportieren Sie einen Anker, die durch ein zweites Gerät mit HoloLens importiert werden.</span><span class="sxs-lookup"><span data-stu-id="3950b-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="3950b-106">Lokale Anker Übertragungen bieten weniger stabil Anchor-Rückruf als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, und IOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3950b-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="3950b-107">Festlegen der SpatialPerception-Funktion</span><span class="sxs-lookup"><span data-stu-id="3950b-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="3950b-108">Damit eine app zum Übertragen von räumlichen Anker, der *SpatialPerception* Funktion muss aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="3950b-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="3950b-109">Vorgehensweise: Aktivieren der *SpatialPerception* Funktion:</span><span class="sxs-lookup"><span data-stu-id="3950b-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="3950b-110">Öffnen Sie im Unity-Editor, der **"Player Settings"** Bereich (Bearbeiten > Projekteinstellungen > Player)</span><span class="sxs-lookup"><span data-stu-id="3950b-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="3950b-111">Klicken Sie auf die **"Windows Store"** Registerkarte</span><span class="sxs-lookup"><span data-stu-id="3950b-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="3950b-112">Erweitern Sie **"Veröffentlichungseinstellungen"** und überprüfen Sie die **"SpatialPerception"** -Funktion in der **"Funktionen"** Liste</span><span class="sxs-lookup"><span data-stu-id="3950b-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="3950b-113">Wenn Sie bereits Ihr Unity-Projekt in Visual Studio-Projektmappe exportiert haben, müssen Sie zum Exportieren in einen neuen Ordner oder manuell [legen Sie diese Funktion in die appxmanifest-Datei in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="3950b-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="3950b-114">Anker-Übertragung</span><span class="sxs-lookup"><span data-stu-id="3950b-114">Anchor Transfer</span></span>

<span data-ttu-id="3950b-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="3950b-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="3950b-116">**Typ**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="3950b-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="3950b-117">Zum Übertragen einer [WorldAnchor](coordinate-systems-in-unity.md), muss einen Anker zu übertragende herstellen.</span><span class="sxs-lookup"><span data-stu-id="3950b-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="3950b-118">Der Benutzer von einem HoloLens scannt ihre Umgebung und entweder manuell oder programmgesteuert, wählt einen Punkt im Raum der Anker für den gemeinsamen Erfahrung sein.</span><span class="sxs-lookup"><span data-stu-id="3950b-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="3950b-119">Die Daten, die von diesem Punkt stellt werden anschließend serialisiert und an die anderen Geräte, die in der Umgebung gemeinsam nutzen übertragen.</span><span class="sxs-lookup"><span data-stu-id="3950b-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="3950b-120">Jedes Gerät dann Deserialisierung wird die Anker-Daten und versucht, diesen Punkt im Raum zu finden.</span><span class="sxs-lookup"><span data-stu-id="3950b-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="3950b-121">In der Reihenfolge für Anker übertragen wird, funktionieren muss jedes Gerät so viele Zeichen von der Umgebung gescannt haben, dass der Punkt, der durch den Anker dargestellt wird, identifiziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="3950b-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="3950b-122">Setup</span><span class="sxs-lookup"><span data-stu-id="3950b-122">Setup</span></span>

<span data-ttu-id="3950b-123">Der Beispielcode auf dieser Seite verfügt über einige Felder, die initialisiert werden müssen:</span><span class="sxs-lookup"><span data-stu-id="3950b-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="3950b-124">*"Gameobject" RootGameObject* ist eine *"gameobject"* in Unity, die eine *WorldAnchor* Komponente auf.</span><span class="sxs-lookup"><span data-stu-id="3950b-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="3950b-125">Ein Benutzer in der gemeinsamen Erfahrung platziert diese *"gameobject"* und Exportieren der Daten in die andere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="3950b-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="3950b-126">*WorldAnchor GameRootAnchor* ist die *UnityEngine.XR.WSA.WorldAnchor* , die sich in *RootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="3950b-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="3950b-127">*Byte [] ImportedData* ist ein Bytearray, für den serialisierten Anker, die jeder Client über das Netzwerk empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="3950b-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="3950b-128">Exportieren</span><span class="sxs-lookup"><span data-stu-id="3950b-128">Exporting</span></span>

<span data-ttu-id="3950b-129">Um zu exportieren, müssen wir nur eine *WorldAnchor* und wissen es nennen wir werden so, dass es für die empfangenden app sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="3950b-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="3950b-130">Ein Client in der freigegebenen Umgebung führt vor, um den freigegebenen Anker zu exportieren:</span><span class="sxs-lookup"><span data-stu-id="3950b-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="3950b-131">Erstellen Sie eine *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="3950b-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="3950b-132">Hinzufügen der *WorldAnchors* übertragen</span><span class="sxs-lookup"><span data-stu-id="3950b-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="3950b-133">Der Export starten</span><span class="sxs-lookup"><span data-stu-id="3950b-133">Begin the export</span></span>
4. <span data-ttu-id="3950b-134">Behandeln der *OnExportDataAvailable* Ereignis als Daten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3950b-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="3950b-135">Behandeln der *OnExportComplete* Ereignis</span><span class="sxs-lookup"><span data-stu-id="3950b-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="3950b-136">Wir erstellen eine *WorldAnchorTransferBatch* , um was zu kapseln wir werden übertragen und dann exportieren, die in Bytes:</span><span class="sxs-lookup"><span data-stu-id="3950b-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="3950b-137">Wenn Daten verfügbar sind, senden Sie die Bytes an den Client oder Puffer zu, wie Segmente der Daten zur Verfügung steht, und senden Sie auf den gewünschten Weise:</span><span class="sxs-lookup"><span data-stu-id="3950b-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="3950b-138">Nachdem der Export abgeschlossen ist, wenn wir Daten übertragen wurden haben, und Fehler bei der Serialisierung, die dem Client mitteilen, die Daten zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="3950b-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="3950b-139">Wenn die Serialisierung erfolgreich war, weisen Sie den Client, dass alle Daten übertragen wurden, und Importieren von starten kann:</span><span class="sxs-lookup"><span data-stu-id="3950b-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="3950b-140">Importieren von</span><span class="sxs-lookup"><span data-stu-id="3950b-140">Importing</span></span>

<span data-ttu-id="3950b-141">Nachdem alle Bytes vom Absender empfangen werden müssen, können wir importieren Sie die Daten wieder in einen *WorldAnchorTransferBatch* und Sperren Sie unsere Spiele Stammobjekt in demselben physischen Standort.</span><span class="sxs-lookup"><span data-stu-id="3950b-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="3950b-142">Hinweis: der Import manchmal transiently fehl, und wiederholt werden muss:</span><span class="sxs-lookup"><span data-stu-id="3950b-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="3950b-143">Nach einer *"gameobject"* gesperrt ist, über die *LockObject* Aufruf muss eine *WorldAnchor* die in derselben physischen Position in der ganzen Welt halten, aber es kann sein, auf eine anderen Standort in der Unity-Zielkoordinatenbereich als andere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="3950b-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

