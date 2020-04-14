---
title: Räumliche Zuordnung in DirectX
description: Erläutert, wie die räumliche Zuordnung in Ihrer DirectX-App implementiert wird. Dies umfasst eine ausführliche Erläuterung der Beispielanwendung für räumliche Zuordnung, die im universelle Windows-Plattform SDK enthalten ist.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, räumliche Zuordnung, Umgebung, Interaktion, DirectX, WinRT, API, Beispielcode, UWP, SDK, Exemplarische Vorgehensweise
ms.openlocfilehash: b3ef74a7e11e0e73fce47e4c7193ace42ffe7c20
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277498"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="aec3d-105">Räumliche Zuordnung in DirectX</span><span class="sxs-lookup"><span data-stu-id="aec3d-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="aec3d-106">In diesem Thema wird beschrieben, wie Sie eine [räumliche Zuordnung](spatial-mapping.md) in Ihrer DirectX-App implementieren.</span><span class="sxs-lookup"><span data-stu-id="aec3d-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="aec3d-107">Dies umfasst eine ausführliche Erläuterung der Beispielanwendung für räumliche Zuordnung, die im universelle Windows-Plattform SDK enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="aec3d-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="aec3d-108">In diesem Thema wird Code aus dem [holographicspatialmapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) -UWP-Codebeispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="aec3d-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="aec3d-109">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="aec3d-110">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="aec3d-111">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="aec3d-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="aec3d-112"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="aec3d-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="aec3d-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="aec3d-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="aec3d-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="aec3d-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="aec3d-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="aec3d-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="aec3d-116">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="aec3d-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="aec3d-117">✔️</span><span class="sxs-lookup"><span data-stu-id="aec3d-117">✔️</span></span></td>
        <td><span data-ttu-id="aec3d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="aec3d-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a><span data-ttu-id="aec3d-119">DirectX-Entwicklungs Übersicht</span><span class="sxs-lookup"><span data-stu-id="aec3d-119">DirectX development overview</span></span>

<span data-ttu-id="aec3d-120">Die native Anwendungsentwicklung für räumliche Zuordnung verwendet die APIs im [Windows. perception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="aec3d-120">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="aec3d-121">Diese APIs bieten vollständige Kontrolle über die Funktionalität räumlicher Mapping in einer Weise, die direkt mit den von [Unity](spatial-mapping-in-unity.md)verfügbar gemachten räumlichen Mapping-APIs vergleichbar ist.</span><span class="sxs-lookup"><span data-stu-id="aec3d-121">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="aec3d-122">Perception-APIs</span><span class="sxs-lookup"><span data-stu-id="aec3d-122">Perception APIs</span></span>

<span data-ttu-id="aec3d-123">Folgende primäre Typen werden für die Entwicklung räumlicher Mapping bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="aec3d-123">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="aec3d-124">[Spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) stellt Informationen zu Oberflächen in anwendungsspezifischen Bereichen des Raums in der Nähe des Benutzers in Form von spatialsurfaceinfo-Objekten bereit.</span><span class="sxs-lookup"><span data-stu-id="aec3d-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="aec3d-125">[Spatialsurfaceinfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) beschreibt eine einzelne räumliche Oberfläche, einschließlich einer eindeutigen ID, eines umgebenden Volumes und einer Zeit der letzten Änderung.</span><span class="sxs-lookup"><span data-stu-id="aec3d-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="aec3d-126">Auf Anforderung wird ein spatialsurfakemesh asynchron bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="aec3d-126">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="aec3d-127">[Spatialsurfakemeshoptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) enthält Parameter, mit denen die von spatialsurfakeinfo angeforderten spatialsurfaesh-Objekte angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="aec3d-128">[Spatialsurfacemesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) stellt die Mesh-Daten für eine einzelne räumliche Oberfläche dar.</span><span class="sxs-lookup"><span data-stu-id="aec3d-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="aec3d-129">Die Daten für Scheitelpunkt Positionen, Scheitelpunkt normale und Dreieck Indizes sind in dem Element spatialsurfakemeschbuffer-Objekten enthalten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-129">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="aec3d-130">[Spatialsurfakemeschbuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) umschließt einen einzelnen Typ von Mesh-Daten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="aec3d-131">Beim Entwickeln einer Anwendung, die diese APIs verwendet, sieht Ihr grundlegender Programmablauf wie folgt aus (wie in der unten beschriebenen Beispielanwendung gezeigt):</span><span class="sxs-lookup"><span data-stu-id="aec3d-131">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="aec3d-132">**Einrichten von spatialsurfaceobserver**</span><span class="sxs-lookup"><span data-stu-id="aec3d-132">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="aec3d-133">Aufrufen von [requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), um sicherzustellen, dass der Benutzer die Berechtigung zum Verwenden der räumlichen Zuordnungsfunktionen des Geräts für die Anwendung erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="aec3d-133">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="aec3d-134">Instanziieren Sie ein spatialsurfaceobserver-Objekt.</span><span class="sxs-lookup"><span data-stu-id="aec3d-134">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="aec3d-135">Aufrufen von [setboundingvolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) , um die Bereiche anzugeben, in denen Sie Informationen über räumliche Oberflächen benötigen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-135">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="aec3d-136">Diese Bereiche können Sie in Zukunft ändern, indem Sie diese Funktion einfach erneut aufrufen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-136">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="aec3d-137">Jede Region wird mit einem [spatialboundingvolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)angegeben.</span><span class="sxs-lookup"><span data-stu-id="aec3d-137">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="aec3d-138">Registrieren Sie sich für das [observedsurfaceschangi-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , das ausgelöst wird, wenn neue Informationen über die räumlichen Oberflächen in den von Ihnen angegebenen Bereichen des Raums verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="aec3d-138">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="aec3d-139">**Prozess-observedsurfaceschge-Ereignisse**</span><span class="sxs-lookup"><span data-stu-id="aec3d-139">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="aec3d-140">Aufrufen von [getobservedoberflächen](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) in Ihrem Ereignishandler, um eine Zuordnung der spatialsurfakeinfo-Objekte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-140">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="aec3d-141">Mithilfe dieser Karte können Sie die Datensätze aktualisieren, in denen räumliche Oberflächen [in der Benutzerumgebung vorhanden](spatial-mapping.md#mesh-caching)sind.</span><span class="sxs-lookup"><span data-stu-id="aec3d-141">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="aec3d-142">Für jedes spatialsurfaceinfo-Objekt können Sie [trygetbounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) Abfragen, um die räumlichen Blöcke der Oberfläche zu ermitteln, die in einem [räumlichen Koordinatensystem](coordinate-systems.md) Ihrer Wahl ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-142">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="aec3d-143">Wenn Sie ein Mesh für eine räumliche Oberfläche anfordern möchten, wenden Sie sich an [trycomputelatestmeshasync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="aec3d-143">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="aec3d-144">Sie können Optionen angeben, indem Sie die gewünschte Dichte der Dreiecke und das Format der zurückgegebenen Mesh-Daten angeben.</span><span class="sxs-lookup"><span data-stu-id="aec3d-144">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="aec3d-145">**Gitter empfangen und verarbeiten**</span><span class="sxs-lookup"><span data-stu-id="aec3d-145">**Receive and process mesh**</span></span>
  - <span data-ttu-id="aec3d-146">Jeder Aufrufen von trycomputelatestmeshasync gibt ein spatialsurfakemesh-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="aec3d-146">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="aec3d-147">Von diesem Objekt aus können Sie auf die enthaltenen spatialsurfaeschbuffer-Objekte zugreifen, um auf die Dreiecks Indizes, die Scheitelpunkt Positionen und (falls angefordert) vertexnormale des Netzes zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-147">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="aec3d-148">Diese Daten befinden sich in einem Format, das direkt mit den [Direct3D 11-APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) kompatibel ist, die zum Rendern von Netzen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-148">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="aec3d-149">Von hier aus kann die Anwendung optional eine Analyse oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Mesh-Daten durchführen und diese zum [Rendern](spatial-mapping.md#rendering) und zum Auftreten von physikalischer und- [Kollisionen](spatial-mapping.md#raycasting-and-collision)verwenden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-149">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="aec3d-150">Ein wichtiges Detail ist, dass Sie eine Skalierung auf die mesvertexpositionen anwenden müssen (z. b. im Vertexshader, der zum Rendern der Meshes verwendet wird), um Sie von den optimierten ganzzahligen Einheiten, in denen Sie im Puffer gespeichert sind, in Meter zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="aec3d-150">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="aec3d-151">Sie können diese Skala abrufen, indem Sie [vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-151">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="aec3d-152">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="aec3d-152">Troubleshooting</span></span>
* <span data-ttu-id="aec3d-153">Vergessen Sie nicht, Mesh-Vertex-Positionen in Ihrem Vertexshader zu skalieren, indem Sie die von [spatialsurfakemesh. vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx) zurückgegebene Skala verwenden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-153">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="aec3d-154">Exemplarische Vorgehensweise zum Codebeispiel für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="aec3d-154">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="aec3d-155">Das Codebeispiel für die [holografische räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) enthält Code, den Sie verwenden können, um mit dem Laden von Oberflächen Netzen in Ihre APP zu beginnen, einschließlich der Infrastruktur zum Verwalten und Rendern von Oberflächen Netzen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-155">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="aec3d-156">Nun erfahren Sie, wie Sie Ihrer DirectX-App Oberflächen Zuordnungsfunktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-156">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="aec3d-157">Sie können diesen Code dem Vorlagen Projekt für die [Windows Holographic-App](creating-a-holographic-directx-project.md) hinzufügen. Alternativ können Sie das oben erwähnte Codebeispiel durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-157">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="aec3d-158">Dieses Codebeispiel basiert auf der Windows Holographic-App-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="aec3d-158">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="aec3d-159">Einrichten Ihrer APP für die Verwendung der spatialperception-Funktion</span><span class="sxs-lookup"><span data-stu-id="aec3d-159">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="aec3d-160">Ihre APP muss die Funktion für räumliche Zuordnung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="aec3d-160">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="aec3d-161">Dies ist erforderlich, da das räumliche Mesh eine Darstellung der Benutzerumgebung ist, die als private Daten betrachtet werden kann.</span><span class="sxs-lookup"><span data-stu-id="aec3d-161">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="aec3d-162">Deklarieren Sie diese Funktion in der Datei "Package. appxmanifest" für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="aec3d-162">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="aec3d-163">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aec3d-163">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="aec3d-164">Die Funktion stammt aus dem **uap2** -Namespace.</span><span class="sxs-lookup"><span data-stu-id="aec3d-164">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="aec3d-165">Um Zugriff auf diesen Namespace in ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns* -Attribut in das &lt;Package >-Elements ein.</span><span class="sxs-lookup"><span data-stu-id="aec3d-165">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="aec3d-166">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aec3d-166">Here's an example:</span></span>

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="aec3d-167">Überprüfen der Funktions Unterstützung für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="aec3d-167">Check for spatial mapping feature support</span></span>

<span data-ttu-id="aec3d-168">Windows Mixed Reality unterstützt eine große Bandbreite von Geräten, darunter Geräte, die keine räumliche Zuordnung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-168">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="aec3d-169">Wenn Ihre APP eine räumliche Zuordnung verwenden oder eine räumliche Zuordnung verwenden muss, sollte Sie zum Bereitstellen von Funktionen überprüfen, ob die räumliche Zuordnung unterstützt wird, bevor Sie versuchen, Sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-169">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="aec3d-170">Wenn z. b. eine räumliche Zuordnung für Ihre Mixed Reality-App erforderlich ist, sollte eine Meldung angezeigt werden, wenn ein Benutzer versucht, die Anwendung auf einem Gerät ohne räumliche Zuordnung durchführen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-170">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="aec3d-171">Oder Sie können Ihre eigene virtuelle Umgebung möglicherweise anstelle der Umgebung des Benutzers Rendering, sodass Sie ein ähnliches Verhalten wie bei der Verfügbarkeit der räumlichen Zuordnung bietet.</span><span class="sxs-lookup"><span data-stu-id="aec3d-171">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="aec3d-172">In jedem Fall ermöglicht diese API Ihrer APP, zu erkennen, wann Sie keine räumlichen Zuordnungsdaten erhält, und antwortet auf die entsprechende Weise.</span><span class="sxs-lookup"><span data-stu-id="aec3d-172">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="aec3d-173">Stellen Sie zunächst sicher, dass der UWP-Vertrag auf der Ebene 4 oder höher ist, und fordern Sie dann spatialsurfaceobserver:: IsSupported () an, um das aktuelle Gerät auf Unterstützung für räumliche Zuordnung zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-173">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="aec3d-174">Dies wird im Kontext des Code Beispiels für die [Holographic-Zuordnung für räumliche Daten](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="aec3d-174">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="aec3d-175">Die Unterstützung wird unmittelbar vor dem Anfordern des Zugriffs geprüft.</span><span class="sxs-lookup"><span data-stu-id="aec3d-175">Support is checked just before requesting access.</span></span>

<span data-ttu-id="aec3d-176">Die spatialsurfaceobserver:: IsSupported ()-API ist ab der SDK-Version 15063 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="aec3d-176">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="aec3d-177">Richten Sie ggf. das Projekt auf die Platt Form Version 15063 zurück, bevor Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-177">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="aec3d-178">Beachten Sie Folgendes: Wenn der UWP-Vertrag niedriger als Ebene 4 ist, sollte die APP so vorgehen, als ob das Gerät eine räumliche Zuordnung durchführen kann.</span><span class="sxs-lookup"><span data-stu-id="aec3d-178">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="aec3d-179">Zugriff auf räumliche Zuordnungsdaten anfordern</span><span class="sxs-lookup"><span data-stu-id="aec3d-179">Request access to spatial mapping data</span></span>

<span data-ttu-id="aec3d-180">Ihre APP muss die Berechtigung für den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Sie versuchen, einen Oberflächen Beobachter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-180">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="aec3d-181">Im folgenden finden Sie ein Beispiel, das auf dem Codebeispiel für die Oberflächen Zuordnung basiert. weitere Details finden Sie weiter unten auf dieser Seite:</span><span class="sxs-lookup"><span data-stu-id="aec3d-181">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="aec3d-182">Erstellen eines Oberflächen Beobachters</span><span class="sxs-lookup"><span data-stu-id="aec3d-182">Create a surface observer</span></span>

<span data-ttu-id="aec3d-183">Der **Windows::P erception:: Spatial:: Oberflächen** -Namespace enthält die [spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Klasse, mit der ein oder mehrere Volumes beobachtet werden, die Sie in einem [spatialcoordinatesystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)angeben.</span><span class="sxs-lookup"><span data-stu-id="aec3d-183">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="aec3d-184">Verwenden Sie eine [spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Instanz, um in Echtzeit auf Oberflächen Mesh-Daten zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-184">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="aec3d-185">Aus **appmain. h**:</span><span class="sxs-lookup"><span data-stu-id="aec3d-185">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="aec3d-186">Wie bereits im vorherigen Abschnitt erwähnt, müssen Sie den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Sie von Ihrer APP verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="aec3d-186">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="aec3d-187">Dieser Zugriff wird automatisch auf den hololens gewährt.</span><span class="sxs-lookup"><span data-stu-id="aec3d-187">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="aec3d-188">Als nächstes müssen Sie den Oberflächen Beobachter so konfigurieren, dass er ein bestimmtes Begrenzungs Volume beobachtet.</span><span class="sxs-lookup"><span data-stu-id="aec3d-188">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="aec3d-189">Hier wird ein Feld mit 20 x 20 x 5 Metern betrachtet, das sich am Ursprung des Koordinatensystems befindet.</span><span class="sxs-lookup"><span data-stu-id="aec3d-189">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="aec3d-190">Beachten Sie, dass Sie stattdessen mehrere Begrenzungs Volumes festlegen können.</span><span class="sxs-lookup"><span data-stu-id="aec3d-190">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="aec3d-191">*Dies ist Pseudocode:*</span><span class="sxs-lookup"><span data-stu-id="aec3d-191">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="aec3d-192">Es ist auch möglich, andere umgebende Formen (z. b. eine ansichtsansicht) oder ein Begrenzungsfeld zu verwenden, das keine Achsen Ausrichtung ist.</span><span class="sxs-lookup"><span data-stu-id="aec3d-192">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="aec3d-193">*Dies ist Pseudocode:*</span><span class="sxs-lookup"><span data-stu-id="aec3d-193">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="aec3d-194">Wenn Ihre APP etwas anders ausführen muss, wenn keine Oberflächen Zuordnungsdaten verfügbar sind, können Sie Code schreiben, um auf den Fall zu reagieren, in dem [spatialperceptionaccessstatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) nicht **zulässig** ist. beispielsweise wird er auf PCs mit angefügten immersiven Geräten nicht zugelassen, da diese Geräte nicht über Hardware für räumliche Zuordnung verfügen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-194">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="aec3d-195">Für diese Geräte sollten Sie sich stattdessen auf die räumliche Phase stützen, um Informationen zur Umgebung und Gerätekonfiguration des Benutzers zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-195">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="aec3d-196">Initialisieren und Aktualisieren der Surface-Mesh-Auflistung</span><span class="sxs-lookup"><span data-stu-id="aec3d-196">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="aec3d-197">Wenn der Oberflächen Beobachter erfolgreich erstellt wurde, können wir mit dem Initialisieren der Oberflächen Gitter Auflistung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="aec3d-197">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="aec3d-198">Hier verwenden wir die Pull Model-API, um den aktuellen Satz von beobachteten Oberflächen sofort abzurufen:</span><span class="sxs-lookup"><span data-stu-id="aec3d-198">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="aec3d-199">Es ist auch ein Push-Modell verfügbar, um Oberflächen Mesh-Daten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-199">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="aec3d-200">Sie können Ihre APP so entwerfen, dass nur das Pull-Modell verwendet wird, wenn Sie sich entscheiden. in diesem Fall rufen Sie alle so oft, einmal pro Frame oder innerhalb eines bestimmten Zeitraums, z. b. während der Spiel Einrichtung, Daten ab.</span><span class="sxs-lookup"><span data-stu-id="aec3d-200">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="aec3d-201">Wenn dies der Fall ist, ist der obige Code das, was Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-201">If so, the above code is what you need.</span></span>

<span data-ttu-id="aec3d-202">In unserem Codebeispiel haben wir uns entschieden, die Verwendung beider Modelle zu pädagogischen Zwecken zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-202">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="aec3d-203">Hier abonnieren wir ein Ereignis, um aktuelle Oberflächen Mesh-Daten zu erhalten, wenn das System eine Änderung erkennt.</span><span class="sxs-lookup"><span data-stu-id="aec3d-203">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="aec3d-204">Unser Codebeispiel ist auch so konfiguriert, dass auf diese Ereignisse reagiert wird.</span><span class="sxs-lookup"><span data-stu-id="aec3d-204">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="aec3d-205">Sehen wir uns an, wie wir dies tun.</span><span class="sxs-lookup"><span data-stu-id="aec3d-205">Let's walk through how we do this.</span></span>

<span data-ttu-id="aec3d-206">**Hinweis:** Dies ist möglicherweise nicht die effizienteste Methode, mit der Ihre APP Mesh-Daten verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="aec3d-206">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="aec3d-207">Dieser Code wird aus Gründen der Übersichtlichkeit geschrieben und ist nicht optimiert.</span><span class="sxs-lookup"><span data-stu-id="aec3d-207">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="aec3d-208">Die Oberflächen Mesh-Daten werden in einer schreibgeschützten Zuordnung bereitgestellt, in der [spatialsurfaceinfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) -Objekte mithilfe von [Platform:: GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) als Schlüsselwerte gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-208">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="aec3d-209">Um diese Daten zu verarbeiten, betrachten wir zuerst die Schlüsselwerte, die nicht in unserer Sammlung sind.</span><span class="sxs-lookup"><span data-stu-id="aec3d-209">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="aec3d-210">Weitere Informationen zum Speichern der Daten in unserer Beispiel-App finden Sie weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="aec3d-210">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="aec3d-211">Wir müssen auch Oberflächen Netze entfernen, die in unserer Oberflächen Mesh-Auflistung enthalten sind, aber nicht mehr in der System Sammlung enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="aec3d-211">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="aec3d-212">Zu diesem Zweck müssen wir etwas tun, das dem Gegenteil ähnelt, was wir soeben zum Hinzufügen und Aktualisieren von Meshes gezeigt haben. Wir durchlaufen die Sammlung unserer APP und überprüfen, ob die **GUID** in der System Sammlung enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="aec3d-212">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="aec3d-213">Wenn er sich nicht in der System Sammlung befindet, entfernen wir ihn von uns.</span><span class="sxs-lookup"><span data-stu-id="aec3d-213">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="aec3d-214">Aus unserem Ereignishandler in appmain. cpp:</span><span class="sxs-lookup"><span data-stu-id="aec3d-214">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="aec3d-215">Die Implementierung des Gitter Bereinigungs in realtimesurfakemeshrenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="aec3d-215">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="aec3d-216">Erfassen und Verwenden von Oberflächen Mesh-Daten Puffern</span><span class="sxs-lookup"><span data-stu-id="aec3d-216">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="aec3d-217">Das Abrufen der Oberflächen Mesh-Informationen war so einfach wie das Abrufen von Datenerfassung und das Verarbeiten von Aktualisierungen für diese Sammlung.</span><span class="sxs-lookup"><span data-stu-id="aec3d-217">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="aec3d-218">Nun erfahren Sie, wie Sie die Daten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="aec3d-218">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="aec3d-219">In unserem Codebeispiel haben wir uns entschieden, die Oberflächen Netze für das Rendering zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-219">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="aec3d-220">Dies ist ein gängiges Szenario zum einleben von holograms hinter realen Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-220">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="aec3d-221">Sie können auch die Meshes und die verarbeiteten Versionen von Ihnen darstellen, um dem Benutzer anzuzeigen, welche Bereiche des Raums gescannt werden, bevor Sie mit der Bereitstellung von APP-oder Spielfunktionen beginnen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-221">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="aec3d-222">Das Codebeispiel startet den Prozess, wenn er Oberflächen Mesh-Aktualisierungen von dem Ereignishandler empfängt, den wir im vorherigen Abschnitt beschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="aec3d-222">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="aec3d-223">Die wichtige Codezeile in dieser Funktion ist der Aufruf zum Aktualisieren des Oberflächen *Netzes*: bisher haben wir die Mesh-Informationen bereits verarbeitet, und wir sind im Begriff, den Scheitelpunkt und die Indexdaten für die Verwendung nach Bedarf abzurufen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-223">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="aec3d-224">Aus realtimesurfakemeshrenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="aec3d-224">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="aec3d-225">Der Beispielcode ist so konzipiert, dass eine Datenklasse, **surfacemesh**, Mesh-Datenverarbeitungs-und-Rendering behandelt.</span><span class="sxs-lookup"><span data-stu-id="aec3d-225">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="aec3d-226">Diese Netze stellen den **realtimesurfakemeshrenderer** tatsächlich eine Karte dar.</span><span class="sxs-lookup"><span data-stu-id="aec3d-226">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="aec3d-227">Jeder verfügt über einen Verweis auf den spatialsurfakemesh, von dem er stammt, und wir verwenden ihn immer dann, wenn wir auf den Gitter Scheitelpunkt oder Index Puffer zugreifen müssen oder eine Transformation für das Mesh abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-227">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="aec3d-228">Vorerst wird das Mesh als Update erforderlich gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="aec3d-228">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="aec3d-229">Aus "surfakemesh. cpp":</span><span class="sxs-lookup"><span data-stu-id="aec3d-229">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="aec3d-230">Wenn das Mesh das nächste Mal aufgefordert wird, sich selbst zu zeichnen, prüft es zuerst das Flag.</span><span class="sxs-lookup"><span data-stu-id="aec3d-230">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="aec3d-231">Wenn ein Update erforderlich ist, werden die Vertex-und Index Puffer auf der GPU aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="aec3d-231">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="aec3d-232">Zunächst rufen wir die Rohdaten Puffer ab:</span><span class="sxs-lookup"><span data-stu-id="aec3d-232">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="aec3d-233">Anschließend erstellen wir Direct3D-Geräte Puffer mit den Netz Daten, die von den hololens bereitgestellt werden:</span><span class="sxs-lookup"><span data-stu-id="aec3d-233">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="aec3d-234">**Hinweis:** Informationen zu der im vorherigen Code Ausschnitt verwendeten Hilfsfunktion "featedirectxbuffer" finden Sie im Codebeispiel für die Oberflächen Zuordnung: surfacemesh. cpp, getdatafromibuffer. h.</span><span class="sxs-lookup"><span data-stu-id="aec3d-234">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="aec3d-235">Die Geräte Ressourcen Erstellung ist nun abgeschlossen, und das Mesh wird als geladen und bereit für Update und Rendering.</span><span class="sxs-lookup"><span data-stu-id="aec3d-235">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="aec3d-236">Aktualisieren und renderoberflächen-Netzen</span><span class="sxs-lookup"><span data-stu-id="aec3d-236">Update and render surface meshes</span></span>

<span data-ttu-id="aec3d-237">Unsere surfacemesh-Klasse verfügt über eine spezialisierte Update-Funktion.</span><span class="sxs-lookup"><span data-stu-id="aec3d-237">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="aec3d-238">Jede [spatialsurfaesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) hat eine eigene Transformation, und in unserem Beispiel wird das aktuelle Koordinatensystem für den **spatialstationaryreferenceframe** verwendet, um die Transformation zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-238">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="aec3d-239">Anschließend wird der Modell Konstante Puffer auf der GPU aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="aec3d-239">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="aec3d-240">Wenn es an der Zeit ist, Oberflächen Netze zu rendern, führen wir vor dem Rendern der Auflistung einige Vorbereitungsaufgaben durch.</span><span class="sxs-lookup"><span data-stu-id="aec3d-240">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="aec3d-241">Wir richten die Shader-Pipeline für die aktuelle renderingkonfiguration ein und richten die Eingabe Assembler-Stufe ein.</span><span class="sxs-lookup"><span data-stu-id="aec3d-241">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="aec3d-242">Beachten Sie, dass die Hilfsklasse der Holographic-Kamera " **cameraresources. cpp** " bereits den Ansichts-/Projektions Konstanten-Puffer bereits eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="aec3d-242">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="aec3d-243">Aus **realtimesurfakemeshrenderer:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="aec3d-243">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="aec3d-244">Nachdem dies geschehen ist, werden wir unsere Netzen durchlaufen und jede einzelne zeichnen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-244">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="aec3d-245">**Hinweis:** Dieser Beispielcode ist nicht für die Verwendung einer beliebigen Art von Frustum-culelt optimiert, aber Sie sollten dieses Feature in Ihre APP einschließen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-245">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="aec3d-246">Die einzelnen Netzen sind für das Einrichten des Vertex-und Index Puffers, des STRIDE-und des Modell Transformations Konstanten Puffers verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="aec3d-246">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="aec3d-247">Wie bei dem spincube in der Windows Holographic-App-Vorlage werden wir mithilfe der Instanziierung zu stereoskopischen Puffern.</span><span class="sxs-lookup"><span data-stu-id="aec3d-247">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="aec3d-248">Von **surfakemesh::D RAW**:</span><span class="sxs-lookup"><span data-stu-id="aec3d-248">From **SurfaceMesh::Draw**:</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="aec3d-249">Renderingoptionen mit Oberflächen Zuordnung</span><span class="sxs-lookup"><span data-stu-id="aec3d-249">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="aec3d-250">Das Codebeispiel für die Oberflächen Zuordnung bietet Code für das reine Rendering von Oberflächen Netz Daten und für das Bildschirm Rendering von Oberflächen Mesh-Daten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-250">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="aec3d-251">Der von Ihnen gewählte Pfad bzw. beides hängt von Ihrer Anwendung ab.</span><span class="sxs-lookup"><span data-stu-id="aec3d-251">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="aec3d-252">In diesem Dokument werden beide Konfigurationen erläutert.</span><span class="sxs-lookup"><span data-stu-id="aec3d-252">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="aec3d-253">**Rendern von Okklusions Puffern für Holographic Effect**</span><span class="sxs-lookup"><span data-stu-id="aec3d-253">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="aec3d-254">Beginnen Sie, indem Sie die renderzielansicht für die aktuelle virtuelle Kamera löschen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-254">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="aec3d-255">Aus appmain. cpp:</span><span class="sxs-lookup"><span data-stu-id="aec3d-255">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="aec3d-256">Dies ist ein "Pre-Rendering"-Durchlauf.</span><span class="sxs-lookup"><span data-stu-id="aec3d-256">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="aec3d-257">Hier erstellen Sie einen oksions Puffer, indem Sie den Mesh-Renderer bitten, nur Tiefe zu Renderern.</span><span class="sxs-lookup"><span data-stu-id="aec3d-257">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="aec3d-258">In dieser Konfiguration wird eine renderzielansicht nicht angefügt, und der Mesh-Renderer legt die Pixel-Shader-Stufe auf **nullptr** fest, damit die GPU keine Pixel zeichnen kann.</span><span class="sxs-lookup"><span data-stu-id="aec3d-258">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="aec3d-259">Die Geometrie wird in den tiefen Puffer gerengt, und die Grafik Pipeline wird dort angehalten.</span><span class="sxs-lookup"><span data-stu-id="aec3d-259">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="aec3d-260">Wir können holograms mit einem zusätzlichen tiefen Test für den cloudverzeichnungs-Puffer für die Oberflächen Zuordnung zeichnen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-260">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="aec3d-261">In diesem Codebeispiel werden Pixel im Cube in einer anderen Farbe dargestellt, wenn Sie sich hinter einer Oberfläche befinden.</span><span class="sxs-lookup"><span data-stu-id="aec3d-261">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="aec3d-262">Aus appmain. cpp:</span><span class="sxs-lookup"><span data-stu-id="aec3d-262">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="aec3d-263">Basierend auf dem Code aus specialeffectpixelshader. HLSL:</span><span class="sxs-lookup"><span data-stu-id="aec3d-263">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="aec3d-264">**Hinweis:** Informationen zu unserer **gatherdepthless** -Routine finden Sie im Codebeispiel für die Oberflächen Zuordnung: specialeffectpixelshader. HLSL.</span><span class="sxs-lookup"><span data-stu-id="aec3d-264">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="aec3d-265">**Rendern von Oberflächen Mesh-Daten für die Anzeige**</span><span class="sxs-lookup"><span data-stu-id="aec3d-265">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="aec3d-266">Wir können auch einfach die Oberfläche für die Stereo Anzeige Puffer zeichnen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-266">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="aec3d-267">Wir haben uns entschieden, vollständige Gesichter mit Beleuchtung zu zeichnen, aber Sie können einen Wireframe zeichnen, Netzen vor dem Rendering verarbeiten, eine Textur Map anwenden usw.</span><span class="sxs-lookup"><span data-stu-id="aec3d-267">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="aec3d-268">Hier weist unser Codebeispiel den Mesh-Renderer an, die Auflistung zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="aec3d-268">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="aec3d-269">Dieses Mal geben wir keinen tiefen Durchlauf an, sondern fügen einen PixelShader an und vervollständigen die Renderingpipeline mithilfe der Ziele, die wir für die aktuelle virtuelle Kamera angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="aec3d-269">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="aec3d-270">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="aec3d-270">See also</span></span>
* [<span data-ttu-id="aec3d-271">Erstellen eines holographischen DirectX-Projekts</span><span class="sxs-lookup"><span data-stu-id="aec3d-271">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="aec3d-272">Windows. perception. Spatial-API</span><span class="sxs-lookup"><span data-stu-id="aec3d-272">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
