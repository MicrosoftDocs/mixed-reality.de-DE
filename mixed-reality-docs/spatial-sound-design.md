---
title: Räumlicher Sound Entwurf
description: Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, räumlicher Sound, Entwurf, Stil
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750307"
---
# <a name="spatial-sound-design"></a>Räumlicher Sound Entwurf

Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.

Wenn Sie jemals [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game))gespielt haben, oder wenn jemand Ihr Telefon anrufen wollte, um es zu finden, sind Sie bereits mit der Wichtigkeit räumlicher Sounds vertraut. Wir verwenden in unserer täglichen Umgebung Sound Hinweise, um nach Objekten zu suchen, die Aufmerksamkeit von Menschen zu erhalten oder ein besseres Verständnis für unsere Umgebung zu erhalten. Umso genauer verhält sich der Sound Ihrer APP, wie es in der realen Welt der Fall ist.

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumlicher Sound Entwurf</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Vier wichtige Dinge, die räumliche Klänge für die Entwicklung gemischter Realität

Standardmäßig werden Sounds in Stereo wiedergegeben. Dies bedeutet, dass der Sound ohne räumliche Position wiedergegeben wird, sodass der Benutzer nicht weiß, woher der Sound stammt. Räumlicher Sound führt vier wichtige Punkte für die Entwicklung gemischter Realität aus:

**Begründet**

Ohne Sound sind virtuelle Objekte tatsächlich nicht mehr vorhanden, wenn wir unsere Kopfzeile ausschalten. Genau wie bei echten Objekten möchten Sie diese Objekte auch dann hören können, wenn Sie Sie nicht sehen können, und Sie möchten Sie in der Lage sein, Sie überall herum zu finden. Ebenso wie virtuelle Objekte visuell auf eine Kombination mit der realen Welt basieren müssen, müssen Sie auch in der Praxis verankert werden. Räumlicher Sound kombiniert ihre reale Audioumgebung nahtlos mit der digitalen Audioumgebung.

**Benutzer Aufmerksamkeit**

In gemischter Realität können Sie nicht davon ausgehen, wo der Benutzer sucht, und erwarten, dass er etwas von Ihnen in der Welt visuell platziert. Benutzer können jedoch immer eine Soundwiedergabe hören, auch wenn sich das Objekt, das den Sound abgespielt hat, dahinter befindet. Menschen werden daran gewöhnt, dass Sie von Sound gezeichnet werden. wir sehen uns instatyp an, dass wir uns auf ein Objekt konzentrieren, das wir uns von uns hören Wenn Sie den Blick Ihres Benutzers an eine bestimmte Stelle leiten möchten, anstatt einen Pfeil zum visuellen darstellen zu verwenden, ist das Platzieren eines Sounds an dieser Stelle eine sehr natürliche und schnelle Möglichkeit, Sie zu begleiten.

**Intensiv**

Wenn Objekte verschoben oder miteinander in Konflikt stehen, werden diese Interaktionen zwischen Material normalerweise angezeigt. Wenn Ihre Objekte also nicht denselben Sound haben, den Sie in der realen Welt haben, gehen Sie wie folgt vor, wenn Sie sich einen beängstigenden Film mit dem Volume ansehen. Alle Sounds in der realen Welt stammen von einem bestimmten Punkt im Raum: Wenn wir unsere Köpfe drehen, hören wir die Änderung in Bezug auf unsere Klänge, und wir können den Speicherort jedes Sounds auf diese Weise nachverfolgen. Räumliche Sounds bilden das "Gefühl" eines Orts, der über das, was wir sehen können, hinausgeht.

**Interaktions Entwurf**

In den meisten herkömmlichen interaktiven Umgebungen werden Interaktions Sounds wie Benutzeroberflächen-Soundeffekte in der standardmäßigen Mono-oder Stereo-Datei wiedergegeben. Da alles in gemischter Realität im 3D-Raum vorhanden ist, einschließlich der Benutzeroberfläche, profitieren diese Objekte von räumlichen Sounds. Wenn wir auf eine Schaltfläche in der realen Welt klicken, kommt der Ton, den wir hören, von dieser Schaltfläche. Durch die Spatialisierung von Interaktions Sounds bieten wir wieder eine natürlichere und realistischere Benutzer Leistung.

## <a name="best-practices-when-using-spatial-sound"></a>Bewährte Methoden bei der Verwendung von räumlichem Sound

**Echte Sounds funktionieren besser als synthetische oder unnatürliche Sounds.**

Umso vertrauter ist Ihr Benutzer mit einem Audiotyp, umso realer ist er, und das ist leichter in der Lage, ihn in der Umgebung zu finden. Eine menschliche Stimme ist z. b. ein sehr gängiger Audiotyp, und Ihre Benutzer finden Sie genau so schnell wie eine echte Person im Raum, die mit Ihnen kommuniziert.

**Simulation der Erwartung von Trumps**

Wenn Sie einen Sound verwenden, der von einer bestimmten Richtung stammt, wird Ihre Aufmerksamkeit unabhängig von räumlichen Cues in diese Richtung geleitet. In den meisten Fällen, in denen wir Vögel hören, sind Sie z. b. über uns. Die Wiedergabe des Sounds eines Vogels führt wahrscheinlich dazu, dass der Benutzer auch dann nach oben sucht, wenn Sie den Sound unterhalb platzieren. Dies ist in der Regel verwirrend, und es wird empfohlen, dass Sie mit Erwartungen wie diesen arbeiten, anstatt sie gegen eine natürlichere Darstellung zu machen.

**Die meisten Sounds sollten räumlich behandelt werden.**

Wie bereits erwähnt, ist alles in gemischter Realität im 3D-Bereich vorhanden. Ihre Klänge sollten ebenfalls angezeigt werden. Selbst Musik kann manchmal von der Spatialisierung profitieren, insbesondere wenn Sie an ein Menü oder eine andere Benutzeroberfläche gebunden ist.

**Vermeiden unsichtbarer Emitter**

Da wir so konzipiert sind, dass wir uns mit den Sounds beschäftigen, die wir uns im Blick haben, kann es sich um eine unnatürliche und sogar entstehende Erfahrung handeln, um einen Sound zu finden, der keine visuelle Präsenz hat. Klänge in der realen Welt stammen nicht aus einem leeren Bereich. Achten Sie daher darauf, dass ein audioemitter in der unmittelbaren Umgebung des Benutzers platziert wird, der auch angezeigt werden kann.

**Vermeiden räumlicher Maskierung**

Räumlicher Sound stützt sich auf sehr feine akustische Hinweise, die von anderen Sounds unterstützt werden können. Wenn Sie Stereo Musik oder Ambient-Sounds haben, stellen Sie sicher, dass Sie in der Mischung niedrig genug sind, um Platz für die Details ihrer räumlichen Sounds zu schaffen, mit denen Ihre Benutzer Sie leicht finden können, und halten Sie Sie realistisch und natürlich.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Allgemeine Konzepte, die bei der Verwendung von räumlichem Sound berücksichtigt werden sollten

**Räumlicher Sound ist eine Simulation**

Die häufigste Verwendung von räumlichem Sound ist, dass ein Sound so erscheint, als wäre er von einem realen oder virtuellen Objekt auf der Welt. Daher ist es möglich, dass räumliche Sounds aus solchen Objekten am sinnvollsten werden.

Beachten Sie, dass die wahrgenommene Genauigkeit räumlicher Töne bedeutet, dass ein Sound nicht notwendigerweise aus dem Mittelpunkt eines Objekts ausgegeben werden sollte, da der Unterschied abhängig von der Größe des Objekts und der Entfernung zum Benutzer erkennbar ist. Bei kleinen Objekten ist der Mittelpunkt des Objekts in der Regel ausreichend. Bei größeren Objekten sollten Sie einen audioemitter oder mehrere Emitter an der spezifischen Position innerhalb des Objekts, das den Sound erzeugen soll, benötigen.

**Alle Sounds normalisieren**

Die Entfernungs Dämpfung erfolgt schnell innerhalb der ersten Verbrauchseinheit des Benutzers, wie dies in der realen Welt der Fall ist. Alle Audiodateien sollten normalisiert werden, um eine physisch exakte Entfernungs Dämpfung sicherzustellen und sicherzustellen, dass ein Sound in einigen Metern entfernt werden kann (falls zutreffend). Das räumliche Audiomodul behandelt die für einen Sound erforderliche Dämpfung, wie es sich in einer bestimmten Entfernung befindet (mit einer Kombination aus Dämpfung und "Entfernungs hinweisen"), und das Anwenden einer beliebigen Dämpfung, die den Effekt verringern kann. Außerhalb der Simulation eines echten Objekts ist der anfängliche Entfernungs Abfall von *räumlichen Sound* Geräuschen wahrscheinlich mehr als ausreichend für eine ordnungsgemäße Mischung ihrer Audiodaten.

**Objekt Ermittlung und Benutzeroberflächen**

Wenn Sie Audiohinweise verwenden, um die Aufmerksamkeit des Benutzers außerhalb der aktuellen Ansicht zu leiten, sollte der Sound in der Mischung, auch über alle Stereo Sounds und alle anderen räumlichen Sounds, die vom direktionalen audiohinweis abweichen können, hörbar und deutlich werden. Bei Sounds und Musik, die einem Element der Benutzeroberfläche (z. b. einem Menü) zugeordnet sind, sollte der audioemitter an dieses Objekt angefügt werden. Stereo und andere nicht positionelle Audiowiedergabe können das Auffinden von räumlichen Elementen erschweren (siehe oben). Vermeiden Sie räumliche Maskierung).

**Verwenden Sie den räumlichen Sound über den 3D-Standard Sound so weit wie möglich**

In gemischter Realität sollte 3D-Audio mit räumlichem Sound anstelle von Legacy-3D-Audiotechnologien erzielt werden. Im Allgemeinen sind bei der verbesserten Spatialisierung die kleinen CPU-Kosten im Vergleich zum 3D-Standard Sound zu verbessern. Standard mäßige 3D-Audiodaten können für Sounds mit niedriger Priorität verwendet werden, für die ein räumliches, aber nicht notwendigerweise an ein physisches oder virtuelles Objekt gebunden ist, sowie für Objekte, die der Benutzer niemals zum interagieren mit der APP benötigt.

## <a name="see-also"></a>Siehe auch
* [Raumklang](spatial-sound.md)
* [Räumliche Abbildung](spatial-mapping.md)
