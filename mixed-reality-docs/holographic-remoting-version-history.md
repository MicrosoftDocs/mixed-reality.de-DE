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
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092305"
---
# <a name="holographic-remoting-version-history"></a>Holographic Remoting-Versionsverlauf

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## Version 2.1.0 (11. März 2020)<a name="v2.1.0"></a>
* Der Netzwerk Transport wurde zum Verwenden von [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP gewechselt. Sichere Verbindungen verwenden jetzt [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) . Beachten Sie, dass der [Holographic Remoting Player](holographic-remoting-player.md) immer noch mit allen zuvor veröffentlichten Holographic Remoting-Versionen kompatibel ist. Um vom neuen Netzwerk Transport profitieren zu können, müssen der Holographic Remoting Player und die betreffende Remote-app Version 2.1.0 verwenden.
* Unterstützung für [holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)hinzugefügt. 

## Version 2.0.20 (2. Februar 2020)<a name="v2.0.20"></a>
* Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.

## Version 2.0.18 (17. Dezember 2019)<a name="v2.0.18"></a>
* Unterstützung für [holographicviewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration) hinzugefügt
* Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.
* Es wurde ein Fehler behoben, bei dem ein holographicspace. cameraadded-Rückruf erforderlich war, damit ein holographiccamera akzeptiert und als hinzugefügte Kamera im holoraphicframe angezeigt werden konnte.

## Version 2.0.16 (11. November 2019)<a name="2.0.16"></a>
* Deadlockfehler bei der Überwachung des QR-Codes.
* Eine unhandliche Ausnahme wurde aufgrund einer blockierenden Wartezeit im Haupt Thread korrigiert.

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
