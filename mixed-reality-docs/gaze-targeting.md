---
title: Blicke für
description: Alle Interaktionen werden erstellt, auf die Fähigkeit eines Benutzers, das Element als Ziel, die, das Sie mit, unabhängig von der Eingabe Modalität interagieren möchten.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität, die Blicke, die Blicke Ziel ist, handelt es sich bei der Interaktion, Entwerfen
ms.openlocfilehash: 1ac4f06208a7574fced0a7e27e93469ec93bf6e0
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873925"
---
# <a name="gaze-and-dwell"></a>Blicke und dwell
Es gibt viele verschiedene Möglichkeiten, vergewissern Sie sich eine _Commit_ wie das Kombinieren von Blicke mit _Voice_ oder _Gesten übergeben_.
Gibt es jedoch werden mehrere Szenarien, in dem Benutzer bereit ist entweder ausgelastet oder können nicht nachverfolgt werden (z. B. Factory Worker mit übergroße hohe designarbeiten Handschuhe). Spracheingabe kann auch aufgrund von benutzereinstellungen, soziale Netzwerke Kontext oder laut Umgebungen nicht verfügbar.
Als alternative Lösung für eine andere option zum Ausführen einer _Commit_ besteht darin, die an ein Benutzeroberflächenelement starren beibehalten, die dies _länger aufhalten_.
Ein _länger aufhalten_ kann mit entweder "Head" oder "Eye Blicke ausgeführt werden. Die Idee ist einfach und kann in den folgenden Phasen unterteilt werden: 
1. Benutzer startet auf Knopfdruck holographic gazing

2. Nach einer kurzen Einsatz Verzögerung (z. B. der 150 ms) wird eine Animation visuelles Feedback gestartet. Die Verzögerung der Einsatz wird verwendet, um zu vermeiden einer Überlastung des Benutzers sofort, etwa durch Feedback jederzeit.
    - Für _Eye Blicke_, es wird empfohlen, die folgenden für den Entwurf des visuellen Elements länger aufhalten, Feedback:
      - **Mische es**: Blend-reibungslos in das Feedback von an, um vollständig deckend kaum noch sichtbar. Dies macht dem Feedback, weniger Ablenkung und Overwhleming und gut richtet sich das vertrauen, das das System hat, dass der Benutzer möchte mit dieser Schaltfläche in Verbindung setzen.
      - **Ziehen Sie sie**: Erstellen Sie ein visuelles Feedback als vergrößern und verschiebt in Richtung der Mitte des Ziels, in visual Aufmerksamkeit des Benutzers abrufen. 

3. Nach einer vordefinierten Dwell-Dauer (z. B. 800 ms) die Dwell abgeschlossen ist, und ein zugeordnetes Ereignis wird ausgelöst.
    - Geben Sie einige akustische abgeschlossen, oder visuelles Feedback, wirklich Startseite, die das Element anzuzeigen haben jetzt ausgewählt.

![Länger aufhalten Zustände](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Blicke für

Alle Interaktionen werden erstellt, auf die Fähigkeit eines Benutzers, das Element als Ziel, die, das Sie mit, unabhängig von der Eingabe Modalität interagieren möchten. In Windows Mixed Reality, erfolgt dies in der Regel mithilfe des Benutzers Blicke.

Damit Benutzer erfolgreich eine Möglichkeit zum arbeiten können, muss des Systems berechnete Verständnis der Absicht des Benutzers und die Absicht des Benutzers tatsächliche, so weit wie möglich ausgerichtet sind. Um den Grad an, dass das System den beabsichtigten Benutzeraktionen interpretiert verbessert ordnungsgemäß Kundenzufriedenheit erhöht und die Leistung.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Blicke für</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> Auge als Ziel</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md).

## <a name="target-sizing-and-feedback"></a>Ziel-größenanpassung und feedback

Der Blicke Vektor hat wiederholt angezeigt wurden, für die Ziel-problemlos verwendet werden kann, aber häufig am besten für gross für die Zielgruppenadressierung (erwerben von etwas größer Ziele). Mindestversion der Zielplattform Größen von 1 bis 1.5 Grad sollte erfolgreich Benutzeraktionen in den meisten Szenarien ermöglichen, wenn Ziele von 3 Grad häufig schneller zu ermöglichen. Beachten Sie, dass die Größe, der Benutzerziele ist eine 2D-Bereich auch für 3D-Elemente – welche Projektion sie-Sie sollte Bereich als Ziel gesetzt sein. Bietet einige wichtige Hinweis, dass ein Element "aktiv" ist, (, dass der Benutzer es abzielt) äußerst hilfreich ist – dazu zählen Behandlungen, damit wie sichtbar "darauf zeigen" Effekte "," audio-Highlights "oder" klickt, oder deaktivieren Sie die Ausrichtung eines Cursors mit einem Element.

![Optimale Zielgröße im Abstand von 2 Verbrauchseinheit](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Verbrauchseinheit*

![Ein Beispiel für ein Zielobjekt Blicke hervorheben](images/gazetargeting-highlighting-640px.jpg)<br>
*Ein Beispiel für ein Zielobjekt Blicke hervorheben*

## <a name="target-placement"></a>Ziel-Platzierung

Benutzer können häufig nicht finden im jeweiligen Lesebereich, Benutzeroberflächenelemente, die sehr hoch oder sehr niedrige positioniert sind die meisten ihre Aufmerksamkeit auf Bereiche, um ihren Mittelpunkt (in der Regel ungefähr Eye-Ebene) konzentrieren. Die meisten Ziele in eine angemessene-Band-Bereich von Eye-Ebene platzieren können. Erhält die Tendenz eines für Benutzer kann für den Blick auf einer relativ kleinen visuellen Elements jederzeit (der attentional Lichtkegel des Vision ist ungefähr 10 Grad), der gruppieren Elemente der Benutzeroberfläche, die den Grad an, dass sie konzeptionell verwandt sind Aufmerksamkeit mit vorwärtsverkettung Verhaltensweisen nutzen Element zu Element als ein Benutzer durchläuft einen Bereich ihre Blicke. Beim Entwerfen der Benutzeroberfläche sollten Sie Bedenken der großen möglichen Variante im Lesebereich zwischen HoloLens und immersive Headsets.

![Ein Beispiel für gruppierte Elemente der Benutzeroberfläche für einfacher Blicke Zielgruppenadressierung in Galaxy-Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ein Beispiel für gruppierte Elemente der Benutzeroberfläche für einfacher Blicke Zielgruppenadressierung in Galaxy-Explorer*

## <a name="improving-targeting-behaviors"></a>Verbessern die Zielgruppenadressierung anhand bestimmter Verhaltensweisen

Wenn Benutzerabsicht etwas Ziel kann werden festgelegt (oder eng angeglichen), kann es sehr hilfreich sein, zu akzeptieren, dass "Near Miss" bei der Interaktion versucht, als ob sie ordnungsgemäß zugewiesen wurden. Es gibt eine Reihe von erfolgreichen Methoden, die in mixed Reality-Benutzeroberfläche integriert werden können:

### <a name="gaze-stabilization-gravity-wells"></a>Blicke Stabilisierung ("Schwerkraft Wells")

Dies sollte die meisten oder alle der Zeit aktiviert werden. Dieses Verfahren wird die natürliche Haupt-/trichterhalses JIT-Compiler, die Benutzer möglicherweise entfernt. Auch Verschiebung aufgrund von Verhaltensweisen suchen/sprechen.

### <a name="closest-link-algorithms"></a>Am nächsten Link-Algorithmen

Diese funktionieren am besten in Bereichen mit geringer Dichte interaktive Inhalte. Liegt eine hohe Wahrscheinlichkeit, dass auf Sie bestimmen können, was ein Benutzer versucht hat, für die Interaktion mit, können Sie die Zielgruppenadressierung anhand bestimmter Möglichkeiten ergänzen, indem Sie einfach vorausgesetzt gewisse Absicht.

### <a name="backdatingpostdating-actions"></a>Backdating/postdating Aktionen

Dieser Mechanismus eignet sich Aufgaben aus, die Geschwindigkeit zur Verfügung. Wenn ein Benutzer den durch eine Reihe von Ziel/Aktivierung Schachzüge Geschwindigkeit ist, es kann hilfreich sein, einige Absicht angenommen und ermöglichen *Schritte fehlen* zu Zielen reagieren, die der Benutzer den Fokus etwas vor oder nach der Tap (etwas 50 ms war gültig. vor/nach dem in einem frühen Stadium testen).

### <a name="smoothing"></a>Glättung

Dieser Mechanismus eignet sich für Pfade Bewegungen, reduzieren die leichte Jitter/bringen aufgrund von natürlichen Bewegungen Merkmale. Wenn Sie über die Pfade Bewegungen, die von der Größe/Entfernung von Bewegungen statt im Laufe der Zeit smooth-Glättung

### <a name="magnetism"></a>Magnetismus

Dieser Mechanismus kann als eine allgemeine Version des "Nächsten link" Algorithmen, zeichnen einen Cursor auf ein Ziel oder Vergrößerung Hitboxes (ob sichtbar oder nicht) betrachtet werden, wie Benutzer wahrscheinlich Ziele Ansatz, verwenden einige Kenntnisse über das interaktive Layout Benutzerabsicht für eine bessere Ansatz. Dies kann besonders für kleine Ziele effektiv sein.

### <a name="focus-stickiness"></a>Fokus-Bindung

Wenn Sie die in der Nähe interaktive Elemente Fokus erhalten bestimmen, geben Sie eine Verschiebung auf das Element, das gerade fokussiert ist. Dadurch können die fehlerhaften Verhalten wechseln, in eine Mitte zwischen zwei Elemente mit dem natürlichen Geräusch unverankerten Fokus zu reduzieren.

## <a name="see-also"></a>Siehe auch
* [Gesten](gestures.md)
* [Sprachentwurf](voice-design.md)
* [Cursor](cursors.md)
