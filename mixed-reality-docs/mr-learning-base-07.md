---
title: 'Tutorials zu den ersten Schritten: 7 Interagieren mit 3D-Objekten'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376422"
---
# <a name="7-interacting-with-3d-objects"></a>7. Interagieren mit 3D-Objekten

In diesem Tutorial erfahren Sie, wie Sie die nahe und ferne Manipulation von 3D-Objekten aktivieren und die zulässigen Manipulationsarten einschränken. Darüber hinaus erfahren Sie, wie Sie 3D-Objekte mit Begrenzungsrahmen umgeben, um die Steuerung der Objektmanipulation zu vereinfachen.

## <a name="objectives"></a>Ziele

* Erfahren, wie 3D-Objekte so konfiguriert werden, dass Interaktion mit ihnen möglich ist
* Erfahren, wie 3D-Objekte mit Begrenzungsrahmen versehen werden

## <a name="manipulating-3d-objects"></a>Manipulieren von 3D-Objekten

In diesem Abschnitt fügen Sie die Funktion zum Manipulieren aller Teile des Rovers hinzu, die Sie im Rahmen des Tutorials [Positionieren von Objekten in der Szene](mr-learning-base-04.md) in der Tabelle angeordnet haben.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Komponente „Object Manipulator (Script)“ (Objektmanipulator (Skript)) zu allen Teilobjekten
2. Hinzufügen der Komponente NearInteractionGrabbable zu allen Teilobjekten
3. Konfigurieren der Komponente „Object Manipulator (Script)“ (Objektmanipulator (Skript))

> [!NOTE]
> Damit Sie **ein Objekt manipulieren** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Object Manipulator (Script)** -Komponente
>
> Damit Sie **ein Objekt manipulieren** und **mit nachverfolgten Händen greifen** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Object Manipulator (Script)** -Komponente
> * **NearInteractionGrabbable**-Komponente

Darüber hinaus werden Sie den Rover Explorer so konfigurieren, dass Sie die Rover-Teile auf dem Rover platzieren können, um ihn zu einer vollständigen Rover-Baugruppe zu machen.

Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **RoverParts**“ auf, und wählen Sie alle seine untergeordneten Rover-Teilobjekte sowie das **RoverAssembly**-Objekt aus. Verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die folgenden Komponenten hinzuzufügen:

* **Object Manipulator (Script)** -Komponente
* **NearInteractionGrabbable**-Komponente
* **Part Assembly Controller (Script)** -Komponente (Teilassembly-Controller (Skript))

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Um mehrere Objekte auszuwählen, die sich nicht nebeneinander befinden, drücken und halten Sie die STRG-Taste, während Sie die Maus verwenden, um ein beliebiges Objekt auszuwählen.

> [!NOTE]
> Im Rahmen dieses Tutorials wurden den Rover-Teilen bereits Collider hinzugefügt. Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.

> [!NOTE]
> Der Part Assembly-Controller (Script) ist nicht Teil des MRTK sondern ist in den Medienobjekten des Tutorials enthalten.

Konfigurieren Sie im Inspektorfenster, während alle Rover-Teilobjekte und das RoverAssembly-Objekt noch ausgewählt sind, die Komponente **Object Manipulator (Script)** (Objektmanipulator (Skript)) wie folgt:

* Deaktivieren Sie in der Dropdownliste **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) die Skalierung, sodass nur **Move** (Verschieben) und **Rotate** (Drehen) aktiviert sind

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> An diesem Punkt haben Sie die Objektmanipulation für alle Rover-Teilobjekte und das RoverAssembly-Objekt aktiviert.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** (Medienobjekte > MRTK > SDK > Standardmedienobjekte), um die Audioclips zu suchen:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

Wählen Sie im Hierarchiefenster erneut alle **Rover-Teilobjekte** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Audio Sources** (Audioquellen) hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Weisen Sie den Audioclip **MRTK_Scale_Start** dem Feld **AudioClip** zu
* Deaktivieren Sie das Kontrollkästchen **Play On Awake** (Nach Laden wiedergeben)
* Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

Klappen Sie im Hierarchiefenster das Objekt „RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints**“ auf, um alle Platzierungshinweisobjekte anzuzeigen, wählen Sie dann das erste Rover-Teil „RoverParts > **Camera_Part**“ aus, und konfigurieren Sie die Komponente **Part Assembly Controller (Script)** wie folgt:

* Weisen Sie das Objekt **Camera_PlacementHint** dem Feld **Location To Place** zu

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

**Wiederholen** Sie diesen Schritt für alle verbleibenden Rover-Teilobjekte und das RoverAssembly-Objekt, um die Komponente **Part Assembly Controller (Script)** wie folgt zu konfigurieren:

* Weisen Sie für das **Generator_Part** das **Generator_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für das **Lights_Part** das **Lights_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für das **UHFAntenna_Part** das **UHFAntenna_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für das **Spectrometer_Part** das **Spectrometer_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für die **RoverAssembly** das Objekt selbst, d. h. eben dieses **RoverAssembly**-Objekt, dem Feld **Location To Place** zu

Wählen Sie im Hierarchiefenster das Schaltflächenobjekt „RoverExplorer > Buttons > **Reset** (RoverExplorer > Schaltflächen > Zurücksetzen) aus, und konfigurieren Sie dann im Inspektorfenster das **OnClick ()** -Interaktionsereignis wie folgt:

* Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **PartAssemblyController** > **ResetPlacement ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

Wenn Sie jetzt in den Spielmodus wechseln, können Sie nahe oder ferne Interaktion verwenden, um die Rover-Teile auf dem Rover zu platzieren. Sobald sich das Teil nahe am entsprechenden Platzierungshinweis befindet, rastet es an der vorgesehenen Position ein und wird zu einem Teil des Rovers. Zum Zurücksetzen der Platzierungen können Sie auf die Schaltfläche „Zurücksetzen“ klicken:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

Weitere Informationen über die Objektmanipulator-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zum [Objektmanipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Hinzufügen von Begrenzungsrahmen

Begrenzungsrahmen machen das einhändige Manipulieren von Objekten sowohl für die Nah- als auch für die Ferninteraktion komfortabler und intuitiver, indem sie Ziehpunkte bereitstellen, die für die Änderung der Größe und zum Rotieren verwendet werden können.

In diesem Beispiel fügen Sie dem RoverExplorer-Objekt einen Begrenzungsrahmen hinzu, damit die gesamte Erfahrung komfortabel bewegt, gedreht und skaliert werden kann. Darüber hinaus werden Sie das Menü so konfigurieren, dass der Begrenzungsrahmen ein- und ausgeschaltet werden kann.

Wählen Sie im Hierarchiefenster das **RoverExplorer**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die folgenden Komponenten hinzuzufügen:

* **BoundingBox**-Komponente(Begrenzungsrahmen)
* **Object Manipulator (Script)** -Komponente

**Deaktivieren** Sie dann das Kontrollkästchen neben beiden Komponenten, um sie als standardmäßig **deaktiviert** festzulegen:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> Die Visualisierung von Begrenzungsrahmen wird zur Laufzeit erstellt und ist daher erst sichtbar, wenn Sie in den Spielmodus wechseln.

> [!NOTE]
> Die BoundingBox-Komponente fügt zur Laufzeit automatisch die NearInteractionGrabbable-Komponente hinzu. Daher brauchen wir diese Komponente nicht hinzuzufügen, um die eingeschlossenen Objekte mit nachverfolgten Händen zu greifen.

Klappen Sie im Hierarchiefenster das Objekt „Menu > **ButtonCollection**“ (Menü > Schaltflächensammlung) auf, um die vier Schaltflächen anzuzeigen, benennen Sie die dritte Schaltfläche in **BoundingBox_Enable** um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:

* Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) in **Enable** (Aktivieren)
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist
* Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist
* Belassen Sie das **Symbol** als Symbol „Cube mit Begrenzungsrahmen“

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

Benennen Sie die vierte und letzte Schaltfläche in **BoundingBox_Disable** um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:

* Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) in **Disable** (Deaktivieren)
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist
* Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist
* Ändern Sie das **Symbol** in das Symbol „Cube mit Begrenzungsrahmen“

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

Wenn Sie jetzt in den Spielmodus wechseln und den Begrenzungsrahmen aktivieren, indem Sie auf die Schaltfläche „Aktivieren“ klicken, können Sie nahe oder ferne Interaktion verwenden, um den Begrenzungsrahmen zu bewegen, drehen und skalieren, und die Schaltfläche „Deaktivieren“ verwenden, um den Begrenzungsrahmen wieder zu deaktivieren:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

Weitere Informationen über die Bounding Box-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zur [Bounding Box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie die nahe und ferne Manipulation für 3D-Objekte aktivieren und die zulässigen Manipulationsarten einschränken. Darüber hinaus haben Sie erfahren, wie Sie 3D-Objekte mit Begrenzungsrahmen umgeben, um die Steuerung der Objektmanipulation zu vereinfachen.

[Nächstes Tutorial: 8. Verwenden von Eye Tracking](mr-learning-base-08.md)
