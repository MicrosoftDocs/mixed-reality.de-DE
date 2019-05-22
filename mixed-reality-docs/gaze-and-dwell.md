---
title: Head-Blicke und dwell
description: Übersicht über das Head-Blicke und Dwell Eingabemodell
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität Blicke, Dwell, Interaktion, Entwerfen
ms.openlocfilehash: aa4713407f14e94c88e654ae6648c4949f98e580
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974866"
---
# <a name="head-gaze-and-dwell"></a>Head-Blicke und Dwell

Wenn praktische Tools und Komponenten belegt sind, können die Gesten mühsam oder unmöglich sein. Voice-Befehle, wie Bewegungen können in bestimmten Kontexten, z. B. unter übermäßig laut Bedingungen unzuverlässig. Darüber hinaus Stimme, die Control-Computer ist nicht universell häufig, jedoch ist sicherlich Datenstrom gewinnen! Head-Blicke und Dwell bietet den meistverwendeten und einfachen Master-Mechanismus für die Arbeit heads-up und physisch auf HoloLens. Darüber hinaus Head-Blicke und Dwell ist 100-prozentige Zuverlässigkeit unabhängig von Rauschen Störungen noch Ruhe-Einschränkungen in der betriebsumgebung.

## <a name="scenarios"></a>Szenarien

Head-Blicke und Dwell lassen sich besonders in Szenarien, in denen einer Person Hände sind mit anderen Aufgaben ausgelastet und stimme nicht bei 100 % zuverlässig oder aufgrund von environmental oder soziale Netzwerke verfügbar. Ein gutes Beispiel ist eine Person, die eine HoloLens um Referenzinformationen beim Reparieren einer Auto-Engine zu überlagern trägt. Der Hand, die mit Tools oder ihren Text unterstützt, wie sie in der Depot-Engine-erfahren Sie, ausgelastet sind. Die Garage-Speicherplatz ist laut, mit der Konstanten, die diesem und Summen von Tools bereit, sodass Sprachbefehle schwierig. Head-Blicke und Dwell ermöglicht dem Mitarbeiter in die HoloLens zuverlässig auf ihre Referenzmaterial ohne Sicherungsstatus navigieren Workflow. 

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td>Head-Blicke und dwell</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
    </tr>
</table>

## <a name="goals"></a>Ziele

Stellen Sie einen Mechanismus zum vollständig freisprechgeräte Interaktionen, ohne Verwendung von Stimme an.

## <a name="design-principles"></a>Designprinzipien

1. Vermeiden Sie "Als Waffe bestaunen"

    Head-Blicke und Dwell erfordert visuelles Feedback intuitiv sein, aber viel Feedback kann hegen auslösen. Das Feedback tragen, dass einen Benutzer wissen, was sie abzielen, jedoch keine automatische Auswahl sie für ihre Absichten. Lesen von Text, Symbole und Bezeichnungen erfordert zusätzliche Überlegung, um eine Person Platz um die Informationen vor der Auswahl der absorb zu schaffen.
    
2. Seek-Goldlöckchen Geschwindigkeit
    
    Dwell Interaktionen können verschiedene Zeitgeber, die basierend auf Auswirkung der Navigation haben – häufig verwendete Funktionen profitieren davon, in der Regel schnellere ausfüllen, während mehr Fill-Mal mehr Folgeschäden Funktionen profitieren können. Wenn Sie einen Fülleffekt verwenden diese Timer angezeigt, können die Animation Kurven der Füllfarbe werde, positiv einen Eindruck, schnellere Füllung beeinflussen. Berücksichtigt sind, um die Entscheidung des Benutzers aus Fast/Mittel/langsame aktivieren Geschwindigkeit Außerkraftsetzungen zu füllen.
    
3. Sagen Sie forschungspseudocode zu Yo-yo Auswirkung

    Die Yo-yo Auswirkung ist eine bedauernswerte Muster Bewegungen, die entstehen kann, wenn die Platzierung von Steuerelementen von Inhalt und Head-Blicke und Dwell erzwingt, Personen dass, ständig nach oben und unten wiederholt zu suchen. Eine Liste Navigationsbereich mit der Head-Blicke und Dwell-Schaltfläche am unteren Rand werden z. B. eine Schleife von - Suchen nach unten um länger aufhalten, sehen Sie sich auf Ergebnisse zu erzielen, Suchen nach unten länger aufhalten, usw. ausgelöst. Dieses resultierende Muster unangenehm ist, und sollte vermieden werden, indem Sie die Navigationssteuerelemente an einem zentralen Ort, der kleiner hin und her erfordert platzieren. Platzierung von Dwell Schaltflächen relativ zu deren Auswirkungen wichtig für Komfort.

## <a name="ux-guidelines-and-best-practices"></a>UX-Richtlinien und bewährte Methoden

### <a name="target-sizes"></a>Zielgrößen
  Um leicht zugänglich zu sein, Head-Blicke und länger aufhalten Sie Ziele muss groß genug, um Comforatably Ziel, und halten Sie die Head stabily auf dem Ziel der vorgegebenen Zeit. Es wird empfohlen, eine Mindestversion der Zielplattform Größe von 2 Grad um die am besten vertraut Erfahrung zu erzielen. 

### <a name="visual-feedback"></a>Visuelles Feedback

Wenn eine radiale Füllung zur Darstellung des Dwell Timers verwenden, starten Sie aus der Mitte der Schaltfläche. Eine konsistente Antwort ist weniger verwirrend, als alle anderen Anweisungen für verschiedene Schaltflächen. 

  * Mit dieser Regel kann jedoch für den direktionalen Interaktionen (z. B. Nav nach-oben/nach unten/links/rechts, usw.) unterbrochen werden. Z. B. Microsoft Dynamics 365-Handbücher wird eine Ausnahme weiter/Back verlassene rechts gefüllt.
  * Betrachten Sie invertieren radiale Füllen von außerhalb für Szenarien wie das Umschalten einer Schaltfläche deaktiviert. Die inverse Eindruck, eine Schaltfläche ist ein praktisches visual Muster zu verwalten. 

### <a name="progressive-disclosure"></a>Schrittweise Anzeige von

Schrittweise Anzeige von bedeutet, dass nur angezeigt, so viele Details wie in den einzelnen Phasen einer Interaktion relevant ist. Für Dwell bedeutet dies, dass es sich bei Ziel Dwell Hervorhebung (z. B. in einem Listensteuerelement) offengelegt wird.

 ### <a name="oversized-targets"></a>Übergroße Ziele
Dwell Region kann größer als inaktiv Symbol zu vereinfachen, verwenden Sie, wie die zurück-Taste in Microsoft Dynamics 365-Handbüchern sein.

### <a name="prevent-flickering-with-delayed-feedback"></a>Bildflimmern bei verzögerten Feedback zu verhindern, dass
Verwenden Sie eine kurze Verzögerung vor dem Starten von visuellen Feedbacks, um zu vermeiden, Flimmern verursachte, wenn ein Benutzer über ein Ziel Dwell bewegt.
* Behalten Sie für Schaltflächen Inteacted mit häufig die sehr kurze Verzögerung ein, damit die Anwendung reaktive fühlt.
* Für Schaltflächen, die mit Infrequenctly interagiert werden kann eine längere Verzögerung Approprate vermeiden Sie die Schnittstelle empfunden twitchy sein.

## <a name="ui-patterns"></a>UI-Muster

### <a name="high-frequency-buttons"></a>Hohe Auslastung Schaltflächen
![Microsoft Dynamics 365 Handbücher Schaltfläche "Weiter"](images/GuideNextButton.png "Microsoft Dynamics 365 Handbücher Schaltfläche \"Weiter\"") sehr häufig befinden sich Schaltflächen, die häufig in der gesamten Anwendung verwendet werden. Ein gutes Beispiel für diese sind die Schaltflächen weiteren und zurück in Microsoft Dynamics 365-Handbücher.

Hohe Auslastung Schaltflächen sollten...
* größere Schaltflächen, leichter mit Head-Blicke erreicht werden
* bleiben Sie in der Nähe der Höhe Eye ergonomische Service zu vermeiden.

### <a name="low-frequency-buttons"></a>Niedrige Auslastung von Schaltflächen
Niedrige Auslastung befinden Schaltflächen, die nicht mit in der gesamten Anwendung als regelmäßig interagiert werden. Ein gutes Beispiel ist möglicherweise eine Schaltfläche auf das Menü "Einstellungen" oder eine Schaltfläche, um alle Aufgaben löschen.

* Versuchen Sie es, zu diese Schaltflächen Bildschirmen häufig Head-Blicke-Pfade, um die versehentliche Aktivierung zu vermeiden. 

### <a name="confirmations"></a>Bestätigungen
![Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher](images/GuidesConfirmation.png "Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher")

Wenn eine Aktion entscheidenden Einfluss, wie Gebühren Geld, löschen die Arbeit oder Starten eines Prozesses lange hat ist es hilfreich, um zu bestätigen, dass eine Person eine Schaltfläche auswählen. Sind für Head-Blicke und Dwell Benutzeroberflächen gibt es einige Muster und Überlegungen zu den Dialogfeldern zur Bestätigung:

  * Enthält die Markierung der Hauptschaltfläche.
  * Anzeigen länger Ziel gleichzeitig Markierung der aufhalten.
  * Für die sekundären Schaltfläche offen legen Sie Dwell Zielstatus auf Head-Blicke.
        
### <a name="toggle-buttons"></a>Umschaltflächen
Umschaltflächen erfordern einige Nachteile Logik ordnungsgemäß funktioniert. Wenn eine Person auf eine Umschaltfläche und aktive aufdecken möchten, müssen sie die Schaltfläche zum Beenden und dann zurück, um die Logik Dwell neu zu starten. Es ist wichtig, das ein-/ausschaltbaren Schaltflächen eine klare aktiv im Vergleich zu den inaktiven Status aufweisen. 

### <a name="list-views"></a>Listenansichten
![Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher](images/GuidesListView.png "Bestätigungsdialogfeld für Microsoft Dynamics 365-Handbücher") Listenansichten stellen eine besondere Herausforderung für Head-Blicke und länger aufhalten Eingabe. Benutzer müssen in der Lage, überprüfen den Inhalt ohne empfunden, die rund um die Ziele Dwell tiptoe müssen. 

Tipps zum Entwerfen von Ansichten aufzulisten:
* haben Sie die gesamte Zeile markieren, wenn Head-gazed jedoch auf der Ziel-spezifische Dwell sei Head-Blicke Dwell beginnt nicht an.
* Das Ziel Dwell nur angezeigt, wenn die Zeile hervorgehoben wird, um auf diese ganzen visuellen Störungen zu verkürzen.
* Löschen und mit die Position des Dwell Ziele konsistent sein.
* Zeigen Sie nicht mehr an, dass alle Ziele auf einmal zur Vermeidung von Benutzeroberfläche länger aufhalten
* Verwenden Sie das gleiche Muster erneut so oft wie möglich zum Herstellen von UX-Kenntnisse
 
 ## <a name="see-also"></a>Siehe auch
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Sprachbefehle](voice-design.md)
