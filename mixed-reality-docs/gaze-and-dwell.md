---
title: Blicke und dwell
description: Übersicht über das Eingabemodell Blicke und dwell
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Gemischte Realität Blicke, Dwell, Interaktion, Entwerfen
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914610"
---
# <a name="gaze-and-dwell"></a>Blicke und dwell

Wenn praktische Tools und Komponenten belegt sind, können die Gesten mühsam oder unmöglich sein.  Sprachbefehle, z. B. Geste können können in bestimmten Situationen unzuverlässig ist, z. B. übermäßig laut ausgelastet sein.  Darüber hinaus Stimme, die Control-Computer ist nicht noch eine grundlegende Interaktion, jedoch ist sicherlich Datenstrom gewinnen!  Blicke Dwell bietet den meistverwendeten und einfachen Master-Mechanismus für die Arbeit Heads-Up physisch auf HoloLens.  Darüber hinaus Blicke Dwell 100-prozentige Zuverlässigkeit ist unabhängig von Rauschen Störungen noch Ruhe-Einschränkungen in der betriebsumgebung.

## <a name="goals"></a>Ziele

Geben Sie einen Mechanismus für die vollständige freisprechgeräte Interaktionen, ohne per Spracheingabe.

## <a name="design-principles"></a>Designprinzipien

1. Es ist kein Blicke Waffe
    
    Blicke erfordert visuelles Feedback für die intuitive Interaktion, aber viel Feedback kann hegen auslösen. Das Feedback tragen, dass einen Benutzer wissen, was sie, aber keine automatische Auswahl für ihre Absichten als Ziel verwendet werden. Lesen von Text erfordert zusätzlich zu einem Benutzer Raum um die Informationen vor der Auswahl der absorb ist zu berücksichtigen.
    
2. Seek-Goldlöckchen Geschwindigkeit
    
    Die Füllung Dwell haben verschiedene Zeitgeber, die basierend auf Auswirkung der Navigation – häufig verwendete Funktionen profitieren davon, in der Regel schnellere ausfüllen, während mehr Fill-Mal mehr Folgeschäden Funktionen profitieren können. Animation-Kurven der Füllfarbe können einen Eindruck, schnellere Füllung werde, positiv beeinflussen. Berücksichtigt sind, um die Entscheidung des Benutzers aus Fast/Mittel/langsame aktivieren Geschwindigkeit Außerkraftsetzungen zu füllen.
    
3. Sagen Sie forschungspseudocode zu Yo-yo Auswirkung

    Die Yo-yo Auswirkung (auch bekannt als "nachts auf die Roxbury") ist ein unbequem Muster, die aus der bestimmten Platzierung von Inhalt und Blicke-basierten Steuerelementen auf den Markt kommen kann. Eine Liste Navigationsbereich mit der Fill-Schaltfläche am unteren Rand werden z. B. eine Schleife von - Suchen nach unten länger aufhalten, Ergebnisse suchen, suchen Sie nach unten Dwell usw. ausgelöst. Dieses resultierende Muster unangenehm ist, und sollte vermieden werden, indem Sie die Navigationssteuerelemente an einem zentralen Ort, der kleiner hin und her erfordert platzieren. Platzierung von Dwell Schaltflächen relativ zu deren Auswirkungen wichtig für Komfort.

## <a name="ui-patterns"></a>UI-Muster

### <a name="high-frequency-buttons"></a>Hohe Auslastung Schaltflächen
    
* Nächste/Back-Schaltflächen
  * Sehr kurze Verzögerung vor füllen (Flyover Flimmern Puffer)
  * Größere Schaltflächen sind leichter zu bedienen mit Blicke
  * Gut, die unter die Augen Höhe behalten Sie also keinen Hinweis auf die Belastung für die Interaktion
  * Dwell Region kann größer als inaktiv Symbol zu erleichtern (zurück) zu verwenden sein.

### <a name="low-frequency-buttons"></a>Niedrige Auslastung von Schaltflächen
    
* Menü "Einstellungen" aktivieren
  * Mehr Verzögerung vor Füllung OK (Flyover Flimmern Puffer)
  * Versuche, diese Schaltflächen Bildschirmen häufig Cursor Wege zu halten.

* Bestätigungen (d. h. Überprüfung Flow, Dialogfelder)
  * Markierung der auf Hauptschaltfläche anzeigen
  * Anzeigen von länger aufhalten Ziel gleichzeitig Auswahl hervorheben
  * Verwendung länger aufhalten Ziel im Zusammenhang mit Symbol, um die Benutzeroberfläche einfach zu halten
  * Wichtige Entscheidung, damit keine Hervorhebung zu aktivieren, werden Dwell Ziel für eine nochmalige Überlegung Zeitraum angezeigt.
        
### <a name="toggle-buttons"></a>Umschaltflächen

* Pin
  * Clear aktiver/inaktiver visuellen Zustand
  * Radiale Füllung hilft Benutzer, den Fokus und natürliche Status angezeigt 

* Individuelle Einstellungen
  * Clear aktiven/inaktiven Status
  * Länger aufhalten Sie Zielen alle auf der linken umgebenden-Symbol
  * Dwell ausgerichtet ist, nur erscheinen, bei der Auswahl aktiv markieren
  * "Länger aufhalten Schieberegler" rechts für ein-und Einstellungen

### <a name="list-views"></a>Listenansichten

* Browsen Listenansicht - Guide-Dateien zu öffnen
  * Cursor-Highlights Zeile aus an einer beliebigen Stelle in Zeile aber Dwell beginnt nicht
  * Wenn Zeilen vom Cursor markiert ist, wird angezeigt, Dwell Ziel links
  * Länger aufhalten Sie Ziel immer ein Kreis auf der linken Seite des Textes in allen Listenansichten
  * Zeigen Sie nicht mehr an, dass alle Ziele auf einmal zur Vermeidung von Benutzeroberfläche länger aufhalten
  * Nutzen Sie das gleiche Muster zum Einrichten von UX-Kenntnisse
        
* Listenansicht - Hierarchie der Aufgaben/Schritte im Leitfaden durchsuchen
  * Länger aufhalten Sie Ziel immer ein Kreis auf der linken Seite des Textes
  * Reduzieren/Erweitern länger Unterstützung aufhalten.
        
* Listenansicht Durchsuchen - Modus auswählen
  * Verwenden Sie die Muster, die über hergestellt

### <a name="contextual-buttons"></a>Kontextbezogene Schaltflächen

* Ein-/3D - zeigt sich in 3D entlang Objektivdeckel in der Nähe Hologramme 
  * Clear aktiver/inaktiver visuellen Zustand

### <a name="pivots"></a>Pivots

* Liste der zuletzt Choice-oder All-Handbücher
  * Geben Sie die UI-Unterstützung, die verbleibt, um anzugeben, welcher Registerkarte aktiv ist.
  * Für kurze Worts Pivots ausgewählt haben wir auf das Dwell Ziel-Muster zu verzichten
  * Wir sitzungsauthentifizierungsmodul bevorzugt die vereinfachte Schnittstelle eine andere 2 Kreis Ziele und eine größere Benutzeroberfläche
  * In diesem Fall werden die Wörter kurz genug, dass eine Verzögerung genügend bequem vor dem Ausfüllen bereitstellt


## <a name="ux-guidelines-and-best-practices"></a>UX-Richtlinien und bewährte Methoden

### <a name="target-sizes"></a>Zielgrößen

  * Minimale Größe des Pin-Symbol: 6cm im Raum der Welt in Unity 30 MRUs (30cm @ 2m)
  * Gibt die Ziele, die "magnetisiert" oder "dauerhaft" überhaupt? (d. h. bestaunen Cursor Glättung)

### <a name="animation"></a>Animation

  * Verzögerung vor Dwell visual Trigger .5sec
  * Dauer der Dwell Visual 1,2 s
  * Die Kurve für Animation?

### <a name="visual-feedback"></a>Visuelles Feedback

  * Radiale Füllen von Blicke Start Cursorposition
  * Immer radiale Füllung aus der Mitte der Schaltfläche. Eine konsistente Antwort ist weniger verwirrend, als alle anderen Anweisungen für verschiedene Schaltflächen. 
    * Mit dieser Regel kann jedoch für den direktionalen Interaktionen (z. B. Nav nach-oben/nach unten/links/rechts, usw.) unterbrochen werden. Z. B. rechts Anleitungen wird eine Ausnahme auf die nächste/BACK verlassene gefüllt.
    * Betrachten Sie Invertieren von radialen Füllen von außerhalb (bei off umschalten) aus. Die inverse Eindruck, eine Schaltfläche ist ein praktisches visual Muster zu verwalten. 

### <a name="progressive-disclosure"></a>Schrittweise Anzeige von

 * Schrittweise Anzeige von bedeutet, dass das Ziel Dwell Hervorhebung (z. B. in einem Listensteuerelement) angezeigt wird
 * Highlights von Text-Leiste mit Spotlight anzuzeigen auf Blicke an einer beliebigen Stelle auf text
 * Blicke Füllung Ziel wird immer angezeigt, auf der linken Seite, jedoch nur für das Element der Liste die hervorgehoben ist
 * Versuchen Sie es, um zu vermeiden, dass alle Dwell Ziele auf jederzeit aufgrund eines wiederholten Aussehen des gestapelten Kreise
 
 ## <a name="see-also"></a>Siehe auch
* [Direkte Bearbeitung](direct-manipulation.md)
* [Punkt- und commit](point-and-commit.md)
* [Interaktionsgrundlagen](interaction-fundamentals.md)
* [Head-Blicke und commit](gaze-and-commit.md)
* [Blicke und Sprache](voice-design.md)
