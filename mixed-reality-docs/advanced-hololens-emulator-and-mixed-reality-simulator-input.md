---
title: Erweiterte HoloLens-Emulator und Mixed Reality-Simulator-Eingabe
description: Ausführliche Anweisungen für die Verwendung der Tastatur, Maus und X-Box-Controller Eingaben für den Emulator für HoloLens und Windows Mixed Reality-Simulator zu simulieren.
author: ChimeraScorn
ms.author: cwhite
ms.date: 02/24/2018
ms.topic: article
keywords: HoloLens, Emulator, Simulation, die Windows Mixed Reality
ms.openlocfilehash: 59bea340a2ecdd2d65481c9ace4ab3f0bf15bc6f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593365"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Erweiterte HoloLens-Emulator und Mixed Reality-Simulator-Eingabe

Die meisten Emulator-Benutzer müssen nur die grundlegenden Eingabesteuerelemente für verwenden die [Emulator für HoloLens](using-the-hololens-emulator.md#basic-emulator-input) oder [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Die folgenden Details sind für erfahrene Benutzer, die Notwendigkeit, komplexe Typen der Eingabe zu simulieren gefunden haben.

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

## <a name="concepts"></a>Konzepte

Informationen zum Einstieg die virtuelle Eingabe auf den Emulator für HoloLens und Windows Mixed Reality-Simulator steuern zu können, sollten Sie über einige Konzepte kennen.

Während der Übertragung bezieht sich auf steuern und ändern Position und Ausrichtung eines Elements in der Szene. Für ein Zielobjekt steuerbar wird während der Übertragung mit Drehung und Übersetzung (Bewegung) entlang der drei Achsen gesteuert.
* **Yaw bezeichnet**: Aktivieren Sie nach links oder rechts.
* **Schriftbreite**: Aktivieren Sie nach oben oder unten.
* **Zurücksetzen**: Setzen Sie die Seite-an-Seite.
* **X**: Nach links oder rechts.
* **Y**: Nach oben oder unten.
* **Z**: Verschoben Sie vorwärts oder rückwärts.

[Geste](gestures.md) und Eingabe der Motion-Controller eng zugeordnet sind, wie sie physische Geräte:
* **Aktion**: Dies simuliert, dass die Aktion aus, drücken die Zeigefinger, um das Thumb-Steuerelement, oder ziehen die Schaltfläche "Aktion" auf einem Domänencontroller. Die Eingabe für die Aktion kann z. B. verwendet werden, um die tippbewegung Geste zum Scrollen durch Inhalt bis zum Drücken und halten zu simulieren.
* **[Bloom](gestures.md#bloom) oder Startseite**: Die HoloLens blühen Geste oder eines Controllers Schaltfläche "Home" wird verwendet, um an die Shell zurückgegeben und Systemaktionen ausführen.

Praktische haben eine umfangreiche Reprresentation in HoloLens V2.  Verfolgt/nicht überwachte, bereitgestellt und fahrbedingungen Gesten, sondern haben praktische jetzt ein articulated Skelett-Modell angepasst werden und für den Entwickler verfügbar gemacht.  Dies führt zu 20 nachverfolgten Punkt auf jeder Seite.  
* **Joint**: Einer der 20 nachverfolgten Positionen für eine bestimmte nachverfolgten Hand. Dies hat einen Punkt 3D-Raum zugeordnet ist.
* **Pose**: Eine vollständige Auflistung aller der Gelenke in einer nachverfolgten Hand. Zu diesem Zeitpunkt ist dies eine Auflistung von 20 Joints. 

Zu diesem Zeitpunkt stellen wir keine direkten Kontrolle des einzelnen gemeinsamen Positionen einzeln über die Benutzeroberfläche des Serveremulators bereit. Sie können diese jedoch durch die Simulation API festlegen. Stattdessen haben wir eine Reihe von nützlich repräsentativ ist, die der Emulator zwischen wechseln kann.

Sie können auch den Status des simulierten Sensoreingaben steuern:
* **Zurücksetzen**: Dies gibt alle simulierte Sensoren auf ihre Standardwerte zurück.
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
|  Blühen |  F2 oder Windows-Taste (Windows-Taste funktioniert nur mit dem Emulator für HoloLens) |  |  B-Taste | 
|  Controller Ziehpunkt-Schaltfläche |  G (Windows Mixed Reality nur Simulator) |  |  | 
|  Controller-Schaltfläche |  M (Windows Mixed Reality nur Simulator) |  |  | 
|  Controller Touchpad touch |  U (Windows Mixed Reality nur Simulator) |  |  | 
|  Drücken Sie die Controller-touchpad |  P (Windows Mixed Reality nur Simulator) |  |  | 
|  Festlegen von Hand Haltung | 7, 8, 9 oder 0 |  |  |
|  Zurücksetzen |  ESC-Taste |  |  Starttaste | 
|  Nachverfolgung |  T oder F3 |  |  X-Taste | 


Hinweis: Nur die Windows Mixed Reality-Simulator können die Controller-Schaltflächen Zielgruppe einerseits oder die andere mit der Hand, die Modifizierer für sein.

## <a name="targeting"></a>Zielbestimmung 

Einige der oben genannten Eingabe Konzepte bereitstellen, auf ihre eigenen.  Aktion, Bloom, Zurücksetzen von Kennwörtern und nachverfolgung sind vollständige Konzepte, ist nicht erforderlich und sind nicht betroffen, weiteren Modifizierer für die Zielplattform.  Die übrigen Konzepte können jedoch auf eine der mehrere Ziele angewendet werden. Wir haben Methoden zum angeben, das Ziel bestimmt, die auf der Befehl angewendet werden soll, eingeführt.  In allen Fällen ist es möglich, über die Benutzeroberfläche oder über die Tastatur drückt, auf welchen Objekttyp Sie Targtet angeben.  In einigen Fällen ist es auch möglich, direkt mit dem Xbox-Controller anzugeben. 

In der folgende Tabelle werden die Optionen für die Zielgruppenadressierung und die Möglichkeit zum Aktivieren aller beschrieben.

| Objekt | Tastatur-Modifizierer | Controller-Modifizierer | Modifizierer für Emulator-Benutzeroberfläche |
|----------|----------|----------|----------|
| Text | <default> | <default> | <default> |
| Head | Halten Sie H | <None available> | Head-PIN in der Benutzeroberfläche |
| Linken/Controller | Linke Alt-Schaltfläche | Linken Schulter-Schaltfläche | Linken PIN | 
| Rechte/Controller | Rechte ALT-Taste Schaltfläche | Schaltfläche "rechts Schulter" | Rechte PIN |
| Augen | Halten Sie Y | <No contoller modifier available> | Augen PIN |
  
Die folgende Tabelle zeigt, wie jeder Modifizierer Ziel aller zu den kernkonzepten Bewegung Eingabe zugeordnet

|  Standard (Text) |  Manuell/Controller (halten Sie Alt / aufnehmen) |  Hauptknoten (halten H)  |  Augen (halten Y) |
|----------|----------|----------|----------|
|  Schwenken |  Aktivieren Sie Text ein, nach links / rechts |  Verschieben von Hand links / rechts |  Aktivieren von Head links / rechts | Eye Blicke sucht nach links/rechts |
|  Nickwinkel |  Aktivieren von Head hoch- / Herunterskalieren |  Verschieben von Hand hoch- / Herunterskalieren |  Aktivieren von Head hoch- / Herunterskalieren | Eye Blicke sieht nach oben/unten aus. | 
|  Roll |  Zurücksetzen von Head links / rechts |  |  Zurücksetzen von Head links / rechts | (Keine Aktion) |
|  X |  Folie Text links / rechts |  Verschieben von Hand/Controller-links / rechts |  Aktivieren von Head links / rechts | (Keine Aktion) |
|  „Y“ zugeordnet ist |  Verschieben Sie Text ein, nach oben / unten |  Verschieben von Hand/Controller hoch- / Herunterskalieren |  Aktivieren von Head hoch- / Herunterskalieren | (Keine Aktion) |
|  Z |  Verschieben von Text Vorwärts / rückwärts |  Manuell/Controller Vorwärts / Rückwärts verschieben |  Aktivieren von Head hoch- / Herunterskalieren | (Keine Aktion) |
 
Hinweis: Nur die Windows Mixed Reality-Simulator können die Controller-Schaltflächen Zielgruppe einerseits oder die andere mit der Hand, die Modifizierer für sein. Ebenso kann nur die HoloLens-Emulators, der Haltung die angezeigte Seite Zielgruppe einerseits oder die andere die Hand-Modifizierer aufweisen. 
 
## <a name="controlling-an-app"></a>Steuern von einer app

In diesem Artikel wurde beschrieben, den vollständigen Satz von Eingabetypen und Eingabemodi an, die in den Emulator für HoloLens und Windows Mixed Reality-Simulator verfügbar sind. Die folgende Gruppe von Steuerelementen wird für die alltägliche Verwendung empfohlen:

|  Vorgang |  Tastatur und Maus |  Controller | 
|----------|----------|----------|
|  Text X |  A / D |  Linken Ministick links / rechts | 
|  Text Y |  Seite nach oben / nach-unten-Seiten |  Steuerkreuz hoch- / Herunterskalieren | 
|  Text Z |  W / S |  Linken Ministick hoch- / Herunterskalieren | 
|  Text Yaw |  Die Maus ziehen nach links / rechts |  Ministick von rechts nach links / rechts | 
|  Head Yaw bezeichnet. |  H + Ziehen mit der Maus nach links / rechts |  H (auf der Tastatur) + Ministick von rechts nach links / rechts | 
|  Head-Schriftbreite |  Ziehen Sie Maus nach oben / unten |  Ministick nach oben / unten rechts | 
|  Head zurücksetzen |  F / E |  Steuerkreuz nach links / rechts | 
|  Hand X |  Alt + Ziehen mit der Maus nach links / rechts |  Schulter + Ministick von rechts nach links / rechts | 
|  Hand Y |  Alt + Ziehen mit der Maus nach oben / unten |  Schulter + Ministick nach oben / unten rechts | 
|  Hand Z |  ALT + W / S |  Schulter + linken Ministick hoch- / Herunterskalieren | 
|  Aktion |  Rechtsklick |  Trigger | 
|  Blühen / Home |  F2 oder Windows-Taste (Windows-Schlüssel ist nur für den Emulator für HoloLens) |  B-Taste | 
|  Zurücksetzen |  Beenden |  Starttaste | 
|  Nachverfolgung |  T |  X-Taste | 
|  Bildlauf |  ALT + nach-rechts-Maustaste, und ziehen Sie die Maus nach oben / unten |  Schulter, Trigger und Ministick nach oben / unten rechts | 

## <a name="see-also"></a>Siehe auch
* [Installieren der tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Verwendung des Simulators Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
