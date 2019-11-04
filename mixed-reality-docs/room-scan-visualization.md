---
title: Raum Scan Visualisierung
description: Anwendungen, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, App-Muster, Entwurf, hololens, Raum Überprüfung, räumliche Zuordnung, Mesh
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437514"
---
# <a name="room-scan-visualization"></a>Raum Scan Visualisierung

Anwendungen, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht. Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich überprüft hat.

Anwendungsentwickler haben mehrere Möglichkeiten, um hilfreiche räumliche Daten zu gewährleisten:
* Verlassen Sie sich darauf, was bereits gesammelt wurde. Diese Daten sind anfänglich möglicherweise unvollständig.
* Bitten Sie den Benutzer, mit der aufblühenden Bewegung den Windows Mixed Reality-Start zu verwenden und dann den Bereich zu erkunden, den Sie für die Benutzeroberfläche verwenden möchten. Mithilfe von Air-Tap können Sie überprüfen, ob dem Gerät der gesamte erforderliche Bereich bekannt ist.
* Erstellen Sie eine benutzerdefinierte Erkundung in ihrer eigenen Anwendung.

Beachten Sie, dass in allen diesen Fällen die während der Durchsuchung gesammelten tatsächlichen Daten vom System gespeichert werden, und die Anwendung muss dies nicht tun.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Raum Scan Visualisierung</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Entwickeln eines benutzerdefinierten Scanvorgangs

Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Umgebung analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen muss, um seine Vollständigkeit und Qualität zu verbessern. Wenn die Analyse anzeigt, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung bereitstellen, um auf der ganzen Welt zu überlagern:
* Der Anteil des Gesamtvolumens in der Benutzer Nähe muss Teil der Benutzerumgebung sein.
* An welcher Stelle der Benutzerdaten verbessern sollte

Benutzer wissen nicht, was einen "guten" Scan vornimmt. Sie müssen angezeigt werden, oder Sie müssen wissen, was Sie suchen müssen, wenn Sie aufgefordert werden, eine Überprüfung zu evaluieren – eine flache, eine Entfernung von tatsächlichen Wänden usw. Der Entwickler sollte eine Feedback Schleife implementieren, die das Aktualisieren der räumlichen Daten während der Scan-oder Auswertungs Phase umfasst.

In vielen Fällen kann es am besten sein, den Benutzern mitzuteilen, was Sie tun müssen (z. b. die Obergrenze, das Aussehen hinter den Möbeln), um die erforderliche Scanqualität zu erhalten.

## <a name="cached-versus-continuous-spatial-mapping"></a>Zwischengespeicherte und fortlaufende räumliche Zuordnung

Die räumlichen Daten sind die Daten, die von den Datenquellen Anwendungen mit hohem Gewicht beansprucht werden können. Um Leistungsprobleme zu vermeiden, wie z. b. gelöschte Frames oder stutor-Daten, sollte die Nutzung dieser Daten sorgfältig erfolgen.

Die aktive Überprüfung während einer-Darstellung kann sowohl vorteilhaft als auch schädlich sein, und der Entwickler muss entscheiden, welche Methode basierend auf der-Methode verwendet werden soll.

### <a name="cached-spatial-mapping"></a>Zwischengespeicherte räumliche Zuordnung

Bei einer zwischengespeicherten räumlichen Zuordnung erstellt die Anwendung in der Regel eine Momentaufnahme der räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme für die Dauer der Arbeit.

**Vorteile**
* Der geringere mehr Aufwand für das System, während die Ausführung ausgeführt wird, führt zu einer enormen Leistungssteigerung, zu Leistungseinbußen und CPU
* Eine einfachere Implementierung des Haupt Erlebnisses, da diese nicht durch Änderungen in den räumlichen Daten unterbrochen wird.
* Ein einzelner Zeitaufwand für die Verarbeitung räumlicher Daten für Physik, Grafiken und andere Zwecke.

**Nachteil**
* Die Verschiebung von realen Objekten oder Personen wird von den zwischengespeicherten Daten nicht widergespiegelt. z. B. die Anwendung wird möglicherweise eine Tür geöffnet, wenn Sie jetzt tatsächlich geschlossen wird.
* Potenziell mehr Anwendungs Speicher, um die zwischengespeicherte Version der Daten beizubehalten.

Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Top-Spiel der Tabelle.

### <a name="continuous-spatial-mapping"></a>Fortlaufende räumliche Zuordnung

Bestimmte Anwendungen verlassen sich möglicherweise auf das Fortsetzen des Scans, um räumliche Daten zu aktualisieren.

**Vorteile**
* Sie müssen in Ihrer Anwendung nicht in einer separaten Überprüfung oder Durchsuchung arbeiten.
* Die Bewegung von realen Objekten kann durch das Spiel reflektiert werden, obwohl es sich um eine Verzögerung handelt.

**Nachteil**
* Höhere Komplexität bei der Implementierung des Haupt Erlebnisses.
* Potenzieller mehr Aufwand für die zusätzliche Verarbeitung von Grafiken oder Physik, da Änderungen von diesen Systemen inkrementell erfasst werden müssen.
* Höhere Stromversorgung, thermische und CPU-Auswirkung.

Ein guter Fall für diese Methode ist eine Methode, bei der holograms mit verschiebenden Objekten interagieren soll, z. b. Wenn ein Holographic Car, das auf dem Boden ist, möglicherweise korrekt in eine Tür wechselt, je nachdem, ob es geöffnet oder geschlossen ist.

## <a name="see-also"></a>Weitere Informationen:
* [Räumliche Abbildung](spatial-mapping.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Raumklangentwurf](spatial-sound-design.md)
