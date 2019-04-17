---
title: MRTK Pakete
description: Dieser Artikel beschreibt die Pakete, die die Microsoft Mixed Reality Toollkit umfassen.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, Komponente, Paket
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604644"
---
# <a name="mrtk-packages"></a>MRTK Pakete

Mixed Reality-Toolkit (MRTK) ist eine Auflistung von Paketen, die Entwicklung von plattformübergreifenden Mixed Reality-Anwendungen zu ermöglichen, durch die Unterstützung für Mixed Reality-Hardware und Plattformen Weise eine in Komponenten gegliederten.

Es gibt drei Kategorien von MRTK Pakete: 

* [Foundation](#foundation-packages)
* [Erweiterung](#extension-packages)
* [Experimentelle](#experimental-packages)

## <a name="foundation-packages"></a>Foundation-Pakete

Mixed Reality Toolkit Grundlage ist die Reihe von Paketen, mit die Ihre Anwendung für die allgemeine Funktionalität für Mixed Reality-Plattformen nutzen zu können. Diese Pakete veröffentlicht werden, und aus dem Quellcode in von Microsoft unterstützt die [Mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) Branch auf GitHub.

![MRTK Foundation Pakete](images/mrtk-foundation.jpg)

*Mixed Reality-Toolkit-Foundation-Pakete*

Die Grundlage MRTK besteht aus:

* [Core-Paket](#core-package)
* [Plattformanbietern](#platform-providers)
* [Systemdienste](#system-services)
* [Feature-Ressourcen](#feature-assets)

Die folgenden Abschnitte beschreiben die Typen von Paketen in jeder Kategorie.

### <a name="core-package"></a>Core-Paket

Das Core-Paket ist eine _erforderlichen_ Komponente und wird als eine Abhängigkeit von allen MRTK Foundation-Paketen.

Das Paket MRTK Core enthält:

* [Allgemeine Schnittstellen, Klassen und -Datentypen](#common-interfaces-clases-and-data-types)
* [MixedRealityToolkit Szene-Komponente](#mixedrealitytoolkit-scene-component)
* [MRTK Standard-Shader](#mrtk-standard-shader)
* [Unity-Eingabeprovider](#unity-input-provider)
* [Paketverwaltung](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>Allgemeine Schnittstellen, Klassen und -Datentypen

Das Mixed Reality-Toolkit-Core-Paket enthält die Definitionen aller die gemeinsamen Schnittstellen, Klassen und Datentypen, die von allen anderen Komponenten verwendet werden. Es wird dringend empfohlen, dass Anwendungen MRTK Komponenten ausschließlich über die definierten Schnittstellen, damit die höchste Ebene der Kompatibilität auf Plattformen zugreifen.

#### <a name="mixedrealitytoolkit-scene-component"></a>MixedRealityToolkit Szene-Komponente

Die MixedRealityToolkit-Szene-Komponente ist der einzelnen, zentralisierten Manager für das Mixed Reality-Toolkit. Diese Komponente lädt und verwaltet die Lebensdauer der Plattform- und Module und bietet Ressourcen für die Systeme auf ihre Konfigurationseinstellungen zugreifen. 

#### <a name="mrtk-standard-shader"></a>MRTK Standard-Shader

Der Standard-Shader von MRTK bildet die Grundlage für praktisch alle der Materialien, die von der MRTK bereitgestellt. Dieser Shader ist äußerst flexibel und optimiert für die Vielzahl von Plattformen, die auf denen MRTK unterstützt wird. Es ist _hoch_ empfohlen, dass es sich bei Ihrer Anwendung Materialien zu den standardmäßigen MRTK-Shader für eine optimale Leistung verwenden.

#### <a name="unity-input-provider"></a>Unity-Eingabeprovider

Der Unity-Eingabe-Anbieter ermöglicht den Zugriff auf allgemeine Eingabegeräte wie z. B. Gamecontroller, Touchscreens und 3D räumliche Maus.

#### <a name="package-management"></a>Paketverwaltung

_In Kürze verfügbar_

Das Mixed Reality-Toolkit-Core-Paket bietet Unterstützung für das Erkennen und verwalten die optionale Foundation, Erweiterung und experimentelle MRTK Pakete.

### <a name="platform-providers"></a>Plattformanbietern

Der Anbieter MRTK-Pakete sind die Komponenten, mit denen die Mixed Reality-Toolkit für Ziel Mixed Reality-Hardware und Plattformfunktionen zur Verfügung.

Den unterstützten Plattformen gehören:

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Windows Voice](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Das Paket Windows Mixed Reality bietet Unterstützung für Microsoft HoloLens und Windows Mixed Reality Immersive-Geräte. Das Paket enthält die vollständige plattformunterstützung, einschließlich:

* Blicke für
* Gesten
* Windows Mixed Reality-Motion-Controller
* Räumliche Zuordnung

#### <a name="openvr"></a>OpenVR

Das Paket OpenVR bietet Hardware- und Plattforminformationen für Geräte, die mithilfe der OpenVR-Plattform.

#### <a name="windows-voice"></a>Windows Voice

Das Windows-Voice-Paket bietet Unterstützung für Schlüsselwort Erkennung und Diktat-Funktionalität auf Microsoft Windows 10-Geräten.

### <a name="system-services"></a>Systemdienste

Core Platform-Dienste werden in System Service-Paketen bereitgestellt. Diese Pakete enthalten das Mixed Reality-Toolkit-standardimplementierungen der System-Dienstschnittstellen, definiert der [Core](#core-package) Paket.

Die Grundlage MRTK umfasst die folgenden Dienste:

* [Grenze-System](#boundary-system)
* [Diagnosesystem](#diagnostic-system)
* [Eingabesystem](#input-system)
* [Räumliche Awareness-System](#spatial-awareness-system)
* [Teleport System](#teleport-system)

#### <a name="boundary-system"></a>Grenze-System

Das MRTK Grenze System liefern Daten über die auf virtuelle Realität Playspace. Auf Systemen, die für die der Benutzer die Grenze konfiguriert hat, kann das System eine Ebene Floor, rechteckigen Playspace, überwachte Bereich und mehr bereitstellen.

#### <a name="diagnostic-system"></a>Diagnosesystem

Das Diagnosesystem MRTK bietet Echtzeit-Leistungsdaten in Ihrer anwendungsumgebung. Auf einer Reihe werden Sie Framerate, Prozessorzeit und andere wichtige Leistungsmetriken anzeigen, wie Sie Ihre Anwendung verwenden können.

#### <a name="input-system"></a>Eingabesystem

MRTK Eingabesysteme ermöglicht die Eingabe in einer plattformübergreifenden Weise den Zugriff auf die durch Benutzeraktionen angeben, und weisen diese Aktionen zu den am besten geeigneten Schaltflächen und die Achsen für Ziel-Controller.

#### <a name="spatial-awareness-system"></a>Räumliche Awareness-System

Das räumliche MRTK-Awareness-System ermöglicht Zugriff auf realen Umgebungsdaten, von Geräten, z. B. die Microsoft HoloLens.

#### <a name="teleport-system"></a>Teleport System

Das MRTK Teleport System unterstützt virtuelle Realität Locomotion.

### <a name="feature-assets"></a>Feature-Ressourcen

Feature-Ressourcen handelt es sich um Sammlungen von verwandte Funktionen, die als Unity-Objekte und Skripts bereitgestellt. Zu diesen Features zählen:

* Steuerelemente der Benutzeroberfläche
* Standard-Ressourcen
* more

## <a name="extension-packages"></a>Erweiterungspakete

Erweiterungspakete MRTK sind eine Auflistung von Paketen, die von Microsoft und der Community geschrieben, die erweitert und verbessert die Funktionalität des Mixed Reality-Toolkits. Erweiterungsautoren Status alle erforderlichen Abhängigkeiten, markiert das Paket als kompatibel mit dem Mixed Reality-Toolkit und geben Sie die Lizenzierung und Unterstützung.

Erweiterungspakete werden möglicherweise neue Features und neue plattformunterstützung bieten. Im Laufe der Zeit können Extensions mit der Unterstützung und die Genehmigung der Autoren, in der Foundation MRTK migriert werden zu diesem, die Zeitpunkt sie freigegeben und von Microsoft unterstützt wird.

![Erweiterungspaket MRTK](images/mrtk-extensions.jpg)

*Mixed Reality-Toolkit-Erweiterung Pakete*

## <a name="experimental-packages"></a>Experimentelle Pakete

Experimentelle Pakete bieten die Möglichkeit, Prototypfunktionen ein Flug, Vorabversionen und aufregende neue Ideen. Das Ziel der meisten experimentelle Pakete ist etwas Neues aus, und Kunden zu messen. Viele, aber nicht alle experimentellen werden Pakete neu veröffentlicht als Erweiterungen nach Abschluss der Erstellung von Prototypen und Testphase.

![Experimentelle MRTK-Pakete](images/mrtk-experimental.jpg)

*Mixed Reality-Toolkit experimentelle Pakete*

## <a name="conclusion"></a>Schlussbemerkung

Die Mixed Reality-Toolkit-Paket und das paketverwaltungssystem dienen zum Aktivieren einer klaren und einfachen Methode für lichtdurchlässigen Funktionen in Ihre Lösungen zu erstellen, ohne dass nicht benötigte Komponenten, die in das Projekt eingeschlossen werden.

Im Laufe der Zeit wird Support für Paket hinzugefügt und im Mixed Reality-Toolkit erweitert werden. Wenn Sie Feedback oder beteiligten abrufen möchten, besuchen Sie bitte die [Mixed Reality-Toolkit-Project](https://github.com/Microsoft/MixedRealityToolkit-Unity) auf GitHub. 

## <a name="see-also"></a>Siehe auch

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

