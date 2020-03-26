---
title: Was ist Mixed Reality?
description: In diesem Artikel wird Mixed Reality definiert und veranschaulicht, welche Teile des Mixed Reality-Spektrums von einfachen AR- und VR-Geräten sowie von Windows Mixed Reality-Geräten wie Microsoft HoloLens und immersiven Windows Mixed Reality-Headsets abgedeckt werden.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: Mixed Reality, Holographic, AR, VR, MR, XR, Augmented Reality, Virtual Reality, Erläuterung
ms.localizationpriority: high
ms.openlocfilehash: f170fe7a3353ac0cce1bd7532802eaff7a357494
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082080"
---
# <a name="what-is-mixed-reality"></a>Was ist Mixed Reality?

![Zeigen und Bestätigen mit den Händen auf HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality ist das Ergebnis der Verschmelzung der physischen Welt mit der digitalen Welt. Mixed Reality ist der nächste Evolutionsschritt in der Interaktion von Mensch, Computer und Umwelt und eröffnet Möglichkeiten, die bisher auf unsere Vorstellungskraft beschränkt waren. Dies wird durch Fortschritte beim maschinellen Sehen, der Grafikverarbeitungsleistung, den Anzeigetechnologien und den Eingabesystemen ermöglicht. Der Begriff *Mixed Reality* wurde ursprünglich 1994 in einer Arbeit von Paul Milgram und Fumio Kishino eingeführt, „[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)“. In diesem Artikel wurde das Konzept des *Virtualitätskontinuums* vorgestellt und schwerpunktmäßig behandelt, wie sich die Kategorisierung der Taxonomie auf Displays anwenden lässt. Seitdem geht die Anwendung von Mixed Reality über Displays hinaus. Sie schließt außerdem Umgebungseinflüsse, Raumklang und den Standort ein.

![Das Spektrum von Mixed Reality](images/mixedrealityspectrum-worlds.png)<br>
*Abbildung: Mixed Reality ist das Ergebnis der Verschmelzung der physischen Welt mit der digitalen Welt.*

<br>

---

## <a name="environmental-input-and-perception"></a>Umgebungseinfluss und Wahrnehmung

In den vergangenen Jahrzehnten wurde die Beziehung zwischen den von Menschen und von Computern stammenden Einflüssen gut untersucht. Es gibt sogar eine Fachrichtung mit der Bezeichnung *Mensch-Computer-Interaktion* (Human Computer Interaction, HCI), die sich großen Zulaufs erfreut. Menschliche Einflüsse erfolgen als Eingaben durch eine Reihe von Mitteln, darunter Tastaturen, Mäuse, Berührung, Freihand, Sprache und sogar Skelettnachverfolgung (Kinect).

Fortschritte bei Sensoren und Verarbeitung lassen ein neues Zeitalter der Computereingaben aus der Umgebung heraufziehen. Die Interaktion zwischen Computern und Umgebungen ist der Sache nach das Verstehen der Umwelt oder *Wahrnehmung*. Daher werden die Namen von APIs in Windows, die Umgebungsinformationen offenlegen, als [Wahrnehmungs-APIs](https://docs.microsoft.com/uwp/api/Windows.Perception) bezeichnet. Bei der Umgebungseingabe werden Dinge wie die Position einer Person in der Welt (z. B. [Kopfnachverfolgung](coordinate-systems.md)), Flächen und Begrenzungen (z. B. [räumliche Abbildung](spatial-mapping.md) und [Szenenverständnis](scene-understanding.md)), Umgebungslicht, Umgebungsgeräusche, Objekterkennung und Standort erfasst.

<br>

![Venn-Diagramm, das Interaktionen zwischen Computern, Menschen und Umgebungen anzeigt](images/mixed-reality-venn-diagram-300px.png)<br> 
*Abbildung: Die Interaktionen zwischen Computern, Menschen und Umgebungen.*

<br>

Die Kombination aus allen dreien – **Computerverarbeitung, menschliche Eingaben und Umgebungseingaben** –-eröffnet nun die Möglichkeit, echte Mixed Reality-Erfahrungen zu schaffen. Bewegung in der physischen Welt kann in Bewegung in der digitalen Wert übersetzt werden. Begrenzungen in der physischen Welt können in der digitalen Welt Einfluss auf das Erleben von Anwendungen haben, beispielsweise in Computerspielen. Ohne Umgebungseinfluss kann keine Mischung aus physischer und digitaler Realität entstehen.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Das Spektrum von Mixed Reality

Da Mixed Reality sowohl physische als auch digitale Welten kombiniert, definieren diese beiden Realitäten die Pole eines Spektrums, das als Virtualitätskontinuum bezeichnet wird. Der Einfachheit halber bezeichnen wir dies als *Spektrum von Mixed Reality*. Auf der linken Seite haben wir die physische Realität, in der wir Menschen leben. Auf der rechten Seite sehen wir die entsprechende digitale Realität.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Augmented Reality im Vergleich mit Virtual Reality

Die meisten aktuell verfügbaren Mobiltelefone haben kaum oder keine Fähigkeiten zum Verstehen der Umgebung. Daher können die von ihnen angebotenen Erfahrungen keine Mischung aus physischer und digitaler Realität darstellen. Die Benutzererfahrungen, bei denen Grafiken Videostreams der realen Welt überlagert werden, sind *Augmented Reality*. Die Benutzererfahrungen, die Ihre Sicht verdecken, um ein digitales Erlebnis darzustellen, sind *Virtual Reality*. Wie Sie sehen können, sind die Erfahrungen, die zwischen diesen beiden Extremen liegen, *Mixed Reality*:
* Ausgehend von der physischen Welt kann ein digitales Objekt platziert werden, etwa ein Hologramm, so, als wäre es wirklich vorhanden.
* Ausgehend von der physischen Welt kann eine digitale Darstellung einer anderen Person – ein Avatar – den Ort anzeigen, an dem die Person stand, als sie Notizen verfasste. Dies sind mit anderen Worten Benutzererfahrungen, die asynchrone Zusammenarbeit zu verschiedenen Zeitpunkten darstellen.
* Ausgehend von einer digitalen Welt können physische Begrenzungen der physischen Welt, wie etwa Wände und Möbel, digital innerhalb der Benutzererfahrung erscheinen, um Benutzern dabei zu helfen, physische Hindernisse zu umgehen.


<br>

![Das Spektrum von Mixed Reality](images/mixedrealityspectrum.png)<br>
*Abbildung: Das Spektrum von Mixed Reality*

<br>

Die meisten heute verfügbaren Angebote an Augmented Reality-und Virtual Reality stellen einen sehr kleinen Teil dieses Spektrums dar. Dabei handelt es sich jedoch um Teilmengen des größeren Mixed Reality-Spektrums. Windows 10 wurde im Hinblick auf das gesamte Spektrum konzipiert und ermöglicht das Mischen digitaler Darstellungen von Personen, Orten und Gegenständen mit der realen Welt.




## <a name="devices-and-experiences"></a>Geräte und Erlebnisse


Es gibt zwei Hauptarten von Geräten, die Windows Mixed Reality-Erlebnisse bieten:
1. **Holografische Geräte.** Diese zeichnen sich durch die Fähigkeit des Geräts aus, digitale Inhalte so in der realen Welt zu platzieren, als wären sie wirklich vorhanden.
2. **Immersive Geräte.** Diese zeichnen sich durch die Fähigkeit des Geräts aus, einen Eindruck von „Gegenwart“ zu erzeugen, indem sie die physische Welt ausblenden und sie durch ein digitales Erlebnis ersetzen.

<table>
<tr>
<th width="30%"> Merkmal</th><th width="35%"> Holografische -Geräte</th><th width="35%"> Immersive Geräte</th>
</tr><tr>
<td><strong>Beispielgerät</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Anzeige</strong></td><td> Transparente Anzeige. Ermöglicht Benutzern, die physische Umgebung zu sehen, während sie das Headset tragen.</td><td> Opake Anzeige. Sperrt die physische Umgebung während des Tragens des Headsets aus.</td>
</tr><tr>
<td><strong>Bewegung</strong></td><td> Volle sechs Freiheitsgrade für Bewegung, sowohl Drehung als auch Verschiebung.</td><td> Volle sechs Freiheitsgrade für Bewegung, sowohl Drehung als auch Verschiebung.</td>
</tr>
</table>



Beachten Sie: Ob ein Gerät (per USB-Kabel oder WLAN) mit einem separaten PC verbunden oder eigenständig (nicht verbunden) ist, sagt nichts darüber aus, ob das Gerät holografisch oder immersiv ist. Naturgemäß führen Features, die eine Verbesserung der Mobilität bewirken, zu besseren Benutzererfahrungen, und sowohl holografische als auch immersive Geräte können gebunden oder eigenständig sein.


Es ist der technische Fortschritt, der Mixed Reality-Erfahrungen ermöglicht hat. Heutzutage gibt es keine Geräte, die das gesamte Spektrum der Erfahrungen ausführen können. Windows 10 bietet jedoch eine gemeinsame Mixed Reality-Plattform für Gerätehersteller und Entwickler. Heutzutage können Geräte einen bestimmten Bereich innerhalb des Mixed Reality-Spektrums unterstützen. Im Laufe der Zeit werden neue Geräte diesen Bereich erweitern. In Zukunft werden holografische Geräte immersiver und immersive Geräte stärker holografisch.

<br>

![Gerätetypen im Mixed Reality-Spektrum](images/Final_WhatIsMixedReality07.png)<br>
*Abbildung: Der Platz von Geräten im Mixed Reality-Spektrum*

Häufig ist es am besten, sich zu überlegen, welche Art von Erfahrung ein Anwendungs- oder Spielentwickler schaffen möchte. Die Erfahrungen zielen normalerweise auf einen bestimmten Punkt oder Teil des Spektrums ab. Außerdem sollten Entwickler die Fähigkeiten der Geräte berücksichtigen, für die sie entwickeln möchten. Beispielsweise lassen sich Erfahrungen, die auf der physischen Welt basieren, optimal in HoloLens ausführen.
* **Mehr links (nahe an der physischen Realität).** Benutzer verbleiben in ihrer physischen Umgebung, und ihnen wird nie vermittelt, sie hätten diese Umgebung verlassen.
* **In der Mitte (vollständige Mixed Reality).** Diese Benutzererfahrungen bestehen aus einer Mischung aus realer Welt und digitaler Welt. Leser, die den Film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) gesehen haben, können nachvollziehen, wie die physische Struktur des Hauses, in dem die Geschichte spielt, mit einer Dschungelumgebung gemischt wurde.
* **Mehr rechts (nahe an der digitalen Realität).** Die Benutzer erleben eine vollständig digitale Umgebung und sind sich nicht bewusst, was sich in der sie umgebenden physischen Umgebung ereignet.


## <a name="see-also"></a>Siehe auch

* [Was ist ein Hologramm?](hologram.md)
* [Verstehen der Grundlagen von Mixed Reality](index.md#understand-the-basics)
* [Einstieg in Erschaffen und Prototyping](design.md)
* [Erlernen von Tools und Architektur](development.md)

