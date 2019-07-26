---
title: Erweiterte hololens-Emulator-und gemischte Reality-simulatoreingaben
description: Ausführliche Anweisungen für die Verwendung des Tastatur-, Maus-und Xbox-Controllers zum Simulieren von Eingaben für den hololens-Emulator und den Windows Mixed Reality-Simulator.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: Hololens, Emulator, Simulation, gemischte Windows-Realität
ms.openlocfilehash: 6ea493d8c1269ff0bea1d4102b9e224e30d06aef
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580591"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Erweiterte hololens-Emulator-und gemischte Reality-simulatoreingaben

Die meisten emulatorbenutzer müssen nur die grundlegenden Eingabe Steuerelemente für den [hololens-Emulator](using-the-hololens-emulator.md#basic-emulator-input) oder den [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md#basic-simulator-input)verwenden. Die folgenden Details sind für fortgeschrittene Benutzer bestimmt, die sich mit dem simulieren komplexer Typen von Eingaben herausgestellt haben.


## <a name="concepts"></a>Konzepte

Um mit dem Steuern der virtuellen Eingabe an den hololens-Emulator und dem Windows Mixed Reality-Simulator zu beginnen, sollten Sie sich zunächst mit einigen Konzepten vertraut machen.

Bewegung bezieht sich auf das Steuern und Ändern der Position und Ausrichtung eines etwas in der Szene. Für ein Ziel steuerbares Objekt wird Bewegung sowohl mit Drehung als auch Übersetzung (Bewegung) entlang von drei Achsen gesteuert.
* **Yaw**: Nach links oder rechts.
* **Tonhöhe**: Ein-oder ausschalten.
* **Rollout**: Parallele Ausführung.
* **X**: Nach links oder rechts verschieben.
* **J**: Nach oben oder unten verschieben.
* **Z**: Vorwärts oder rückwärts.

[Gesten](gestures.md) -und Bewegungs Controller Eingaben werden genau der Art der physischen Geräte zugeordnet:
* **Aktion**: Dadurch wird die Aktion simuliert, mit der der Vordergrund zum Ziehpunkt gedrückt oder die Schaltfläche Aktion auf einem Controller gezogen wird. Beispielsweise kann die Aktions Eingabe verwendet werden, um die Luft tippen Bewegung zu simulieren, einen Bildlauf durch den Inhalt durchführen und die Tastenkombination zu drücken.
* **[Bloom](gestures.md#bloom)/Systemanbieter Geste oder Startseite**: Die hololens-Blüte/System Bewegung oder die Start Schaltfläche eines Controllers wird verwendet, um zur Shell zurückzukehren und System Aktionen auszuführen.

Hände haben eine umfassende reprressentiments in hololens 2.  Neben der Nachverfolgung/nicht Nachverfolgung und der Verwendung für den Einsatz von Gesten verfügen die Hände nun über ein geclustertes Skelett Modell, das für den Entwickler verfügbar ist.  Dadurch werden jeweils 26 nach verfolgte Punkte eingeführt.  
* **Gemeinsam**: Eine von 20 nach verfolgten Positionen für eine bestimmte verfolgte Hand. Dabei muss es sich um einen Punkt mit einem zugeordneten 3D--Bereich handelt.
* **Pose**: Eine vollständige Auflistung aller Gelenke in einer nach verfolgten Hand. Zurzeit ist dies eine Auflistung von 26 Gelenken. 

Zu diesem Zeitpunkt machen wir die direkte Steuerung der einzelnen gemeinsamen Positionen nicht einzeln über die Emulator-Benutzeroberfläche verfügbar. Sie können Sie jedoch über die Simulations-API festlegen. Stattdessen haben wir eine Reihe nützlicher Vertreter, die es Ihnen ermöglicht, zwischen zu wechseln.

Sie können auch den Status der simulierten Sensor Eingabe Steuern:
* **Zurücksetzen**: Dadurch werden alle simulierten Sensoren auf ihre Standardwerte zurückgegeben.  Beginnend mit dem hololens 2-Emulator kann eine zurück setzung auf ein oder beide Hände beschränkt werden, indem Sie die gewünschten Hand (e) mithilfe der entsprechenden Modifizierertasten oder Schaltflächen (Links und/rechts alt oder die linke und/oder Rechte Stoß Taste im Gamepad) einbinden.
* Nach **Verfolgung**: Durchläuft die nach Verfolgungs Modi mit Feldern fester Breite. Dazu zählen:
  * **Standard**: Das Betriebssystem wählt basierend auf den Anforderungen des Systems den besten Überwachungsmodus aus.
   * **Ausrichtung**: Erzwingt die Ausrichtung, unabhängig von den Anforderungen des Systems.
   * **Positions**: Erzwingt die Positionsüberwachung, unabhängig von den Anforderungen des Systems.

## <a name="types-of-input"></a>Eingabetypen

In der folgenden Tabelle ist dargestellt, wie die einzelnen Eingabetypen dem Tastatur-, Maus-und Xbox-Controller zugeordnet werden. Jeder Typ hat abhängig vom Eingabe Steuerungs Modus eine andere Zuordnung. Weitere Informationen zu den Eingabe Steuerungs Modi finden Sie weiter unten in diesem Dokument.

|  |  Tastatur |  Maus |  Xbox-Controller | 
|----------|----------|----------|----------|
|  Schwenken |  Pfeile nach links/rechts |  Nach links/rechts ziehen |  Rechter Finger Stick links/rechts | 
|  Nickwinkel |  Pfeile nach oben/nach unten |  Nach oben/unten ziehen |  Rechter fingerstick nach oben/unten | 
|  Roll |  Q/E |  |  Dpad links/rechts | 
|  X |  A/D |  |  Linker Finger Stick links/rechts | 
|  J |  Bild-auf/Bild-ab |  |  Dpad nach oben/unten | 
|  Z |  W/S |  |  Linker Finger Stick nach oben/unten | 
|  Aktion |  Eingabe oder Leerraum |  Rechte Schaltfläche |  Eine Schaltfläche oder einen der beiden Optionen | 
|  Blüht/System |  F2-oder Windows-Taste |  |  B-Taste | 
|  Controller ziehfläche |  G  |  |  | 
|  Schaltfläche "controller" |  M  |  |  | 
|  Touchpad-Touch für Controller |  U  |  |  | 
|  Controller Touchpad-Taste |  P  |  |  | 
|  STRG-Taste für Controller |  K  |  |  | 
|  Linker Controller-nach verfolgungsstatus |  F9 |  |  | 
|  Rechter Controller-nach verfolgungsstatus |  F10 |  |  | 
|  Hand "Close"-Pose | 7 |  |  |
|  Hand ' Open '-Pose (Standard) | 8 |  |  |
|  Hand Punkt darstellen | 9 |  |  |
|  Hand "Pinch" darstellen | 0 |  |  |
|  Zurücksetzen |  Escapeschlüssel |  |  Starttaste | 
|  Paletten |  T oder F3 |  |  X-Taste | 


Hinweis: Die Controller Schaltflächen können mithilfe der handzugriffsmodifizierern auf eine Hand/einen Controller oder die andere ausgerichtet werden.

## <a name="targeting"></a>Zielbestimmung 

Einige der oben genannten Eingabe Konzepte sind eigenständig.  Action, Bloom/System, Reset und Tracking sind umfassende Konzepte, die nicht benötigt werden und von denen keine weiteren modifiziererer für die Zielgruppe betroffen sind.  Die verbleibenden Konzepte können jedoch auf eines von mehreren Zielen angewendet werden. Wir haben Möglichkeiten zum Angeben des beabsichtigten Ziels eingeführt, auf das der Befehl angewendet werden soll.  In allen Fällen ist es möglich, über die Benutzeroberfläche oder über Tastatureingaben anzugeben, die auf targtett festgelegt sind.  In einigen Fällen ist es auch möglich, mit dem Xbox-Controller direkt anzugeben. 

In der folgenden Tabelle werden die Optionen für die Zielplattform und die Möglichkeit zum Aktivieren der einzelnen Optionen beschrieben.

| Objekt | Tastatur-Modifizierer | Controllermodifizierer | Emulator UI-Modifizierer |
|----------|----------|----------|----------|
| Text | (Standard) | (Standard) | (Standard) |
| Stadt | Halten H | (Nicht verfügbar) | (Nicht verfügbar) |
| Linker/Controller | Linke ALT-Taste gedrückt halten | Linke Schulter Taste halten | Linke Hand Nadel | 
| Rechte Seite/Controller | Alt-Taste gedrückt halten | Rechte Schulter Taste halten | Rechte Hand Nadel |
| Blicke | Halten Sie Y | (Nicht verfügbar) | Augen-PushPin |
  
In der folgenden Tabelle wird gezeigt, wie die einzelnen zielmodifizierer die einzelnen Grundkonzepte der Verschiebungs Eingabe zuordnen.

|  | Standard (Text) |  Hand-/Controller (alt, halten, Gamepad-Schulter Schaltfläche halten oder UI-PushPin umschalten) |  Head (halten H)  |  Augen (halten Sie die UI-PushPin gedrückt oder Umschalten) |
|----------|----------|----------|----------|
|  Schwenken |  Text nach links/rechts drehen |  Hand nach links/rechts verschieben |  Kopfzeile nach links/rechts | Der Augenblick sieht links/rechts aus. |
|  Nickwinkel |  Kopf-/ausschalten |  Hand nach oben/unten verschieben |  Kopf-/ausschalten | Eye-Blick nach oben/unten | 
|  Roll |  Rollenspitze links/rechts |  |  Rollenspitze links/rechts | (Keine Aktion) |
|  X |  Folien Text Links/rechts |  Hand/Controller nach links/rechts verschieben |  Kopfzeile nach links/rechts | (Keine Aktion) |
|  J |  Text nach oben/unten verschieben |  Hand/Controller nach oben/unten verschieben |  Kopf-/ausschalten | (Keine Aktion) |
|  Z |  Text vorwärts/rückwärts verschieben |  Hand/Controller vorwärts/rückwärts verschieben |  Kopf-/ausschalten | (Keine Aktion) |
 
 
## <a name="controlling-an-app"></a>Steuern einer APP

Der folgende Satz von Steuerelementen wird für die alltägliche Verwendung vorgeschlagen:

|  Vorgang |  Tastatur und Maus |  Controller | 
|----------|----------|----------|
|  Text X |  A/D |  Linker Finger Stick links/rechts | 
|  Textkörper Y |  Bild-auf/Bild-ab |  Dpad nach oben/unten | 
|  Text Z |  W/S |  Linker Finger Stick nach oben/unten | 
|  Text-Yaw |  Ziehen Sie die Maus nach links/rechts |  Rechter Finger Stick links/rechts | 
|  Head-Yaw |  H + Maus nach links/rechts ziehen |  H (auf Tastatur) + Rechte fingerstick links/rechts | 
|  Head-Tonhöhe |  Maus nach oben/nach unten ziehen |  Rechter fingerstick nach oben/unten | 
|  Head-Roll |  Q/E |  Dpad links/rechts | 
|  Hand/Controller X |  Alt + A/D |  Schulter + Linker Finger Stick links/rechts | 
|  Hand-/controllery |  Alt + Bild-auf/Bild-ab |  Schulter + Dpad nach oben/unten | 
|  Hand/Controller Z |  Alt + W/S |  Schulter + Left-fingerstick nach oben/unten | 
|  Hand-/Controller-Yaw |  Alt + Maus nach links/rechts ziehen |  Schulter + nach-rechts-Taste links/rechts | 
|  Hand-/Controller-Tonhöhe |  Alt + Maus nach oben/unten ziehen |  Schulter + rechter fingerstick nach oben/unten | 
|  Hand-/controllerrollen |  Alt + Q/E |  Schulter + Dpad links/rechts | 
|  Aktion |  Rechte Maustaste |  Trigger | 
|  Blüte/System/Startseite |  F2-oder Windows-Taste |  B-Taste | 
|  Zurücksetzen |  Beenden |  Starttaste | 
|  Paletten |  T |  X-Taste | 
|  Bildlauf |  Alt + nach-rechts-Taste + Maus nach oben/unten ziehen |  Schulter + Auslöse Taste + rechter fingerstick nach oben/unten | 
|  Schneller verschieben/drehen | Linke oder Rechte UMSCHALTTASTE | Halten Sie den richtigen Finger Stick gedrückt. |
|  Langsam verschieben/drehen | Links oder rechts STRG-Taste | Halten Sie den linken Finger Stick gedrückt. |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>System Steuerungs Tastenkombinationen für die Wahrnehmungs Simulation

Die folgenden Tastenkombinationen sind für den Zugriff auf die Systemsteuerung für die Wahrnehmungs Simulation und das Aktivieren oder Deaktivieren von PC-Eingabegeräten zur Verwendung mit Simulationen verfügbar.

| Vorgang | Tastenkombination | Beschreibung/Notizen |
|-----------|----------|-------------|
| "Tastatur für Simulation verwenden" umschalten | F4 | Wenn diese deaktiviert ist, wird die Tastatureingabe an die hololens-oder Windows Mixed Reality-Anwendung weitergeleitet. |
| "Maus für Simulation verwenden" umschalten | F5 | Wenn Sie ausgeschaltet ist, wird die Mauseingabe an die gemischte Reality-Umgebung weitergeleitet (nur Windows Mixed Reality). |
| "Gamepad für Simulation verwenden" umschalten | F6 | Wenn Sie ausgeschaltet ist, wird die Gamepad-Eingabe von der Simulation ignoriert. |
| Anzeigen oder Ausblenden der Systemsteuerung | F7 | |
| Festlegen des Tastaturfokus auf die Systemsteuerung | F8 | Wenn das Panel momentan nicht sichtbar ist, wird es zuerst angezeigt. |
| Andocken oder Abdocken des Bereichs im Emulator-oder Mixed Reality-Portal Fenster | F9 | Wenn das Fenster geschlossen wird, wenn es nicht angedockt ist, wird es angedockt und ausgeblendet. |

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Verwenden des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md)
