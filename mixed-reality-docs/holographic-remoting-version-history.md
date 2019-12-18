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
# <a name="holographic-remoting-version-history"></a>Holographic Remoting-Versionsverlauf

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## Version 2.0.18.0 (17. Dezember 2019)<a name="v2.0.18"></a>
* Hinzugefügte Unterstützung für holographicviewconfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration
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
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
