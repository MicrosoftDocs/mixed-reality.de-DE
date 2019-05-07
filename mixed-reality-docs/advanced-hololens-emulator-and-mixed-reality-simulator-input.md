---
title: Erweiterte HoloLens-Emulator und Mixed Reality-Simulator-Eingabe
description: Ausführliche Anweisungen für die Verwendung der Tastatur, Maus und Xbox-Controller Eingaben für den Emulator für HoloLens und Windows Mixed Reality-Simulator zu simulieren.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, Emulator, Simulation, die Windows Mixed Reality
ms.openlocfilehash: 6ea493d8c1269ff0bea1d4102b9e224e30d06aef
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580591"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Erweiterte HoloLens-Emulator und Mixed Reality-Simulator-Eingabe

Die meisten Emulator-Benutzer müssen nur die grundlegenden Eingabesteuerelemente für verwenden die [Emulator für HoloLens](using-the-hololens-emulator.md#basic-emulator-input) oder [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Die folgenden Details sind für erfahrene Benutzer, die Notwendigkeit, komplexe Typen der Eingabe zu simulieren gefunden haben.


## <a name="concepts"></a>Konzepte

Informationen zum Einstieg die virtuelle Eingabe für den Emulator für HoloLens und Windows Mixed Reality-Simulator steuern zu können, sollten Sie über einige Konzepte kennen.

Während der Übertragung bezieht sich auf steuern und ändern Position und Ausrichtung eines Elements in der Szene. Für ein Zielobjekt steuerbar wird während der Übertragung mit Drehung und Übersetzung (Bewegung) entlang der drei Achsen gesteuert.
* **Yaw bezeichnet**: Aktivieren Sie nach links oder rechts.
* **Schriftbreite**: Aktivieren Sie nach oben oder unten.
* **Zurücksetzen**: Setzen Sie die Seite-an-Seite.
* **X**: Nach links oder rechts.
* **Y**: Nach oben oder unten.
* **Z**: Verschoben Sie vorwärts oder rückwärts.

[Geste](gestures.md) und Eingabe der Motion-Controller eng zugeordnet sind, wie sie physische Geräte:
* **Aktion**: Dies simuliert, dass die Aktion aus, drücken die Zeigefinger, um das Thumb-Steuerelement, oder ziehen die Schaltfläche "Aktion" auf einem Domänencontroller. Die Eingabe für die Aktion kann z. B. verwendet werden, um die tippbewegung Geste zum Scrollen durch Inhalt bis zum Drücken und halten zu simulieren.
* **[Bloom](gestures.md#bloom)/System-Geste oder Home**: Die HoloLens Bloom/System-Geste oder einen Controller für die Schaltfläche "Home" wird an die Shell zurückgegeben und System-Aktionen verwendet.

Praktische haben eine umfangreiche Reprresentation in HoloLens 2.  Verfolgt/nicht überwachte, bereitgestellt und fahrbedingungen Gesten, sondern haben praktische jetzt ein articulated Skelett-Modell angepasst werden und für den Entwickler verfügbar gemacht.  Dies führt zu 26 nachverfolgten Punkte auf jeder Seite.  
* **Joint**: Einer der 20 nachverfolgten Positionen für eine bestimmte nachverfolgten Hand. Dies hat einen Punkt 3D-Raum zugeordnet ist.
* **Pose**: Eine vollständige Auflistung aller der Gelenke in einer nachverfolgten Hand. Zu diesem Zeitpunkt ist dies eine Auflistung von 26 Joints. 

Zu diesem Zeitpunkt machen wir direkte Kontrolle der einzelnen gemeinsamen Position einzeln über die Benutzeroberfläche des Emulators, Sie nicht, wenn Sie diese durch die Simulation API festlegen können. Stattdessen haben wir eine Reihe von nützlich repräsentativ ist, die der Emulator zwischen wechseln kann.

Sie können auch den Status des simulierten Sensoreingaben steuern:
* **Zurücksetzen**: Dies gibt alle simulierte Sensoren auf ihre Standardwerte zurück.  Ab der 2-Emulator für HoloLens, kann ein Zurücksetzen zu einem oder beiden praxisorientierten heruntergebrochen werden machen, wenn die gewünschte Hand(s) mithilfe der entsprechenden Modifizierer Schlüssel oder die Tasten (links bzw. rechts Alt oder Stoßstange linken bzw. rechten auf den Gamepad).
* **Nachverfolgen von**: Wechselt zwischen den Modi mit Feldern fester Breite nachverfolgen. Dazu zählen:
  * **Standard**: Das Betriebssystem wählt die beste Modus zum Nachverfolgen von basierend auf Anforderungen des Systems.
   * **Ausrichtung**: Erzwingt, dass nur Ausrichtung nachverfolgen, unabhängig von den Anforderungen des Systems.
   * **Positional**: Erzwingt, dass mit Feldern fester Breite nachverfolgen, unabhängig von den Anforderungen des Systems.

## <a name="types-of-input"></a>Arten von Eingaben

Die folgende Tabelle zeigt wie jede von Art Eingabe zugeordnet, der Tastatur, Maus und Xbox-Controller. Jeder Typ verfügt über keine andere Zuordnung abhängig vom Steuerelement Modus; Weitere Informationen zu Eingabesteuerelement Modi wird weiter unten in diesem Dokument bereitgestellt.

|  |  Tastatur |  Maus |  Xbox-controller | 
|----------|----------|----------|----------|
|  Schwenken |  Nach links / rechts-Taste |  Ziehen Sie nach links / rechts |  Ministick von rechts nach links / rechts | 
|  Nickwinkel |  Nach oben / nach-unten-Taste |  Ziehen Sie nach oben / unten |  Ministick nach oben / unten rechts | 
|  Roll |  F / E |  |  Steuerkreuz nach links / rechts | 
|  X |  A / D |  |  Linken Ministick links / rechts | 
|  „Y“ zugeordnet ist |  Seite nach oben / nach-unten-Seiten |  |  Steuerkreuz hoch- / Herunterskalieren | 
|  Z |  W / S |  |  Linken Ministick hoch- / Herunterskalieren | 
|  Aktion |  Die EINGABETASTE oder LEERTASTE |  Rechte Schaltfläche |  Eine Schaltfläche oder beide trigger | 
|  Bloom/System |  F2 oder Windows-Taste |  |  B-Taste | 
|  Controller Ziehpunkt-Schaltfläche |  G  |  |  | 
|  Controller-Schaltfläche |  M  |  |  | 
|  Controller Touchpad touch |  U  |  |  | 
|  Drücken Sie die Controller-touchpad |  P  |  |  | 
|  Drücken Sie die Controller-Ministick |  K  |  |  | 
|  Linken zustandsnachverfolgung controller |  F9 |  |  | 
|  Richtige zustandsnachverfolgung controller |  F10 |  |  | 
|  Seite 'Schließen' Haltung | 7 |  |  |
|  Übergeben von "Open" Haltung (Standard) | 8 |  |  |
|  Seite "Zeigen" Haltung | 9 |  |  |
|  Seite 'Verkleinern' Haltung | 0 |  |  |
|  Zurücksetzen |  ESC-Taste |  |  Starttaste | 
|  Nachverfolgung |  T oder F3 |  |  X-Taste | 


Hinweis: Die Controller-Schaltflächen können es sich um die Zielgruppe einer Hand/Controller oder die andere mit der Hand, die Modifizierer für sein.

## <a name="targeting"></a>Zielbestimmung 

Einige der oben genannten Eingabe Konzepte bereitstellen, auf ihre eigenen.  Aktion "," Bloom/System "," Zurücksetzen "und" nachverfolgung sind vollständige Konzepte, ist nicht erforderlich und sind nicht betroffen, weiteren Modifizierer für die Zielplattform.  Die übrigen Konzepte können jedoch auf eine der mehrere Ziele angewendet werden. Wir haben Methoden zum angeben, das Ziel bestimmt, die auf der Befehl angewendet werden soll, eingeführt.  In allen Fällen ist es möglich, über die Benutzeroberfläche oder über die Tastatur drückt, auf welchen Objekttyp Sie Targtet angeben.  In einigen Fällen ist es auch möglich, direkt mit dem Xbox-Controller anzugeben. 

In der folgende Tabelle werden die Optionen für die Zielgruppenadressierung und die Möglichkeit zum Aktivieren aller beschrieben.

| Objekt | Tastatur-Modifizierer | Controller-Modifizierer | Modifizierer für Emulator-Benutzeroberfläche |
|----------|----------|----------|----------|
| Text | (Standard) | (Standard) | (Standard) |
| Head | Halten Sie H | (Nicht verfügbar) | (Nicht verfügbar) |
| Linken/Controller | Halten Sie gedrückt, linke ALT-Taste | Halten Sie gedrückt, linken Schulter | Linken PIN | 
| Rechte/Controller | Halten Sie Rechte ALT-Taste gedrückt | Halten Sie richtige Schulter | Rechte PIN |
| Augen | Halten Sie Y | (Nicht verfügbar) | Augen PIN |
  
Die folgende Tabelle zeigt, wie jeder Modifizierer Ziel aller zu den kernkonzepten Bewegung Eingabe zugeordnet

|  | Standard (Text) |  Manuell/Controller (halten Sie Alt, halten Gamepad Schulter Schaltfläche oder Umschaltfläche UI PIN) |  Hauptknoten (halten H)  |  Augen (Y enthalten oder ein-/ausschalten UI-PIN) |
|----------|----------|----------|----------|
|  Schwenken |  Aktivieren Sie Text ein, nach links / rechts |  Verschieben von Hand links / rechts |  Aktivieren von Head links / rechts | Eye Blicke sucht nach links/rechts |
|  Nickwinkel |  Aktivieren von Head hoch- / Herunterskalieren |  Verschieben von Hand hoch- / Herunterskalieren |  Aktivieren von Head hoch- / Herunterskalieren | Eye Blicke sieht nach oben/unten aus. | 
|  Roll |  Zurücksetzen von Head links / rechts |  |  Zurücksetzen von Head links / rechts | (Keine Aktion) |
|  X |  Folie Text links / rechts |  Verschieben von Hand/Controller-links / rechts |  Aktivieren von Head links / rechts | (Keine Aktion) |
|  „Y“ zugeordnet ist |  Verschieben Sie Text ein, nach oben / unten |  Verschieben von Hand/Controller hoch- / Herunterskalieren |  Aktivieren von Head hoch- / Herunterskalieren | (Keine Aktion) |
|  Z |  Verschieben von Text Vorwärts / rückwärts |  Manuell/Controller Vorwärts / Rückwärts verschieben |  Aktivieren von Head hoch- / Herunterskalieren | (Keine Aktion) |
 
 
## <a name="controlling-an-app"></a>Steuern von einer app

Die folgende Gruppe von Steuerelementen wird für die alltägliche Verwendung empfohlen:

|  Vorgang |  Tastatur und Maus |  Controller | 
|----------|----------|----------|
|  Text X |  A / D |  Linken Ministick links / rechts | 
|  Text Y |  Seite nach oben / nach-unten-Seiten |  Steuerkreuz hoch- / Herunterskalieren | 
|  Text Z |  W / S |  Linken Ministick hoch- / Herunterskalieren | 
|  Text Yaw |  Die Maus ziehen nach links / rechts |  Ministick von rechts nach links / rechts | 
|  Head Yaw bezeichnet. |  H + Ziehen mit der Maus nach links / rechts |  H (auf der Tastatur) + Ministick von rechts nach links / rechts | 
|  Head-Schriftbreite |  Ziehen Sie Maus nach oben / unten |  Ministick nach oben / unten rechts | 
|  Head zurücksetzen |  F / E |  Steuerkreuz nach links / rechts | 
|  Manuell/Controller X |  ALT + A / D |  Schulter + linken Ministick links / rechts | 
|  Manuell/Controller Y |  ALT + Bild-oben / nach unten Seite |  Schulter + Steuerkreuz hoch- / Herunterskalieren | 
|  Manuell/Controller Z |  ALT + W / S |  Schulter + linken Ministick hoch- / Herunterskalieren | 
|  Manuell/Controller Yaw |  Alt + Ziehen mit der Maus nach links / rechts |  Schulter + Ministick von rechts nach links / rechts | 
|  Manuell/Controller Tonhöhe |  Alt + Ziehen mit der Maus nach oben / unten |  Schulter + Ministick nach oben / unten rechts | 
|  Manuell/Controller ein |  ALT + Q / E |  Schulter + Steuerkreuz nach links / rechts | 
|  Aktion |  Rechtsklick |  Trigger | 
|  Bloom / System / Home |  F2 oder Windows-Taste |  B-Taste | 
|  Zurücksetzen |  Beenden |  Starttaste | 
|  Nachverfolgung |  T |  X-Taste | 
|  Bildlauf |  ALT + nach-rechts-Maustaste, und ziehen Sie die Maus nach oben / unten |  Schulter, Trigger und Ministick nach oben / unten rechts | 
|  Rotieren Sie verschieben/schneller | Linke oder Rechte UMSCHALTTASTE | Drücken Sie und halten Sie die richtigen Ministick |
|  Langsame verschieben und drehen | Linke oder rechte STRG-Taste | Drücken Sie und halten Sie den linken Ministick |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Perception Systemsteuerung für die Simulation von Tastenkombinationen

Die folgenden Tastenkombinationen stehen für den Zugriff auf die Wahrnehmung Simulation-Systemsteuerung, und aktivieren, oder Deaktivieren für Eingabegeräte PC verwenden, mit Simulation.

| Vorgang | Tastenkombination | Beschreibung/Hinweise |
|-----------|----------|-------------|
| Umschalten Sie "Verwenden der Tastatur für die Simulation" | F4 | Wenn deaktiviert, wird Tastatureingaben an die HoloLens oder Windows Mixed Reality-Anwendung ein. |
| Umschalten Sie "Verwenden der Maus für die Simulation" | F5 | Wenn deaktiviert, wird die Mauseingabe der Mixed Reality-Umgebung (Windows Mixed Reality nur) |
| Umschalten Sie "Verwenden von Gamepad für die Simulation" | F6 | Wenn deaktiviert, wird Gamepad-Eingabe durch Simulation ignoriert. |
| Anzeigen oder Ausblenden der Systemsteuerung | F7 | |
| Legen Sie den Tastaturfokus auf die Systemsteuerung | F8 | Wenn der Bereich nicht derzeit angezeigt wird. wird es zuerst angezeigt. |
| Docken Sie an oder docken Sie Bereich in und aus den Emulator oder das Fenster Mixed Reality-Portal ab | F9 | Wenn das Fenster geschlossen wird, wenn abgedockt, dabei handelt es sich angedockt ausgeblendet. |

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Verwenden des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md)
