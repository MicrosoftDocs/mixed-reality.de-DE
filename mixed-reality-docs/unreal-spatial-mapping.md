---
title: Räumliche Abbildung in Unreal
description: Leitfaden für die Verwendung der räumlichen Abbildung in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, räumliche Abbildung
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720406"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="f9432-104">Räumliche Abbildung in Unreal</span><span class="sxs-lookup"><span data-stu-id="f9432-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f9432-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f9432-105">Overview</span></span>
<span data-ttu-id="f9432-106">Die räumliche Abbildung ermöglicht es, durch Anzeigen der die HoloLens umgebenden Welt Objekte auf Oberflächen in der physischen Welt zu platzieren. Dadurch erscheinen Hologramme für den Benutzer realer.</span><span class="sxs-lookup"><span data-stu-id="f9432-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="f9432-107">Die räumliche Abbildung verankert darüber hinaus Objekte in der Welt des Benutzers und nutzt dazu Tiefeninformationen der realen Welt. Dies hilft dabei, den Benutzer zu überzeugen, dass sich die betreffenden Hologramme tatsächlich in seinem Bereich befinden; frei im Raum schwebende oder sich mit dem Benutzer bewegende Hologramme fühlen sich weniger real an.</span><span class="sxs-lookup"><span data-stu-id="f9432-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="f9432-108">Wann immer es möglich ist, sollten Sie Elemente platzieren, um das Wohlbefinden des Benutzers zu steigern.</span><span class="sxs-lookup"><span data-stu-id="f9432-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="f9432-109">Weitere Informationen zur Qualität der räumlichen Abbildung, Platzierung, Verdeckung, Rendering und mehr finden Sie im Dokument [Räumliche Abbildung](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f9432-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="f9432-110">Aktivieren der räumlichen Abbildung</span><span class="sxs-lookup"><span data-stu-id="f9432-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="f9432-111">So aktivieren Sie die räumliche Abbildung in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f9432-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="f9432-112">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), und scrollen Sie zum Abschnitt **Platforms** (Plattformen) herunter.</span><span class="sxs-lookup"><span data-stu-id="f9432-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="f9432-113">Wählen Sie **HoloLens** aus, und aktivieren Sie **Spatial Perception** (Räumliche Wahrnehmung).</span><span class="sxs-lookup"><span data-stu-id="f9432-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="f9432-114">So abonnieren Sie räumliche Abbildung und debuggen das **MRMesh** in einem HoloLens-Spiel:</span><span class="sxs-lookup"><span data-stu-id="f9432-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="f9432-115">Öffnen Sie die **ARSessionConfig**, und klappen Sie den Abschnitt **ARSettings > World Mapping** (Weltdarstellung) auf.</span><span class="sxs-lookup"><span data-stu-id="f9432-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="f9432-116">Aktivieren Sie **Generate Mesh Data from Tracked Geometry** (Daten des Gittermodells auf der Grundlage der nachverfolgten Geometrie generieren), wodurch das HoloLens-Plug-In angewiesen wird, mit dem asynchronen Abrufen von räumlichen Abbildungsdaten und ihrer Oberflächenzuordnung in Unreal mithilfe von **MRMesh** zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="f9432-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="f9432-117">Aktivieren Sie **Render Mesh Data in Wireframe** (Gittermodelldaten im Drahtmodell rendern), um einen weißen Drahtmodellumriss jedes Dreiecks im **MRMesh** darzustellen.</span><span class="sxs-lookup"><span data-stu-id="f9432-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Raumanker: Speicher bereit](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="f9432-119">Räumliche Abbildung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="f9432-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="f9432-120">Sie können die folgenden Parameter ändern, um das Laufzeitverhalten der räumlichen Abbildung zu ändern:</span><span class="sxs-lookup"><span data-stu-id="f9432-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="f9432-121">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie nach unten zum Abschnitt **Platforms** (Plattformen), und wählen Sie **HoloLens > Spatial Mapping** (HoloLens > Räumliche Abbildung) aus:</span><span class="sxs-lookup"><span data-stu-id="f9432-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Raumanker: Projekteinstellungen](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="f9432-123">**Max Triangles Per Cubic Meter** (Maximale Anzahl von Dreiecken pro Kubikmeter) dient zum Aktualisieren der Dichte der Dreiecke im Gitter der räumlichen Abbildung.</span><span class="sxs-lookup"><span data-stu-id="f9432-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="f9432-124">**Spatial Meshing Volume Size** (Volumengröße des räumlichen Gitters) dient zum Angeben der Größe des Würfels, der den Spieler umgibt, um Daten der räumlichen Abbildung zu rendern und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f9432-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="f9432-125">Im Falle einer großen Anwendungslaufzeitumgebung muss dieser Wert ggf. hoch sein, um dem realen Raum gerecht zu werden.</span><span class="sxs-lookup"><span data-stu-id="f9432-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="f9432-126">Dagegen kann dieser Wert kleiner sein, wenn die Anwendung lediglich Hologramme auf Oberflächen in der unmittelbareren Umgebung des Benutzers platzieren muss.</span><span class="sxs-lookup"><span data-stu-id="f9432-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="f9432-127">Wenn sich der Benutzer in der Umgebung bewegt, bewegt sich das Volumen der räumlichen Abbildung mit ihm mit.</span><span class="sxs-lookup"><span data-stu-id="f9432-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="f9432-128">Arbeiten mit MRMesh</span><span class="sxs-lookup"><span data-stu-id="f9432-128">Working with MRMesh</span></span>
<span data-ttu-id="f9432-129">So erhalten Sie zur Laufzeit Zugriff auf das **MRMesh**:</span><span class="sxs-lookup"><span data-stu-id="f9432-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="f9432-130">Fügen Sie einem Blaupausenakteur eine **ARTrackableNotify**-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="f9432-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Raumanker: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="f9432-132">Wählen Sie die **ARTrackableNotify**-Komponente aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf.</span><span class="sxs-lookup"><span data-stu-id="f9432-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="f9432-133">Klicken Sie auf die Schaltfläche **+** für die Ereignisse, die Sie überwachen möchten.</span><span class="sxs-lookup"><span data-stu-id="f9432-133">Click the **+** button on the events you want to monitor.</span></span> 

![Raumanker: Ereignisse](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="f9432-135">In diesem Fall wird das Ereignis **On Add Tracked Geometry** überwacht, das nach gültigen Gittermodellen der Realumgebung sucht, die mit Daten der räumlichen Abbildung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="f9432-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="f9432-136">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="f9432-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="f9432-137">Sie können das Material des Gittermodells im Ereignisdiagramm der Blaupause oder in C++ ändern.</span><span class="sxs-lookup"><span data-stu-id="f9432-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="f9432-138">Auf dem Screenshot unten ist die Route der Blaupause dargestellt:</span><span class="sxs-lookup"><span data-stu-id="f9432-138">The screenshot below shows the Blueprint route:</span></span> 

![Raumanker: Beispiel](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="f9432-140">In C++ können Sie den `OnTrackableAdded`-Delegat abonnieren, um die `ARTrackedGeometry` abzurufen, sobald sie verfügbar ist, wie im Code unten zu sehen.</span><span class="sxs-lookup"><span data-stu-id="f9432-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f9432-141">Die build.cs-Datei des Projekts **MUSS** **AugmentedReality** in der Liste **PublicDependencyModuleNames** aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f9432-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="f9432-142">Dies schließt **ARBlueprintLibrary.h** und **MRMeshComponent.h** ein, mit deren Hilfe Sie die **MRMesh**-Komponente von **UARTrackedGeometry** untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="f9432-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![Raumanker: C++-Beispielcode](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="f9432-144">Räumliche Abbildung ist nicht der einzige Datentyp, der mithilfe von **ARTrackedGeometries** dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="f9432-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="f9432-145">Sie können überprüfen, ob `EARObjectClassification` den Wert `World` aufweist, was bedeutet, dass es sich um Geometriedaten der räumlichen Abbildung handelt.</span><span class="sxs-lookup"><span data-stu-id="f9432-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="f9432-146">Für Aktualisierungs- und Entfernungsereignisse stehen ähnliche Delegaten zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="f9432-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="f9432-147">`AddOnTrackableRemovedDelegate_Handle`.</span><span class="sxs-lookup"><span data-stu-id="f9432-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="f9432-148">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="f9432-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9432-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f9432-149">See also</span></span>
* [<span data-ttu-id="f9432-150">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="f9432-150">Spatial mapping</span></span>](spatial-mapping.md)
