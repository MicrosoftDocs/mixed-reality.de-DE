---
title: 'Tutorials zu den ersten Schritten: 5 Interagieren mit 3D-Objekten'
description: Erfahren Sie mehr über einfache 3D-Inhalte und-Benutzeroberflächen, z. B. das Organisieren von 3D-Objekten und Begrenzungsrahmen für einfache Bearbeitung.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b807ac7e51e4009d2c44d3b7c67fbdf3488ccbd9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604991"
---
# <a name="5-interacting-with-3d-objects"></a>5. Interagieren mit 3D-Objekten

In diesem Tutorial erfahren Sie mehr über einfache 3D-Inhalte und Benutzeroberflächen, etwa das Organisieren von 3D-Objekten als Teil einer Sammlung, Begrenzungsrahmen für einfache Manipulation, Nah- und Ferninteraktion sowie Berührungs- und Greifgesten mit Hand-Tracking.

## <a name="objectives"></a>Ziele

* Erstellen eines Bereichs von 3D-Objekten, die für die anderen Lernziele verwendet werden
* Implementieren von Begrenzungsrahmen
* Konfigurieren von 3D-Objekten für grundlegende Manipulationen, wie etwa Bewegen, Drehen und Skalieren
* Erkunden von nahen und fernen Interaktionen
* Vermittlung von Informationen zu zusätzlichen Hand-Tracking-Gesten wie „Greifen“ und „Berühren“

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie das benutzerdefinierte Unity-Paket herunter, und importieren Sie es:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="decluttering-the-scene-view"></a>Aufräumen der Szenenansicht

Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die **scene visibility** (Sichtbarkeit in der Szene) für die Objekte **Cube** (Würfel) und **ButtonCollection** auf „Aus“ fest, indem Sie links neben den Objekten auf das **Augensymbol** klicken. Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Mehr zu den Steuerelementen für die Sichtbarkeit in der Szene und ihre Verwendung zum Optimieren Ihrer Szenenansicht und Ihres Workflows finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene).

## <a name="organizing-3d-objects-in-a-collection"></a>Organisieren von 3D-Objekten in einer Sammlung

In diesem Abschnitt erstellen Sie einen Bereich aus 3D-Objekten, die Sie beim Erforschen verschiedener Verfahren zur Interaktion mit 3D-Objekten in den folgenden Abschnitten dieses Tutorials verwenden. Insbesondere konfigurieren Sie die 3D-Objekte, die in einem 3x3-Raster angeordnet werden sollen.

Ähnlich wie beim [Erstellen eines Bereichs mit Schaltflächen](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection) sind dies die wichtigsten Schritte, die Sie dazu ausführen müssen:

1. Unterordnen der 3D-Objekte unter einem übergeordneten Objekt
2. Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. Unterordnen der 3D-Objekte unter einem übergeordneten Objekt

Sie müssen im Hierarchiefenster **ein leeres Objekt erstellen**, ihm einen passenden Namen geben, beispielsweise **3DObjectCollection** und es an einer geeigneten Stelle positionieren, z. B. X = 0, Y = -0,2, Z = 2.

Navigieren Sie im Projektfenster zu **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Ressourcen > MRTK.Tutorials.GettingStarted > Prefabs), und **unterordnen** Sie die folgenden Prefabs unter die **3DObjectCollection**:

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

Sie müssen im Hierarchiefenster **drei Würfel erstellen**, als untergeordnete Objekte der **3DObjectCollection**, deren **Transformationsmaßstab** Sie auf X = 0,15, Y = 0,15 und Z = 0,15 festlegen:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> Falls Sie zur Ausführung der oben aufgeführten Schritte eine Auffrischung benötigen, lesen Sie das Tutorial [Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md).

Ordnen Sie die Würfel neu an, sodass Sie jeden Würfel sehen können:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

Navigieren Sie im Projektfenster zu **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** (Ressourcen > MixedRealityToolkit.SDK > StandardAssets > Materialien), um die mit dem MRTK zur Verfügung gestellten Materialien anzuzeigen.

Bewegen Sie mithilfe von **Klicken und Ziehen** ein geeignetes Material auf die **Materials** Element 0-Eigenschaft des Gittermodell-Renderers jedes Würfels, beispielsweise:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“

Fügen Sie eine **Grid Object Collection (Script)** -Komponente (Rasterobjektsammlung (Skript)) zum **3DObjectCollection**-Objekt hinzu, und konfigurieren Sie sie wie folgt:

* Ändern Sie den **Sort Type** (Sortierungstyp) in **Child Order** (Reihenfolge untergeordneter Elemente), um sicherzustellen, dass die untergeordneten Objekte in der Reihenfolge sortiert werden, in der Sie sie unter dem übergeordneten Objekt platziert haben

Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren**, um die neue Konfiguration zu übernehmen:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Manipulieren von 3D-Objekten

In diesem Abschnitt fügen Sie die Funktion zum Manipulieren aller 3D-Objekte in dem Bereich hinzu, den Sie im vorherigen Abschnitt erstellt haben. Darüber hinaus geben Sie den Benutzern für die Prefab-Objekte die Möglichkeit, nach diesen Objekten mit nachverfolgten Händen zu greifen und sie zu fassen. Anschließend untersuchen Sie einige der Manipulationsverhaltensweisen, die Sie auf Ihre Objekte anwenden können.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Manipulation Handler (Script)-Komponente zu allen Objekten
2. Hinzufügen der Near Interaction Grabbable (Script)-Komponente (Nah-Interaktion, berührbar (Skript)) zu den Prefab-Objekten
3. Konfigurieren der Manipulation Handler (Script)-Komponente

> [!IMPORTANT]
> Damit Sie **ein Objekt manipulieren** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Manipulation Handler (Script)** -Komponente
>
> Damit Sie **ein Objekt manipulieren** und **mit nachverfolgten Händen greifen** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Manipulation Handler (Script)** -Komponente
> * **Near Interaction Grabbable (Script)** -Komponente (Nah-Interaktion, greifbar (Skript))

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Hinzufügen der Manipulation Handler (Script)-Komponente zu allen Objekten

Wählen Sie im Hierarchiefenster das Objekt **Cheese** (Käse) aus, halten Sie die **UMSCHALTTASTE** gedrückt, wählen Sie dann das **Cube () 2**-Objekt aus, und fügen Sie die **Manipulation Handler (Script)** -Komponente allen Objekten hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Im Rahmen dieses Tutorials wurden den Prefabs bereits Collider hinzugefügt. Für Unity-Primitive, wie etwa die Cube-Objekte, wird die Collider-Komponente beim Erstellen des Objekts automatisch hinzugefügt. In der Abbildung oben sind die Collider durch grüne Umrisslinien dargestellt. Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Hinzufügen der Near Interaction Grabbable (Script)-Komponente (Nah-Interaktion, berührbar (Skript)) zu den Prefab-Objekten

Wählen Sie im Hierarchiefenster das Objekt **Cheese** (Käse) aus, halten Sie die **UMSCHALTTASTE** gedrückt, wählen Sie dann das **TheModule**-Objekt aus, und fügen Sie die **Near Interaction Grabbable (Script)** -Komponente (Nah-Interaktion, greifbar (Skript)) allen Objekten hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. Konfigurieren der Manipulation Handler (Script)-Komponente

#### <a name="default-manipulation"></a>Standardmanipulation

Belassen Sie für das **Cube**-Objekt alle Eigenschaften auf den Standardwerten, um das Standardmanipulationsverhalten zu erleben:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Um eine Komponente auf ihre Standardwerte zurückzusetzen, können Sie das Symbol „Einstellungen“ der Komponente auswählen und auf „Zurücksetzen“ klicken.

#### <a name="restrict-manipulation-to-scale-only"></a>Einschränken der Manipulation nur auf die Größe

Ändern Sie für das **Cube (1)** -Objekt den **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) auf **Scale** (Maßstab), um dem Benutzer nur die Änderung der Objektgröße zu erlauben:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Einschränken der Bewegung auf einen festen Abstand vom Benutzer

Ändern Sie für das **Cube (2)** -Objekt **Constraint On Movement** (Bewegungseinschränkung) in **Fix Distance From Head** (Fester Abstand vom Kopf), sodass das Objekt, wenn es bewegt wird, immer den gleichen Abstand vom Benutzer beibehält:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Greifbar-Standardmanipulation

Belassen Sie für die Objekte **Cheese**, **CoffeeCup** und **EarthCore** alle Eigenschaften auf den Standardwerten, um das Greifbar-Standardmanipulationsverhalten zu erleben:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Entfernen der Möglichkeit zur Fernmanipulation

Deaktivieren Sie für das **Octa**-Objekt das Kontrollkästchen **Allow Far Manipulation** (Fern-Manipulation zulassen), um zu erreichen, dass der Benutzer mit dem Objekt nur direkt mithilfe der nachverfolgten Hände interagieren kann:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Drehen eines Objekts um seine Mitte

Ändern Sie für das **Platonic**-Objekt **One Hand Rotation Mode Near** (Einhanddrehungsmodus nah) und **One Hand Rotation Mode Far** (Einhanddrehungsmodus fern) in **Rotate About Object Center** (Drehung um Objektmitte), um zu erreichen, dass das Objekt sich um seine Mitte dreht, wenn der Benutzer es mit einer Hand dreht:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>Beibehalten der Bewegung nach dem Freigeben des Objekts

Fügen Sie für das **TheModule**-Objekt eine **Rigidbody**-Komponente hinzu, um physikalische Eigenschaften zu aktivieren, und deaktivieren Sie dann das Kontrollkästchen **Use Gravity** (Schwerkraft verwenden), damit das Objekt nicht durch Schwerkraft beeinflusst wird:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Überprüfen Sie in der Manipulation Handler (Script)-Komponente, dass für **Release Behavior** (Freigabeverhalten) sowohl **Keep Velocity** (Geschwindigkeit beibehalten) als auch **Keep Angular Velocity** (Winkelgeschwindigkeit beibehalten) aktiviert ist, sodass das Objekt seine Bewegung fortsetzt, wenn der Benutzer es mit seiner Hand freigibt:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Weitere Informationen über die Manipulationshandler-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zum [Manipulationshandler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Hinzufügen von Begrenzungsrahmen

Begrenzungsrahmen machen das einhändige Manipulieren von Objekten sowohl für die Nah- als auch für die Ferninteraktion komfortabler und intuitiver, indem sie Ziehpunkte bereitstellen, die für die Änderung der Größe und zum Rotieren verwendet werden können.

In diesem Beispiel fügen Sie dem EarthCore-Objekt einen Begrenzungsrahmen hinzu, damit die Interaktion mit diesem Objekt nun mithilfe der Objektmanipulation erfolgen kann, die Sie im vorherigen Abschnitt konfiguriert haben. Außerdem kann es mithilfe der Ziehpunkte des Begrenzungsrahmens gedreht und in der Größe verändert werden.

> [!IMPORTANT]
> Damit Sie **einen Begrenzungsrahmen** verwenden können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Bounding Box (Script)** -Komponente (Begrenzungsrahmen (Skript))

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Hinzufügen der Bounding Box (Script)-Komponente zum EarthCore-Objekt

Wählen Sie im Inspektorfenster das **EarthCore**-Objekt aus, und fügen Sie ihm die **Bounding Box (Script)** -Komponente hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> Die Visualisierungen von Begrenzungsrahmen werden zur Laufzeit erstellt und sind daher erst sichtbar, wenn Sie in den Spielmodus wechseln.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. Visualisieren und Testen des Begrenzungsrahmens mithilfe der in den Editor integrierten Simulation

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln. Drücken und halten Sie dann die Leertaste, um die Hand anzuzeigen, und verwenden Sie die Maus, um mit dem Begrenzungsrahmen zu interagieren:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Weitere Informationen über die Bounding Box-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zur [Bounding Box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Hinzufügen von Berührungseffekten

In diesem Beispiel aktivieren Sie Ereignisse, die ausgelöst werden, wenn Sie ein Objekt mit der Hand berühren. Insbesondere konfigurieren Sie das Octa-Objekt dafür, einen Soundeffekt wiederzugeben, wenn der Benutzer es berührt.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen einer Audioquellenkomponente zum Objekt
2. Hinzufügen der Komponente „Near Interaction touchable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Objekt
3. Hinzufügen der Komponente „Hand Interaction Touch (Script)“ (Handinteraktion, Berührung (Skript)) zum Objekt
4. Implementieren des On Touch Started-Ereignisses
5. Testen der Berührungsinteraktion mithilfe der Simulation im Editor

> [!IMPORTANT]
> Damit Sie **Berührungsereignisse auslösen** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, vorzugsweise ein Feld-Collider
> * **Near Interaction touchable (Script)** -Komponente (Nah-Interaktion, berührbar (Skript))
> * **Hand Interaction Touch (Script)** -Komponente (Handinteraktion Berührung (Skript))

> [!NOTE]
> Die Komponente „Hand Interaction Touch (Script)“ (Handinteraktion Berührung (Skript)) ist nicht Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen dieses Tutorials importiert und ist ursprünglich Teil der MixedReality Toolkit Unity-Beispiele.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. Hinzufügen einer Audioquellenkomponente zum Objekt

Wählen Sie im Hierarchiefenster das **Octa**-Objekt aus, fügen Sie ihm eine **Audioquelle**-Komponente hinzu, und ändern Sie dann **Spatial Blend** (Räumliche Mischung) in 1, um räumliche Audiowiedergabe zu aktivieren:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Hinzufügen der Komponente „Near Interaction touchable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Objekt

Fügen Sie bei noch ausgewähltem **Octa**-Objekt dem Octa-Objekt die Komponente **Near Interaction Touchable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzu, und klicken Sie dann auf die Schaltflächen **Fix Bounds** (Begrenzungen fixieren) und **Fix Center** (Mitte fixieren), um die Eigenschaften „Local Center“ und „Bounds“ von Near Interaction Touchable (Script) so zu aktualisieren, dass sie mit dem Feld-Collider übereinstimmen:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. Hinzufügen der Komponente „Hand Interaction Touch (Script)“ (Handinteraktion Berührung (Skript)) zum Objekt

Fügen Sie bei immer noch ausgewähltem **Octa**-Objekt dem Octa-Objekt die **Hand Interaction Touch (Script)** -Komponente hinzu:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. Implementieren des On Touch Started-Ereignisses

Klicken Sie in der **Hand Interaction Touch (Script)** -Komponente auf das kleine **+** -Symbol, um ein neues **On Touch Started ()** -Ereignis zu erstellen. Konfigurieren Sie anschließend das **Octa**-Objekt für den Empfang des Ereignisses, und definieren Sie **AudioSource.PlayOneShot** als die auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Navigieren Sie zu **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** (Ressourcen > MixedRealityToolkit.SDK > StandardAssets > Audio), um die mit dem MRTK mitgelieferten Audioclips anzuzeigen, und weisen Sie dann dem Feld **Audio Clip** einen passenden Audioclip zu, beispielsweise den Audioclip „MRTK_Gem“:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Implementieren von Ereignissen benötigen, lesen Sie die Anweisungen unter [Gesten für Hand-Tracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. Testen der Berührungsinteraktion mithilfe der Simulation im Editor

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln. Drücken und halten Sie dann die LEERTASTE, um die Hand anzuzeigen, und verwenden Sie die Maus, um das Octa-Objekt zu berühren und den Soundeffekt auszulösen:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Wie Sie beim Testen der Berührungsinteraktion gesehen haben und es in der Abbildung oben dargestellt ist, pulsierte die Farbe des Octa-Objekts, während es berührt wurde. Dieser Effekt ist in der Hand Interaction Touch (Script)-Komponente hart codiert und kein Ergebnis der Ereigniskonfiguration, die Sie in den Schritten oben abgeschlossen haben.
>
> Wenn Sie diesen Effekt deaktivieren möchten, können Sie beispielsweise Zeile 32 'TargetRenderer = GetComponentInChildren<Renderer>();' auskommentieren, was dazu führt, dass TargetRenderer den Wert null beibehält und die Farbe nicht pulsiert.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie 3D-Objekte in einer Rastersammlung organisieren und wie Sie diese Objekte durch Nah-Interaktion (direktes Greifen mit nachverfolgten Händen) und Fern-Interaktion (mit Lichtstrahlen zum Anvisieren oder Handstrahlen) manipulieren (Skalieren, Drehen und Bewegen) können. Sie haben außerdem erfahren, wie Sie um 3D-Objekte herum Begrenzungsrahmen positionieren, und wie Sie die Ziehpunkte für die Begrenzungsrahmen verwenden und anpassen können. Schließlich haben Sie erfahren, wie Sie beim Berühren eines Objekts Ereignisse auslösen können.

[Nächste Lektion: 6. Untersuchen erweiterter Eingabeoptionen](mrlearning-base-ch5.md)
