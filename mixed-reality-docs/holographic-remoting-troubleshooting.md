---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Schritte zur Problembehandlung für Holographic Remoting auf hololens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434232"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="9e67e-104">Problembehandlung bei Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="9e67e-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e67e-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="9e67e-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="9e67e-106">Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="9e67e-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="9e67e-107">Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.</span><span class="sxs-lookup"><span data-stu-id="9e67e-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="9e67e-108">Wenn Sie einen schwerwiegenden Linker-Fehler erhalten, der besagt, dass "vccorlib. lib" nicht geöffnet werden kann, müssen Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von Spectre abgeminderten Bibliotheken enthält</span><span class="sxs-lookup"><span data-stu-id="9e67e-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="9e67e-109">Weitere Informationen finden Sie unter https://aka.ms/Ofhn4c.</span><span class="sxs-lookup"><span data-stu-id="9e67e-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="9e67e-110">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="9e67e-110">Limitations</span></span>

<span data-ttu-id="9e67e-111">Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird, und es wird ein ```ERROR_NOT_SUPPORTED``` Fehler ausgelöst, sofern nichts anderes angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="9e67e-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="9e67e-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="9e67e-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="9e67e-113">Holographiccamera. viewconfiguration</span><span class="sxs-lookup"><span data-stu-id="9e67e-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="9e67e-114">Holographiccamerapose. override projectiontransform</span><span class="sxs-lookup"><span data-stu-id="9e67e-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="9e67e-115">Holographiccamerapose. overrideviewport</span><span class="sxs-lookup"><span data-stu-id="9e67e-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="9e67e-116">Holographiccamerapose. override viewtransform</span><span class="sxs-lookup"><span data-stu-id="9e67e-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="9e67e-117">Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="9e67e-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="9e67e-118">Schlägt nicht fehl, aber der tiefen Puffer wird nicht remotetet.</span><span class="sxs-lookup"><span data-stu-id="9e67e-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="9e67e-119">Holographicdisplay. trygetviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="9e67e-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="9e67e-120">Holographicspace. kreateframepresentationmonitor</span><span class="sxs-lookup"><span data-stu-id="9e67e-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="9e67e-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="9e67e-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="9e67e-122">SpatialLocation. absoluteangularacceleration</span><span class="sxs-lookup"><span data-stu-id="9e67e-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="9e67e-123">SpatialLocation. absoluteangularaccelerationaxisangle</span><span class="sxs-lookup"><span data-stu-id="9e67e-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="9e67e-124">SpatialLocation. absoluteangularvelocity</span><span class="sxs-lookup"><span data-stu-id="9e67e-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="9e67e-125">SpatialLocation. absoluteangularvelocityaxisangle</span><span class="sxs-lookup"><span data-stu-id="9e67e-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="9e67e-126">SpatialLocation. absolutelinearacceleration</span><span class="sxs-lookup"><span data-stu-id="9e67e-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="9e67e-127">SpatialLocation. absolutelinearvelocity</span><span class="sxs-lookup"><span data-stu-id="9e67e-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="9e67e-128">Spatialstageframeofreferenzierungs. Current</span><span class="sxs-lookup"><span data-stu-id="9e67e-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="9e67e-129">Gibt immer ```nullptr```zurück.</span><span class="sxs-lookup"><span data-stu-id="9e67e-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="9e67e-130">Spatialstageframeofreferenzierung. requestnewstageasync</span><span class="sxs-lookup"><span data-stu-id="9e67e-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="9e67e-131">Spatialanchor. removedbyuser</span><span class="sxs-lookup"><span data-stu-id="9e67e-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="9e67e-132">Spatialanchorexporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="9e67e-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="9e67e-133">Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="9e67e-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="9e67e-134">In früheren Versionen gibt immer ```nullptr```zurück.</span><span class="sxs-lookup"><span data-stu-id="9e67e-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="9e67e-135">Spatialanchorexporter. requestaccessasync</span><span class="sxs-lookup"><span data-stu-id="9e67e-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="9e67e-136">Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="9e67e-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="9e67e-137">In früheren Versionen wurde der asynchrone Vorgang immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="9e67e-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="9e67e-138">Spatialanchortransfermanager. requestaccessasync</span><span class="sxs-lookup"><span data-stu-id="9e67e-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="9e67e-139">Der Async-Vorgang wird immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="9e67e-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="9e67e-140">Spatialanchortransfermanager. tryexportanchorsasync</span><span class="sxs-lookup"><span data-stu-id="9e67e-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="9e67e-141">Der Async-Vorgang wird immer mit ```false```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="9e67e-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="9e67e-142">Spatialanchortransfermanager. tryimportanchorsasync</span><span class="sxs-lookup"><span data-stu-id="9e67e-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="9e67e-143">Der Async-Vorgang wird immer mit ```nullptr```abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="9e67e-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="9e67e-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="9e67e-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="9e67e-145">Spatialinteraktionsource. trykreatehandmeshobserver</span><span class="sxs-lookup"><span data-stu-id="9e67e-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="9e67e-146">Spatialinteraktionsource. trykreatehandmeshobserverasync</span><span class="sxs-lookup"><span data-stu-id="9e67e-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="9e67e-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="9e67e-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="9e67e-148">Spatialgraphinteroppreview. kreatelocatorfornode</span><span class="sxs-lookup"><span data-stu-id="9e67e-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="9e67e-149">Spatialgraphinteroppreview. trykreateframeofreferenzierung</span><span class="sxs-lookup"><span data-stu-id="9e67e-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="9e67e-150">Spatialinteraktionsource. Controller</span><span class="sxs-lookup"><span data-stu-id="9e67e-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="9e67e-151">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9e67e-151">See Also</span></span>
* [<span data-ttu-id="9e67e-152">Holographic Remoting-Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="9e67e-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="9e67e-153">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="9e67e-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="9e67e-154">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="9e67e-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="9e67e-155">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="9e67e-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="9e67e-156">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="9e67e-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
