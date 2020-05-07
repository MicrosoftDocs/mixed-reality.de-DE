---
title: Anvisieren und Verweilen
description: Übersicht über das Eingabemodell „Anvisieren mit den Augen und Verweilen“
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: Eye-Tracking, Blickverfolgung, Mixed Reality, Eingabe, Anvisieren mit den Augen, Zielen mit den Augen, HoloLens 2, Blickgestützte Auswahl, Verweilen
ms.openlocfilehash: ba793f6b1a95fe4b95aa9a043d36823487886b5e
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604901"
---
# <a name="eye-gaze-and-dwell"></a>Anvisieren und Verweilen

Das Interaktionsmodell _„Anvisieren mit den Augen und Verweilen“_ ist ein Sonderfall des Interaktionsmodells [Anvisieren mit den Augen und Ausführen](gaze-and-commit.md):
1. Schauen Sie einfach ein Ziel an, und 
2. führen Sie zum Bestätigen Ihrer Zielauswahl eine sekundäre explizite Eingabe aus: _Visieren Sie einfach das Ziel an, das Sie auswählen möchten_.

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>Vorteile des Interaktionsmodells „Anvisieren mit den Augen und Verweilen“ 
Wenn Ihre Hände bereits mit einer Aufgabe beschäftigt sind oder Tools halten, ist es möglicherweise nicht möglich, diese für die Interaktion mit Hologrammen zu verwenden.
Eine freihändige Alternative der Interaktion zum Auswählen von Hologrammen ist „Anvisieren mit den Augen und verweilen“, mit anderen Worten: _„Anvisieren und Starren“_ . Der Vorteil dieses Ansatzes besteht darin, dass selbst stark eingeschränkte Benutzer, die möglicherweise nicht in der Lage sind, ihren Kopf oder Körper vollständig zu drehen, mit Hologrammen interagieren können (z. B. in einer sehr beengten Arbeitsumgebung).
Der Benutzer visiert das Ziel einfach weiter an, das er auswählen möchte, und es werden verschiedene Feedbacks zum Verweilen angezeigt, um den Prozess anzugeben.


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>Herausforderungen des Interaktionsmodells „Anvisieren mit den Augen und Verweilen“
Generell empfehlen wir, die auf Verweilen basierten Aktivierungen nur dann als letzte Alternative zu verwenden, wenn weder Sprach- noch Handeingaben verfügbar sind. Der Grund dafür ist, dass die Wahl der Verweildauer ziemlich schwierig sein kann. Anfänger sind mit längeren Verweilzeiten einverstanden, während erfahrene Benutzer schnell und effizient navigieren möchten. Daraus ergibt sich die Herausforderung, die Verweildauer an die individuellen Bedürfnisse eines Benutzers anzupassen.
Wenn die Verweildauer zu kurz ist: Der Benutzer kann sich überfordert fühlen, wenn Hologramme die ganze Zeit auf sein Anvisieren mit den Augen reagieren. Wenn die Verweildauer zu lang ist: Die Benutzererfahrung fühlt sich möglicherweise zu langsam und unterbrochen an, da der Benutzer die Ziele für lange Zeit anvisieren muss.

## <a name="design-recommendations"></a>Entwurfsempfehlungen
Wir empfehlen einen zweistufigen Ansatz für das Verweilfeedback:
1. *Anfangsverzögerung*: Wenn der Benutzer anfängt, ein Ziel anzuvisieren, sollte keine unmittelbare Reaktion erfolgen, da dies zu einer unangenehmen und überfordernden Benutzererfahrung führen kann. Starten Sie stattdessen einen Timer, um zu ermitteln, ob der Benutzer absichtlich auf das Ziel starrt oder er es nur überfliegt.
Wir empfehlen eine Ausführungszeit von 150 bis 250 ms bei einer bestimmten Nähe (d. h. der Benutzer ist auf ein Ziel fixiert, anstatt ein größeres Ziel länger zu betrachten).  
2. *Starten des Verweilfeedbacks:* Nachdem Sie sichergestellt haben, dass der Benutzer das Ziel absichtlich anvisiert, beginnen Sie mit der Anzeige des Verweildauerfeedbacks, um den Benutzer darüber zu informieren, dass die Verweilaktivierung eingeleitet wird. 
3. *Fortlaufendes Feedback:* Während der Benutzer das Ziel weiterhin anvisiert, zeigen Sie eine fortlaufende Fortschrittsanzeige an, damit der Benutzer weiß, dass er das Ziel weiter anvisieren muss. Insbesondere für die Eingabe über das Anvisieren mit den Augen empfehlen wir, _die visuelle Aufmerksamkeit des Benutzers zu gewinnen_, indem wir mit einem größeren Kreis oder einer Kugel beginnen, die sich zu einer kleineren Version zusammenzieht. Die Anzeige eines Indikators für den Endzustand (kleiner Kreis) hilft dem Benutzer zu vermitteln, wann das Verweilen beendet sein wird. Eine Beispielabbildung ist unten dargestellt. 
4. *Fertig stellen:* Wenn der Benutzer das Ziel weiterhin fixiert hat (für weitere 650 bis 850 ms), schließen Sie die Verweilaktivierung ab und wählen das anvisierte Ziel aus.

![Verweilzustände](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>Siehe auch
* [Eyetracking – Blickverfolgung](eye-tracking.md)
* [Mit den Augen anvisieren und ausführen](gaze-and-commit-eyes.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Spracheingabe](voice-design.md)
