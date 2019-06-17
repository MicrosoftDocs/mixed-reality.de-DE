---
title: Räumliche Zuordnung in Unity
description: Rendern, und mit der realen Welt Geometrie um Sie in Unity Konflikt zu geraten.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Zuordnung, Renderer, "collider", Netz, Überprüfung, Komponente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148647"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="ec46c-104">Räumliche Zuordnung in Unity</span><span class="sxs-lookup"><span data-stu-id="ec46c-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="ec46c-105">In diesem Thema wird beschrieben, wie Sie mit [räumliche Zuordnung](spatial-mapping.md) in Ihrem Unity-Projekt abrufen Dreieckgitter, die die Flächen in die Welt um ein HoloLens-Gerät, für die Platzierung, verdecken, Raum Analyse und mehr darstellen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="ec46c-106">Unity bietet vollständige Unterstützung für räumliche Zuordnung, die für Entwickler auf folgende Weise verfügbar gemacht wird:</span><span class="sxs-lookup"><span data-stu-id="ec46c-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="ec46c-107">Räumliche Zuordnung von Komponenten, die in der MixedRealityToolkit verfügbar, geben Sie die einen einfachen und schnellen Pfad für den Einstieg in die räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ec46c-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="ec46c-108">Räumliche Zuordnung von Low-Level-APIs, die vollständigen gewähren steuern und höher entwickelte Anwendung spezifische Anpassung aktivieren</span><span class="sxs-lookup"><span data-stu-id="ec46c-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="ec46c-109">Um räumliche Zuordnung in Ihrer app verwenden zu können, muss die SpatialPerception-Funktion in Ihrem AppxManifest festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="ec46c-110">Festlegen der SpatialPerception-Funktion</span><span class="sxs-lookup"><span data-stu-id="ec46c-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="ec46c-111">Damit eine app, räumliche Zuordnungsdaten zu verwenden muss die SpatialPerception-Funktion aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="ec46c-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="ec46c-112">Informationen zum Aktivieren der SpatialPerception-Funktion:</span><span class="sxs-lookup"><span data-stu-id="ec46c-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="ec46c-113">Öffnen Sie im Unity-Editor, der **"Player Settings"** Bereich (Bearbeiten > Projekteinstellungen > Player)</span><span class="sxs-lookup"><span data-stu-id="ec46c-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="ec46c-114">Klicken Sie auf die **"Windows Store"** Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ec46c-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="ec46c-115">Erweitern Sie **"Veröffentlichungseinstellungen"** und überprüfen Sie die **"SpatialPerception"** -Funktion in der **"Funktionen"** Liste</span><span class="sxs-lookup"><span data-stu-id="ec46c-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="ec46c-116">Beachten Sie, dass wenn Sie bereits Ihr Unity-Projekt in Visual Studio-Projektmappe exportiert haben, Sie die zum Exportieren in einen neuen Ordner oder manuell müssen [legen Sie diese Funktion in die appxmanifest-Datei in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="ec46c-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="ec46c-117">Räumliche Zuordnung erfordert außerdem eine "maxversiontested", der mindestens 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="ec46c-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="ec46c-118">In Visual Studio, klicken Sie mit der rechten Maustaste auf **"Package.appxmanifest"** im Projektmappen-Explorer, und wählen **Anzeigecode**</span><span class="sxs-lookup"><span data-stu-id="ec46c-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="ec46c-119">Suchen Sie die Zeile anzugeben, **TargetDeviceFamily** , und ändern Sie **"maxversiontested" = "10.0.10240.0"** zu **"maxversiontested" = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="ec46c-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="ec46c-120">**Speichern Sie** der Datei "Package.appxmanifest".</span><span class="sxs-lookup"><span data-stu-id="ec46c-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="ec46c-121">Erste Schritte mit Komponenten der Unity-integrierte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ec46c-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="ec46c-122">Unity bietet 2 Komponenten für die räumliche Zuordnung auf einfache Weise in Ihrer app hinzuzufügen **räumliche Zuordnung Renderer** und **räumliche Zuordnung "collider"** .</span><span class="sxs-lookup"><span data-stu-id="ec46c-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="ec46c-123">Räumliche Zuordnung Renderer</span><span class="sxs-lookup"><span data-stu-id="ec46c-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="ec46c-124">Der räumliche Zuordnung-Renderer ermöglicht die Visualisierung des Netzes räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="ec46c-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Räumliche Zuordnung-Renderer in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="ec46c-126">Räumliche Zuordnung "collider"</span><span class="sxs-lookup"><span data-stu-id="ec46c-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="ec46c-127">Die räumliche Zuordnung "collider" holographic Inhalt (oder Zeichen) ermöglicht Interaktion mit dem Netz räumliche Zuordnung, wie z. B. Physik.</span><span class="sxs-lookup"><span data-stu-id="ec46c-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Räumliche Zuordnung "collider" in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ec46c-129">Verwenden die Komponenten für die integrierte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ec46c-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="ec46c-130">Sie können beide Komponenten zu Ihrer app hinzufügen, wenn Sie sowohl visualisieren und physische interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ec46c-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="ec46c-131">So verwenden Sie diese beiden Komponenten in Ihrer Unity-app</span><span class="sxs-lookup"><span data-stu-id="ec46c-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="ec46c-132">Wählen Sie ein "gameobject" in der Mitte des Bereichs, in dem Sie räumliche Oberfläche Gitter erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="ec46c-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="ec46c-133">Im Inspektor-Fenster **Add Component** > **XR** > **räumliche Zuordnung "collider"**  oder **räumlich Zuordnung Renderer**.</span><span class="sxs-lookup"><span data-stu-id="ec46c-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="ec46c-134">Finden Sie weitere Informationen zur Verwendung dieser Komponenten unter den <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentationswebsite</a>.</span><span class="sxs-lookup"><span data-stu-id="ec46c-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ec46c-135">Darum geht, über die Komponenten für die integrierte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="ec46c-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="ec46c-136">Diese Komponenten erleichtern die Drag & Drop einfach zum Einstieg in die räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="ec46c-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="ec46c-137"> Wenn Sie fortfahren möchten, gibt es zwei Hauptmethoden, um zu untersuchen:</span><span class="sxs-lookup"><span data-stu-id="ec46c-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="ec46c-138">Um Ihre eigene Low-Level-Mesh-Verarbeitung durchführen zu können, finden Sie im Abschnitt auf niedriger Ebene räumliche Zuordnung zum Skript zur API.</span><span class="sxs-lookup"><span data-stu-id="ec46c-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="ec46c-139">Um auf höherer Ebene Mesh-Analyse durchzuführen, finden Sie im Abschnitt über die Bibliothek SpatialUnderstanding in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="ec46c-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="ec46c-140">Der Low-Level Unity räumliche Zuordnung-API</span><span class="sxs-lookup"><span data-stu-id="ec46c-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="ec46c-141">Wenn Sie mehr Kontrolle benötigen, als Sie von den Komponenten räumliche Zuordnung-Renderer und räumliche Zuordnung "collider" erhalten, können Sie die Low-Level, räumliche Zuordnung Skript APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="ec46c-142">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="ec46c-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ec46c-143">**Typen**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="ec46c-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="ec46c-144">Im folgenden finden einen Überblick über die vorgeschlagenen Flow für eine Anwendung, die räumliche Zuordnung APIs verwendet.</span><span class="sxs-lookup"><span data-stu-id="ec46c-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="ec46c-145">Richten Sie die SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="ec46c-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="ec46c-146">Instanziieren Sie ein SurfaceObserver-Objekt für jede Region anwendungsdefinierte des Speicherplatzes, der Sie räumliche Zuordnung von Daten für benötigen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="ec46c-147">Geben Sie die Region des Speicherplatzes, der jedes Objekt SurfaceObserver Daten für die durch Aufrufen von entweder SetVolumeAsSphere SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox oder SetVolumeAsFrustum bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="ec46c-148">Sie können die Region des Speicherplatzes in der Zukunft neu definieren, durch den Aufruf einer der folgenden Methoden einfach erneut aus.</span><span class="sxs-lookup"><span data-stu-id="ec46c-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="ec46c-149">Wenn Sie SurfaceObserver.Update() aufrufen, müssen Sie einen Handler für jede räumliche Fläche in der SurfaceObservers Region des Speicherplatzes bereitstellen, die das räumliche Zuordnung System neue Informationen für.</span><span class="sxs-lookup"><span data-stu-id="ec46c-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="ec46c-150">Der Handler empfängt, für eine räumliche Oberfläche:</span><span class="sxs-lookup"><span data-stu-id="ec46c-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="ec46c-151">Behandeln von Surface-Änderungen</span><span class="sxs-lookup"><span data-stu-id="ec46c-151">Handling Surface Changes</span></span>

<span data-ttu-id="ec46c-152">Es gibt mehrere main Fälle zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="ec46c-152">There are several main cases to handle.</span></span> <span data-ttu-id="ec46c-153">Hinzugefügt und aktualisiert die gleich verwenden kann, codieren, Pfad "und" entfernt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="ec46c-154">In den Fällen hinzugefügte und aktualisierte im Beispiel wir hinzufügen oder abrufen, das "gameobject" ein, diese aus dem Wörterbuch mesh, erstellen eine SurfaceData-Struktur mit der erforderlichen Komponenten, und rufen Sie dann RequestMeshDataAsync zum Auffüllen der "gameobject" mit den Daten des Mesh, und Positionieren Sie in der Szene.</span><span class="sxs-lookup"><span data-stu-id="ec46c-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="ec46c-155">Im Fall entfernt, wenn wir das dieses Mesh darstellt, aus dem Wörterbuch "gameobject" zu entfernen und zerstören sie.</span><span class="sxs-lookup"><span data-stu-id="ec46c-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="ec46c-156">Behandlung von Daten bereit</span><span class="sxs-lookup"><span data-stu-id="ec46c-156">Handling Data Ready</span></span>

<span data-ttu-id="ec46c-157">Der OnDataReady Handler empfängt ein SurfaceData-Objekt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="ec46c-158">Die WorldAnchor, MeshFilter und (optional) MeshCollider die darin enthaltenen Objekte repräsentieren den aktuellen Status der zugehörigen räumliche Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="ec46c-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="ec46c-159">Führen Sie optional eine Analyse und/oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Daten durch den Zugriff auf die Mesh-Member des Objekts MeshFilter Mesh.</span><span class="sxs-lookup"><span data-stu-id="ec46c-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="ec46c-160">Die räumliche Oberfläche mit dem aktuellen Netz zu rendern, und (optional) für Physik Kollisionen und Raycasts verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="ec46c-161">Es ist wichtig, um sicherzustellen, dass der Inhalt der SurfaceData nicht null sind.</span><span class="sxs-lookup"><span data-stu-id="ec46c-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="ec46c-162">Starten von updates</span><span class="sxs-lookup"><span data-stu-id="ec46c-162">Start processing on updates</span></span>

<span data-ttu-id="ec46c-163">SurfaceObserver.Update() sollte auf eine Verzögerung, die nicht für jedes Bild aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="ec46c-164">Mesh-Analyse auf höherer Ebene: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="ec46c-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="ec46c-165">Die <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> ist eine Sammlung von hilfreich dienstprogrammcodes für holographic Entwicklung, die auf die holographic Unity-APIs basieren.</span><span class="sxs-lookup"><span data-stu-id="ec46c-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="ec46c-166">Räumliche verstehen</span><span class="sxs-lookup"><span data-stu-id="ec46c-166">Spatial Understanding</span></span>

<span data-ttu-id="ec46c-167">Beim Platzieren von Hologramme in der realen Welt ist es oft wünschenswert, wechseln über die räumliche Zuordnung mesh und Ebenen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="ec46c-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="ec46c-168">Bei der Platzierung Prozedural abgeschlossen ist, ist ein höheres Maß an die Umwelt Verständnis wünschenswert.</span><span class="sxs-lookup"><span data-stu-id="ec46c-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="ec46c-169">Dies erfordert normalerweise, Entscheidungen darüber, was Floor, Ceiling und Wänden ist.</span><span class="sxs-lookup"><span data-stu-id="ec46c-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="ec46c-170">Darüber hinaus die Möglichkeit, für einen Satz von platzierungseinschränkungen zum Festlegen der am häufigsten gewünscht physischen Standorten für holographic Objekte zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="ec46c-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="ec46c-171">Bei der Entwicklung von Young Conker und Fragmente konfrontiert Asobo Studios diese Problem Head-Datei auf einem Solver Raum zu diesem Zweck entwickeln.</span><span class="sxs-lookup"><span data-stu-id="ec46c-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="ec46c-172">Für jede dieser Spiele spielen bestimmte Anforderungen wurde, aber sie räumliche Verständnis kerntechnologie freigegeben.</span><span class="sxs-lookup"><span data-stu-id="ec46c-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="ec46c-173">Die HoloToolkit.SpatialUnderstanding Bibliothek kapselt diese Technologie ermöglicht, dass Sie schnell suchen Leerzeichen an den Wänden, direkten-Objekten, auf die Obergrenze identifizieren platziert für Zeichen, das sich befinden und unzählige andere räumliche Grundlegendes zu Abfragen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="ec46c-174">Alle des Quellcodes enthalten ist, können Sie es an Ihre Anforderungen anpassen und Ihrer Verbesserungen mit der Community teilen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="ec46c-175">Der Code für die C++ Solver umschlossen in eine Dll für UWP und Unity mit einen Abfall der MixedRealityToolkit enthaltenen Prefab verfügbar gemacht wurde.</span><span class="sxs-lookup"><span data-stu-id="ec46c-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="ec46c-176">Grundlegendes zur-Module</span><span class="sxs-lookup"><span data-stu-id="ec46c-176">Understanding Modules</span></span>

<span data-ttu-id="ec46c-177">Es gibt drei primäre Schnittstellen, die vom Modul offengelegte: Topologie für einfache Oberfläche und räumliche Abfragen, Form für die objekterkennung und der Solver Objekt Platzierung für die Platzierung Objektsätze Einschränkung basierend.</span><span class="sxs-lookup"><span data-stu-id="ec46c-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="ec46c-178">Jedes davon wird unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ec46c-178">Each of these is described below.</span></span> <span data-ttu-id="ec46c-179">Zusätzlich zu den drei primäre Modulschnittstellen eine Chow Umwandlung-Schnittstelle kann verwendet werden, um die markierte Oberfläche Typen abzurufen, und einem benutzerdefinierten wasserdichte Playspace Mesh werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="ec46c-180">Chow Umwandlung</span><span class="sxs-lookup"><span data-stu-id="ec46c-180">Ray Casting</span></span>

<span data-ttu-id="ec46c-181">Nachdem Raum gescannt und abgeschlossen wurde, werden die Bezeichnungen für Oberflächen wie die Floor, Ceiling und Wände intern generiert.</span><span class="sxs-lookup"><span data-stu-id="ec46c-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="ec46c-182">Der "PlayspaceRaycast"-Funktion nimmt ein Strahl und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche verursacht einen Konflikt, und wenn dies der Fall, die Informationen, die dann in Form einer "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="ec46c-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="ec46c-183">Die Raycast wird intern für die berechnete 8 cm hoch drei Voxel Darstellung der Playspace berechnet.</span><span class="sxs-lookup"><span data-stu-id="ec46c-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="ec46c-184">Jede Voxel enthält einen Satz von Surface-Elementen mit verarbeiteten Topologiedaten (auch bekannt als Surfels).</span><span class="sxs-lookup"><span data-stu-id="ec46c-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="ec46c-185">Die in der Zelle überschneidungen Voxel enthaltenen Surfels verglichen werden, und die beste Übereinstimmung verwendet, um die Topologieinformationen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="ec46c-186">Diese Topologiedaten enthalten die Bezeichnung in Form von der Enumeration "SurfaceTypes" als auch die Oberfläche der überschneidungen Oberfläche zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ec46c-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="ec46c-187">Im Unity-Beispiel wird der Cursor jeder Frame ein Strahl umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="ec46c-188">Zunächst anhand von Unity-collider.</span><span class="sxs-lookup"><span data-stu-id="ec46c-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="ec46c-189">Zweitens: für das Verständnis des Moduls-Welt-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="ec46c-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="ec46c-190">Und schließlich erneut UI-Elementen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-190">And finally, again UI elements.</span></span> <span data-ttu-id="ec46c-191">In dieser Anwendung UI ruft Priorität ab, als Nächstes das Ergebnis verstehen und die Unity-collider.</span><span class="sxs-lookup"><span data-stu-id="ec46c-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="ec46c-192">Die SurfaceType wird als Text neben dem Cursor gemeldet.</span><span class="sxs-lookup"><span data-stu-id="ec46c-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="ec46c-193">![Surface-Typ wird neben dem Cursor bezeichnet.](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec46c-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="ec46c-194">*Surface-Typ wird neben dem Cursor bezeichnet.*</span><span class="sxs-lookup"><span data-stu-id="ec46c-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="ec46c-195">Abfragen der Topologie</span><span class="sxs-lookup"><span data-stu-id="ec46c-195">Topology Queries</span></span>

<span data-ttu-id="ec46c-196">In der DLL behandelt Topologie-Manager die Bezeichnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="ec46c-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="ec46c-197">Wie bereits erwähnt, wird ein Großteil der Daten in Surfels, ein Volume Voxel enthaltenen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ec46c-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="ec46c-198">Darüber hinaus wird die Struktur "PlaySpaceInfos" zum Speichern von Informationen zu den Playspace, einschließlich der Welt, Ausrichtung (Weitere Einzelheiten hierzu finden Sie nachstehend), Floor und Ceiling Höhe.</span><span class="sxs-lookup"><span data-stu-id="ec46c-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="ec46c-199">Heuristik beim Ermitteln der werden verwendet, um zu bestimmen, Floor, Ceiling und Wänden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="ec46c-200">Beispielsweise gilt die größte und niedrigste horizontale Oberfläche mit mehr als 1 m2 Oberfläche den Boden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="ec46c-201">Beachten Sie, dass der Pfad "Kamera" während des Scanvorgangs auch in diesem Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ec46c-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="ec46c-202">Eine Teilmenge der Abfragen, die von der Topologie-Manager verfügbar gemacht werden über die Dll bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="ec46c-203">Die verfügbar gemachten Topologie-Abfragen sind wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="ec46c-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="ec46c-204">Alle Abfragen verfügt über einen Satz von Parametern, die spezifisch für den Abfragetyp.</span><span class="sxs-lookup"><span data-stu-id="ec46c-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="ec46c-205">Im folgenden Beispiel gibt den Benutzer, die minimale Höhe und Breite der gewünschte Volume, minimale Platzierung Höhe über dem Boden und die Mindestmenge an sicherheitsbestätigung vor dem Volume.</span><span class="sxs-lookup"><span data-stu-id="ec46c-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="ec46c-206">Alle Messungen sind in Meter.</span><span class="sxs-lookup"><span data-stu-id="ec46c-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="ec46c-207">Jeder dieser Abfragen akzeptiert ein vorab zugeordnete Array von "TopologyResult"-Strukturen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="ec46c-208">Der Parameter "LocationCount" gibt die Länge des übergebenen Arrays an.</span><span class="sxs-lookup"><span data-stu-id="ec46c-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="ec46c-209">Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="ec46c-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="ec46c-210">Diese Zahl ist niemals größer als der übergebene Parameter für "LocationCount".</span><span class="sxs-lookup"><span data-stu-id="ec46c-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="ec46c-211">Die "TopologyResult" enthält die zentrierte Textposition des zurückgegebenen Volumes, die zugänglichen Richtung (d. h. normal), und die Abmessungen des Bereich gefunden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="ec46c-212">Beachten Sie, dass in der Unity-Beispiel, jeder dieser Abfragen sich auf eine Schaltfläche in der virtuellen Benutzeroberflächen-Panel verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="ec46c-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="ec46c-213">Das Beispiel schwer-codes die Parameter für jede dieser Abfragen für Sie geeignete Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="ec46c-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="ec46c-214">Der Beispielcode für weitere Beispiele finden Sie in SpaceVisualizer.cs.</span><span class="sxs-lookup"><span data-stu-id="ec46c-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="ec46c-215">Shape-Abfragen</span><span class="sxs-lookup"><span data-stu-id="ec46c-215">Shape Queries</span></span>

<span data-ttu-id="ec46c-216">Innerhalb der Dll verwendet der Shape-Analyzer ("ShapeAnalyzer_W") den Topologie-Analyzer für den Abgleich von benutzerdefinierter Formen, die vom Benutzer definiert.</span><span class="sxs-lookup"><span data-stu-id="ec46c-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="ec46c-217">Im Unity-Beispiel definiert einen Satz von Formen und stellt die Ergebnisse, über das Abfragemenü mit in-app-, auf die Registerkarte "Form". Die Absicht ist, dass der Benutzer kann eigene Form Objektabfragen zu definieren, und stellen diese bei Bedarf von ihrer Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="ec46c-218">Beachten Sie, dass die Form-Analyse auf nur horizontale Oberflächen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="ec46c-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="ec46c-219">Ein Sofa, wird z. B. durch die Flatfile-Arbeitsplatz-Oberfläche und flache Anfang den Garten wieder definiert.</span><span class="sxs-lookup"><span data-stu-id="ec46c-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="ec46c-220">Shape-Abfrage sucht nach zwei Oberflächen von einer bestimmten Größe, Höhe und Aspekt-Bereich mit den beiden Oberflächen ausgerichtet und verbunden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="ec46c-221">Verwenden die APIs Terminologie, im Sofa Arbeitsplatz und Back sind Shape-Komponenten, und der ausrichtungsanforderungen werden Beschränkungen hinsichtlich der Form Komponenten.</span><span class="sxs-lookup"><span data-stu-id="ec46c-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="ec46c-222">Eine Beispielabfrage, die in der Unity-Beispiel (ShapeDefinition.cs), "sittable" Objekte definiert, lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ec46c-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="ec46c-223">Jedes Shape-Abfrage wird definiert, indem eine Reihe von Form-Komponenten, jeweils eine Reihe von Beschränkungen hinsichtlich der Komponenten und einer Reihe von Form-Einschränkungen das Auflisten von Abhängigkeiten zwischen den Komponenten.</span><span class="sxs-lookup"><span data-stu-id="ec46c-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="ec46c-224">Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponente-Definition und keine Einschränkungen der Form zwischen Komponenten, (wie es nur eine Komponente ist).</span><span class="sxs-lookup"><span data-stu-id="ec46c-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="ec46c-225">Im Gegensatz dazu verfügt über die Form Sofa, zwei Shape-Komponenten und Einschränkungen für vier Form.</span><span class="sxs-lookup"><span data-stu-id="ec46c-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="ec46c-226">Beachten Sie, dass Komponenten anhand ihres Indexes in der Liste der Komponenten des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="ec46c-227">Wrapperfunktionen werden zur einfachen Erstellung von Definitionen für benutzerdefinierte Form, die im Unity-Modul bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="ec46c-228">Die vollständige Liste der Komponente und Form-Einschränkungen finden Sie in "SpatialUnderstandingDll.cs" in der "ShapeComponentConstraint" und "ShapeConstraint" Strukturen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="ec46c-229">![Rechteckige Form wird auf dieser Oberfläche gefunden.](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec46c-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="ec46c-230">*Rechteckige Form wird auf dieser Oberfläche gefunden.*</span><span class="sxs-lookup"><span data-stu-id="ec46c-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="ec46c-231">Die Platzierung Solver Objekt</span><span class="sxs-lookup"><span data-stu-id="ec46c-231">Object Placement Solver</span></span>

<span data-ttu-id="ec46c-232">Der Objekt-Solver Platzierung kann verwendet werden, um ideal Orte im physischen Raum platzieren Ihrer Objekte zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="ec46c-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="ec46c-233">Der Solver findet, dass die besten Speicherort, der die Objektregeln und Einschränkungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="ec46c-234">Darüber hinaus beibehalten Objektabfragen, bis das Objekt, mit "Solver_RemoveObject entfernt wird" oder "Solver_RemoveAllObjects" aufrufen, sodass Platzierung Multi-Objekts eingeschränkte.</span><span class="sxs-lookup"><span data-stu-id="ec46c-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="ec46c-235">Platzierung Objects-Abfragen bestehen aus drei Teilen: die Platzierungstyp mit Parametern, eine Liste der Regeln und eine Liste der Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="ec46c-236">Verwenden Sie zum Ausführen einer Abfrage, die folgende API ein.</span><span class="sxs-lookup"><span data-stu-id="ec46c-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="ec46c-237">Diese Funktion akzeptiert ein Objektname, Platzierungsdefinition und eine Liste von Regeln und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="ec46c-238">Die C# Wrapper Konstruktion Stellt Hilfsfunktionen bereit, um die Regel oder Einschränkung Erstellung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="ec46c-239">Die Platzierungsdefinition enthält den Abfragetyp – d. h. eine der folgenden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="ec46c-240">Alle Platzierungstypen, hat es sich um einen Satz von Parametern, die nur für den Typ.</span><span class="sxs-lookup"><span data-stu-id="ec46c-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="ec46c-241">Die Struktur "ObjectPlacementDefinition" enthält einen Satz von statischen Hilfsfunktionen für diese Definitionen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="ec46c-242">Um einer bestimmten Stelle ablegen ein Objekts auf dem Boden zu suchen, können Sie z. B. die folgende Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="ec46c-243">Öffentliche statische ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) neben die Platzierungstyp, können Sie einen Satz von Regeln und Einschränkungen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="ec46c-244">Regeln können nicht verletzt werden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-244">Rules cannot be violated.</span></span> <span data-ttu-id="ec46c-245">Mögliche Platzierung von Standorten, die den Typ und die Regeln zu erfüllen sind klicken Sie dann mit einem Satz an Einschränkungen optimiert, um den Speicherort für die optimale Platzierung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="ec46c-246">Alle Regeln und Einschränkungen kann von den Funktionen für die angegebene statische Erstellung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="ec46c-247">Eine Beispiel-Regel und die Einschränkung der Konstruktorfunktion wird unten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="ec46c-248">Die unter-Objekt für eine Umgebung zum Einfügen eines Cubes Hälfte Verbrauchseinheit am Rand einer Oberfläche, von anderen Objekten zuvor platzieren und in der Nähe der Mitte des Raums Platzierung Abfrage sucht.</span><span class="sxs-lookup"><span data-stu-id="ec46c-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="ec46c-249">Bei Erfolg wird eine "ObjectPlacementResult"-Struktur, die mit der Platzierung, Dimensionen und die Ausrichtung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ec46c-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="ec46c-250">Darüber hinaus wird die Platzierung des Dll interne Liste der platzierten Objekte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="ec46c-251">Platzierung der nachfolgenden Abfragen werden dieses Objekt zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="ec46c-252">Die Datei "LevelSolver.cs" in der Unity-Beispiel enthält weitere Beispiele für Abfragen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="ec46c-253">![Ergebnisse der objektplatzierung](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec46c-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="ec46c-254">*Abbildung 3: Die blauen Felder wie das Ergebnis von drei Ort auf Floor mit Abfragen, von der Kamera Position Regeln*</span><span class="sxs-lookup"><span data-stu-id="ec46c-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="ec46c-255">Bei der Lösung für die Platzierung-Speicherort, der mehrere Objekte, die für ein Szenario Ebene oder eine Anwendung erforderlich sind, lösen Sie zuerst unverzichtbaren und große Objekte zur Maximierung der der Wahrscheinlichkeit, die ein Leerzeichen befinden.</span><span class="sxs-lookup"><span data-stu-id="ec46c-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="ec46c-256">Platzierung Reihenfolge ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="ec46c-256">Placement order is important.</span></span> <span data-ttu-id="ec46c-257">Wenn das Objekt Platzierungen nicht gefunden wird, versuchen Sie es weniger eingeschränkte Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="ec46c-258">Eine Reihe von Konfigurationen ist entscheidend für die Unterstützung von Funktionen in vielen Konfigurationen von Platz.</span><span class="sxs-lookup"><span data-stu-id="ec46c-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="ec46c-259">Raum Scanningprozess</span><span class="sxs-lookup"><span data-stu-id="ec46c-259">Room Scanning Process</span></span>

<span data-ttu-id="ec46c-260">Zwar allgemein genug, um die Anforderungen die gesamte Palette von Problembereiche werden räumliche Zuordnung-Lösung durch die HoloLens ausgelegt ist, wurde das räumliche Verständnis-Modul erstellt, um die Anforderungen von zwei bestimmte Spiele zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="ec46c-261">Seine Lösung basiert auf einem bestimmten Prozess und eine Reihe von Annahmen, die im folgenden zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="ec46c-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="ec46c-262">Benutzergesteuerte Playspace "Zeichnen" – während der Überprüfungsphase, der Benutzer wechselt und sieht sich der Wiedergabe der Bedingungen, für die tatsächlich Zeichnen der Bereiche, die einbezogen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="ec46c-263">Das generierte Netz ist wichtig, Feedback von Benutzern bereitzustellen, während dieser Phase.</span><span class="sxs-lookup"><span data-stu-id="ec46c-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="ec46c-264">In geschlossenen Räumen home oder das Office-setup – der Abfrage, die Funktionen für flache Flächen und Wände rechtwinklig konzipiert sind.</span><span class="sxs-lookup"><span data-stu-id="ec46c-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="ec46c-265">Dies ist eine weiche Einschränkung.</span><span class="sxs-lookup"><span data-stu-id="ec46c-265">This is a soft limitation.</span></span> <span data-ttu-id="ec46c-266">Jedoch wird während der Überprüfungsphase, eine Analyse der primären Achse abgeschlossen, um das Netz Mosaik Haupt- und Nebenversionsnummern Achse zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="ec46c-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="ec46c-267">Der eingebundenen Datei SpatialUnderstanding.cs verwaltet den Scanvorgang-Phase.</span><span class="sxs-lookup"><span data-stu-id="ec46c-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="ec46c-268">Sie ruft die folgenden Funktionen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="ec46c-269">Scan Datenfluss durch das Verhalten "SpatialUnderstanding" gesteuert ruft InitScan, und klicken Sie dann auf UpdateScan jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="ec46c-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="ec46c-270">Wenn die Abfrage Statistiken angemessenen Coverage meldet, darf der Benutzer auf Airtap RequestFinish, um anzugeben, das Ende der Überprüfungsphase aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="ec46c-271">UpdateScan weiterhin aufgerufen werden, bis sie die Rückgabe ist der Wert gibt an, dass die Dll die Verarbeitung abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="ec46c-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="ec46c-272">Grundlegendes zu Netz</span><span class="sxs-lookup"><span data-stu-id="ec46c-272">Understanding Mesh</span></span>

<span data-ttu-id="ec46c-273">Grundlegendes zur Dll speichert intern die Playspace als ein Raster aus 8cm Größe Voxel Cubes.</span><span class="sxs-lookup"><span data-stu-id="ec46c-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="ec46c-274">Während des ersten Teils Scannen ist eine Hauptkomponente Analyse abgeschlossen, um zu bestimmen, die Achsen des Raums.</span><span class="sxs-lookup"><span data-stu-id="ec46c-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="ec46c-275">Sie speichert intern Voxel Speicherplatzes ausgerichtet, diese Achsen.</span><span class="sxs-lookup"><span data-stu-id="ec46c-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="ec46c-276">Ein Mesh wird ungefähr pro Sekunde generiert, mit dem Extrahieren der Isofläche aus dem Voxel Volume.</span><span class="sxs-lookup"><span data-stu-id="ec46c-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="ec46c-277">![Generierte Mesh erstellt, von dem Volume voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec46c-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="ec46c-278">*Generierte Mesh erstellt, von dem Volume voxel*</span><span class="sxs-lookup"><span data-stu-id="ec46c-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ec46c-279">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="ec46c-279">Troubleshooting</span></span>
* <span data-ttu-id="ec46c-280">Stellen Sie sicher, die Sie festgelegt haben die [SpatialPerception](#setting-the-spatialperception-capability) Funktion</span><span class="sxs-lookup"><span data-stu-id="ec46c-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="ec46c-281">Bei der nachverfolgung verloren geht, wird das nächste OnSurfaceChanged Ereignis alle Gitter entfernt.</span><span class="sxs-lookup"><span data-stu-id="ec46c-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="ec46c-282">Räumliche Zuordnung in Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="ec46c-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="ec46c-283">Weitere Informationen zur Verwendung von räumliche Zuordnung mit Mixed Reality-Toolkit v2 finden Sie unter den <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">räumliche Awareness Abschnitt</a> MRTK Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="ec46c-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec46c-284">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ec46c-284">See also</span></span>
* [<span data-ttu-id="ec46c-285">MR räumlich 230: Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="ec46c-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="ec46c-286">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="ec46c-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="ec46c-287">Koordinatensysteme in Unity</span><span class="sxs-lookup"><span data-stu-id="ec46c-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="ec46c-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="ec46c-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="ec46c-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="ec46c-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="ec46c-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="ec46c-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="ec46c-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="ec46c-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
