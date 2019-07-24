---
title: Was ist Mixed Reality?
description: In diesem Artikel wird die gemischte Realität erläutert, und es wird veranschaulicht, wo einfache AR-und VR-Geräte sowie Windows Mixed Reality-Geräte wie Microsoft hololens und Windows Mixed Reality-immersive Headsets entlang des gemischten Reality-Spektrums sitzen.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: Mixed Reality, Holographic, AR, VR, Mr, XR, Augmented Reality, Virtual Reality, Erläuterung
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326315"
---
# <a name="what-is-mixed-reality"></a>Was ist Mixed Reality?

Gemischte Realität ist das Ergebnis der Mischung der physischen Welt mit der digitalen Welt. Gemischte Realität ist die nächste Weiterentwicklung bei der Interaktion von Menschen, Computern und Umgebungen sowie bei der Beseitigung von Möglichkeiten, die bisher auf unsere imagationen beschränkt waren. Dies wird durch Weiterentwicklungen bei Maschinelles sehen, grafischer Verarbeitungsleistung, Anzeige Technologie und Eingabe Systemen ermöglicht. Der Begriff " *gemischte Realität* " wurde ursprünglich in einem 1994 Paper von Paul Milgram und Fumio Kishino eingeführt, "[eine Taxonomie von visuellen Darstellung in gemischter Realität](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". In diesem Artikel wurde das Konzept des *virtualisierungskontinuums*vorgestellt, und es wurde darauf eingegangen, wie die Kategorisierung der Taxonomie auf angezeigt wird. Seitdem geht die Anwendung von Mixed Reality über die Anzeige hinaus. Außerdem sind Umgebungs Eingaben, räumlicher Sound und Speicherort enthalten.

## <a name="environmental-input-and-perception"></a>Umwelt Eingabe und-Wahrnehmung

![Venn-Diagramm, das Interaktionen zwischen Computern, Menschen und Umgebungen anzeigt](images/mixed-reality-venn-diagram-300px.png)<br> 

In den vergangenen Jahrzehnten wurde die Beziehung zwischen der Eingabe von Menschen und Computern gut untersucht. Es verfügt sogar über eine weit verbreitete Disziplin, die als Interaktion mit dem Benutzer *Computer* oder HCI bezeichnet wird. Menschen Eingaben werden auf verschiedene Weise durchgeführt, einschließlich Tastaturen, Mäuse, Finger Eingaben, Freihand-und Spracheingaben und sogar kinect-Skelett Nachverfolgung.

Verbesserungen bei Sensoren und der Verarbeitung erhöhen den neuen Bereich der Computer Eingaben aus Umgebungen. Die Interaktion zwischen Computern und Umgebungen ist praktisch das Verständnis der Umgebung und die *Wahrnehmung*. Die API-Namen in Windows, die Umgebungs Informationen offenlegen, werden daher als [perception-APIs](https://docs.microsoft.com/uwp/api/Windows.Perception)bezeichnet. In der Umgebungs Eingabe werden Dinge wie die Position einer Person (z. b. [Kopf Nachverfolgung](coordinate-systems.md)), Oberflächen und Grenzen (z. b. [räumliche Zuordnung](spatial-mapping.md) und [räumliches Verständnis](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), Umgebungsbeleuchtung, Umgebungs Sound, Objekt Erkennung und Speicherort.

Die Kombination aus allen drei Computer-, Benutzer-und Umgebungs Eingaben bietet nun die Möglichkeit, echte gemischte Realität zu schaffen. Bewegung durch die physische Welt kann zu einer Bewegung in der digitalen Welt führen. Grenzen in der physischen Welt können die Anwendungserfahrung beeinflussen, wie z. b. Spiele Spiele, in der digitalen Welt. Ohne Umgebungs Eingabe können Umgebungen nicht zwischen physischer und digitaler Realität verschmelzen.

## <a name="the-mixed-reality-spectrum"></a>Das gemischte Reality-Spektrum

Da Mixed Reality sowohl physische als auch digitale Welten kombiniert, definieren diese beiden Realitäten die Polar Enden eines Spektrums, das als Virtualität Continuum bezeichnet wird. Der Einfachheit halber wird dies als *gemischtes Reality-Spektrum*bezeichnet. Auf der linken Seite haben wir eine physische Realität, in der wir, Menschen, vorhanden sind. auf der rechten Seite haben wir die entsprechende digitale Realität.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

Die meisten Mobiltelefone auf dem Markt haben heute kaum noch keine Kenntnisse in der Umwelt Umgebung. Daher können die von Ihnen angebotenen Erfahrungen nicht zwischen physischen und digitalen Realitäten gemischt werden. Die Umgebung, in der Grafiken in Videostreams der physischen Welt überlagern werden, ist die *Erweiterte Realität*. Die Umgebung, in der Ihre Ansicht zur Verfügung steht, um ein digitales Erlebnis zu bieten, ist die *virtuelle Realität*. Wie Sie sehen können, sind die zwischen diesen beiden extremen aktivierten Erfahrungen *gemischt*:
* Angefangen mit der physischen Welt, das Platzieren eines digitalen Objekts, z. b. eines Hologramms, so, als wäre es wirklich vorhanden.
* Beginnend mit der physischen Welt, eine digitale Darstellung einer anderen Person (ein Avatar), zeigt die Position an, an der Sie beim hinterlassen von Notizen standen. Anders ausgedrückt: Erfahrungen, die die asynchrone Zusammenarbeit zu unterschiedlichen Zeitpunkten darstellen.
* Beginnend mit einer digitalen Welt werden physische Grenzen von der physischen Welt, wie z. b. Wände und Möbel, in der Umgebung digital angezeigt, um Benutzer bei der Vermeidung physischer Objekte zu unterstützen.

![Das gemischte Reality-Spektrum](images/mixed-reality-spectrum-550px.png)

Die meisten heute verfügbaren erweiterten Reality-und Virtual Reality-Angebote stellen einen sehr kleinen Teil dieses Spektrums dar. Dabei handelt es sich jedoch um Teilmengen des größeren gemischten Reality-Spektrums. Windows 10 basiert auf dem gesamten Spektrum und ermöglicht die Mischung digitaler Darstellungen von Personen, Orten und Dingen in der realen Welt.

![Gerätetypen im gemischten Reality-Spektrum](images/mixed-reality-spectrum-device-types-550px.png)

Es gibt zwei Hauptarten von Geräten, die Windows Mixed Reality-Umgebungen bereitstellen:
1. **Holographic-Geräte.** Diese sind durch die Fähigkeit des Geräts gekennzeichnet, digitale Inhalte in der realen Welt zu platzieren, als wäre es wirklich vorhanden.
2. **Immersive Geräte.** Diese sind durch die Fähigkeit des Geräts gekennzeichnet, eine Vorstellung von "Präsenz" zu schaffen, die physische Welt zu verbergen und durch eine digitale Umgebung zu ersetzen.

<table>
<tr>
<th width="20%"> Merkmal</th><th width="40%"> Holographic-Geräte</th><th width="40%"> Immersive Geräte</th>
</tr><tr>
<td> Beispiel Gerät</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows Mixed Reality Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Anzeige</td><td> <i>Siehe anzeigen.</i> Ermöglicht Benutzern das Anzeigen der physischen Umgebung beim durch tragen des Headsets.</td><td> <i>Nicht transparente Anzeige.</i> Blockiert die physische Umgebung beim durch tragen des Headsets.</td>
</tr><tr>
<td> Bewegung</td><td> Vollständige Bewegung von sechs Grad an Freiheit, sowohl Drehung als auch Übersetzung.</td><td> Vollständige Bewegung von sechs Grad an Freiheit, sowohl Drehung als auch Übersetzung.</td>
</tr>
</table>

Beachten Sie, ob ein Gerät mit einem separaten PC (über USB-Kabel oder Wi-Fi) verbunden ist oder ob es sich in einem eigenständigen PC oder in einem eigenständigen (untethering) Gerät befindet. Natürlich sind Features, die die Mobilität verbessern, zu besseren Erfahrungen geführt, und sowohl Holographic-als auch immersive Geräte könnten in den Team-oder untethering-Umgebungen kommen.

## <a name="devices-and-experiences"></a>Geräte und Erfahrungen

Der technologische Fortschritt ist die Aktivierung gemischter Reality-Umgebungen. Heutzutage gibt es keine Geräte, auf denen das gesamte Spektrum von Umgebungen ausgeführt werden kann. Windows 10 bietet jedoch eine gemeinsame gemischte Reality-Plattform für Gerätehersteller und Entwickler. Heutzutage können Geräte einen bestimmten Bereich innerhalb des gemischten Reality-Spektrums unterstützen. Im Laufe der Zeit werden neue Geräte diesen Bereich erweitern. In Zukunft werden Holographic-Geräte rekursiver, und immersive Geräte werden eher holografisch.

![Wo sich Geräte im gemischten Reality-Spektrum befinden](images/mixed-reality-spectrum-device-placement-550px.png)

Häufig ist es am besten, zu sehen, welche Art von Anwendung ein Anwendungs-oder Spielentwickler erstellen möchte. Die Oberfläche wird in der Regel auf einen bestimmten Punkt oder einen bestimmten Teil des Spektrums ausgerichtet. Dann sollten Entwickler die Funktionen von Geräten berücksichtigen, auf die Sie abzielen möchten. Beispielsweise werden Erfahrungen, die auf der physischen Welt basieren, am besten in hololens ausgeführt.
* **Auf der linken Seite (in der Nähe der physischen Realität).** Benutzer bleiben in ihrer physischen Umgebung präsent und werden niemals darauf hingewiesen, dass Sie diese Umgebung verlassen haben.
* **In der Mitte (vollständig gemischt).** Diese Oberflächen werden in der realen Welt und in der digitalen Welt miteinander verschmelzen. Viewer, die den Film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) gesehen haben, können abstimmen, wie die physische Struktur des Hauses, in dem die Story stattfand, mit einer Dschungel Umgebung gemischt wurde.
* **Auf der rechten Seite (in der Nähe digitaler Realität).** Benutzer erleben eine vollständig digitale Umgebung und wissen nicht, was in der physischen Umgebung herum passiert.


## <a name="see-also"></a>Siehe auch
* [API-Referenz: Windows. perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API-Referenz: Windows. perception. Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API-Referenz: Windows. perception. Spatial. Oberflächen](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
