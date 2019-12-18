---
title: Holographic Remoting-Versionsverlauf
description: Versionsverlauf für Holographic Remoting auf hololens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181960"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="09be5-104">Holographic Remoting-Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="09be5-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09be5-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="09be5-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="09be5-106">Version 2.0.18.0 (17. Dezember 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="09be5-107">Hinzugefügte Unterstützung für holographicviewconfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="09be5-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="09be5-108">Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.</span><span class="sxs-lookup"><span data-stu-id="09be5-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="09be5-109">Es wurde ein Fehler behoben, bei dem ein holographicspace. cameraadded-Rückruf erforderlich war, damit ein holographiccamera akzeptiert und als hinzugefügte Kamera im holoraphicframe angezeigt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="09be5-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="09be5-110">Version 2.0.16 (11. November 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="09be5-111">Deadlockfehler bei der Überwachung des QR-Codes.</span><span class="sxs-lookup"><span data-stu-id="09be5-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="09be5-112">Eine unhandliche Ausnahme wurde aufgrund einer blockierenden Wartezeit im Haupt Thread korrigiert.</span><span class="sxs-lookup"><span data-stu-id="09be5-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="09be5-113">Version 2.0.14 (26. Oktober 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="09be5-114">Unterstützung für neue "perceptiondevice"-APIs (Windows 10-Update vom November 2019).</span><span class="sxs-lookup"><span data-stu-id="09be5-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="09be5-115">Ein Problem wurde behoben, durch das das Auslösen von halte Gesten Ereignissen durch spatialgesturerecognizer verhindert wird.</span><span class="sxs-lookup"><span data-stu-id="09be5-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="09be5-116">Das Threading Problem wurde behoben, wenn spatialsurfaceobserver. setboundingvolume verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="09be5-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="09be5-117">Version 2.0.12 (18. Oktober 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="09be5-118">Absturz in spatialgesturerecognizer bei Verwendung von navigationrail (X/Y/Z) korrigiert.</span><span class="sxs-lookup"><span data-stu-id="09be5-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="09be5-119">Version 2.0.10 (10. Oktober 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="09be5-120">Absturz bei Verwendung der Schaltfläche "-Taste" von VR-Controllern</span><span class="sxs-lookup"><span data-stu-id="09be5-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="09be5-121">Holographic-Remoting unterstützt Controller nicht vollständig, nur die Schaltfläche "Abbrechen" und die Schaltfläche "Windows" funktionieren, wenn Sie mit hololens 2 gekoppelt sind.</span><span class="sxs-lookup"><span data-stu-id="09be5-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="09be5-122">Version 2.0.9 (19. September 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="09be5-123">Unterstützung für [spatialanchorexporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="09be5-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="09be5-124">Neue Schnittstellen ```IPlayerContext2``` (implementiert durch ```PlayerContext```) hinzugefügt, die die folgenden Mitglieder bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="09be5-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="09be5-125">[Blitremoteframetimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="09be5-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="09be5-126">Hinzugefügter ```Failed_RemoteFrameTooOld``` Wert ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="09be5-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="09be5-127">Verbesserungen der Stabilität und Zuverlässigkeit</span><span class="sxs-lookup"><span data-stu-id="09be5-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="09be5-128">Version 2.0.8 (20. August 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="09be5-129">Absturz beim Aufrufen von [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as-Parameter korrigiert.</span><span class="sxs-lookup"><span data-stu-id="09be5-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="09be5-130">Verbesserungen der Stabilität und Zuverlässigkeit</span><span class="sxs-lookup"><span data-stu-id="09be5-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="09be5-131">Version 2.0.7 (26. Juli 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="09be5-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="09be5-132">Erstes öffentliches Release von Holographic Remoting für hololens 2.</span><span class="sxs-lookup"><span data-stu-id="09be5-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="09be5-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="09be5-133">See Also</span></span>
* [<span data-ttu-id="09be5-134">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="09be5-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="09be5-135">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="09be5-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="09be5-136">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="09be5-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="09be5-137">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="09be5-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="09be5-138">Datenschutzerklärung von Microsoft</span><span class="sxs-lookup"><span data-stu-id="09be5-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
