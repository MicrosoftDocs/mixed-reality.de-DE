---
title: Räumliche Zuordnung in DirectX
description: Erläutert, wie die räumliche Zuordnung in Ihrer DirectX-App implementiert wird. Dies umfasst eine ausführliche Erläuterung der Beispielanwendung für räumliche Zuordnung, die im universelle Windows-Plattform SDK enthalten ist.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, räumliche Zuordnung, Umgebung, Interaktion, DirectX, WinRT, API, Beispielcode, UWP, SDK, Exemplarische Vorgehensweise
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550696"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="0ad52-105">Räumliche Zuordnung in DirectX</span><span class="sxs-lookup"><span data-stu-id="0ad52-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="0ad52-106">In diesem Thema wird beschrieben, wie Sie eine [räumliche Zuordnung](spatial-mapping.md) in Ihrer DirectX-App implementieren.</span><span class="sxs-lookup"><span data-stu-id="0ad52-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="0ad52-107">Dies umfasst eine ausführliche Erläuterung der Beispielanwendung für räumliche Zuordnung, die im universelle Windows-Plattform SDK enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="0ad52-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="0ad52-108">In diesem Thema wird Code aus dem [holographicspatialmapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) -UWP-Codebeispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="0ad52-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="0ad52-109">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="0ad52-110">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="0ad52-111">DirectX-Entwicklungs Übersicht</span><span class="sxs-lookup"><span data-stu-id="0ad52-111">DirectX development overview</span></span>

<span data-ttu-id="0ad52-112">Die native Anwendungsentwicklung für räumliche Zuordnung verwendet die APIs im [Windows. perception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="0ad52-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="0ad52-113">Diese APIs bieten vollständige Kontrolle über die Funktionalität räumlicher Mapping in einer Weise, die direkt mit den von [Unity](spatial-mapping-in-unity.md)verfügbar gemachten räumlichen Mapping-APIs vergleichbar ist.</span><span class="sxs-lookup"><span data-stu-id="0ad52-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="0ad52-114">Perception-APIs</span><span class="sxs-lookup"><span data-stu-id="0ad52-114">Perception APIs</span></span>

<span data-ttu-id="0ad52-115">Folgende primäre Typen werden für die Entwicklung räumlicher Mapping bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="0ad52-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="0ad52-116">[Spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) stellt Informationen zu Oberflächen in anwendungsspezifischen Bereichen des Raums in der Nähe des Benutzers in Form von spatialsurfaceinfo-Objekten bereit.</span><span class="sxs-lookup"><span data-stu-id="0ad52-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="0ad52-117">[Spatialsurfaceinfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) beschreibt eine einzelne räumliche Oberfläche, einschließlich einer eindeutigen ID, eines umgebenden Volumes und einer Zeit der letzten Änderung.</span><span class="sxs-lookup"><span data-stu-id="0ad52-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="0ad52-118">Auf Anforderung wird ein spatialsurfakemesh asynchron bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="0ad52-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="0ad52-119">[Spatialsurfakemeshoptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) enthält Parameter, mit denen die von spatialsurfakeinfo angeforderten spatialsurfaesh-Objekte angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="0ad52-120">[Spatialsurfacemesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) stellt die Mesh-Daten für eine einzelne räumliche Oberfläche dar.</span><span class="sxs-lookup"><span data-stu-id="0ad52-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="0ad52-121">Die Daten für Scheitelpunkt Positionen, Scheitelpunkt normale und Dreieck Indizes sind in dem Element spatialsurfakemeschbuffer-Objekten enthalten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="0ad52-122">[Spatialsurfakemeschbuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) umschließt einen einzelnen Typ von Mesh-Daten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="0ad52-123">Beim Entwickeln einer Anwendung, die diese APIs verwendet, sieht Ihr grundlegender Programmablauf wie folgt aus (wie in der unten beschriebenen Beispielanwendung gezeigt):</span><span class="sxs-lookup"><span data-stu-id="0ad52-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="0ad52-124">**Einrichten von spatialsurfaceobserver**</span><span class="sxs-lookup"><span data-stu-id="0ad52-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="0ad52-125">Aufrufen von [requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), um sicherzustellen, dass der Benutzer die Berechtigung zum Verwenden der räumlichen Zuordnungsfunktionen des Geräts für die Anwendung erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="0ad52-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="0ad52-126">Instanziieren Sie ein spatialsurfaceobserver-Objekt.</span><span class="sxs-lookup"><span data-stu-id="0ad52-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="0ad52-127">Aufrufen von [setboundingvolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) , um die Bereiche anzugeben, in denen Sie Informationen über räumliche Oberflächen benötigen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="0ad52-128">Diese Bereiche können Sie in Zukunft ändern, indem Sie diese Funktion einfach erneut aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="0ad52-129">Jede Region wird mit einem [spatialboundingvolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)angegeben.</span><span class="sxs-lookup"><span data-stu-id="0ad52-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="0ad52-130">Registrieren Sie sich für das [observedsurfaceschangi-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , das ausgelöst wird, wenn neue Informationen über die räumlichen Oberflächen in den von Ihnen angegebenen Bereichen des Raums verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0ad52-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="0ad52-131">**Prozess-observedsurfaceschge-Ereignisse**</span><span class="sxs-lookup"><span data-stu-id="0ad52-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="0ad52-132">Aufrufen von [getobservedoberflächen](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) in Ihrem Ereignishandler, um eine Zuordnung der spatialsurfakeinfo-Objekte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="0ad52-133">Mithilfe dieser Karte können Sie die Datensätze aktualisieren, in denen räumliche Oberflächen [in der Benutzerumgebung vorhanden](spatial-mapping.md#mesh-caching)sind.</span><span class="sxs-lookup"><span data-stu-id="0ad52-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="0ad52-134">Für jedes spatialsurfaceinfo-Objekt können Sie [trygetbounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) Abfragen, um die räumlichen Blöcke der Oberfläche zu ermitteln, die in einem [räumlichen Koordinatensystem](coordinate-systems.md) Ihrer Wahl ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="0ad52-135">Wenn Sie ein Mesh für eine räumliche Oberfläche anfordern möchten, wenden Sie sich an [trycomputelatestmeshasync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="0ad52-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="0ad52-136">Sie können Optionen angeben, indem Sie die gewünschte Dichte der Dreiecke und das Format der zurückgegebenen Mesh-Daten angeben.</span><span class="sxs-lookup"><span data-stu-id="0ad52-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="0ad52-137">**Gitter empfangen und verarbeiten**</span><span class="sxs-lookup"><span data-stu-id="0ad52-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="0ad52-138">Jeder Aufrufen von trycomputelatestmeshasync gibt ein spatialsurfakemesh-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="0ad52-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="0ad52-139">Von diesem Objekt aus können Sie auf die enthaltenen spatialsurfaeschbuffer-Objekte zugreifen, um auf die Dreiecks Indizes, die Scheitelpunkt Positionen und (falls angefordert) vertexnormale des Netzes zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="0ad52-140">Diese Daten befinden sich in einem Format, das direkt mit den [Direct3D 11-APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) kompatibel ist, die zum Rendern von Netzen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="0ad52-141">Von hier aus kann die Anwendung optional eine Analyse oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Mesh-Daten durchführen und diese zum [Rendern](spatial-mapping.md#rendering) und zum Auftreten von physikalischer und- [Kollisionen](spatial-mapping.md#raycasting-and-collision)verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="0ad52-142">Ein wichtiges Detail ist, dass Sie eine Skalierung auf die mesvertexpositionen anwenden müssen (z. b. im Vertexshader, der zum Rendern der Meshes verwendet wird), um Sie von den optimierten ganzzahligen Einheiten, in denen Sie im Puffer gespeichert sind, in Meter zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="0ad52-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="0ad52-143">Sie können diese Skala abrufen, indem Sie [vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="0ad52-144">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="0ad52-144">Troubleshooting</span></span>
* <span data-ttu-id="0ad52-145">Vergessen Sie nicht, Mesh-Vertex-Positionen in Ihrem Vertexshader zu skalieren, indem Sie die von [spatialsurfakemesh. vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx) zurückgegebene Skala verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="0ad52-146">Exemplarische Vorgehensweise zum Codebeispiel für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="0ad52-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="0ad52-147">Das Codebeispiel für die [holografische räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) enthält Code, den Sie verwenden können, um mit dem Laden von Oberflächen Netzen in Ihre APP zu beginnen, einschließlich der Infrastruktur zum Verwalten und Rendern von Oberflächen Netzen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="0ad52-148">Nun erfahren Sie, wie Sie Ihrer DirectX-App Oberflächen Zuordnungsfunktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="0ad52-149">Sie können diesen Code dem Vorlagen Projekt für die [Windows Holographic-App](creating-a-holographic-directx-project.md) hinzufügen. Alternativ können Sie das oben erwähnte Codebeispiel durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="0ad52-150">Dieses Codebeispiel basiert auf der Windows Holographic-App-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="0ad52-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="0ad52-151">Einrichten Ihrer APP für die Verwendung der spatialperception-Funktion</span><span class="sxs-lookup"><span data-stu-id="0ad52-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="0ad52-152">Ihre APP muss die Funktion für räumliche Zuordnung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0ad52-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="0ad52-153">Dies ist erforderlich, da das räumliche Mesh eine Darstellung der Benutzerumgebung ist, die als private Daten betrachtet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0ad52-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="0ad52-154">Deklarieren Sie diese Funktion in der Datei "Package. appxmanifest" für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="0ad52-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="0ad52-155">Im Folgenden ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0ad52-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="0ad52-156">Die Funktion stammt aus dem **uap2** -Namespace.</span><span class="sxs-lookup"><span data-stu-id="0ad52-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="0ad52-157">Um Zugriff auf diesen Namespace in ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns* -Attribut &lt;in das Paket >-Element ein.</span><span class="sxs-lookup"><span data-stu-id="0ad52-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="0ad52-158">Im Folgenden ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0ad52-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="0ad52-159">Überprüfen der Funktions Unterstützung für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="0ad52-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="0ad52-160">Windows Mixed Reality unterstützt eine große Bandbreite von Geräten, darunter Geräte, die keine räumliche Zuordnung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="0ad52-161">Wenn Ihre APP eine räumliche Zuordnung verwenden oder eine räumliche Zuordnung verwenden muss, sollte Sie zum Bereitstellen von Funktionen überprüfen, ob die räumliche Zuordnung unterstützt wird, bevor Sie versuchen, Sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="0ad52-162">Wenn z. b. eine räumliche Zuordnung für Ihre Mixed Reality-App erforderlich ist, sollte eine Meldung angezeigt werden, wenn ein Benutzer versucht, die Anwendung auf einem Gerät ohne räumliche Zuordnung durchführen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="0ad52-163">Oder Sie können Ihre eigene virtuelle Umgebung möglicherweise anstelle der Umgebung des Benutzers Rendering, sodass Sie ein ähnliches Verhalten wie bei der Verfügbarkeit der räumlichen Zuordnung bietet.</span><span class="sxs-lookup"><span data-stu-id="0ad52-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="0ad52-164">In jedem Fall ermöglicht diese API Ihrer APP, zu erkennen, wann Sie keine räumlichen Zuordnungsdaten erhält, und antwortet auf die entsprechende Weise.</span><span class="sxs-lookup"><span data-stu-id="0ad52-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="0ad52-165">Stellen Sie zunächst sicher, dass der UWP-Vertrag auf der Ebene 4 oder höher ist, und fordern Sie dann spatialsurfaceobserver:: IsSupported () an, um das aktuelle Gerät auf Unterstützung für räumliche Zuordnung zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="0ad52-166">Dies wird im Kontext des Code Beispiels für die [Holographic-Zuordnung für räumliche Daten](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0ad52-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="0ad52-167">Die Unterstützung wird unmittelbar vor dem Anfordern des Zugriffs geprüft.</span><span class="sxs-lookup"><span data-stu-id="0ad52-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="0ad52-168">Die spatialsurfaceobserver:: IsSupported ()-API ist ab der SDK-Version 15063 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0ad52-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="0ad52-169">Richten Sie ggf. das Projekt auf die Platt Form Version 15063 zurück, bevor Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="0ad52-170">Beachten Sie Folgendes: Wenn der UWP-Vertrag niedriger als Ebene 4 ist, sollte die APP so vorgehen, als ob das Gerät eine räumliche Zuordnung durchführen kann.</span><span class="sxs-lookup"><span data-stu-id="0ad52-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="0ad52-171">Zugriff auf räumliche Zuordnungsdaten anfordern</span><span class="sxs-lookup"><span data-stu-id="0ad52-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="0ad52-172">Ihre APP muss die Berechtigung für den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Sie versuchen, einen Oberflächen Beobachter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="0ad52-173">Im folgenden finden Sie ein Beispiel, das auf dem Codebeispiel für die Oberflächen Zuordnung basiert. weitere Details finden Sie weiter unten auf dieser Seite:</span><span class="sxs-lookup"><span data-stu-id="0ad52-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="0ad52-174">Erstellen eines Oberflächen Beobachters</span><span class="sxs-lookup"><span data-stu-id="0ad52-174">Create a surface observer</span></span>

<span data-ttu-id="0ad52-175">Der **Windows::P erception:: Spatial:: Oberflächen** -Namespace enthält die [spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Klasse, mit der ein oder mehrere Volumes beobachtet werden, die Sie in einem [spatialcoordinatesystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)angeben.</span><span class="sxs-lookup"><span data-stu-id="0ad52-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="0ad52-176">Verwenden Sie eine [spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Instanz, um in Echtzeit auf Oberflächen Mesh-Daten zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="0ad52-177">Aus **appmain. h**:</span><span class="sxs-lookup"><span data-stu-id="0ad52-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="0ad52-178">Wie bereits im vorherigen Abschnitt erwähnt, müssen Sie den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Sie von Ihrer APP verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="0ad52-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="0ad52-179">Dieser Zugriff wird automatisch auf den hololens gewährt.</span><span class="sxs-lookup"><span data-stu-id="0ad52-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="0ad52-180">Als nächstes müssen Sie den Oberflächen Beobachter so konfigurieren, dass er ein bestimmtes Begrenzungs Volume beobachtet.</span><span class="sxs-lookup"><span data-stu-id="0ad52-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="0ad52-181">Hier wird ein Feld mit 20 x 20 x 5 Metern betrachtet, das sich am Ursprung des Koordinatensystems befindet.</span><span class="sxs-lookup"><span data-stu-id="0ad52-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="0ad52-182">Beachten Sie, dass Sie stattdessen mehrere Begrenzungs Volumes festlegen können.</span><span class="sxs-lookup"><span data-stu-id="0ad52-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="0ad52-183">*Dies ist Pseudocode:*</span><span class="sxs-lookup"><span data-stu-id="0ad52-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="0ad52-184">Es ist auch möglich, andere umgebende Formen (z. b. eine ansichtsansicht) oder ein Begrenzungsfeld zu verwenden, das keine Achsen Ausrichtung ist.</span><span class="sxs-lookup"><span data-stu-id="0ad52-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="0ad52-185">*Dies ist Pseudocode:*</span><span class="sxs-lookup"><span data-stu-id="0ad52-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="0ad52-186">Wenn Ihre APP etwas anders ausführen muss, wenn keine Oberflächen Zuordnungsdaten verfügbar sind, können Sie Code schreiben, um auf den Fall zu reagieren, in dem [spatialpertionaccessstatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) nicht **zulässig** ist, z. b. auf PCs mit immersiver Verwendung nicht zulässig. Geräte, die angefügt sind, weil diese Geräte nicht über Hardware für räumliche Zuordnung verfügen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="0ad52-187">Für diese Geräte sollten Sie sich stattdessen auf die räumliche Phase stützen, um Informationen zur Umgebung und Gerätekonfiguration des Benutzers zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="0ad52-188">Initialisieren und Aktualisieren der Surface-Mesh-Auflistung</span><span class="sxs-lookup"><span data-stu-id="0ad52-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="0ad52-189">Wenn der Oberflächen Beobachter erfolgreich erstellt wurde, können wir mit dem Initialisieren der Oberflächen Gitter Auflistung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="0ad52-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="0ad52-190">Hier verwenden wir die Pull Model-API, um den aktuellen Satz von beobachteten Oberflächen sofort abzurufen:</span><span class="sxs-lookup"><span data-stu-id="0ad52-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="0ad52-191">Es ist auch ein Push-Modell verfügbar, um Oberflächen Mesh-Daten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="0ad52-192">Sie können Ihre APP so entwerfen, dass nur das Pull-Modell verwendet wird, wenn Sie sich entscheiden. in diesem Fall rufen Sie alle so oft, einmal pro Frame oder innerhalb eines bestimmten Zeitraums, z. b. während der Spiel Einrichtung, Daten ab.</span><span class="sxs-lookup"><span data-stu-id="0ad52-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="0ad52-193">Wenn dies der Fall ist, ist der obige Code das, was Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="0ad52-194">In unserem Codebeispiel haben wir uns entschieden, die Verwendung beider Modelle zu pädagogischen Zwecken zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="0ad52-195">Hier abonnieren wir ein Ereignis, um aktuelle Oberflächen Mesh-Daten zu erhalten, wenn das System eine Änderung erkennt.</span><span class="sxs-lookup"><span data-stu-id="0ad52-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="0ad52-196">Unser Codebeispiel ist auch so konfiguriert, dass auf diese Ereignisse reagiert wird.</span><span class="sxs-lookup"><span data-stu-id="0ad52-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="0ad52-197">Sehen wir uns an, wie wir dies tun.</span><span class="sxs-lookup"><span data-stu-id="0ad52-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="0ad52-198">**HINWEIS:** Dies ist möglicherweise nicht die effizienteste Methode, mit der Ihre APP Mesh-Daten verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="0ad52-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="0ad52-199">Dieser Code wird aus Gründen der Übersichtlichkeit geschrieben und ist nicht optimiert.</span><span class="sxs-lookup"><span data-stu-id="0ad52-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="0ad52-200">Die Oberflächen Mesh-Daten werden in einer schreibgeschützten Zuordnung bereitgestellt, in der [spatialsurfaceinfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) -Objekte mithilfe von [Platform:: GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) als Schlüsselwerte gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="0ad52-201">Um diese Daten zu verarbeiten, betrachten wir zuerst die Schlüsselwerte, die nicht in unserer Sammlung sind.</span><span class="sxs-lookup"><span data-stu-id="0ad52-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="0ad52-202">Weitere Informationen zum Speichern der Daten in unserer Beispiel-App finden Sie weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="0ad52-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="0ad52-203">Wir müssen auch Oberflächen Netze entfernen, die in unserer Oberflächen Mesh-Auflistung enthalten sind, aber nicht mehr in der System Sammlung enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="0ad52-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="0ad52-204">Zu diesem Zweck müssen wir etwas tun, das dem Gegenteil ähnelt, was wir soeben zum Hinzufügen und Aktualisieren von Meshes gezeigt haben. Wir durchlaufen die Sammlung unserer APP und überprüfen, ob die **GUID** in der System Sammlung enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="0ad52-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="0ad52-205">Wenn er sich nicht in der System Sammlung befindet, entfernen wir ihn von uns.</span><span class="sxs-lookup"><span data-stu-id="0ad52-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="0ad52-206">Aus unserem Ereignishandler in appmain. cpp:</span><span class="sxs-lookup"><span data-stu-id="0ad52-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="0ad52-207">Die Implementierung des Gitter Bereinigungs in realtimesurfakemeshrenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="0ad52-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="0ad52-208">Erfassen und Verwenden von Oberflächen Mesh-Daten Puffern</span><span class="sxs-lookup"><span data-stu-id="0ad52-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="0ad52-209">Das Abrufen der Oberflächen Mesh-Informationen war so einfach wie das Abrufen von Datenerfassung und das Verarbeiten von Aktualisierungen für diese Sammlung.</span><span class="sxs-lookup"><span data-stu-id="0ad52-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="0ad52-210">Nun erfahren Sie, wie Sie die Daten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0ad52-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="0ad52-211">In unserem Codebeispiel haben wir uns entschieden, die Oberflächen Netze für das Rendering zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="0ad52-212">Dies ist ein gängiges Szenario zum einleben von holograms hinter realen Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="0ad52-213">Sie können auch die Meshes und die verarbeiteten Versionen von Ihnen darstellen, um dem Benutzer anzuzeigen, welche Bereiche des Raums gescannt werden, bevor Sie mit der Bereitstellung von APP-oder Spielfunktionen beginnen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="0ad52-214">Das Codebeispiel startet den Prozess, wenn er Oberflächen Mesh-Aktualisierungen von dem Ereignishandler empfängt, den wir im vorherigen Abschnitt beschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="0ad52-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="0ad52-215">Die wichtige Codezeile in dieser Funktion ist der Aufruf zum Aktualisieren des Oberflächen *Netzes*: bisher haben wir die Mesh-Informationen bereits verarbeitet, und wir sind im Begriff, den Scheitelpunkt und die Indexdaten für die Verwendung nach Bedarf abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="0ad52-216">Aus realtimesurfakemeshrenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="0ad52-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="0ad52-217">Der Beispielcode ist so konzipiert, dass eine Datenklasse, **surfacemesh**, Mesh-Datenverarbeitungs-und-Rendering behandelt.</span><span class="sxs-lookup"><span data-stu-id="0ad52-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="0ad52-218">Diese Netze stellen den **realtimesurfakemeshrenderer** tatsächlich eine Karte dar.</span><span class="sxs-lookup"><span data-stu-id="0ad52-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="0ad52-219">Jeder verfügt über einen Verweis auf den spatialsurfakemesh, von dem er stammt, und wir verwenden ihn immer dann, wenn wir auf den Gitter Scheitelpunkt oder Index Puffer zugreifen müssen oder eine Transformation für das Mesh abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="0ad52-220">Vorerst wird das Mesh als Update erforderlich gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="0ad52-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="0ad52-221">Aus "surfakemesh. cpp":</span><span class="sxs-lookup"><span data-stu-id="0ad52-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="0ad52-222">Wenn das Mesh das nächste Mal aufgefordert wird, sich selbst zu zeichnen, prüft es zuerst das Flag.</span><span class="sxs-lookup"><span data-stu-id="0ad52-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="0ad52-223">Wenn ein Update erforderlich ist, werden die Vertex-und Index Puffer auf der GPU aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0ad52-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="0ad52-224">Zunächst rufen wir die Rohdaten Puffer ab:</span><span class="sxs-lookup"><span data-stu-id="0ad52-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="0ad52-225">Anschließend erstellen wir Direct3D-Geräte Puffer mit den Netz Daten, die von den hololens bereitgestellt werden:</span><span class="sxs-lookup"><span data-stu-id="0ad52-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="0ad52-226">**HINWEIS:** Informationen zu der im vorherigen Code Ausschnitt verwendeten Hilfsfunktion "featedirectxbuffer" finden Sie im Codebeispiel für die Oberflächen Zuordnung: "Surfakemesh. cpp", "getdatafromibuffer. h".</span><span class="sxs-lookup"><span data-stu-id="0ad52-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="0ad52-227">Die Geräte Ressourcen Erstellung ist nun abgeschlossen, und das Mesh wird als geladen und bereit für Update und Rendering.</span><span class="sxs-lookup"><span data-stu-id="0ad52-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="0ad52-228">Aktualisieren und renderoberflächen-Netzen</span><span class="sxs-lookup"><span data-stu-id="0ad52-228">Update and render surface meshes</span></span>

<span data-ttu-id="0ad52-229">Unsere surfacemesh-Klasse verfügt über eine spezialisierte Update-Funktion.</span><span class="sxs-lookup"><span data-stu-id="0ad52-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="0ad52-230">Jede [spatialsurfaesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) hat eine eigene Transformation, und in unserem Beispiel wird das aktuelle Koordinatensystem für den **spatialstationaryreferenceframe** verwendet, um die Transformation zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="0ad52-231">Anschließend wird der Modell Konstante Puffer auf der GPU aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0ad52-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="0ad52-232">Wenn es an der Zeit ist, Oberflächen Netze zu rendern, führen wir vor dem Rendern der Auflistung einige Vorbereitungsaufgaben durch.</span><span class="sxs-lookup"><span data-stu-id="0ad52-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="0ad52-233">Wir richten die Shader-Pipeline für die aktuelle renderingkonfiguration ein und richten die Eingabe Assembler-Stufe ein.</span><span class="sxs-lookup"><span data-stu-id="0ad52-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="0ad52-234">Beachten Sie, dass die Hilfsklasse der Holographic-Kamera " **cameraresources. cpp** " bereits den Ansichts-/Projektions Konstanten-Puffer bereits eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="0ad52-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="0ad52-235">Aus **realtimesurfakemeshrenderer:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="0ad52-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="0ad52-236">Nachdem dies geschehen ist, werden wir unsere Netzen durchlaufen und jede einzelne zeichnen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="0ad52-237">**HINWEIS:** Dieser Beispielcode ist nicht für die Verwendung einer beliebigen Art von Frustum-culelt optimiert, aber Sie sollten dieses Feature in Ihre APP einschließen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="0ad52-238">Die einzelnen Netzen sind für das Einrichten des Vertex-und Index Puffers, des STRIDE-und des Modell Transformations Konstanten Puffers verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="0ad52-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="0ad52-239">Wie bei dem spincube in der Windows Holographic-App-Vorlage werden wir mithilfe der Instanziierung zu stereoskopischen Puffern.</span><span class="sxs-lookup"><span data-stu-id="0ad52-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="0ad52-240">Von **surfakemesh::D RAW**:</span><span class="sxs-lookup"><span data-stu-id="0ad52-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="0ad52-241">Renderingoptionen mit Oberflächen Zuordnung</span><span class="sxs-lookup"><span data-stu-id="0ad52-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="0ad52-242">Das Codebeispiel für die Oberflächen Zuordnung bietet Code für das reine Rendering von Oberflächen Netz Daten und für das Bildschirm Rendering von Oberflächen Mesh-Daten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="0ad52-243">Der von Ihnen gewählte Pfad bzw. beides hängt von Ihrer Anwendung ab.</span><span class="sxs-lookup"><span data-stu-id="0ad52-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="0ad52-244">In diesem Dokument werden beide Konfigurationen erläutert.</span><span class="sxs-lookup"><span data-stu-id="0ad52-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="0ad52-245">**Rendern von Okklusions Puffern für Holographic Effect**</span><span class="sxs-lookup"><span data-stu-id="0ad52-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="0ad52-246">Beginnen Sie, indem Sie die renderzielansicht für die aktuelle virtuelle Kamera löschen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="0ad52-247">Aus appmain. cpp:</span><span class="sxs-lookup"><span data-stu-id="0ad52-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="0ad52-248">Dies ist ein "Pre-Rendering"-Durchlauf.</span><span class="sxs-lookup"><span data-stu-id="0ad52-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="0ad52-249">Hier erstellen Sie einen oksions Puffer, indem Sie den Mesh-Renderer bitten, nur Tiefe zu Renderern.</span><span class="sxs-lookup"><span data-stu-id="0ad52-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="0ad52-250">In dieser Konfiguration wird eine renderzielansicht nicht angefügt, und der Mesh-Renderer legt die Pixel-Shader-Stufe auf **nullptr** fest, damit die GPU keine Pixel zeichnen kann.</span><span class="sxs-lookup"><span data-stu-id="0ad52-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="0ad52-251">Die Geometrie wird in den tiefen Puffer gerengt, und die Grafik Pipeline wird dort angehalten.</span><span class="sxs-lookup"><span data-stu-id="0ad52-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="0ad52-252">Wir können holograms mit einem zusätzlichen tiefen Test für den cloudverzeichnungs-Puffer für die Oberflächen Zuordnung zeichnen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="0ad52-253">In diesem Codebeispiel werden Pixel im Cube in einer anderen Farbe dargestellt, wenn Sie sich hinter einer Oberfläche befinden.</span><span class="sxs-lookup"><span data-stu-id="0ad52-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="0ad52-254">Aus appmain. cpp:</span><span class="sxs-lookup"><span data-stu-id="0ad52-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="0ad52-255">Basierend auf dem Code aus specialeffectpixelshader. HLSL:</span><span class="sxs-lookup"><span data-stu-id="0ad52-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="0ad52-256">**Hinweis**: Informationen zu unserer **gatherdepthless** -Routine finden Sie im Codebeispiel für die Oberflächen Zuordnung: Specialeffectpixelshader. HLSL.</span><span class="sxs-lookup"><span data-stu-id="0ad52-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="0ad52-257">**Rendern von Oberflächen Mesh-Daten für die Anzeige**</span><span class="sxs-lookup"><span data-stu-id="0ad52-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="0ad52-258">Wir können auch einfach die Oberfläche für die Stereo Anzeige Puffer zeichnen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="0ad52-259">Wir haben uns entschieden, vollständige Gesichter mit Beleuchtung zu zeichnen, aber Sie können einen Wireframe zeichnen, Netzen vor dem Rendering verarbeiten, eine Textur Map anwenden usw.</span><span class="sxs-lookup"><span data-stu-id="0ad52-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="0ad52-260">Hier weist unser Codebeispiel den Mesh-Renderer an, die Auflistung zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="0ad52-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="0ad52-261">Dieses Mal geben wir keinen tiefen Durchlauf an, sondern fügen einen PixelShader an und vervollständigen die Renderingpipeline mithilfe der Ziele, die wir für die aktuelle virtuelle Kamera angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="0ad52-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="0ad52-262">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0ad52-262">See also</span></span>
* [<span data-ttu-id="0ad52-263">Erstellen eines holographischen DirectX-Projekts</span><span class="sxs-lookup"><span data-stu-id="0ad52-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="0ad52-264">Windows. perception. Spatial-API</span><span class="sxs-lookup"><span data-stu-id="0ad52-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
