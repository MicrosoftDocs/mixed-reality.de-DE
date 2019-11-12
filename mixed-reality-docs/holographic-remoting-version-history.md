---
title: Holographic Remoting-Versionsverlauf
description: Versionsverlauf für Holographic Remoting auf hololens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 9ff6a5f7594eb67dd4c1c8690812ab724cac9012
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926651"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="d286f-104">Holographic Remoting-Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="d286f-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d286f-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="d286f-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="d286f-106">Version 2.0.14 (26. Oktober 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="d286f-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="d286f-107">Unterstützung für neue "perceptiondevice"-APIs (Windows 10-Update vom November 2019).</span><span class="sxs-lookup"><span data-stu-id="d286f-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="d286f-108">Ein Problem wurde behoben, durch das das Auslösen von halte Gesten Ereignissen durch spatialgesturerecognizer verhindert wird.</span><span class="sxs-lookup"><span data-stu-id="d286f-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="d286f-109">Das Threading Problem wurde behoben, wenn spatialsurfaceobserver. setboundingvolume verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d286f-109">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="d286f-110">Version 2.0.12 (18. Oktober 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="d286f-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="d286f-111">Absturz in spatialgesturerecognizer bei Verwendung von navigationrail (X/Y/Z) korrigiert.</span><span class="sxs-lookup"><span data-stu-id="d286f-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="d286f-112">Version 2.0.10 (10. Oktober 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="d286f-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="d286f-113">Absturz bei Verwendung der Schaltfläche "-Taste" von VR-Controllern</span><span class="sxs-lookup"><span data-stu-id="d286f-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="d286f-114">Holographic-Remoting unterstützt Controller nicht vollständig, nur die Schaltfläche "Abbrechen" und die Schaltfläche "Windows" funktionieren, wenn Sie mit hololens 2 gekoppelt sind.</span><span class="sxs-lookup"><span data-stu-id="d286f-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="d286f-115">Version 2.0.9 (19. September 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="d286f-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="d286f-116">Unterstützung für [spatialanchorexporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="d286f-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="d286f-117">Neue Schnittstellen ```IPlayerContext2``` (implementiert durch ```PlayerContext```) hinzugefügt, die die folgenden Mitglieder bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="d286f-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="d286f-118">[Blitremoteframetimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d286f-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="d286f-119">Hinzugefügter ```Failed_RemoteFrameTooOld``` Wert ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="d286f-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="d286f-120">Verbesserungen der Stabilität und Zuverlässigkeit</span><span class="sxs-lookup"><span data-stu-id="d286f-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="d286f-121">Version 2.0.8 (20. August 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="d286f-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="d286f-122">Absturz beim Aufrufen von [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as-Parameter korrigiert.</span><span class="sxs-lookup"><span data-stu-id="d286f-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="d286f-123">Verbesserungen der Stabilität und Zuverlässigkeit</span><span class="sxs-lookup"><span data-stu-id="d286f-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="d286f-124">Version 2.0.7 (26. Juli 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="d286f-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="d286f-125">Erstes öffentliches Release von Holographic Remoting für hololens 2.</span><span class="sxs-lookup"><span data-stu-id="d286f-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="d286f-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d286f-126">See Also</span></span>
* [<span data-ttu-id="d286f-127">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="d286f-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="d286f-128">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="d286f-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="d286f-129">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d286f-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="d286f-130">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="d286f-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="d286f-131">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="d286f-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
