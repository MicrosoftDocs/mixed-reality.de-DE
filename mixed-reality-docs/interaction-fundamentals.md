---
title: Instinktive Interaktionen
description: Lernen Sie die Philosophie der einfachen, instinktiven Interaktionen kennen, die in der gesamten Mixed Reality-Plattform verwurzelt ist.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf, Hololens, MMR, kombiniert
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539718"
---
# <a name="introducing-instinctual-interactions"></a>Einführung in instinktive Interaktionen

![Fernmanipulation mit den Händen](images/04_InteractionFundamentals.png)

Die Philosophie der einfachen, instinktiven Interaktionen ist in der gesamten Mixed Reality-Plattform (MR) verwurzelt. Wir haben drei Schritte unternommen, um sicherzustellen, dass Anwendungsdesigner und -entwickler ihren Kunden einfache und intuitive Interaktionen bereitstellen können. 

Zunächst haben wir sichergestellt, dass sich unsere Sensoren und Eingabetechnologien (die Hand- und Eyetracking sowie natürliche Spracheingabe umfassen) zu nahtlos kombinierten Interaktionsmodellen verbinden.  
Basierend auf unseren Studien ist das kombinierte Entwerfen und Entwickeln in einem multimodalen Framework – und nicht die Fokussierung auf einzelne Eingaben – der Schlüssel zur Realisierung instinktiver Erfahrungen.

Zweitens haben wir erkannt, dass viele Entwickler auf mehrere HoloLens-Geräte ausgerichtet sind, z. B. HoloLens 2 und HoloLens (1. Generation) oder HoloLens und VR.  
Deshalb haben wir unsere Interaktionsmodelle so konzipiert, dass sie geräteübergreifend funktionieren, auch wenn die Eingabetechnologie von Gerät zu Gerät variiert.  
So verwenden z. B. die ferne Interaktion bei einem Windows Immersive Headset mit einem 6DoF-Controller und die ferne Interaktion bei HoloLens 2 jeweils dieselben Angebote und Muster, was die geräteübergreifende Anwendungsentwicklung erleichtert und den Benutzerinteraktionen ein natürliches Gefühl verleiht. 

Wir haben zwar erkannt, dass Mixed Reality (MR) Tausende von effektiven, ansprechenden und einzigartigen Interaktionen bietet, aber wir haben festgestellt, dass der bewusste Einsatz eines einzelnen umfassenden Interaktionsmodells in einer Anwendung der beste Weg ist, um sicherzustellen, dass Benutzer erfolgreich sind und ein großartiges Erlebnis haben. Zu diesem Zweck haben wir drei Punkte in diese Interaktionsanleitung einbezogen:
* Diese Anleitung um die drei primären Interaktionsmodelle und die für jedes einzelne Modell erforderlichen Komponenten und Muster.
* Zusätzliche Anleitungen zu weiteren Vorteilen, die unsere Plattform bietet.
* Allgemeine Anleitungen zur Auswahl des geeigneten Interaktionsmodells für Ihr Entwicklungsszenario.

## <a name="multimodal-interaction-models"></a>Kombinierte Interaktionsmodelle

Basierend auf unseren bisherigen Studien sowie dem Feedback von Kunden haben wir festgestellt, dass drei primäre Interaktionsmodelle für die meisten Mixed Reality-Umgebungen geeignet sind. In vielerlei Hinsicht ist das Interaktionsmodell das mentale Modell des Benutzers zur Durchführung eines Workflows. Jedes dieser Interaktionsmodelle ist für eine Reihe von Kundenanforderungen optimiert und ist bei richtiger Anwendung benutzerfreundlich, leistungsstark und praktikabel. 

Das folgende Diagramm stellt eine vereinfachte Übersicht dar. Ausführliche Informationen zur Verwendung der einzelnen Interaktionsmodelle sind auf den folgenden Seiten mit Bildern und Codebeispielen verknüpft. 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modell</strong></td>
        <td><strong>Beispielszenarien</strong></td>
        <td><strong>Eignung</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Hände und Motion-Controller</a></td>
        <td>3D-Raumerlebnisse, z. B. räumliches Layout und räumlicher Entwurf, Inhaltsmanipulation oder Simulation.</td>
        <td>Ideal für neue Benutzer, kombiniert mit Stimme, Eyetracking oder Anvisieren mit dem Kopf. Niedrige Lernkurve. Konsistente Benutzererfahrung für Handtracking und Controller mit 6 Freiheitsgraden.</td>
        <td>HoloLens 2<br>Immersive Headsets</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Freihändig</a></td>
        <td>Kontextbezogene Erfahrungen, bei denen die Hände eines Benutzers beschäftigt sind, z. B. praxisnahes Lernen und Wartung.</td>
        <td>Gewisser Lernaufwand erforderlich. Das Gerät ist gut für Stimme und natürliche Sprache geeignet, wenn die Hände nicht verfügbar sind.</td>
        <td>HoloLens 2<br>HoloLens (1. Generation)<br>Immersive Headsets</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Anvisieren und Ausführen</a></td>
        <td>Click-Through-Erfahrungen, z. B. 3D-Präsentationen, Demos.</td>
        <td>Erfordert Training für HMDs, aber nicht für mobile Geräte. Ideal für verfügbare Controller. Ideal für HoloLens (1. Generation).</td>
        <td>HoloLens 2<br>HoloLens (1. Generation)<br>Immersive Headsets<br>Mobile AR</td>
    </tr>
</table>
<br>

Die beste Möglichkeit, um sicherzustellen, dass es keine Lücken bei der Interaktion für Ihr Erlebnis gibt, besteht darin, der Anleitung für ein einzelnes Modell von Anfang bis Ende zu folgen.

Die folgenden Abschnitte führen durch die Schritte zur Auswahl und Implementierung eines dieser Interaktionsmodelle.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Am Ende dieser Seite werden Sie unsere Anleitung zu Folgendem verstehen:
 
* Auswählen eines Interaktionsmodells für Ihren Kunden
* Implementieren des Interaktionsmodells
* Wechseln zwischen Interaktionsmodellen
* Entwerfen der nächsten Schritte


## <a name="choose-an-interaction-model-for-your-customer"></a>Auswählen eines Interaktionsmodells für Ihren Kunden

In der Regel haben Entwickler und Ersteller die Arten von Interaktionen, die Ihre Kunden ausführen können, bereits durchdacht. Um einen kundenorientierten Ansatz für den Entwurf zu fördern, empfehlen wir Ihnen die folgende Anleitung zur Auswahl des für Ihren Kunden optimierten Interaktionsmodells.

### <a name="why-follow-this-guidance"></a>Gründe zum Befolgen dieser Anleitung

* Unsere Interaktionsmodelle werden auf objektive und subjektive Kriterien wie physische und kognitive Leistung, Intuitivität und Erlernbarkeit getestet. 
* Da die Interaktion unterschiedlich verläuft, können sich auch die visuellen/akustischen Angebote sowie das Objektverhalten zwischen Interaktionsmodellen unterscheiden.  
* Die Kombination von Komponenten verschiedener Interaktionsmodelle birgt das Risiko konkurrierender Angebote, z. B. simultane Handstrahlen und ein Cursor zum Anvisieren mit dem Kopf. Dies kann Benutzer überfordern und verwirren.

Hier folgen einige Beispiele dazu, wie Angebote und Verhaltensweisen für die einzelnen Interaktionsmodelle optimiert werden. Neue Benutzer haben häufig ähnliche Fragen, z. B. _„Woher weiß ich, dass das System funktioniert?“_ , _„Woher weiß ich, über welche Möglichkeiten ich verfüge?“_ und _„Woher weiß ich, ob es verstanden hat, was ich gerade getan habe?“_ .

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modell</strong></td>
        <td><strong>Woher weiß ich, dass es funktioniert?</strong></td>
        <td><strong>Woher weiß ich, über welche Möglichkeiten ich verfüge?</strong></td>
        <td><strong>Woher weiß ich, was ich gerade getan habe?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Hände und Motion-Controller</a></td>
        <td>Ich sehe ein Handgittermodell, ein Fingerspitzenangebot oder Hand-/Controllerstrahlen.</td>
        <td>Es werden greifbare Ziehpunkte oder ein Begrenzungsrahmen angezeigt, wenn die Hand sich in der Nähe des Objekts befindet.</td>
        <td>Ich höre Töne und sehe Animationen beim Greifen und Loslassen.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></td>
        <td>Ich sehe einen Cursor in der Mitte meines Sichtfelds.</td>
        <td>Der Cursor wechselt den Zustand, wenn er sich über bestimmten Objekten befindet.</td>
        <td>Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Freihändig (Anvisieren mit dem Kopf und Verweilen)</a></td>
        <td>Ich sehe einen Cursor in der Mitte meines Sichtfelds.</td>
        <td>Ich sehe eine Statusanzeige, wenn ich über einem interaktionsfähigen Objekt verweile.</td>
        <td>Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Freihändig (Sprachbefehle)</a></td>
        <td>Ich sehe eine Anzeige zur Spracherkennung und Untertitel, die zeigen, was das System gehört hat.</td>
        <td>Ich erhalte Sprachansagen und Hinweise. Wenn ich Folgendes sage: Was kann ich sagen? Ich sehe ein Feedback.</td>
        <td>Ich sehe/höre visuelle und akustische Bestätigungen, wenn ich einen Befehl erteile, oder erhalte bei Bedarf die Benutzerumgebung zur Mehrdeutigkeitsvermeidung.</a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Nachfolgend sind Fragen aufgeführt, die Teams (gemäß unserer Erfahrung) bei der Auswahl eines Interaktionsmodells geholfen haben:
 
1.  Q:  Möchten meine Benutzer Hologramme berühren und präzise holografische Eingriffe durchführen?<br><br>
A:  In diesem Fall sollten Sie das Interaktionsmodell für Hände und Motion-Controller für die Präzisionszielbestimmung und für Eingriffe ausprobieren.
 
2.  Q:  Müssen meine Benutzer für reale Aufgaben die Hände frei haben?<br><br>
A:  In diesem Fall sollten Sie sich das Interaktionsmodell „Freihändig“ ansehen, das durch blick- und sprachbasierte Interaktionen eine großartige freihändige Umgebung bietet.
 
3.  Q:  Haben meine Benutzer Zeit, Interaktionen für meine MR-Anwendung zu erlernen, oder sind Interaktionen mit einer möglichst geringen Lernkurve erforderlich?<br><br>
A:  Wir empfehlen das Modell für Hände und Motion-Controller für die niedrigste Lernkurve und intuitivste Interaktion, sofern die Benutzer ihre Hände zur Interaktion nutzen können.
 
4.  Q:  Verwenden meine Benutzer Motion-Controller zum Zeigen und Bearbeiten?<br><br>
A:  Das Modell für Hände und Motion-Controller enthält alle Anleitungen für ein großartiges Erlebnis mit den Motion-Controllern.
 
5.  Q:  Verwenden meine Benutzer einen Controller für Barrierefreiheit oder einen herkömmlichen Bluetooth-Controller, z. B. ein Klick-Gerät?<br><br>
A:  Wir empfehlen das Modell „Anvisieren mit dem Kopf und Ausführen“ für alle nicht nachverfolgten Controller. Es wurde für Benutzer entwickelt, um ein ganzheitliches Erlebnis mit einem einfachen Mechanismus für „Anvisieren und Ausführen“ zu durchlaufen. 
 
6.  Q: Können meine Benutzer in einer Umgebung nur durch „Durchklicken“ voranschreiten (z. B. wie bei einer 3D-Diashow), anstatt durch kompakte Layouts von Steuerelementen der Benutzeroberfläche zu navigieren?<br><br>
A:  Wenn Benutzer nicht viele Komponenten einer Benutzeroberfläche steuern müssen, bietet „Anvisieren mit dem Kopf und Ausführen“ eine erlernbare Option, bei der sich Benutzer nicht um die Zielbestimmung kümmern müssen. 
 
7.  Q:  Verwenden meine Benutzer sowohl HoloLens (1. Generation) als auch HoloLens 2/Immersive Windows Mixed Reality-Headsets (VR)?<br><br>
A:  Da „Anvisieren mit dem Kopf und Ausführen“ das Interaktionsmodell für HoloLens (1. Generation) ist, empfehlen wir Entwicklern, die HoloLens (1. Generation) unterstützen, „Anvisieren mit dem Kopf und Ausführen“ nur alle Features oder Modi zu verwenden, die Benutzer auf einem HoloLens-Headset (1. Generation) erleben können. Weitere Informationen zur Erstellung einer großartigen Umgebung für mehrere HoloLens-Generationen finden Sie nachfolgend unter *Wechseln zwischen Interaktionsmodellen*.
 
8.  Q: Wie sieht es mit generell mobilen Benutzern, die einen großen Raum einnehmen oder sich zwischen verschiedenen Räumen bewegen, gegenüber Benutzern aus, die dazu neigen, in einem einzelnen Raum zu arbeiten?<br><br>
A:  Für diese Benutzer ist jedes der Interaktionsmodelle geeignet.  

> [!NOTE]
> Weitere Anleitungen zum App-Design sind [bald verfügbar](news.md).


## <a name="transitioning-interaction-models"></a>Wechseln zwischen Interaktionsmodellen
Es kann auch vorkommen, dass Ihre Anwendungsfälle die Verwendung mehrerer Interaktionsmodelle erfordern. Beim „Erstellungsablauf“ Ihrer Anwendung wird z. B. das Interaktionsmodell _„Hände und Motion-Controller“_ verwendet, aber Sie möchten einen Freihandmodus für Außendiensttechniker verwenden.
Wenn Ihre Umgebung mehrere Interaktionsmodelle erfordert, sollten Sie daran denken, dass viele Benutzer Schwierigkeiten beim Übergang von einem Modell zum anderen haben können – insbesondere Benutzer, die noch nicht mit Mixed Reality vertraut sind.

> [!Note]
> Wir arbeiten ständig an weiteren Anleitungen, die Entwicklern und Designern zur Verfügung stehen werden und sie über das Wie, Wann und Warum für den Einsatz mehrerer MR-Interaktionsmodelle informieren sollen.
 

## <a name="see-also"></a>Weitere Informationen
* [Komfort](comfort.md)
* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Motion-Controller](motion-controllers.md)
* [Räumliche Abbildung](spatial-mapping.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Spracheingabe](voice-input.md)


