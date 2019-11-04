---
title: Freisprechen
description: Optimieren Ihrer APP für praktische Übungen
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Gemischte Realität, Hände frei, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435074"
---
# <a name="hands-free"></a>Freisprechen

## <a name="scenarios"></a>Szenarien

Wie in der [Übersicht über das Interaktionsmodell](interaction-fundamentals.md)erläutert, stellen Sie nach der Identifizierung Ihrer Benutzer und ihrer Ziele selbst fest, welche Umgebungs-oder situations Probleme bei der Ausführung ihrer Aufgaben auftreten können. Beispielsweise müssen viele Benutzer ihre Hand haben, um Ihre tatsächlichen Ziele zu erreichen, und Sie haben Schwierigkeiten beim interagieren mit einer auf der Hand-und Controller basierten Schnittstelle. 

Einige bestimmte Szenarien umfassen Folgendes: 
* Sie werden durch eine Aufgabe geleitet, während die Hände des Benutzers ausgelastet sind.
* Referenzierende Materialien, während die Benutzer Hände ausgelastet sind
* Hand Müdigkeit
* Handschuhe, die nicht überwacht werden können
* Praktische Ausführung
* Soziale Unbekümmertheit zum Durchführen von großen Handgesten
* Enge Leerzeichen


## <a name="hands-free-modalities"></a>Hände freie Modalitäten

### <a name="voice-inputvoice-inputmd"></a>[Spracheingabe](voice-input.md)

Die Verwendung Ihrer Stimme für die Befehls-und Steuerungsmöglichkeiten einer Schnittstelle bietet eine bequeme Möglichkeit, die Hände frei zu betreiben und Verknüpfungen zu verwenden, um mehrere Schritte bei Bedarf flexibel zu überspringen. Mit der Spracheingabe kann der Benutzer einfach den Namen einer beliebigen Schaltfläche mit dem Namen "Loud" lesen, um ihn zu aktivieren _("anzeigen, sagen Sie")_ und sich mit einem Digital Agent abgleichen, der Aufgaben für Sie erledigen kann.


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[Anvisieren und Verweilen](gaze-and-dwell.md)

In einigen praktischen Situationen ist die Verwendung Ihrer Stimme nicht ideal oder gar nicht möglich. Laute Factory-Umgebungen, Datenschutz oder soziale Standards können Einschränkungen aufweisen. Mit dem "Eye + Dwell"-Modell kann der Benutzer durch eine APP navigieren, ohne dass zusätzliche Eingaben von der Augen-oder Kopfzeile entfernt werden: der Benutzer wird einfach im Ziel angezeigt (mit seinen Köpfen oder Augen), und er wird für einen Moment darauf gewartet, ihn zu aktivieren. Weitere Informationen zu den einzelnen Entwurfs Überlegungen für "Blick" und "Wohnen" finden Sie unter " [Eye-Eye](gaze-and-dwell-eyes.md) " und "Wohnen" und " [Kopf-](gaze-and-dwell-head.md)und neben schauen"


## <a name="transitioning-in-and-out-of-hands-free"></a>Wechsel in und aus der Praxis freie Umstellung

In diesen Szenarien kann die Interaktion mit holograms für die Befehls-und Navigations Phase von einer absoluten Anforderung bis zum Ende des Betriebs der Anwendung bis zum Ende reichen, bis zu einer zusätzlichen Benutzererfahrung, von der der Benutzer jederzeit und von allen Zeit. 

Wenn die Anforderung der Anwendung ist, dass Sie immer mit der Hand frei verwendet wird, egal ob mithilfe von "Dwell", benutzerdefinierten Sprachbefehlen oder mit dem Befehl "Select", dann stellen Sie sicher, dass Sie die entsprechenden Unternehmen in Ihrer Benutzeroberfläche vornehmen. 

Wenn Ihr Ziel Benutzer in der Lage sein muss, nach eigenem Ermessen von Hand zu Hand zu wechseln, ist es wichtig, dass Sie die folgenden Prinzipien berücksichtigen.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Gehen Sie davon aus, dass der Benutzer bereits im Modus ist, zu dem gewechselt werden soll.
Wenn sich der Benutzer beispielsweise auf der Werks Seite befindet, sehen Sie sich einen Video Verweis auf den hololens an und beschließt, einen Schraubendreher zu starten, um die Arbeit zu starten. er würde höchstwahrscheinlich in Hand arbeiten arbeiten, ohne den Schrauben Strich zum Drücken einer Schaltfläche ablegen zu müssen. Sie sollte in der Lage sein, eine sprach Sitzung mit einem Voice-Befehl aufzurufen, eine bereits sichtbare Benutzeroberfläche zu finden, um zu beginnen, oder das Wort "Select".

Der Benutzer sollte folgende Möglichkeiten haben: 
* Wechseln Sie in die Hände frei, während Sie kostenlos
* Wechseln Sie zur Hand.
* Wechseln zum Controller mithilfe eines Controllers 

### <a name="create-redundant-ways-to-switch-modes"></a>Erstellen von redundanten Möglichkeiten zum Wechseln von Modi
Beim ersten Prinzip geht es um den Zugriff, bei dem zweiten Prinzip um die Verfügbarkeit. Es darf nicht nur eine Möglichkeit zum Wechseln in einen und aus einem Modus kommen. 

Einige Beispiele sind: 
* Eine Schaltfläche zum Starten von sprach Interaktionen
* Ein Sprachbefehl für den Übergang zu, Verwendung von Head-Gaze und wohnen

### <a name="add-a-dash-of-drama"></a>Hinzufügen eines Bindestrichs
Ein Modusschalter ist ein großer Unternehmen, und es ist wichtig, dass Sie, wenn diese Übergänge eintreten, ein expliziter, sogar ein dramatischer Switch ist, damit der Benutzer weiß, was passiert ist. 


## <a name="usability-checklist"></a>Benutzerfreundlichkeit

**Kann der Benutzer alles durchführen, und alles, was für das Ende von Hand ist.**
* Jede austauschbare Tabelle sollte auf die Hand frei zugreifen können.
* Stellen Sie sicher, dass alle benutzerdefinierten Gesten ersetzt werden, z. b. das Ändern der Größe, das platzieren, das Schwenken, das Tippen usw.
* Stellen Sie sicher, dass der Benutzer jederzeit über eine sichere Kontrolle über das vorhanden sein von Benutzeroberflächen, die Platzierung und Ausführlichkeit verfügt.
    * So erhalten Sie die Benutzeroberfläche
    * Adressieren der Benutzeroberfläche, die nicht in der Ansicht angezeigt wird (FOV)
    * Wie viel ich sehe, wo, wann

**Werden die Mechanismen der Interaktion mit den richtigen Kosten für die Interaktion gelehrt und verstärkt?**

Versteht der Benutzer...
* ... In welchem Modus befinden Sie sich?
* ... Was können Sie in diesem Modus tun?
* ... Was ist der aktuelle Zustand?
* ... Wie können Sie übergehen?
    
**Ist die Benutzeroberfläche für die Hände frei optimiert?**   

* Beispiel: das Verb bauen von Strukturen ist nicht in typische 2D-Muster integriert.
* Beispiel: die sprach Ausrichtung ist besser mit der Objekt Hervorhebung.
* Beispiel: sprach Interaktionen sind besser mit Untertiteln, die eingeschaltet werden müssen


## <a name="see-also"></a>Weitere Informationen:
* [Augen Verfolgung auf hololens 2](eye-tracking.md)
* [Blick und Commit](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Bearbeitung von Hand direkt](direct-manipulation.md)
* [Handgesten](gaze-and-commit.md#composite-gestures)
* ["Hand Punkt" und "Commit"](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
