---
title: Tutorials zu den ersten Schritten-7. Erstellen einer Beispielanwendung für ein Mond Modul
description: In dieser Lektion kombinieren Sie mehrere Konzepte, die Sie aus vorherigen Lektionen gelernt haben, um eine einzigartige Stichprobe zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555278"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Erstellen einer Beispielanwendung für ein Mond Modul
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

In diesem Tutorial werden mehrere Konzepte aus früheren Lektionen kombiniert, um ein eindeutiges Beispiel zu erstellen. Sie erfahren, wie Sie eine teilassemblyanwendung erstellen, in der ein Benutzer überwachte Hände verwenden muss, um Teile zu erfassen und zu versuchen, ein Mond Modul zusammenzustellen. Mithilfe von druckbaren Schaltflächen können Sie Platzierungs Hinweise ein-und ausschalten, die Leistung zurücksetzen und das Mond Modul in den Raum bringen!

In zukünftigen Tutorials werden Sie weiterhin auf dieser Benutzer Funktionalität aufbauen, die leistungsstarke mehr Benutzer Anwendungsfälle umfasst, die räumliche Azure-Anker für räumliche Ausrichtung nutzen.

## <a name="objectives"></a>Ziele

* Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen
* Informationen zum Umschalten von Objekten
* Auslösen komplexer Ereignisse über drückbare Schaltflächen
* Verwenden der physischen Effekte und Kräfte von Starrkörpern
* Erkunden der Verwendung von QuickInfos

## <a name="lunar-module-parts-overview"></a>Übersicht über die Komponenten von Mond Modulen
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

In diesem Abschnitt erstellen Sie eine einfache teilassemblyherausforderung, bei der das Ziel des Benutzers darin besteht, fünf Teile, die in der Tabelle verteilt sind, am richtigen Speicherort im Mond Modul zu platzieren.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Prefab für das Raketenstart Programm zur Szene
2. Aktivieren der Objekt Bearbeitung für alle Teile
3. Hinzufügen und Konfigurieren der Komponente "Part Assembly Demo (Skript)"

> [!NOTE]
> Die Komponente "Part Assembly Demo (Skript)" ist nicht Bestandteil von mrtk. Es wurde mit den Assets dieses Tutorials bereitgestellt.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Fügen Sie der Szene die Prefab des Raketenstart Programms hinzu.

Navigieren Sie im Projektfenster zu den **Assets** > **mrtk. Tutorials. GettingStarted** > Ordner **Prefabs** > **RocketLauncher** , ziehen Sie den **RocketLauncher** -Prefab in das Hierarchie Fenster, um ihn Ihrer Szene hinzuzufügen, und positionieren Sie ihn dann an einem geeigneten Speicherort, z. b.:

* Transformations Position X = 1,5, Y =-0,4, Z = 0, sodass Sie auf der rechten Seite des Benutzers bei der Taillenhöhe positioniert ist.
* Transformations Drehung X = 0, Y = 180, Z = 0, sodass die Hauptfunktionen der Benutzeroberflächen dem Benutzer ausgesetzt sind

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. Aktivieren Sie die Objekt Bearbeitung für alle Teile.

Suchen Sie im Fenster Hierarchie nach dem Objekt RocketLauncher > **lunarmoduleparts** , und wählen Sie alle untergeordneten **Objekte**aus. Fügen Sie dann die Komponente **Manipulations Handler (Skript)** und **near Interaktion grabbable (Script)** hinzu, und konfigurieren Sie dann den Manipulations Handler (Skript) wie folgt:

* Deaktivieren Sie das Kontrollkästchen " **lange Bearbeitung zulassen** ", um nur die Near-Interaktion zuzulassen.
* Ändern von **zwei handungstyp** zum **verschieben** ändern, sodass die Skalierung deaktiviert ist

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Eine Erinnerung, eine Schritt-für-Schritt-Anleitung zur Implementierung der Objekt Bearbeitung, finden Sie in den Anweisungen zum Bearbeiten von [3D-Objekten](mrlearning-base-ch4.md#manipulating-3d-objects) .

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. hinzufügen und Konfigurieren der Komponente "Part Assembly Demo (Skript)"

Wenn alle untergeordneten Objekte von lunarmoduleparts noch ausgewählt sind, fügen Sie eine **audioquellkomponente** hinzu, und konfigurieren Sie Sie wie folgt:

* Weisen Sie dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. MRKT_Scale_Start
* Deaktivieren Sie das Kontrollkästchen **Play on wacht** , sodass der Audioclip beim Laden der Szene nicht automatisch wiedergegeben wird.
* **Räumliche Blend** in 1 ändern, um räumliche Audiodaten zu ermöglichen

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Wenn alle untergeordneten Objekte von lunarmoduleparts weiterhin ausgewählt sind, fügen Sie die Komponente **Part Assembly Demo (Skript)** hinzu:

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

Wählen Sie im Fenster "Hierarchie" das **roverenclosure** -Objekt aus, und konfigurieren Sie die Komponente " **Part Assembly Demo (Skript)** " wie folgt:

* Weisen Sie das Objekt **selbst**, in diesem Fall das roverenclosure-Objekt, dem Objekt **zu platzieren** .
* Weisen Sie im Feld **Speicherort** die entsprechenden Platz **Halter** Objekte zu, in diesem Fall das RoverEnclosure_PlacementHint Objekt.
* Weisen Sie im Feld QuickInfo- **Objekt** **die entsprechende**QuickInfo zu, in diesem Fall das RoverEnclosure_ToolTip Objekt.
* Weisen Sie das Objekt **selbst**(in diesem Fall das roverenclosure-Objekt) dem Feld **Audioquelle** zu.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Wiederholen** Sie diesen Schritt für jedes der anderen untergeordneten lunarmoduleparts-Objekte, z. b. fueltank, energycell, dockingportal und externalsensor.

Wenn Sie nun in den Spielmodus wechseln und ein ' Objekt an den Ort ' in der Nähe von ' Location to Place ' verschieben, werden Sie Folgendes bemerken:

* Das Objekt wird an der Stelle ausgerichtet und unter dem lunarmodule-Objekt untergeordnet, sodass es Teil des mondmoduls wird.
* Die Audioquelle des Objekts übernimmt den zugewiesenen Audioclip an der Position des Objekts.
* Das entsprechende QuickInfo-Objekt wird ausgeblendet.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Eine Erinnerung zur Verwendung der in-Editor-Eingabe Simulation finden Sie unter [Verwenden der in-Editor-Hand Eingabe Simulation zum Testen eines Szenen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Handbuchs im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Konfigurieren der Mondlandefähre

In diesem Abschnitt fügen Sie der Anwendung für das Raketenstart Programm zusätzliche Features hinzu, damit der Benutzer folgende Aktionen ausführen kann:

* Interagieren mit dem Lunar-Modul
* Starten Sie das Mond Modul, und geben Sie einen Sound wieder, wenn es gestartet wird.
* Setzen Sie die Anwendung zurück, damit das Mond Modul und alle Teile wieder an der ursprünglichen Position abgelegt werden.
* Blenden Sie die Platzierungs Hinweise aus, um die Herausforderung der Teile Assembly zu erschweren.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Objekt Bearbeitung aktivieren
2. Aktivieren der Physik
3. Hinzufügen einer audioquellkomponente
4. Hinzufügen und Konfigurieren der Komponente "Launch Lunar Module (Script)"
5. Hinzufügen und Konfigurieren der Komponente zum Umschalten der Platzierungs Hinweise (Skript)

> [!NOTE]
> Die Komponente Launch Lunar Module (Script) und die Funktion zum Umschalten der Platzierungs Hinweise (Skript) sind nicht Teil von mrtk. Sie wurden mit den Assets dieses Tutorials bereitgestellt.

### <a name="1-enable-object-manipulation"></a>1. Aktivieren der Objekt Bearbeitung

Wählen Sie im Fenster Hierarchie das Objekt RocketLauncher > **lunarmodule** aus, fügen Sie die Komponente **Manipulations Handler (Skript)** und **near Interaktion grabbable (Skript)** hinzu, und konfigurieren Sie dann den Manipulations Handler (Skript) wie folgt:

* Deaktivieren Sie das Kontrollkästchen " **lange Bearbeitung zulassen** ", um nur die Near-Interaktion zuzulassen.
* Ändern von **zwei handungstyp** zum Verschieben ändern, sodass die Skalierung deaktiviert ist

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. Aktivieren der Physik

Wenn das RocketLauncher > **lunarmodule** -Objekt noch ausgewählt ist, fügen Sie eine **Rigidbody** -Komponente hinzu, und konfigurieren Sie Sie dann wie folgt:

* Deaktivieren Sie das Kontrollkästchen **use Gravity** , damit das Lunar-Modul nicht von der Schwerkraft betroffen ist.
* Aktivieren Sie das Kontrollkästchen **ist Kinematic** , damit das Mond Modul anfänglich nicht von Physic-Kräften betroffen ist.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. Hinzufügen einer audioquellkomponente

Wenn das Objekt RocketLauncher > **lunarmodule** noch ausgewählt ist, fügen Sie eine **audioquellkomponente** hinzu, und konfigurieren Sie Sie dann wie folgt:

* Ändern von **Spatial Blend** in 1 zum Aktivieren räumlicher Audiodaten

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. hinzufügen und Konfigurieren der Komponente "Launch Lunar Module (Script)"

Wenn das Objekt RocketLauncher > **lunarmodule** noch ausgewählt ist, fügen Sie die Komponente **Launch Lunar Module (Script)** hinzu, und konfigurieren Sie Sie dann wie folgt:

* Ändern **Sie** den Werte Wert, damit das Mond Modul beim Start ordnungsgemäß gestartet wird, z. b. in 0,01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. hinzufügen und Konfigurieren der Komponente zum Umschalten der Platzierungs Hinweise (Skript)

Wenn das Objekt RocketLauncher > **lunarmodule** noch ausgewählt ist, fügen Sie die Komponente zum **Umschalten der Platzierungs Hinweise (Skript)** hinzu, und konfigurieren Sie Sie dann wie folgt:

* Legen Sie die Eigenschaft "Spielobjekt Array **Größe** " auf 5 fest.
* Weisen Sie jedes der untergeordneten **Objekte** von "RocketLauncher > lunarmodule > **placementhints** " dem **Element** Feld im Spielobjekt Array zu:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Konfigurieren der Schaltfläche "starten"

Wählen Sie im Fenster Hierarchie die > Schaltflächen RocketLauncher > **launchbutton** -Objekt aus, und erstellen Sie dann auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Button-Ereignis **()** , und konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, und erstellen Sie **launchlunarmodule. startthruster** als auszulösenden Aktion

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Eine Erinnerung, wie Ereignisse implementiert werden können, finden Sie in den Anweisungen [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .

Wenn die Schaltflächen RocketLauncher > > **launchbutton** -Objekt noch ausgewählt ist, erstellen Sie auf der **Schaltfläche "Druck Bare Schaltfläche (Skript)** " ein neues Button-Ereignis **()** , konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, definieren Sie **audiosource. playoneshot** als auszulösenden Aktion, und weisen Sie dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. den MRTK_Gem Audioclip:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Wenn die Schaltflächen RocketLauncher > > **launchbutton** -Objekt noch ausgewählt ist, erstellen Sie auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Fingerabdruck Ereignis **()** , konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, und definieren Sie **launchlunarmodule. stopthruster** als Aktion, die ausgelöst werden soll:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Wenn Sie jetzt den Spielmodus eingeben und auf die Schaltfläche "Start" klicken, wird der Audioclip abgespielt. Wenn Sie die Schaltfläche "Start" für ungefähr eine Sekunde oder länger gedrückt halten, sehen Sie, dass das Mond Modul in den Speicherplatz wechselt:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Konfigurieren der Schaltfläche Zurücksetzen

Wählen Sie im Fenster Hierarchie die Schaltflächen RocketLauncher > > **ResetButton** -Objekt aus, und erstellen Sie dann auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Button-Ereignis **()** , und konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen. Legen Sie **launchlunarmodule. resetmodule als auszulösenden** Aktion fest

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Wenn die Schaltflächen RocketLauncher > **> ResetButton** -Objekt noch ausgewählt ist, erstellen Sie auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Button-Ereignis **()** , konfigurieren Sie das " **RocketLauncher** "-Objekt, um das Ereignis zu empfangen, legen Sie " **gameobject. broadcastmessage** " als auszulösenden **Aktion** fest

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> Die Aktion "gameobject. broadcastmessage" sendet die resetplacement-Nachricht vom "RocketLauncher"-Objekt an das gesamte untergeordnete Objekt. Jedes untergeordnete Objekt, das über die resetplacement-Funktion verfügt, die in der Komponente Part Assembly Demo (Skript) definiert ist, die Sie allen untergeordneten Objekten von lunarmoduleparts hinzugefügt haben, ruft die resetplacement-Funktion auf, die die Platzierung des untergeordneten Objekts zurücksetzt.

Wenn Sie jetzt den Spielmodus wechseln, einige Teile verschieben und/oder das Modul "Mond" starten und dann auf die Schaltfläche "Zurücksetzen" klicken, sehen Sie, dass die Teile und/oder das Mond Modul an die ursprüngliche Position zurückgesetzt werden:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Konfigurieren der Schaltfläche Platzierungs Hinweise
<!-- TODO: Rename to 'Configuring the Hints button'-->

Wählen Sie im Fenster Hierarchie die Schaltflächen RocketLauncher > > **hinzbutton** -Objekt aus, und erstellen Sie dann auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Schaltflächen- **()** Ereignis, konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, und definieren Sie " **deggleplacementhints**

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Wenn Sie jetzt den Spielmodus eingeben, werden Sie feststellen, dass die über sichtigen Platzierungs Hinweise standardmäßig deaktiviert sind. Sie können Sie jedoch durch Drücken der Schaltfläche "Hinweise" aktivieren und deaktivieren.

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben diese Anwendung vollständig konfiguriert. Nun können Benutzer mit Ihrer Anwendung das Mond Modul vollständig Assemblieren, das Mond Modul starten, Hinweise umschalten und die Anwendung zurücksetzen, damit Sie erneut gestartet wird.
