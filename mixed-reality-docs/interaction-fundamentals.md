---
title: Grundlagen der Interaktion
description: Wie wir Umgebungen für HoloLens erstellt haben (der 1. Generation), HoloLens 2 und immersive Headsets, haben wir begonnen, Schreiben Sie einige Dinge freigeben nützlich herausgestellt.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität Interaktion, Entwerfen
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593245"
---
# <a name="interaction-fundamentals"></a>Grundlagen der Interaktion

Wie wir Umgebungen für HoloLens und immersive Headsets erstellt haben, haben wir begonnen, Schreiben Sie einige Dinge, die es nützlich, um die Freigabe gefunden. Stellen Sie sich diese als die grundlegenden Bausteine für den Entwurf für die Interaktion von mixed Reality.

## <a name="device-support"></a>Unterstützung von Geräten

Hier ist eine Gliederung verfügbaren Interaktion Entwurf Artikeln und der Typ des Geräts oder Typen zu gelten.
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>Eingabe</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">Umrissene Händen</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">Auge als Ziel</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">Blicke für</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">Gesten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">Voice-Entwurf</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> Gamepad</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">Motion-Controller</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>Vorstellung und räumliche Funktionen</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">Räumliche Entwurf</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">Räumliche Zuordnung entwerfen</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">Holograms</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>Der Benutzer ist der Kamera

![Benutzer wird die Kamera](images/useriscamera-640px.jpg)

Denken Sie immer zum Entwurf für die Sicht des Benutzers, wie sie über die reellen und virtuelle Welten verschieben.

**Einige Fragen**
* Wird der Benutzer befindet, reclining, ständigen oder Schritt für Schritt bei der Verwendung von Ihren Erfahrungen?
* Wie anpassen Ihre Inhalte an andere Positionen?
* Kann der Benutzer es werden angepasst?
* Wird der Benutzer Ihre app mit der Anwendung vertraut sein?

**Empfohlene Methoden**
* Der Benutzer die Kamera und steuern sie die Bewegung. Sie steuern können.
* Wenn Sie praktisch den Benutzer übertragen müssen, werden Sie Probleme vestibular angefasst.
* Verwenden Sie kürzere Animationen
* Animieren von nach unten/links/rechts, oder blenden Sie im, anstelle von Z
* Verlangsamen der zeitlichen Steuerung
* Zulassen, dass Benutzer die Welt im Hintergrund finden Sie unter

**Was Sie vermeiden sollten**
* Bewegen die Kamera oder Sperren Sie es absichtlich 3DOF nicht (nur Ausrichtung, keine Übersetzung), unbequem können Benutzer vorzunehmen.
* Keine abrupte Verschiebung. Wenn Sie Inhalte zum oder vom Benutzer bringen möchten, verschieben Sie sie langsam und reibungslos in diese Richtung für optimalen Komfort. Benutzer werden auf großen Menüs, die Ihnen bald zu reagieren.
* Nicht beschleunigen oder des Benutzers Kamera zu aktivieren. Benutzer sind anfällig für Beschleunigung (angular und translatorische).

## <a name="leverage-the-users-perspective"></a>Nutzen Sie die Sicht des Benutzers

Benutzer sehen die Welt von mixed Reality über zeigt auf immersive und holographic-Geräten. Klicken Sie auf die HoloLens, diese Anzeige heißt die [holographic Frame](holographic-frame.md).

Entwicklung von 2D können häufig verwendete Inhalte und Einstellungen in den Ecken des Bildschirms, um sie leicht zugänglich zu machen platziert werden. In holographic apps kann Inhalt in die Ecken aus Sicht der Benutzer jedoch unbequem für den Zugriff auf sein. In diesem Fall ist die Mitte des Frames, holographic die wichtigste Quelle für Inhalte.

Der Benutzer müssen möglicherweise geführt werden, um das Auffinden von wichtigen Ereignissen oder Objekte außerhalb ihrer unmittelbaren anzeigen. Sie können die Pfeile, light-Trails, Zeichen Bewegungen, Sprechblasen, Zeiger, räumliche Sound und Sprachansagen um zu unterstützen, den Benutzer auf wichtige Inhalte in Ihrer app verwenden.

Es wird keine Sperre Inhalt auf dem Bildschirm des Benutzers aus Annehmlichkeitsgründen empfohlen. Wenn Sie in einer Ansicht Inhalt beibehalten möchten, fügen Sie ihn in der ganzen Welt, und machen Sie den Inhalt "Tag-along", z. B. das Startmenü. Inhalte, die zusammen mit der Sicht des Benutzers basisteilkonfiguration werden in der Umgebung natürlichere fühlen.

![Die Ansicht des Benutzers im Startmenü befolgt werden, wenn der Rand des Frames erreicht](images/tagalong-1000px.jpg)<br>
*Die Ansicht des Benutzers im Startmenü befolgt werden, wenn der Rand des Frames erreicht*

Für HoloLens können Hologramme real, wenn sie innerhalb des Rahmens holographic passen, da sie abgeschnitten abrufen nicht. Benutzer werden verschoben, um zu sehen, das die Begrenzungen des ggf. ein Hologramm innerhalb des Rahmens. Für HoloLens ist es wichtig, die Benutzeroberfläche in die Ansicht des Benutzers passen, und behalten Sie den Fokus auf die Hauptaktion vereinfachen. Für immersive Headsets ist es wichtig, den Eindruck einer persistenten virtuellen Welt innerhalb des Geräts Sichtfeld zu verwalten.

## <a name="user-comfort"></a>Benutzerkomfort

Um sicherzustellen, dass maximal [bequem](comfort.md) auf Head-eingebunden angezeigt, und es ist wichtig für Designer und Entwickler zum Erstellen und zeigen den Inhalt in einer Weise, die imitiert, wie Menschen 3D-Formen und die relative Position von Objekten in der natürlichen interpretieren World. Hinsichtlich der physischen ist es auch wichtig, Inhalte zu entwickeln, die keine fatiguing Bewegungen des trichterhalses oder Arms erforderlich ist.

Ob für HoloLens oder immersive Headsets entwickeln zu können, ist es wichtig, um Darstellung für beide Augen zu rendern. Ein Heads-Up-Display in ein Auge rendern kann nur eine Schnittstelle schwer zu verstehen sind, sowie Uneasiness des Benutzers Augen und Brain-Problem verursacht, vornehmen.

## <a name="share-your-experience"></a>Teilen Sie Ihre Erfahrungen

Mithilfe von [mixed Reality-Erfassung](mixed-reality-capture.md), Benutzer können eines Fotos oder Videos des Benutzererlebnisses zu einem beliebigen Zeitpunkt erfassen. Erwägen Sie die Umgebungen in Ihrer app, in dem Sie Momentaufnahmen oder Videos empfehlen möchten.

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>Nutzen Sie die Windows Mixed Reality home basic UI-Elemente

Genau wie die Windows-PC-Umgebung mit dem Desktop gestartet wird, startet Windows Mixed Reality, mit der Startseite. Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) nutzt unsere ausgeprägten besser zu verstehen, und navigieren 3D stellen. Mit HoloLens ist Ihre Startseite Ihrer physischen Raum. Mit immersive Headsets ist Ihre Startseite einen virtuellen Ort.

Ihre Startseite ist auch, in dem Sie verwenden des Startmenüs zu öffnen, und platzieren Sie apps und Inhalt. Können Sie Ihre Startseite mit mixed Reality-Inhalt füllen und Multitasking mit mehreren apps zur gleichen Zeit. Die Dinge, die Sie in Ihrem Haus platzieren bleiben, selbst wenn Sie Ihr Gerät neu starten.

## <a name="see-also"></a>Siehe auch
* [Blicke für](gaze-targeting.md)
* [Gesten](gestures.md)
* [Voice-Entwurf](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Räumliche Entwurf](spatial-sound-design.md)
* [Räumliche Zuordnung entwerfen](spatial-mapping-design.md)
* [Comfort](comfort.md)
* [Navigieren Sie in der Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
