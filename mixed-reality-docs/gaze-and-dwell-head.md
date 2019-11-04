---
title: Anvisieren mit dem Kopf und Verweilen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Verweilen“
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Verweilen, Interaktion, Entwurf
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439311"
---
# <a name="head-gaze-and-dwell"></a>Anvisieren mit dem Kopf und Verweilen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein. Sprachbefehle können wie Gesten in bestimmten Kontexten unzuverlässig sein, z. B. unter zu lauten Umgebungsbedingungen. Darüber hinaus ist der Einsatz der Stimme zur Steuerung von Computern nicht überall üblich, aber seine Bedeutung nimmt sicherlich zu. „Anvisieren mit dem Kopf und Verweilen“ bietet den bekanntesten und einfach zu bedienenden Mechanismus für das freihändige Heads-Up-Arbeiten mit der HoloLens. Darüber hinaus ist das Modell „Anvisieren mit dem Kopf und Verweilen“ unabhängig von Störgeräuschen und Ruheeinschränkungen in der Betriebssystemumgebung zu 100 % zuverlässig.

## <a name="scenarios"></a>Szenarien

In Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, ist der Kopf-und sprach Einstieg hervorragend, und die Stimme ist aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig oder nicht verfügbar. Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern. Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt. Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet. In der Kopfzeile und im Leben kann die Person, die die hololens verwendet, sicher in Ihrem Referenzmaterial navigieren, ohne den Workflow zu unterbrechen. 

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Eingabemodell</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Verweilen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
    </tr>
</table>


## <a name="design-principles"></a>Designprinzipien

**Vermeiden Sie "Blick als Waffe".**

„Anvisieren mit dem Kopf und Verweilen“ erfordert ein intuitives visuelles Feedback, aber zu viel Feedback kann beklemmend wirken. Das Feedback sollte einem Benutzer helfen sein Ziel zu erkennen, aber das Ziel nicht gegen seinen Willen automatisch auswählen. Das Lesen von Text, Symbolen und Beschriftungen erfordert eine zusätzliche Berücksichtigung, um einer Person den Raum zu geben, die Informationen vor der Auswahl zu erfassen.
    
**Durchsuchen der Goldilocks-Geschwindigkeit**
    
Verweilinteraktionen können je nach Auswirkung der Navigation unterschiedliche Timer aufweisen – häufiger verwendete Funktionen profitieren in der Regel von schnelleren Füllzeiten, während konsequentere Funktionen von längeren Füllzeiten profitieren können. Bei der Verwendung eines Fülleffekts zur Darstellung dieser Timer können Animationskurven der Füllfarbe das Gefühl schnellerer Füllzeiten positiv beeinflussen. Es sollte erwogen werden, dem Benutzer die Möglichkeit zu bieten, sich für eine schnelle, mittlere und langsame Füllgeschwindigkeit zu entscheiden.
    
**"No-No to Yo-Yo Effect"**

Der Jo-Jo-Effekt ist ein unangenehmes Muster der Kopfbewegung, das entstehen kann, wenn die Positionierung von Inhalten und die Steuerung durch „Anvisieren mit dem Kopf und Verweilen“ die Personen zwingt, ständig auf und ab zu schauen. Beispielsweise löst ein Listen Navigationsbereich mit der Schaltfläche "Head-Blick" und "Wohnen" am unteren Rand eine Schleife von "-Look down" aus, um zu leben, nach Ergebnissen zu suchen, zu warten, usw. Dieses resultierende Muster ist unbequem und sollte vermieden werden, indem Navigations Steuerelemente an einem zentralisierten Speicherort platziert werden, der weniger hin und her erfordert. Die Positionierung der Schaltflächen zum Verweilen in Bezug auf ihre Wirkung wird für den Tragekomfort wichtig.

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>Richtlinien und bewährte Methoden für die Benutzerumgebung

### <a name="target-sizes"></a>Zielgrößen
  Um auf einfache Weise zugänglich zu sein, müssen die Haupt-und zielziele groß genug sein, um sich bequem anzusehen und einen Head-stabilen auf dem Ziel für den vorgeschriebenen Zeitraum zu halten. Wir empfehlen eine minimale Zielgröße von 2 Grad, um die komfortablere Leistung zu erzielen. 

### <a name="visual-feedback"></a>Visuelles Feedback

Wenn Sie eine radiale Füllung zur Darstellung des Timers für das Verweilen verwenden, beginnen Sie in der Mitte der Schaltfläche. Eine konsistente Reaktion ist weniger irritierend als vollständig unterschiedliche Richtungen auf verschiedenen Schaltflächen. 

  * Diese Regel kann jedoch für direktionale Interaktionen (z. B. Navigation nach oben/unten/links/rechts usw.) missachtet werden. Microsoft Dynamics 365-Handbücher machen z. B. eine Ausnahme, wenn WEITER/ZURÜCK von links nach rechts ausgefüllt werden.
  * Erwägen Sie für Szenarien wie das Umschalten einer Schaltfläche, die radiale Füllung von außen zu invertieren. Das gegenläufige Gefühl beim Drücken einer Schaltfläche ist ein angenehmes visuelles Muster, das beibehalten werden sollte. 

### <a name="progressive-disclosure"></a>Schrittweise Offenlegung

„Schrittweise Offenlegung“ bedeutet, dass nur so viele Details angezeigt werden, wie in den einzelnen Phasen einer Interaktion relevant sind. Für das Verweilen bedeutet dies, dass das Verweilziel beim Hervorheben (z. B. in einem Listensteuerelement) offengelegt wird.

 ### <a name="oversized-targets"></a>Überdimensionale Ziele
Der Verweilbereich kann größer als das inaktive Symbol sein, um die Verwendung zu erleichtern, wie die Schaltfläche „Zurück“ in Microsoft Dynamics 365-Handbüchern.

### <a name="prevent-flickering-with-delayed-feedback"></a>Vermeiden von Flimmern durch verzögertes Feedback
Verwenden Sie eine kurze Verzögerung, bevor Sie mit dem visuellen Feedback beginnen, um ein Flimmern zu vermeiden, wenn ein Benutzer ein Verweilziel überquert.
* Halten Sie für Schaltflächen, mit denen häufig interagiert wird, die Verzögerung sehr kurz, damit die Anwendung reaktiv ist.
* Für Schaltflächen, die nur selten behandelt werden, kann eine längere Verzögerung sinnvoll sein, um die Schnittstelle zu vermeiden, die twitlapp ist.


<br>

---

## <a name="ui-patterns"></a>Muster der Benutzeroberfläche

### <a name="high-frequency-buttons"></a>Schaltflächen mit häufiger Interaktion

:::row:::
    :::column:::
        Schaltflächen mit hoher Frequenz sind Schaltflächen, die in der Regel in einer Anwendung verwendet werden. Ein gutes Beispiel hierfür sind die Schaltflächen „Weiter“ und „Zurück“ in Microsoft Dynamics 365-Handbüchern.<br>
        <br>
        **Empfehlungen**<br>
  * Die Schaltflächen mit hoher Frequenz sollten groß sein, und es ist einfacher, mit dem Kopf zu erreichen
  * Bleiben Sie in der Nähe der Augen, um eine ergonomische Überlastung zu vermeiden.<br>
        <br>
*Bild: Microsoft Dynamics 365 Guides Schaltfläche "weiter"*
    :::column-end:::
        :::column:::
       ![Schaltfläche "Microsoft Dynamics 365 Guides Next"](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Schaltflächen mit seltener Interaktion
Schaltflächen mit seltener Interaktion sind Schaltflächen, mit denen in der Anwendung nicht so häufig interagiert wird. Ein gutes Beispiel könnte eine Schaltfläche für den Zugriff auf das Einstellungsmenü oder eine Schaltfläche zum Löschen der gesamten Arbeit sein.

* Versuchen Sie, diese Schaltflächen von häufig genutzten Pfaden zum Anvisieren mit dem Kopf fernzuhalten, um eine versehentliche Aktivierung zu vermeiden. 

<br>

---

### <a name="confirmations"></a>Bestätigungen

:::row:::
    :::column:::
        Wenn eine Aktion erhebliche Auswirkungen hat, wie das Aufladen von Geld, das Löschen von Arbeit oder das Starten eines zeitintensiven Prozesses, ist es sinnvoll, die Auswahl einer Schaltfläche durch eine Person bestätigen zu lassen.<br>
        <br>
        **Empfehlungen**<br>
  * Auswahlhervorhebung auf Hauptschaltfläche anzeigen.
  * Verweilziel gleichzeitig mit der Auswahlhervorhebung anzeigen.
  * Verweilziel für die sekundäre Schaltfläche beim Anvisieren mit dem Kopf anzeigen.<br>
        <br>
*Bild: Microsoft Dynamics 365-Führungslinien Bestätigungs Dialogfeld*
    :::column-end:::
        :::column:::
       ![Bestätigungs Dialogfeld für Microsoft Dynamics 365-Anleitungen](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Umschalter
Umschalter erfordern eine differenzierte Logik, um ordnungsgemäß zu funktionieren. Wenn eine Person auf einem Umschalter verweilt und ihn aktiviert, muss sie die Schaltfläche verlassen und dann zurückkehren, um die Verweillogik neu zu starten. Es ist wichtig, dass die umschaltbaren Schaltflächen einen eindeutigen aktiven und inaktiven Zustand aufweisen. 

<br>

---

### <a name="list-views"></a>Listenansichten

:::row:::
    :::column:::
        Listenansichten stellen eine besondere Herausforderung für Kopf-und eingabeeingaben dar. Benutzer müssen in der Lage sein, den Inhalt zu scannen, ohne das Gefühl zu haben, dass sie sich in der Nähe der Verweilziele besonders vorsichtig bewegen müssen.<br>
        <br>
**Empfehlungen**<br>
  * Lassen Sie die ganze Zeile hervorheben, wenn Sie in den Kopf-und Ausgangspunkt steht
  * Zeigt nur das Ziel an, wenn die Zeile hervorgehoben wird, um das visuelle Rauschen zu verringern.
  * Sie sollten klar und konsistent mit der Position von "Dwell Targets" sein.
  * Zeigen Sie nicht alle Ziele auf einmal an, um sich wiederholende Benutzeroberflächen zu vermeiden.
  * Verwenden Sie das gleiche Muster so oft wie möglich, um die Benutzerfreundlichkeit der UX zu gewährleisten.<br>
        <br>
*Abbildung: Liste der Microsoft Dynamics 365-Leitfäden*
    :::column-end:::
        :::column:::
       ![Liste der Microsoft Dynamics 365-Leitfäden](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Weitere Informationen:
* [Blick und Commit](gaze-and-commit.md)
* [Bearbeitung von Hand direkt](direct-manipulation.md)
* [Handgesten](gaze-and-commit.md#composite-gestures)
* ["Hand Punkt" und "Commit"](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
