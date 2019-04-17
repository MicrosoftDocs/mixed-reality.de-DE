---
title: Was ist die Realität gemischter?
description: Dieser Artikel definiert, mixed Reality und veranschaulicht, in dem einfachen AR und VR-Geräte als auch Windows Mixed Reality-Geräte, wie Microsoft HoloLens und Windows Mixed Reality immersive Headsets, entlang des Spektrums mixed Reality befinden.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Realität, holographic, Ar, Vr, Mr, Xr, augmented Reality-Modus, virtuelle Realität, Erklärung
ms.openlocfilehash: 3f6000b3d700d7c13f1efa13a81561464f8fdad1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604814"
---
# <a name="what-is-mixed-reality"></a>Was ist die Realität gemischter?

Gemischte Realität ist das Ergebnis der Kombination der realen Welt mit der digitalen Welt. Gemischte Realität ist der nächste Entwicklungsschritt bei Menschen, Computer- und Umgebung Interaktion und entsperrt Möglichkeiten, die zuvor auf unsere Imaginations beschränkt waren. Es wird durch Verbesserungen im Computer Vision, grafische verarbeitungsleistung, Technologie und Eingabesysteme ermöglicht. Der Begriff *mixed Reality* wurde ursprünglich von Paul Milgram und Fumio Kishino, finden Sie im Dokument 1994 eingeführt "[eine Taxonomie für Mixed Reality Visual zeigt](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)." Ihre Artikel wurde das Konzept der eingeführt. die *Virtuality Continuum* und spezialisiert auf die Anzeige von der Kategorisierung der Taxonomie angewendet. Seit damals wechselt die Anwendung von mixed Reality darüber hinaus zeigt enthält jedoch auch environmental Eingabe, räumliche Sound und Speicherort.

## <a name="environmental-input-and-perception"></a>Environmental Eingabe- und Wahrnehmung

![Venn-Diagramm darstellen der Interaktionen zwischen Computern, die Menschen und Umgebungen](images/mixed-reality-venn-diagram-300px.png)<br> 

Über den letzten Dekaden hat die Beziehung zwischen menschlichem Input und Computer Eingabe auch untersucht wurden. Sie verfügt sogar über eine erforschten Disziplin, bekannt als *Interaktionen zwischen menschlichen Computer* oder HCI erfolgreich abgeschlossen hatte. Menschlichem Input erfolgt über verschiedene Methoden, einschließlich Tastaturen, Mäuse, Touch, Freihandeingaben, Sprach- und sogar etwas grob strukturierte Kinect-nachverfolgung.

Fortschritte in der Sensoren und -Verarbeitung sind Anstieg in der Eingabe der Computer einen neuen Bereich aus Umgebungen gewähren. Die Interaktion zwischen Computern und Umgebungen ist effektiv Umgebung besser zu verstehen, oder *Perception*. Daher werden die API-Namen in Windows, das Offenlegen von Umgebungsinformationen bezeichnet die [Perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception). Environmental Eingabe erfasst, z.B. einer Person Position in der ganzen Welt (z. B. [Head nachverfolgung](coordinate-systems.md)), Flächen und Grenzen (z. B. [räumliche Zuordnung](spatial-mapping.md) und [räumliche Verständnis](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), umgebenden Beleuchtung, Umwelt Sound, objekterkennung und Speicherort.

Jetzt die Kombination aller drei: Computer zu verarbeiten, Straßenbilder und environmental Eingabe – legt fest, die Möglichkeit, um auf "true" mixed Reality zu schaffen. Verschieben von Daten in die digitale Welt kann verschieben über die physische Welt übersetzt werden. Grenzen in der realen Welt können Funktionsumfang einer Anwendung, z. B. Spiels, in der digitalen Welt beeinflussen. Ohne environmental Eingabe können nicht das wirkliche physische und digitale Erfahrungen angleichen.

## <a name="the-mixed-reality-spectrum"></a>Das Spektrum mixed reality

Da gemischte Realität die Kombination der realen Welt und digitalen Welt ist, definieren Sie zwei Problemen konfrontiert polar Ende ein Spektrum an, das Kontinuum Virtuality genannt. Der Einfachheit halber wir bezeichnen dies als die *mixed Reality Spektrum*. Auf der linken Seite haben wir die physischen Realität, in denen wir Menschen vorhanden sein. Dann müssen wir auf der rechten Seite die entsprechenden digitale Realität.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

Die meisten Mobiltelefone auf dem Markt haben heute kleine Funktionen keine Umgebung verstehen. Daher können die Erfahrungen angebotenen zwischen physischen und digitale Realitäten nicht mischen. Die Benutzeroberflächen, die Überlagern von Grafiken auf video-Streams, der physischen Welt sind *augmented Reality*, und die Benutzeroberflächen, die Ihrer Ansicht um eine digitale Inhalte zu präsentieren verdeckt sind *virtuelle Realität*. Wie Sie sehen können, ist die Benutzeroberflächen, die zwischen diesen beiden extremen aktiviert *mixed Reality*:
* Beginnend mit der realen Welt, platzieren ein digitales Objekt, z. B. ggf. ein Hologramm, als gäbe es wirklich.
* Beginnend mit der realen Welt digitaler Darstellungen von einer anderen Person zeigt – ein Avatar – den Speicherort, in dem sie ständigen wurden beim Verlassen der Anmerkungen zu dieser Version. Das heißt, Benutzeroberflächen, die asynchrone Zusammenarbeit zu unterschiedlichen Zeitpunkten Zeitpunkt darstellen.
* Mit einer digitalen Welt werden angezeigt physische Grenzen hinaus aus der realen Welt, z. B. Wände und Möbel, Digital auf der Oberfläche für Benutzer physischen Objekte zu vermeiden.

![Das Spektrum mixed reality](images/mixed-reality-spectrum-550px.png)

Die meisten augmented Reality-Modus und virtuelle Realität Angebote stellen heute einen sehr kleinen Teil dieser Spektrum dar. Sie sind jedoch Teilmengen der größeren mixed Reality-Auftragsübermittlung. Windows 10 basiert auf das gesamte Spektrum Denken Sie daran, und ermöglicht die Kombination von digitaler Darstellungen von Personen, Orte und Aufgaben mit der realen Welt.

![Gerätetypen in das Spektrum mixed reality](images/mixed-reality-spectrum-device-types-550px.png)

Es gibt zwei Haupttypen von Geräten, die Windows Mixed Reality-Funktionen bereitzustellen:
1. **Holographic-Geräten.** Diese sind durch die Fähigkeit des Geräts digitalen Inhalte in der realen Welt platziert werden, als wäre es eigentlich nur gekennzeichnet.
2. **Immersive Geräte.** Diese werden durch die Fähigkeit des Geräts erstellen Sie einen Eindruck von "Anwesenheit" – durch das Ausblenden der realen Welt, und Ersetzen durch eine digitale Inhalte charakterisiert.

<table>
<tr>
<th width="20%"> Merkmal</th><th width="40%"> Holographic-Geräten</th><th width="40%"> Immersive Geräte</th>
</tr><tr>
<td> Beispiel-Gerät</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows Mixed Reality Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Anzeige</td><td> <i>Durchsichtigen anzeigen.</i> Ermöglicht Benutzer, die physische Umgebung angezeigt wird, wenn Sie den Kopfhörer trägt.</td><td> <i>Nicht transparente Anzeige.</i> Blockiert, während der Kopfhörer trägt der physischen Umgebung.</td>
</tr><tr>
<td> Datenverschiebung</td><td> Vollständige Verschiebung von sechs Grad von Freiheit, sowohl der Drehung und Übersetzung.</td><td> Vollständige Verschiebung von sechs Grad von Freiheit, sowohl der Drehung und Übersetzung.</td>
</tr>
</table>

Beachten Sie, dass gibt an, ob ein Gerät verbunden oder für das verbundene auf einem separaten PC (per USB-Kabel oder WLAN) oder eigenständig (unabhängig) wird nicht angezeigt, ob ein Gerät holographic oder eine immersive ist. Natürlich konnte Features, die Mobilität Lead für eine bessere benutzererfahrung und holographic und immersive Geräte verbessern für das verbundene oder kontinuierlich sein.

## <a name="devices-and-experiences"></a>Geräte und Erfahrungen

Technologischen Fortschritt ist was mixed Reality-Funktionen aktiviert hat. Es sind keine noch heute, die Funktionen für das gesamte Spektrum ausgeführt werden können; Windows 10 bietet jedoch eine allgemeine mixed Reality-Plattform für Hersteller von Geräten und Entwickler. Geräte können noch heute einen bestimmten Bereich innerhalb des Spektrums mixed Reality unterstützen, und im Laufe der Zeit neue Geräte, Bereich erweitern soll. In Zukunft holographic-Geräten wird seine, und immersive Geräte mehr holographic werden.

![Erstellen, in denen Geräte auf das Spektrum mixed reality](images/mixed-reality-spectrum-device-placement-550px.png)

Häufig empfiehlt sich, Sie denken, welche Art von Umgebung eine app oder Spieleentwickler erstellen möchte. Die Benutzeroberflächen werden in der Regel einen bestimmten Zeitpunkt oder einen Teil des Spektrums abzielen. Klicken Sie dann, sollten Entwickler die Funktionen von Geräten, die sie abzielen möchten. Benutzeroberflächen, die abhängig von der realen Welt werden z. B. für HoloLens bewährte ausgeführt.
* **Klicken Sie auf der linken Seite (in der Nähe physischen Realität).** Benutzer in ihrer physischen Umgebung beibehalten und nie vorgenommen werden, zu glauben, dass sie diese Umgebung verlassen haben.
* **In der Mitte (vollständig mixed Reality).** Diese Erfahrungen in der realen Welt und die digitale Welt perfekt blend. Wenn andere Benutzer den Film gesehen haben [Jumanji](https://en.wikipedia.org/wiki/Jumanji) können abstimmen, wie die physische Struktur des Hauses, in denen die Story fand, in einer Umgebung (Decision Jungle) kombiniert wurde.
* **Klicken Sie auf der rechten Seite (in der Nähe digitale Realität).** Benutzer eine vollständig digitale Umgebung sind und keine Ahnung von in der physischen Umgebung, um sie herum Abläufe.


## <a name="see-also"></a>Siehe auch
* [API-Referenz: Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API-Referenz: Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API-Referenz: Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
