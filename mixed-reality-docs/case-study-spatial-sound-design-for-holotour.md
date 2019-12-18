---
title: 'Fallstudie: räumliches Sound Design für holotour'
description: Zum Erstellen einer wahrhaft immersiven 3D-Tour für Microsoft hololens sind die Panorama Videos und Holographic-Kulissen nur Teil der Formel.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, holotour, räumlicher Sound, Fallstudie
ms.openlocfilehash: f2dd704089d9c76b7ba175a4a1ad5cebf9ec6c68
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181925"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Fallstudie: räumliches Sound Design für holotour

Panorama-Videos und holografische Szenen sind nur ein Teil der Formel für eine wirklich immersive virtuelle Microsoft hololens-Tour. In diesem Artikel wird beschrieben, wie Sound verwendet wurde, um zu sehen, wie Sie sich tatsächlich an jedem holotour-Standort befinden.

## <a name="the-tech"></a>Die Technologie

Die wunderbare Darstellung und Holographic Szenen, die in holotour angezeigt werden, sind nur ein Teil der glaubwürdigen gemischten Realität. Obwohl holograms nur visuell vor einem Benutzer angezeigt werden können, bietet der [räumliche Ton](spatial-sound.md) , der hololens von allen Richtungen liefert, eine vollständigere sensoringdarstellung.

Räumlicher Sound stellt Hinweise bereit, mit denen eine Richtung angezeigt wird, die der Benutzer einschalten sollte, oder um dem Benutzer mitzuteilen, dass im Speicherplatz mehr holograms vorhanden sind. Wir können einem – Hologramm auch einen Sound direkt anfügen und kontinuierlich die Richtung und Entfernung des holograms vom Benutzer aktualisieren. Diese Technik ist so, als ob der Sound direkt aus diesem Objekt stammt.

Für holotour wollten wir die räumlichen Audiofunktionen von hololens nutzen, um eine Umgebung mit 360-Grad-Umgebung zu erstellen, die mit dem Video synchronisiert wird, um die Highlights der einzelnen Orte zu verdeutlichen.

## <a name="behind-the-scenes"></a>Im Hintergrund

Wir haben holotour-Erfahrungen von zwei verschiedenen Standorten erstellt: Rom und Machu Picchu. Um diese Touren authentisch und aussagekräftigen zu gestalten, wollten wir Audio von den Standorten erfassen, an denen wir gedreht haben, statt generische Sounds zu verwenden.

### <a name="capture-the-audio"></a>Audioerfassung

In unserer [Fallstudie zur Erfassung des visuellen Inhalts für holotour](case-study-capturing-and-creating-content-for-holotour.md)wird das Design des Kamera-Rig erläutert. Es umfasste 14 GoPro-Kameras in einem 3D-gedruckten Gehäuse, das auf das Stativ zugeschnitten ist. Zum Erfassen von Audiodaten haben wir unter den Kameras ein vier-Mikrofon-Array hinzugefügt. Der Sound wurde in eine kompakte vier-Kanal-Aufzeichnungseinheit an der Basis des mums eingespeist. Wir haben das Mikrofon ausgewählt, das gut verlief, aber klein genug war, um das stören der Kameras zu vermeiden.

![benutzerdefinierte Kamera und Mikrofon](images/camera-rig-microphones-300px.png)<br>
*Benutzerdefinierte Kamera und Mikrofon*

Dieses Setup erfasst Sound in vier Richtungen. Wir haben genügend Informationen zum erneuten Erstellen eines 3D-Audiowiedergabe-Panoramas aus räumlichem Sound aufgezeichnet, das wir später mit dem 360-Grad-Video synchronisieren konnten.

Eine Herausforderung der Kamera-Array-Audiodatei besteht darin, dass Sie vor Kamera Geräuschen, wie etwa Sirenen, Flugzeug oder hoher Wind, sind. Um sicherzustellen, dass alle benötigten Soundelemente verwendet werden, haben wir auch Stereo-und Mono-Mobile Recorder verwendet, um den asynchronen Ambient-Sound an bestimmten Punkten an den einzelnen Standorten zu erfassen. Diese Aufzeichnungen sorgen dafür, dass der Sound-Designer Inhalte bereinigt und die Direktionalität in der Postproduktion verbessern könnte.

An jedem Erfassungs Tag werden viele Dateien generiert. Daher war es wichtig, ein System zu entwickeln, um zu verfolgen, welche Dateien einem bestimmten Ort oder einer Kamera entsprechen. Unsere Aufzeichnungseinheit wurde so eingerichtet, dass Dateien automatisch nach Datum und "Take"-Nummer benennen. Am Ende eines Tages haben wir Dateien auf externen Laufwerken gesichert. Wir haben auch festgestellt, dass es wichtig ist, den Anfang der Audioaufzeichnungen verbal zu Slate. Diese Vorsichtsmaßnahme ermöglicht eine einfache kontextabhängige Identifizierung des Inhalts, wenn Probleme mit dem Dateinamen auftreten. Außerdem war es wichtig, die Kamera Erfassung visuell zu manipulieren, da Video und Audiodaten als separates Medium aufgezeichnet waren und während der Postproduktion synchronisiert werden mussten.

### <a name="edit-the-audio"></a>Audiodatei bearbeiten

Nach dem Erfassungs Trip wird der erste Schritt bei der Zusammenführung eines direktionalen und immersiven Audiowiedergabe-Erlebnisses darin besteht, alle Audiodaten zu überprüfen, die für einen Speicherort aufgezeichnet wurden. Wir wählen das Beste aus und identifizieren Highlights, die während der Integration angewendet werden können. Anschließend wird das Audiomenü bearbeitet und bereinigt. Beispielsweise kann ein Fahrzeug Strahl, der eine Sekunde oder so lange dauert und mehrmals wiederholt wird, durch eine ruhigere Umgebungs Audiodaten aus derselben Erfassungs Sitzung ersetzt werden.

Nachdem die Videobearbeitung für einen Speicherort festgelegt wurde, kann der Sound-Designer die entsprechende Audiodatei synchronisieren. An diesem Punkt bewerten wir sowohl das Kamera-Rig-als auch das Mobile Sound Erfassungen, um zu entscheiden, welche Elemente zum Erstellen einer immersiven audioszene funktionieren würden. Wir haben festgestellt, dass es sinnvoll ist, alle Soundelemente in einem Audioeditor zu platzieren und schnelle lineare Mock-ups zu erstellen, um mit verschiedenen Mischungs Ideen zu experimentieren. In diesem Schritt haben wir besser formatierte Ideen für den Zeitpunkt der Erstellung der eigentlichen holotour-Szenen gegeben.

### <a name="assemble-the-scene"></a>Szene zusammenstellen

Der erste Schritt beim Erstellen einer 3D-Ambient-Szene besteht darin, einen Überblick über allgemeine Hintergrund Umgebungs Schleifen zu schaffen, die andere Features und interaktive Soundelemente in einer Szene unterstützen. Wir verwenden einen ganzheitlichen Ansatz für die Implementierung, der durch die Entwurfskriterien für eine bestimmte Szene festgelegt wird. Einige Szenen können mit der Synchronisierung der synchronisierten Kamera in den Index aufgenommen werden Weitere "filmische" Momente erfordern möglicherweise einen zusammengestellten Ansatz, der auf diskreten Sounds, interaktiven Elementen und Musik basiert.

Bei der Indizierung bei der Kamera: Wir haben die Audio-audioemitter mit räumlichem Sound ermöglicht, die der direktionalen Ausrichtung der Kameras entsprach. In der Ansicht Nord Kamera werden Audiodaten aus dem Nord Mikrofon und auch für die anderen Hauptrichtungen abgespielt. Diese Emitter sind weltweit gesperrt. Dies bedeutet, dass sich der Sound ändert, wenn der Benutzer seine Kopfzeile zu diesen wechselt. Diese Technik modelliert den Sound der Position an diesem Speicherort. Lauschen Sie auf die Piazza Navona oder das Pantheon, um Beispiele für Szenen zu verwenden, die eine gute Mischung aus Kamera erfasster Audiodaten verwenden.

Bei einem anderen Ansatz spielen wir in manchen Fällen in Kombination mit räumlichen audioemittoren, die in der Szene platziert werden, Schleifen Stereo-Ambiente. Diese Emitter spielen einen einmaligen Sound von zufällisierter Menge, Tonhöhe und Auslöse Häufigkeit. Mit dieser Technik wird ein Ambiente erstellt, das einen verbesserten Sinn der Direktionalität hat. In der Aguas-Umgebung können Sie z. b. hören, wie jeder Quadrant des Panoramas bestimmte Emitter hat, die bestimmte Bereiche der geography hervorheben, aber zusammenarbeiten, um ein allgemeines, immersives Ambiente zu schaffen.

## <a name="tips-and-tricks"></a>Tipps und Tricks

Es gibt einige zusätzliche Möglichkeiten, die Direktionalität hervorzuheben und das Eintauchen zu verbessern, um die räumlichen Audiofunktionen von hololens vollständig nutzen zu können. Wir haben hier eine Liste bereitgestellt. Lauschen Sie auf diese Auswirkungen beim nächsten Versuch von holotour.
* **Ziele suchen:** Diese Sounds werden ausgelöst, wenn Sie ein bestimmtes Objekt oder einen Bereich des Holographic-Frames betrachten. Sehen Sie sich z. b. das Street-Side-Café in der Piazza Navona von Rom an, um stark ausgelastete Sounds zu initiieren.
* **Lokale Vision:** Die Reise durch holotour enthält bestimmte "Beats", bei denen Ihr Einführungs Handbuch, das von holograms unterstützt wird, ein Thema ausführlich untersucht. Wenn sich beispielsweise die Fassade des Pantheon auflöst, um den Oculus offenzulegen, wird der Benutzer beim Durchsuchen von Audiodaten, die als 3D-Emitter aus dem Pantheon platziert wurden, dazu ermutigt, das Innere zu durchsuchen.
* **Erweiterte Direktionalität:** In vielen Szenen haben wir Klänge auf verschiedene Weise platziert, um der Direktionalität hinzuzufügen. In der Pantheon-Szene wurde z. b. der Sound des Brunnens als separater Emitter für den Benutzer so nah platziert, dass er den Eindruck hat, dass er "sonstiger" ist, während er den Wiedergabe Bereich durchläuft. In der Welt von Peru von Peru waren die Klänge einzelner kleiner Streams als separate Emitter, um eine immersive Umgebungsumgebung zu schaffen, die den Benutzer mit den authentischen Tönen dieses Orts umgibt.
* **Spline-Emitter:** Diese Emitter bewegen sich in 3D-Raum relativ zur visuellen Position des Objekts, an das Sie angefügt sind. Ein Beispiel hierfür ist das Training in Machu Picchu, bei dem wir einen Spline-Emitter verwendet haben, um einen unterschiedlichen Sinn von Direktionalität und Bewegung zu vermitteln.
* **Musik und SFX:** Bestimmte Aspekte von holotour, die eine stärker stilisierte oder filmische Herangehensweise darstellen, nutzen Musik und Soundeffekte, um die emotionalen Auswirkungen zu erhöhen. Im gladiatorkampf am Ende der Rom-Tour können z. b. besondere Effekte wie z. b. "whooshes" und "Stingers" die Auswirkung von Bezeichnungen in den Kulissen stärken.

## <a name="see-also"></a>Weitere Informationen:
* [Raumklang](spatial-sound.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Raumklang in Unity](spatial-sound-in-unity.md)
* [Video: Microsoft hololens: holotour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
