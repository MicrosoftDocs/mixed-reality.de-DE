---
title: Optimieren Ihre app für freisprechgeräte
description: Optimieren Ihre app für freisprechgeräte
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, physisch, bestaunen, bestaunen Ziel ist, handelt es sich bei Interaktion, Entwurf
ms.openlocfilehash: b64dec802d8ed2886021a54f302ba4a948c4f5b9
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581030"
---
# <a name="optimizing-your-app-for-hands-free"></a>Optimieren Ihre app für freisprechgeräte



## <a name="scenarios"></a>Szenarien

Wie in der [Interaktion Modellübersicht](interaction-fundamentals.md), nachdem Sie die Benutzer und ihre Ziele identifiziert haben, Fragen Sie sich, welche Herausforderungen Umwelt- oder Informationen, die sie möglicherweise konfrontiert, wenn sie zum Ausführen ihrer Aufgaben arbeiten. Beispielsweise müssen viele Benutzer verwenden, wenn sich ihre echten Ziele zu erreichen und schwierigkeiten bei der Interaktion mit der eine Grundlage Hands-und-Controller-Schnittstelle. 

Unter Umständen einige spezifischen Szenarien: 
* Durch eine Aufgabe, geführt werden, während Hands ausgelastet sind.
* Verweisen auf die Materialien, während Sie sich mit der ausgelastet sind.
* Hand-fatigue
* Handschuhe, die nicht überwacht werden können
* Etwas ausführen


## <a name="hands-free-modalities"></a>Physisch Modalitäten

### <a name="voice-commanding"></a>Voice-Befehle

Verwenden Ihre Stimme zum Befehl und Steuerung, die eine Schnittstelle kann nicht nur ermöglicht dem Benutzer, arbeiten Handsfree, aber auch mehrere Schritte überspringen. Die Verwendung dieser Modalität reichen von der Benutzer kann alle diese Schaltfläche einfach zu lesen laut aktivieren, wie finden Sie unter-It-Say-It, um die Konversation mit einem Agent, der Aufgaben für Sie ausführen kann.

* [Sprachentwurf](voice-design.md)


### <a name="head-gaze-and-dwell"></a>Head Blicke und dwell

In einigen Situationen physisch ist mit der Stimme nicht ideal oder sogar möglich. Laut Factoryumgebungen, Datenschutz oder soziale Normen können alle Einschränkungen sein. Die Kopfzeile bestaunen + länger aufhalten Modell kann der Benutzer die app zu navigieren, indem Sie ihre Head Vektor um zu zeigen, während die veralteten, oder auf eine Schaltfläche Einstichs wird Aktivieren der nach einem bestimmten Zeitraum (in der Regel ca. 1 Sekunde oder so). 

* [Blicke und dwell](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a>Übergang und physisch

Für diese Szenarien können Sie sich von der Interaktion mit Hologramme für Befehle und Navigation freigeben reichen von eine zwingende Voraussetzung nicht erfüllt, die beim Betrieb von End-to-End auf benutzerfreundlichkeit, die der Benutzer zu einem beliebigen Zeitpunkt in und aus der Übergang kann der app wird. 

Wenn die Anforderung der app ist, dass er immer ohne Benutzereingriff, verwendet wird, ob mithilfe Dwell, Sprachbefehle, oder die einzigen Sprachbefehl, "select", und dann stellen Sie sicher, dass die entsprechenden für Unterkünfte in Ihrer Benutzeroberfläche vornehmen. 

Wenn sich der Zielbenutzer von Hand zu physisch am nach eigenem Ermessen wechseln können muss, ist es wichtig, diese Prinzipien berücksichtigen:

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Wird davon ausgegangen Sie, dass der Benutzer bereits in den Modus, der sie wechseln möchten.
Z. B. wenn der Benutzer am Herstellerstandort ist, einen video Verweis auf ihr Hololens, überwachen und entscheidet, um ein Schraubenschlüsselsymbol zu übernehmen, um zu arbeiten, möchte in den meisten Fällen sie mit der Arbeit in Handsfree ohne versetzt, das Schraubenschlüsselsymbol drücken eine Schaltfläche beginnen. Sie sollten eine Voice-Sitzung mit einem Voice-Befehl aufrufen, werden für bereits sichtbare Benutzeroberfläche auf Dwell beginnen länger aufhalten Lage sein, oder z. B. das Wort "select".

Der Benutzer muss die Möglichkeit, verfügen: 
* Wechseln Sie zur Handsfree beim handsfree
* Wechseln Sie zur Hand, mit der Hand
* Wechseln Sie zu dem Controller mithilfe eines Controllers 

### <a name="create-redundant-ways-to-switch-modes"></a>Erstellen Sie redundante Möglichkeiten, die für einen Moduswechsel
Während das vorherrschende Prinzip bei Zugriff ist, ist der zweite über die Verfügbarkeit. Es sollten nur keine einzelne Möglichkeit für den Übergang in einen Modus. 

Einige Beispiele für würde folgendermaßen lauten: 
* Eine Schaltfläche, um die sprachliche Interaktionen zu beginnen
* Einen Sprachbefehl für den Übergang zur Verwendung von Blicke + dwell

### <a name="add-a-dash-of-drama"></a>Fügen Sie ein wenig vom Drama hinzu.
Einen Moduswechsel ist sehr aufwendig – es ist wichtig, die auftreten, wenn diese Übergänge, die, dass sie sich einen expliziten, sogar erhebliche-Switch, damit der Benutzer wissen, was passiert ist. 


## <a name="usability-checklist"></a>Checkliste für die benutzerfreundlichkeit

**Möglich der Benutzer alles und jedes physisch, End-to-End-alles?**
* Jede interactible zugänglich physisch sein sollen
* Stellen Sie sicher, dass ein Ersatz für alle benutzerdefinierten stiftbewegungen, z. B. Ändern der Größe, platzieren, Kundenkarte, tippen usw. vorhanden ist.
* Stellen Sie sicher, dass der Benutzer davon überzeugt Steuerelement der Benutzeroberfläche vorhanden, Platzierung, Ausführlichkeit jederzeit verfügt
    * Abrufen von UI aus dem Weg
    * Behandeln von Benutzeroberfläche, die außerhalb des Sichtfelds (Blickfeld) liegt
    * Wie viel angezeigt, wobei bei

**Sind die Mechanismen der Interaktion eines und Kopplung mit dem richtigen visueller Hinweise werden?**

Der Benutzer ist versteht...
* ... Modus sind sie in?
* ... Welche Möglichkeiten sie in diesem Modus?
* ... Was ist der aktuelle Zustand?
* ... Wie können sie sich wechseln?
    
**Ist die Benutzeroberfläche für freisprechgeräte optimiert?**   

* Beispiel: Dwell visueller Hinweise sind nicht in typischen 2D Muster integriert
* Beispiel: Für die Zielgruppenadressierung von Voice ist besser mit Hervorhebung von Objekt
* Beispiel: Sprachliche Interaktionen sind besser mit Beschriftungen, die aktiviert werden müssen


## <a name="see-also"></a>Siehe auch
* [Blicke und commit](gaze-and-commit.md)
* [Direkte Bearbeitung](direct-manipulation.md)
* [Punkt- und commit](point-and-commit.md)
