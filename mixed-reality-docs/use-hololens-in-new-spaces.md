---
title: Verwenden von hololens in neuen Leerzeichen
description: Hololens erfährt, wie ein Raum im Laufe der Zeit aussieht. Benutzer können diesen Prozess vereinfachen, indem Sie die hololens auf bestimmte Weise über den Raum verschieben.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, räumliche Zuordnung, hololens, Oberflächenrekonstruktion, Mesh, Head Tracking, Mapping
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566019"
---
# <a name="use-hololens-in-new-spaces"></a>Verwenden von hololens in neuen Leerzeichen

Hololensordnet Informationen zu Ihrer Umgebung zu oder erfährt diese, wenn der Benutzer sich um ein Leerzeichen bewegt. Im Laufe der Zeit erstellt der hololens eine *räumliche Karte* aller Teile der Umgebung, die beobachtet wurden. Hololens aktualisiert die Karte, wenn Änderungen in der Umgebung beobachtet werden. Diese Überprüfung wird automatisch zwischen App-Starts beibehalten.

Hololens erstellt und aktualisiert Zuordnungen, solange das Gerät eingeschaltet ist und ein Benutzer angemeldet ist. Wenn Sie das Gerät mit den Kameras halten, die auf ein Leerzeichen zeigen, wird das Gerät versuchen, den Bereich zuzuordnen. Obwohl die hololens im Laufe der Zeit ein Leerzeichen erlernen, stehen Ihnen Tipps und Tricks zur Verfügung, mit denen Sie den Raum schneller und effizienter zuordnen können. 

Wenn Ihre hololens Ihren Speicherplatz nicht zuordnen können oder nicht. Im eingeschränkten Modus können Sie holograms nicht in Ihrer Umgebung platzieren.

## <a name="tips-and-tricks-for-mapping-spaces"></a>Tipps und Tricks zum Mapping von Leerzeichen

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>Stellen Sie sicher, dass der Speicherplatz für die gemischte Realität eingerichtet ist.

Funktionen in einer Umgebung können es den hololens erschweren, ein Leerzeichen zu interpretieren. Helle Ebenen, Materialien im Raum, das Layout von Objekten und mehr können beeinflussen, wie hololens einen Bereich zuordnet.

Tipps zum Einrichten Ihres Speicherplatzes für hololens und andere gemischte Reality-Geräte finden Sie unter [Überlegungen zur Umgebung für hololens](environment-considerations-for-hololens.md).

### <a name="understand-the-scenarios-for-the-area"></a>Verstehen der Szenarien für den Bereich

Es ist wichtig, dass Sie die meiste Zeit aufwenden, in der Sie die hololens verwenden, damit die Karte relevant und fertig ist. 

Wenn z. b. ein Benutzer Szenario für hololens von Punkt a zu Punkt B wechselt, führen Sie diesen Pfad zwei bis drei Mal aus, und suchen Sie in allen Richtungen nach dem verschieben. 

### <a name="walk-slowly-around-the-space"></a>Gehen Sie langsam um den Bereich.

Wenn Sie den Bereich zu schnell durchlaufen, ist es wahrscheinlich, dass die hololens zuordnungsbereiche übersehen werden. Gehen Sie langsam um den Raum, und beenden Sie alle 5-8 Meter, um sich in Ihrer Umgebung anzusehen.

Smooth Movement unterstützt auch die Zuordnung von hololens.

### <a name="look-in-all-directions"></a>In alle Richtungen suchen

Wenn Sie den Leerraum Zuordnungen, werden den hololens mehr Daten angezeigt, in denen sich Punkte relativ zueinander befinden. 

Wenn Sie z. b. nicht nachschlagen, wissen die hololens möglicherweise nicht, wo die Obergrenze in einem Raum liegt. 

Vergessen Sie nicht, auf dem Boden zu suchen, während Sie das Leerzeichen zuordnen.

### <a name="cover-key-areas-multiple-times"></a>Wichtige Bereiche mehrmals abdecken

Wenn Sie einen Bereich mehrmals durchlaufen, können Sie Features auswählen, die Sie in der ersten exemplarischen Vorgehensweise übersehen haben. Versuchen Sie, einen Bereich von zwei bis drei Mal zu durchlaufen, um eine ideale Karte zu erstellen.

Wenn dies möglich ist, können Sie sich beim Wiederholen dieser Bewegungen Zeit um einen Bereich in einer Richtung machen und dann die Art und Weise wiederholen, wie Sie es kam.

### <a name="take-your-time-mapping-the-area"></a>Nehmen Sie die Zeit für die Zuordnung des Bereichs

Es kann zwischen 15 und 20 Minuten dauern, bis der hololens vollständig zugeordnet ist und sich an seine Umgebung anpasst. Wenn Sie über ein Leerzeichen verfügen, in dem Sie regelmäßig ein hololens verwenden möchten, können Sie das Problem später vermeiden, indem Sie diese Zeit zum Zuordnen des Speicherplatzes verwenden. 

## <a name="possible-errors-in-the-spatial-map"></a>Mögliche Fehler in der räumlichen Karte

Fehler bei räumlichen Zuordnungsdaten lassen sich in eine von drei Kategorien unterteilen:

* *Löcher*: In den räumlichen Mapping-Daten fehlen reale Oberflächen.
* *Halluerationen*: In den räumlichen Mapping-Daten, die nicht in der realen Welt vorhanden sind, sind Oberflächen vorhanden.
* *Wurmlöcher*: Hololens "verliert" einen Teil der räumlichen Zuordnung, indem er denkt, dass er sich in einem anderen Teil der Karte befindet, als er tatsächlich ist.
* *Bias*: Oberflächen in den räumlichen Zuordnungsdaten sind unpassend an realen Oberflächen ausgerichtet, die entweder per pushübertragung oder ausgecheckt werden.

Viele dieser Fehler können durch [Löschen der Hologramme](environment-considerations-for-hololens.md) und Neuzuordnung des Speicherplatzes verringert werden.