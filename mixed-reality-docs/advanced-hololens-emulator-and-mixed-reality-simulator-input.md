---
title: Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator
description: Ausführliche Anweisungen für die Verwendung des Tastatur-, Maus-und Xbox-Controllers zum Simulieren von Eingaben für den hololens-Emulator und den Windows Mixed Reality-Simulator.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: Hololens, Emulator, Simulation, gemischte Windows-Realität
ms.openlocfilehash: 0812b1d498ea557e84eecc44142b38d86099f832
ms.sourcegitcommit: dc60c6ca075e7086b87478f1d7e87ebe02160c0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84631479"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator

Die meisten emulatorbenutzer müssen nur die grundlegenden Eingabe Steuerelemente für den [hololens-Emulator](using-the-hololens-emulator.md#basic-emulator-input) oder den [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md#basic-simulator-input)verwenden. Die folgenden Details sind für fortgeschrittene Benutzer bestimmt, die sich mit dem simulieren komplexer Typen von Eingaben herausgestellt haben.


## <a name="concepts"></a>Konzepte

Um mit dem Steuern der virtuellen Eingabe an den hololens-Emulator und dem Windows Mixed Reality-Simulator zu beginnen, sollten Sie sich zunächst mit einigen Konzepten vertraut machen.

Bewegung bezieht sich auf das Steuern und Ändern der Position und Ausrichtung eines etwas in der Szene. Für ein Ziel steuerbares Objekt wird Bewegung sowohl mit Drehung als auch Übersetzung (Bewegung) entlang von drei Achsen gesteuert.
* **Yaw**: nach links oder rechts.
* **Tonhöhe**: ein-oder ausschalten.
* **Roll**: Roll Side-to-Side
* **X**: nach links oder rechts verschieben.
* **Y**: nach oben oder unten verschieben.
* **Z**: vorwärts oder rückwärts.

Gesten-und Bewegungs Controller Eingaben werden genau der Art der physischen Geräte zugeordnet:
* **Aktion**: Dadurch wird die Aktion simuliert, mit der der Vorder-Finger zum Ziehpunkt gedrückt oder die Aktions Schaltfläche auf einem Controller abgerufen wird. Beispielsweise kann die Aktions Eingabe verwendet werden, um die Luft tippen Bewegung zu simulieren, einen Bildlauf durch den Inhalt durchführen und die Tastenkombination zu drücken.
* ** [Bloom](system-gesture.md#bloom)/Systemanbieter Geste oder Home**: die hololens-Blüte/System Bewegung oder die Start Schaltfläche eines Controllers wird verwendet, um zur Shell zurückzukehren und System Aktionen auszuführen.

Hände haben eine umfangreiche Darstellung in hololens 2.  Neben der Nachverfolgung/nicht Nachverfolgung und der Verwendung für den Einsatz von Gesten verfügen die Hände nun über ein geclustertes Skelett Modell, das für den Entwickler verfügbar ist.  Dadurch werden jeweils 26 nach verfolgte Punkte eingeführt.  
* **Joint**: eine von 20 nach verfolgten Positionen für eine bestimmte verfolgte Hand. Dabei muss es sich um einen Punkt mit einem zugeordneten 3D--Bereich handelt.
* **Pose**: eine vollständige Auflistung aller Gelenke in einer nach verfolgten Hand. Zurzeit ist dies eine Auflistung von 26 Gelenken. 

Zu diesem Zeitpunkt machen wir die direkte Steuerung der einzelnen gemeinsamen Positionen nicht einzeln über die Emulator-Benutzeroberfläche verfügbar. Sie können Sie jedoch über die Simulations-API festlegen. Stattdessen haben wir eine Reihe nützlicher Vertreter, die es Ihnen ermöglicht, zwischen zu wechseln.

Sie können auch den Status der simulierten Sensor Eingabe Steuern:
* **Reset**: Hiermit werden alle simulierten Sensoren auf ihre Standardwerte zurückgesetzt.  Beginnend mit dem hololens 2-Emulator kann eine zurück setzung auf ein oder beide Hände beschränkt werden, indem Sie die gewünschten Hand (e) mithilfe der entsprechenden Modifizierertasten oder Schaltflächen (Links und/rechts alt oder die linke und/oder Rechte Stoß Taste im Gamepad) einbinden.
* Nach **Verfolgung**: durchläuft die nach Verfolgungs Modi mit Feldern fester Breite. Dies schließt Folgendes ein:
  * **Standard**: das Betriebssystem wählt basierend auf den Anforderungen des Systems den besten Überwachungsmodus aus.
   * **Ausrichtung**: erzwingt die Nachverfolgung nur Nachverfolgung, unabhängig von den Anforderungen des Systems.
   * **Positional**: erzwingt die Positionsüberwachung, unabhängig von den Anforderungen des Systems.

## <a name="types-of-input"></a>Eingabetypen

In der folgenden Tabelle ist dargestellt, wie die einzelnen Eingabetypen dem Tastatur-, Maus-und Xbox-Controller zugeordnet werden. Jeder Typ hat abhängig vom Eingabe Steuerungs Modus eine andere Zuordnung. Weitere Informationen zu den Eingabe Steuerungs Modi finden Sie weiter unten in diesem Dokument.

|  |  Tastatur |  Maus |  Xbox-Controller | 
|----------|----------|----------|----------|
|  Yaw |  Pfeile nach links/rechts |  Nach links/rechts ziehen |  Rechter Finger Stick links/rechts | 
|  Tonhöhe |  Pfeile nach oben/nach unten |  Nach oben/unten ziehen |  Rechter fingerstick nach oben/unten | 
|  N |  Q/E |  |  Dpad links/rechts | 
|  X |  A/D |  |  Linker Finger Stick links/rechts | 
|  J |  Bild-auf/Bild-ab |  |  Dpad nach oben/unten | 
|  Z |  W/S |  |  Linker Finger Stick nach oben/unten | 
|  Aktion |  Eingabe oder Leerraum |  Rechte Schaltfläche |  Eine Schaltfläche oder einen der beiden Optionen | 
|  Blüht/System |  F2-oder Windows-Taste |  |  B-Taste | 
|  Schaltfläche für Controller Zieh Fläche/Hand |  G  |  |  | 
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
|  Reset |  Escapeschlüssel |  |  Starttaste | 
|  Nachverfolgung |  T oder F3 |  |  X-Taste | 


Hinweis: die Controller Schaltflächen können mit den Modifizierern für die Hand Ausrichtung auf eine Hand/einen Controller oder die andere als Ziel verwendet werden.

## <a name="targeting"></a>Zielgruppenadressierung 

Einige der oben genannten Eingabe Konzepte sind eigenständig.  Action, Bloom/System, Reset und Tracking sind umfassende Konzepte, die nicht benötigt werden und von denen keine weiteren modifiziererer für die Zielgruppe betroffen sind.  Die verbleibenden Konzepte können jedoch auf eines von mehreren Zielen angewendet werden. Wir haben Möglichkeiten zum Angeben des beabsichtigten Ziels eingeführt, auf das der Befehl angewendet werden soll.  In allen Fällen ist es möglich, über die Benutzeroberfläche oder über Tastatureingaben anzugeben, welches Objekt als Ziel festgelegt wird.  In einigen Fällen ist es auch möglich, mit dem Xbox-Controller direkt anzugeben. 

In der folgenden Tabelle werden die Optionen für die Zielplattform und die Möglichkeit zum Aktivieren der einzelnen Optionen beschrieben.

| Object | Tastatur-Modifizierer | Controllermodifizierer | Emulator UI-Modifizierer |
|----------|----------|----------|----------|
| Text | (Standard) | (Standard) | (Standard) |
| Head | Halten H | (Nicht verfügbar) | (Nicht verfügbar) |
| Linker/Controller | Linke ALT-Taste gedrückt halten | Linke Schulter Taste halten | Linke Hand Nadel | 
| Rechte Seite/Controller | Alt-Taste gedrückt halten | Rechte Schulter Taste halten | Rechte Hand Nadel |
| Blicke | Halten Sie Y | (Nicht verfügbar) | Augen-PushPin |
  
In der folgenden Tabelle wird gezeigt, wie die einzelnen zielmodifizierer die einzelnen Grundkonzepte der Verschiebungs Eingabe zuordnen.

|  | Standard (Text) |  Hand-/Controller (alt, halten, Gamepad-Schulter Schaltfläche halten oder UI-PushPin umschalten) |  Head (halten H)  |  Augen (halten Sie die UI-PushPin gedrückt oder Umschalten) |
|----------|----------|----------|----------|
|  Yaw |  Text nach links/rechts drehen |  Hand nach links/rechts verschieben |  Kopfzeile nach links/rechts | Der Augenblick sieht links/rechts aus. |
|  Tonhöhe |  Kopf-/ausschalten |  Hand nach oben/unten verschieben |  Kopf-/ausschalten | Eye-Blick nach oben/unten | 
|  N |  Rollenspitze links/rechts |  |  Rollenspitze links/rechts | (Keine Aktion) |
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
|  Reset |  Escape |  Starttaste | 
|  Nachverfolgung |  T |  X-Taste | 
|  Scrollen |  Alt + nach-rechts-Taste + Maus nach oben/unten ziehen |  Schulter + Auslöse Taste + rechter fingerstick nach oben/unten | 
|  Schneller verschieben/drehen | Linke oder Rechte UMSCHALTTASTE | Halten Sie den richtigen Finger Stick gedrückt. |
|  Langsam verschieben/drehen | Links oder rechts STRG-Taste | Halten Sie den linken Finger Stick gedrückt. |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Verwenden eines immersiven Headsets für Windows Mixed Reality und des Motion-Controllers mit dem Hololens 2-Emulator

Wenn Sie ein Windows Mixed Reality-immersives Headset mit dem hololens 2-Emulator verwenden, werden Bewegung und Drehung automatisch der Headset-Bewegung und-Drehung zugeordnet.  Position und Ausrichtung des Bewegungs Controllers werden automatisch der Handposition und Ausrichtung im Emulator zugeordnet.  In der folgenden Tabelle sind zusätzliche Aktionen aufgeführt, die bei der Verwendung eines Bewegungs Controllers verfügbar sind.

Beachten Sie, dass bei Verwendung eines Headsets standardmäßige Tastatur-, Maus-und Gamepad-Steuerelemente automatisch ignoriert werden.

|  Vorgang |  Aktion |  Notizen | 
|----------|----------|----------|
|  Text X |  Thumbstick links/rechts |   | 
|  Text Z |  Fingerabdruck vorwärts/zurück |   | 
|  Textkörper Y |  Tastatur Seite nach oben/Down | Stellen Sie sicher, dass Windows Mixed Reality den Fokus besitzt.  Drücken Sie Win + Y, wenn sich der Fokus auf dem Windows-Desktop befindet, um den Fokus auf Windows Mixed Reality zurückzusetzen. |
|  Augen sehen Links/rechts |  Dpad links/rechts | |
|  Augen suchen nach oben/unten | Dpad nach oben/unten | |
|  Tippen | Trigger | |
|  Pinsel/Reichweite | Zieh Schaltfläche | |
|  System Geste | Menü-Taste | |
|  Position zurücksetzen | Fingerabdruck klicken | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>System Steuerungs Tastenkombinationen für die Wahrnehmungs Simulation

Die folgenden Tastenkombinationen sind für den Zugriff auf die Systemsteuerung für die Wahrnehmungs Simulation und das Aktivieren oder Deaktivieren von PC-Eingabegeräten zur Verwendung mit Simulationen verfügbar.

| Vorgang | Verknüpfung | Beschreibung/Notizen |
|-----------|----------|-------------|
| "Tastatur für Simulation verwenden" umschalten | F4 | Wenn diese deaktiviert ist, wird die Tastatureingabe an die hololens-oder Windows Mixed Reality-Anwendung weitergeleitet. |
| "Maus für Simulation verwenden" umschalten | F5 | Wenn Sie ausgeschaltet ist, wird die Mauseingabe an die gemischte Reality-Umgebung weitergeleitet (nur Windows Mixed Reality). |
| "Gamepad für Simulation verwenden" umschalten | F6 | Wenn Sie ausgeschaltet ist, wird die Gamepad-Eingabe von der Simulation ignoriert. |
| Anzeigen oder Ausblenden der Systemsteuerung | F7 | |
| Festlegen des Tastaturfokus auf die Systemsteuerung | F8 | Wenn das Panel momentan nicht sichtbar ist, wird es zuerst angezeigt. |
| Andocken oder Abdocken des Bereichs im Emulator-oder Mixed Reality-Portal Fenster | F9 | Wenn das Fenster geschlossen wird, wenn es nicht angedockt ist, wird es angedockt und ausgeblendet. |

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](install-the-tools.md)
* [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md)
* [Verwenden des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md)
