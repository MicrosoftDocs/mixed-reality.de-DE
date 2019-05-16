---
title: Übersicht über die Multimodale Interaktion
description: Übersicht über die Multimodale Interaktion
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität, die Blicke, die Blicke Ziel ist, handelt es sich bei der Interaktion, entwerfen, Hololens, MMR, Multimodal
ms.openlocfilehash: 771ebe44dc984c9d4550638bef405810d86b8d69
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730824"
---
# <a name="introducing-instinctual-interactions"></a>Einführung in instinctual Interaktionen

Die Philosophie von einfachen, instinctual Interaktionen wird in der Microsoft Mixed Reality (MMR)-Plattform, von der Hardware, Software Gewebe.

Diese instinctual Interaktionen nutzen alle verfügbaren Eingabe Technologien, einschließlich auf den Kopf nachverfolgen, die manuell nachverfolgen, Eye-tracking und natürlicher Sprache, in nahtlose Multimodale Interaktion-Modellen. Basierend auf unseren Studien entwerfen und Entwickeln von unbedingt multimodals und nicht basierend auf einzelnen Eingaben beim naheliegende Benutzeroberflächen zu erstellen.

Die Instinctual interaktionsmodelle richten Sie auch auf natürliche Weise Gerätetypen aus.  Z. B. verwenden ganz Interaktion in eine immersive Kopfhörer mit einem 6 Freiheit (FG)-Controller und weit Interaktion auf einem HoloLens 2 die gleichen visueller Hinweise, Muster und Verhaltensweisen.  Ist nicht nur diesem praktische für Entwickler und Designer, aber natürlich erscheint für Endbenutzer bereitzustellen.


Schließlich, während wir erkennen, dass es Tausende von effektiven interessanter, magische Interaktionen in MR möglich, wir haben festgestellt, absichtlich mit einer einzelnen Interaktionsmodell End-to-End in eine Anwendung ist die beste Möglichkeit, um sicherzustellen, dass Benutzer erfolgreich und haben Sie eine großartige Erfahrung.  Zu diesem Zweck haben wir drei Dinge in dieser Anleitung für die Interaktion mit einbezogen:
* Wir haben diese Anleitung für die drei interaktionsmodelle mit primären und den Komponenten und Muster, die jeweils erforderliche strukturiert.
* Wir haben zusätzliche Anleitungen zu den anderen Vorteilen, die unsere Plattform bietet eingefügt.
* Wir haben dabei helfen, wählen Sie die entsprechenden Interaktionsmodell für Ihr Szenario eingefügt.

## <a name="multimodal-interaction-models"></a>Multimodale interaktionsmodelle

Basierend auf unseren Untersuchungen von und Arbeiten mit Kunden, Datum, haben wir drei primäre interaktionsmodelle ermittelt, die die meisten Mixed Reality-Funktionen entsprechen.  

Stellen Sie sich diese interaktionsmodelle als des Benutzers mentales Modell zum Ausführen ihrer Flows.

Jedes dieser interaktionsmodelle ist praktisch, leistungsfähigen und eigenständig verwendet werden, und alle sind optimiert für einen Satz von Anforderungen des Kunden. Zeigen Sie das Diagramm unten, für Szenarien, Beispiele und Vorteile der einzelnen Interaktionsmodell.  

**Modell** | **[Praktische und Tools](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)** | **[Hands free](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)** | **[Blicke und Commit](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**
|--------- | --------------| ------------| ---------|
**Beispielszenarien** | Inhalt von 3D räumliche Funktionen, z. B. räumliche Layout und Entwurf, Bearbeitung oder simulation | Kontextbezogener Umgebungen, in denen eines Benutzers Hände belegt sind, z. B. für die Auftrag-learning, Wartung| Per Klick Umgebungen, z. B. 3D Präsentationen, demos
**Anpassen** | Ideal für neue Benutzer, die gekoppelte Wit-Sprachanrufe, eye-Tracking oder Head Blicke. Niedrige Lernkurve. Konsistente Benutzererfahrung in manuell nachverfolgen und 6 FG-Controller. | Einige learning erforderlich. Wenn Hände nicht verfügbar-Paare, gut mit Sprach- und natürlicher Sprache sind | Müssen Schulungen für HMDs jedoch nicht für Mobile. Am besten für zugänglich Controller am besten für HoloLens (1. Generation) |
**Hardware** | HoloLens 2 Immersive headsets | HoloLens-2-HoloLens (1. Generation) Immersive Headsets | HoloLens 2 Immersive headsets | HoloLens-2-HoloLens (1. Generation) Immersive Headsets Mobile AR |

Ausführliche Informationen für alle verfügbaren Eingaben nahtlos zusammen in jedem Interaktionsmodell mit ist auf den Seiten, die folgen, sowie einige Darstellungen und Links zu Beispielinhalt aus unserer MRTK Unity.


## <a name="choose-an-interaction-model-for-your-customer"></a>Wählen Sie ein Interaktionsmodell für Ihre Kunden


In den meisten Fällen Entwickler und Entwickler auch verfügen bereits über einige Ideen Beachten Sie die Art der Interaktion geboten, die sie ihren Benutzern zuweisen möchten.
Um einen Kunden bezogener Ansatz zum Entwerfen, zu fördern, empfehlen wir, gemäß der Anleitung unten das Interaktionsmodell auswählen, das für Ihre Kunden optimiert ist.

### <a name="why-follow-this-guidance"></a>Befolgen diese Anweisungen, warum?

* Die interaktionsmodelle sind für Ziel und subjektive Kriterien wie z. B. physische und kognitive Zeit-und Intuition und Learnability getestet. 
* Da Interaktion abweicht, können zwischen den interaktionsmodellen auch SEH- und visueller Hinweise und Objektverhalten abweichen.  
* Kombinieren Teile des interaktionsmodelle wird das Risiko von konkurrierenden visueller Hinweise, wie z. B. gleichzeitige Hand Strahlung und einen Head-Blicke-Cursor, die überlasten und Benutzer erstellt.

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
        <td><strong>Wie weiß ich, was kann ich tun?</strong></td>
        <td><strong>Wie weiß ich, was gerade demonstriert hat?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Praktische und tools</a></td>
        <td>Ich sehe, dass eine Hand mesh, ich sehe eine fingertippen Unterstützung oder manuell / Controller Strahlung.</td>
        <td>Ich sehe grabbable Handles oder eines umgebenden Felds angezeigt werden, wenn meine Hand in der Nähe befindet.</td>
        <td>Ich Töne hörbar hören und sehen Sie Animationen auf Ziehpunkte und Version.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></td>
        <td>Ich sehe es sich um einen Cursor in der Mitte der meine Sichtfeld.</td>
        <td>Die Head-Blicke Cursor ändert den Zustand beim über bestimmte Objekte.</td>
        <td>Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn Aktionen ausgeführt werden.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Physisch (Head-Blicke und Dwell)</a></td>
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
 
1.  Q:  Möchten meine Benutzer Hologramme touch und holographic Manipulationen mit einfacher Genauigkeit ausführen?<br><br>
A:  Wenn dies der Fall ist, checken Sie das Interaktionsmodell Hände und Tools für die Genauigkeit als Ziel und-Bearbeitung in die Hände oder während der Übertragung Controller aus.
 
2.  Q:  Müssen meine Benutzer, wenn sich kostenlos, für wirklichkeitsgetreue Aufgaben zu halten?<br><br>
A:  Wenn dies der Fall ist, sehen Sie sich das Interaktionsmodell physisch, das physisch rundum durch Interaktionen Blicke und sprachbasierten bereitstellt.
 
3.  Q:  Haben meine Benutzer noch Zeit, um Interaktionen für meine mixed Reality-Anwendung zu erfahren, oder benötigen sie die Interaktionen mit der niedrigsten Lernkurve möglich?<br><br>
A:  Das Modell Hände und Tools für die niedrigste Lernkurve und die intuitivste Interaktionen, wird empfohlen, solange der Benutzer sich für die Interaktion verwenden können.
 
4.  Q:  Werden meine Benutzer während der Übertragung Controller für verweist und-Bearbeitung verwendet?<br><br>
A:  Das praktische und Tools umfasst alle Anleitungen für die Erfahrung mit der Motion-Controller.
 
5.  Q:  Verwenden meine Benutzer einen Zugriff auf Controller oder eine allgemeine Bluetooth-Controller, z. B. eine Clicker?<br><br>
A:  Es wird empfohlen, das Head-Blicke und Commit-Modell für alle Controller im nicht nachverfolgt.  Es wurde entwickelt, damit der Benutzer eine gesamte Erfahrung mit einer einfachen "" Target "und" Commit "Mechanikers durchlaufen kann. 
 
6.  Q: Status meine Benutzer nur über eine Benutzeroberfläche von "bei der Betrachtung" (z. B. in einer 3d Diaschau-ähnliche Umgebung), im Gegensatz zu dichten Layouts von UI-Steuerelementen zu navigieren?<br><br>
A:  Wenn Benutzer nicht um einen Großteil der Benutzeroberfläche steuern müssen, bietet Head-Blicke und Commit eine learnable Option, in dem Benutzer keine Zielgruppenadressierung kümmern. 
 
7.  Q:  Meine Benutzer verwenden Sie beide HoloLens (1. Generation) und HoloLens 2 / Immersive Windows (VR Headsets)<br><br>
A:  Da Head-Blicke und Commit ist das Interaktionsmodell für HoloLens (der 1. Generation), es wird empfohlen, die Entwickler, die HoloLens unterstützt (1. Generation) Head-Blicke verwenden und einen commit für alle Features oder Modi, die Benutzer auf eine HoloLens auftreten können (der 1. Generation) Kopfhörer.  Finden Sie im nächsten Abschnitt unten auf *Übergang interaktionsmodelle* ausführliche Informationen zum Erstellen einer überzeugenden Umgebung für mehrere Generationen von HoloLens.
 
8.  Q: Wie sieht es für Benutzer, die in der Regel mobile (deckt einen großen Speicherplatz oder Verschieben zwischen Leerzeichen), sind im Vergleich zu Benutzer, die in der Regel in einem einzelnen Leerzeichen arbeiten?<br><br>
A:  Keines der interaktionsmodelle funktioniert für diese Benutzer.  

> [!NOTE]
> Weitere Anleitungen, die speziell für app-Design [bald](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Übergang von interaktionsmodellen
Es gibt auch Fälle, in dem Ihre Anwendungsfälle, die Nutzung von mehr als ein Interaktionsmodell möglicherweise erfordern.  Z. B. Erstellung Ihrer app "Datenfluss" nutzt das Interaktionsmodell Hände und Tools, aber Sie einen Modus physisch für Außendiensttechniker verwenden möchten.  

Wenn Ihre Umgebung interaktionsmodelle erforderlich ist, haben wir festgestellt, dass es sich bei viele Endbenutzer um einen Übergang aus einem Modell in ein anderes – insbesondere Benutzer gedacht, die MR schwierigkeiten auftreten können.

> [!Note]
> Damit können die Anleitung-Designern und Entwicklern über Optionen, die in MR schwierig sein können, arbeiten wir an weitere Anleitungen zur Verwendung von interaktionsmodelle.
 

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Direkte Manipulation](direct-manipulation.md)
* [Zeigen und Ausführen](point-and-commit.md)
* [Anvisieren](gaze-targeting.md)
* [Gesten](gestures.md)
* [Sprachentwurf](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Gestaltung von räumlicher Abbildung](spatial-mapping-design.md)
* [Komfort](comfort.md)
