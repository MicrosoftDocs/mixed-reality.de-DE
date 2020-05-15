---
title: Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840139"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="8d31c-104">Raumanker in Unreal</span><span class="sxs-lookup"><span data-stu-id="8d31c-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="8d31c-105">Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="8d31c-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="8d31c-106">Dies wird über Unreal mithilfe von „ARPins“ erreicht und für spätere Sitzungen im Ankerspeicher von HoloLens gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8d31c-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="8d31c-107">Vergewissern Sie sich vor dem Speichern oder Laden von Ankern zunächst, dass der Ankerspeicher bereit ist.</span><span class="sxs-lookup"><span data-stu-id="8d31c-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="8d31c-108">Wenn Sie versuchen, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, ist der Aufruf nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="8d31c-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Raumanker: Speicher bereit](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="8d31c-110">Speichern von Ankern</span><span class="sxs-lookup"><span data-stu-id="8d31c-110">Save Anchors</span></span>

<span data-ttu-id="8d31c-111">Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="8d31c-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Raumanker: Speichern](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="8d31c-113">Hier erzeugen wir einen Akteur an einer bekannten Position und erstellen einen AR-Pin mit dieser Position sowie einen Namen, der auf der Klasse des Akteurs basiert. Außerdem fügen wir den Akteur dem AR-Pin hinzu und speichern den Pin im HoloLens-Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="8d31c-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="8d31c-114">Da der gewählte Ankername eindeutig sein muss, wird in diesem Beispiel der aktuelle Zeitstempel angefügt.</span><span class="sxs-lookup"><span data-stu-id="8d31c-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="8d31c-115">Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter „System“ > „Map manager“ (Zuordnungs-Manager) > „Anchor Files Saved On Device“ (Auf dem Gerät gespeicherte Ankerdateien) überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="8d31c-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="8d31c-116">Laden von Ankern</span><span class="sxs-lookup"><span data-stu-id="8d31c-116">Load Anchors</span></span>

<span data-ttu-id="8d31c-117">Beim Start einer Anwendung kann die folgende Blaupause aufgerufen werden, um Komponenten an ihren Ankerpositionen wiederherzustellen:</span><span class="sxs-lookup"><span data-stu-id="8d31c-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![Raumanker: Laden](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="8d31c-119">In diesem Beispiel durchlaufen wir alle Anker im Ankerspeicher, erzeugen einen Akteur am neutralen Element und heften diesen Akteur an den AR-Pin aus dem Ankerspeicher an.</span><span class="sxs-lookup"><span data-stu-id="8d31c-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="8d31c-120">Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren, sodass jede hier hinzugefügte Transformation dem Anker ein Offset hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="8d31c-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="8d31c-121">Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können.</span><span class="sxs-lookup"><span data-stu-id="8d31c-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="8d31c-122">Entfernen von Ankern</span><span class="sxs-lookup"><span data-stu-id="8d31c-122">Remove Anchors</span></span> 

<span data-ttu-id="8d31c-123">Wenn Sie einen Anker nicht mehr benötigen, können Sie entweder den gesamten Ankerspeicher löschen oder einzelne Anker aus dem Ankerspeicher entfernen, damit sie in zukünftigen Sitzungen nicht mehr verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="8d31c-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![Raumanker: Entfernen](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="8d31c-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8d31c-125">See also</span></span>
* [<span data-ttu-id="8d31c-126">Raumanker</span><span class="sxs-lookup"><span data-stu-id="8d31c-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="8d31c-127">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="8d31c-127">Coordinate systems</span></span>](coordinate-systems.md)
