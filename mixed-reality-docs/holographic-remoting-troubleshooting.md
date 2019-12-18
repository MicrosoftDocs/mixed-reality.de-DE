---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Schritte zur Problembehandlung für Holographic Remoting auf hololens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181970"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="11c72-104">Problembehandlung bei Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="11c72-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11c72-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="11c72-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="11c72-106">Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="11c72-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="11c72-107">Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.</span><span class="sxs-lookup"><span data-stu-id="11c72-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="11c72-108">Wenn Sie einen schwerwiegenden Linker-Fehler erhalten, der besagt, dass "vccorlib. lib" nicht geöffnet werden kann, müssen Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von Spectre abgeminderten Bibliotheken enthält</span><span class="sxs-lookup"><span data-stu-id="11c72-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="11c72-109">Weitere Informationen finden Sie unter https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="11c72-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="11c72-110">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="11c72-110">Limitations</span></span>

<span data-ttu-id="11c72-111">Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird, und es wird ein ```ERROR_NOT_SUPPORTED``` Fehler ausgelöst, sofern nichts anderes angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="11c72-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="11c72-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="11c72-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="11c72-113">Holographiccamera. viewconfiguration</span><span class="sxs-lookup"><span data-stu-id="11c72-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="11c72-114">Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="11c72-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="11c72-115">In früheren Versionen löst immer einen Fehler aus.</span><span class="sxs-lookup"><span data-stu-id="11c72-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="11c72-116">Holographicviewconfiguration. requestrendertargetsize</span><span class="sxs-lookup"><span data-stu-id="11c72-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="11c72-117">Schlägt nicht fehl, aber die Größe des Renderziels wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="11c72-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="11c72-118">Holographiccamerapose. override projectiontransform</span><span class="sxs-lookup"><span data-stu-id="11c72-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="11c72-119">Holographiccamerapose. overrideviewport</span><span class="sxs-lookup"><span data-stu-id="11c72-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="11c72-120">Holographiccamerapose. override viewtransform</span><span class="sxs-lookup"><span data-stu-id="11c72-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="11c72-121">Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="11c72-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="11c72-122">Schlägt nicht fehl, aber der tiefen Puffer wird nicht remotetet.</span><span class="sxs-lookup"><span data-stu-id="11c72-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="11c72-123">Holographicdisplay. trygetviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="11c72-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="11c72-124">Beim Abfragen von holographicviewconfigurationkind. photovideocamera wird immer ein ```nullptr```zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="11c72-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="11c72-125">Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="11c72-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="11c72-126">In früheren Versionen löst immer einen Fehler aus.</span><span class="sxs-lookup"><span data-stu-id="11c72-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="11c72-127">Holographicspace. kreateframepresentationmonitor</span><span class="sxs-lookup"><span data-stu-id="11c72-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="11c72-128">Holographicdisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="11c72-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="11c72-129">Meldet einen Fehler, wenn aufgerufen wird, bevor eine Verbindung hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="11c72-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="11c72-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="11c72-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="11c72-131">SpatialLocation. absoluteangularacceleration</span><span class="sxs-lookup"><span data-stu-id="11c72-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="11c72-132">SpatialLocation. absoluteangularaccelerationaxisangle</span><span class="sxs-lookup"><span data-stu-id="11c72-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="11c72-133">SpatialLocation. absoluteangularvelocity</span><span class="sxs-lookup"><span data-stu-id="11c72-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="11c72-134">SpatialLocation. absoluteangularvelocityaxisangle</span><span class="sxs-lookup"><span data-stu-id="11c72-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="11c72-135">SpatialLocation. absolutelinearacceleration</span><span class="sxs-lookup"><span data-stu-id="11c72-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="11c72-136">SpatialLocation. absolutelinearvelocity</span><span class="sxs-lookup"><span data-stu-id="11c72-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="11c72-137">Spatialstageframeofreferenzierungs. Current</span><span class="sxs-lookup"><span data-stu-id="11c72-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="11c72-138">Gibt immer ```nullptr``` zurück.</span><span class="sxs-lookup"><span data-stu-id="11c72-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="11c72-139">Spatialstageframeofreferenzierung. requestnewstageasync</span><span class="sxs-lookup"><span data-stu-id="11c72-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="11c72-140">Spatialanchor. removedbyuser</span><span class="sxs-lookup"><span data-stu-id="11c72-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="11c72-141">Spatialanchorexporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="11c72-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="11c72-142">Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="11c72-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="11c72-143">In früheren Versionen gibt immer ```nullptr```zurück.</span><span class="sxs-lookup"><span data-stu-id="11c72-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="11c72-144">Spatialanchorexporter. requestaccessasync</span><span class="sxs-lookup"><span data-stu-id="11c72-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="11c72-145">Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="11c72-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="11c72-146">In früheren Versionen wurde der asynchrone Vorgang immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="11c72-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="11c72-147">Spatialanchortransfermanager. requestaccessasync</span><span class="sxs-lookup"><span data-stu-id="11c72-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="11c72-148">Der Async-Vorgang wird immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="11c72-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="11c72-149">Spatialanchortransfermanager. tryexportanchorsasync</span><span class="sxs-lookup"><span data-stu-id="11c72-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="11c72-150">Der Async-Vorgang wird immer mit ```false```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="11c72-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="11c72-151">Spatialanchortransfermanager. tryimportanchorsasync</span><span class="sxs-lookup"><span data-stu-id="11c72-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="11c72-152">Der Async-Vorgang wird immer mit ```nullptr```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="11c72-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="11c72-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="11c72-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="11c72-154">Spatialinteraktionsource. trykreatehandmeshobserver</span><span class="sxs-lookup"><span data-stu-id="11c72-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="11c72-155">Spatialinteraktionsource. trykreatehandmeshobserverasync</span><span class="sxs-lookup"><span data-stu-id="11c72-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="11c72-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="11c72-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="11c72-157">Spatialgraphinteroppreview. kreatelocatorfornode</span><span class="sxs-lookup"><span data-stu-id="11c72-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="11c72-158">Spatialgraphinteroppreview. trykreateframeofreferenzierung</span><span class="sxs-lookup"><span data-stu-id="11c72-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="11c72-159">Spatialinteraktionsource. Controller</span><span class="sxs-lookup"><span data-stu-id="11c72-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="11c72-160">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="11c72-160">See Also</span></span>
* [<span data-ttu-id="11c72-161">Holographic Remoting-Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="11c72-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="11c72-162">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="11c72-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="11c72-163">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="11c72-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="11c72-164">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="11c72-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="11c72-165">Datenschutzerklärung von Microsoft</span><span class="sxs-lookup"><span data-stu-id="11c72-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
