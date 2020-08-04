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
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="0e41b-105">7. Interagieren mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="0e41b-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="0e41b-106">In diesem Tutorial erfahren Sie, wie Sie die nahe und ferne Manipulation von 3D-Objekten aktivieren und die zulässigen Manipulationsarten einschränken.</span><span class="sxs-lookup"><span data-stu-id="0e41b-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="0e41b-107">Darüber hinaus erfahren Sie, wie Sie 3D-Objekte mit Begrenzungsrahmen umgeben, um die Steuerung der Objektmanipulation zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0e41b-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="0e41b-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="0e41b-108">Objectives</span></span>

* <span data-ttu-id="0e41b-109">Erfahren, wie 3D-Objekte so konfiguriert werden, dass Interaktion mit ihnen möglich ist</span><span class="sxs-lookup"><span data-stu-id="0e41b-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="0e41b-110">Erfahren, wie 3D-Objekte mit Begrenzungsrahmen versehen werden</span><span class="sxs-lookup"><span data-stu-id="0e41b-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="0e41b-111">Manipulieren von 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="0e41b-111">Manipulating 3D objects</span></span>

<span data-ttu-id="0e41b-112">In diesem Abschnitt fügen Sie die Funktion zum Manipulieren aller Teile des Rovers hinzu, die Sie im Rahmen des Tutorials [Positionieren von Objekten in der Szene](mr-learning-base-04.md) in der Tabelle angeordnet haben.</span><span class="sxs-lookup"><span data-stu-id="0e41b-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="0e41b-113">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="0e41b-114">Hinzufügen der Komponente „Object Manipulator (Script)“ (Objektmanipulator (Skript)) zu allen Teilobjekten</span><span class="sxs-lookup"><span data-stu-id="0e41b-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="0e41b-115">Hinzufügen der Komponente NearInteractionGrabbable zu allen Teilobjekten</span><span class="sxs-lookup"><span data-stu-id="0e41b-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="0e41b-116">Konfigurieren der Komponente „Object Manipulator (Script)“ (Objektmanipulator (Skript))</span><span class="sxs-lookup"><span data-stu-id="0e41b-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="0e41b-117">Damit Sie **ein Objekt manipulieren** können, muss das Objekt die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="0e41b-118">**Collider**-Komponente, z. B. ein Feld-Collider</span><span class="sxs-lookup"><span data-stu-id="0e41b-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="0e41b-119">**Object Manipulator (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="0e41b-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="0e41b-120">Damit Sie **ein Objekt manipulieren** und **mit nachverfolgten Händen greifen** können, muss das Objekt die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="0e41b-121">**Collider**-Komponente, z. B. ein Feld-Collider</span><span class="sxs-lookup"><span data-stu-id="0e41b-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="0e41b-122">**Object Manipulator (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="0e41b-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="0e41b-123">**NearInteractionGrabbable**-Komponente</span><span class="sxs-lookup"><span data-stu-id="0e41b-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="0e41b-124">Darüber hinaus werden Sie den Rover Explorer so konfigurieren, dass Sie die Rover-Teile auf dem Rover platzieren können, um ihn zu einer vollständigen Rover-Baugruppe zu machen.</span><span class="sxs-lookup"><span data-stu-id="0e41b-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="0e41b-125">Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **RoverParts**“ auf, und wählen Sie alle seine untergeordneten Rover-Teilobjekte sowie das **RoverAssembly**-Objekt aus. Verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die folgenden Komponenten hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="0e41b-126">**Object Manipulator (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="0e41b-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="0e41b-127">**NearInteractionGrabbable**-Komponente</span><span class="sxs-lookup"><span data-stu-id="0e41b-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="0e41b-128">**Part Assembly Controller (Script)** -Komponente (Teilassembly-Controller (Skript))</span><span class="sxs-lookup"><span data-stu-id="0e41b-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="0e41b-130">Um mehrere Objekte auszuwählen, die sich nicht nebeneinander befinden, drücken und halten Sie die STRG-Taste, während Sie die Maus verwenden, um ein beliebiges Objekt auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="0e41b-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="0e41b-131">Im Rahmen dieses Tutorials wurden den Rover-Teilen bereits Collider hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0e41b-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="0e41b-132">Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.</span><span class="sxs-lookup"><span data-stu-id="0e41b-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="0e41b-133">Der Part Assembly-Controller (Script) ist nicht Teil des MRTK sondern ist in den Medienobjekten des Tutorials enthalten.</span><span class="sxs-lookup"><span data-stu-id="0e41b-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="0e41b-134">Konfigurieren Sie im Inspektorfenster, während alle Rover-Teilobjekte und das RoverAssembly-Objekt noch ausgewählt sind, die Komponente **Object Manipulator (Script)** (Objektmanipulator (Skript)) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0e41b-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="0e41b-135">Deaktivieren Sie in der Dropdownliste **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) die Skalierung, sodass nur **Move** (Verschieben) und **Rotate** (Drehen) aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="0e41b-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="0e41b-137">An diesem Punkt haben Sie die Objektmanipulation für alle Rover-Teilobjekte und das RoverAssembly-Objekt aktiviert.</span><span class="sxs-lookup"><span data-stu-id="0e41b-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="0e41b-138">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** (Medienobjekte > MRTK > SDK > Standardmedienobjekte), um die Audioclips zu suchen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="0e41b-140">Wählen Sie im Hierarchiefenster erneut alle **Rover-Teilobjekte** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Audio Sources** (Audioquellen) hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0e41b-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="0e41b-141">Weisen Sie den Audioclip **MRTK_Scale_Start** dem Feld **AudioClip** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="0e41b-142">Deaktivieren Sie das Kontrollkästchen **Play On Awake** (Nach Laden wiedergeben)</span><span class="sxs-lookup"><span data-stu-id="0e41b-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="0e41b-143">Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1</span><span class="sxs-lookup"><span data-stu-id="0e41b-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="0e41b-145">Klappen Sie im Hierarchiefenster das Objekt „RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints**“ auf, um alle Platzierungshinweisobjekte anzuzeigen, wählen Sie dann das erste Rover-Teil „RoverParts > **Camera_Part**“ aus, und konfigurieren Sie die Komponente **Part Assembly Controller (Script)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0e41b-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="0e41b-146">Weisen Sie das Objekt **Camera_PlacementHint** dem Feld **Location To Place** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="0e41b-148">**Wiederholen** Sie diesen Schritt für alle verbleibenden Rover-Teilobjekte und das RoverAssembly-Objekt, um die Komponente **Part Assembly Controller (Script)** wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="0e41b-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="0e41b-149">Weisen Sie für das **Generator_Part** das **Generator_PlacementHint**-Objekt dem Feld **Location To Place** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="0e41b-150">Weisen Sie für das **Lights_Part** das **Lights_PlacementHint**-Objekt dem Feld **Location To Place** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="0e41b-151">Weisen Sie für das **UHFAntenna_Part** das **UHFAntenna_PlacementHint**-Objekt dem Feld **Location To Place** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="0e41b-152">Weisen Sie für das **Spectrometer_Part** das **Spectrometer_PlacementHint**-Objekt dem Feld **Location To Place** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="0e41b-153">Weisen Sie für die **RoverAssembly** das Objekt selbst, d. h. eben dieses **RoverAssembly**-Objekt, dem Feld **Location To Place** zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="0e41b-154">Wählen Sie im Hierarchiefenster das Schaltflächenobjekt „RoverExplorer > Buttons > **Reset** (RoverExplorer > Schaltflächen > Zurücksetzen) aus, und konfigurieren Sie dann im Inspektorfenster das **OnClick ()** -Interaktionsereignis wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0e41b-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="0e41b-155">Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e41b-156">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **PartAssemblyController** > **ResetPlacement ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="0e41b-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="0e41b-158">Wenn Sie jetzt in den Spielmodus wechseln, können Sie nahe oder ferne Interaktion verwenden, um die Rover-Teile auf dem Rover zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="0e41b-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="0e41b-159">Sobald sich das Teil nahe am entsprechenden Platzierungshinweis befindet, rastet es an der vorgesehenen Position ein und wird zu einem Teil des Rovers.</span><span class="sxs-lookup"><span data-stu-id="0e41b-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="0e41b-160">Zum Zurücksetzen der Platzierungen können Sie auf die Schaltfläche „Zurücksetzen“ klicken:</span><span class="sxs-lookup"><span data-stu-id="0e41b-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="0e41b-162">Weitere Informationen über die Objektmanipulator-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zum [Objektmanipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0e41b-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="0e41b-163">Hinzufügen von Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="0e41b-163">Adding bounding boxes</span></span>

<span data-ttu-id="0e41b-164">Begrenzungsrahmen machen das einhändige Manipulieren von Objekten sowohl für die Nah- als auch für die Ferninteraktion komfortabler und intuitiver, indem sie Ziehpunkte bereitstellen, die für die Änderung der Größe und zum Rotieren verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="0e41b-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="0e41b-165">In diesem Beispiel fügen Sie dem RoverExplorer-Objekt einen Begrenzungsrahmen hinzu, damit die gesamte Erfahrung komfortabel bewegt, gedreht und skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0e41b-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="0e41b-166">Darüber hinaus werden Sie das Menü so konfigurieren, dass der Begrenzungsrahmen ein- und ausgeschaltet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0e41b-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="0e41b-167">Wählen Sie im Hierarchiefenster das **RoverExplorer**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die folgenden Komponenten hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="0e41b-168">**BoundingBox**-Komponente(Begrenzungsrahmen)</span><span class="sxs-lookup"><span data-stu-id="0e41b-168">**BoundingBox** component</span></span>
* <span data-ttu-id="0e41b-169">**Object Manipulator (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="0e41b-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="0e41b-170">**Deaktivieren** Sie dann das Kontrollkästchen neben beiden Komponenten, um sie als standardmäßig **deaktiviert** festzulegen:</span><span class="sxs-lookup"><span data-stu-id="0e41b-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="0e41b-172">Die Visualisierung von Begrenzungsrahmen wird zur Laufzeit erstellt und ist daher erst sichtbar, wenn Sie in den Spielmodus wechseln.</span><span class="sxs-lookup"><span data-stu-id="0e41b-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="0e41b-173">Die BoundingBox-Komponente fügt zur Laufzeit automatisch die NearInteractionGrabbable-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="0e41b-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="0e41b-174">Daher brauchen wir diese Komponente nicht hinzuzufügen, um die eingeschlossenen Objekte mit nachverfolgten Händen zu greifen.</span><span class="sxs-lookup"><span data-stu-id="0e41b-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="0e41b-175">Klappen Sie im Hierarchiefenster das Objekt „Menu > **ButtonCollection**“ (Menü > Schaltflächensammlung) auf, um die vier Schaltflächen anzuzeigen, benennen Sie die dritte Schaltfläche in **BoundingBox_Enable** um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0e41b-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="0e41b-176">Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) in **Enable** (Aktivieren)</span><span class="sxs-lookup"><span data-stu-id="0e41b-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="0e41b-177">Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e41b-178">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="0e41b-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e41b-179">Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="0e41b-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="0e41b-180">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="0e41b-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="0e41b-181">Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e41b-182">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="0e41b-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e41b-183">Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="0e41b-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="0e41b-184">Belassen Sie das **Symbol** als Symbol „Cube mit Begrenzungsrahmen“</span><span class="sxs-lookup"><span data-stu-id="0e41b-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="0e41b-186">Benennen Sie die vierte und letzte Schaltfläche in **BoundingBox_Disable** um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0e41b-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="0e41b-187">Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) in **Disable** (Deaktivieren)</span><span class="sxs-lookup"><span data-stu-id="0e41b-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="0e41b-188">Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e41b-189">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="0e41b-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e41b-190">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="0e41b-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="0e41b-191">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="0e41b-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="0e41b-192">Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="0e41b-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e41b-193">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="0e41b-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e41b-194">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="0e41b-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="0e41b-195">Ändern Sie das **Symbol** in das Symbol „Cube mit Begrenzungsrahmen“</span><span class="sxs-lookup"><span data-stu-id="0e41b-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="0e41b-197">Wenn Sie jetzt in den Spielmodus wechseln und den Begrenzungsrahmen aktivieren, indem Sie auf die Schaltfläche „Aktivieren“ klicken, können Sie nahe oder ferne Interaktion verwenden, um den Begrenzungsrahmen zu bewegen, drehen und skalieren, und die Schaltfläche „Deaktivieren“ verwenden, um den Begrenzungsrahmen wieder zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="0e41b-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="0e41b-199">Weitere Informationen über die Bounding Box-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zur [Bounding Box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0e41b-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="0e41b-200">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="0e41b-200">Congratulations</span></span>

<span data-ttu-id="0e41b-201">In diesem Tutorial haben Sie erfahren, wie Sie die nahe und ferne Manipulation für 3D-Objekte aktivieren und die zulässigen Manipulationsarten einschränken.</span><span class="sxs-lookup"><span data-stu-id="0e41b-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="0e41b-202">Darüber hinaus haben Sie erfahren, wie Sie 3D-Objekte mit Begrenzungsrahmen umgeben, um die Steuerung der Objektmanipulation zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0e41b-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="0e41b-203">Nächstes Tutorial: 8. Verwenden von Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="0e41b-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
