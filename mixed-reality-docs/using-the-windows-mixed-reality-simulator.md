---
title: Verwendung des Simulators Windows Mixed Reality
description: Die Windows Mixed Reality-Simulator können Sie mixed Reality-apps auf Ihren PC ohne eine immersive Windows Mixed Reality-Kopfhörer testen.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows gemischte Realität-Simulator testen
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580703"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Verwendung des Simulators Windows Mixed Reality

Die Windows Mixed Reality-Simulator können Sie mixed Reality-apps auf Ihren PC ohne eine immersive Windows Mixed Reality-Kopfhörer testen. Es ist ab Windows 10 Creators Update verfügbar. Der Simulator ist vergleichbar mit der [Emulator für HoloLens](using-the-hololens-emulator.md), wenn der Simulator einen virtuellen Computer nicht verwendet. Apps im Simulator in Ihrer Windows 10-Desktopbenutzer Sitzung ausgeführt wird, wie sie bei der Verwendung einer immersive Kopfhörer ausgeführt. Die menschliche und environmental Eingabe, die in der Regel von den Sensoren in eine immersive Kopfhörer gelesen werden, werden stattdessen simuliert mithilfe Ihrer Tastatur, Maus oder Xbox-Controller. Apps müssen nicht geändert werden, um die im Simulator auszuführen, und Sie wissen nicht, dass auf dem eine immersive Kopfhörer werden nicht ausgeführt.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Aktivieren die Windows Mixed Reality-simulator

1. **Aktivieren Sie den Entwicklermodus** Einstellungen "->" Updates und Sicherheit -> für Entwickler
2. Starten Sie den **Mixed Reality-Portal** über den Desktop
3. Ist dies zum ersten Mal im Portal zu starten, müssen Sie die Setup-Benutzeroberfläche wechseln
   1. Klicken Sie auf **erste Schritte**
   2. Klicken Sie auf **ich stimme zu** die Vereinbarung zustimmen
   3. Klicken Sie auf **richten Sie für die Simulation (für Entwickler)** durchlaufen, ohne ein physisches Gerät
   4. Klicken Sie auf **einrichten** zur Bestätigung Ihrer Auswahl
4. Klicken Sie auf die **für Entwickler** Schaltfläche auf der linken Seite des Mixed Reality-Portals
5. Aktivieren Sie die Simulation ein/aus-Option **auf**
   * Aktivieren der Simulation installiert und den linken simulierten 6-FG Controller sind standardmäßig aktiviert.  Vor Windows sind 10 Mai 2019 Updates, installieren einen Controller simulierten 6-FG Administratorberechtigungen erforderlich.  Sie müssen das Dialogfeld "Benutzerkontensteuerung" akzeptieren, sobald eins verfügbar.

Sie sollten jetzt mit Simulation ausführen!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Bereitstellen von apps für den Simulator Mixed Reality

Da der Simulator auf dem lokalen Computer ohne einen virtuellen Computer ausgeführt wird, können Sie einfach Ihre universelle Windows-apps zum Bereitstellen der **lokalen Computer** beim Debuggen.

## <a name="basic-simulator-input"></a>Grundlegende Simulator-Eingabe

Steuern den Simulator ähnelt sehr viele allgemeine 3D-Videospiele und [Emulator für HoloLens](using-the-hololens-emulator.md). Eingabeoptionen stehen zur Verfügung, mit der Tastatur, Maus oder Xbox-Controller.

Sie steuern den Simulator durch die Aktionen eines simulierten Benutzers steht, geteert eine immersive Kopfhörer weiterleiten. Ihre Aktionen verschieben Sie den simulierten Benutzer und dazu führen, dass Interaktionen mit apps, die genauso wie in eine immersive Kopfhörer zu reagieren.
* **Schritt für Schritt nach vorne, zurück, links und rechts** -verwenden Sie die W, D, S und ein Schlüssel auf der Tastatur oder der linken Stick auf eine Xbox-Controller.
* **Suchen, nach unten, links und rechts** -Klick und Ziehen der Maus, verwenden Sie die Pfeiltasten auf der Tastatur oder der richtigen Stick auf eine Xbox-Controller.
* **Aktion-Tastendruck auf Controller** – mit der rechten Maustaste des Mauszeigers, drücken Sie die EINGABETASTE auf der Tastatur, oder verwenden Sie die A-Taste auf ein Xbox-Controller.
* **Home-Schaltfläche, klicken Sie auf Controller** – drücken Sie die Windows-Taste oder F2-Taste auf der Tastatur, oder drücken Sie die Schaltfläche "B" auf eine Xbox-Controller.
* **Verschieben der Controller für den Bildlauf** – gedrückter Alt-Taste, halten Sie die rechte Maustaste gedrückt, und ziehen Sie die Maus nach oben / unten, oder in ein Xbox-Controller halten der richtige Trigger und eine Schaltfläche und den richtigen Stick nach oben oder unten verschieben.

## <a name="tracked-controllers"></a>Überwachte Controller

Der Simulator Mixed Reality kann bis zu zwei Handheld nachverfolgten Motion-Controller simulieren. Aktivieren Sie sie mit der ein/aus-Schalter im Mixed Reality-Portal. Jedes simulierte Controller hat:
* Position und Ausrichtung im Raum
* Startschaltfläche
* Menü-Taste
* Schaltfläche "Ziehpunkt"
* Touchpad
* Ministick
* Akkukapazität

## <a name="see-also"></a>Siehe auch
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Erweiterte Mixed Reality-Simulator-Eingabe](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Räumliche Abbildung in Unity](spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)
