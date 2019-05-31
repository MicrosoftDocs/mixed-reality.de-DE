---
title: Voice-Befehle
description: Blicke, Gesten und Stimme (GGV) sind das primäre Mittel der Interaktion bei HoloLens. Dieser Artikel enthält eine gut durchdachte Anleitungen Voice-Entwurf.
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, entwerfen, die Interaktion, die Stimme
ms.openlocfilehash: f2362400cba2946c3e97a7128c410ddcd17b4362
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402371"
---
# <a name="voice-commanding"></a>Voice-Befehle

Wenn Sie Sprachbefehle zu verwenden, Blicke ist in der Regel als die Zielgruppenadressierung anhand bestimmter Mechaninism, ob als Zeiger verwendet ("Select") oder leiten Sie den Befehl zu einer Anwendung ("angezeigt, das so sagen"). Einige Sprachbefehle erforderlich nicht natürlich ein Ziel, wie "Gehe um zu starten" oder"Hey Cortana.".


## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>Voice-Befehle</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (mit Kopfhörer angeschlossen)</td>
</tr>
</table>



## <a name="how-to-use-voice"></a>Gewusst wie: Verwenden von Stimme

Sollten Sie über Erfahrungen, die Sie erstellen Sprachbefehle hinzufügen. Voice ist eine leistungsfähige und bequeme Möglichkeit steuern, das System und Anwendungen. Da Benutzer mit einer Vielzahl von Dialekte und Akzente sprechen, stellt geeignete Wahl Schlüsselwörter der Sprache sicher, dass es sich bei Ihrer Benutzer Befehle eindeutig interpretiert werden.

### <a name="best-practices"></a>Empfohlene Methoden

Im folgenden sind einige Methoden, die smooth-Spracherkennung Remotesysteme werden.
* **Verwenden Sie präzise Befehle** – Wenn möglich ist, wählen Sie die Schlüsselwörter von zwei oder mehr Silben. Einsilbiges Wörter dazu neigen, verschiedene Vokalen während von Personen, die von anderen Akzenten gesprochen zu verwenden. Beispiel: "Video abspielen" ist besser, als "das derzeit ausgewählte Video wiedergeben"
* **Verwenden Sie einfache Vokabular** -Beispiel: "Hinweis anzeigen" ist besser als "Placard anzeigen"
* **Stellen Sie sicher, dass die Befehle sind nicht** – sicherzustellen, dass alle Aktionen, die von einem Speech-Befehl ausgeführt werden kann, ist nicht zerstörerische und können einfach nicht rückgängig gemacht werden für den Fall, dass eine andere Person sprechen in der Nähe des Benutzers versehentlich einen Befehl auslöst.
* **Vermeiden Sie ähnlich klingende Befehle** -Registrierung mehrerer gesprochene Befehle, die sehr ähnlich klingen zu vermeiden. Beispiel: "Mehr anzeigen" und "Anzeigen Store" können sehr ähnlich klingende sein.
* **Heben Sie die Registrierung Ihrer app, wenn es nicht verwenden,** : Wenn Ihre app nicht in einem Zustand befindet, in dem ein Sprachbefehl bestimmte gültig ist, sollten Sie die Registrierung wird aufgehoben, damit andere Befehle nicht eine verwechselt werden.
* **Test mit verschiedenen Akzenten** – Testen Ihrer app für Benutzer von anderen Akzenten.
* **Voice-Befehl Konsistenz beizubehalten,** : Wenn "Zurück", die zur vorherigen Seite, werden dieses Verhalten in Ihren Anwendungen verwalten.
* **Vermeiden Sie die Verwendung von Systembefehle** -sind die folgenden Sprachbefehle für das System reserviert. Diese sollten nicht von Anwendungen verwendet werden.
   * "Hey Cortana"
   * "Auswählen"

### <a name="select"></a>"Auswählen"

Sagen "select" zu einem beliebigen Zeitpunkt wird aktiviert, was die Blicke Cursor zeigt. 

>Hinweis: HoloLens-2 Wählen"Sie in der Blicke Cursor muss zuerst aufgerufen werden, indem Sie das Wort". Angenommen, "select" erneut um zu aktivieren. Um den Cursor Blicke auszublenden, verwenden Sie die Hände – Airtap oder tippen Sie auf ein Objekt. 

### <a name="see-it-say-it"></a>Anzeigen, das so sagen

Windows Mixed Reality verfügt über ein "angezeigt, das so sagen" Voice-Modell eingesetzt, in denen **Bezeichnungen auf Schaltflächen sind identisch mit den zugehörigen Sprachbefehle**. Da übergeordnete zwischen der Bezeichnung und der Sprachbefehl nicht, können Benutzer was an, dass das System So kontrollieren besser verstehen. Zu diesem vertiefen, während auf eine Schaltfläche, Einstichs eine **"Stimme länger aufhalten Tipp"** angezeigt, die für die Kommunikation, welche Schaltflächen werden Sprache aktiviert wird.


![Sehen Sie es noch einmal von Beispiel 1](images/voice-seeitsayit1-640px.jpg)

![Sehen Sie es noch einmal von Beispiel 2](images/voice-seeitsayit2-640px.jpg)<br>
*Beispiele für "angezeigt, das so sagen"*

### <a name="voices-strengths"></a>Voice Vorteile

Spracheingabe ist eine natürliche Möglichkeit, unser Absichten zu kommunizieren. Voice ist besonders gut für die Schnittstelle **traversierungen** denn sie können Benutzern senken, über mehrere Schritte einer Schnittstelle (ein Benutzer kann z. B. "zurück" bei der Suche auf der Webseite, anstatt zu einrichten, und drücken Sie die Schaltfläche "zurück", in der app). Diese kleine Zeitersparnis ist eine leistungsfähige **emotionaler Auswirkungen** für Benutzer der Wahrnehmung der Umgebung, und erhalten sie eine kleine Menge boosten. Voicemail ist auch eine praktische Methode für die Eingabe, wenn wir wir die vollständige Arme haben oder **Multitasking**. Auf Geräten, auf einer Standardtastatur eingeben schwierig ist, **voice-Diktat** kann eine effiziente Alternative zur Eingabe sein. Und schließlich in einigen Fällen bei der **Bereich der Genauigkeit** für Blicke und Gesten beschränkt sind, Sprache möglicherweise eines Benutzers ausschließlich vertrauenswürdige Methode, die Eingabe.

**Wie den Benutzer per Spracheingabe profitieren können**
* Verringert Zeit – es sollte das endgültige Ziel effizienter gestalten.
* Wird der Aufwand - minimiert hergestellt werden soll Aufgaben flüssiger und sorgen.
* Reduziert cognitive-Last – es ist, intuitiv und einfach Informationen und denken Sie daran.
* Social akzeptabel ist – er sollte mit dem quantumcomputing Normen in Bezug auf Verhalten passen.
* Es handelt sich um Routine - Voice kann leicht einen gewöhnlichen Verhalten werden.

### <a name="voices-weaknesses"></a>Voice Schwächen

Voice hat auch einige Schwächen. Eine präzisere Kontrolle gehört dazu. (z. B. ein Benutzer könnte "lauter", aber nicht sagen, wie viel. "Etwas" ist Quantifizierung schwierig. Verschieben oder Dinge mit Stimme Skalierung ist es schwieriger (Voice bietet nicht die Granularität des Steuerelements). Voice kann auch perfekt sein. Ein Voice-System wird manchmal fälschlicherweise hört einen Befehl, oder der ein Fehler auftritt, einen Befehl zu hören. Wiederherstellen von solche Fehler ist eine Herausforderung in einer beliebigen Schnittstelle. Abschließend Voice Social akzeptable an öffentlichen Orten möglicherweise nicht. Es gibt einige Dinge, die Benutzer haben und sollte nicht sagen können. Diese Felsen können für die Spracherkennung verwendet werden, für was am besten ist.

### <a name="voice-feedback-states"></a>Voice-Feedback-Status

Wenn Voice ordnungsgemäß angewendet wird, wird der Benutzer versteht **was sie sagen und erzielen können rückmeldungen** das System **haben sie richtig gehört**. Diese zwei Signale stellen den Benutzer, die bei der Verwendung von Sprach als eine primäre Eingabe darauf vertrauen können. Im folgenden finden, dass das Diagramm zeigt, was geschieht, den Cursor, wenn Spracheingabe erkannt wird und wie es, die für den Benutzer kommuniziert.

![Voice-Feedback-Zustände für cursor](images/voicefeedbackstates.png)<br>
*Voice-Feedback-Zustände für cursor*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Top-Aufgaben, die Benutzer sollten über "Speech" in mixed Reality wissen.
* Sagen Sie **"Select"** beim Abzielen auf eine Schaltfläche (Hiermit können Sie überall auf eine Schaltfläche klicken).
* Angenommen, Sie können die **Bezeichnungsnamen einer app-Leiste Schaltfläche** in einigen apps aus, um eine Aktion auszuführen. Bei der Suche auf eine app, kann ein Benutzer beispielsweise den Befehl "Entfernen" zum Entfernen der app auf der ganzen Welt (Dies spart Zeit erspart, um mit der Hand auf diese Schaltfläche klicken).
* Können Sie Cortana Lauschen durch Spruch initiieren **"Hey Cortana".** Sie können ihre Fragen ("Hey Cortana, wie hoch ist von der Eiffel Tower"), sage zum Öffnen einer app ("Hey Cortana, open Netflix") oder sage, rufen Sie im Startmenü ("Hey Cortana, Take mich home") und vieles mehr.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Allgemeine Fragen und Probleme Benutzer verfügen über Stimme
* Was soll ich sagen?
* Wie weiß ich, dass das System, die mich richtig gehört?
   * Das System ständig Meine Sprachbefehle falsch.
   * Es reagieren nicht, wenn ich einen Sprachbefehl erteilen.
* Es reagiert die falsche Methode, wenn ich einen Sprachbefehl erteilen.
* Wie werden meine Stimme an eine bestimmte app oder app-Befehl ausgerichtet?
* Kann ich stimme, Befehl Sachen da draußen holographic Frames für HoloLens verwenden?

## <a name="see-also"></a>Siehe auch
* [Gesten](gestures.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
