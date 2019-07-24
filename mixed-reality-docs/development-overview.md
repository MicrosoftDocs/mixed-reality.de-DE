---
title: Entwicklungs Übersicht
description: Dieser Artikel beschreibt die grundlegenden Bausteine der Entwicklung einer Windows Mixed Reality-app.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Getting Started, Basics, hololens, hololens 2, immersives Headset, Unity, Visual Studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873971"
---
# <a name="development-overview"></a>Entwicklungs Übersicht

Mixed Reality-Apps können mithilfe verschiedener Entwickler Technologien entwickelt werden.  Hololens führt Apps aus, die mit dem [universelle Windows-Plattform](https://dev.windows.com/getstarted)erstellt wurden.  Immersive Headsets werden universelle Windows-Plattform apps und Win32-Anwendungen ausgeführt.
Wenn Sie sich mit Middleware-Tools wie Unity vertraut machen, können Sie heute mit dem entwickeln gemischter Realität beginnen.  Nutzen Sie das Open Source [Mixed Reality Toolkit](install-the-tools.md) , um schnell loslegen zu können.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Gemischte Reality-Dienste</a>, wie z. b. <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumliche Azure-Anker</a>, haben sdgs, die auch in verschiedene plattformübergreifende Entwickler Technologien integriert werden können.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Grundlagen der Mixed Reality-Entwicklung

[Mixed Reality](mixed-reality.md)-Umgebungen werden durch neue Windows-Features zur Umgebungserkennung ermöglicht. Diese ermöglichen es Entwicklern, ein [Hologramm](hologram.md) in der realen Welt zu platzieren, und ermöglichen es zudem den Benutzern, sich durch digitale Welten zu bewegen, indem sie buchstäblich herumlaufen. 

Dies sind die zentralen Bausteine für die Mixed Reality-Entwicklung:

<table>
<tr>
<th>Eingabe</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> <a href="gaze.md">Anvisieren mit dem Kopf</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Anvisieren mit den Augen</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Hände/ <a href="gestures.md">Gesten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Sprache</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Motion-Controller</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Wahrnehmung und Raummerkmale</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Weltkoordinaten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Raumklang</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Räumliche Abbildung</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



Das grundlegende Interaktionsmodell für [HoloLens](hololens-hardware-details.md) ist [Anvisieren](gaze.md) (Gaze), [Gesten](gestures.md) (Gesture) und [Sprache](voice-input.md) (Voice), manchmal auch als *GGV* bezeichnet. [Windows Mixed Reality – Immersive Headsets](immersive-headset-hardware-details.md) verwenden ebenfalls Anvisieren und Sprache, aber [Motion-Controller](motion-controllers.md) anstelle der Gesten.


Alle Windows-basierten Mixed Reality-Geräte profitieren von dem Eingabe Ökosystem, das für Windows verfügbar ist, einschließlich Maus, Tastatur, Gamepads und mehr. Bei HoloLens wird [Hardwarezubehör](hardware-accessories.md) über Bluetooth verbunden. Bei immersiven Headsets wird das Zubehör über Bluetooth, USB und andere unterstützte Protokolle mit dem Host-PC verbunden.

Die umgebungsbezogenen Erkennungsmerkmale wie [Koordinaten](coordinate-systems.md), [Raumklang](spatial-sound.md) und [räumliche Abbildung](spatial-mapping.md) bieten die notwendigen Fähigkeiten für Mixed Reality. Die räumliche Abbildung ist einzigartig für HoloLens und ermöglicht es Hologrammen, sowohl mit dem Benutzer als auch mit der physischen Umgebung um sie herum zu interagieren. Koordinatensysteme ermöglichen es, dass die Bewegung des Benutzers die Bewegung in der digitalen Welt beeinflusst.

[Holograms](hologram.md) bestehen aus Licht und Sound, die auf [Holographic Rendering](rendering.md)basieren. Wenn Sie das Konzept von Platzierung und Persistenz verstehen, wie es auf der [Windows Mixed Reality-Startseite](navigating-the-windows-mixed-reality-home.md) (manchmal als „Shell“ bezeichnet) veranschaulicht wird, ist dies eine gute Möglichkeit, sich in der Benutzerumgebung zu etablieren.

## <a name="tools-for-developing-for-mixed-reality"></a>Tools zur Entwicklung für Mixed Reality

Die von Ihnen verwendeten Tools hängen von der [Art der App](app-views.md) ab, die Sie erstellen möchten.
* [Apps mit einer 2D-Ansicht](building-2d-apps.md) nutzen Tools zum Erstellen von Apps der universellen Windows-Plattform, die für Umgebungen wie Windows Phone, PC und Tablets geeignet sind. Diese Apps werden als 2D-Projektionen auf der Startseite von Windows Mixed Reality erlebt und können auf mehreren Gerätetypen (einschließlich Mobiltelefon und PC) eingesetzt werden.
* Immersive und holografische Apps benötigen Tools, die die Vorteile der Windows Mixed Reality-APIs nutzen. Wir [empfehlen Unity](unity-development-overview.md) für die Erstellung von Mixed Reality-Apps. Entwickler, die daran interessiert sind, eine eigene Engine zu entwickeln, können [ DirectX und andere Windows-APIs](directx-development-overview.md) verwenden.

Unabhängig davon, welche Art von App Sie erstellen, werden diese Tools Ihnen die Entwicklung von Apps erleichtern:
* [Visual Studio und das Windows SDK](using-visual-studio.md)
* [Windows-Geräteportal](using-the-windows-device-portal.md)
* [Hololens-Emulator](using-the-hololens-emulator.md) (Hololens 2-Emulator in Kürze verfügbar)
* [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md)
* [Kriterien für die App-Qualität](app-quality-criteria.md)

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed Reality-Dienste</a>
* [Lernprogramme für gemischte Realität](tutorials.md)
* [Open-Source-Projekte](open-source-projects.md)
* [MR-Grundlagen 100: Erste Schritte mit Unity](holograms-100.md)
* [Windows Mixed Reality-Mindestanforderungen für die PC-Hardware Kompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Übermitteln einer APP an den Windows Store](submitting-an-app-to-the-microsoft-store.md)
