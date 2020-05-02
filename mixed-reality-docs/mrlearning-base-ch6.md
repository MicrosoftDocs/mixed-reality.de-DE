---
title: 'Tutorials zu den ersten Schritten: 7 Erstellen einer Beispielanwendung für eine Mondlandefähre (Lunar Module)'
description: In dieser Lektion kombinieren Sie mehrere Konzepte, die Sie in früheren Lektionen kennengelernt haben, um eine einzigartige Beispielerfahrung zu schaffen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031561"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Erstellen einer Beispielanwendung für eine Mondlandefähre (Lunar Module)
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

In diesem Tutorial werden mehrere Konzepte aus früheren Lektionen kombiniert, um eine einzigartige Beispielerfahrung zu schaffen. Sie erfahren, wie Sie eine Anwendung zur Montage von Teilen erstellen, bei der ein Benutzer mit nachverfolgten Händen Teile aufnehmen und versuchen muss, eine Mondlandefähre zu montieren. Sie verwenden drückbare Schaltflächen, um Platzierungshinweise ein- und auszuschalten, die Umgebung zurückzusetzen und die Mondlandefähre in den Weltraum zu befördern.

In zukünftigen Tutorials können Sie auf dieser Umgebung aufbauen, einschließlich leistungsfähiger Anwendungsfälle für mehrere Benutzer, die Azure Spatial Anchors für die räumliche Ausrichtung nutzen.

## <a name="objectives"></a>Ziele

* Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen
* Informationen zum Umschalten von Objekten
* Auslösen komplexer Ereignisse über drückbare Schaltflächen
* Verwenden der physischen Effekte und Kräfte von Starrkörpern
* Erkunden der Verwendung von QuickInfos

## <a name="lunar-module-parts-overview"></a>Übersicht über die Komponenten der Mondlandefähre
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

In diesem Abschnitt erstellen Sie eine einfache Montageaufgabe, bei der das Ziel für den Benutzer darin besteht, fünf Teile, die auf dem Tisch verteilt sind, an der richtigen Stelle der Mondlandefähre zu platzieren.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen des Rocket Launcher-Prefabs (Raketenstartanlage) zur Szene
2. Aktivieren der Objektmanipulation für alle Teile
3. Hinzufügen und Konfigurieren der Part Assembly Demo (Script)-Komponente (Teilemontagedemo (Skript))

> [!NOTE]
> Die Komponente „Part Assembly Demo (Script)“ ist nicht Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Hinzufügen des Rocket Launcher-Prefabs (Raketenstartanlage) zur Szene

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, ziehen Sie das Prefab **RocketLauncher** in das Hierarchiefenster, um es Ihrer Szene hinzuzufügen, und platzieren Sie es dann an einem passenden Ort, beispielsweise:

* Transformationsposition X = 1,5, Y = -0,4, Z = 0, so dass es sich rechts vom Benutzer auf Hüfthöhe befindet
* Transformationsrotation X = 0, Y = 180, Z = 0, sodass die Hauptfeatures des Experiments dem Benutzer zugewandt sind

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. Aktivieren der Objektmanipulation für alle Teile

Suchen Sie im Hierarchiefenster das Objekt „RocketLauncher > **LunarModuleParts**“, wählen Sie alle **untergeordneten Objekte** aus, fügen Sie die **Manipulation Handler (Script)** -Komponente und die **Near Interaction Grabbable (Script)** -Komponente hinzu, und konfigurieren Sie dann Manipulation Handler (Script) wie folgt:

* Deaktivieren Sie das Kontrollkästchen **Allow Far Manipulation** (Fern-Manipulation zulassen), um nur Nah-Interaktion zuzulassen
* Ändern Sie **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) in **Move Rotate** (Bewegen Drehen), sodass das Ändern der Größe deaktiviert ist

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Wenn Sie eine Auffrischung zu den Schrittanleitungen zum Implementieren der Objektmanipulation benötigen, lesen Sie die Anweisungen zum [Manipulieren von 3D-Objekten](mrlearning-base-ch4.md#manipulating-3d-objects).

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. Hinzufügen und Konfigurieren der Part Assembly Demo (Script)-Komponente (Teilemontagedemo (Skript))

Fügen Sie eine **Audio Source**-Komponente (Audioquelle) hinzu, während alle untergeordneten Objekte von LunarModuleParts noch ausgewählt sind, und konfigurieren Sie sie wie folgt:

* Weisen Sie dem Feld **AudioClip** einen passenden Audioclip zu, beispielsweise „MRKT_Scale_Start“
* Deaktivieren Sie das Kontrollkästchen **Play On Awake** (Nach Laden wiedergeben), sodass der Audioclip nach dem Laden der Szene nicht automatisch wiedergegeben wird
* Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1, um räumliche Audiowiedergabe zu aktivieren

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Fügen Sie bei immer noch ausgewählten untergeordneten Objekten von LunarModuleParts die Komponente **Part Assembly Demo (Script)** hinzu:

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

Wählen Sie im Hierarchiefenster das **RoverEnclosure**-Objekt aus, und konfigurieren Sie dessen **Part Assembly Demo (Script)** -Komponente folgendermaßen:

* Weisen Sie dem Feld **Object To Place** (Zu platzierendes Objekt) das Objekt **selbst** zu, in diesem Fall das RoverEnclosure-Objekt
* Weisen Sie dem Feld **Location To Place** (Ort für Platzierung) das entsprechende **PlacementHints**-Objekt zu, in diesem Fall das RoverEnclosure_PlacementHint-Objekt
* Weisen Sie dem **Tool Tip Object**-Feld (QuickInfo-Objekt) den entsprechenden **ToolTip** (QuickInfo) zu, in diesem Fall das RoverEnclosure_ToolTip-Objekt
* Weisen Sie dem Feld **Audio Source** (Audioquelle) das Objekt **selbst** zu, in diesem Fall das RoverEnclosure-Objekt

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Wiederholen** Sie diese Schritte für jedes der anderen untergeordneten LunarModuleParts-Objekte, d. h. FuelTank (Treibstofftank), EnergyCell (Batteriezelle), DockingPortal (Andockportal) und ExternalSensor (externer Sensor).

Wenn Sie jetzt in den Spielmodus wechseln und ein 'Object To Place' (Zu platzierendes Objekt) in die Nähe seiner 'Location To Place' (Ort für die Platzierung) bewegen, werden Sie Folgendes bemerken:

* Das Objekt rastet am Ort ein und wird dem LunarModule-Objekt untergeordnet, sodass es Teil des Mondlandemoduls wird
* Die Audio Source des Objekts gibt den zugewiesenen Audioclip an der Position des Objekts wieder
* Das entsprechende QuickInfo-Objekt wird ausgeblendet

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Verwenden der in den Editor integrierten Eingabesimulation benötigen, lesen Sie den Leitfaden [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) (Verwenden der in den Editor integrierten Handeingabesimulation zum Testen einer Szene) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Konfigurieren der Mondlandefähre

In diesem Abschnitt fügen Sie der Rocket Launcher-Anwendung weitere Funktionen hinzu, damit der Benutzer Folgendes ausführen kann:

* Mit dem Mondlandemodul interagieren
* Das Mondlandemodul ins All starten und beim Start einen Soundeffekt wiedergeben
* Die Anwendung zurücksetzen, sodass das Mondlandemodul und alle seine Teile wieder an ihrer ursprünglichen Position platziert werden
* Die Platzierungshinweise ausblenden, um die Aufgabe der Teilemontage zu erschweren.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Aktivieren der Objektmanipulation
2. Aktivieren von physikalischen Wirkungen
3. Hinzufügen einer Audioquellenkomponente
4. Hinzufügen und Konfigurieren der Launch Lunar Module (Script)-Komponente (Mondlandemodul starten (Skript))
5. Hinzufügen und Konfigurieren der Toggle Placement Hints (Script)-Komponente (Platzierungshinweise ein-/ausschalten (Skripts))

> [!NOTE]
> Die Launch Lunar Module (Script)-Komponente und die Toggle Placement Hints (Script)-Komponente sind nicht Bestandteil von MRTK. Sie wurden zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

### <a name="1-enable-object-manipulation"></a>1. Aktivieren der Objektmanipulation

Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > **LunarModule**“ aus, fügen Sie die **Manipulation Handler (Script)** -Komponente und die **Near Interaction Grabbable (Script)** -Komponente hinzu, und konfigurieren Sie dann Manipulation Handler (Script) wie folgt:

* Deaktivieren Sie das Kontrollkästchen **Allow Far Manipulation** (Fern-Manipulation zulassen), um nur Nah-Interaktion zuzulassen
* Ändern Sie **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) in Move Rotate (Bewegen Drehen), sodass das Ändern der Größe deaktiviert ist

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. Aktivieren von physikalischen Wirkungen

Fügen Sie bei immer noch ausgewähltem Objekt „RocketLauncher > **LunarModule**“ eine **Rigidbody**-Komponente hinzu, und konfigurieren Sie sie dann wie folgt:

* Deaktivieren Sie das Kontrollkästchen **Use Gravity** (Schwerkraft verwenden), damit das Mondlandemodul nicht der Schwerkraft unterliegt
* Aktivieren Sie das **Is Kinematic**-Kontrollkästchen, sodass im Ausgangszustand keine physikalischen Kräfte auf das Mondlandemodul wirken

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. Hinzufügen einer Audioquellenkomponente

Fügen Sie eine **Audio Source**-Komponente (Audioquelle) hinzu, während das „RocketLauncher > **LunarModule**“-Objekt noch ausgewählt ist, und konfigurieren Sie sie wie folgt:

* Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1, um räumliche Audiowiedergabe zu aktivieren

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Hinzufügen und Konfigurieren der Launch Lunar Module (Script)-Komponente (Mondlandemodul starten (Skript))

Fügen Sie die **Launch Lunar Module (Script)** -Komponente hinzu, während das „RocketLauncher > **LunarModule**“-Objekt noch ausgewählt ist, und konfigurieren Sie sie wie folgt:

* Ändern Sie den **Thrust**-Wert (Schub), damit sich das Lunar Module beim Start ansprechend erhebt, beispielsweise auf 0,01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. Hinzufügen und Konfigurieren der Toggle Placement Hints (Script)-Komponente (Platzierungshinweise ein-/ausschalten (Skripts))

Fügen Sie die **Toggle Placement Hints (Script)** -Komponente hinzu, während das „RocketLauncher > **LunarModule**“-Objekt noch ausgewählt ist, und konfigurieren Sie sie wie folgt:

* Legen Sie die Eigenschaft **Size** (Größe) von Game Object Array auf 5 fest
* Weisen Sie jedes der **untergeordneten Objekte** des „RocketLauncher > LunarModule > **PlacementHints**“-Objekts einem **Element**-Feld im Game Object Array zu:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Konfigurieren der Startschaltfläche

Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > Buttons > **LaunchButton**“ aus, erstellen Sie dann für die Komponente **Pressable Button (Script)** ein neues Ereignis **Button Pressed ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **LaunchLunarModule.StartThruster** als die auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Implementieren von Ereignissen benötigen, lesen Sie die Anweisungen unter [Gesten für Hand-Tracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

Erstellen Sie mit immer noch ausgewähltem Objekt „RocketLauncher > Buttons > **LaunchButton**“ für die Komponente „**Pressable Button (Script)** “ ein neues **Button Pressed ()** -Ereignis, konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, definieren Sie **AudioSource.PlayOneShot** als die auszulösende Aktion, und weisen Sie dem Feld **Audio Clip** einen passenden Audioclip zu, beispielsweise den Audioclip „MRTK_Gem“:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Erstellen Sie mit immer noch ausgewähltem Objekt „RocketLauncher > Buttons > **LaunchButton**“ für die Komponente **Pressable Button (Script)** ein neues Ereignis **Touch End ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **LaunchLunarModule.StopThruster** als die auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Wenn Sie jetzt in den Spielmodus wechseln und die Startschaltfläche drücken, hören Sie, wie der Audioclip wiedergegeben wird, und wenn Sie die Startschaltfläche etwa eine Sekunde oder länger gedrückt halten, sehen Sie, wie das Mondlandemodul ins All startet:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Konfigurieren der Schaltfläche zum Zurücksetzen

Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > Buttons > **ResetButton**“ aus, erstellen Sie dann für die Komponente **Pressable Button (Script)** ein neues Ereignis **Button Pressed ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **LaunchLunarModule.ResetModule** als die auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Erstellen Sie mit immer noch ausgewähltem Objekt „RocketLauncher > Buttons > **ResetButton**“ für die Komponente **Pressable Button (Script)** ein neues **Button Pressed ()** -Ereignis, konfigurieren Sie das **RocketLauncher**-Objekt für den Empfang des Ereignisses, definieren Sie **GameObject.BroadcastMessage** als auszulösende Aktion, und geben Sie im Nachrichtenfeld **ResetPlacement** ein:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> Die Aktion GameObject.BroadcastMessage sendet die ResetPlacement-Nachricht vom RocketLauncher-Objekt an alle dessen untergeordneten Objekte. Jedes untergeordnete Objekt, das über die ResetPlacement-Funktion verfügt, die in der Komponente „Part Assembly Demo (Script)“ definiert ist, die Sie allen untergeordneten Objekten von LunarModuleParts hinzugefügt haben, ruft die ResetPlacement-Funktion auf, die die Platzierung des betreffenden untergeordneten Objekts zurücksetzt.

Wenn Sie jetzt in den Spielmodus wechseln, einige Teile bewegen und/oder das Mondlandemodul starten und dann die Zurücksetzen-Schaltfläche drücken, sehen Sie, dass die Teile und/oder das Mondlandemodul auf ihre Ausgangsposition zurückgesetzt werden:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Konfigurieren der Placement Hints-Schaltfläche (Platzierungshinweise)
<!-- TODO: Rename to 'Configuring the Hints button'-->

Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > Buttons > **HintsButton**“ aus, erstellen Sie dann für die Komponente **Pressable Button (Script)** ein neues Ereignis **Button Pressed ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **TogglePlacementHints.ToggleGameObjects** als die auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Wenn Sie jetzt in den Spielmodus wechseln, stellen Sie fest, dass die durchscheinenden Platzierungshinweise standardmäßig deaktiviert sind, dass Sie sie aber ein- und ausschalten können, indem Sie die Hints-Schaltfläche (Hinweise) drücken:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben diese Anwendung vollständig konfiguriert. Jetzt ermöglicht es Ihnen Ihre Anwendung, das Mondlandemodul vollständig zu montieren, das Mondlandemodul zu starten, Hinweise umzuschalten und die Anwendung wieder auf Start zurückzusetzen.
