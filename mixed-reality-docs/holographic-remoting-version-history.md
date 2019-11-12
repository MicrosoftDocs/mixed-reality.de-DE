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
# <a name="holographic-remoting-version-history"></a>Holographic Remoting-Versionsverlauf

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## Version 2.0.14 (26. Oktober 2019)<a name="v2.0.14"></a>
* Unterstützung für neue "perceptiondevice"-APIs (Windows 10-Update vom November 2019).
* Ein Problem wurde behoben, durch das das Auslösen von halte Gesten Ereignissen durch spatialgesturerecognizer verhindert wird.
* Das Threading Problem wurde behoben, wenn spatialsurfaceobserver. setboundingvolume verwendet wurde.

## Version 2.0.12 (18. Oktober 2019)<a name="v2.0.12"></a>
* Absturz in spatialgesturerecognizer bei Verwendung von navigationrail (X/Y/Z) korrigiert.

## Version 2.0.10 (10. Oktober 2019)<a name="v2.0.10"></a>
* Absturz bei Verwendung der Schaltfläche "-Taste" von VR-Controllern Holographic-Remoting unterstützt Controller nicht vollständig, nur die Schaltfläche "Abbrechen" und die Schaltfläche "Windows" funktionieren, wenn Sie mit hololens 2 gekoppelt sind.

## Version 2.0.9 (19. September 2019)<a name="v2.0.9"></a>
* Unterstützung für [spatialanchorexporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt
* Neue Schnittstellen ```IPlayerContext2``` (implementiert durch ```PlayerContext```) hinzugefügt, die die folgenden Mitglieder bereitstellen:
  - [Blitremoteframetimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) -Eigenschaft.
* Hinzugefügter ```Failed_RemoteFrameTooOld``` Wert ```BlitResult```
* Verbesserungen der Stabilität und Zuverlässigkeit

## Version 2.0.8 (20. August 2019)<a name="v2.0.8"></a>

* Absturz beim Aufrufen von [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as-Parameter korrigiert.
* Verbesserungen der Stabilität und Zuverlässigkeit

## Version 2.0.7 (26. Juli 2019)<a name="v2.0.7"></a>

* Erstes öffentliches Release von Holographic Remoting für hololens 2.

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
