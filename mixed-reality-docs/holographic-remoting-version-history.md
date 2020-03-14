---
title: Holographic Remoting-Versionsverlauf
description: Versionsverlauf für Holographic Remoting auf hololens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 62f54dbcf5327cdd5f13622704684a2cb0606d7d
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375657"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="7178a-104">Holographic Remoting-Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="7178a-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7178a-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="7178a-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="7178a-106">Version 2.1.0 (11. März 2020)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="7178a-107">Der Netzwerk Transport wurde zum Verwenden von [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP gewechselt.</span><span class="sxs-lookup"><span data-stu-id="7178a-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="7178a-108">Sichere Verbindungen verwenden jetzt [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) .</span><span class="sxs-lookup"><span data-stu-id="7178a-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="7178a-109">Beachten Sie, dass der [Holographic Remoting Player](holographic-remoting-player.md) immer noch mit allen zuvor veröffentlichten Holographic Remoting-Versionen kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="7178a-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="7178a-110">Um vom neuen Netzwerk Transport profitieren zu können, müssen der Holographic Remoting Player und die betreffende Remote-app Version 2.1.0 verwenden.</span><span class="sxs-lookup"><span data-stu-id="7178a-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="7178a-111">Unterstützung für [holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7178a-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <span data-ttu-id="7178a-112">Version 2.0.20 (2. Februar 2020)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="7178a-113">Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.</span><span class="sxs-lookup"><span data-stu-id="7178a-113">Fixed various bugs that lead to crashes.</span></span>

## <span data-ttu-id="7178a-114">Version 2.0.18 (17. Dezember 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="7178a-115">Unterstützung für [holographicviewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration) hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7178a-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="7178a-116">Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.</span><span class="sxs-lookup"><span data-stu-id="7178a-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="7178a-117">Es wurde ein Fehler behoben, bei dem ein holographicspace. cameraadded-Rückruf erforderlich war, damit ein holographiccamera akzeptiert und als hinzugefügte Kamera im holoraphicframe angezeigt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="7178a-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="7178a-118">Version 2.0.16 (11. November 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="7178a-119">Deadlockfehler bei der Überwachung des QR-Codes.</span><span class="sxs-lookup"><span data-stu-id="7178a-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="7178a-120">Eine unhandliche Ausnahme wurde aufgrund einer blockierenden Wartezeit im Haupt Thread korrigiert.</span><span class="sxs-lookup"><span data-stu-id="7178a-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="7178a-121">Version 2.0.14 (26. Oktober 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="7178a-122">Unterstützung für neue "perceptiondevice"-APIs (Windows 10-Update vom November 2019).</span><span class="sxs-lookup"><span data-stu-id="7178a-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="7178a-123">Ein Problem wurde behoben, durch das das Auslösen von halte Gesten Ereignissen durch spatialgesturerecognizer verhindert wird.</span><span class="sxs-lookup"><span data-stu-id="7178a-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="7178a-124">Das Threading Problem wurde behoben, wenn spatialsurfaceobserver. setboundingvolume verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="7178a-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="7178a-125">Version 2.0.12 (18. Oktober 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="7178a-126">Absturz in spatialgesturerecognizer bei Verwendung von navigationrail (X/Y/Z) korrigiert.</span><span class="sxs-lookup"><span data-stu-id="7178a-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="7178a-127">Version 2.0.10 (10. Oktober 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="7178a-128">Absturz bei Verwendung der Schaltfläche "-Taste" von VR-Controllern</span><span class="sxs-lookup"><span data-stu-id="7178a-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="7178a-129">Holographic-Remoting unterstützt Controller nicht vollständig, nur die Schaltfläche "Abbrechen" und die Schaltfläche "Windows" funktionieren, wenn Sie mit hololens 2 gekoppelt sind.</span><span class="sxs-lookup"><span data-stu-id="7178a-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="7178a-130">Version 2.0.9 (19. September 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="7178a-131">Unterstützung für [spatialanchorexporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7178a-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="7178a-132">Neue Schnittstellen ```IPlayerContext2``` (implementiert durch ```PlayerContext```) hinzugefügt, die die folgenden Mitglieder bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="7178a-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="7178a-133">[Blitremoteframetimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="7178a-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="7178a-134">Hinzugefügter ```Failed_RemoteFrameTooOld``` Wert ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="7178a-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="7178a-135">Verbesserungen der Stabilität und Zuverlässigkeit</span><span class="sxs-lookup"><span data-stu-id="7178a-135">Stability and reliability improvements</span></span>

## <span data-ttu-id="7178a-136">Version 2.0.8 (20. August 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="7178a-137">Absturz beim Aufrufen von [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as-Parameter korrigiert.</span><span class="sxs-lookup"><span data-stu-id="7178a-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="7178a-138">Verbesserungen der Stabilität und Zuverlässigkeit</span><span class="sxs-lookup"><span data-stu-id="7178a-138">Stability and reliability improvements</span></span>

## <span data-ttu-id="7178a-139">Version 2.0.7 (26. Juli 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="7178a-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="7178a-140">Erstes öffentliches Release von Holographic Remoting für hololens 2.</span><span class="sxs-lookup"><span data-stu-id="7178a-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="7178a-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7178a-141">See Also</span></span>
* [<span data-ttu-id="7178a-142">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="7178a-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="7178a-143">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="7178a-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="7178a-144">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="7178a-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="7178a-145">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="7178a-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="7178a-146">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="7178a-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
