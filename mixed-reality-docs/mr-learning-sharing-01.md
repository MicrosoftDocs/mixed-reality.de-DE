---
title: 'Tutorials zu Mehrbenutzerfunktionen: 1 Einführung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376342"
---
# <a name="1-introduction"></a>1. Einführung

## <a name="overview"></a>Übersicht

Willkommen bei den Tutorials zu Mehrbenutzerfunktionen! In dieser Tutorialreihe erlernen Sie die Grundlagen zum Entwickeln einer Mehrbenutzerumgebung mithilfe von <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen.

Tutorials in dieser Reihe:

* [Einrichten von Photon Unity Networking](mr-learning-sharing-02.md)
* [Verbinden mehrerer Benutzer](mr-learning-sharing-03.md)
* [Freigeben von Objektbewegungen für mehrere Benutzer](mr-learning-sharing-04.md)
* [Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mr-learning-sharing-05.md)

## <a name="objectives"></a>Ziele

* Erfahren, wie PUN-App erstellt und eine Verbindung Ihres Unity-Projekts mit ihr hergestellt wird
* Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung
* Erfahren, wie Objektbewegungen mit anderen Benutzern geteilt werden können
* Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-Computer, auf dem die richtigen [Tools installiert](install-the-tools.md) sind
* Windows 10 SDK (10.0.18362.0 oder höher)
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform
* Durchgearbeiteter Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Durchgearbeitete Tutorialserie [Erste Schritte](mr-learning-base-01.md) oder vorherige grundlegende Erfahrung mit Unity und MRTK
* Durchgearbeitete [Tutorialserie „Azure Spatial Anchors“](mr-learning-asa-01.md) oder vorherige Erfahrung im Erstellen eines Azure Spatial Anchors-Kontos
* Wenn Sie unter Android sowie HoloLens bereitstellen möchten
  * Ein Android-Gerät mit <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">Entwicklerunterstützung</a> und <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore-Unterstützung</a> mit USB-Verbindung zu Ihrem Windows- oder macOS-Computer
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für Android
* Wenn Sie unter iOS sowie HoloLens bereitstellen möchten
  * Ein macOS-Computer mit installierter neuester Version von <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> und <a href="https://cocoapods.org" target="_blank">CocoaPods</a>
  * Ein iOS-Gerät mit <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit-Unterstützung</a> und USB-Verbindung mit Ihrem macOS-Computer
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für iOS

> [!CAUTION]
> Die empfohlene Mixed Reality Toolkit-Version für diese Tutorialreihe ist MRTK 2.4.0.

> [!CAUTION]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.3.15. Diese Informationen besitzen Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

[Nächstes Tutorial: 2. Einrichten von Photon Unity Networking](mr-learning-sharing-02.md)
