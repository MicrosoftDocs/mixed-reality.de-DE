---
title: Ansicht "Betrachter"
description: Visualisieren Sie holograms von einem externen Gerät, um eine gemischte Realität auf einem externen Bildschirm zu demonstrieren oder ein Video mit gemischter Realität zu erfassen.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Zuschauer Ansicht, iPhone, Ios, iPad, opencv, Kamera, Arkit, hololens, Mixed Reality, mixedrealitytoolkit, Demo, Datensatz
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387666"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Ansicht "Betrachter" für hololens und hololens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Übersicht

Beim Durcharbeiten von hololens vergessen wir oft nicht, dass eine Person, die nicht über diese verfügt, nicht die Wunder, die wir haben, nicht erleben kann. Mit der Ansicht "Betrachter" können andere Benutzer auf einem 2D-Bildschirm sehen, was ein hololens-Benutzer in der Welt sieht.
Die Zuschauer Ansicht bietet einen schnellen und kostengünstigen Ansatz zum Aufzeichnen von holograms in HD mit mobilen Geräten. Außerdem bietet es eine qualitativ hochwertige Aufzeichnung von holograms mit Videokameras.

## <a name="key-resources"></a>Wichtige Ressourcen

* [**Ansicht "Betrachter" auf GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Architektur**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**Stich**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**Anweisungen für die Mobile Installation**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**Anweisungen zur Installation von Video Kameras**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a>Anwendungsfälle
* Sie können eine gemischte Realität mit einem iPhone oder Android-Gerät aufzeichnen. Notieren Sie sich die vollständige Festplatte, und wenden Sie Antialiasing auf holograms und sogar Schatten an. Es ist eine kostengünstige und schnelle Möglichkeit, Videos von holograms zu erfassen.
* Streamen Sie das Live Mixed Reality-Erlebnis direkt von Ihrem iPhone oder iPad auf eine Apple TV-Umgebung.
* Teilen Sie die Arbeit mit Gästen: Gestatten Sie Benutzern, die nicht hololens sind, direkt von Ihrem Smartphone oder Tablet aus.

## <a name="current-features"></a>Aktuelle Features

* Räumliche Synchronisierung von holograms, sodass alle Hologramme an der gleichen Stelle sehen.
* IOS-Unterstützung (Arkit-fähige Geräte) und Android-Unterstützung (Arcore-fähige Geräte).
Mehrere IOS-Gäste.
Aufzeichnung von Video + holograms + Ambient Sound + – Hologramm Sound.
Freigabe Blatt, damit Sie Videos speichern, per e-Mail senden oder mit anderen unterstützenden apps freigeben können.

![](images/SpecViewPhoneDemo.jpg)
 ![Markermarkermarker](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

In der folgenden Tabelle werden die verschiedenen Funktionen der Zuschauer Ansicht und ihre Funktionen gezeigt. Wählen Sie die Option aus, die Ihren Video Aufzeichnungs Anforderungen am besten entspricht:

|                                      | Mobil                  |                    Video Kamera              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD-Qualität                           |         Vollständige HD         |        Qualität der professionellen Qualität (wie von der Videokamera festgelegt)      |
| Einfache Kamerabewegung                 |            ✔            |                      ✔                      |
| Ansicht für dritte Person                    |            ✔            |                      ✔                      |
| Kann auf Bildschirme gestreamt werden           |            ✔            |                      ✔                      |
| Tabel                             |            ✔            |                                             |
| Drahtlos                             |            ✔            |                                             |
| Zusätzliche erforderliche Hardware         |     Android Phone, iPhone    | Hololens + Rig + Stativ + Video Kamera + PC + Unity |
| Hardware Investition                  |           Niedrig            |                     Hoch                    |
| Plattformübergreifend                       |           Android, ios   |                                             |
| Synchronisierter Inhalt                 |            ✔            |                      ✔                      |
| Laufzeit-Setup Dauer               |         Blick          |                     Verzögerte Anzeige                    |
## <a name="see-also"></a>Siehe auch

* [Mixed Reality-Aufnahme](mixed-reality-capture.md) 
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
