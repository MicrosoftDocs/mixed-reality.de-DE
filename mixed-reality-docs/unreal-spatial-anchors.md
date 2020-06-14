---
title: Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker
ms.openlocfilehash: 1100704cae40de1997eb869bfc6c82bba3d0dc6e
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428730"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="f992c-104">Raumanker in Unreal</span><span class="sxs-lookup"><span data-stu-id="f992c-104">Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f992c-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f992c-105">Overview</span></span>

<span data-ttu-id="f992c-106">Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f992c-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="f992c-107">Diese werden über Unreal mithilfe von **ARPin**s angezeigt und im Ankerspeicher von HoloLens gespeichert, der in zukünftigen Sitzungen geladen wird.</span><span class="sxs-lookup"><span data-stu-id="f992c-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> 

## <a name="checking-the-anchor-store"></a><span data-ttu-id="f992c-108">Überprüfen des Ankerspeichers</span><span class="sxs-lookup"><span data-stu-id="f992c-108">Checking the anchor store</span></span>

<span data-ttu-id="f992c-109">Vor dem Speichern oder Laden von Ankern müssen Sie sich zunächst vergewissern, dass der Ankerspeicher bereit ist.</span><span class="sxs-lookup"><span data-stu-id="f992c-109">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="f992c-110">Versuche, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, sind nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="f992c-110">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Raumanker: Speicher bereit](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="f992c-112">Speichern von Ankern</span><span class="sxs-lookup"><span data-stu-id="f992c-112">Saving anchors</span></span>

<span data-ttu-id="f992c-113">Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="f992c-113">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Raumanker: Speichern](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="f992c-115">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="f992c-115">Breaking this down:</span></span>
1. <span data-ttu-id="f992c-116">Erzeugen Sie einen Akteur an einer bekannten Position.</span><span class="sxs-lookup"><span data-stu-id="f992c-116">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="f992c-117">Erstellen Sie einen **ARPin** mit dieser Position und einem Namen, der auf der Klasse des Akteurs basiert.</span><span class="sxs-lookup"><span data-stu-id="f992c-117">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="f992c-118">Fügen Sie dem **ARPin** den Akteur hinzu, und speichern Sie den Pin im HoloLens-Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="f992c-118">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="f992c-119">Der gewählte Ankername muss eindeutig sein, in diesem Fall verwenden wir dafür den aktuellen Zeitstempel.</span><span class="sxs-lookup"><span data-stu-id="f992c-119">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="f992c-120">Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter **System > Map manager > Anchor Files Saved On Device** (System > Zuordnungs-Manager > Auf dem Gerät gespeicherte Ankerdateien) überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="f992c-120">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="f992c-121">Laden von Ankern</span><span class="sxs-lookup"><span data-stu-id="f992c-121">Loading anchors</span></span>

<span data-ttu-id="f992c-122">Beim Start einer Anwendung können Sie die folgende Blaupause verwenden, um Komponenten an ihren Ankerpositionen wiederherzustellen:</span><span class="sxs-lookup"><span data-stu-id="f992c-122">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Raumanker: Laden](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="f992c-124">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="f992c-124">Breaking this down:</span></span>
1. <span data-ttu-id="f992c-125">Iterieren Sie über alle Anker im Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="f992c-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="f992c-126">Erzeugen Sie einen Akteur an einem neutralen Element.</span><span class="sxs-lookup"><span data-stu-id="f992c-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="f992c-127">Heften Sie diesen Akteur an den **ARPin** aus dem Ankerspeicher an.</span><span class="sxs-lookup"><span data-stu-id="f992c-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="f992c-128">Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="f992c-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="f992c-129">Jede hier hinzugefügte Transformation fügt dem Anker einen Offset hinzu.</span><span class="sxs-lookup"><span data-stu-id="f992c-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="f992c-130">Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können.</span><span class="sxs-lookup"><span data-stu-id="f992c-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="f992c-131">Entfernen von Ankern</span><span class="sxs-lookup"><span data-stu-id="f992c-131">Removing anchors</span></span> 

<span data-ttu-id="f992c-132">Wenn Sie die Arbeit mit einem Anker beendet haben, können Sie einzelne Anker oder den gesamten Ankerspeicher mit den Komponenten **Remove ARPin from WMRAnchor Store** (ARPin aus WMRAnkerspeicher entfernen) und **Remove All ARPins from WMRAnchor Store** (Alle ARPins aus WMRAnkerspeicher entfernen) löschen.</span><span class="sxs-lookup"><span data-stu-id="f992c-132">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Raumanker: Entfernen](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="f992c-134">Beachten Sie, dass Raumanker sich noch in der Betaphase befinden, prüfen Sie also unbedingt auf aktualisierte Informationen und Features.</span><span class="sxs-lookup"><span data-stu-id="f992c-134">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="f992c-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f992c-135">See also</span></span>
* [<span data-ttu-id="f992c-136">Raumanker</span><span class="sxs-lookup"><span data-stu-id="f992c-136">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="f992c-137">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="f992c-137">Coordinate systems</span></span>](coordinate-systems.md)
