---
title: 'Tutorials zu Azure Spatial Anchors: 1 Einführung'
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f273c573d40b1e65e325bd31b5dd9e14c1ee66ec
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376552"
---
# <a name="1-introduction"></a>1. Einführung

## <a name="overview"></a>Übersicht

Willkommen bei den Tutorials zu Azure Spatial Anchors! Durch diese Tutorialreihe lernen Sie die Grundlagen von <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) kennen und erfahren, wie Sie eine vollständige Mixed Reality-Erfahrung in der realen Welt verankern. Außerdem erfahren Sie, wie Sie Ihr Projekt für Android und iOS bereitstellen.

Tutorials in dieser Reihe:

1. [Einführung](mr-learning-asa-01.md)
2. [Erste Schritte mit Azure Spatial Anchors](mr-learning-asa-02.md)
3. [Speichern, Abrufen und Freigeben von Azure Spatial Anchors](mr-learning-asa-03.md)
4. [Anzeigen von Azure Spatial Anchors-Feedback](mr-learning-asa-04.md)
5. [Azure Spatial Anchors für Android und iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Ziele

* Erfahren, wie Raumanker erstellt und aus Azure abgerufen werden
* Erfahren, wie die räumliche Ausrichtung über mehrere App-Sitzungen erreicht wird
* Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann
* Erfahren, wie Ihr Projekt für Android und iOS vorbereitet, erstellt und bereitgestellt wird

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-Computer, auf dem die richtigen [Tools installiert](install-the-tools.md) sind
* Windows 10 SDK (Version 10.0.18362.0 oder höher)
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform
* Durchgearbeiteter Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* Durchgearbeitete Tutorialreihe [Erste Schritte](mr-learning-base-01.md) oder vorherige grundlegende Erfahrung mit Unity und MRTK
* Durchgearbeitete Tutorialreihe [Azure Spatial Anchors](mr-learning-asa-01.md) oder vorherige Erfahrung im Erstellen eines Azure Spatial Anchors-Kontos
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

[Nächstes Tutorial: 2. Erste Schritte mit Azure Spatial Anchors](mr-learning-asa-02.md)
