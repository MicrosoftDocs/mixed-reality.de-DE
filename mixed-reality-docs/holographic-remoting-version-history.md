---
title: Holographic Remoting-Versionsverlauf
description: Versionsverlauf für Holographic Remoting auf hololens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 1f4d463ab734cbb627f251486b0058fbf295d2ed
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300521"
---
# <a name="holographic-remoting-version-history"></a>Holographic Remoting-Versionsverlauf

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## <a name="version-222-july-10-2020"></a>Version 2.2.2 (10. Juli 2020)<a name="v2.2.2"></a>
* Es wurde ein Problem mit [holographiccamera. leftviewportparameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_LeftViewportParameters) und [holographiccamera. rightviewportparameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_RightViewportParameters) behoben, bei dem das Streaming von einem Windows Mixed Reality-Headset keine ausgeblendeten Bereiche zurückgegeben hat.
* Ein Absturz, der mit einer schlechten Netzwerkverbindung möglich ist, wurde korrigiert.

## <a name="version-221-july-6-2020"></a>Version 2.2.1 (6. Juli 2020)<a name="v2.2.1"></a>
> [!IMPORTANT]
> Die Validierung des [Zertifizierungs Kits für Windows-apps](https://developer.microsoft.com/windows/downloads/app-certification-kit/) mit Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) schlägt fehl. Wenn Sie die Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) haben und Ihre Anwendung an den Microsoft Store übermitteln möchten, aktualisieren Sie mindestens Version 2.2.1.
* Kompatibilitätsprobleme beim [zertifizierungskit für Windows App](https://developer.microsoft.com/windows/downloads/app-certification-kit/)

## <a name="version-220-july-1-2020"></a>Version 2.2.0 (1. Juli 2020)<a name="v2.2.0"></a>
* Der Holographic Remoting Player kann nun auf PCs installiert werden, auf denen [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)ausgeführt wird, sodass es möglich ist, zu immersiven Headsets zu streamen.
* [Bewegungs Controller](motion-controllers.md) werden nun von Holographic Remoting unterstützt, und Controller spezifische Daten können über " [spatialinteraktionsource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)" abgerufen werden.
* [Spatialstageframeofreferenwird](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) jetzt unterstützt, und die aktuelle Phase kann über [spatialstageframeofreferen. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)abgerufen werden. Außerdem kann eine neue Stufe über [spatialstageframeofreferen. requestnewstageasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)angefordert werden.
* In früheren Versionen wurde die Pose-Vorhersage auf der Player Seite vom Holographic Remoting Player vollständig behandelt. Ab Version 2.2.0 verfügt Holographic Remoting über eine Zeitsynchronisierung, und die Vorhersage wird von der Remote Anwendung vollständig durchgeführt. Benutzer sollten außerdem eine verbesserte hologrammstabilität in schwierigen Netzwerk Situationen erwarten.

## <a name="version-213-may-25-2020"></a>Version 2.1.3 (dem 25. Mai 2020)<a name="v2.1.3"></a>
* Geändertes Verhalten des [holographicspace. cameraadded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) -Ereignisses. In früheren Versionen konnte **nicht** garantiert werden, dass ein hinzugefügter [holographiccamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera?view=winrt-18362) auch über eine gültige [holographiccamerapose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) verfügt, wenn der nächste Frame über [holographicspace. kreatenextframe](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe?view=winrt-18362#Windows_Graphics_Holographic_HolographicSpace_CreateNextFrame)erstellt wird. Ab Version 2.1.3 ist [holographicspace. cameraadded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) mit Daten aus dem Holographic Remoting Player synchronisiert, und Benutzer können davon ausgehen, dass beim Hinzufügen einer Kamera auch eine gültige [holographiccamerapose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) für die Kamera im nächsten Frame verfügbar ist.
* "Depthbufferstreamresolution" wurde **deaktiviert** und kann verwendet werden, um das tiefe Puffer Streaming über RemoteContext.Configuredepthvideostream zu deaktivieren. Beachten Sie, dass bei Verwendung von [holographiccamerarenderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer?view=winrt-18362#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) mit *E_ILLEGAL_METHOD_CALL*fehlschlägt.
* Der Startbildschirm des Holographic Remoting-Players wurde neu entworfen und blockiert nun nicht die Ansicht "Benutzer".
* Verbesserungen der Stabilität und Fehlerbehebungen.

## <a name="version-212-april-5-2020"></a>Version 2.1.2 (5. April 2020)<a name="v2.1.2"></a>
* Es wurde ein Problem mit der audioabwärts Kompatibilität zwischen dem neuesten Holographic Remoting Player und Remote-apps mit einer Version kleiner als 2.1.0 behoben.
* Behobene räumliches Anker Problem, das den Holographic Remoting-Player unerwartet geschlossen hat. Dieses Problem betrifft auch benutzerdefinierte Player.

## <a name="version-211-march-20-2020"></a>Version 2.1.1 (20. März 2020)<a name="v2.1.1"></a>
* Beheben von Video Codierungs Problemen mit Remote-Apps bei Verwendung von AMD-GPUs.
* Leistungsverbesserungen für Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Version 2.1.0 (11. März 2020)<a name="v2.1.0"></a>
* Der Netzwerk Transport wurde zum Verwenden von [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP gewechselt. Sichere Verbindungen verwenden jetzt [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) . Beachten Sie, dass der [Holographic Remoting Player](holographic-remoting-player.md) immer noch mit allen zuvor veröffentlichten Holographic Remoting-Versionen kompatibel ist. Um vom neuen Netzwerk Transport profitieren zu können, müssen der Holographic Remoting Player und die betreffende Remote-app Version 2.1.0 verwenden.
* Unterstützung für [holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)hinzugefügt. 

## <a name="version-2020-february-2-2020"></a>Version 2.0.20 (2. Februar 2020)<a name="v2.0.20"></a>
* Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.

## <a name="version-2018-december-17-2019"></a>Version 2.0.18 (17. Dezember 2019)<a name="v2.0.18"></a>
* Unterstützung für [holographicviewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration) hinzugefügt
* Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.
* Es wurde ein Fehler behoben, bei dem ein holographicspace. cameraadded-Rückruf erforderlich war, damit ein holographiccamera akzeptiert und als hinzugefügte Kamera im holographicframe angezeigt werden konnte.

## <a name="version-2016-november-11-2019"></a>Version 2.0.16 (11. November 2019)<a name="2.0.16"></a>
* Deadlockfehler bei der Überwachung des QR-Codes.
* Eine unhandliche Ausnahme wurde aufgrund einer blockierenden Wartezeit im Haupt Thread korrigiert.

## <a name="version-2014-october-26-2019"></a>Version 2.0.14 (26. Oktober 2019)<a name="v2.0.14"></a>
* Unterstützung für neue "perceptiondevice"-APIs (Windows 10-Update vom November 2019).
* Ein Problem wurde behoben, durch das das Auslösen von halte Gesten Ereignissen durch spatialgesturerecognizer verhindert wird.
* Das Threading Problem wurde behoben, wenn spatialsurfaceobserver. setboundingvolume verwendet wurde.

## <a name="version-2012-october-18-2019"></a>Version 2.0.12 (18. Oktober 2019)<a name="v2.0.12"></a>
* Absturz in spatialgesturerecognizer bei Verwendung von navigationrail (X/Y/Z) korrigiert.

## <a name="version-2010-october-10-2019"></a>Version 2.0.10 (10. Oktober 2019)<a name="v2.0.10"></a>
* Absturz bei Verwendung der Schaltfläche "-Taste" von VR-Controllern Holographic-Remoting unterstützt Controller nicht vollständig, nur die Schaltfläche "Abbrechen" und die Schaltfläche "Windows" funktionieren, wenn Sie mit hololens 2 gekoppelt sind.

## <a name="version-209-september-19-2019"></a>Version 2.0.9 (19. September 2019)<a name="v2.0.9"></a>
* Unterstützung für [spatialanchorexporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt
* Neue Schnittstelle ```IPlayerContext2``` (implementiert von) wurde hinzugefügt, ```PlayerContext``` die die folgenden Member bereitstellt:
  - [Blitremoteframetimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) -Eigenschaft.
* Hinzugefügter ```Failed_RemoteFrameTooOld``` Wert zu```BlitResult```
* Verbesserungen der Stabilität und Zuverlässigkeit

## <a name="version-208-august-20-2019"></a>Version 2.0.8 (20. August 2019)<a name="v2.0.8"></a>

* Absturz beim Aufrufen von [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as-Parameter korrigiert.
* Verbesserungen der Stabilität und Zuverlässigkeit

## <a name="version-207-july-26-2019"></a>Version 2.0.7 (26. Juli 2019)<a name="v2.0.7"></a>

* Erstes öffentliches Release von Holographic Remoting für hololens 2.

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
