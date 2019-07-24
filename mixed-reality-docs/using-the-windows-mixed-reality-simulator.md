---
title: Verwenden des Windows Mixed Reality-Simulators
description: Der Windows Mixed Reality-Simulator ermöglicht Ihnen das Testen von Mixed Reality-apps auf Ihrem PC ohne ein Windows Mixed Reality-immersives-Headset.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Gemischte Windows-Realität, Simulator, Tests
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580703"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Verwenden des Windows Mixed Reality-Simulators

Der Windows Mixed Reality-Simulator ermöglicht Ihnen das Testen von Mixed Reality-apps auf Ihrem PC ohne ein Windows Mixed Reality-immersives-Headset. Sie steht ab dem Windows 10 Creators Update zur Verfügung. Der Simulator ähnelt dem [hololens-Emulator](using-the-hololens-emulator.md), obwohl der Simulator keinen virtuellen Computer verwendet. Apps, die im Simulator ausgeführt werden, werden in Ihrer Windows 10-Desktop Benutzersitzung genauso wie bei Verwendung eines immersiven Headsets ausgeführt. Die Benutzer-und Umgebungs Eingaben, die normalerweise von den Sensoren auf einem immersiven Headset gelesen werden, werden stattdessen mit dem Tastatur-, Maus-oder Xbox-Controller simuliert. Apps müssen nicht so geändert werden, dass Sie im Simulator ausgeführt werden, und Sie wissen nicht, dass Sie nicht auf einem immersiven Headset ausgeführt werden.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Aktivieren des Windows Mixed Reality-Simulators

1. **Aktivieren des Entwicklermodus** über Einstellungen-> Update-und Sicherheits > für Entwickler
2. Starten des **Mixed Reality-Portals** über den Desktop
3. Wenn Sie das Portal zum ersten Mal starten, müssen Sie die Einrichtung durchlaufen.
   1. Klicken Sie auf **Get Started**
   2. Klicken Sie auf **Ich stimme** zu, um die Vereinbarung zu akzeptieren
   3. Klicken Sie auf **für Simulation einrichten (für Entwickler)** , um das Setup ohne ein physisches Gerät durchzugehen.
   4. Klicken Sie auf **Einrichten** , um Ihre Auswahl zu bestätigen.
4. Klicken Sie auf der linken Seite des Mixed Reality-Portals auf die Schaltfläche **für Entwickler** .
5. Aktivieren **Sie die** UMSCHALT Fläche für Simulation aktivieren auf ein.
   * Durch das Aktivieren der Simulation wird der linke simulierte 6-DOF-Controller standardmäßig installiert und aktiviert.  Vor dem Windows 10-Update von Mai 2019 ist für die Installation eines simulierten 6-DOF-Controllers Administrator Berechtigungen erforderlich.  Wenn eine solche angezeigt wird, müssen Sie das Dialogfeld "Benutzerkontensteuerung" akzeptieren.

Sie sollten jetzt mit Simulation ausführen!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Bereitstellen von apps im Mixed Reality-Simulator

Da der Simulator auf dem lokalen PC ohne einen virtuellen Computer ausgeführt wird, können Sie beim Debuggen einfach Ihre universellen Windows-apps auf dem **lokalen Computer** bereitstellen.

## <a name="basic-simulator-input"></a>Grundlegende simulatoreingabe

Das Steuern des Simulators ähnelt vielen gängigen 3D-Videospielen und dem [hololens-Emulator](using-the-hololens-emulator.md). Es stehen Eingabeoptionen über die Tastatur, Maus oder den Xbox-Controller zur Verfügung.

Sie steuern den Simulator, indem Sie die Aktionen eines simulierten Benutzers mit einem immersiven Headset umleiten. Ihre Aktionen verschieben den simulierten Benutzer und bewirken Interaktionen mit apps, die so reagieren, wie Sie auf einem immersiven Headset auftreten würden.
* **Nach vorne, hinten, links und rechts gehen**: Verwenden Sie die Tasten W, A, S und D auf Ihrer Tastatur oder den linken Stick eines Xbox-Controllers.
* **Nach oben, unten, links und rechts schauen**: Klicken und ziehen Sie mit der Maus, verwenden Sie die Pfeiltasten auf Ihrer Tastatur oder den rechten Stick eines Xbox-Controllers.
* **Aktions Schaltfläche auf Controller drücken** : Klicken Sie mit der rechten Maustaste auf die Maus, drücken Sie die Eingabetaste auf der Tastatur, oder verwenden Sie die Schaltfläche A auf einem Xbox-Controller.
* **Start Taste auf dem Controller** drücken Sie die Windows-Taste oder F2-Taste auf der Tastatur, oder drücken Sie auf einem Xbox-Controller die Taste B.
* **Controller Bewegung für** den Bildlauf: halten Sie die Alt-Taste gedrückt, halten Sie die Maustaste gedrückt, und ziehen Sie die Maus nach oben/unten, oder in einem Xbox-Controller halten Sie den rechten-und einen Schaltflächen nach oben und nach unten.

## <a name="tracked-controllers"></a>Nach verfolgte Controller

Der Simulator für gemischte Realität kann bis zu zwei handgehaltene Bewegungs Controller simulieren. Aktivieren Sie diese mithilfe der umschaltschalter im Mixed Reality-Portal. Jeder simulierte Controller hat Folgendes:
* Position und Ausrichtung im Raum
* Startschaltfläche
* Menü-Taste
* Zieh Schaltfläche
* Touchpad
* Ministick
* Akku Pegel

## <a name="see-also"></a>Siehe auch
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Erweiterte Eingabe des gemischten Reality-Simulators](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Räumliche Abbildung in Unity](spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)
