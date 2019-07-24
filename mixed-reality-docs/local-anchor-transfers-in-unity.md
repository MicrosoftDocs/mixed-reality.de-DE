---
title: Lokale Anker Übertragungen in Unity
description: Übertragen von Ankern zwischen mehreren hololens-Geräten in einer Unity-Anwendung.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Freigabe, Anker, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Transfer, local Anchor Transfer, Anchor Export, Anchor Import
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516136"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="6b314-104">Lokale Anker Übertragungen in Unity</span><span class="sxs-lookup"><span data-stu-id="6b314-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="6b314-105">In Fällen, in denen Sie keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumlichen Anker von Azure</a>verwenden können, ermöglichen lokale Anker Übertragungen einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b314-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="6b314-106">Lokale Anker Übertragungen bieten weniger robusten Anker als Anker als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumliche Azure-Anker</a>, und IOS-und Android-Geräte werden von diesem Ansatz nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b314-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="6b314-107">Festlegen der spatialperception-Funktion</span><span class="sxs-lookup"><span data-stu-id="6b314-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="6b314-108">Damit eine APP räumliche Anker übertragen kann, muss die *spatialperception* -Funktion aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="6b314-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="6b314-109">Aktivieren der *spatialperception* -Funktion:</span><span class="sxs-lookup"><span data-stu-id="6b314-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="6b314-110">Öffnen Sie im Unity-Editor den Bereich **"Player Einstellungen"** (Bearbeiten > Projekteinstellungen > Player).</span><span class="sxs-lookup"><span data-stu-id="6b314-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="6b314-111">Klicken Sie auf die Registerkarte **"Windows Store"** .</span><span class="sxs-lookup"><span data-stu-id="6b314-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="6b314-112">Erweitern Sie **"Veröffentlichungs Einstellungen"** , und überprüfen Sie die Funktion **"spatialperception"** in der Liste **"Funktionen"** .</span><span class="sxs-lookup"><span data-stu-id="6b314-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="6b314-113">Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projekt Mappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder [Diese Funktion manuell in "appxmanifest" in Visual Studio festlegen](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="6b314-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="6b314-114">Anker Übertragung</span><span class="sxs-lookup"><span data-stu-id="6b314-114">Anchor Transfer</span></span>

<span data-ttu-id="6b314-115">**Namespace:** *Unityengine. XR. WSA. Sharing*</span><span class="sxs-lookup"><span data-stu-id="6b314-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="6b314-116">**Typ**: *Worldanchortransferbatch*</span><span class="sxs-lookup"><span data-stu-id="6b314-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="6b314-117">Zum Übertragen eines [worldanchors](coordinate-systems-in-unity.md)müssen Sie den Anker einrichten, der übertragen werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b314-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="6b314-118">Der Benutzer eines hololens scannt seine Umgebung und wählt entweder manuell oder Programm gesteuert einen Punkt im Bereich aus, um als Anker für die gemeinsame Nutzung zu gelten.</span><span class="sxs-lookup"><span data-stu-id="6b314-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="6b314-119">Die Daten, die diesen Punkt darstellen, können dann serialisiert und an die anderen Geräte übertragen werden, die in der-Funktion gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="6b314-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="6b314-120">Jedes Gerät deserialisiert dann die Anker Daten und versucht, diesen Punkt im Speicherplatz zu finden.</span><span class="sxs-lookup"><span data-stu-id="6b314-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="6b314-121">Damit die Anker Übertragung funktioniert, muss jedes Gerät in genügend der Umgebung gescannt werden, damit der durch den Anker dargestellte Punkt identifiziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6b314-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="6b314-122">Setup</span><span class="sxs-lookup"><span data-stu-id="6b314-122">Setup</span></span>

<span data-ttu-id="6b314-123">Der Beispielcode auf dieser Seite verfügt über einige Felder, die initialisiert werden müssen:</span><span class="sxs-lookup"><span data-stu-id="6b314-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="6b314-124">*Gameobject rootgameobject* ist ein *gameobject* in Unity, das über eine *worldanchor* -Komponente verfügt.</span><span class="sxs-lookup"><span data-stu-id="6b314-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="6b314-125">Ein Benutzer in der freigegebenen Benutzer Darstellung wird dieses *gameobject* platzieren und die Daten an die anderen Benutzer exportieren.</span><span class="sxs-lookup"><span data-stu-id="6b314-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="6b314-126">*Worldanchor gamerootanchor* ist das *unityengine. XR. WSA. worldanchor* -Objekt, das auf *rootgameobject*basiert.</span><span class="sxs-lookup"><span data-stu-id="6b314-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="6b314-127">*Byte [] importeddata* ist ein Bytearray für den serialisierten Anker, der von jedem Client über das Netzwerk empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="6b314-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="6b314-128">Export</span><span class="sxs-lookup"><span data-stu-id="6b314-128">Exporting</span></span>

<span data-ttu-id="6b314-129">Zum Exportieren benötigen wir lediglich einen *worldanchor* und wissen, wie wir ihn nennen werden, damit er für die empfangende App sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="6b314-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="6b314-130">Ein Client in der freigegebenen Darstellung führt diese Schritte aus, um den gemeinsamen Anker zu exportieren:</span><span class="sxs-lookup"><span data-stu-id="6b314-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="6b314-131">Erstellen eines *worldanchortransferbatches*</span><span class="sxs-lookup"><span data-stu-id="6b314-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="6b314-132">Zu übertragenden *worldanchors* hinzufügen</span><span class="sxs-lookup"><span data-stu-id="6b314-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="6b314-133">Export starten</span><span class="sxs-lookup"><span data-stu-id="6b314-133">Begin the export</span></span>
4. <span data-ttu-id="6b314-134">Behandeln Sie das *onexportdataavailable* -Ereignis, wenn Daten verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="6b314-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="6b314-135">Behandeln des *onexportcomplete* -Ereignisses</span><span class="sxs-lookup"><span data-stu-id="6b314-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="6b314-136">Wir erstellen einen *worldanchortransferbatch* , um zu kapseln, was wir übertragen werden, und exportieren Sie dann in Bytes:</span><span class="sxs-lookup"><span data-stu-id="6b314-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="6b314-137">Wenn Daten verfügbar werden, senden Sie die Bytes an den Client oder Puffer, wenn Daten Segmente verfügbar sind, und senden Sie Sie über beliebige Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="6b314-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="6b314-138">Nachdem der Export abgeschlossen ist, weisen Sie den Client an, die Daten zu verwerfen, wenn die Daten übertragen wurden und die Serialisierung fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="6b314-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="6b314-139">Wenn die Serialisierung erfolgreich war, teilen Sie dem Client mit, dass alle Daten übertragen wurden und der Import Vorgang gestartet werden kann:</span><span class="sxs-lookup"><span data-stu-id="6b314-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="6b314-140">Humi</span><span class="sxs-lookup"><span data-stu-id="6b314-140">Importing</span></span>

<span data-ttu-id="6b314-141">Nachdem alle Bytes vom Absender empfangen wurden, können wir die Daten zurück in ein *worldanchortransferbatch* importieren und das Stamm Spielobjekt an demselben physischen Speicherort sperren.</span><span class="sxs-lookup"><span data-stu-id="6b314-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="6b314-142">Hinweis: der Import schlägt gelegentlich fehl, und es muss ein erneuter Versuch unternommen werden:</span><span class="sxs-lookup"><span data-stu-id="6b314-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="6b314-143">Nachdem ein *gameobject-Objekt* über den *Lock Object* -Befehl gesperrt wurde, verfügt es über einen *worldanchor* , der ihn an derselben physischen Position in der Welt hält, er kann sich aber an einem anderen Speicherort im Unity-Koordinaten Bereich befinden als andere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="6b314-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

