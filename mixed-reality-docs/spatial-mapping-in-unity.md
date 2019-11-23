---
title: Räumliche Zuordnung in Unity
description: Rendering und Konflikt mit der realen Geometrie in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Zuordnung, Renderer, Collider, Mesh, Scannen, Komponente
ms.openlocfilehash: 452e629a877df585ffbc0a6466ffeb2588b66ecf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438037"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="176f1-104">Räumliche Zuordnung in Unity</span><span class="sxs-lookup"><span data-stu-id="176f1-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="176f1-105">In diesem Thema wird beschrieben, wie die [räumliche Zuordnung](spatial-mapping.md) in Ihrem Unity-Projekt verwendet wird, und es werden Dreiecksnetze abgerufen, die die Oberflächen weltweit um ein hololens-Gerät, für Platzierung, Okklusion, Raumanalyse usw. darstellen.</span><span class="sxs-lookup"><span data-stu-id="176f1-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="176f1-106">Unity bietet vollständige Unterstützung für die räumliche Zuordnung, die Entwicklern auf folgende Weise zur Verfügung gestellt wird:</span><span class="sxs-lookup"><span data-stu-id="176f1-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="176f1-107">In mixedrealitytoolkit verfügbare räumliche Zuordnungskomponenten, die einen einfachen und schnellen Weg für den Einstieg in die räumliche Zuordnung bieten</span><span class="sxs-lookup"><span data-stu-id="176f1-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="176f1-108">Räumliche Mapping-APIs auf niedrigerer Ebene, die Vollzugriff bieten und eine anspruchsvollere anwendungsspezifische Anpassung ermöglichen</span><span class="sxs-lookup"><span data-stu-id="176f1-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="176f1-109">Um die räumliche Zuordnung in der APP zu verwenden, muss die spatialperception-Funktion in Ihrem appxmanifest festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="176f1-110">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="176f1-110">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="176f1-111"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="176f1-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="176f1-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="176f1-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="176f1-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="176f1-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="176f1-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="176f1-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="176f1-115">Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="176f1-115">Spatial mapping</span></span></td>
        <td><span data-ttu-id="176f1-116">✔️</span><span class="sxs-lookup"><span data-stu-id="176f1-116">✔️</span></span></td>
        <td><span data-ttu-id="176f1-117">✔️</span><span class="sxs-lookup"><span data-stu-id="176f1-117">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="176f1-118">Festlegen der spatialperception-Funktion</span><span class="sxs-lookup"><span data-stu-id="176f1-118">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="176f1-119">Damit eine APP räumliche Zuordnungs Daten verarbeiten kann, muss die spatialperception-Funktion aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-119">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="176f1-120">Aktivieren der spatialperception-Funktion:</span><span class="sxs-lookup"><span data-stu-id="176f1-120">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="176f1-121">Öffnen Sie im Unity-Editor den Bereich **"Player Einstellungen"** (Bearbeiten > Projekteinstellungen > Player).</span><span class="sxs-lookup"><span data-stu-id="176f1-121">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="176f1-122">Klicken Sie auf die Registerkarte **"Windows Store"** .</span><span class="sxs-lookup"><span data-stu-id="176f1-122">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="176f1-123">Erweitern Sie **"Veröffentlichungs Einstellungen"** , und überprüfen Sie die Funktion **"spatialperception"** in der Liste **"Funktionen"** .</span><span class="sxs-lookup"><span data-stu-id="176f1-123">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="176f1-124">Beachten Sie Folgendes: Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projekt Mappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder [Diese Funktion manuell in "appxmanifest" in Visual Studio festlegen](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="176f1-124">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="176f1-125">Die räumliche Zuordnung erfordert auch ein maxversiongetestet von mindestens 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="176f1-125">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="176f1-126">Klicken Sie in Visual Studio im Projektmappen-Explorer mit der rechten Maustaste auf **Package. appxmanifest** , und wählen Sie **Code anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="176f1-126">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="176f1-127">Suchen Sie die Zeile, in der **targetdevicefamily** angegeben ist, und ändern Sie **maxversiongete= "10.0.10240.0"** in **maxversiongete= "10.0.10586.0"** .</span><span class="sxs-lookup"><span data-stu-id="176f1-127">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="176f1-128">**Speichern** Sie die Datei "Package. appxmanifest".</span><span class="sxs-lookup"><span data-stu-id="176f1-128">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="176f1-129">Die ersten Schritte mit den integrierten räumlichen Mapping-Komponenten von Unity</span><span class="sxs-lookup"><span data-stu-id="176f1-129">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="176f1-130">Unity bietet zwei Komponenten für das einfache Hinzufügen von räumlicher Zuordnung zu Ihrer APP, den **Renderer für räumliche** zuzuzuzuzufügende **Daten und den**</span><span class="sxs-lookup"><span data-stu-id="176f1-130">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="176f1-131">Renderer für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="176f1-131">Spatial Mapping Renderer</span></span>

<span data-ttu-id="176f1-132">Der Renderer für räumliche Zuordnung ermöglicht die Visualisierung des diagrammdiagrammdiagrammers.</span><span class="sxs-lookup"><span data-stu-id="176f1-132">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Renderer für räumliche Zuordnung in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="176f1-134">Der Collider für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="176f1-134">Spatial Mapping Collider</span></span>

<span data-ttu-id="176f1-135">Der Collider der räumlichen Zuordnung ermöglicht die holografische Inhalts Interaktion (oder Zeichen Interaktion), wie z. b. die Physik, mit dem Mesh für räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="176f1-135">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Der Collider für räumliche Zuordnung in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="176f1-137">Verwenden der integrierten Komponenten für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="176f1-137">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="176f1-138">Wenn Sie physische Oberflächen visualisieren und mit ihnen interagieren möchten, können Sie Ihrer APP beide Komponenten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="176f1-138">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="176f1-139">So verwenden Sie diese beiden Komponenten in ihrer Unity-App:</span><span class="sxs-lookup"><span data-stu-id="176f1-139">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="176f1-140">Wählen Sie ein gameobject-Objekt in der Mitte des Bereichs aus, in dem Sie räumliche Oberflächen Netze erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="176f1-140">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="176f1-141">**Fügen Sie** im Inspektor-Fenster Komponenten > **XR** >  ** ** der oder **räumliche Zuordnung**hinzu.</span><span class="sxs-lookup"><span data-stu-id="176f1-141">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="176f1-142">Weitere Informationen zur Verwendung dieser Komponenten finden Sie auf der <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentations Website</a>.</span><span class="sxs-lookup"><span data-stu-id="176f1-142">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="176f1-143">Über die integrierten Komponenten für räumliche Zuordnung hinausgehen</span><span class="sxs-lookup"><span data-stu-id="176f1-143">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="176f1-144">Diese Komponenten vereinfachen den Einstieg in die räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="176f1-144">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="176f1-145"> Wenn Sie fortfahren möchten, können Sie zwei Haupt Pfade untersuchen:</span><span class="sxs-lookup"><span data-stu-id="176f1-145"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="176f1-146">Wenn Sie eine eigene Mesh-Verarbeitung auf niedrigerer Ebene durchführen möchten, finden Sie im Abschnitt weiter unten Informationen zur Skript-API auf niedriger Ebene.</span><span class="sxs-lookup"><span data-stu-id="176f1-146">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="176f1-147">Informationen zu einer übergeordneten Mesh-Analyse finden Sie im Abschnitt weiter unten über die spatialunderstanding-Bibliothek in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">mixedrealitytoolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="176f1-147">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="176f1-148">Verwenden der Unity-API für die räumliche Zuordnung auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="176f1-148">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="176f1-149">Wenn Sie mehr Kontrolle benötigen, als Sie von den Komponenten des Renderers für räumliche Zuordnung und der Komponenten Zuordnung für räumliche Zuordnung erhalten, können Sie die Low-Level-Skript-APIs für die räumliche Zuordnung verwenden.</span><span class="sxs-lookup"><span data-stu-id="176f1-149">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="176f1-150">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="176f1-150">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="176f1-151">**Typen**: *surfaceobserver*, *SurfaceChange*, *surfacedata*, *surfaceid*</span><span class="sxs-lookup"><span data-stu-id="176f1-151">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="176f1-152">Im folgenden finden Sie einen Überblick über den empfohlenen Ablauf für eine Anwendung, die die APIs für die räumliche Zuordnung verwendet.</span><span class="sxs-lookup"><span data-stu-id="176f1-152">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="176f1-153">Einrichten von "surfaceobserver (s)"</span><span class="sxs-lookup"><span data-stu-id="176f1-153">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="176f1-154">Instanziieren Sie ein surfaceobserver-Objekt für jeden Anwendungs definierten Bereich, für den Sie räumliche Mapping-Daten benötigen.</span><span class="sxs-lookup"><span data-stu-id="176f1-154">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="176f1-155">Geben Sie den Bereich des Speicherplatzes an, für den jedes surfaceobserver-Objektdaten bereitstellt, indem Sie entweder setvolumeassphere, setvolumeasaxisalignedbox, setvolumeasorientedbox oder setvolumeasfrustum aufrufen.</span><span class="sxs-lookup"><span data-stu-id="176f1-155">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="176f1-156">Sie können den Bereich des Speicherplatzes in der Zukunft neu definieren, indem Sie einfach eine dieser Methoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="176f1-156">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="176f1-157">Wenn Sie surfaceobserver. Update () aufgerufen haben, müssen Sie für jede räumliche Oberfläche im Bereich von surfaceobserver einen Handler bereitstellen, für den das räumliche Zuordnungssystem über neue Informationen verfügt.</span><span class="sxs-lookup"><span data-stu-id="176f1-157">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="176f1-158">Der Handler empfängt für eine räumliche Oberfläche Folgendes:</span><span class="sxs-lookup"><span data-stu-id="176f1-158">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="176f1-159">Verarbeiten von Oberflächen Änderungen</span><span class="sxs-lookup"><span data-stu-id="176f1-159">Handling Surface Changes</span></span>

<span data-ttu-id="176f1-160">Es gibt mehrere Hauptfälle, die behandelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="176f1-160">There are several main cases to handle.</span></span> <span data-ttu-id="176f1-161">Hinzugefügte & aktualisiert, die denselben Codepfad verwenden und entfernt werden können.</span><span class="sxs-lookup"><span data-stu-id="176f1-161">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="176f1-162">In den hinzugefügten & aktualisierten Fällen im Beispiel fügen wir das gameobject-Objekt, das dieses Mesh darstellt, aus dem Wörterbuch hinzu, erstellen eine surfacedata-Struktur mit den erforderlichen Komponenten und rufen dann requestmeshdataasync auf, um das gameobject mit den Mesh-Daten aufzufüllen. Position in der Szene.</span><span class="sxs-lookup"><span data-stu-id="176f1-162">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="176f1-163">Im entfernten Fall entfernen wir das gameobject, das dieses Mesh darstellt, aus dem Wörterbuch und zerstören es.</span><span class="sxs-lookup"><span data-stu-id="176f1-163">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="176f1-164">Verarbeiten von Daten</span><span class="sxs-lookup"><span data-stu-id="176f1-164">Handling Data Ready</span></span>

<span data-ttu-id="176f1-165">Der ondataready-Handler empfängt ein surfacedata-Objekt.</span><span class="sxs-lookup"><span data-stu-id="176f1-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="176f1-166">Die in der Datei "worldanchor", "meshfilter" und "(optional) meshcollider" enthaltenen Objekte entsprechen dem aktuellen Zustand der zugeordneten räumlichen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="176f1-166">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="176f1-167">Führen Sie optional eine Analyse und/oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Mesh-Daten durch, indem Sie auf den Mesh-Member des meshfilter-Objekts zugreifen.</span><span class="sxs-lookup"><span data-stu-id="176f1-167">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="176f1-168">Rendersie die räumliche Oberfläche mit dem aktuellen Mesh, und (optional) verwenden Sie Sie für Physik-und Raycasts.</span><span class="sxs-lookup"><span data-stu-id="176f1-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="176f1-169">Es ist wichtig zu bestätigen, dass der Inhalt der surfacedata nicht NULL ist.</span><span class="sxs-lookup"><span data-stu-id="176f1-169">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="176f1-170">Verarbeitung bei Updates starten</span><span class="sxs-lookup"><span data-stu-id="176f1-170">Start processing on updates</span></span>

<span data-ttu-id="176f1-171">"Surfaceobserver. Update ()" sollte bei einer Verzögerung und nicht bei jedem Frame aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="176f1-172">Mesh-Analyse auf höherer Ebene: spatialunderstanding</span><span class="sxs-lookup"><span data-stu-id="176f1-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="176f1-173"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixedrealitytoolkit</a> ist eine Sammlung hilfreicher hilfsprogrammcodes für die Holographic-Entwicklung, die auf den Holographic Unity-APIs basiert.</span><span class="sxs-lookup"><span data-stu-id="176f1-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="176f1-174">Räumliche Kenntnisse</span><span class="sxs-lookup"><span data-stu-id="176f1-174">Spatial Understanding</span></span>

<span data-ttu-id="176f1-175">Beim Platzieren von holograms in der physischen Welt ist es häufig wünschenswert, das Gitter-und Oberflächen Flächen der räumlichen Zuordnung zu überschreiten.</span><span class="sxs-lookup"><span data-stu-id="176f1-175">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="176f1-176">Wenn die Platzierung prozedurale durchgeführt wird, ist ein höheres Maß an Umwelt Kenntnissen wünschenswert.</span><span class="sxs-lookup"><span data-stu-id="176f1-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="176f1-177">Dies erfordert in der Regel Entscheidungen hinsichtlich der Fläche "Floor", "Ceiling" und "Wände".</span><span class="sxs-lookup"><span data-stu-id="176f1-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="176f1-178">Außerdem können Sie mit einer Reihe von Platzierungs Einschränkungen optimieren, um die begehrtesten physischen Speicherorte für Holographic-Objekte zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="176f1-178">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="176f1-179">Bei der Entwicklung von jung-und-Fragmenten stellten Asobo-Studios dieses Problem in den Kopf, um für diesen Zweck ein Raum-Solver zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="176f1-179">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="176f1-180">Bei jedem dieser Spiele gab es Spiel spezifische Anforderungen, aber Sie haben die grundlegende Technologie für räumliche Daten genutzt.</span><span class="sxs-lookup"><span data-stu-id="176f1-180">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="176f1-181">Die Bibliothek "holotoolkit. spatialunderstanding" kapselt diese Technologie, sodass Sie schnell leere Leerzeichen auf den Wänden finden, Objekte auf der Obergrenze platzieren, für das Zeichen platzieren und eine Vielzahl anderer Abfragen mit räumlichem Verständnis festlegen können.</span><span class="sxs-lookup"><span data-stu-id="176f1-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="176f1-182">Der gesamte Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und die Verbesserungen für die Community freigeben können.</span><span class="sxs-lookup"><span data-stu-id="176f1-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="176f1-183">Der Code für den C++ Solver wurde in eine UWP-dll umschließt und Unity mit einem Drop in Prefab verfügbar gemacht, das in mixedrealitytoolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="176f1-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="176f1-184">Grundlegendes zu Modulen</span><span class="sxs-lookup"><span data-stu-id="176f1-184">Understanding Modules</span></span>

<span data-ttu-id="176f1-185">Es gibt drei primäre Schnittstellen, die vom Modul verfügbar gemacht werden: Topologie für einfache Oberflächen-und räumliche Abfragen, Form zur Objekterkennung und das objektplatzierungs-Solver für die Einschränkungs basierte Platzierung von Objekt Sätzen.</span><span class="sxs-lookup"><span data-stu-id="176f1-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="176f1-186">Diese werden nachfolgend beschrieben.</span><span class="sxs-lookup"><span data-stu-id="176f1-186">Each of these is described below.</span></span> <span data-ttu-id="176f1-187">Zusätzlich zu den drei primären Modulschnittstellen kann eine Strahl Umwandlungs Schnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes, wasserdichtes Playspace-Mesh kann kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="176f1-188">Strahl Umwandlung</span><span class="sxs-lookup"><span data-stu-id="176f1-188">Ray Casting</span></span>

<span data-ttu-id="176f1-189">Nachdem der Raum gescannt und fertiggestellt wurde, werden Bezeichnungen intern für Oberflächen, wie z. b. Boden, Ceiling und Wände, generiert.</span><span class="sxs-lookup"><span data-stu-id="176f1-189">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="176f1-190">Die "playspaceraycast"-Funktion nimmt einen Strahl an und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert. wenn dies der Fall ist, werden Informationen über diese Oberfläche in Form von "raycastresult" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="176f1-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="176f1-191">Intern wird der raycast anhand der berechneten Voxel-Darstellung im 8cm-Format des Playspace berechnet.</span><span class="sxs-lookup"><span data-stu-id="176f1-191">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="176f1-192">Jeder Voxel enthält einen Satz von Oberflächenelementen mit verarbeiteten Topologiedaten (auch als Surfels bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="176f1-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="176f1-193">Der Surfels, der in der überschneidenden Voxel-Zelle enthalten ist, wird verglichen und die beste Entsprechung für die Suche nach den Topologieinformationen.</span><span class="sxs-lookup"><span data-stu-id="176f1-193">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="176f1-194">Diese Topologieinformationen enthalten die Bezeichnung, die in Form der "surfacetypes"-Aufzählung zurückgegeben wird, sowie den Oberflächen Bereich der überschneidenden Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="176f1-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="176f1-195">Im Unity-Beispiel wandelt der Cursor einen Strahl in jedem Frame um.</span><span class="sxs-lookup"><span data-stu-id="176f1-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="176f1-196">Zuerst für Unity-Kollisionen.</span><span class="sxs-lookup"><span data-stu-id="176f1-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="176f1-197">Zweitens, mit der Welt Darstellung des grundlegenden Moduls.</span><span class="sxs-lookup"><span data-stu-id="176f1-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="176f1-198">Und schließlich wieder Benutzeroberflächen Elemente.</span><span class="sxs-lookup"><span data-stu-id="176f1-198">And finally, again UI elements.</span></span> <span data-ttu-id="176f1-199">In dieser Anwendung erhält die Benutzeroberfläche Priorität, das Ergebnis des Ergebnisses und schließlich Unity-Kollisionen.</span><span class="sxs-lookup"><span data-stu-id="176f1-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="176f1-200">Der surfaketype wird als Text neben dem Cursor gemeldet.</span><span class="sxs-lookup"><span data-stu-id="176f1-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="176f1-201">![Surface-Typ wird neben dem Cursor bezeichnet](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="176f1-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="176f1-202">*Der Surface-Typ wird neben dem Cursor bezeichnet.*</span><span class="sxs-lookup"><span data-stu-id="176f1-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="176f1-203">Topologieabfragen</span><span class="sxs-lookup"><span data-stu-id="176f1-203">Topology Queries</span></span>

<span data-ttu-id="176f1-204">Innerhalb der DLL übernimmt der topologiemanager die Bezeichnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="176f1-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="176f1-205">Wie bereits erwähnt, werden viele der Daten in Surfels gespeichert, das in einem Voxel-Volume enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="176f1-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="176f1-206">Außerdem wird die "playspaceinfos"-Struktur zum Speichern von Informationen über den Playspace verwendet, einschließlich der Welt Ausrichtung (weitere Details zu diesem unten), der Etage und der Höhe des ceiling.</span><span class="sxs-lookup"><span data-stu-id="176f1-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="176f1-207">Heuristiken werden zum Bestimmen von Boden, Ceiling und Wänden verwendet.</span><span class="sxs-lookup"><span data-stu-id="176f1-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="176f1-208">Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Größe von mehr als 1 m2 als Floor betrachtet.</span><span class="sxs-lookup"><span data-stu-id="176f1-208">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="176f1-209">Beachten Sie, dass der Kamerapfad während des Scanvorgangs auch in diesem Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="176f1-209">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="176f1-210">Eine Teilmenge der Abfragen, die vom topologiemanager verfügbar gemacht werden, wird über die dll verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="176f1-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="176f1-211">Die verfügbar gemachten Topologieabfragen lauten wie folgt.</span><span class="sxs-lookup"><span data-stu-id="176f1-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="176f1-212">Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="176f1-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="176f1-213">Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die minimale Platzierungs Höhe oberhalb der Etage und den minimalen Abstand vor dem Volume an.</span><span class="sxs-lookup"><span data-stu-id="176f1-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="176f1-214">Alle Messungen befinden sich in Meter.</span><span class="sxs-lookup"><span data-stu-id="176f1-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="176f1-215">Jede dieser Abfragen nimmt ein vorab zugeordenes Array von "topologyresult"-Strukturen an.</span><span class="sxs-lookup"><span data-stu-id="176f1-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="176f1-216">Der "locationcount"-Parameter gibt die Länge des übergebenen Arrays an.</span><span class="sxs-lookup"><span data-stu-id="176f1-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="176f1-217">Der Rückgabewert meldet die Anzahl der zurückgegebenen Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="176f1-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="176f1-218">Diese Zahl ist nie größer als der Wert des "locationcount"-Parameters.</span><span class="sxs-lookup"><span data-stu-id="176f1-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="176f1-219">"Topologyresult" enthält die Mittelpunkt Position des zurückgegebenen Volumes, die Richtung (d. h. Normal) und die Abmessungen des gefundenen Speicherplatzes.</span><span class="sxs-lookup"><span data-stu-id="176f1-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="176f1-220">Beachten Sie, dass im Unity-Beispiel jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="176f1-220">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="176f1-221">Im Beispiel werden die Parameter für jede dieser Abfragen in angemessene Werte fest codiert.</span><span class="sxs-lookup"><span data-stu-id="176f1-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="176f1-222">Weitere Beispiele finden Sie unter SpaceVisualizer.cs im Beispielcode.</span><span class="sxs-lookup"><span data-stu-id="176f1-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="176f1-223">Shape-Abfragen</span><span class="sxs-lookup"><span data-stu-id="176f1-223">Shape Queries</span></span>

<span data-ttu-id="176f1-224">Innerhalb der dll verwendet der Shape Analyzer ("ShapeAnalyzer_W") die topologieanalyse, um mit den vom benutzerdefinierten benutzerdefinierten Formen zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="176f1-224">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="176f1-225">Das Unity-Beispiel definiert einen Satz von Formen und macht die Ergebnisse über das in-App-Abfrage Menü auf der Registerkarte Form verfügbar. Die Absicht besteht darin, dass der Benutzer seine eigenen Objektform Abfragen definieren und diese verwenden kann, je nach Bedarf von der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="176f1-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="176f1-226">Beachten Sie, dass die Formanalyse nur auf horizontalen Oberflächen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="176f1-226">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="176f1-227">Eine Couch wird z. b. durch die flache Arbeitsplatz Oberfläche und den flachen oberen Rand der Couch zurückgelegt.</span><span class="sxs-lookup"><span data-stu-id="176f1-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="176f1-228">Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, wobei die beiden Oberflächen ausgerichtet und verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="176f1-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="176f1-229">Bei Verwendung der APIs-Terminologie sind der Couch-und der Back-Top Form Komponenten, und die Ausrichtungs Anforderungen sind Shape-Komponenten Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="176f1-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="176f1-230">Eine Beispiel Abfrage, die im Unity-Beispiel (ShapeDefinition.cs) für "sitbare" Objekte definiert ist, lautet wie folgt.</span><span class="sxs-lookup"><span data-stu-id="176f1-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="176f1-231">Jede Shape-Abfrage wird durch einen Satz von Form Komponenten definiert, die jeweils über einen Satz von Komponenten Einschränkungen und einen Satz von Form Einschränkungen verfügen, die Abhängigkeiten zwischen den Komponenten auflisten.</span><span class="sxs-lookup"><span data-stu-id="176f1-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="176f1-232">Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponenten Definition und keine Formen Einschränkungen zwischen Komponenten (da nur eine Komponente vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="176f1-232">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="176f1-233">Im Gegensatz dazu hat die Form "Couch" zwei Form Komponenten und vier Form Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="176f1-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="176f1-234">Beachten Sie, dass die Komponenten durch ihren Index in der Komponentenliste des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-234">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="176f1-235">Wrapper Funktionen werden im Unity-Modul bereitgestellt, um eine einfache Erstellung benutzerdefinierter Formen Definitionen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="176f1-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="176f1-236">Die vollständige Liste der Komponenten-und Shape-Einschränkungen finden Sie in "SpatialUnderstandingDll.cs" innerhalb der "shapecomponenteinschränkung"-und "shapeconstraint"-Strukturen.</span><span class="sxs-lookup"><span data-stu-id="176f1-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="176f1-237">auf dieser Oberfläche wird ![Rechteck Form gefunden](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="176f1-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="176f1-238">*Die Rechteck Form wird auf dieser Oberfläche gefunden.*</span><span class="sxs-lookup"><span data-stu-id="176f1-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="176f1-239">Objektplatzierungs-Solver</span><span class="sxs-lookup"><span data-stu-id="176f1-239">Object Placement Solver</span></span>

<span data-ttu-id="176f1-240">Der objektplatzierungs-Solver kann verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, um die Objekte zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="176f1-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="176f1-241">Der Solver findet den am besten geeigneten Speicherort anhand der Objekt Regeln und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="176f1-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="176f1-242">Außerdem bleiben Objekt Abfragen so lange erhalten, bis das Objekt mit "Solver_RemoveObject"-oder "Solver_RemoveAllObjects"-aufrufen entfernt wird, sodass die eingeschränkte Platzierung von mehreren Objekten ermöglicht wird.</span><span class="sxs-lookup"><span data-stu-id="176f1-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="176f1-243">Die Platzierungs Abfragen von Objekten bestehen aus drei Teilen: Platzierungs Typ mit Parametern, eine Liste von Regeln und eine Liste von Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="176f1-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="176f1-244">Verwenden Sie die folgende API, um eine Abfrage auszuführen.</span><span class="sxs-lookup"><span data-stu-id="176f1-244">To run a query, use the following API.</span></span>

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

<span data-ttu-id="176f1-245">Diese Funktion nimmt einen Objektnamen, eine Platzierungs Definition und eine Liste von Regeln und Einschränkungen an.</span><span class="sxs-lookup"><span data-stu-id="176f1-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="176f1-246">Die C# Wrapper stellen Konstruktions Hilfsfunktionen bereit, um die Erstellung von Regeln und Einschränkungen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="176f1-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="176f1-247">Die Platzierungs Definition enthält den Abfragetyp – d. h. einen der folgenden.</span><span class="sxs-lookup"><span data-stu-id="176f1-247">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="176f1-248">Jeder der Platzierungs Typen hat eine Reihe von Parametern, die für den Typ eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="176f1-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="176f1-249">Die "objectplacementdefinition"-Struktur enthält einen Satz statischer Hilfsfunktionen zum Erstellen dieser Definitionen.</span><span class="sxs-lookup"><span data-stu-id="176f1-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="176f1-250">Wenn Sie z. b. einen Speicherort zum Platzieren eines Objekts im Boden finden möchten, können Sie die folgende Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="176f1-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="176f1-251">public static objectplacementdefinition Create_OnFloor (Vector3 halfdims) zusätzlich zum Platzierungs Typ können Sie einen Satz von Regeln und Einschränkungen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="176f1-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="176f1-252">Regeln können nicht verletzt werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-252">Rules cannot be violated.</span></span> <span data-ttu-id="176f1-253">Mögliche Platzierungs Speicherorte, die den Typ und die Regeln erfüllen, werden dann anhand des Satzes von Einschränkungen optimiert, um den optimalen Speicherort für die Platzierung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="176f1-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="176f1-254">Alle Regeln und Einschränkungen können von den bereitgestellten statischen Erstellungs Funktionen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="176f1-255">Eine Beispiel Regel und eine Einschränkungs Erstellungs Funktion finden Sie unten.</span><span class="sxs-lookup"><span data-stu-id="176f1-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="176f1-256">Die nachstehende Objekt Platzierungs Abfrage sucht nach einer Stelle, an der der Rand einer Oberfläche von anderen Objekten, die sich in der Mitte des Raums befinden, platziert wird.</span><span class="sxs-lookup"><span data-stu-id="176f1-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="176f1-257">Wenn erfolgreich, wird eine "objectplacementresult"-Struktur mit der Platzierungsposition, den Dimensionen und der Ausrichtung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="176f1-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="176f1-258">Außerdem wird die Platzierung der internen Liste der platzierten Objekte der dll hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="176f1-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="176f1-259">Bei nachfolgenden Platzierungs Abfragen wird dieses Objekt berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="176f1-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="176f1-260">Die Datei "LevelSolver.cs" im Unity-Beispiel enthält weitere Beispielabfragen.</span><span class="sxs-lookup"><span data-stu-id="176f1-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="176f1-261">![Ergebnisse der Objekt Platzierung](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="176f1-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="176f1-262">*Abbildung 3: die blauen Felder, die ergeben, wie sich das Ergebnis von drei Positionen im Boden von der Kamera positionsregeln entfernt hat*</span><span class="sxs-lookup"><span data-stu-id="176f1-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="176f1-263">Wenn Sie für den Speicherort der Platzierung mehrerer Objekte, die für ein Level-oder Anwendungsszenario erforderlich sind, lösen möchten, lösen Sie zunächst unentbehrliche und große Objekte aus, um die Wahrscheinlichkeit zu maximieren, dass ein Platz gefunden wird</span><span class="sxs-lookup"><span data-stu-id="176f1-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="176f1-264">Die Platzierungs Reihenfolge ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="176f1-264">Placement order is important.</span></span> <span data-ttu-id="176f1-265">Wenn die Platzierung von Objekten nicht gefunden werden kann, versuchen Sie es mit weniger eingeschränkten Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="176f1-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="176f1-266">Eine Reihe von Fall Back Konfigurationen ist wichtig für die Unterstützung von Funktionen in vielen Raum Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="176f1-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="176f1-267">Raum Scanprozess</span><span class="sxs-lookup"><span data-stu-id="176f1-267">Room Scanning Process</span></span>

<span data-ttu-id="176f1-268">Obwohl die von hololens bereitgestellte räumliche Mappinglösung generisch genug ist, um den Anforderungen des gesamten Bereichs von Problembereichen gerecht zu werden, wurde das räumliche grundlegendes Modul erstellt, um die Anforderungen von zwei bestimmten spielen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="176f1-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="176f1-269">Die Lösung ist um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert, die unten zusammengefasst werden.</span><span class="sxs-lookup"><span data-stu-id="176f1-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="176f1-270">Benutzergesteuerte Playspace "Paint" – während der Überprüfungsphase bewegt der Benutzer die Wiedergabegeschwindigkeit und untersucht die Bereiche, die eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="176f1-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="176f1-271">Das generierte Mesh ist wichtig, um Benutzer Feedback in dieser Phase bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="176f1-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="176f1-272">Startseite oder Office-Setup – die Abfragefunktionen werden um flache Flächen und Wände im rechten Winkel entworfen.</span><span class="sxs-lookup"><span data-stu-id="176f1-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="176f1-273">Dies ist eine weiche Einschränkung.</span><span class="sxs-lookup"><span data-stu-id="176f1-273">This is a soft limitation.</span></span> <span data-ttu-id="176f1-274">Während der Scan Phase wird jedoch eine primäre Achsen Analyse abgeschlossen, um das Gitter Mosaik entlang der Haupt-und der Nebenachse zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="176f1-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="176f1-275">Die enthaltene SpatialUnderstanding.cs-Datei verwaltet den Scan Phasen Prozess.</span><span class="sxs-lookup"><span data-stu-id="176f1-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="176f1-276">Es werden die folgenden Funktionen aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="176f1-276">It calls the following functions.</span></span>

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

<span data-ttu-id="176f1-277">Der Scanvorgang, der vom "spatialunderstanding"-Verhalten gesteuert wird, ruft initscan auf und aktualisiert dann jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="176f1-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="176f1-278">Wenn die Statistik Abfrage eine angemessene Abdeckung meldet, kann der Benutzer mit airtap auf requestfinish aufrufen, um das Ende der Scan Phase anzugeben.</span><span class="sxs-lookup"><span data-stu-id="176f1-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="176f1-279">Updatescan wird weiterhin aufgerufen, bis der Rückgabewert angibt, dass die dll die Verarbeitung abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="176f1-279">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="176f1-280">Grundlegendes zum Mesh</span><span class="sxs-lookup"><span data-stu-id="176f1-280">Understanding Mesh</span></span>

<span data-ttu-id="176f1-281">Die Understanding dll speichert den Playspace intern als Raster von Voxel-Cubes mit 8 cm.</span><span class="sxs-lookup"><span data-stu-id="176f1-281">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="176f1-282">Während des ersten Teils der Überprüfung wird eine Analyse der primären Komponenten abgeschlossen, um die Achsen des Raums zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="176f1-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="176f1-283">Intern speichert Sie seinen Voxel-Bereich, der auf diese Achsen ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="176f1-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="176f1-284">Ein Mesh wird ungefähr jede Sekunde generiert, indem die Isofläche aus dem Voxel-Volume extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="176f1-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="176f1-285">![generierte Gitter, das aus dem Voxel-Volume erstellt wurde](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="176f1-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="176f1-286">*Generiertes Mesh, das vom Voxel-Volume erstellt wurde*</span><span class="sxs-lookup"><span data-stu-id="176f1-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="176f1-287">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="176f1-287">Troubleshooting</span></span>
* <span data-ttu-id="176f1-288">Stellen Sie sicher, dass Sie die Funktion [spatialperception](#setting-the-spatialperception-capability) festgelegt haben</span><span class="sxs-lookup"><span data-stu-id="176f1-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="176f1-289">Wenn die Nachverfolgung verloren geht, entfernt das nächste onsurfacechanged-Ereignis alle Meshes.</span><span class="sxs-lookup"><span data-stu-id="176f1-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="176f1-290">Räumliche Zuordnung im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="176f1-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="176f1-291">Weitere Informationen zur Verwendung der räumlichen Zuordnung mit Mixed Reality Toolkit v2 finden Sie im <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Abschnitt räumliche</a> Informationen der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="176f1-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="176f1-292">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="176f1-292">See also</span></span>
* [<span data-ttu-id="176f1-293">Räumliche Daten 230: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="176f1-293">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="176f1-294">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="176f1-294">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="176f1-295">Koordinatensysteme in Unity</span><span class="sxs-lookup"><span data-stu-id="176f1-295">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="176f1-296"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="176f1-296"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="176f1-297"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">Unityengine. meshfilter</a></span><span class="sxs-lookup"><span data-stu-id="176f1-297"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="176f1-298"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">Unityengine. meshcollider</a></span><span class="sxs-lookup"><span data-stu-id="176f1-298"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="176f1-299"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">Unityengine. Bounds</a></span><span class="sxs-lookup"><span data-stu-id="176f1-299"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
