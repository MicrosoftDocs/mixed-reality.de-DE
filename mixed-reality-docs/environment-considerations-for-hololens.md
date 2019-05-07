---
title: Aspekte der Umgebung für HoloLens
description: Rufen Sie die bestmögliche Leistung mit HoloLens, wenn Sie das Gerät für Ihre Augen und die Umgebung optimieren. Sind viele andere Umgebungsfaktoren zusammen zu fused Aktivieren der nachverfolgung, aber als Entwickler Mixed Reality, es gibt mehrere Faktoren Sie berücksichtigen, um ein Speicherplatz für eine bessere Hologramme optimieren beibehalten können.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: holographic Frame, Sichtfeld, Blickfeld, Kalibrierung, Leerzeichen, Umgebung, exemplarische Vorgehensweise
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670171"
---
# <a name="environment-considerations-for-hololens"></a>Aspekte der Umgebung für HoloLens

HoloLens mischt die holographic mit der Außenwelt "echten" Hologramme in Ihrer Umgebung zu platzieren. Ein holographic app-Fenster "hängt" an die Wand, eine holographic Ballerina führt Spin-Vorgänge auf den rackfähige Häschen Ohren befinden sich auf Ihr ahnungslosen Freund Head. Wenn Sie ein immersives Spiel oder eine app verwenden, wird holographic die ganzen Welt verteilt, um Ihre Umgebung zu füllen, aber Sie werden weiterhin in der Lage finden Sie unter, und bewegen den Speicherplatz.

Die Hologramme, die Sie platzieren, bleibt, wo Sie sie erstellt haben, auch wenn Sie Ihr Gerät deaktivieren. 

## <a name="setting-up-an-environment"></a>Das Einrichten einer Umgebung

HoloLens-Geräten wissen, wie Sie stabile und genau Hologramme durch platzieren *nachverfolgung* Benutzer in einem Bereich. Ohne ordnungsgemäße Überwachung versteht das Gerät nicht die Umgebung oder den Benutzer – damit Hologramme in der falschen Stelle angezeigt werden, nicht an derselben Stelle jedes Mal angezeigt oder überhaupt nicht angezeigt werden können.

Verfolgen der Leistung ist stark von der Umgebung, die der Benutzer angehört, und Optimieren eine Umgebung zum Auslösen von stabilen und konsistenten nachverfolgung Wissenschaft, anstatt eine Kunst ist. Sind viele andere Umgebungsfaktoren zusammen zu fused Aktivieren der nachverfolgung, aber als Entwickler Mixed Reality, es gibt mehrere Faktoren Sie berücksichtigen, um ein Leerzeichen zur besseren nachverfolgung optimieren beibehalten können.
 
### <a name="lighting"></a>Beleuchtung
Windows Mixed Reality verwendet visual Licht, um den Standort des Benutzers nachzuverfolgen. Wenn eine Umgebung zu grell ist, können die Kameras ausgelastet abzurufen und "nothing" wird angezeigt. Wenn die Umgebung zu dunkel, die Kameras können nicht genug Informationen übernehmen und "nothing" wird angezeigt. Beleuchtung sollte selbst und in ausreichendem Maße hellen sein, dass eine Person ohne Aufwand, aber nicht so hell sehen kann, dass das Licht betrachten ist.

Bereiche vorliegen Fehlerquellen helles Licht in einem allgemeinen dim Bereich sind ebenfalls problematisch, da die Kamera verfügt, um anzupassen, beim Verschieben von ein-und der hellen Leerzeichen. Dadurch kann das Gerät "get-verloren" und stellen Sie sich, die eine Änderung der Position die Änderung in der Licht entspricht. Stabile Lichtintensität in einem Bereich führt zu besseren nachverfolgung.

Alle Außenbeleuchtung kann auch in Tracker Instabilität verursachen, wie die Sonne im Laufe der Zeit erheblich variieren kann. Überwachung in den gleichen Platz im Sommer im Vergleich zu Winter kann z. B. deutlich unterschiedliche Ergebnisse erzeugen, außerhalb der secondhand Licht zu unterschiedlichen Zeiten des Jahres höher sein.

Wenn Sie eine Luxmeter verfügen, ist eine stetige 500-1000 Lux ein guter Ausgangspunkt. 

#### <a name="types-of-lighting"></a>Typen von Beleuchtung
Verschiedene Arten von Licht in einem Bereich können auch beeinflussen, nachverfolgen. Glühbirnen IWV (Puls) mit der AC Strom durch – ausgeführt wird, wenn die AC Häufigkeit 50 Hz ist, und klicken Sie dann das Licht bei 50 Hz fortbewegt. Für einen Menschen ist diese zeitverzerrten nicht bemerkt. Allerdings HoloLens 30 BpS Kamera erkennt diese Änderungen – einige Frames werden ausgewogene, einige mangelhaft leuchtet und einige übermäßig zur Verfügung gestellt, wie die Kamera versucht wird, um helle Schritten zu kompensieren.

In den USA wird der Strom Häufigkeit standard 60Hz daher Lightbulb Schritten mit HoloLens' Framerate abgestimmt sind – 60Hz-Schritten, die mit Hololens 30 FPS Framerate ausrichten. Allerdings haben viele Länder einen AC Häufigkeit Standard von 50Hz, d. h. einige Frames Hololens während Schritten ausgeführt werden, und andere hingegen nicht. Insbesondere ist hohe Beleuchtung in "Europa" bekannt, dass die Probleme verursachen. 

Es gibt einige Dinge, die Sie ausprobieren können, um Flimmern Probleme zu beheben. Temperatur, Bulb Alter und Aufwärmphase Zyklen werden häufige Ursachen für hohe Flimmern, und Ersetzen von Glühbirnen kann hilfreich sein. Glühbirnen verschärft und sicherstellen, dass die aktuelle zeichnet konstant sind, können auch. 

### <a name="items-in-a-space"></a>Elemente in einem Bereich
HoloLens verwendet eindeutige environmental Orientierungspunkte im Gelände, auch bekannt als *Features*, um sich selbst in einem Bereich zu suchen. 

Ein Gerät kann fast nie in einem Bereich Feature-schlecht nachverfolgen, wie das Gerät keine Möglichkeit festzustellen hat, in dem im Raum ist es. Hinzufügen von Funktionen, das die Wände eines Leerzeichens ist in der Regel eine gute Möglichkeit, um die nachverfolgung zu verbessern. Poster, geklebt Symbole an einer Wand, Werke, eindeutige Objekte oder anderen ähnlichen Elementen gesamte Hilfe. Eine unübersichtliche – ist ein gutes Beispiel einer Umgebung, die auf gute Überwachung führt – es gibt viele verschiedene Funktionen in einem einzelnen Bereich. 

Verwenden Sie außerdem einzigartige Funktionen im selben Raum. Dasselbe Poster wird mehrere Male wiederholt, über eine Wand, wird z. B. Gerät Verwirrung sorgen, wie die HoloLens die wiederholten Poster kennen wird nicht auf sucht. Eine allgemeine Möglichkeit einzigartigen Features hinzufügen ist die Verwendung von Codezeilen Maskierung Band eindeutig ist, erstellen Nonrepetitve Muster entlang der Wände und der niedrigste Wert der ein Leerzeichen. 

Eine gute Frage sich Fragen ist – Wenn Sie nur eine kleine Menge der Szene, gesehen haben Sie sich im Bereich eindeutig gefunden? Wenn dies nicht der Fall ist, ist es wahrscheinlich das Gerät Probleme nachverfolgen sowie hat.

#### <a name="wormholes"></a>Wurmlöcher
Wenn Sie haben zwei Bereiche oder Bereiche, die gleich aussehen, eventuell die nachverfolgung der Meinung, dass sie identisch sind. Dies führt zu dem Gerät Konten selbst vorzutäuschen, es ist an anderer Stelle. Wir bezeichnen diese Art von wiederholten Bereiche *Wurmlöcher*. 

Um Wurmlöcher zu verhindern, versuchen Sie, zu verhindern, dass identische Bereichen im selben Raum. Identische Bereiche können manchmal Factory Stationen Windows in einem Gebäude, Server-Racks oder Arbeitsstationen enthalten. Kennzeichnung von Bereichen oder zum Hinzufügen von einzigartigen Features auf einzelnen ähnliche Bereiche können dabei, Wurmlöcher zu verringern.
 
### <a name="temporal-stability-of-a-space"></a>Temporale Stabilität eines Leerzeichens
Wenn Ihre Umgebung ständig Verschiebung geändert und ist, hat das Gerät keine stabile Funktionen für gefunden. 

Mehr bewegliche Objekte in einem Bereich, einschließlich Menschen, desto einfacher ist Überwachung verloren gehen. Verschieben von Fließbändern, Elemente in unterschiedlichen Zustände des Konstruktion und viele Leute, die in einem Bereich wurden alle als nachverfolgung Probleme verursachen.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Elemente im Bereich der Nähe des Benutzers
Abmüht auf ähnliche Weise wie die Menschen auf Objekte in der Nähe der Augen konzentrieren können nicht, HoloLens, wenn Objekte in der Nähe der Kameras sind durchläuft. Wenn ein Objekt ist auch in der Nähe mit beiden Kameras angezeigt werden, oder wenn ein Objekt eine Kamera blockiert wird, das Gerät wesentlich mehr Probleme bei der nachverfolgung für das Objekt müssen. 

Die Kameras können nicht näher als 15 cm aus einem Objekt anzeigen.
 
### <a name="surfaces-in-a-space"></a>Oberflächen in einem Bereich
Stark reflektierende Flächen wahrscheinlich sucht je nach den Winkel die nachverfolgung beeinflusst. Stellen Sie sich ein völlig neues Auto - zurückwirft Sie dazu bewegen, und sehen Sie verschiedene Objekte in der Oberfläche, wie Sie verschieben. Die nachverfolgung die verschiedenen Objekte, der in der Entwurfsoberfläche darstellen eine sich ändernde Umgebung übernommen und das Gerät verliert, nachverfolgung.

Weniger beleuchtete Objekte sind einfacher mit verfolgen können.

### <a name="wifi-fingerprint-considerations"></a>Überlegungen zur WiFi-Fingerabdruck
Solange WiFi aktiviert ist, werden Sitemap-Daten mit einem Fingerabdruck WiFi korreliert werden, auch wenn nicht mit einem tatsächlichen WiFi-Netzwerk/Router verbunden. Ohne WiFi-Informationen können der Speicherplatz und der Hologramme zur Erkennung von etwas langsamer sein. Wenn die WLAN-Signalen erheblich ändern, denken, dass sie einen anderen Bereich vollständig ist das Gerät auf.

Netzwerk-ID (d. h. SSID, MAC-Adresse) wird nicht an Microsoft gesendet, und alle Verweise werden lokalen gespeichert, auf die HoloLens WiFi.

## <a name="mapping-new-spaces"></a>Zuordnen von neuen Leerzeichen
Wenn Sie geben Sie einen neuen Space (oder eine vorhandene laden), sehen Sie eine Verteilung über den Raum Mesh-Grafik. Das bedeutet, dass Ihr Gerät [zuordnen Ihrer Umgebung](spatial-mapping-design.md). 

Wenn Sie Hologramme platzieren Probleme auftreten, versuchen Sie es rund um den Speicherplatz durchlaufen werden, damit HoloLens es genauer zugeordnet werden können. 

Wenn Ihre HoloLens der Speicherplatz nicht zugeordnet werden, oder außerhalb des gültigen Kalibrierung liegt, können Sie eingeschränkten Modus eingeben. Im eingeschränkten Modus wird nicht Sie Hologramme in Ihrer Umgebung platzieren können.

## <a name="environment-management"></a>Umgebungsverwaltung
Es gibt zwei Einstellungen, die Benutzer zum "bereinigen" ermöglichen Hologramme und Ursache HoloLens "ein Leerzeichen vergessen".  Sie existieren unter "Hologramme und Umgebungen" in der Einstellungsapp mit der zweiten Einstellung auch unter "Datenschutz" in der einstellungs-app angezeigt werden.

1.  Löschen in der Nähe Hologramme: Wenn Sie diese Einstellung auswählen, HoloLens löscht alle verankerten Hologramme und alle gespeicherten Kartendaten für die "aktuelle Adressraum" auf dem sich das Gerät befindet.  Ein neuer Abschnitt für die Zuordnung wird erstellt und in der Datenbank für den betreffenden Speicherort gespeichert werden, sobald Hologramme erneut im gleichen Raum befinden werden.

2.  Löschen alle Hologramme: Wenn Sie diese Einstellung auswählen, HoloLens, werden alle Zuordnungsdaten gelöscht, und verankert Hologramme in den gesamten Datenbanken, der Leerzeichen.  Werden keine Hologramme erneut ermittelt werden, und alle Hologramme müssen neu platziert werden, um die Map-Abschnitte in der Datenbank zu speichern.

### <a name="managing-your-spaces"></a>Verwalten Ihre Leerzeichen

Die Map-Abschnitte und die verschiedenen Bereiche müssen in eine einzelne Datenbank lokal gespeichert, auf dem Gerät HoloLens reduziert wurde. Die Datenbank wird sicher gespeichert, mit Zugriff ist nur verfügbar, das interne System und nie zu einem Benutzer des Geräts, auch wenn mit einem PC verbunden bzw. mithilfe der Datei-Explorer-app. Wenn Bitlocker aktiviert ist, werden die der gespeicherten Zuordnungsdaten ebenfalls verschlüsselt.

Wenn Hologramme an verschiedenen Standorten ohne geballten Pfad zwischen den Standorten-Hologramme platziert werden, sind mehrere Map-Komponenten vorhanden.  In diesem Abschnitt der Karte verankert Hologramme gelten als "in Ihrer Nähe" im aktuellen Bereich.

Es ist eine Entwickler-API, um eine kleine Teilmenge der "aktuelle Adressraum" zu exportieren (ein Teil der Map-Komponente, die aktuell erkannt wird) um freigegebenen – Hologramm Szenarien zu ermöglichen.  Es ist derzeit keinen Mechanismus zum Herunterladen von der gesamten Datenbank aller Arbeitsbereiche, die zugeordnet wurden.


## <a name="hologram-quality"></a>– Hologramm Qualität

Hologramme platziert werden können, in der gesamten Umgebung – hoch, Niedrig, und für Sie – aber sehen Sie ihn durch einen [holographic Frame](holographic-frame.md) , die sich vor Ihren Augen befindet. Um die beste Darstellung erhalten zu können, müssen Sie Ihr Gerät anpassen, damit Sie, den gesamten Rahmen sehen können zur Verfügung. Und dann Ihrer Umgebung, und untersuchen zögern Sie nicht!

Für Ihre [Hologramme](hologram.md) um gestochen scharfe, klar und stabil zu suchen, Ihre HoloLens, die nur für Sie kalibriert werden muss. Wenn Sie zuerst Ihre HoloLens eingerichtet haben, werden Sie durch diesen Vorgang geführt. Wenn Hologramme nicht angezeigt ordnungsgemäß, oder Sie viele Fehler sehen, können Sie später Anpassungen vornehmen.

### <a name="calibration"></a>Kalibrierung

Wenn Ihre Hologramme, ganz nervös oder Verwackelte suchen, oder wenn Sie Hologramme platzieren Probleme auftreten, versuchen Sie es zunächst den [Kalibrierung app](calibration.md). Diese app kann auch helfen, wenn Sie angefasst auftreten, bei der Verwendung Ihrer HoloLens.

Um die Kalibrierung-app zu erhalten, wechseln Sie zu Einstellungen > System > Dienstprogramme. Wählen Sie öffnen Kalibrierung, und befolgen Sie die Anweisungen.

Wenn Sie die Kalibrierung-app ausführen und immer noch Probleme mit – Hologramm Qualität, oder Sie eine häufige "tracking verloren"-Meldung wird angezeigt, versuchen Sie es der app-Sensor zu optimieren. Wechseln Sie zu Einstellungen > System > Dienstprogramme, wählen Sie die Open-Sensor-Optimierung, und befolgen Sie die Anweisungen.

Wenn eine andere Person ist Ihre HoloLens verwenden möchten, sollten Kalibrierung Ausführen der app zunächst damit das Gerät für sie ordnungsgemäß eingerichtet ist.

## <a name="see-also"></a>Siehe auch
* [Gestaltung von räumlicher Abbildung](spatial-mapping-design.md)
* [Holograms](hologram.md)
* [Kalibrierung](calibration.md)
