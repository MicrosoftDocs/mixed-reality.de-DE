---
title: Übersicht über die Entwicklung
description: Dieser Artikel beschreibt die grundlegenden Bausteine der Entwicklung einer Windows Mixed Reality-app.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Erste Schritte, Grundlagen HoloLens, HoloLens-2, immersive Kopfhörer, Unity und visual Studio
ms.openlocfilehash: 1d23e458477cc23252ccd4c44f67c400aa356965
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605114"
---
# <a name="development-overview"></a>Übersicht über die Entwicklung

Mixed Reality-apps können mithilfe einer Vielzahl von entwicklertechnologien entwickelt werden.  HoloLens ausgeführt wird, apps, die mit basieren die [universelle Windows-Plattform](https://dev.windows.com/getstarted).  Führen Sie immersive Headsets apps der universellen Windows-Plattform als auch für Win32-Anwendungen.
Durch die damit vertraut machen, Middleware-Tools wie Unity, können Sie beginnen, Erstellen von mixed Reality heute auftritt.  Nutzen Sie die open Source [Mixed Reality-Toolkit](install-the-tools.md) einen schnellen Einstieg.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed Reality-Services</a>, z. B. <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, haben Sie die SDKs, die in verschiedenen plattformübergreifenden entwicklertechnologien auch integrieren können.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Grundlagen der Entwicklung von mixed reality

[Mixed Reality](mixed-reality.md) Funktionen werden durch neue Windows-Features für das Verständnis der Umgebung aktiviert. Diese ermöglichen Entwicklern das Platzieren einer [– Hologramm](hologram.md) in der realen Welt Benutzern ermöglicht, die digitale Welt buchstäblich Schritt für Schritt zu durchlaufen. 

Dies sind die wichtigsten Bausteine für die Entwicklung von mixed Reality:

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> <a href="gaze.md">Head Blicke</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Eye Blicke</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Praktische / <a href="gestures.md">Gesten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voice</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Motion-Controller</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Vorstellung und räumliche Funktionen</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Globale Koordinaten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Räumliche sound</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Räumliche Zuordnung</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



Das grundlegende Interaktionsmodell für [HoloLens](hololens-hardware-details.md) ist [bestaunen](gaze.md), [Geste](gestures.md), und [Voice](voice-input.md), auch als bezeichnet *GGV* . [Windows Mixed Reality immersive Headsets](immersive-headset-hardware-details.md) auch verwenden Blicke "und" Stimme, aber "Swap [motion Controller](motion-controllers.md) für Gesten.


Alle Windows-basierten mixed Reality-Geräte gibt das Eingabe-Ökosystem zur Verfügung, Windows, einschließlich Maus, Tastatur, Gamepads und mehr profitieren. Mit HoloLens [Hardwarezubehör](hardware-accessories.md) über Bluetooth verbunden sind. Verbinden mit immersive Headsets Zubehör zum Host-PC über Bluetooth, USB und anderen unterstützten Protokolle.

Die Umwelt Grundlegendes zu Funktionen wie [Koordinaten](coordinate-systems.md), [räumliche Sound](spatial-sound.md), und [räumliche Zuordnung](spatial-mapping.md) bieten die notwendigen Funktionen für das Kombinieren von Realität. Räumliche Zuordnung gilt nur für HoloLens und ermöglicht Hologramme sowohl für den Benutzer als auch für die physische Welt zu interagieren. Koordinatensysteme ermöglichen der Bewegung der Benutzer Verschieben von Daten in die digitale Welt zu beeinflussen.

[Hologramme](hologram.md) erfolgen von Licht und Sound, die von abhängig sind [holographic Rendering](rendering.md). Die Erfahrung der Platzierung und Persistenz zu verstehen, wie in der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (der "Shell" bezeichnet) ist eine gute Möglichkeit erden Sie sich auf der Benutzeroberfläche.

## <a name="tools-for-developing-for-mixed-reality"></a>Tools für die Entwicklung für mixed reality

Die Tools, die Sie verwenden, hängt von der [Art von app](app-views.md) erstellt werden soll.
* [Apps mit einer 2D-Ansicht](building-2d-apps.md) nutzen Sie Tools für universelle Windows-Plattform-apps erstellen, die für die Umgebungen wie Windows Phone, PCs und Tablets geeignet. Diese apps als 2D Projektionen, die in die Windows Mixed Reality home platziert vertraut sind, und können über mehrere Gerätetypen (einschließlich Telefon und PC) arbeiten.
* Immersive und holographic apps benötigen Tools, die Vorteile der Windows Mixed Reality-APIs nutzen. Wir [wird empfohlen, mithilfe von Unity](unity-development-overview.md) , mixed Reality-apps zu erstellen. Entwickler, die bei der Erstellung ihres eigenen Moduls können [DirectX und anderen Windows-APIs verwenden](directx-development-overview.md).

Unabhängig von der Art der app, die Sie erstellen, werden diese Tools app-Entwicklungsprozess vereinfachen:
* [Visual Studio und das Windows SDK](using-visual-studio.md)
* [Windows-Geräteportal](using-the-windows-device-portal.md)
* [Emulator für HoloLens](using-the-hololens-emulator.md) (HoloLens-2-Emulator in Kürze verfügbar)
* [Windows Mixed Reality-simulator](using-the-windows-mixed-reality-simulator.md)
* [Qualitätskriterien für die App](app-quality-criteria.md)

## <a name="see-also"></a>Siehe auch
* [Installieren der tools](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed Reality-Dienste</a>
* [Mixed Reality-Lernprogramme](academy.md)
* [Open Source-Projekte](open-source-projects.md)
* [MR Basics 100: Erste Schritte mit Unity](holograms-100.md)
* [Windows Mixed Reality minimale PC Kompatibilität an die hardwareempfehlungen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Übermitteln einer app an den Windows Store](submitting-an-app-to-the-microsoft-store.md)
