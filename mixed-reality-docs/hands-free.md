---
title: Freisprechen
description: Optimieren Ihrer APP für praktische Übungen
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Gemischte Realität, Hände frei, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414392"
---
# <a name="hands-free"></a>Freisprechen



## <a name="scenarios"></a>Szenarien

Wie in der [Übersicht über das Interaktionsmodell](interaction-fundamentals.md)erläutert, stellen Sie nach dem Ermitteln der Benutzer und ihrer Ziele selbst fest, welche Umgebungs-oder situations Probleme auftreten können, wenn Sie Ihre Aufgaben erledigen. Beispielsweise müssen viele Benutzer ihre Hand haben, um Ihre tatsächlichen Ziele zu erreichen, und Sie haben Schwierigkeiten bei der Interaktion mit einer auf der Hand-und Controller basierten Schnittstelle. 

Einige spezifische Szenarien können wie folgt lauten: 
* Sie werden durch eine Aufgabe geleitet, während die Hände ausgelastet sind.
* Referenzierende Materialien, während Ihre Hände ausgelastet sind
* Hand Müdigkeit
* Handschuhe, die nicht überwacht werden können
* Ausführen von etwas


## <a name="hands-free-modalities"></a>Hände freie Modalitäten

### <a name="voice-commandingvoice-designmd"></a>[Sprachbefehle](voice-design.md)

Durch die Verwendung Ihrer Stimme für Befehls-und Steuerungsmöglichkeiten einer Schnittstelle kann der Benutzer nicht nur Handsfree betreiben, sondern auch mehrere Schritte überspringen. Die Verwendung dieser Modalität kann zwischen dem zulassen, dass der Benutzer einfach den Namen einer Schaltfläche ausliest, um ihn zu aktivieren, wie in "See-it-it-it", um eine konvergung mit einem Agent auszuführen, der Aufgaben für Sie ausführen kann.



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)

In einigen praktischen Situationen ist die Verwendung Ihrer Stimme nicht ideal oder gar nicht möglich. Laute Factory-Umgebungen, Datenschutz oder soziale Standards können Einschränkungen aufweisen. Mit dem Modell "Head-Do + Dwell" kann der Benutzer durch die APP navigieren, indem er den Kopf Vektor verwendet, um zu zeigen, während er nicht mehr ist, oder auf einer Schaltfläche auf einer Schaltfläche, die ihn nach einem bestimmten Zeitraum aktiviert, in der Regel etwa 1 Sekunde. 


## <a name="transitioning-in-and-out-of-hands-free"></a>Wechsel in und aus der Praxis freie Umstellung

In diesen Szenarien kann die Interaktion mit holograms für die Befehls-und Navigations Phase von einer absoluten Anforderung bis zum Ende des Betriebs der Anwendung bis zum Ende reichen, bis zu einer zusätzlichen Benutzererfahrung, von der der Benutzer jederzeit und von allen Zeit. 

Wenn die Anforderung der Anwendung darin besteht, dass Sie immer mit der Hand frei verwendet wird, egal ob mithilfe von "Dwell", "Voice"-Befehlen oder mit einem einzelnen Sprachbefehl "Select", stellen Sie sicher, dass Sie die entsprechenden Unterkünfte in der Benutzeroberfläche vornehmen. 

Wenn Ihr Ziel Benutzer in der Lage sein muss, nach eigenem Ermessen von Hand zu Hand zu wechseln, ist es wichtig, dass Sie die folgenden Prinzipien berücksichtigen.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Gehen Sie davon aus, dass der Benutzer bereits im Modus ist, zu dem gewechselt werden soll.
Wenn sich der Benutzer beispielsweise auf der Werks Seite befindet, sehen Sie sich einen Video Verweis auf den hololens an und beschließt, einen Schraubendreher zu starten, um die Arbeit zu starten, würde er wahrscheinlich in Handsfree arbeiten, ohne den Schrauben Strich zum Drücken einer Schaltfläche ablegen zu müssen. Sie sollte in der Lage sein, eine sprach Sitzung mit einem Voice-Befehl aufzurufen, eine bereits sichtbare Benutzeroberfläche zu finden, um zu beginnen, oder das Wort "Select".

Der Benutzer sollte folgende Möglichkeiten haben: 
* Wechseln Sie in die Hände frei, während Sie kostenlos
* Wechseln Sie zur Hand.
* Wechseln zum Controller mithilfe eines Controllers 

### <a name="create-redundant-ways-to-switch-modes"></a>Erstellen von redundanten Möglichkeiten zum Wechseln von Modi
Beim ersten Prinzip geht es um den Zugriff, bei dem zweiten Prinzip um die Verfügbarkeit. Es darf nicht nur eine Möglichkeit zum Wechseln in einen und aus einem Modus kommen. 

Einige Beispiele sind: 
* Eine Schaltfläche zum Starten von sprach Interaktionen
* Ein Sprachbefehl für den Übergang zu Verwendung von Blick und wohnen

### <a name="add-a-dash-of-drama"></a>Hinzufügen eines Bindestrichs
Ein Modusschalter ist ein großer Unternehmen. es ist wichtig, dass Sie, wenn diese Übergänge eintreten, ein expliziter, sogar dramatischer Switch ist, damit der Benutzer weiß, was passiert ist. 


## <a name="usability-checklist"></a>Benutzerfreundlichkeit

**Kann der Benutzer alles durchführen, und alles, was für das Ende von Hand ist.**
* Jeder interacable sollte auf die Hände frei zugreifen können.
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

* Beispiel: Das Verb-aufforstbau ist nicht in typische 2D-Muster integriert.
* Beispiel: Die sprach Ausrichtung ist besser mit der Objekt Hervorhebung.
* Beispiel: Sprach Interaktionen sind besser mit Untertiteln, die eingeschaltet werden müssen.


## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
