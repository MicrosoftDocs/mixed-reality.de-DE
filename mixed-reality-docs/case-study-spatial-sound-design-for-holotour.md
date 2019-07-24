---
title: 'Fallstudie: räumliches Sound Design für holotour'
description: Zum Erstellen einer wahrhaft immersiven 3D-Tour für Microsoft hololens sind die Panorama Videos und Holographic-Kulissen nur Teil der Formel.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, holotour, räumlicher Sound, Fallstudie
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522444"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Fallstudie: räumliches Sound Design für holotour

Zum Erstellen einer wahrhaft immersiven 3D-Tour für Microsoft hololens sind die Panorama Videos und Holographic-Kulissen nur Teil der Formel. Der audiodesigner Jason syltebo spricht darüber, wie Sound aufgezeichnet und verarbeitet wurde, um Ihnen zu ermöglichen, dass Sie sich an jedem der Orte in holotour befinden.

## <a name="the-tech"></a>Die Technologie

Die wunderbare Darstellung und Holographic Szenen, die in holotour angezeigt werden, sind nur ein Teil der Erstellung einer glaubwürdigen gemischten Realität. Obwohl holograms nur visuell vor einem Benutzer angezeigt werden können, ermöglicht das [räumliche Sound](spatial-sound.md) Feature von hololens die Verwendung von Audio aus allen Richtungen, wodurch dem Benutzer eine vollständigere sensoringfunktionalität zur Verfügung steht.

Räumlicher Sound ermöglicht es uns, audiocues anzugeben, um eine Richtung anzugeben, in der der Benutzer eine Umwandlung durchgeführt werden soll, oder um dem Benutzer mitzuteilen, dass es mehr Hologramme gibt, damit Sie in Ihrem Raum angezeigt werden. Wir können einem – Hologramm auch einen Sound direkt anfügen und die Richtung fortlaufend aktualisieren, und das – Hologramm wird von einem Benutzer entfernt, damit es so erscheint, als ob der Sound direkt aus diesem Objekt stammt.

Mit holotour wollten wir die räumlichen Audiofunktionen von hololens nutzen, um eine Umgebung mit 360-Grad-Umgebung zu erstellen, die mit dem Video synchronisiert wird, um die Highlights der einzelnen Orte zu verdeutlichen.

## <a name="behind-the-scenes"></a>Im Hintergrund

Wir haben holotour-Erfahrungen von zwei verschiedenen Standorten erstellt: Rom und Machu Picchu. Damit diese Touren authentisch und aussagekräftigen sind, wollten wir die Verwendung von generischen Sounds vermeiden und stattdessen Audio direkt an den Standorten erfassen, an denen wir das Buch gedreht haben.

### <a name="capturing-the-audio"></a>Erfassen der Audiodatei

In unserer [Fallstudie zur Erfassung des visuellen Inhalts für holotour](case-study-capturing-and-creating-content-for-holotour.md)haben wir uns über den benutzerdefinierten Entwurf unseres Kamera-Rigs gesprochen. Es umfasste 14 GoPro-Kameras, die in einem 3D-gedruckten Gehäuse enthalten waren, das auf die spezifischen Abmessungen des-endms zugeschnitten ist. Um Audiodaten von diesem Rig zu erfassen, haben wir unter den Kameras ein vier-Mikrofon-Array hinzugefügt, das in eine kompakte 4-Kanal-Aufzeichnungseinheit gebracht wurde, die an der Basis des Stamms saß. Wir haben das Mikrofon ausgewählt, das nicht nur gut ausgeführt wurde, sondern nur einen sehr geringen Speicherbedarf hat, um die Ansicht der Kamera nicht zu verzieren.

![Benutzerdefinierte Kamera und Mikrofon](images/camera-rig-microphones-300px.png)<br>
*Benutzerdefinierte Kamera und Mikrofon*

In dieser Einrichtung wurde Sound in vier Richtungen vom genauen Speicherort der Kamera aufgezeichnet, sodass wir genügend Informationen zum erneuten Erstellen eines 3D-Informations Panoramas mit räumlichem Sound erhalten, das wir später mit dem 360-Grad-Video synchronisieren konnten.

Eine der Herausforderungen bei der Audiodatei des Kamera Arrays besteht darin, dass Sie die Informationen zum Zeitpunkt der Erfassung kennen. Auch wenn die Video Erfassung in Ordnung ist, kann die Audioerfassung aufgrund von nicht-Kamera-Sounds, wie etwa Sirenen, Flugzeug oder hoher Wind, problematisch werden. Um sicherzustellen, dass wir alle benötigten Elemente haben, haben wir eine Reihe von Stereo-und Mono-Mobil Aufzeichnungs Einheiten verwendet, um asynchrone Ambient-Elemente an bestimmten Punkten an den einzelnen Standorten zu erhalten. Diese Erfassung ist wichtig, da Sie dem Sound-Designer die Möglichkeit bietet, saubere und verwendbare Inhalte zu suchen, die in der Produktionsumgebung verwendet werden können, um Interessen zu erstellen und weitere Direktionalität hinzuzufügen.

Jeder gegebene Erfassungs Tag würde eine große Anzahl von Dateien generieren. Es war wichtig, ein System zu entwickeln, um zu verfolgen, welche Dateien einem bestimmten Speicherort oder einem Kamera-shot entsprechen. Unsere Aufzeichnungseinheit wurde so eingerichtet, dass Dateien automatisch nach Datum und Anzahl von Dateien automatisch benennen, und wir würden Sie am Ende des Tages auf externen Laufwerken sichern. Zumindest war es wichtig, den Anfang der Audioaufzeichnungen zu benennen, da dies eine einfache kontextabhängige Identifizierung der Inhalte ermöglicht, wenn Dateinamen zu einem Problem werden. Außerdem war es wichtig, dass wir die Kamera-Rig-Erfassung visuell manipulieren, da Video und Audiodaten als separates Medium aufgezeichnet und während des Beitrags synchronisiert werden mussten.

### <a name="editing-the-audio"></a>Bearbeiten der Audiodatei

Der erste Schritt bei der Zusammenfassung des Erfassungs Trips besteht darin, die gesamte Audioerfassung für einen Speicherort zu überprüfen, die beste Leistung auszuwählen und alle Highlights zu ermitteln, die während der tions. Anschließend wird das Audiomenü bearbeitet und bereinigt. Beispielsweise kann ein lautes Fahrzeug Horn, das eine Sekunde oder so lange dauert und mehrmals wiederholt wird, ersetzt und in Abschnitte von stillen, Ambient-Audiodaten aus derselben Erfassung eingebunden werden.

Nachdem die Videobearbeitung für einen Speicherort festgelegt wurde, kann der Sound-Designer die entsprechende Audiodatei synchronisieren. An dieser Stelle haben wir sowohl mit der Kamera-als auch mit der Mobile Erfassung gearbeitet, um zu entscheiden, welche Elemente bzw. Kombinationen aus der Erstellung einer immersiven audioszene funktionieren werden. Eine Technik, die wir als nützlich empfunden haben, bestand darin, alle Soundelemente einem Audioeditor hinzuzufügen und schnelle lineare Mock-ups zu erstellen, um mit verschiedenen Mischungs Ideen zu experimentieren. Dies gab uns besser formatierte Ideen, als es Zeit zum Erstellen der eigentlichen holotour-Szenen kam.

### <a name="assembling-the-scene"></a>Zusammenstellen der Szene

Der erste Schritt beim Erstellen einer 3D-Ambient-Szene besteht darin, einen Überblick über allgemeine Hintergrund Umgebungs Schleifen zu schaffen, die andere Features und interaktive Soundelemente in einer Szene unterstützen. Dabei haben wir eine ganzheitliche Herangehensweise an verschiedene Implementierungs Techniken unternommen, die durch die spezifischen Anforderungen und Entwurfskriterien einer bestimmten Szene festgelegt wurden. In manchen Szenen kann die Verwendung der synchronisierten Kamera aufgezeichnet werden, während andere möglicherweise einen stärker aufgebrachten Ansatz benötigen, bei dem eher diskretere Sounds, interaktive Elemente und Musik und Soundeffekte für die mehr filmischen Momentaufnahmen in holotour verwendet werden.

Bei der Indizierung bei der Kamera Erfassung haben wir räumliche, audiofähige Ambient-audioemitter, die den direktionalen Koordinaten der Kameraausrichtung entsprechen, so platziert, dass die Ansicht "Nord Kamera" Audio aus dem Nord Mikrofon und ebenso für die anderen Hauptrichtungen. Diese Emitter sind weltweit gesperrt. Dies bedeutet, dass der Benutzer den Kopf in Bezug auf diese Emitter freischalten kann. der Sound ändert sich entsprechend und modelliert den Sound der Position an diesem Speicherort. Lauschen Sie auf die Piazza Navona oder das Pantheon, um Beispiele für Szenen zu verwenden, die eine gute Kombination aus der Kamera erfassen.

Ein anderer Ansatz besteht darin, ein schleifenes Stereo-Ambiente in Verbindung mit räumlichen audioemittern zu spielen, die in der Szene um ein-ab-Ton spielen, das in Bezug auf Volumen, Tonhöhe und auslöserhäufigkeit zufällig ist. Dadurch wird ein Ambiente mit einem verbesserten Sinn der Direktionalität geschaffen. In Aguas Calientes können Sie beispielsweise überwachen, wie die einzelnen Quadranten des Panoramas bestimmte Emitter haben, die absichtlich bestimmte Bereiche der Geografie hervorheben, aber zusammenarbeiten, um ein allgemeines immersives Ambiente zu schaffen.

## <a name="tips-and-tricks"></a>Tipps und Tricks

Wenn Sie Audio für eine Szene erstellen, gibt es einige zusätzliche Methoden, die Sie verwenden können, um die Direktionalität und das Eintauchen genauer hervorzuheben, wobei die räumlichen Audiofunktionen von hololens vollständig genutzt werden. Wir haben eine Liste mit einigen unten bereitgestellt – lauschen Sie auf diese, wenn Sie das nächste Mal mit holotour versuchen.
* **Ziele suchen**: Dies sind Sounds, die nur dann auslöst, wenn Sie ein bestimmtes Objekt oder einen Bereich des Holographic-Frames betrachten. Wenn Sie z. b. in der Richtung des Straßencafés in der Piazza Navona von Rom suchen, werden die Klänge eines ausgelasteten Restaurants auf eine beliebige Weise angezeigt.
* **Lokale Vision**: Die Tour in holotour enthält bestimmte Beats, bei denen Ihr Einführungs Handbuch, das von holograms unterstützt wird, ein Thema eingehend untersucht. Wenn sich beispielsweise die Fassade des Pantheon auflöst, um den Oculus offenzulegen, wird der Benutzer beim Durchsuchen von Audiodaten, die als 3D-Emitter aus dem Innenbereich der Pantheon platziert werden, dazu ermutigt, das innere Modell zu durchsuchen.
* **Erweiterte Direktionalität**: In vielen Szenen haben wir Klänge auf verschiedene Weise platziert, um der Direktionalität hinzuzufügen. In der Pantheon-Szene wurde z. b. der Sound des Brunnens als separater Emitter in den Benutzer eingefügt, sodass er beim Durchlaufen des Wiedergabe Raums den Eindruck hat, dass es sich um einen Eindruck von ' Sonic Parser ' handelt. In der Welt von Peru, in der sich die einzelnen Datenströme befinden, handelte es sich um einen separaten Emitter, um eine immersive Umgebungsumgebung zu schaffen, die den Benutzer mit den authentischen Tönen dieses Standorts umgibt.
* **Spline-Emitter**: Dieser besondere räumliche audioemitter bewegt sich in 3D-Raum relativ zur visuellen Position des Objekts, mit dem es verbunden ist. Ein Beispiel hierfür war das Training in Machu Picchu, bei dem wir einen Spline-Emitter verwendet haben, um einen eindeutigen Eindruck von Direktionalität und Bewegung zu vermitteln.
* **Musik und SFX**: Bestimmte Aspekte von holotour, die eine stärker stilisierte oder filmische Herangehensweise darstellen, nutzen Musik und Soundeffekte, um die emotionalen Auswirkungen zu erhöhen. Im Gladiator-Kampf am Ende der Rom-Tour wurden besondere Effekte wie z. b. "whooshes" oder "Stingers" verwendet, um die Auswirkung von Bezeichnungen in Szenen zu verstärken.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason syltebo</b><br>Audiodesigner@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Raumklang](spatial-sound.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Raumklang in Unity](spatial-sound-in-unity.md)
* [Räumliche Daten 220](holograms-220.md)
* [Video: Microsoft hololens: Holotour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
