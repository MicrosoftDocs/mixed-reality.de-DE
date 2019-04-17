---
title: Räumliche Zuordnung in DirectX
description: Erläutert, wie Sie räumliche Zuordnung in DirectX-Apps zu implementieren. Dies schließt eine ausführliche Erläuterung der beispielanwendung räumliche Zuordnung, die mit dem Universal Windows Platform SDK enthalten ist.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed Reality, räumliche Zuordnung, Umgebung, Interaktion, Directx, Winrt, api, Beispielcode, UWP, SDK, exemplarische Vorgehensweise
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605135"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="22ae1-105">Räumliche Zuordnung in DirectX</span><span class="sxs-lookup"><span data-stu-id="22ae1-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="22ae1-106">In diesem Thema wird beschrieben, wie implementieren [räumliche Zuordnung](spatial-mapping.md) in DirectX-Apps.</span><span class="sxs-lookup"><span data-stu-id="22ae1-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="22ae1-107">Dies schließt eine ausführliche Erläuterung der beispielanwendung räumliche Zuordnung, die mit dem Universal Windows Platform SDK enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="22ae1-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="22ae1-108">In diesem Thema verwendet den Code aus der [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP-Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="22ae1-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="22ae1-109">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="22ae1-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="22ae1-110">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="22ae1-111">Übersicht über die Entwicklung von DirectX</span><span class="sxs-lookup"><span data-stu-id="22ae1-111">DirectX development overview</span></span>

<span data-ttu-id="22ae1-112">Entwicklung von systemeigenen Anwendungen für räumliche Zuordnung verwendet, die APIs unter dem [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) Namespace.</span><span class="sxs-lookup"><span data-stu-id="22ae1-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="22ae1-113">Diese APIs bieten Vollzugriff auf räumliche Mapping-Funktion direkt auf die räumliche Zuordnung APIs verfügbar gemacht werden, indem Sie analog [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="22ae1-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="22ae1-114">Perception-APIs</span><span class="sxs-lookup"><span data-stu-id="22ae1-114">Perception APIs</span></span>

<span data-ttu-id="22ae1-115">Die primären Typen für die räumliche Zuordnung Entwicklung lauten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="22ae1-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="22ae1-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) enthält Informationen über die Flächen in anwendungsspezifische Regionen des Speicherplatzes in der Nähe der Benutzer in Form von SpatialSurfaceInfo-Objekten.</span><span class="sxs-lookup"><span data-stu-id="22ae1-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="22ae1-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) wird beschrieben, eine einzelne Zusammenführungsmechanismus räumliche Oberfläche, einschließlich einer eindeutigen ID, die umgebenden Volume und die Uhrzeit der letzten Änderung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="22ae1-118">Sie erhalten eine SpatialSurfaceMesh asynchron auf Anfrage.</span><span class="sxs-lookup"><span data-stu-id="22ae1-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="22ae1-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) enthält Parameter, die zur Anpassung der SpatialSurfaceMesh-Objekten, die vom SpatialSurfaceInfo angefordert.</span><span class="sxs-lookup"><span data-stu-id="22ae1-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="22ae1-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) die Mesh-Daten für eine einzelne räumliche Oberfläche darstellt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="22ae1-121">Die Daten für die Vertexpositionen, Vertex Normals und Dreiecksindizes ist in SpatialSurfaceMeshBuffer Memberobjekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="22ae1-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="22ae1-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) dient als Wrapper für einen einzelnen Zugriffstyp für Mesh-Daten.</span><span class="sxs-lookup"><span data-stu-id="22ae1-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="22ae1-123">Bei der Entwicklung einer Anwendung, die mithilfe dieser APIs sieht der basic-Programm-Flow (wie in der beispielanwendung, die unten beschriebenen):</span><span class="sxs-lookup"><span data-stu-id="22ae1-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="22ae1-124">**Richten Sie Ihre SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="22ae1-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="22ae1-125">Rufen Sie ["requestaccessasync"](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), um sicherzustellen, dass der Benutzer über die Berechtigung für Ihre Anwendung zur Verwendung von Funktionen des Geräts räumliche Zuordnung erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="22ae1-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="22ae1-126">Instanziieren Sie ein SpatialSurfaceObserver-Objekt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="22ae1-127">Rufen Sie [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) Regionen des Speicherplatzes angeben, in dem Informationen zu räumlichen Flächen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="22ae1-128">Sie können diese Regionen in Zukunft ändern, indem Sie einfach erneut aufrufen dieser Funktion.</span><span class="sxs-lookup"><span data-stu-id="22ae1-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="22ae1-129">Jede Region angegeben ist, mit einem [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="22ae1-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="22ae1-130">Registrieren Sie sich für die [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) -Ereignis, das ausgelöst wird, sobald neue Informationen zu den räumlichen Oberflächen in den Regionen Speicherplatz verfügbar sind, Sie angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="22ae1-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="22ae1-131">**Verarbeiten von Ereignissen ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="22ae1-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="22ae1-132">Rufen Sie im Ereignishandler, [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) erhalten Sie eine Zuordnung von SpatialSurfaceInfo-Objekten.</span><span class="sxs-lookup"><span data-stu-id="22ae1-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="22ae1-133">Mithilfe dieser Zuordnung, können Sie Ihre Einträge von der räumlichen Oberflächen aktualisieren [vorhanden sind, in der Umgebung des Benutzers](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="22ae1-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="22ae1-134">Für jedes Objekt SpatialSurfaceInfo, können Sie Abfragen [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) um zu bestimmen, die räumliche Blöcke der Oberfläche, ausgedrückt in einem [räumliche Koordinatensystem](coordinate-systems.md) Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="22ae1-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="22ae1-135">Wenn Sie Mesh für eine räumliche Fläche anfordern möchten, rufen Sie [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="22ae1-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="22ae1-136">Sie können Optionen festlegen, die gewünschten Dichte der Dreiecke und das Format der zurückgegebenen Mesh Daten angeben.</span><span class="sxs-lookup"><span data-stu-id="22ae1-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="22ae1-137">**Empfangen und Verarbeiten von Netz**</span><span class="sxs-lookup"><span data-stu-id="22ae1-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="22ae1-138">Jeder Aufruf von TryComputeLatestMeshAsync wird Aysnchronously geben eine SpatialSurfaceMesh-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="22ae1-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="22ae1-139">Von diesem Objekt können Sie die enthaltenen SpatialSurfaceMeshBuffer-Objekte zugreifen, um Zugriff auf die Dreiecksindizes und Vertexpositionen und (falls angefordert) flächenspezifische des Mesh.</span><span class="sxs-lookup"><span data-stu-id="22ae1-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="22ae1-140">Diese Daten werden in einem Format direkt kompatibel mit der [Direct3D 11-API](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) zum Rendern der Gitter verwendet.</span><span class="sxs-lookup"><span data-stu-id="22ae1-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="22ae1-141">Von hier aus Ihrer Anwendung optional Analyse ausführen kann oder [Verarbeitung](spatial-mapping.md#mesh-processing) Mesh Daten ein, und verwenden dieses Zugriffstokens für [Rendering](spatial-mapping.md#rendering) und physikalische Eigenschaften [feinheiten beim Raycasting und kollisionserkennung](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="22ae1-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="22ae1-142">Ein wichtiges Detail zu beachten ist, müssen Sie eine Skalierung auf die Mesh-Vertexpositionen (z. B. in den Vertex-Shader, der zum Rendern der Gitter verwendet wird) anwenden, Zähler um sie aus den optimierten Ganzzahl Einheiten konvertieren in der sie in den Puffer zu gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="22ae1-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="22ae1-143">Sie können diese Skalierung abrufen, durch den Aufruf [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="22ae1-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="22ae1-144">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="22ae1-144">Troubleshooting</span></span>
* <span data-ttu-id="22ae1-145">Vergessen Sie nicht, Netz Vertexpositionen in Ihre Vertex-Shader, der unter Verwendung der Dezimalstellen, die vom skalieren [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="22ae1-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="22ae1-146">Exemplarische Vorgehensweise räumliche Zuordnung code</span><span class="sxs-lookup"><span data-stu-id="22ae1-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="22ae1-147">Die [Holographic räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) Codebeispiel enthält Code, der für den Einstieg in die Oberfläche Gitter in Ihre app, einschließlich der Infrastruktur zur Verwaltung von laden können und die Renderingoberfläche Gitter.</span><span class="sxs-lookup"><span data-stu-id="22ae1-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="22ae1-148">Nun führen wir durch die Oberfläche Zuordnungsfunktion DirectX-Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="22ae1-149">Sie können diesen Code zum Hinzufügen Ihrer [Windows Holographic-app-Vorlage](creating-a-holographic-directx-project.md) -Projekt, oder Sie mithilfe des Durchsuchens im oben erwähnten Beispiels nachvollziehen können.</span><span class="sxs-lookup"><span data-stu-id="22ae1-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="22ae1-150">Dieses Codebeispiel basiert auf Windows Holographic-app-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="22ae1-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="22ae1-151">Richten Sie Ihre app, um die SpatialPerception-Funktion verwenden</span><span class="sxs-lookup"><span data-stu-id="22ae1-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="22ae1-152">Ihre app muss die räumliche Zuordnungsfunktion verwenden können.</span><span class="sxs-lookup"><span data-stu-id="22ae1-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="22ae1-153">Dies ist erforderlich, da das räumliche Netz eine Darstellung der Umgebung des Benutzers, ist, die private Daten angesehen werden kann.</span><span class="sxs-lookup"><span data-stu-id="22ae1-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="22ae1-154">Deklarieren Sie diese Funktion wird in der Datei "Package.appxmanifest" für Ihre app ein.</span><span class="sxs-lookup"><span data-stu-id="22ae1-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="22ae1-155">Im Folgenden ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="22ae1-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="22ae1-156">Die Funktion stammt aus dem **uap2** Namespace.</span><span class="sxs-lookup"><span data-stu-id="22ae1-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="22ae1-157">Um Zugriff auf diesen Namespace in Ihrem Manifest zu erhalten, fügen Sie ihn als einen *Xlmns* -Attribut in der &lt;Paket > Element.</span><span class="sxs-lookup"><span data-stu-id="22ae1-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="22ae1-158">Im Folgenden ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="22ae1-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="22ae1-159">Überprüfen Sie für die Unterstützung für räumliche Zuordnung-Funktion</span><span class="sxs-lookup"><span data-stu-id="22ae1-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="22ae1-160">Windows Mixed Reality unterstützt eine Vielzahl von Geräten, einschließlich Geräte, die räumliche Zuordnung nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="22ae1-161">Wenn Ihre app räumliche Zuordnung können oder räumliche Zuordnung verwenden muss, um Funktionen bereitzustellen, sollten sie sicherstellen, dass räumliche Zuordnung unterstützt wird, bevor Sie versuchen, die sie verwenden überprüfen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="22ae1-162">Z. B. wenn räumliche Zuordnung Ihrer mixed Reality-app erforderlich ist, sollten sie eine entsprechende Meldung angezeigt, wenn ein Benutzer versucht, die es auf ein Gerät ohne räumliche Zuordnung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="22ae1-163">Oder Ihre app möglicherweise zum Rendern einer eigenen virtuellen Umgebung anstelle der Umgebung des Benutzers, gleichzeitig eine Methode, die ähnelt dem, was geschieht, wenn räumliche Zuordnung zur Verfügung standen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="22ae1-164">In jedem Fall kann diese API Ihrer app zu beachten, wenn es nicht räumliche Zuordnungsdaten abrufen und auf die geeignete Weise reagieren.</span><span class="sxs-lookup"><span data-stu-id="22ae1-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="22ae1-165">Um das aktuelle Gerät für die Unterstützung für räumliche Zuordnung überprüfen zu können, stellen Sie zunächst sicher, dass der UWP-Vertrag auf Ebene 4 oder höher ist, und rufen Sie dann die SpatialSurfaceObserver::IsSupported() aus.</span><span class="sxs-lookup"><span data-stu-id="22ae1-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="22ae1-166">Hier ist wie das geht im Rahmen der [Holographic räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="22ae1-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="22ae1-167">Unterstützung wird unmittelbar vor das Anfordern des Zugriffs überprüft.</span><span class="sxs-lookup"><span data-stu-id="22ae1-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="22ae1-168">Die SpatialSurfaceObserver::IsSupported()-API steht im SDK, Version 15063 ab.</span><span class="sxs-lookup"><span data-stu-id="22ae1-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="22ae1-169">Bei Bedarf neu zuweisen Sie Ihr Projekt auf die Plattformversion 15063 vor der Verwendung dieser API.</span><span class="sxs-lookup"><span data-stu-id="22ae1-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="22ae1-170">Beachten Sie, dass bei der UWP-Vertrag kleiner als Stufe 4 ist, die app fortgesetzt werden soll, als wäre die räumliche Zuordnung durchführen kann.</span><span class="sxs-lookup"><span data-stu-id="22ae1-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="22ae1-171">Anfordern des Zugriffs auf den spatial Zuordnen von Daten</span><span class="sxs-lookup"><span data-stu-id="22ae1-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="22ae1-172">Ihre app muss zum Anfordern von Berechtigungen für den Datenzugriff räumliche Zuordnung, bevor Sie versuchen, die Oberfläche Beobachter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="22ae1-173">Hier ist ein Beispiel anhand unserer Zuordnen von Surface-Codebeispiel, mit weiteren Details bereitgestellt weiter unten auf dieser Seite:</span><span class="sxs-lookup"><span data-stu-id="22ae1-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="22ae1-174">Erstellen Sie einen Beobachter Oberflächen</span><span class="sxs-lookup"><span data-stu-id="22ae1-174">Create a surface observer</span></span>

<span data-ttu-id="22ae1-175">Die **Windows::Perception::Spatial::Surfaces** Namespace enthält die [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Klasse, die ein oder mehrere Volumes, die Sie angeben berücksichtigt, in einem [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="22ae1-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="22ae1-176">Verwenden einer [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) Instanz für den Datenzugriff über die Oberfläche Mesh in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="22ae1-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="22ae1-177">Von **AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="22ae1-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="22ae1-178">Wie im vorherigen Abschnitt erwähnt, müssen Sie den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Ihre app verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="22ae1-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="22ae1-179">Dieser Zugriff wird automatisch auf die HoloLens gewährt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="22ae1-180">Als Nächstes müssen Sie den Oberflächen Beobachter, um zu beobachten, ein bestimmtes umgebendes Volume zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="22ae1-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="22ae1-181">Hier stellen wir ein Dialogfeld mit der 20 x 20 x 5-Zähler, um den Ursprung des Koordinatensystems zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="22ae1-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="22ae1-182">Beachten Sie, dass Sie mehrere umgebende Volumes stattdessen festlegen können.</span><span class="sxs-lookup"><span data-stu-id="22ae1-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="22ae1-183">*Dies ist der Pseudocode:*</span><span class="sxs-lookup"><span data-stu-id="22ae1-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="22ae1-184">Es ist auch möglich, andere umgebenden Formen – z. B. eine Frustums Ansicht verwenden oder ein umgebendes Felds an, die nicht Achse ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="22ae1-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="22ae1-185">*Dies ist der Pseudocode:*</span><span class="sxs-lookup"><span data-stu-id="22ae1-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="22ae1-186">Wenn Ihre app muss etwas anders machen, wenn Surface Zuordnen von Daten nicht verfügbar ist, können Sie schreiben Code zum Antworten auf die Groß-/Kleinschreibung, in denen die [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) nicht **zulässige** – z. B. Es sind nicht zulässig auf PCs mit immersive Geräten, die angefügt werden, da diese Geräte der Hardware für räumliche Zuordnung nicht.</span><span class="sxs-lookup"><span data-stu-id="22ae1-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="22ae1-187">Für diese Geräte sollten Sie stattdessen auf den spatial Informationen zu Konfiguration und Umgebung des Benutzers verlassen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="22ae1-188">Initialisieren Sie und aktualisieren Sie die Oberfläche Mesh-Sammlung</span><span class="sxs-lookup"><span data-stu-id="22ae1-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="22ae1-189">Wenn der Beobachter Oberfläche wurde erfolgreich erstellt wurde, können Sie zum Initialisieren unserer Oberfläche Mesh-Auflistung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="22ae1-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="22ae1-190">Hier verwenden wir die Pull-Modell-API, um den aktuellen Satz von beobachteten Flächen sofort zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="22ae1-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="22ae1-191">Es gibt auch ein Push-Modell, das zum Abrufen von Daten von Surface Mesh verfügbar.</span><span class="sxs-lookup"><span data-stu-id="22ae1-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="22ae1-192">Sie sind kostenlos, Entwerfen Sie Ihre app nur das Pullmodell verwenden, wenn Sie auswählen, bei dem Sie Daten regelmäßig - abrufen müssen, z. B. einmal pro Frame – oder während eines bestimmten Zeitraums, z. B. während des Setups von Spielen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="22ae1-193">Wenn dies der Fall ist, ist der obige Code an, was Sie.</span><span class="sxs-lookup"><span data-stu-id="22ae1-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="22ae1-194">In unserem Codebeispiel haben wir die Verwendung beider Modelle pädagogischer Natur zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="22ae1-195">Hier, wir ein Ereignis abonnieren, die auf dem neuesten Stand Oberfläche Mesh-Daten zu erhalten, wenn das System eine Änderung erkennt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="22ae1-196">Unser Beispiel ist auch auf diese Ereignisse reagieren konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="22ae1-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="22ae1-197">Betrachten Sie wie wir dies getan haben.</span><span class="sxs-lookup"><span data-stu-id="22ae1-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="22ae1-198">**HINWEIS:** Dies möglicherweise nicht die effizienteste Methode für Ihre app, die Mesh-Daten verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="22ae1-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="22ae1-199">Dieser Code wird aus Gründen der Übersichtlichkeit geschrieben und ist nicht optimiert.</span><span class="sxs-lookup"><span data-stu-id="22ae1-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="22ae1-200">Die Oberfläche Mesh-Daten werden in einer nur-Lese Zuordnung, die speichert bereitgestellt [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) -Objekte mit [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) als Schlüsselwerte.</span><span class="sxs-lookup"><span data-stu-id="22ae1-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="22ae1-201">Um diese Daten zu verarbeiten, geht es zuerst für die Schlüsselwerte, die nicht in der Sammlung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="22ae1-202">Informationen zur Speicherung der das in unserem Beispiel-app werden weiter unten in diesem Thema angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="22ae1-203">Wir müssen auch Oberfläche Gitter zu entfernen, die in der Entwurfsoberfläche Mesh-Sammlung sind, aber, die nicht in der Auflistung nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="22ae1-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="22ae1-204">Zu diesem Zweck müssen wir möchten Sie etwas Ähnliches wie das Gegenteil von was wir gerade gezeigt haben für das Hinzufügen und Aktualisieren von Gitter. Schleife in unseren app Sammlung und Prüfung, ob die **Guid** wir haben in der Auflistung ist.</span><span class="sxs-lookup"><span data-stu-id="22ae1-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="22ae1-205">Wenn es sich nicht in der Auflistung ist, können wir es aus unsere entfernen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="22ae1-206">Von der Ereignishandler in AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="22ae1-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="22ae1-207">Die Implementierung des Mesh-Bereinigung in RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="22ae1-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="22ae1-208">Abrufen und Verwenden von Surface-Netz von Datenpuffern</span><span class="sxs-lookup"><span data-stu-id="22ae1-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="22ae1-209">Die Oberfläche von meshinformationen war so einfach wie das Abrufen einer Datensammlung und die Verarbeitung der Updates für diese Sammlung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="22ae1-210">Nun, wir uns ausführlich auf, wie Sie die Daten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="22ae1-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="22ae1-211">In unserem Codebeispiel haben wir die Oberfläche Netze für das Rendering zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="22ae1-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="22ae1-212">Dies ist ein häufiges Szenario für occluding Hologramme hinter realen Flächen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="22ae1-213">Sie können auch Rendern der Gitter oder verarbeitete Versionen zu rendern, um dem Benutzer anzuzeigen, welche Bereiche der werden Raum überprüft, bevor Sie beginnen, App- oder Spiele-Funktionalität bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="22ae1-214">Im Codebeispiel wird der Prozess beim Empfang von Updates für Surface-Netz aus dem Ereignishandler, die wir im vorherigen Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="22ae1-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="22ae1-215">Die wichtige Zeile des Codes in dieser Funktion ist der Aufruf zum Aktualisieren der Oberfläche *mesh*: zu diesem Zeitpunkt haben wir bereits die Mesh-Informationen verarbeitet, und Sie können die Vertex- und Daten für die Verwendung abgerufen werden, wie wir nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="22ae1-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="22ae1-216">Von RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="22ae1-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="22ae1-217">Unserem Beispielcode wurde entwickelt, damit eine Datenklasse **SurfaceMesh**, Handles Mesh Daten verarbeiten und rendern.</span><span class="sxs-lookup"><span data-stu-id="22ae1-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="22ae1-218">Diese Meshes sind, was die **RealtimeSurfaceMeshRenderer** tatsächlich hält eine Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="22ae1-219">Jeweils enthält einen Verweis auf die SpatialSurfaceMesh er stammt, und wir verwenden sie jedes Mal, die Zugriff auf die Mesh-Vertex oder Index-Puffer oder eine Transformation für das Netz abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="22ae1-220">Vorerst flag wir das Netz als ein Update erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22ae1-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="22ae1-221">Von SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="22ae1-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="22ae1-222">Beim nächsten Mesh aufgefordert wird, selbst zeichnen wird das Flag zuerst überprüft.</span><span class="sxs-lookup"><span data-stu-id="22ae1-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="22ae1-223">Wenn ein Update erforderlich ist, werden die Vertex- und Indexpuffer auf der GPU aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="22ae1-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="22ae1-224">Zunächst rufen wir die Rohdaten-Puffer:</span><span class="sxs-lookup"><span data-stu-id="22ae1-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="22ae1-225">Klicken Sie dann erstellen Puffer, die wir Direct3D-Gerät mit den Netzdaten die HoloLens:</span><span class="sxs-lookup"><span data-stu-id="22ae1-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="22ae1-226">**HINWEIS:** Die CreateDirectXBuffer-Hilfsfunktion, der im vorherigen Codeausschnitt verwendet wird finden Sie im Codebeispiel Oberfläche zuordnen: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span><span class="sxs-lookup"><span data-stu-id="22ae1-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="22ae1-227">Der ressourcenerstellung Gerät ist jetzt abgeschlossen, und das Netz gilt werden geladen und bereit für die Aktualisierung und zu rendern.</span><span class="sxs-lookup"><span data-stu-id="22ae1-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="22ae1-228">Aktualisieren und zu Rendern der Entwurfsoberfläche Gitter</span><span class="sxs-lookup"><span data-stu-id="22ae1-228">Update and render surface meshes</span></span>

<span data-ttu-id="22ae1-229">Unsere SurfaceMesh-Klasse verfügt über eine spezielle Update-Funktion.</span><span class="sxs-lookup"><span data-stu-id="22ae1-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="22ae1-230">Jede [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) verfügt über eine eigene Transformation und in diesem Beispiel verwendet das aktuelle Koordinatensystem für unsere **SpatialStationaryReferenceFrame** , die Transformation abzurufen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="22ae1-231">Anschließend wird den Modell-Konstantenpuffer auf der GPU aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="22ae1-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="22ae1-232">Wenn es Zeit, die zum Rendern der Entwurfsoberfläche Gitter ist, führen wir einige vorbereitende arbeiten, vor dem Rendern der Auflistung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="22ae1-233">Wir richten die Shader-Pipeline für die aktuelle Rendering-Konfiguration, und richten wir die Eingabe-Assembler-Stufe.</span><span class="sxs-lookup"><span data-stu-id="22ae1-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="22ae1-234">Beachten Sie, dass die Hilfsklasse holographic Kamera **CameraResources.cpp** bereits eingerichtet hat den Konstantenpuffer Ansichts-und Projektionsmatrix jetzt.</span><span class="sxs-lookup"><span data-stu-id="22ae1-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="22ae1-235">Von **RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="22ae1-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="22ae1-236">Sobald dies geschehen ist, werden wir auf unsere Gitter Schleife und teilen Sie jeweils auf sich selbst zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="22ae1-237">**HINWEIS:** Dieser Beispielcode ist nicht optimiert, um jede Art von Frustums culling zu verwenden, aber Sie sollten diese Funktion in Ihrer app einschließen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="22ae1-238">Die einzelne Gitter sind verantwortlich für das Einrichten der Vertex- und Puffer Stride und Konstantenpuffer des Modell-Transformation.</span><span class="sxs-lookup"><span data-stu-id="22ae1-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="22ae1-239">Wie bei der sich drehenden Würfels in der Windows Holographic-app-Vorlage, Rendern wir stereoskopische Puffern, die mit der Instanziierung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="22ae1-240">Von **SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="22ae1-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="22ae1-241">Rendern von Funktionen mit Oberfläche zuordnen</span><span class="sxs-lookup"><span data-stu-id="22ae1-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="22ae1-242">Das Zuordnen von Surface-Codebeispiel bietet verdecken nur Rendern der Entwurfsoberfläche Mesh-Daten und auf dem Bildschirm Rendern der Entwurfsoberfläche Mesh-Daten.</span><span class="sxs-lookup"><span data-stu-id="22ae1-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="22ae1-243">Welchen Pfad Sie auswählen – oder beides – hängt von Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="22ae1-244">Beide Konfigurationen in diesem Dokument erläutert.</span><span class="sxs-lookup"><span data-stu-id="22ae1-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="22ae1-245">**Rendering verdecken Puffer für die holographic Auswirkungen**</span><span class="sxs-lookup"><span data-stu-id="22ae1-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="22ae1-246">Starten Sie durch die renderzielansicht für die aktuelle virtuelle Kamera zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="22ae1-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="22ae1-247">Von AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="22ae1-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="22ae1-248">Dies ist eine "vor dem eigentlichen Rendern" übergeben.</span><span class="sxs-lookup"><span data-stu-id="22ae1-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="22ae1-249">Hier erstellen wir einen Puffer verdecken, werden aufgefordert, den Mesh-Renderer zum Rendern von nur Tiefe.</span><span class="sxs-lookup"><span data-stu-id="22ae1-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="22ae1-250">In dieser Konfiguration nicht wir eine renderzielansicht Anfügen und die Mesh-Renderer die Pixel-Shader-Stufe an **"nullptr"** so, dass die GPU gar nicht Pixel gezeichnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="22ae1-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="22ae1-251">Die Geometrie werden gerastert im Tiefenpuffer, und die Grafikpipeline wird es beendet.</span><span class="sxs-lookup"><span data-stu-id="22ae1-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="22ae1-252">Wir können Hologramme zeichnen, mit einer zusätzlichen Tiefentest für Puffer verdecken Oberfläche zuordnen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="22ae1-253">In diesem Codebeispiel Rendern wir Pixel für den Cube eine andere Farbe, wenn sie sich hinter einer Fläche befinden.</span><span class="sxs-lookup"><span data-stu-id="22ae1-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="22ae1-254">Von AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="22ae1-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="22ae1-255">Basierend auf Code SpecialEffectPixelShader.hlsl:</span><span class="sxs-lookup"><span data-stu-id="22ae1-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="22ae1-256">**Hinweis**: Für unsere **GatherDepthLess** -Routine, finden Sie im Codebeispiel Oberfläche zuordnen: SpecialEffectPixelShader.hlsl.</span><span class="sxs-lookup"><span data-stu-id="22ae1-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="22ae1-257">**Rendering-Oberfläche Mesh-Daten auf dem Bildschirm**</span><span class="sxs-lookup"><span data-stu-id="22ae1-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="22ae1-258">Wir können auch einfach nur die Oberfläche Gitter den Puffern Stereo Anzeige zeichnen.</span><span class="sxs-lookup"><span data-stu-id="22ae1-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="22ae1-259">Es wurde entschieden, zeichnen Sie die vollständige Gesichtern mit Beleuchtung, aber Sie können zum Drahtmodell zu zeichnen, verarbeiten Gitter vor dem Rendern, Anwenden einer Texturmaps und so weiter.</span><span class="sxs-lookup"><span data-stu-id="22ae1-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="22ae1-260">Unser Codebeispiel teilt, die Mesh-Renderer zum Zeichnen der Auflistung.</span><span class="sxs-lookup"><span data-stu-id="22ae1-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="22ae1-261">Dieses Mal nicht wir bestanden Tiefe nur angeben, damit einen Pixel-Shader Anfügen und verwenden die Ziele, die wir angegeben, für die aktuelle virtuelle Kamera die Rendering-Pipeline abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="22ae1-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="22ae1-262">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="22ae1-262">See also</span></span>
* [<span data-ttu-id="22ae1-263">Erstellen eines holographic DirectX-Projekts</span><span class="sxs-lookup"><span data-stu-id="22ae1-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="22ae1-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="22ae1-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
