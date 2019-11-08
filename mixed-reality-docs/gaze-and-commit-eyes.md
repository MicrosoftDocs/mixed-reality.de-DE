---
title: Anvisieren mit den Augen und Ausführen
description: Übersicht über das Eingabemodell „Anvisieren mit den Augen und Ausführen“
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Eye-Tracking, Blickverfolgung, Mixed Reality, Eingabe, Anvisieren mit den Augen, Zielen mit den Augen, HoloLens 2, Blickgestützte Auswahl
ms.openlocfilehash: 89f5031635f2b67ba4c9afdf605559c2b9da4ac2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437826"
---
# <a name="eye-gaze-and-commit"></a>Anvisieren mit den Augen und Ausführen
_Anvisieren mit den Augen und Ausführen_ ist ein Sonderfall des Eingabemodells [Anvisieren und Ausführen](gaze-and-commit.md), bei dem es darum geht, ein Objekt anzuvisieren, indem es einfach betrachtet und dann mit einer sekundären _Ausführen_-Eingabe darauf reagiert, z. B. mit einer Handgeste, einem Sprachbefehl oder einer Peripheriegeräteingabe (z. B. einem Gamecontroller). 

Mit HoloLens 2 haben wir die großartige Möglichkeit, das Eingabemodell _Anvisieren und Ausführen_ durch das Anvisieren mit den Augen statt mit dem Kopf schneller und komfortabler zu gestalten. Auf diese Weise kann das häufig verwendete Interaktionsmodell [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md) erweitert werden: 
1. Schauen Sie einfach ein Ziel an, und 
2. führen Sie zum Bestätigen Ihrer Zielauswahl eine der folgenden sekundären expliziten Eingaben aus:  
   - Handgeste (z. B. Tippen in die Luft)
   - Drücken einer Schaltfläche (z. B. auf einer Bluetooth-Tastatur oder einem Klick-Gerät)
   - Sprachbefehl (z. B. „Auswählen“)
   - Verweilen (d. h. der Benutzer schaut zum Auswählen weiterhin auf das Ziel)

Auf bestimmte Weise verhält sich das „Anvisieren mit den Augen“ jedoch anders als das Anvisieren mit dem Kopf und bringt daher einige spezielle Herausforderungen mit sich. In den [Entwurfsrichtlinien für das Anvisieren mit den Augen](eye-tracking.md) sind die allgemeinen Vorteile und Herausforderungen zusammengefasst, die beim Verwenden der Blickvefolgung als Eingabemodell für die holografische App zu berücksichtigen sind. In diesem Abschnitt konzentrieren wir uns auf die speziellen Entwurfsüberlegungen für das Modell _Anvisieren mit den Augen und Ausführen_.
Zu Beginn sei vorausgeschickt, dass unsere Augen sich unglaublich schnell bewegen und daher hervorragend für die schnelle Zieladressierung im Sichtfeld geeignet sind. Daher ist das Anvisieren mit den Augen ideal für schnelle Aktionen des Typs „Anvisieren und Ausführen“ geeignet, besonders in Kombination mit schnellen Ausführaktionen wie Tippen in die Luft oder Drücken einer Schaltfläche.
   
Im Folgenden geht es um die Entwurfsrichtlinien bei Verwendung des Anvisierens mit den Augen für diese Art von Interaktion. Außerdem werden die Unterschiede zwischen dem Anvisieren mit den Augen und dem Anvisieren mit dem Kopf behandelt, die zu berücksichtigen sind.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Entwurfsrichtlinien für „Anvisieren mit den Augen und Ausführen“

**Zeigen Sie keinen Cursor an**: Eine Interaktion ohne Cursor ist beim Anvisieren mit dem Kopf nahezu unmöglich. Beim Anvisieren mit den Augen lenkt der Cursor jedoch schnell ab und wirkt störend. Verwenden Sie zur Information des Benutzers, ob das Anvisieren mit den Augen funktioniert und das aktuell anvisierte Ziel korrekt erkannt wurde, dezente optische Markierungen (Einzelheiten hierzu finden Sie weiter unten).

**Bemühen Sie sich um ein dezent ein- und ausgeblendetes Zeigefeedback**: Was beim Anvisieren mit dem Kopf als hervorragendes visuelles Feedback erscheint, kann beim Anvisieren mit den Augen eine ziemliche Überforderung sein. Denken Sie daran, dass Augen überaus schnell sind und schnell über Punkte im Sichtfeld fliegen. Schnelle plötzliche Markierungsänderungen (Ein/Aus) können beim Umherschauen zu einem flackernden Feedback führen. Wir empfehlen daher, beim Zeigefeedback eine sanft eingeblendete (und beim Wegschauen sanft ausgeblendete) Markierung zu verwenden. Dies bedeutet, dass Sie beim Anvisieren eines Ziels das Feedback zuerst kaum wahrnehmen. Im Verlauf von 500-1000 ms würde die Markierung an Intensität zunehmen. Während unerfahrene Benutzer weiterhin das Ziel anvisieren könnten, um sicherzustellen, dass das System das anvisierte Ziel korrekt bestimmt hat, könnten erfahrene Benutzer schnell die Aktion „Anvisieren und Ausführen“ abschließen, ohne darauf zu warten, bis das Feedback die volle Intensität erreicht. Darüber hinaus empfehlen wir, auch ein Ausblenden des Zeigefeedbacks zu verwenden. Untersuchungen haben gezeigt, dass schnelle Bewegungen und Kontraständerungen im peripheren Sichtbereich (dem Bereich des Sichtfelds, den Sie nicht direkt anschauen) gut wahrnehmbar sind.
Das Ausblenden muss nicht so langsam erfolgen wie das Einblenden. Dies ist nur wichtig, wenn Sie für die Markierung starke Kontrast- oder Farbänderungen verwenden. Wenn das Zeigefeedback zu Beginn recht dezent war, werden Sie wahrscheinlich keinen Unterschied feststellen.

**Achten Sie auf die Synchronisierung der Anvisier- und Ausführungssignale**: Die Synchronisierung der Eingabesignale ist wahrscheinlich keine große Herausforderung für das einfache in die Luft tippen und Drücken von Schaltflächen. Wenn Sie etwas kompliziertere Ausführungsaktionen verwenden möchten, sollten Sie allerdings darauf achten, auch wenn das lange Sprachbefehle oder komplizierte Handgesten beinhalten kann. Stellen Sie sich vor, dass Sie ein Ziel anvisieren und einen langen Sprachbefehl äußern. In der Zeit, die Sie zum Sprechen benötigen, und der Zeit, die das System für die Spracherkennung benötigt, hat sich Ihr Auge in der Regel schon längst einem neuen Ziel in der Szene zugewandt. Daher müssen Sie entweder Ihre Benutzer darauf hinweisen, dass sie solange das Ziel anvisieren müssen, bis der Befehl erkannt wurde, oder Sie müssen bei der Verarbeitung der Eingabe den Beginn des Befehls und den zu diesem Zeitpunkt anvisierten Punkt bestimmen.

## <a name="see-also"></a>Weitere Informationen
* [Augenbasierte Interaktion] (eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2] (eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
