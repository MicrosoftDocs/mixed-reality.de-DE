---
title: Spectator View
description: Visualisieren Sie Hologramme von einem externen Gerät als Mittel zur Darstellung eines Mixed Reality-Erlebnisses auf einem externen Display oder zur Aufzeichnung eines Mixed Reality-Erlebnisses.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Kamera, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, Demo, aufzeichnen
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491160"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Spectator View für HoloLens und HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Übersicht

Beim Tragen einer HoloLens vergessen wir oft, dass eine Person, die sie nicht trägt, all die Wunder, die wir erfahren, nicht erleben kann. Mit Spectator View können andere auf einem zweidimensionalen Bildschirm sehen, was HoloLens-Benutzer in ihrer Welt sehen.
Spectator View bietet einen schnellen und bezahlbaren Ansatz zum Aufzeichnen von Hologrammen in HD mit mobilen Geräten. Ferner bietet es die Möglichkeit zur Aufzeichnung von Hologrammen mit Videokameras in professioneller Qualität.

## <a name="key-resources"></a>Wichtige Ressourcen

* [**Spectator View auf GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Spectator View-Dokumentation**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Spectator View-Beispiele**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Anwendungsfälle
* Sie können ein Mixed Reality-Erlebnis mithilfe eines iPhone- oder Android-Geräts aufzeichnen. Zeichnen Sie in Full HD auf, und wenden Sie Antialiasing auf Hologramme und sogar auf Schatten an. Dies ist eine kostengünstige und schnelle Möglichkeit zum Erfassen von Videos von Hologrammen.
* Streamen Sie von Ihrem iPhone oder iPad verzögerungsfrei Mixed Reality-Erlebnisse live auf ein Apple TV!
* Teilen Sie das Erlebnis mit Gästen: Lassen Sie Benutzer ohne HoloLens Hologramme direkt auf Ihren Smartphones oder Tablets erleben.

## <a name="current-features"></a>Aktuelle Features

* Synchronisierung von Hologrammen im Raum, sodass alle die Hologramme an genau der gleichen Stelle sehen.
* Unterstützung für iOS- (ARKit-fähige Geräte) und Android-Geräte (ARCore-fähige Geräte).
Mehrere iOS-Gäste.
Aufzeichnung von Video + Hologrammen + Raumklang + Hologrammklang.
Freigabeblatt, auf dem Sie Videos speichern, sie per E-Mail senden oder sie mit anderen unterstützten Apps teilen können.

![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)

In der folgenden Tabelle sind verschiedene Funktionen von Spectator View aufgeführt. Wählen Sie die Option aus, die Ihren Anforderungen an Videoaufzeichnung am besten entspricht:

|                                      | Mobile                  |                    Videokamera              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD-Qualität                           |         Full HD         |        Filmen in professioneller Qualität (durch die Videokamera bestimmt)      |
| Einfache Kamerabewegung                 |            ✔            |                      ✔                      |
| Third-Person-Ansicht                    |            ✔            |                      ✔                      |
| Kann auf Bildschirme gestreamt werden           |            ✔            |                      ✔                      |
| Tragbar                             |            ✔            |                                             |
| Drahtlos                             |            ✔            |                                             |
| Zusätzlich erforderliche Hardware         |     Android-Smartphone, iPhone    | HoloLens + Rig + Stativ + Videokamera + PC + Unity |
| Hardwareinvestition                  |           Niedrig            |                     Hoch                    |
| Plattformübergreifend                       |           Android, iOS   |                                             |
| Synchronisierte Inhalte                 |            ✔            |                      ✔                      |
| Dauer des Runtime-Setups               |         Instant          |                     Langsam                    |
## <a name="see-also"></a>Weitere Informationen

* [Mixed Reality-Aufnahme](mixed-reality-capture.md) 
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
