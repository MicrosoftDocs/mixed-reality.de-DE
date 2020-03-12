---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Schritte zur Problembehandlung für Holographic Remoting auf hololens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe
ms.openlocfilehash: 79258832d29741c56a1e7e89baeb7d728c806dd1
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092366"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="4e636-104">Problembehandlung bei Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="4e636-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e636-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="4e636-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="4e636-106">Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="4e636-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="4e636-107">Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.</span><span class="sxs-lookup"><span data-stu-id="4e636-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="4e636-108">Wenn Sie einen schwerwiegenden Linker-Fehler erhalten, der besagt, dass "vccorlib. lib" nicht geöffnet werden kann, müssen Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von Spectre abgeminderten Bibliotheken enthält</span><span class="sxs-lookup"><span data-stu-id="4e636-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="4e636-109">Weitere Informationen finden Sie unter https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="4e636-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="4e636-110">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="4e636-110">Limitations</span></span>

<span data-ttu-id="4e636-111">Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird, und es wird ein ```ERROR_NOT_SUPPORTED``` Fehler ausgelöst, sofern nichts anderes angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="4e636-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="4e636-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="4e636-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="4e636-113">Holographiccamera. viewconfiguration</span><span class="sxs-lookup"><span data-stu-id="4e636-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="4e636-114">Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="4e636-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="4e636-115">In früheren Versionen löst immer einen Fehler aus.</span><span class="sxs-lookup"><span data-stu-id="4e636-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="4e636-116">Holographicviewconfiguration. requestrendertargetsize</span><span class="sxs-lookup"><span data-stu-id="4e636-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="4e636-117">Schlägt nicht fehl, aber die Größe des Renderziels wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="4e636-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="4e636-118">Holographiccamerapose. override projectiontransform</span><span class="sxs-lookup"><span data-stu-id="4e636-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="4e636-119">Holographiccamerapose. overrideviewport</span><span class="sxs-lookup"><span data-stu-id="4e636-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="4e636-120">Holographiccamerapose. override viewtransform</span><span class="sxs-lookup"><span data-stu-id="4e636-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="4e636-121">Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="4e636-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="4e636-122">Schlägt nicht fehl, aber der tiefen Puffer wird nicht remotetet.</span><span class="sxs-lookup"><span data-stu-id="4e636-122">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="4e636-123">Unterstützt ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span><span class="sxs-lookup"><span data-stu-id="4e636-123">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="4e636-124">Holographicdisplay. trygetviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="4e636-124">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="4e636-125">Beim Abfragen von holographicviewconfigurationkind. photovideocamera wird immer ein ```nullptr```zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="4e636-125">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="4e636-126">Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="4e636-126">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="4e636-127">In früheren Versionen löst immer einen Fehler aus.</span><span class="sxs-lookup"><span data-stu-id="4e636-127">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="4e636-128">Holographicspace. kreateframepresentationmonitor</span><span class="sxs-lookup"><span data-stu-id="4e636-128">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="4e636-129">Holographicdisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="4e636-129">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="4e636-130">Meldet einen Fehler, wenn aufgerufen wird, bevor eine Verbindung hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="4e636-130">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="4e636-131">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="4e636-131">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="4e636-132">SpatialLocation. absoluteangularacceleration</span><span class="sxs-lookup"><span data-stu-id="4e636-132">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="4e636-133">SpatialLocation. absoluteangularaccelerationaxisangle</span><span class="sxs-lookup"><span data-stu-id="4e636-133">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="4e636-134">SpatialLocation. absoluteangularvelocity</span><span class="sxs-lookup"><span data-stu-id="4e636-134">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="4e636-135">SpatialLocation. absoluteangularvelocityaxisangle</span><span class="sxs-lookup"><span data-stu-id="4e636-135">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="4e636-136">SpatialLocation. absolutelinearacceleration</span><span class="sxs-lookup"><span data-stu-id="4e636-136">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="4e636-137">SpatialLocation. absolutelinearvelocity</span><span class="sxs-lookup"><span data-stu-id="4e636-137">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="4e636-138">Spatialstageframeofreferenzierungs. Current</span><span class="sxs-lookup"><span data-stu-id="4e636-138">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="4e636-139">Gibt immer ```nullptr```zurück.</span><span class="sxs-lookup"><span data-stu-id="4e636-139">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="4e636-140">Spatialstageframeofreferenzierung. requestnewstageasync</span><span class="sxs-lookup"><span data-stu-id="4e636-140">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="4e636-141">Spatialanchor. removedbyuser</span><span class="sxs-lookup"><span data-stu-id="4e636-141">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="4e636-142">Spatialanchorexporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="4e636-142">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="4e636-143">Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="4e636-143">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="4e636-144">In früheren Versionen gibt immer ```nullptr```zurück.</span><span class="sxs-lookup"><span data-stu-id="4e636-144">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="4e636-145">Spatialanchorexporter. requestaccessasync</span><span class="sxs-lookup"><span data-stu-id="4e636-145">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="4e636-146">Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="4e636-146">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="4e636-147">In früheren Versionen wurde der asynchrone Vorgang immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="4e636-147">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="4e636-148">Spatialanchortransfermanager. requestaccessasync</span><span class="sxs-lookup"><span data-stu-id="4e636-148">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="4e636-149">Der Async-Vorgang wird immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="4e636-149">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="4e636-150">Spatialanchortransfermanager. tryexportanchorsasync</span><span class="sxs-lookup"><span data-stu-id="4e636-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="4e636-151">Der Async-Vorgang wird immer mit ```false```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="4e636-151">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="4e636-152">Spatialanchortransfermanager. tryimportanchorsasync</span><span class="sxs-lookup"><span data-stu-id="4e636-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="4e636-153">Der Async-Vorgang wird immer mit ```nullptr```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="4e636-153">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="4e636-154">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="4e636-154">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="4e636-155">Spatialinteraktionsource. trykreatehandmeshobserver</span><span class="sxs-lookup"><span data-stu-id="4e636-155">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="4e636-156">Spatialinteraktionsource. trykreatehandmeshobserverasync</span><span class="sxs-lookup"><span data-stu-id="4e636-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="4e636-157">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="4e636-157">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="4e636-158">Spatialgraphinteroppreview. kreatelocatorfornode</span><span class="sxs-lookup"><span data-stu-id="4e636-158">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="4e636-159">Spatialgraphinteroppreview. trykreateframeofreferenzierung</span><span class="sxs-lookup"><span data-stu-id="4e636-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="4e636-160">Spatialinteraktionsource. Controller</span><span class="sxs-lookup"><span data-stu-id="4e636-160">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="4e636-161">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4e636-161">See Also</span></span>
* [<span data-ttu-id="4e636-162">Holographic Remoting-Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="4e636-162">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="4e636-163">Schreiben einer Holographic Remoting-Remote-app</span><span class="sxs-lookup"><span data-stu-id="4e636-163">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="4e636-164">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="4e636-164">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="4e636-165">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="4e636-165">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="4e636-166">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="4e636-166">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
