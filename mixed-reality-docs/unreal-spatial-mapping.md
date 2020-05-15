---
title: Räumliche Abbildung in Unreal
description: Leitfaden für die Verwendung der räumlichen Abbildung in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, räumliche Abbildung
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840079"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="a827d-104">Räumliche Abbildung in Unreal</span><span class="sxs-lookup"><span data-stu-id="a827d-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="a827d-105">Im Unreal-Editor muss unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Capabilities“ (Funktionen) die Funktion für die räumliche Wahrnehmung (Spatial Perception) aktiviert sein, um die räumliche Abbildung für HoloLens verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="a827d-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="a827d-106">Wenn Sie die räumliche Abbildung in einem HoloLens-Spiel verwenden möchten, aktivieren Sie in „ARSessionConfig“ die Option „Generate Mesh Data from Tracked Geometry“ (Gitterdaten auf der Grundlage der nachverfolgten Geometrie generieren).</span><span class="sxs-lookup"><span data-stu-id="a827d-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="a827d-107">Daraufhin werden vom HoloLens-Plug-In asynchron räumliche Abbildungsdaten abgerufen und über „MRMesh“ für Unreal verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="a827d-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![Raumanker: Speicher bereit](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="a827d-109">Aktivieren Sie zum Anzeigen einer Debugvisualisierung des Gitters der räumlichen Abbildung das Kontrollkästchen „Render Mesh Data in Wireframe“ (Gitterdaten in Drahtmodell rendern) in „ARSessionConfig“, um eine weiße Drahtmodellkontur jedes Dreiecks in „MRMesh“ anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a827d-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="a827d-110">Unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Spatial Mapping“ (Räumliche Abbildung) können folgende Parameter geändert werden, um das Laufzeitverhalten der räumlichen Abbildung zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="a827d-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![Raumanker: Projekteinstellungen](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="a827d-112">„Max Triangles Per Cubic Meter“ (Maximale Anzahl von Dreiecken pro Kubikmeter) dient zum Aktualisieren der Dichte der Dreiecke im Gitter der räumlichen Abbildung.</span><span class="sxs-lookup"><span data-stu-id="a827d-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="a827d-113">„Spatial Meshing Volume Size“ (Volumengröße des räumlichen Gitters) dient zum Angeben der Größe des Würfels, der den Spieler umgibt, um Daten der räumlichen Abbildung zu rendern und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a827d-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="a827d-114">Im Falle einer großen Anwendungslaufzeitumgebung muss der Wert in diesem Feld ggf. hoch sein, um dem realen Raum gerecht zu werden.</span><span class="sxs-lookup"><span data-stu-id="a827d-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="a827d-115">Müssen von der Anwendung dagegen lediglich Hologramme auf Oberflächen in der unmittelbareren Umgebung des Benutzers platziert werden, kann in diesem Feld ein niedrigerer Wert verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a827d-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="a827d-116">Wenn sich der Benutzer in der Umgebung bewegt, bewegt sich das Volumen der räumlichen Abbildung mit ihm mit.</span><span class="sxs-lookup"><span data-stu-id="a827d-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="a827d-117">Um zur Laufzeit auf „MRMesh“ zugreifen zu können, fügen Sie zunächst einem Blaupausenakteur eine in AR nachverfolgbare Benachrichtigungskomponente hinzu:</span><span class="sxs-lookup"><span data-stu-id="a827d-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![Raumanker: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="a827d-119">Navigieren Sie dann zu den Details der Komponente, und klicken Sie auf die grüne Plusschaltfläche (+) für die zu überwachenden Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="a827d-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![Raumanker: Ereignisse](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="a827d-121">In diesem Fall überwachen wir das Ereignis „On Add Tracked Geometry“ (Beim Hinzufügen von nachverfolgter Geometrie), um nach gültigen Weltgittern zu suchen, die Daten der räumlichen Abbildung entsprechen, und ändern das Material des Gitters:</span><span class="sxs-lookup"><span data-stu-id="a827d-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![Raumanker: Beispiel](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="a827d-123">In C++ kann der Delegat „OnTrackableAdded“ abonniert werden, um die in AR nachverfolgte Geometrie (ARTrackedGeometry) abzurufen, sobald sie verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a827d-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="a827d-124">Für Aktualisierungs- und Entfernungsereignisse stehen ähnliche Delegaten zur Verfügung: „AddOnTrackableUpdatedDelegate_Handle“ und „AddOnTrackableRemovedDelegate_Handle“.</span><span class="sxs-lookup"><span data-stu-id="a827d-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![Raumanker: C++-Beispielcode](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="a827d-126">„build.cs“ des Projekts muss „AugmentedReality“ in der Liste „PublicDependencyModuleNames“ enthalten, um „ARBlueprintLibrary.h“ und „MRMesh“ für die Untersuchung der MRMesh-Komponente von „UARTrackedGeometry“ einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="a827d-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="a827d-127">Da die räumliche Abbildung nicht der einzige Datentyp ist, der über „ARTrackedGeometries“ verfügbar gemacht wird, vergewissern wir uns zunächst, dass „EARObjectClassification“ auf „World“ festgelegt ist. Dadurch wird angegeben, dass es sich hierbei um eine Geometrie der räumlichen Abbildung handelt.</span><span class="sxs-lookup"><span data-stu-id="a827d-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="a827d-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a827d-128">See also</span></span>
* [<span data-ttu-id="a827d-129">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="a827d-129">Spatial mapping</span></span>](spatial-mapping.md)
