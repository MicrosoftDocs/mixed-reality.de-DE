---
title: Eye-Blicke und commit
description: Übersicht über das Eingabemodell Eye-Blicke und commit
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität, Input, Eye Blicke, Auge als Ziel, HoloLens 2 "," Auswahl Eye-basierte Eye nachverfolgung
ms.openlocfilehash: 9cc27f24e1275223f33becd1ff0ec6bdf5b43a57
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66455086"
---
# <a name="eye-gaze-and-commit"></a>Eye-Blicke und commit
Mit HoloLens 2 haben wir die großartige Gelegenheit, die Blicke & Commit schneller und besser vertraut zu machen, indem Sie Head Blicke Eye Blicke anstelle. Auf diese Weise können die allgemeinen erweitern [Head-Blicke und Commit](gaze-and-commit.md) Interaktionsmodell: 
1. Betrachten Sie einfach ein Ziel und 
2. Um Ihre Absicht zum Auswählen des Ziels zu bestätigen, führen Sie eine sekundäre Datenbank explizite Eingabe wie z. B. a:  
   - Hand-Geste (z. B. ein Air Tippen Sie auf)
   - Drücken Sie die Schaltfläche (z. B. auf eine Bluetooth-Tastatur oder Clicker)
   - Voice-Befehl (z. B. "Select")
   - Einstichs (d. h. der Benutzer einfach hält Suche am Zielspeicherort auswählen)

Allerdings Eye Blicke verhält sich sehr unterschiedlich Head Blicke auf bestimmte Weise und enthält daher eine Reihe von einzigartige Herausforderungen bereit. In der [Eye bestaunen Entwurfsrichtlinien](eye-tracking.md), eine Übersicht über allgemeine Vorteile und Herausforderungen in Betracht ziehen, bei Verwendung-Augen-Überwachung in Ihrer app holographic als Eingabe. In diesem Abschnitt liegt der Schwerpunkt auf die spezifische Überlegungen zu lösungsentwürfen für Eye-Blicke & Commit.
Zunächst unser Auge unglaublich schnell zu verschieben und somit auch sehr schnell über die Ansicht als Ziel. Dadurch wird die Augen bestaunen ideal für schnelle Blicke-und-Commit-Aktionen vor allem zusammen mit schnellen Commits wie z. B. eine tippbewegung oder eine Schaltfläche drücken.
   
Im folgenden wir geht es um Richtlinien für den Entwurf Wenn Eye für diese Art von Interaktion bestaunen und besprechen die Unterschiede zwischen Haupt- und Eye Blicke, die Sie bedenken sollten.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Entwurfsrichtlinien Sie für Eye-Blicke und commit

**Einen Cursor nicht mehr anzeigen**: Es nahezu unmöglich, Sie interagieren zwar bestaunen ohne einen Cursor, wenn Head verwenden, der Cursor wird schnell zu allgemeiner Ablenkung und es ziemlich ärgerlich Verwendung Eye Blicke. Statt eines Cursors für den Benutzer zu informieren, ob Eye-tracking arbeitet und wurde ordnungsgemäß ermittelt derzeit suchenden am Ziel werden geringfügige Visual verwenden (Weitere Details folgen).

**Streben nach einer feine kombinierten zeigen Sie Feedback**: Scheinbar hervorragende visuelles Feedback für Head Blicke kann dazu führen, dass terrible, überwältigend-Erfahrungen, die mit Eye Blicke. Denken Sie daran, dass Ihre Augen überaus schnell und schnell für Punkte in Ihre Feldansicht darting sind. Schnelle plötzliche Hervorhebung Änderungen (ein/aus) können bei der Suche um flickery Feedback führen. Also beim Zeigen Sie Feedback Wir empfiehlt sich, eine Markierung reibungslos gemischt-in (und kombiniert wird, wenn sofort suchen). Dies bedeutet, dass auf den ersten Sie kaum das Feedback bemerken würden bei Betrachtung von einem Ziel. Im Verlauf von 500-1000 ms würde die Hervorhebung an Intensität erhöhen. Während der Benutzer konnte Ausschau zu halten, an das Ziel aus, um sicherzustellen, dass das System das fokussierte Ziel ordnungsgemäß erkannt wurde, können erfahrene Benutzer schnell bestaunen & Commit ausgeführt, ohne zu warten, bis das Feedback ist für die höchste Intensität. Darüber hinaus empfehlen wir Ihnen ebenfalls ein Blend-Out verwenden, wenn sich das Feedback gezeigt wird eingeblendet. Research hat gezeigt, dass schnelle Bewegungen und Kontrast Änderungen äußerst bemerkenswerten in Ihre peripheren Vision (also den Bereich des Felds Visual, in denen Sie nicht angezeigt wird). Das Ausblenden der videoüberlagerung benötigt keine so langsam wie die Blend-in zu sein. Dies ist nur wichtig, wenn hoher Kontrast oder farbänderungen für die hervorhebungs-wurden. Wenn das Feedback gezeigt wird zunächst sehr komplex war, wird nicht Sie wahrscheinlich einen Unterschied bemerken.

**Achten Sie für die Synchronisierung von Blicke und Commit-Signale**: Die Synchronisierung von Eingabe signalisiert ist möglicherweise kein großes Problem für einfache Blicke & Commit-, also, keine Sorge! Es ist etwas zu beachten müssen, sollten Sie kompliziertere Commit-Aktionen verwenden, obwohl, lange Sprachbefehle oder komplizierte gestensteuerung beinhalten kann. Angenommen Sie, Sie sehen Sie sich Ziel und einen lange Sprachbefehl Ramsch. Berücksichtigt die Zeit, die Sie benötigen, zu sprechen und die Zeit, die das System erkennen, was Sie gesagt werden musste, wurde Ihre Augen Blicke lange in der Regel einige neue Ziel in der Szene verschoben auf. Daher müssen Sie entweder Ihre Benutzer Beachten Sie, dass sie möglicherweise müssen an ein Ziel Ausschau zu halten, bis der Befehl erkannt wurde oder verarbeiten die Eingabe in eine Methode zum Bestimmen der Einsatz des Befehls und was der Benutzer am damals gesucht habe.

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Gestensteuerung](gestures.md)
* [Spracheingabe](voice-design.md)
* [Motion-Controller](motion-controllers.md)
