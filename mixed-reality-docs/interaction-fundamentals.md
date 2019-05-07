---
title: Übersicht über die Multimodale Interaktion
description: Übersicht über die Multimodale Interaktion
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Gemischte Realität Blicke, Blicke Ziel ist, handelt es sich bei der Interaktion, Entwerfen
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993603"
---
# <a name="introducing-instinctual-interactions"></a>Einführung in instinctual Interaktionen
Die Philosophie von einfachen, instinctual Interaktionen wird in der Microsoft Mixed Reality-Plattform Gewebe.  Wir haben drei Schritte aus, um sicherzustellen, dass die Anwendung-Designer und Entwickler einfache und intuitive Interaktionen für ihre Kunden bereitstellen können, erstellt. 

Erstens haben dafür gesorgt, dass unsere erstaunliche Sensoren und Eingabe-Technologie, einschließlich manuell nachverfolgen, Eye-tracking und natürlicher Sprache, in nahtlose Multimodale interaktionsmodellen kombinieren.  Basierend auf unseren Studien entwerfen und entwickeln multimodally – und nicht auf einzelner Eingaben basiert – ist der Schlüssel zum Erstellen von instinctual Funktionen.

Als Nächstes das wissen wir viele Entwickler mehrere Zielgeräten, ob das HoloLens-2 und HoloLens bedeutet (1. Generation) oder HoloLens und VR.  Wir haben so gestaltet, dass unsere interaktionsmodellen, geräteübergreifendes arbeiten (auch wenn die Eingabe-Technologie auf den einzelnen Geräten variiert).  Z. B., weit Interaktion in eine Immersive Windows Kopfhörer mit einem Controller 6DOF und weit Interaktion auf einem HoloLens 2 beide verwenden, die identische visueller Hinweise und dem Muster für geräteübergreifenden Anwendungen zu vereinfachen. Ist nicht nur diesem praktische für Entwickler und Designer, aber natürlich erscheint für Endbenutzer bereitzustellen. 

Schließlich, während wir erkennen, dass es Tausende von effektiven interessanter, magische Interaktionen in MR möglich, wir haben festgestellt, absichtlich mit einer einzelnen Interaktionsmodell End-to-End in eine Anwendung ist die beste Möglichkeit, um sicherzustellen, dass Benutzer erfolgreich und haben Sie eine großartige Erfahrung.  Zu diesem Zweck haben wir drei Dinge in dieser Anleitung für die Interaktion mit einbezogen:
* Wir haben diese Anleitung für die drei interaktionsmodelle mit primären und den Komponenten und Muster, die jeweils erforderliche strukturiert.
* Wir haben zusätzliche Anleitungen zu den anderen Vorteilen, die unsere Plattform bietet eingefügt.
* Wir haben dabei helfen, wählen Sie die entsprechenden Interaktionsmodell für Ihr Szenario eingefügt.


## <a name="three-multimodal-interaction-models"></a>Drei interaktionsmodelle für Multimodale
Basierend auf unseren Untersuchungen von und Arbeiten mit Kunden, Datum, haben wir festgestellt, dass es sich bei drei primäre interaktionsmodelle die Mehrheit der Mixed Reality-Umgebungen anpassen.

In vielerlei Hinsicht ist das Interaktionsmodell des Benutzers mentales Modell zum Ausführen ihrer Flows.  Jedes dieser interaktionsmodelle ist optimiert für einen Satz von Anforderungen des Kunden, und jede ist praktisch, leistungsfähigen und eigenständig verwendet werden. 

Im folgenden Diagramm ist eine vereinfachte Übersicht über.  Ausführliche Informationen für die Verwendung der einzelnen Modelle für die Interaktion ist in den folgenden Seiten, Bilder und Codebeispiele verknüpft.  

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
        <td><strong>Anpassen</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Praktische und tools</a></td>
        <td>3D räumliche Funktionen<br>z. B. räumliche Layout und Entwurf, Bearbeiten von Inhalten oder simulation</td>
        <td>Ideal für neue Benutzer<br>Niedrige Lernkurve<br>In einfachen visual visueller Hinweise an die Hand geben.<br>Konsistente Benutzererfahrung in manuell nachverfolgen und 6 FG-Controller<br>In Kombination mit der Stimme, Eye-Tracking oder Head Blicke hervorragende</td>
        <td>HoloLens 2<br>Windows mit 6DOF Controller Immersive</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Hands-free</a></td>
        <td>Kontextbezogener Umgebungen eines Benutzers Hände, in dem z. B. für die Auftrag-learning, Wartung belegt sind</td>
        <td>Einige erforderlichen lernen<br>Wenn die Hände nicht verfügbar sind.<br>Paare mit Sprach- und natürlicher Sprache</td>
        <td>HoloLens 2<br>HoloLens (1. Generation)<br> Immersive Windows</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Head-Blicke und commit</a></td>
        <td>Per Klick hat z. B. 3D Präsentationen, demos</td>
        <td>Schulung für HMDs jedoch nicht für Mobile erfordert<br>Am besten für Controller, zugegriffen werden kann<br>Am besten für HoloLens (1. Generation)</td>
        <td>HoloLens 2<br>HoloLens (1. Generation)<br> Immersive Windows<br> Mobile AR</td>
    </tr>
</table>
<br>

Die beste Möglichkeit, um sicherzustellen, dass keine Lücken oder Lücken bei der Interaktion für Ihre Umgebung ist, die Anleitung für ein einzelnes Modell von Anfang bis Ende zu befolgen. 

Um den Entwurf und Entwicklung zu beschleunigen, haben wir ausführliche Informationen und Links zu Bildern und Codebeispiele in unsere Abdeckung jedes Modells eingefügt.

Aber zuerst die Schritte zum auswählen und Implementieren eines dieser interaktionsmodelle in den folgenden Abschnitten erläutert.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Am Ende dieser Seite wissen Sie, unsere Leitfäden auf:
 
* Auswählen einer Interaktionsmodell für Ihre Kunden
* Mithilfe der Interaktion Modell Anleitungen
* Übergang zwischen interaktionsmodelle
* Entwurf der nächste Schritte

## <a name="choosing-an-interaction-model-for-your-customer"></a>Auswählen einer Interaktionsmodell für Ihre Kunden

In den meisten Fällen Entwickler und Ersteller verfügen bereits über einige Ideen Beachten Sie die Art der Interaktion geboten, die sie für ihre Benutzer möchten.
Um einen Kunden bezogener Ansatz zum Entwerfen, zu fördern, empfehlen wir, gemäß der Anleitung unten das Interaktionsmodell auswählen, das für Ihre Kunden optimiert ist.

### <a name="why-follow-this-guidance"></a>Befolgen diese Anweisungen, warum?

* Die interaktionsmodelle sind für Ziel und subjektive Kriterien wie z. B. physische und kognitive Zeit-und Intuition und Learnability getestet. 
* Da Interaktion abweicht, können zwischen den interaktionsmodellen auch SEH- und visueller Hinweise und Objektverhalten abweichen.  
* Kombinieren Teile des interaktionsmodelle wird das Risiko von konkurrierenden visueller Hinweise, wie z. B. gleichzeitige Hand Strahlung und einen Cursor Blicke zu entlasten und die Benutzer erstellt.

Hier sind einige Beispiele für wie visueller Hinweise und Verhaltensweisen für die einzelnen Interaktionsmodell optimiert sind.  Wir häufig finden Sie unter neuen Benutzer als ähnliche Fragen, wie z. B. "Wie erfahre ich, das System arbeitet, wie erfahre ich, was kann ich tun, und wie weiß ich, wenn es verstanden gerade getan?"

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
        <td><strong>Wie erfahre ich, es funktioniert?</strong></td>
        <td><strong>Wie erfahre ich, was kann ich tun?</strong></td>
        <td><strong>Wie weiß ich, was gerade demonstriert hat?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Praktische und tools</a></td>
        <td>Ich sehe, dass eine Hand mesh, ich sehe eine fingertippen Unterstützung oder manuell / Controller Strahlung.</td>
        <td>Ich sehe grabbable Handles oder eines umgebenden Felds angezeigt werden, wenn meine Hand in der Nähe befindet.</td>
        <td>Ich Töne hörbar hören und sehen Sie Animationen auf Ziehpunkte und Version.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Head-Blicke und commit</a></td>
        <td>Ich sehe es sich um einen Cursor in der Mitte der meine Sichtfeld.</td>
        <td>Der Cursor Blicke ändert, Status, wenn Sie über bestimmte Objekte.</td>
        <td>Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn Aktionen ausgeführt werden.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Physisch (Blicke und Dwell)</a></td>
        <td>Ich sehe es sich um einen Cursor in der Mitte der meine Sichtfeld.</td>
        <td>Ich sehe eine Statusanzeige eingeblendet, wenn ich auf ein Objekt es länger aufhalten.</td>
        <td>Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn Aktionen ausgeführt werden.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Physisch (Voice-Befehle)</a></td>
        <td>Ich sehe ein Indikator überwacht und Untertiteln für Hörgeschädigte, die zeigen, was das System gehört.</td>
        <td>Erhalte ich Sprachansagen und Hinweise.  Wenn ich sage "Was ich sagen können?" Ich sehe Feedback.</td>
        <td>Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn ich einen Befehl erhalten, oder rufen zur mehrdeutigkeitsvermeidung UX bei Bedarf.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Im folgenden finden Sie Fragen, die wir Hilfe Teams wählen ein Interaktionsmodell gefunden haben:
 
1.  Q:  Möchten meine Benutzer Hologramme touch und holographic Manipulationen mit einfacher Genauigkeit ausführen?
A:  Wenn dies der Fall ist, checken Sie das Interaktionsmodell Hände und Tools für die Genauigkeit als Ziel und-Bearbeitung in die Hände oder während der Übertragung Controller aus.
 
2.  Q:  Müssen meine Benutzer, wenn sich kostenlos, für wirklichkeitsgetreue Aufgaben zu halten?
A:  Wenn dies der Fall ist, sehen Sie sich das Interaktionsmodell Hands-Free, das physisch rundum durch Interaktionen Blicke und sprachbasierten bereitstellt.
 
3.  Q:  Haben meine Benutzer noch Zeit, um Interaktionen für meine mixed Reality-Anwendung zu erfahren, oder benötigen sie die Interaktionen mit der niedrigsten Lernkurve möglich?
A:  Das Modell Hände und Tools für die niedrigste Lernkurve und die intuitivste Interaktionen, wird empfohlen, solange der Benutzer sich für die Interaktion verwenden können.
 
4.  Q:  Werden meine Benutzer während der Übertragung Controller für verweist und-Bearbeitung verwendet?
A:  Das praktische und Tools umfasst alle Anleitungen für die Erfahrung mit der Motion-Controller.
 
5.  Q:  Verwenden meine Benutzer einen Zugriff auf Controller oder eine allgemeine Bluetooth-Controller, z. B. eine Clicker?
A:  Es wird empfohlen, das Head-Blicke und Commit-Modell für alle Controller im nicht nachverfolgt.  Es wurde entwickelt, damit der Benutzer eine gesamte Erfahrung mit einer einfachen "" Target "und" Commit "Mechanikers durchlaufen kann. 
 
6.  Q: Status meine Benutzer nur über eine Benutzeroberfläche von "bei der Betrachtung" (z. B. in einer 3d Diaschau-ähnliche Umgebung), im Gegensatz zu dichten Layouts von UI-Steuerelementen zu navigieren?
A:  Wenn Benutzer nicht um einen Großteil der Benutzeroberfläche steuern müssen, bietet Head-Blicke und Commit eine learnable Option, in dem Benutzer keine Zielgruppenadressierung kümmern. 
 
7.  Q:  Meine Benutzer verwenden Sie beide HoloLens (1. Generation) und HoloLens 2 / Immersive Windows (VR Headsets) A:  Da Head-Blicke und Commit ist das Interaktionsmodell für HoloLens (der 1. Generation), es wird empfohlen, die Entwickler, die HoloLens unterstützt (1. Generation) Head-Blicke verwenden und einen commit für alle Features oder Modi, die Benutzer auf eine HoloLens auftreten können (der 1. Generation) Kopfhörer.  Finden Sie im nächsten Abschnitt unten auf *Übergang interaktionsmodelle* ausführliche Informationen zum Erstellen einer überzeugenden Umgebung für mehrere Generationen von HoloLens.
 
8.  Q: Wie sieht es für Benutzer, die in der Regel mobile (deckt einen großen Speicherplatz oder Verschieben zwischen Leerzeichen), sind im Vergleich zu Benutzer, die in der Regel in einem einzelnen Leerzeichen arbeiten?  
A:  Keines der interaktionsmodelle funktioniert für diese Benutzer.  

> [!NOTE]
> Weitere Anleitungen, die speziell für app-Design [bald](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Übergang von interaktionsmodellen
Es gibt auch Fälle, in dem Ihre Anwendungsfälle, die Nutzung von mehr als ein Interaktionsmodell möglicherweise erfordern.  Z. B. Erstellung Ihrer app "Datenfluss" nutzt das Interaktionsmodell Hände und Tools, aber Sie einen Modus physisch für Außendiensttechniker verwenden möchten.  

Wenn Ihre Umgebung interaktionsmodelle erforderlich ist, haben wir festgestellt, dass es sich bei viele Endbenutzer um einen Übergang aus einem Modell in ein anderes – insbesondere Benutzer gedacht, die MR schwierigkeiten auftreten können.

> [!Note]
> Damit können die Anleitung-Designern und Entwicklern über Optionen, die in MR schwierig sein können, arbeiten wir an weitere Anleitungen zur Verwendung von interaktionsmodelle.
 

## <a name="see-also"></a>Siehe auch
* [Head-Blicke und commit](gaze-and-commit.md)
* [Direkte Bearbeitung](direct-manipulation.md)
* [Punkt- und commit](point-and-commit.md)
* [Anvisieren](gaze-targeting.md)
* [Gesten](gestures.md)
* [Sprachentwurf](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Gestaltung von räumlicher Abbildung](spatial-mapping-design.md)
* [Komfort](comfort.md)
