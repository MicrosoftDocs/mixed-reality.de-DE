---
title: Unreal-Entwicklung – Übersicht
description: Übersicht über die Mixed Reality-Entwicklung mit der Unreal Engine 4
author: hferrone
ms.author: v-haferr
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: ecf982eb5d8128734c862bac2d8be29c1554edfe
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303621"
---
# <a name="unreal-development-overview"></a>Unreal-Entwicklung – Übersicht

Die ersten Schritte mit <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Mixed Reality-Dokumentation"> Mixed Reality-Anwendungen</a> sind eine Herausforderung. Neue Konzepte, Plattformen und neuartige Hardware können sich als Hürden erweisen. Wenn Sie jedoch Unreal-Entwickler sind, haben Sie Glück. Unterstützung für <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality-Dokumentation">Windows Mixed Reality</a> (VR) und <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2-Dokumentation">HoloLens 2</a> (AR) ist jetzt in der aktuellen <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Versionshinweisen zu Unreal Engine 4.25">Release</a> von Unreal Engine enthalten. Das Update enthält:
* Unterstützung für das Mixed Reality UX-Plug-In
* OpenXR-Unterstützung
* App-Remoting über eine Desktop-App
* Bessere Leistung
* Mixed-Reality-Aufnahme
* Anfängliche Unterstützung für Azure Spatial Anchors

Wenn Sie noch nicht mit der Unreal-Entwicklung vertraut sind, sollten Sie sich zunächst etwas einarbeiten. Sehen Sie sich die <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">Tutorialreihe</a> zu Unreal an, um einen Einstieg zu finden, und nutzen Sie Ressourcen und Support im Unreal-<a href="https://www.unrealengine.com/marketplace/store" target="_blank">Marketplace</a> und den Mixed Reality-<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Foren</a>. Dabei handelt es sich um Links zur Community von Entwicklern und Problemlösern auf dem Gebiet der Mixed Reality.

## <a name="mixed-reality-toolkit-for-unreal"></a>Mixed Reality-Toolkit für Unreal

Das [Mixed Reality Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) bietet eine Reihe von Komponenten, die entwickelt wurden, um Ihre Entwicklung für Unreal zu beschleunigen. Jede Komponente enthält Plug-Ins, Beispiele und Dokumentation zum Einrichten von immersiven Erlebnissen. 

[UX Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) ist die erste Komponente, die veröffentlicht wird. Derzeit wird sie nur auf HoloLens 2 unterstützt. Das Komponenten-Plug-In enthält Code, Blaupausen und Beispielressourcen für gängige UX-Features, einschließlich:
* Eingabesimulation
* Handinteraktionsakteur
* Drückbare Schaltflächenkomponente
* Manipulatorkomponente
* Folgeverhaltenskomponente

Ausführliche Informationen zu Funktionen und zum Einrichten Ihres Projekts finden Sie im GitHub-Repository [UX Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal).

## <a name="hololens-2-platform-support"></a>HoloLens 2-Plattformunterstützung
Wenn Sie zum ersten Mal eine Unreal-App für HoloLens erstellen oder bereitstellen, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien zur Plattformunterstützung herunterladen](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="tutorial"></a>Tutorial

Neue Fertigkeiten eignen Sie sich am besten an, indem Sie ein Projekt selbst erstellen. Eine gute Gelegenheit für den Einstieg ist das [Erstellen und Bereitstellen einer einfachen Schach-App](unreal-uxt-ch1.md) für HoloLens 2 mit dem UX Tools-Plug-In. 

Diese umfassende Tutorialreihe vermittelt Ihnen praktische Erfahrungen mit allgemeinen interaktiven UX-Komponenten und -Szenarien. Sie absolvieren die Projekteinrichtung, das Hinzufügen von Interaktionen zur Szene und das Bereitstellen auf einem Gerät oder in einem Emulator. Sie benötigen lediglich Windows 10, einen Emulator und Visual Studio 2019.

## <a name="debugging"></a>Debuggen

Befolgen Sie zum Debuggen einer App mit Visual Studio, die auf HoloLens 2 ausgeführt wird, die Anweisungen hier zum [Debuggen einer installierten UWP-App auf einem Remotegerät](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package?view=vs-2019#remote).

## <a name="performance"></a>Leistung

Die Entwicklung für Mixed Reality ist mit Leistungsprüfpunkten verbunden, die von der Plattform abhängen. Eine HoloLens 2-App muss mit 60 Frames pro Sekunde ausgeführt werden, um stabile und reaktionsfähige Hologramme zu erhalten. Glücklicherweise stehen [Leistungsempfehlungen](performance-recommendations-for-unreal.md) zur Verfügung, damit Sie das Ziel mit Ihren Unreal-Anwendungen erfolgreich erreichen.

## <a name="guides-to-specific-features"></a>Leitfäden für spezifische Features

Es gibt mehrere wichtige Features der Mixed Reality-Entwicklung, die in unserer Tutorialreihe nicht behandelt werden. Weitere Informationen und praktische Anwendungsfälle finden Sie in den folgenden Handbüchern: 
* [Eyetracking – Blickverfolgung](unreal-gaze-input.md)
* [Handtracking](unreal-hand-tracking.md)
* [HoloLens-Kamera](unreal-hololens-camera.md)
* [Raumanker](unreal-spatial-anchors.md)
* [Räumliche Abbildung](unreal-spatial-mapping.md)
* [Räumliche Audiowiedergabe](unreal-spatial-audio.md)
* [Streaming](unreal-streaming.md)
* [Spracheingabe](unreal-voice-input.md)
* [QR-Codes](unreal-qr-codes.md)
* [Leistungsempfehlungen](performance-recommendations-for-unreal.md)

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
| Beispiel-Apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) und [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Mobile Multiansicht: Leistung erreicht 60 FPS | 4.25 |
| Rendering der dritten Kamera | 4.25 |
| Streaming aus einer verpackten Desktop-App | 4.25.1 |
| Azure Spatial Anchors für HoloLens 2 (Beta) | 4.25 |
| OpenXR-Unterstützung (Beta) | 4.25 |
| Unterstützung von UX-Tools (0.8) | 4.25 |
| Dokumentation und Tutorials für Entwickler | 4.25 |

## <a name="see-also"></a>Siehe auch
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Unreal-Dokumentation für Streaming und Bereitstellung (Emulator und Gerät)</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Unreal-Leistungsrichtlinien für mobile Geräte</a>
