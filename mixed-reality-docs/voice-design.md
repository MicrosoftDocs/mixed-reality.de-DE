---
title: Sprachbefehle
description: Anvisieren, Gesten und Sprache sind primäre Möglichkeiten zur Interaktion für die HoloLens. Dieser Artikel bietet eine durchdachte Anleitung zum Sprachentwurf.
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Interaktion, Sprache
ms.openlocfilehash: 724ef87dae1c731289af51504a518193c20b7d96
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387643"
---
# <a name="voice-commanding"></a>Sprachbefehle

Bei der Verwendung von Sprachbefehlen wird das Anvisieren typischerweise als Mechanismus zur Zielbestimmung verwendet, sei es als Zeiger („auswählen“) oder um Ihren Befehl an eine Anwendung zu richten („Sehen, sagen“). Natürlich benötigen einige Sprachbefehle kein Ziel, wie „Zum Startmenü“ oder „Hey Cortana“.


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
        <td>Sprachbefehle</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (mit angeschlossenem Headset)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>Verwendung der Spracheingabe

Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen. Die Spracheingabe ist eine leistungsstarke und komfortable Möglichkeit zur Steuerung von System und Apps. Da Benutzer mit einer Vielzahl von Dialekten und Akzenten sprechen, stellt die richtige Auswahl der Schlüsselwörter für die Spracherkennung sicher, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.

### <a name="best-practices"></a>Empfohlene Methoden

Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.
* **Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus. Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden. Beispiel: „Video wiedergeben“ ist besser als „Das aktuell ausgewählte Video wiedergeben“.
* **Einfaches Vokabular verwenden** – Beispiel: „Hinweis anzeigen“ ist besser als „Plakat anzeigen“.
* **Sicherstellen, dass Befehle nicht destruktiv sind**: Stellen Sie sicher, dass alle Aktionen, die von einem Spracherkennungsbefehl ausgeführt werden können, nicht destruktiv sind und leicht rückgängig gemacht werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.
* **Ähnlich klingende Befehle vermeiden**: Vermeiden Sie es, mehrere Spracherkennungsbefehle zu registrieren, die sehr ähnlich klingen. Beispiel: „Show more“ (Mehr anzeigen) und „Show store“ (Shop anzeigen) können z. B. sehr ähnlich klingen.
* **Registrierung der App aufheben, wenn sie nicht verwendet wird**: Wenn sich Ihre Anwendung nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung der App aufheben, damit andere Befehle nicht mit diesem verwechselt werden.
* **Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.
* **Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.
* **Verwendung von Systembefehlen vermeiden**: Die folgenden Sprachbefehle sind für das System reserviert. Diese sollten nicht von Anwendungen verwendet werden.
   * „Hey Cortana“
   * „Auswählen“

### <a name="select"></a>„Auswählen“

Wenn Sie zu einem beliebigen Zeitpunkt „Auswählen“ sagen, wird das aktiviert, worauf der beim Anvisieren verwendete Cursor zeigt. 

>Hinweis: In HoloLens 2 muss der beim Anvisieren verwendete Cursor zunächst mit dem Wort „Auswählen“ aufgerufen werden. Sagen Sie zum Aktivieren erneut „Auswählen“. Um den beim Anvisieren verwendeten Cursor auszublenden, verwenden Sie Ihre Hände – Berühren Sie ein Objekt, oder tippen Sie in die Luft. 

### <a name="see-it-say-it"></a>Sehen, sagen

Windows Mixed Reality hat ein „Sehen, sagen“-Sprachmodell eingesetzt, bei dem **Beschriftungen auf Schaltflächen mit den zugehörigen Sprachbefehlen identisch sind**. Da es keine Missverständnisse zwischen Beschriftung und Sprachbefehl gibt, können Benutzer besser verstehen, was sie sagen müssen, um das System zu steuern. Um dies zu verstärken, wird beim Verweilen auf einer Schaltfläche ein **Tipp zum Verweilen** angezeigt, um mitzuteilen, welche Schaltflächen sprachaktiviert sind.


![Sehen, sagen – Beispiel 1](images/voice-seeitsayit1-640px.jpg)

![Sehen, sagen – Beispiel 2](images/voice-seeitsayit2-640px.jpg)<br>
*Beispiele für „Sehen, sagen“*

### <a name="voices-strengths"></a>Vorteile der Spracheingabe

Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren. Die Spracheingabe ist besonders gut bei den **Übergängen** von Schnittstellen geeignet, da sie den Benutzern helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen (ein Benutzer könnte „Zurück“ sagen, während er eine Webseite betrachtet, anstatt in der App zum Seitenanfang zu wechseln und die Schaltfläche „Zurück“ zu betätigen). Diese kleine Zeitersparnis hat einen starken **emotionalen Effekt** auf die Wahrnehmung der Umgebung für den Benutzer und verleiht ihm eine gewisse „Kraft“. Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen. Auf Geräten, bei denen die Eingabe über eine Tastatur schwierig ist, kann das **Sprachdiktat** eine effiziente Eingabealternative sein. In einigen Fällen, wenn der **Genauigkeitsbereich** für Anvisieren und Gesten begrenzt ist, könnte die Spracheingabe schließlich die einzige vertrauenswürdige Eingabemethode eines Benutzers sein.

**Vorteile der Spracheingabe für den Benutzer**
* Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.
* Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.
* Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.
* Sie ist sozialverträglich – sie sollte sich in Bezug auf das Verhalten in die gesellschaftlichen Normen einfügen.
* Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.

### <a name="voices-weaknesses"></a>Nachteile der Spracheingabe

Die Spracheingabe weist auch einige Schwächen auf. Eine davon ist die differenzierte Steuerung. (Ein Benutzer kann z. B. „lauter“ sagen, aber nicht angeben, wie viel lauter es sein soll.) „Etwas“ ist schwer zu quantifizieren. Das Bewegen oder Skalieren von Objekten per Spracheingabe ist ebenfalls schwierig (die Spracheingabe bietet nicht die Genauigkeit bei der Steuerung). Die Spracheingabe kann auch unvollkommen sein. Gelegentlich hört ein Spracheingabesystem einen Befehl falsch oder überhaupt nicht. Die Wiederherstellung nach solchen Fehlern stellt für jede Schnittstelle eine Herausforderung dar. Schließlich ist die Spracheingabe an öffentlichen Orten möglicherweise nicht gesellschaftsfähig. Es gibt einige Dinge, die Benutzer nicht sagen können oder sollten. Diese Hindernisse ermöglichen es, die Spracherkennung dafür zu nutzen, wofür sie am besten geeignet ist.

### <a name="voice-feedback-states"></a>Statusangaben für Spracherkennungsfeedback

Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**. Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann. Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.

![Statusangaben für Spracherkennungsfeedback für Cursor](images/voicefeedbackstates.png)<br>
*Statusangaben für Spracherkennungsfeedback für Cursor*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Wichtige Informationen zur Spracherkennung in Mixed Reality
* Sagen Sie **„Auswählen“** , während Sie eine Schaltfläche anvisieren (Sie können dies überall verwenden, um auf eine Schaltfläche zu klicken).
* Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen. Beim Betrachten einer App kann ein Benutzer z. B. den Befehl „Entfernen“ sagen, um die App aus der Umgebung zu entfernen (das spart Zeit, da die App nicht mit der Hand angeklickt werden muss).
* Sie können initiieren, dass Cortana zuhört, indem Sie **„Hey Cortana“** sagen. Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe
* Was kann ich sagen?
* Woher weiß ich, ob das System mich richtig verstanden hat?
   * Das System versteht meine Sprachbefehle immer wieder falsch.
   * Es reagiert nicht, wenn ich einen Sprachbefehl erteile.
* Es reagiert falsch, wenn ich einen Sprachbefehl erteile.
* Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?
* Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?

## <a name="see-also"></a>Siehe auch
* [Gesten](gestures.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
