---
title: 'Tutorials zu den ersten Schritten: 5. Interagieren mit 3D-Objekten'
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555501"
---
# <a name="5-interacting-with-3d-objects"></a>5. interagieren mit 3D-Objekten

In diesem Tutorial erfahren Sie mehr über grundlegende 3D-Inhalte und-Benutzeroberflächen, wie z. b. das Organisieren von 3D-Objekten als Teil einer Auflistung, das umschließende Kästchen für die grundlegende Bearbeitung, die Near-und die weite Interaktion und das Berühren von Handbewegungen und Hand Eingaben

## <a name="objectives"></a>Ziele

* Erstellen Sie einen Bereich von 3D-Objekten, die für die anderen Lernziele verwendet werden.
* Implementieren von Begrenzungsrahmen
* Konfigurieren von 3D-Objekten für grundlegende Manipulationen, z. b. verschieben, drehen und Skalieren
* Erkunden von nahen und fernen Interaktionen
* Weitere Informationen zu weiteren Hand nach Verfolgungs Gesten, z. b. zum Erfassen und berühren

## <a name="importing-the-tutorial-assets"></a>Importieren der tutorialassets

Herunterladen und Importieren des benutzerdefinierten Unity-Pakets:

* [Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

Nachdem Sie die tutorialassets importiert haben, sollte Ihr Projektfenster etwa wie folgt aussehen:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Eine Erinnerung zum Importieren eines benutzerdefinierten Unity-Pakets finden Sie in den Anweisungen zum [Importieren von Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

## <a name="decluttering-the-scene-view"></a>Die Szenen Ansicht wird entcluttert.

Um die Arbeit mit Ihrer Szene zu vereinfachen, legen Sie die **Sichtbarkeit der Szene** für die **Cube** -und **buttoncollection** -Objekte auf OFF fest, indem Sie auf das **Augen** Symbol links neben den Objekten klicken. Dadurch wird das Objekt im Szenen Fenster ausgeblendet, ohne die in-Game-Sichtbarkeit zu ändern:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Weitere Informationen zu den Steuerelementen für die Szenen Sichtbarkeit und deren Verwendung zur Optimierung Ihrer Szenen Ansicht und des Workflows finden Sie in der Dokumentation zur <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Szene Sichtbarkeit</a> von Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Organisieren von 3D-Objekten in einer Sammlung

In diesem Abschnitt erstellen Sie einen Bereich von 3D-Objekten, die Sie verwenden werden, wenn Sie in den folgenden Abschnitten dieses Tutorials verschiedene Möglichkeiten der Interaktion mit 3D-Objekten untersuchen. Insbesondere konfigurieren Sie die 3D-Objekte, die auf einem 3 x 3-Raster positioniert werden sollen.

Ähnlich wie bei der [Erstellung eines Bereichs von Schalt](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)Flächen werden folgende Hauptschritte ausgeführt:

1. Übergeordnetes Element der 3D-Objekte zu einem übergeordneten Objekt
2. Hinzufügen und Konfigurieren der Komponente "Raster Objekt Auflistung (Skript)"

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. übergeordnetes Element der 3D-Objekte zu einem übergeordneten Objekt

Erstellen Sie im Hierarchie Fenster **ein leeres-Objekt**, geben Sie ihm einen passenden Namen, z **. b. 3dobjectcollection**, und positionieren Sie es an einem geeigneten Speicherort, z. b. X = 0, Y =-0,2, Z = 2.

Navigieren Sie im Projektfenster zu **Assets** > **mrtk. Tutorials. GettingStarted** > **Prefabs** **und dann die** folgenden Prefabs der **3dobjectcollection**übergeordnet:

* Käse
* CoffeeCup
* Erdkern
* Octacore
* Platonic
* Das Modul

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

Erstellen Sie im Fenster Hierarchie **drei Cubes** als untergeordnete Objekte der **3dobjectcollection** , und legen Sie Ihre Transformations **Skala** auf X = 0,15, Y = 0,15, Z = 0,15 fest:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> Eine Erinnerung, wie Sie die oben aufgeführten Schritte ausführen, finden Sie im Tutorial Erstellen von [Benutzeroberflächen und Konfigurieren von Mixed Reality Toolkit](mrlearning-base-ch2.md) .

Positionieren Sie die Cubes neu, damit Sie jeden Cube sehen können:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

Navigieren Sie im Projektfenster zu **Assets** > **mixedrealitytoolkit. SDK** > **standardassets** > **Material** , um die Materialien anzuzeigen, die mit dem mrtk bereitgestellt werden.

**Klicken und ziehen Sie** ein geeignetes Material auf die mesrenderer **Materials** Element 0-Eigenschaft jedes Cubes, z. b.:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. hinzufügen und Konfigurieren der Raster Objekt-Sammlungs Komponente (Skript)

Fügen Sie dem **3dobjectcollection-** Objekt eine Komponente für eine **Raster Objekt Auflistung (Skript)** hinzu, und konfigurieren Sie Sie wie folgt:

* Ändern Sie den **Sortierungstyp** in die untergeordnete **Reihenfolge** , um sicherzustellen, dass die untergeordneten Objekte in der Reihenfolge sortiert werden, in der Sie

Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren** , um die neue Konfiguration zu übernehmen:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Bearbeiten von 3D-Objekten

In diesem Abschnitt fügen Sie die Möglichkeit hinzu, alle 3D-Objekte in dem Bereich zu bearbeiten, den Sie im vorherigen Abschnitt erstellt haben. Außerdem können Sie für die Prefab-Objekte es Benutzern ermöglichen, diese Objekte mit nach verfolgten Händen zu erreichen und zu erfassen. Anschließend werden Sie einige Manipulations Verhalten untersuchen, die Sie auf Ihre Objekte anwenden können.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Bearbeitungs Handler-Komponente (Skript) zu allen Objekten
2. Hinzufügen der fast-interaktionsgrabbable-Komponente (Skript) zu den Prefab-Objekten
3. Konfigurieren der Manipulations Handler-Komponente (Skript)

> [!IMPORTANT]
> Um **ein Objekt bearbeiten**zu können, muss das-Objekt über die folgenden Komponenten verfügen:
>
> * **Collider** -Komponente, z. b. ein Box-Collider
> * **Bearbeitungs Handler (Skript)** -Komponente
>
> **Damit ein Objekt mit nach verfolgten Händen**bearbeitet und gezogen werden kann, muss das-Objekt über die folgenden Komponenten verfügen:
>
> * **Collider** -Komponente, z. b. ein Box-Collider
> * **Bearbeitungs Handler (Skript)** -Komponente
> * **Near-Interaktion (Skript-)** Komponente

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Fügen Sie die Bearbeitungs Handlerkomponente (Skript) allen Objekten hinzu.

Wählen Sie im Fenster Hierarchie das **Käse** Objekt aus, halten Sie die **UMSCHALT** Taste gedrückt, und wählen Sie dann das Cube-Objekt **() 2** aus, und fügen Sie die **Bearbeitungs Handlerkomponente (Skript)** allen Objekten hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Im Rahmen dieses Tutorials wurden den Prefabs bereits Colliders hinzugefügt. Für Unity-primitive, z. b. die Cubeobjekte, wird die Collider-Komponente automatisch hinzugefügt, wenn das-Objekt erstellt wird. In der obigen Abbildung werden die Kollisionen durch die grünen Gliederungen dargestellt. Weitere Informationen zu Kollisionen finden Sie in der <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> -Dokumentation von Unity.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Hinzufügen der fast-interaktionsgrabbable-Komponente (Skript) zu den Prefab-Objekten

Wählen Sie im Fenster Hierarchie das **Käse** Objekt aus, halten Sie die **UMSCHALT** Taste gedrückt, und wählen Sie dann das Objekt "- **Modul** " aus, und fügen Sie die Komponente " **near Interaktion grabbable (Skript)** " zu allen Objekten hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. Konfigurieren der Manipulations Handler-Komponente (Skript)

#### <a name="default-manipulation"></a>Standard Manipulation

Belassen Sie für das **Cube** -Objekt standardmäßig alle Eigenschaften, damit das Standardverhalten der Manipulation angezeigt wird:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Wenn Sie eine Komponente auf die Standardwerte zurücksetzen möchten, können Sie das Einstellungssymbol der Komponente auswählen und auf Zurücksetzen klicken.

#### <a name="restrict-manipulation-to-scale-only"></a>Beschränken der Bearbeitung auf die Skalierung

Ändern Sie für das Cube-Objekt **(1)** den **zwei handungstyp** für die Bearbeitung in " **Scale** ", sodass der Benutzer nur die Größe des Objekts ändern kann:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Beschränken Sie die Bewegung auf einen eingeschränkten Abstand vom Benutzer.

Ändern Sie für das Cube-Objekt **(2)** die **Einschränkung bei der Bewegung** , um die **Entfernung vom Kopf zu korrigieren** , sodass beim Verschieben des Objekts der gleiche Abstand zum Benutzer besteht:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Standardmäßige abbrechbare Manipulation

Belassen Sie für die Objekte " **Käse**", " **coffecup**" und " **Erdkern** " standardmäßig alle Eigenschaften, um das Standardverhalten für die abrechenbare Manipulation zu erleben:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Entfernen der Funktion für eine lange Bearbeitung

Deaktivieren Sie für das **Octa** -Objekt das Kontrollkästchen " **lange Bearbeitung zulassen** ", um es zu machen, damit der Benutzer nur mit dem Objekt direkt über verfolgte Hände interagieren kann:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Drehen eines Objekts um seinen Mittelpunkt

Ändern Sie für das **platonische** Objekt den **1-Hand-Rotationsmodus in der Nähe** und den Modus für die manuelle **Drehung** , um das Objekt **Center zu drehen** , um dies zu ermöglichen, wenn der Benutzer das Objekt mit einer Hand dreht, dreht es sich um den Mittelpunkt des Objekts:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>Bewegung nach Veröffentlichung des Objekts beibehalten

Fügen Sie für das Objekt "- **Module** " eine **Rigidbody** -Komponente hinzu, um die Physik zu aktivieren, und deaktivieren Sie dann das Kontrollkästchen **use Gravity** , damit das Objekt nicht von der Schwerkraft betroffen ist:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Stellen Sie sicher, dass das **Freigabe Verhalten** auf der Bearbeitungs Handlerkomponente (Skript) so festgelegt ist, dass sowohl die **Geschwindigkeit beibehalten** als auch die **Angular-Geschwindigkeit beibehalten** wird.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Weitere Informationen zur handlerhandlerkomponente und den zugehörigen Eigenschaften finden Sie im Handbuch mit [Manipulations Handlern](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Hinzufügen von Begrenzungs Feldern

Begrenzungs Felder vereinfachen und intuitiver das Bearbeiten von Objekten mit einer Hand für die Near-und Far-Interaktion durch Bereitstellen von Handles, die für die Skalierung und Rotation verwendet werden können.

In diesem Beispiel fügen Sie dem erdcore-Objekt ein Begrenzungsfeld hinzu, damit dieses Objekt nun mit der Objekt Bearbeitung, die Sie im vorherigen Abschnitt konfiguriert haben, interagiert und mithilfe der umgebenden Feld Handles skaliert und gedreht werden kann.

> [!IMPORTANT]
> Um ein **Begrenzungsfeld**verwenden zu können, muss das-Objekt über die folgenden Komponenten verfügen:
>
> * **Collider** -Komponente, z. b. ein Box-Collider
> * **Begrenzungs Box-Komponente (Skript)**

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Hinzufügen der umgebenden Box-Komponente (Skript) zum Erdkern Objekt

Wählen Sie im Inspektor-Fenster das **Erdkern** Objekt aus, und fügen Sie die Komponente für das umgebende **Feld (Skript)** dem Objekt "Erdkern" hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> Die Visualisierungen des umgebenden Felds werden zur Laufzeit erstellt und daher nicht angezeigt, bevor Sie in den Spielmodus wechseln.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. visualisieren und testen Sie das umgebende Feld mithilfe der in-Editor-Simulation.

Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben. Halten Sie die Leertaste gedrückt, um die Hand zu bringen, und verwenden Sie die Maus, um mit dem umgebenden Feld zu interagieren:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Weitere Informationen zur Begrenzungsfeld Komponente und den zugehörigen Eigenschaften finden Sie im Leitfaden für [Begrenzungs](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) Felder im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Hinzufügen von Berührungs Effekten

In diesem Beispiel werden Ereignisse aktiviert, die ausgelöst werden, wenn Sie ein Objekt mit der Hand berühren. Insbesondere konfigurieren Sie das Octa-Objekt so, dass es einen Soundeffekt spielt, wenn der Benutzer es berührt.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Fügen Sie dem-Objekt eine audioquellkomponente hinzu.
2. Fügen Sie dem-Objekt die touchable-Komponente der Near-Interaktion (Skript) hinzu.
3. Fügen Sie die Komponente "Hand Interaktion (Skript)" zum Objekt hinzu.
4. Implementieren des Ereignisses on Touchscreen Started
5. Testen der Berührungs Interaktion mithilfe der in-Editor-Simulation

> [!IMPORTANT]
> Damit **Berührungs Ereignisse auslöst**werden können, muss das-Objekt über die folgenden Komponenten verfügen:
>
> * **Collider** -Komponente, vorzugsweise ein Box-Collider
> * **Touchable-Komponente der Near-Interaktion (Skript)**
> * **Hand Interaktion (Skript)** -Komponente

> [!NOTE]
> Die Komponente "Hand Interaktion (Skript)" ist nicht Bestandteil von mrtk. Es wurde mit den Assets dieses Lernprogramms importiert und ursprünglich Teil des mixedreality Toolkit Unity-Beispielen.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. Fügen Sie dem Objekt eine audioquellkomponente hinzu.

Wählen Sie im Fenster Hierarchie das **Octa** -Objekt aus, fügen Sie dem Octa-Objekt eine **audioquellkomponente** hinzu, und ändern Sie dann **räumliche Blend** in 1, um räumliche Audiodaten zu aktivieren:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Hinzufügen der Near-interaktionstouchable-Komponente (Skript) zum Objekt

Wenn das **Octa** -Objekt noch ausgewählt ist, fügen Sie dem Octa-Objekt die touchable-Komponente der **near-Interaktion (Script)** hinzu, und klicken Sie dann auf die Schaltflächen **fixbegrenzungen** und **Fix Center** , um die Eigenschaften des lokalen Centers und der Begrenzungen der Near-interaktionstouchable (Script) zu aktualisieren

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. Fügen Sie dem Objekt die Komponente "Hand Interaktion (Skript)" hinzu.

Wenn das **Octa** -Objekt noch ausgewählt ist, fügen Sie dem Octa-Objekt die Komponente " **Hand Interaktion (Skript)** " hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. implementieren Sie das Ereignis "on Touchscreen Started".

Klicken Sie in der Komponente **Hand Interaktion (Skript)** auf das kleine **+** Symbol, um ein neues **on Touchscreen-Ereignis ()** zu erstellen. Konfigurieren Sie dann das **Octa** -Objekt so, dass es das Ereignis empfängt, und definieren Sie **audiosource. playoneshot** als Aktion, die ausgelöst werden soll:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Navigieren Sie zu **Assets** > **mixedrealitytoolkit. SDK** > **standardassets** > Material, um Audioclips anzuzeigen, die mit dem mrtk bereitgestellt werden, und weisen Sie dann dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. den MRTK_Gem Audioclip:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Eine Erinnerung, wie Ereignisse implementiert werden können, finden Sie in den Anweisungen [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. Testen der Berührungs Interaktion mithilfe der in-Editor-Simulation

Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben. Halten Sie die Leertaste gedrückt, um die Hand zu bringen, und verwenden Sie die Maus, um das Octa-Objekt zu berühren und den Soundeffekt zu initiieren:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Wie Sie gesehen haben, als Sie die Berührungs Interaktion getestet haben, und wie in der obigen Abbildung gezeigt, wurde die Octa-Objekt Farbe während der Arbeit gepultet. Dieser Effekt ist in der Komponente "Hand Interaktion berühren (Skript)" hart codiert und ist nicht das Ergebnis der Ereignis Konfiguration, die Sie in den obigen Schritten abgeschlossen haben.
>
> Wenn Sie diesen Effekt deaktivieren möchten, können Sie z. b. "targetrenderer = getcomponentinchildren<Renderer>();" auskommentieren oder Zeile 32, was dazu führt, dass der targetrenderer NULL bleibt und die Farbe nicht pullt wird.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie 3D-Objekte in einer Raster Auflistung organisieren und wie Sie diese Objekte (Skalieren, drehen und verschieben) mithilfe der Near-Interaktion (direkt mit nach verfolgten Händen) und der äußersten Interaktion (mit Blick-und Handzeichen) bearbeiten können. Sie haben auch gelernt, wie sie umgebende Felder um 3D-Objekte platzieren und wie Sie die Handles in den Begrenzungs Feldern verwenden und anpassen können. Schließlich haben Sie erfahren, wie Sie beim Berühren eines Objekts Ereignisse auslösen können.

[Nächste Lektion: 6. untersuchen der erweiterten Eingabeoptionen](mrlearning-base-ch5.md)
