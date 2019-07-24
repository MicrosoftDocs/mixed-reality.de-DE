---
title: Ziel Ausrichtung
description: Alle Interaktionen basieren auf der Fähigkeit eines Benutzers, das Element, mit dem er interagieren möchte, unabhängig von der Eingabemethode auszuwählen.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Ziel Ausrichtung, Interaktion, Entwurf
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829838"
---
# <a name="gaze-and-dwell"></a>Schauen und wohnen
Es gibt viele verschiedene Möglichkeiten, einen _Commit_ zu bestätigen, wie z. b  . die Kombination von Blick und _Handgesten_.
Es gibt jedoch mehrere Benutzer Szenarios, in denen Benutzer Hände entweder ausgelastet sind oder nicht nachverfolgt werden können (z. b. Factory-Worker mit überdimensionalen Handschuhen). Die Spracheingabe ist möglicherweise auch aufgrund von Benutzereinstellungen, sozialer Kontext oder lauter Umgebungen nicht verfügbar.
Eine alternative Möglichkeit, einen _Commit_ auszuführen, besteht darin, einfach auf ein Benutzeroberflächen Element zu schauen, das wir als " _wohnen_" bezeichnen.
Ein " _Dwell_ " kann entweder mit dem Kopf-oder Augenblick ausgeführt werden. Die Idee ist einfach und kann in den folgenden Phasen aufgeschlüsselt werden: 
1. Benutzer beginnt mit der Eingabe auf einer Holographic-Schaltfläche

2. Nach einer kurzen Verzögerung (z. b. 150 ms) wird eine visuelle Feedback Animation gestartet. Die Verzögerung wird verwendet, um zu vermeiden, dass der Benutzer immer wieder über das Feedback kommt.
    - Für den _Augenblick_empfiehlt es sich, Folgendes für den Entwurf des Feedbacks für visuelle Informationen zu erhalten:
      - **Kombinieren Sie es**: Nahtlos in das Feedback von kaum sichtbarem zu vollständig undurchsichtigem Feedback. Dadurch wird das Feedback weniger ablenkend und überschrieben, und es wird sicher mit dem Vertrauen abgestimmt, das das System hat, dass der Benutzer diese Schaltfläche wirklich einbinden möchte.
      - Per **Pull abrufen**: Erstellen Sie ein visuelles Feedback als Verkleinerung der Größe, und bewegen Sie sich zur Mitte des Ziels, um die visuelle Aufmerksamkeit des Benutzers zu erhalten. 

3. Nach einer vordefinierte verlaufdauer (z. b. 800 ms) wird das Ende abgeschlossen, und ein zugeordnetes Ereignis wird ausgelöst.
    - Stellen Sie ein entsprechendes Akustik-oder visuelles Feedback bereit, um zu Hause zu kommen, dass das Element jetzt ausgewählt wurde.

![Verweil Zustände](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Ziel Ausrichtung

Alle Interaktionen basieren auf der Fähigkeit eines Benutzers, das Element, mit dem er interagieren möchte, unabhängig von der Eingabemethode auszuwählen. In Windows Mixed Reality erfolgt dies in der Regel durch das Anvisieren durch den Benutzer.

Damit ein Benutzer erfolgreich mit einer Umgebung arbeiten kann, muss die vom System berechnete Absicht des Benutzers mit der tatsächlichen Absicht des Benutzers weitestgehend übereinstimmen. In dem Maße, in dem das System die beabsichtigten Aktionen des Benutzers richtig interpretiert, steigen Zufriedenheit und Leistung.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Ziel Ausrichtung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Ziel Ausrichtung</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](index.md)verfügbar.

## <a name="target-sizing-and-feedback"></a>Skalieren von Zielen und Feedback

Der Anvisierungsvektor hat wiederholt gezeigt, dass er zur Bestimmung präziser Ziele geeignet ist, aber oftmals funktioniert er bei der Bestimmung größerer Ziele am besten. Mindestzielgrößen von 1 bis 1,5 Grad sollten in den meisten Szenarien erfolgreiche Benutzeraktionen ermöglichen, obwohl Ziele von 3 Grad oft eine höhere Geschwindigkeit ermöglichen. Beachten Sie, dass die Größe, auf die der Benutzer ausgerichtet ist, auch für 3D-Elemente effektiv ein 2D-Bereich ist. Die ihm jeweils zugewandte Projektion sollte der Zielbereich sein. Es ist äußerst hilfreich, einen markanten Hinweis darauf zu geben, dass ein Element „aktiv“ ist (es wurde vom Benutzer anvisiert). Dies kann die Anwendung von sichtbaren „Hover“-Effekten, akustischen Hervorhebungen oder Klicks oder die eindeutige Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Metern*

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-640px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung

Benutzer können häufig keine Benutzeroberflächenelemente finden, die in ihrem Sichtfeld sehr hoch oder sehr niedrig positioniert sind, sodass sie sich hauptsächlich auf Bereiche um ihren Hauptfokus konzentrieren (in der Regel in etwa auf Augenhöhe). Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Tendenz, dass sich der Benutzer jeweils auf einen relativ kleinen visuellen Bereich konzentrieren kann (der Blickwinkel beträgt etwa 10 Grad), kann die Gruppierung von Benutzeroberflächenelementen in dem Maße, in dem sie konzeptionell verwandt sind, das Verhalten zum Kombinieren der Aufmerksamkeit von Element zu Element nutzen, wenn der Blick eines Benutzers durch einen Bereich schweift. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung

Wenn die Absicht des Benutzers, etwas anzuvisieren, bestimmt (oder näherungsweise ermittelt) werden kann, ist es möglicherweise sehr hilfreich, „near miss“-Versuche (Beinahekollision) bei der Interaktion so zu akzeptieren, als ob die Zielbestimmung ordnungsgemäß erfolgt wäre. Es gibt eine Reihe erfolgreicher Methoden, die in Mixed Reality-Umgebungen integriert werden können:

### <a name="gaze-stabilization-gravity-wells"></a>Blick Stabilisierung ("gravitationsbrunnen")

Dies sollte meistens/immer aktiviert sein. Bei diesem Verfahren werden die natürlichen Kopf-/Nackenschwankungen entfernt, die Benutzer möglicherweise aufweisen. Ebenso Bewegungen aufgrund von Verhaltensweisen beim Sehen/Sprechen.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung

Diese funktionieren am besten in Bereichen mit wenig interaktiven Inhalten. Wenn es eine hohe Wahrscheinlichkeit gibt, dass Sie das Interaktionsziel eines Benutzers bestimmen können, haben Sie die Möglichkeit, ihre Fähigkeiten zur Zielbestimmung zu ergänzen, indem Sie einfach einen Absichtsgrad annehmen.

### <a name="backdatingpostdating-actions"></a>Rückdatierung/Nachdatierung von Aktionen

Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn ein Benutzer mit der Geschwindigkeit eine Reihe von Ziel-/Aktivierungs Manövern durchläuft, kann es sinnvoll sein, eine Absicht anzunehmen und *versäumte Schritte* zuzulassen, um auf Ziele zu reagieren, auf die sich der Benutzer vor oder nach dem tippen etwas bewegt hat (50 ms vor/nachher). in frühen Tests wirksam).

### <a name="smoothing"></a>Glättung

Dieser Mechanismus ist hilfreich bei Wegstreckenbewegungen und reduziert das leichte Zittern/Schwanken aufgrund der natürlichen Kopfbewegungseigenschaften. Bei der Glättung über Wegstreckenbewegungen, glätten Sie eher nach Größe/Abstand der Bewegungen als nach Zeit.

### <a name="magnetism"></a>Magnetismus

Dieser Mechanismus kann als eine allgemeinere Version der Algorithmen für die engste Verbindung betrachtet werden. Dabei wird ein Cursor in Richtung eines Ziels gezogen oder es werden einfach die Trefferfelder (sichtbar oder nicht) vergrößert, wenn sich Benutzer voraussichtlichen Zielen nähern. Dabei werden Kenntnisse des interaktiven Layouts verwendet, um sich der Absicht des Benutzers besser zu nähern. Dies kann insbesondere bei kleinen Zielen sehr wirkungsvoll sein.

### <a name="focus-stickiness"></a>Fokusbindung

Wenn Sie bestimmen, welche interaktiven Elemente in der Nähe den Fokus erhalten sollen, stellen Sie eine Tendenz für das Element bereit, das gerade über den Fokus verfügt. Dies trägt dazu bei, unkontrolliertes Verhalten beim Fokuswechsel zu reduzieren, wenn Sie mittig zwischen zwei Elementen mit natürlicher Verzerrung schwanken.

## <a name="see-also"></a>Siehe auch
* [Gesten](gestures.md)
* [Sprachbefehle](voice-design.md)
* [Cursor](cursors.md)
