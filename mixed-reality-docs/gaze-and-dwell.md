---
title: Anvisieren mit dem Kopf und Verweilen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Verweilen“
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Verweilen, Interaktion, Entwurf
ms.openlocfilehash: d522ca3a6f36995959e8e6e87482279d05bf0aa3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387539"
---
# <a name="head-gaze-and-dwell"></a>Anvisieren mit dem Kopf und Verweilen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein. Sprachbefehle können wie Gesten in bestimmten Kontexten unzuverlässig sein, z. B. unter zu lauten Umgebungsbedingungen. Darüber hinaus ist der Einsatz der Stimme zur Steuerung von Computern nicht überall üblich, aber seine Bedeutung nimmt sicherlich zu. „Anvisieren mit dem Kopf und Verweilen“ bietet den bekanntesten und einfach zu bedienenden Mechanismus für das freihändige Heads-Up-Arbeiten mit der HoloLens. Darüber hinaus ist das Modell „Anvisieren mit dem Kopf und Verweilen“ unabhängig von Störgeräuschen und Ruheeinschränkungen in der Betriebssystemumgebung zu 100 % zuverlässig.

## <a name="scenarios"></a>Szenarien

„Anvisieren mit dem Kopf und Verweilen“ zeichnet sich durch Szenarien aus, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind und die Stimme aufgrund von Umgebungs- oder sozialen Einschränkungen nicht 100 % zuverlässig oder verfügbar ist. Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern. Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt. Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet. „Anvisieren mit dem Kopf und Verweilen“ ermöglicht es der Person, in der HoloLens sicher durch das Referenzmaterial zu navigieren, ohne den Workflow zu unterbrechen. 

## <a name="device-support"></a>Unterstützung von Geräten

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Verweilen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
    </tr>
</table>

## <a name="goals"></a>Ziele

Stellen Sie einen Mechanismus für völlig freihändige Interaktionen zur Verfügung, ohne die Stimme zu verwenden.

## <a name="design-principles"></a>Designprinzipien

1. Vermeiden Sie „Anvisieren als Waffe“

    „Anvisieren mit dem Kopf und Verweilen“ erfordert ein intuitives visuelles Feedback, aber zu viel Feedback kann beklemmend wirken. Das Feedback sollte einem Benutzer helfen sein Ziel zu erkennen, aber das Ziel nicht gegen seinen Willen automatisch auswählen. Das Lesen von Text, Symbolen und Beschriftungen erfordert eine zusätzliche Berücksichtigung, um einer Person den Raum zu geben, die Informationen vor der Auswahl zu erfassen.
    
2. Informationen zur Geschwindigkeit
    
    Verweilinteraktionen können je nach Auswirkung der Navigation unterschiedliche Timer aufweisen – häufiger verwendete Funktionen profitieren in der Regel von schnelleren Füllzeiten, während konsequentere Funktionen von längeren Füllzeiten profitieren können. Bei der Verwendung eines Fülleffekts zur Darstellung dieser Timer können Animationskurven der Füllfarbe das Gefühl schnellerer Füllzeiten positiv beeinflussen. Es sollte erwogen werden, dem Benutzer die Möglichkeit zu bieten, sich für eine schnelle, mittlere und langsame Füllgeschwindigkeit zu entscheiden.
    
3. Vermeiden von Jo-Jo-Effekten

    Der Jo-Jo-Effekt ist ein unangenehmes Muster der Kopfbewegung, das entstehen kann, wenn die Positionierung von Inhalten und die Steuerung durch „Anvisieren mit dem Kopf und Verweilen“ die Personen zwingt, ständig auf und ab zu schauen. Eine Listennavigation mit der Schaltfläche für „Anvisieren mit dem Kopf und Verweilen“ am unteren Rand bewirkt z. B. den folgenden Schleifenablauf: Zum Verweilen nach unten schauen, nach oben auf die Ergebnisse blicken, zum Verweilen nach unten schauen usw. Dieses resultierende Muster ist unangenehm und sollte vermieden werden, indem die Steuerelemente für die Navigation an einer zentralen Position platziert werden, die weniger Hin- und Herbewegung erfordert. Die Positionierung der Schaltflächen zum Verweilen in Bezug auf ihre Wirkung wird für den Tragekomfort wichtig.

## <a name="ux-guidelines-and-best-practices"></a>Richtlinien und bewährte Methoden für die Benutzerumgebung

### <a name="target-sizes"></a>Zielgrößen
  Um leicht zugänglich zu sein, müssen die Ziele für „Anvisieren mit dem Kopf und Verweilen“ zur komfortablen Zielbestimmung ausreichend groß sein und dabei den Kopf für die vorgeschriebene Zeit beständig auf dem Ziel halten. Es wird eine minimale Zielgröße von 2 Grad empfohlen, um ein möglichst komfortables Erlebnis zu erzielen. 

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
* Bei Schaltflächen mit häufiger Interaktion sollte die Verzögerung sehr kurz gehalten werden, damit die Anwendung einen reaktiven Eindruck macht.
* Bei Schaltflächen mit weniger häufiger Interaktion kann eine längere Verzögerung angemessen sein, um zu vermeiden, dass die Benutzeroberfläche unruhig wirkt.

## <a name="ui-patterns"></a>Muster der Benutzeroberfläche

### <a name="high-frequency-buttons"></a>Schaltflächen mit häufiger Interaktion
![Schaltfläche Microsoft Dynamics 365 Guides Next](images/GuideNextButton.png "Schaltfläche \"Microsoft Dynamics 365 Guides Next")<br>
*Schaltflächen mit hoher Frequenz sind Schaltflächen, die in der Regel in einer Anwendung verwendet werden. Ein gutes Beispiel hierfür sind die Schaltflächen "weiter" und "zurück" in Microsoft Dynamics 365 Guides.*

Merkmale von Schaltflächen mit häufiger Interaktion:
* Es sollte sich um größere Schaltflächen handeln, die beim Anvisieren mit dem Kopf leichter zu treffen sind.
* Sie sollten auf Augenhöhe verbleiben, um ergonomische Belastungen zu vermeiden.

### <a name="low-frequency-buttons"></a>Schaltflächen mit seltener Interaktion
Schaltflächen mit seltener Interaktion sind Schaltflächen, mit denen in der Anwendung nicht so häufig interagiert wird. Ein gutes Beispiel könnte eine Schaltfläche für den Zugriff auf das Einstellungsmenü oder eine Schaltfläche zum Löschen der gesamten Arbeit sein.

* Versuchen Sie, diese Schaltflächen von häufig genutzten Pfaden zum Anvisieren mit dem Kopf fernzuhalten, um eine versehentliche Aktivierung zu vermeiden. 

### <a name="confirmations"></a>Bestätigungen
![Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher](images/GuidesConfirmation.png "Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher")

Wenn eine Aktion erhebliche Auswirkungen hat, wie das Aufladen von Geld, das Löschen von Arbeit oder das Starten eines zeitintensiven Prozesses, ist es sinnvoll, die Auswahl einer Schaltfläche durch eine Person bestätigen zu lassen. Für Benutzeroberflächenelemente zum Anvisieren mit dem Kopf und Verweilen gibt es einige Muster und Überlegungen für Bestätigungsdialogfelder:

  * Auswahlhervorhebung auf Hauptschaltfläche anzeigen.
  * Verweilziel gleichzeitig mit der Auswahlhervorhebung anzeigen.
  * Verweilziel für die sekundäre Schaltfläche beim Anvisieren mit dem Kopf anzeigen.
        
### <a name="toggle-buttons"></a>Umschalter
Umschalter erfordern eine differenzierte Logik, um ordnungsgemäß zu funktionieren. Wenn eine Person auf einem Umschalter verweilt und ihn aktiviert, muss sie die Schaltfläche verlassen und dann zurückkehren, um die Verweillogik neu zu starten. Es ist wichtig, dass die umschaltbaren Schaltflächen einen eindeutigen aktiven und inaktiven Zustand aufweisen. 

### <a name="list-views"></a>Listenansichten
![Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher](images/GuidesListView.png "Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher")<br>
*Listenansichten stellen eine besondere Herausforderung für Kopf-und eingabeeingaben dar. Personen müssen die Inhalte scannen können, ohne dass Sie sich so fühlen müssen, dass Sie die zielziele kippen müssen.*

Einige Tipps zum Entwerfen von Listenansichten:
* Beim Anvisieren mit dem Kopf die gesamte Zeile hervorheben, aber erst mit dem Verweilen beginnen, wenn das Anvisieren mit dem Kopf ein bestimmtes Verweilziel erreicht hat.
* Das Verweilziel nur anzeigen, wenn die Zeile hervorgehoben ist, um visuelle Störungen zu reduzieren.
* Mit der Position der Verweilziele eindeutig und konsistent sein.
* Nicht alle Verweilziele auf einmal anzeigen, um wiederholte Benutzeroberflächenelemente zu vermeiden.
* Dasselbe Muster so oft wie möglich wiederverwenden, um die Vertrautheit mit der Benutzerumgebung herzustellen.
 
 ## <a name="see-also"></a>Siehe auch
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Sprachbefehle](voice-design.md)
