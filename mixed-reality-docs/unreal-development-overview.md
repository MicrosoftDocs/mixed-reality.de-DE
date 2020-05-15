---
title: 'Unreal-Entwicklung: Übersicht'
description: Übersicht über die Mixed Reality-Entwicklung mit Unreal Engine 4
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851564"
---
# <a name="unreal-development-overview"></a>Unreal-Entwicklung: Übersicht

Unreal Engine 4 unterstützt nun uneingeschränkt die Entwicklung für Windows Mixed Reality-Geräte (VR) und für HoloLens 2-Geräte (AR). Wenn Sie neu in die Entwicklung mit Unreal einsteigen, ist <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Erste Schritte mit Unreal Engine 4</a> eine hervorragende Seite, die Sie erforschen sollten. Wenn Sie Ressourcen benötigen, finden Sie diese im umfangreich ausgestatteten <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Asset Store</a>. 

Nachdem Sie sich mit den Grundlagen der Unreal-Entwicklung vertraut gemacht haben, können Sie sich das Tutorial im nächsten Abschnitt ansehen, um zu erfahren, wie Sie Ihre Apps für HoloLens erstellen und ausführen. Besuchen Sie unbedingt die <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality-Foren</a>, und interagieren Sie mit der Community, die Mixed Reality-Apps in Unreal entwickelt. So finden Sie häufig Lösungen für Probleme, die Ihnen begegnen.

## <a name="tutorial"></a>Tutorial

In unserem umfassenden HoloLens 2-Tutorial erfahren Sie, wie Sie [eine einfache Schach-App für HoloLens 2 erstellen und bereitstellen](unreal-uxt-ch1.md). In diesem Tutorial wird das UX-Tools-Plug-In verwendet, um die App-Entwicklung mit interaktiven UX-Komponenten wie etwa einer Taste und einem Manipulator zu beschleunigen. Weitere Informationen zum UX-Tools-Plug-In finden Sie im nächsten Abschnitt zum MRTK. 

## <a name="mixed-reality-toolkit-for-unreal"></a>Mixed Reality-Toolkit für Unreal

Das [Mixed Reality-Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) umfasst eine Reihe von Komponenten in Form von Plug-Ins, Beispielen und Dokumentationsmaterial, um die Entwicklung von Mixed Reality-Anwendungen mit Unreal Engine zu beschleunigen. Als erste Komponente dieses Toolkits wurden die [UX-Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) veröffentlicht. Dieses Plug-In kann Ihrem HoloLens 2-Projekt hinzugefügt werden, um UX-Features für HoloLens 2-Anwendungen bereitzustellen. Die Dokumentation für das Mixed Reality-Toolkit und die UX-Tools für Unreal finden Sie in den jeweiligen GitHub-Repositorys. 

## <a name="performance"></a>Leistung

Eine HoloLens 2-App muss mit 60 Frames pro Sekunde ausgeführt werden, um stabile und reaktionsfähige Hologramme zu erhalten. Wir empfehlen daher dringend, unsere [Leistungsempfehlungen für Unreal](performance-recommendations-for-unreal.md) umzusetzen, um dies in Ihrer App zu erreichen. 

## <a name="guides-to-specific-features"></a>Leitfäden für spezifische Features

Informationen zur Verwendung spezifischer Features in Unreal finden Sie in den folgenden Leitfäden: 
* [Handtracking](unreal-hand-tracking.md)
* [Eyetracking – Blickverfolgung](unreal-gaze-input.md)
* [Räumliche Abbildung](unreal-spatial-mapping.md)
* [Raumanker](unreal-spatial-anchors.md)
* [Spracheingabe](unreal-voice-input.md)
* [HoloLens-Kamera](unreal-hololens-camera.md)
* [QR-Codes](unreal-qr-codes.md)

## <a name="supported-features"></a>Unterstützte Features

| HoloLens 2-Feature | Niedrigste unterstützte Unreal Engine-Version |
| ----------- | ----------- |
| ARM64-Unterstützung | 4.23 |
| Streaming von einem PC | 4.23 |
| Räumliche Abbildung | 4.23 |
| Hand- und Gelenktracking | 4.23 |
| Eyetracking – Blickverfolgung | 4.23 |
| Spracheingabe | 4.23 |
| Raumanker | 4.23 |
| Kamerazugriff | 4.23 |
| QR-Codes | 4.23 |
| Räumliche Audiowiedergabe | 4.23 |
| Zuschauerbildschirmunterstützung für Streaming | 4.24 |
| Planar-LSR über Streaming | 4.24 |
| Beispiel-Apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) und [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Mobile Multiansicht: Leistung erreicht 60 FPS | 4.25 |
| Rendering der dritten Kamera | 4.25 |
| Streaming aus einer verpackten Desktop-App | 4.25 |
| Azure Spatial Anchors für HoloLens 2 (Beta) | 4.25 |
| OpenXR-Unterstützung (Beta) | 4.25 |
| Unterstützung von UX-Tools (0.8) | 4.25 |
| Dokumentation und Tutorials für Entwickler | 4.25 |

## <a name="see-also"></a>Siehe auch
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Unreal-Dokumentation für Streaming und Bereitstellung (Emulator und Gerät)</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal-Leistungsrichtlinien für mobile Geräte</a>
