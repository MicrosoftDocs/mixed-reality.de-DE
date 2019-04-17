---
title: Die Überprüfung Visualisierung Platz
description: Anwendungen, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Design, HoloLens, Raum Scan, räumliche Zuordnung Wiederaufbau, surface mesh
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604645"
---
# <a name="room-scan-visualization"></a>Die Überprüfung Visualisierung Platz

Anwendungen, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv. Der Vollständigkeit und die Qualität der Daten hängt von einer Reihe von Faktoren wie der Menge der, die der Benutzer ausgeführt hat, wie viel Zeit verstrichen ist, da die Auswertung und gibt an, ob die Objekte, z. B. Möbel und Türen verschoben haben, da das Gerät über den Bereich überprüft.

Um nützliche räumliche Zuordnungsdaten zu gewährleisten, haben Anwendungsentwickler für mehrere Optionen:
* Abhängig, was bereits gesammelt wurden. Diese Daten können ursprünglich unvollständig sein.
* Bitten Sie den Benutzer mit, dass die Bewegung Bloom lernen Sie die Windows Mixed Reality-home und sehen Sie sich dann den Bereich, die, den Sie für die Umgebung verwenden möchten. Sie können die tippbewegung verwenden, um sicherzustellen, dass alle erforderlichen Bereich, auf dem Gerät bekannt ist.
* Erstellen Sie eine benutzerdefinierte Auswertung Erfahrung in seiner eigenen Anwendung.

Beachten Sie, dass in all diesen Fällen die tatsächlichen Daten, die während der Auswertung durch das System gespeichert ist und die Anwendung nicht dazu muss.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Die Überprüfung Visualisierung Platz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Erstellen eine benutzerdefinierte Überprüfung Erfahrung

Anwendungen können auf den analizar los datos räumliche Zuordnung zu Beginn der Umgebung zu beurteilen, ob sie möchten, dass die Benutzer auf die zusätzlichen Schritte ausführen, um die Vollständigkeit und Qualität zu verbessern. Wenn Analysen weisen darauf hin, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung für die Überlagerung auf der ganzen Welt an bereitstellen:
* Wie viel von der Gesamtgröße des Datenträgers in der Nähe der Benutzer muss in der Umgebung sein.
* In denen der Benutzer zur Verbesserung der Daten gespeichert werden sollen

Benutzer ist nicht bekannt macht eine Überprüfung "good". Sie müssen angezeigt werden oder usw. mitgeteilt, wonach gesucht werden soll, wenn sie aufgefordert werden, einen Scan – Flachheit, Entfernung von der tatsächlichen Wände, ausgewertet. Der Entwickler muss eine Feedbackschleife implementieren, die enthält, die räumliche Zuordnung datenaktualisierung während der Phase Scannen oder durchsuchen.

In vielen Fällen ist es möglicherweise am besten, die dem Benutzer mitzuteilen, was sie (z. B. die Obergrenze suchen hinter Möbel ansehen), um die Überprüfung der erforderlichen Qualität zu erhalten.

## <a name="cached-versus-continuous-spatial-mapping"></a>Zwischenspeicherung im Vergleich zu fortlaufenden räumliche Zuordnung

Die Daten für die räumliche Zuordnung ist die am häufigsten hohes Gewicht, Data Source-Anwendungen nutzen können. Um Leistungsprobleme zu vermeiden, z. B. abfallende Frames oder Stottern erfüllt, Verbrauch dieser Daten muss sorgfältig durchgeführt werden.

Aktive scannen, während eine Benutzeroberfläche kann sowohl nützlich oder gleichzeitiger Aufrufe nachteilig auswirken und die Entwickler müssen Sie festlegen, die zu verwendende Methode abhängig von der Umgebung.

### <a name="cached-spatial-mapping"></a>Zwischengespeicherte räumliche Zuordnung

Im Fall von zwischengespeicherten räumliche Zuordnung, wird die Anwendung in der Regel eine Momentaufnahme der Daten räumliche Zuordnung, und diese Momentaufnahme für die Dauer der Benutzeroberfläche verwendet.

**Vorteile**
* Gemeinkosten auf dem System während die Oberfläche führende, auf eindrucksvolle Stromversorgung, temperaturüberwachung ausgeführt wird und cpu-Leistung erzielt.
* Eine einfachere Implementierung der main-Umgebung, da er nicht von Änderungen in den räumlichen Daten unterbrochen wird.
* Ein einzelnes einmal, die Kosten für die räumlichen Daten für Physik, Grafiken und andere Zwecke verarbeitet Post.

**Drawbacks**
* Das Verschieben von realen Objekten oder Personen, die nicht durch die zwischengespeicherten Daten wiedergegeben. z. B. die Anwendung ggf. eine Tür geöffnet, wenn sie nun geschlossen wird.
* Möglicherweise weitere Anwendungsspeicher auf die zwischengespeicherte Version der Daten zu verwalten.

Ein überzeugendes Argument für diese Methode ist einer kontrollierten Umgebung oder eine Tabelle, die Top-Spiel.

### <a name="continuous-spatial-mapping"></a>Fortlaufende räumliche Zuordnung

Bestimmte Anwendungen basieren möglicherweise auf weiterhin Scans aus, um die räumliche Zuordnungsdaten zu aktualisieren.

**Vorteile**
* Sie müssen nicht in einer separaten Scannen oder Durchsuchen Benutzeroberfläche schon im Vorfeld in Ihrer Anwendung zu erstellen.
* Die Verschiebung der realen Welt Objekte kann durch das Spiel auch mit der eine Verzögerung wiedergegeben.

**Drawbacks**
* Höhere Komplexität in der Implementierung der main-Umgebung.
* Potenzielle Aufwand für die zusätzliche Verarbeitung für Grafik oder Physik als Änderungen inkrementell von diesen Systemen erfasst werden müssen.
* Höhere Leistung, thermischer und Auswirkung auf die CPU.

Ein überzeugendes Argument für diese Methode ist eine Hologramme werden, in denen erwartet, für die Interaktion mit dem Verschieben von Objekten, z. B. ein holographic Auto, die Laufwerke auf dem Boden ordnungsgemäß in eine Tür abhängig davon, ob sie offene oder geschlossene erhöhen möchten.

## <a name="see-also"></a>Siehe auch
* [Räumliche Zuordnung entwerfen](spatial-mapping-design.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Entwurf](spatial-sound-design.md)
