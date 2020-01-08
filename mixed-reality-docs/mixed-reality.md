---
title: Was ist Mixed Reality?
description: In diesem Artikel wird die gemischte Realität erläutert, und es wird veranschaulicht, wo einfache AR-und VR-Geräte sowie Windows Mixed Reality-Geräte wie Microsoft hololens und Windows Mixed Reality-immersive Headsets entlang des gemischten Reality-Spektrums sitzen.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: Mixed Reality, Holographic, AR, VR, Mr, XR, Augmented Reality, Virtual Reality, Erläuterung
ms.openlocfilehash: e3205590ce46e0fc9113421e0dbaeb87fe6bc0c2
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334035"
---
# <a name="what-is-mixed-reality"></a>Was ist Mixed Reality?

![Point und Commit mit Händen auf hololens 2](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality ist das Ergebnis der Verschmelzung der physischen Welt mit der digitalen Welt. Mixed Reality ist der nächste Evolutionsschritt in der Interaktion von Mensch, Computer und Umwelt und eröffnet Möglichkeiten, die bisher auf unsere Vorstellungskraft beschränkt waren. Dies wird durch Weiterentwicklungen bei Maschinelles sehen, grafischer Verarbeitungsleistung, Anzeige Technologie und Eingabe Systemen ermöglicht. Der Begriff " *gemischte Realität* " wurde ursprünglich in einem 1994 Paper von Paul Milgram und Fumio Kishino eingeführt, "[eine Taxonomie von visuellen Darstellung in gemischter Realität](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". In diesem Artikel wurde das Konzept des *virtualisierungskontinuums*vorgestellt, und es wurde darauf eingegangen, wie die Kategorisierung der Taxonomie auf angezeigt wird. Seitdem geht die Anwendung von Mixed Reality über die Anzeige hinaus. Außerdem sind Umgebungs Eingaben, räumlicher Sound und Speicherort enthalten.

![Sie das gemischte Reality-Spektrum](images/mixedrealityspectrum-worlds.png)<br>
*Image: Gemischte Realität ist das Ergebnis der Mischung der physischen Welt mit der digitalen Welt.*

<br>

---

## <a name="environmental-input-and-perception"></a>Umwelt Eingabe und-Wahrnehmung

In den vergangenen Jahrzehnten wurde die Beziehung zwischen der Eingabe von Menschen und Computern gut untersucht. Es verfügt sogar über eine weit verbreitete Disziplin, die als Interaktion mit dem Benutzer *Computer* oder HCI bezeichnet wird. Menschen Eingaben werden auf verschiedene Weise durchgeführt, einschließlich Tastaturen, Mäuse, Finger Eingaben, Freihand-und Spracheingaben und sogar kinect-Skelett Nachverfolgung.

Verbesserungen bei Sensoren und der Verarbeitung erhöhen den neuen Bereich der Computer Eingaben aus Umgebungen. Die Interaktion zwischen Computern und Umgebungen ist praktisch das Verständnis der Umgebung und die *Wahrnehmung*. Die API-Namen in Windows, die Umgebungs Informationen offenlegen, werden daher als [perception-APIs](https://docs.microsoft.com/uwp/api/Windows.Perception)bezeichnet. In der Umgebungs Eingabe werden Dinge wie die Position einer Person (z. b. [Kopf Nachverfolgung](coordinate-systems.md)), Oberflächen und Grenzen (z. b. [räumliche Zuordnung](spatial-mapping.md) und [Szenen Verständnis](scene-understanding.md)), Umgebungsbeleuchtung, Umgebungs Sound, Objekterkennung und Standort erfasst.

<br>

![Venn-Diagramm, das Interaktionen zwischen Computern, Menschen und Umgebungen anzeigt](images/mixed-reality-venn-diagram-300px.png)<br> 
*Abbildung: Interaktionen zwischen Computern, Menschen und Umgebungen.*

<br>

Die Kombination aus allen drei Computer-, Benutzer-**und Umgebungs Eingaben**bietet nun die Möglichkeit, echte gemischte Realität zu schaffen. Bewegung durch die physische Welt kann zu einer Bewegung in der digitalen Welt führen. Grenzen in der physischen Welt können die Anwendungserfahrung beeinflussen, wie z. b. Spiele Spiele, in der digitalen Welt. Ohne Umgebungs Eingabe können Umgebungen nicht zwischen physischer und digitaler Realität verschmelzen.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Das gemischte Reality-Spektrum

Da Mixed Reality sowohl physische als auch digitale Welten kombiniert, definieren diese beiden Realitäten die Polar Enden eines Spektrums, das als Virtualität Continuum bezeichnet wird. Der Einfachheit halber wird dies als *gemischtes Reality-Spektrum*bezeichnet. Auf der linken Seite haben wir eine physische Realität, in der wir, Menschen, vorhanden sind. auf der rechten Seite haben wir die entsprechende digitale Realität.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Versteigerte und virtuelle Realität

Die meisten Mobiltelefone auf dem Markt haben heute kaum noch keine Kenntnisse in der Umwelt Umgebung. Daher können die von Ihnen angebotenen Erfahrungen nicht zwischen physischen und digitalen Realitäten gemischt werden. Die Umgebung, in der Grafiken in Videostreams der physischen Welt überlagern werden, ist die *Erweiterte Realität*. Die Umgebung, in der Ihre Ansicht zur Verfügung steht, um ein digitales Erlebnis zu bieten, ist die *virtuelle Realität*. Wie Sie sehen können, sind die zwischen diesen beiden extremen aktivierten Erfahrungen *gemischt*:
* Angefangen mit der physischen Welt, das Platzieren eines digitalen Objekts, z. b. eines Hologramms, so, als wäre es wirklich vorhanden.
* Beginnend mit der physischen Welt, eine digitale Darstellung einer anderen Person (ein Avatar), zeigt die Position an, an der Sie beim hinterlassen von Notizen standen. Anders ausgedrückt: Erfahrungen, die die asynchrone Zusammenarbeit zu unterschiedlichen Zeitpunkten darstellen.
* Beginnend mit einer digitalen Welt werden physische Grenzen von der physischen Welt, wie z. b. Wände und Möbel, in der Umgebung digital angezeigt, um Benutzer bei der Vermeidung physischer Objekte zu unterstützen.


<br>

![Sie das gemischte Reality-Spektrum](images/mixedrealityspectrum.png)<br>
*Bild: das gemischte Reality-Spektrum*

<br>

Die meisten heute verfügbaren erweiterten Reality-und Virtual Reality-Angebote stellen einen sehr kleinen Teil dieses Spektrums dar. Dabei handelt es sich jedoch um Teilmengen des größeren gemischten Reality-Spektrums. Windows 10 basiert auf dem gesamten Spektrum und ermöglicht die Mischung digitaler Darstellungen von Personen, Orten und Dingen in der realen Welt.




## <a name="devices-and-experiences"></a>Geräte und Erfahrungen


Es gibt zwei Hauptarten von Geräten, die Windows Mixed Reality-Umgebungen bereitstellen:
1. **Holographic-Geräte.** Diese sind durch die Fähigkeit des Geräts gekennzeichnet, digitale Inhalte in der realen Welt zu platzieren, als wäre es wirklich vorhanden.
2. **Immersive Geräte.** Diese sind durch die Fähigkeit des Geräts gekennzeichnet, eine Vorstellung von "Präsenz" zu schaffen, die physische Welt zu verbergen und durch eine digitale Umgebung zu ersetzen.

<table>
<tr>
<th width="30%"> Merkmal</th><th width="35%"> Holographic-Geräte</th><th width="35%"> Immersive Geräte</th>
</tr><tr>
<td><strong>Beispiel Gerät</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssee und höher<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Display</strong></td><td> Siehe anzeigen. Ermöglicht Benutzern das Anzeigen der physischen Umgebung beim durch tragen des Headsets.</td><td> Nicht transparente Anzeige. Blockiert die physische Umgebung beim durch tragen des Headsets.</td>
</tr><tr>
<td><strong>Bewegung</strong></td><td> Vollständige Bewegung von sechs Grad an Freiheit, sowohl Drehung als auch Übersetzung.</td><td> Vollständige Bewegung von sechs Grad an Freiheit, sowohl Drehung als auch Übersetzung.</td>
</tr>
</table>



Beachten Sie, ob ein Gerät mit einem separaten PC (über USB-Kabel oder Wi-Fi) verbunden ist oder ob es sich in einem eigenständigen PC oder in einem eigenständigen (untethering) Gerät befindet. Natürlich sind Features, die die Mobilität verbessern, zu besseren Erfahrungen geführt, und sowohl Holographic-als auch immersive Geräte könnten in den Team-oder untethering-Umgebungen kommen.


Der technologische Fortschritt ist die Aktivierung gemischter Reality-Umgebungen. Heutzutage gibt es keine Geräte, auf denen das gesamte Spektrum von Umgebungen ausgeführt werden kann. Windows 10 bietet jedoch eine gemeinsame gemischte Reality-Plattform für Gerätehersteller und Entwickler. Heutzutage können Geräte einen bestimmten Bereich innerhalb des gemischten Reality-Spektrums unterstützen. Im Laufe der Zeit werden neue Geräte diesen Bereich erweitern. In Zukunft werden Holographic-Geräte rekursiver, und immersive Geräte werden eher holografisch.

<br>

![Gerätetypen im gemischten Reality-Spektrum](images/Final_WhatIsMixedReality07.png)<br>
*Image: wo Geräte im gemischten Reality-Spektrum vorhanden sind*

Häufig ist es am besten, zu sehen, welche Art von Anwendung ein Anwendungs-oder Spielentwickler erstellen möchte. Die Oberfläche wird in der Regel auf einen bestimmten Punkt oder einen bestimmten Teil des Spektrums ausgerichtet. Dann sollten Entwickler die Funktionen von Geräten berücksichtigen, auf die Sie abzielen möchten. Beispielsweise werden Erfahrungen, die auf der physischen Welt basieren, am besten in hololens ausgeführt.
* **Auf der linken Seite (in der Nähe der physischen Realität).** Benutzer bleiben in ihrer physischen Umgebung präsent und werden niemals darauf hingewiesen, dass Sie diese Umgebung verlassen haben.
* **In der Mitte (vollständig gemischt).** Diese Oberflächen werden in der realen Welt und in der digitalen Welt miteinander verschmelzen. Viewer, die den Film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) gesehen haben, können abstimmen, wie die physische Struktur des Hauses, in dem die Story stattfand, mit einer Dschungel Umgebung gemischt wurde.
* **Auf der rechten Seite (in der Nähe digitaler Realität).** Benutzer erleben eine vollständig digitale Umgebung und wissen nicht, was in der physischen Umgebung herum passiert.


## <a name="see-also"></a>Weitere Informationen:

* [Was ist ein Hologramm?](hologram.md)
* [Verstehen der Grundlagen von Mixed Reality](index.md#understand-the-basics)
* [Beginnen Sie mit dem Erstellen und Prototypen](design.md)
* [Erlernen von Tools und Architektur](development.md)

