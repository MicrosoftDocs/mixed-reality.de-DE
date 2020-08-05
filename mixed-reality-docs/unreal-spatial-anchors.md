---
title: Lokale Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376046"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="7db46-104">Lokale Raumanker in Unreal</span><span class="sxs-lookup"><span data-stu-id="7db46-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="7db46-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7db46-105">Overview</span></span>

<span data-ttu-id="7db46-106">Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7db46-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="7db46-107">Diese werden über Unreal mithilfe von **ARPin**s angezeigt und im Ankerspeicher von HoloLens gespeichert, der in zukünftigen Sitzungen geladen wird.</span><span class="sxs-lookup"><span data-stu-id="7db46-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="7db46-108">Lokale Anker eignen sich ideal als Fallback, wenn keine Internetverbindung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="7db46-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7db46-109">Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="7db46-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="7db46-110">Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](unreal-azure-spatial-anchors.md) geführt werden.</span><span class="sxs-lookup"><span data-stu-id="7db46-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="7db46-111">Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.</span><span class="sxs-lookup"><span data-stu-id="7db46-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="7db46-112">Überprüfen des Ankerspeichers</span><span class="sxs-lookup"><span data-stu-id="7db46-112">Checking the anchor store</span></span>

<span data-ttu-id="7db46-113">Vor dem Speichern oder Laden von Ankern müssen Sie sich zunächst vergewissern, dass der Ankerspeicher bereit ist.</span><span class="sxs-lookup"><span data-stu-id="7db46-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="7db46-114">Versuche, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, sind nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="7db46-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Raumanker: Speicher bereit](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="7db46-116">Speichern von Ankern</span><span class="sxs-lookup"><span data-stu-id="7db46-116">Saving anchors</span></span>

<span data-ttu-id="7db46-117">Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="7db46-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Raumanker: Speichern](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="7db46-119">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="7db46-119">Breaking this down:</span></span>
1. <span data-ttu-id="7db46-120">Erzeugen Sie einen Akteur an einer bekannten Position.</span><span class="sxs-lookup"><span data-stu-id="7db46-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="7db46-121">Erstellen Sie einen **ARPin** mit dieser Position und einem Namen, der auf der Klasse des Akteurs basiert.</span><span class="sxs-lookup"><span data-stu-id="7db46-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="7db46-122">Fügen Sie dem **ARPin** den Akteur hinzu, und speichern Sie den Pin im HoloLens-Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="7db46-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="7db46-123">Der gewählte Ankername muss eindeutig sein, in diesem Fall verwenden wir dafür den aktuellen Zeitstempel.</span><span class="sxs-lookup"><span data-stu-id="7db46-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="7db46-124">Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter **System > Map manager > Anchor Files Saved On Device** (System > Zuordnungs-Manager > Auf dem Gerät gespeicherte Ankerdateien) überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="7db46-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="7db46-125">Laden von Ankern</span><span class="sxs-lookup"><span data-stu-id="7db46-125">Loading anchors</span></span>

<span data-ttu-id="7db46-126">Beim Start einer Anwendung können Sie die folgende Blaupause verwenden, um Komponenten an ihren Ankerpositionen wiederherzustellen:</span><span class="sxs-lookup"><span data-stu-id="7db46-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Raumanker: Laden](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="7db46-128">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="7db46-128">Breaking this down:</span></span>
1. <span data-ttu-id="7db46-129">Iterieren Sie über alle Anker im Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="7db46-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="7db46-130">Erzeugen Sie einen Akteur an einem neutralen Element.</span><span class="sxs-lookup"><span data-stu-id="7db46-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="7db46-131">Heften Sie diesen Akteur an den **ARPin** aus dem Ankerspeicher an.</span><span class="sxs-lookup"><span data-stu-id="7db46-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="7db46-132">Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="7db46-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="7db46-133">Jede hier hinzugefügte Transformation fügt dem Anker einen Offset hinzu.</span><span class="sxs-lookup"><span data-stu-id="7db46-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="7db46-134">Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können.</span><span class="sxs-lookup"><span data-stu-id="7db46-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="7db46-135">Entfernen von Ankern</span><span class="sxs-lookup"><span data-stu-id="7db46-135">Removing anchors</span></span> 

<span data-ttu-id="7db46-136">Wenn Sie die Arbeit mit einem Anker beendet haben, können Sie einzelne Anker oder den gesamten Ankerspeicher mit den Komponenten **Remove ARPin from WMRAnchor Store** (ARPin aus WMRAnkerspeicher entfernen) und **Remove All ARPins from WMRAnchor Store** (Alle ARPins aus WMRAnkerspeicher entfernen) löschen.</span><span class="sxs-lookup"><span data-stu-id="7db46-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Raumanker: Entfernen](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="7db46-138">Beachten Sie, dass Raumanker sich noch in der Betaphase befinden, prüfen Sie also unbedingt auf aktualisierte Informationen und Features.</span><span class="sxs-lookup"><span data-stu-id="7db46-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="7db46-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7db46-139">See also</span></span>
* [<span data-ttu-id="7db46-140">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="7db46-140">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="7db46-141">Raumanker</span><span class="sxs-lookup"><span data-stu-id="7db46-141">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="7db46-142">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="7db46-142">Coordinate systems</span></span>](coordinate-systems.md)
