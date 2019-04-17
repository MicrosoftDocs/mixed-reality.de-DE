---
title: Aspekte der Umgebung für HoloLens
description: Rufen Sie die bestmögliche Leistung mit HoloLens, wenn Sie das Gerät für Ihre Augen und die Umgebung optimieren.
author: thetuvix
ms.author: msamples
ms.date: 02/24/2019
ms.topic: article
keywords: holographic Frame, Sichtfeld, Blickfeld, Kalibrierung, Leerzeichen, Umgebung, exemplarische Vorgehensweise
ms.openlocfilehash: d5433dc923aeb70e3ae82e75c9358d3a569e8f83
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594830"
---
# <a name="environment-considerations-for-hololens"></a>Aspekte der Umgebung für HoloLens

HoloLens mischt die holographic mit der Außenwelt "echten" Hologramme in Ihrer Umgebung zu platzieren. Ein holographic app-Fenster "hängt" an die Wand, eine holographic Ballerina führt Spin-Vorgänge auf den rackfähige Häschen Ohren befinden sich auf Ihr ahnungslosen Freund Head. Wenn Sie ein immersives Spiel oder eine app verwenden, wird holographic die ganzen Welt verteilt, um Ihre Umgebung zu füllen, aber Sie werden weiterhin in der Lage finden Sie unter, und bewegen den Speicherplatz.

Die Hologramme, die Sie platzieren, bleibt, wo Sie sie erstellt haben, auch wenn Sie Ihr Gerät deaktivieren. 

Hier sind einige Dinge zu bedenken für optimale Ergebnisse mit der holographic Welt. Beachten Sie, dass HoloLens soll in einem abgesicherten Bereich mit keine tripping Gefahren in geschlossener Umgebung verwendet werden. Verwenden sie nicht beim einbringen oder Ausführen von anderen Aktivitäten, die Ihre volle Aufmerksamkeit erfordern.

## <a name="spaces"></a>Leerzeichen

HoloLens erfährt der Speicherplatz aus, damit sie wissen, wo Sie platziert haben Hologramme. HoloLens merken kann mehrere Leerzeichen, und wurde entwickelt, um den richtigen Platz zu laden, wenn Sie es aktivieren.

### <a name="setting-up"></a>Einrichten

HoloLens können zuordnen, und speichern Ihre Leerzeichen am besten bei der Auswahl der richtigen Umgebung.
* Verwenden Sie einen Raum mit ausreichend Licht und ausreichend Platz ein. Vermeiden Sie dunkel Leerzeichen und Räume mit einer Vielzahl von dunkel, shiny oder lichtdurchlässiger Oberflächen (z.B. Spiegel oder thin Tiefe).
* Wenn Sie die HoloLens, um ein Leerzeichen erfahren möchten, nichts vor direkt aus ungefähr einem Messgerät entfernt.
* Vermeiden Sie die Leerzeichen durch viele Objekte zu verschieben. Wenn ein Element verschoben wurde und HoloLens sich seiner neue Position angezeigt werden sollen (z. B. Sie verschoben Kaffee Tabelle um eine neue Stelle), bestaunen und verschieben Sie es.

### <a name="spatial-mapping"></a>Räumliche Zuordnung

Wenn Sie geben Sie einen neuen Space (oder eine vorhandene laden), sehen Sie eine Verteilung über den Raum Mesh-Grafik. Das bedeutet, dass Ihr Gerät [zuordnen Ihrer Umgebung](spatial-mapping-design.md). Wenn Sie Hologramme platzieren Probleme auftreten, versuchen Sie es rund um den Speicherplatz durchlaufen werden, damit HoloLens es genauer zugeordnet werden können. Wenn Ihre HoloLens der Speicherplatz nicht zugeordnet werden, oder außerhalb des gültigen Kalibrierung liegt, können Sie eingeschränkten Modus eingeben. Im eingeschränkten Modus wird nicht Sie Hologramme in Ihrer Umgebung platzieren können.

### <a name="managing-your-spaces"></a>Verwalten Ihre Leerzeichen

Die Map-Abschnitte und die verschiedenen Bereiche müssen in eine einzelne Datenbank lokal gespeichert, auf dem Gerät HoloLens reduziert wurde.  Die Datenbank wird sicher gespeichert, mit Zugriff ist nur verfügbar, das interne System und nie zu einem Benutzer des Geräts, auch wenn mit einem PC verbunden bzw. mithilfe der Datei-Explorer-app.  Wenn Bitlocker aktiviert ist, werden die der gespeicherten Zuordnungsdaten ebenfalls verschlüsselt.
Wenn Hologramme an verschiedenen Standorten ohne geballten Pfad zwischen den Standorten-Hologramme platziert werden, sind mehrere Map-Komponenten vorhanden.  Hologramme, die in diesem Abschnitt der Karte verankert sind eine Entwickler-API, um eine kleine Teilmenge der "aktuelle Adressraum" zu exportieren ist als "in Ihrer Nähe" im aktuellen Bereich vorhanden sein (ein Teil der Map-Komponente, die aktuell erkannt wird) um freigegebenen – Hologramm Szenarien zu ermöglichen.  Es ist derzeit keinen Mechanismus zum Herunterladen von der gesamten Datenbank aller Arbeitsbereiche, die zugeordnet wurden.

#### <a name="wifi"></a>WLAN
Verbundene Visual Studio. Nicht – solange WiFi aktiviert ist, werden Sitemap-Daten mit einem Fingerabdruck WiFi korreliert werden, auch wenn nicht mit einem tatsächlichen WiFi-Netzwerk/Router verbunden.  Dies ist, da die MAC-Adresse und Signal Stärke (d. h. WiFi-Fingerabdruck) einen Router verfügbar ist, ohne eine Verbindung hergestellt wird.  Netzwerk-ID (d. h. SSID, MAC-Adresse) wird nicht an Microsoft gesendet, und alle Verweise werden lokalen gespeichert, auf die HoloLens WiFi.

Aktiviert im Vergleich zu Deaktiviert – wird HoloLens, erkennen und Leerzeichen Denken Sie daran, auch wenn WiFi deaktiviert ist, durch das sichere Speichern der Daten von triebwerksensoren Hologramme platziert werden.  Ohne die WiFi-Informationen die Leerzeichen und Hologramme möglicherweise etwas vermindert, zu einem späteren Zeitpunkt, zu erkennen, wie nötig ab, die HoloLens, aktive Überprüfungen auf alle – Hologramm Anker und Map-Abschnitte, die auf dem Gerät gespeichert werden, um die "im rechten Teil der Zuordnung relocalize" verglichen werden soll.

#### <a name="environment-management"></a>Umgebungsverwaltung
Es gibt 2 Einstellungen, die Benutzer zum "bereinigen" aktivieren-Hologramme und Ursache HoloLens "ein Leerzeichen vergessen".  Sie existieren unter "Hologramme und Umgebungen" in der Einstellungsapp mit der zweiten Einstellung auch unter "Datenschutz" in der einstellungs-app angezeigt werden.
1.  Löschen in der Nähe Hologramme: Wenn Sie diese Einstellung auswählen, HoloLens löscht alle verankerten Hologramme und alle gespeicherten Kartendaten für die "aktuelle Adressraum" auf dem sich das Gerät befindet.  Ein neuer Abschnitt für die Zuordnung wird erstellt und in der Datenbank für den betreffenden Speicherort gespeichert werden, sobald Hologramme erneut im gleichen Raum befinden werden.
2.  Löschen alle Hologramme: Wenn Sie diese Einstellung auswählen, HoloLens, werden alle Zuordnungsdaten gelöscht, und verankert Hologramme in den gesamten Datenbanken, der Leerzeichen.  Werden keine Hologramme erneut ermittelt werden, und alle Hologramme müssen neu platziert werden, um die Map-Abschnitte in der Datenbank zu speichern.


## <a name="hologram-quality"></a>– Hologramm Qualität

Hologramme platziert werden können, in der gesamten Umgebung – hoch, Niedrig, und für Sie – aber sehen Sie ihn durch einen [holographic Frame](holographic-frame.md) , die sich vor Ihren Augen befindet. Um die beste Darstellung erhalten zu können, müssen Sie Ihr Gerät anpassen, damit Sie, den gesamten Rahmen sehen können zur Verfügung. Und dann Ihrer Umgebung, und untersuchen zögern Sie nicht!

Für Ihre [Hologramme](hologram.md) um gestochen scharfe, klar und stabil zu suchen, Ihre HoloLens, die nur für Sie kalibriert werden muss. Wenn Sie zuerst Ihre HoloLens eingerichtet haben, werden Sie durch diesen Vorgang geführt. Wenn Hologramme nicht angezeigt ordnungsgemäß, oder Sie viele Fehler sehen, können Sie später Anpassungen vornehmen.

### <a name="calibration"></a>Kalibrierung

Wenn Ihre Hologramme, ganz nervös oder Verwackelte suchen, oder wenn Sie Hologramme platzieren Probleme auftreten, versuchen Sie es zunächst den [Kalibrierung app](calibration.md). Diese app kann auch helfen, wenn Sie angefasst auftreten, bei der Verwendung Ihrer HoloLens.

Um die Kalibrierung-app zu erhalten, wechseln Sie zu Einstellungen > System > Dienstprogramme. Wählen Sie öffnen Kalibrierung, und befolgen Sie die Anweisungen.

Wenn Sie die Kalibrierung-app ausführen und immer noch Probleme mit – Hologramm Qualität, oder Sie eine häufige "tracking verloren"-Meldung wird angezeigt, versuchen Sie es der app-Sensor zu optimieren. Wechseln Sie zu Einstellungen > System > Dienstprogramme, wählen Sie die Open-Sensor-Optimierung, und befolgen Sie die Anweisungen.

Wenn eine andere Person ist Ihre HoloLens verwenden möchten, sollten Kalibrierung Ausführen der app zunächst damit das Gerät für sie ordnungsgemäß eingerichtet ist.

## <a name="see-also"></a>Siehe auch
* [Räumliche Zuordnung entwerfen](spatial-mapping-design.md)
* [Holograms](hologram.md)
* [Kalibrierung](calibration.md)
