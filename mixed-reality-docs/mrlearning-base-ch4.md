---
title: 'Tutorials zu den ersten Schritten: 5. Interagieren mit 3D-Objekten'
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130281"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="575ce-104">5. interagieren mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="575ce-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="575ce-105">In diesem Tutorial erfahren Sie mehr über grundlegende 3D-Inhalte und-Benutzeroberflächen, wie z. b. das Organisieren von 3D-Objekten als Teil einer Auflistung, das umschließende Kästchen für die grundlegende Bearbeitung, die Near-und die weite Interaktion und das Berühren von Handbewegungen und Hand Eingaben</span><span class="sxs-lookup"><span data-stu-id="575ce-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="575ce-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="575ce-106">Objectives</span></span>

* <span data-ttu-id="575ce-107">Erstellen Sie einen Bereich von 3D-Objekten, die für die anderen Lernziele verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="575ce-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="575ce-108">Implementieren von Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="575ce-108">Implement bounding boxes</span></span>
* <span data-ttu-id="575ce-109">Konfigurieren von 3D-Objekten für grundlegende Manipulationen, z. b. verschieben, drehen und Skalieren</span><span class="sxs-lookup"><span data-stu-id="575ce-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="575ce-110">Erkunden von nahen und fernen Interaktionen</span><span class="sxs-lookup"><span data-stu-id="575ce-110">Explore near and far interaction</span></span>
* <span data-ttu-id="575ce-111">Weitere Informationen zu weiteren Hand nach Verfolgungs Gesten, z. b. zum Erfassen und berühren</span><span class="sxs-lookup"><span data-stu-id="575ce-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="575ce-112">Importieren der tutorialassets</span><span class="sxs-lookup"><span data-stu-id="575ce-112">Importing the tutorial assets</span></span>

<span data-ttu-id="575ce-113">Herunterladen und Importieren des benutzerdefinierten Unity-Pakets:</span><span class="sxs-lookup"><span data-stu-id="575ce-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="575ce-114">Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.2.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="575ce-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

<span data-ttu-id="575ce-115">Nachdem Sie die tutorialassets importiert haben, sollte Ihr Projektfenster etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="575ce-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="575ce-117">Eine Erinnerung zum Importieren eines benutzerdefinierten Unity-Pakets finden Sie in den Anweisungen zum [Importieren von Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="575ce-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="575ce-118">Die Szenen Ansicht wird entcluttert.</span><span class="sxs-lookup"><span data-stu-id="575ce-118">Decluttering the scene view</span></span>

<span data-ttu-id="575ce-119">Um die Arbeit mit Ihrer Szene zu vereinfachen, legen Sie die **Sichtbarkeit der Szene** für die Cube-und buttoncollection-Objekte auf OFF fest, indem Sie auf das **Augen** Symbol links neben den Objekten klicken.</span><span class="sxs-lookup"><span data-stu-id="575ce-119">To make it easier to work with your scene, set the **scene visibility** for the Cube and ButtonCollection objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="575ce-120">Dadurch wird das Objekt im Szenen Fenster ausgeblendet, ohne die in-Game-Sichtbarkeit zu ändern:</span><span class="sxs-lookup"><span data-stu-id="575ce-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="575ce-122">Weitere Informationen zu den Steuerelementen für die Szenen Sichtbarkeit und deren Verwendung zur Optimierung Ihrer Szenen Ansicht und des Workflows finden Sie in der Dokumentation zur <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Szene Sichtbarkeit</a> von Unity.</span><span class="sxs-lookup"><span data-stu-id="575ce-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="575ce-123">Organisieren von 3D-Objekten in einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="575ce-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="575ce-124">In diesem Abschnitt erstellen Sie einen Bereich von 3D-Objekten, die Sie verwenden werden, wenn Sie in den folgenden Abschnitten dieses Tutorials verschiedene Möglichkeiten der Interaktion mit 3D-Objekten untersuchen.</span><span class="sxs-lookup"><span data-stu-id="575ce-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="575ce-125">Insbesondere konfigurieren Sie die 3D-Objekte, die auf einem 3 x 3-Raster positioniert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="575ce-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="575ce-126">Ähnlich wie bei der [Erstellung eines Bereichs von Schalt](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)Flächen werden folgende Hauptschritte ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="575ce-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="575ce-127">Übergeordnetes Element der 3D-Objekte zu einem übergeordneten Objekt</span><span class="sxs-lookup"><span data-stu-id="575ce-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="575ce-128">Hinzufügen und Konfigurieren der Komponente "Raster Objekt Auflistung (Skript)"</span><span class="sxs-lookup"><span data-stu-id="575ce-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="575ce-129">1. übergeordnetes Element der 3D-Objekte zu einem übergeordneten Objekt</span><span class="sxs-lookup"><span data-stu-id="575ce-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="575ce-130">Erstellen Sie im Hierarchie Fenster **ein leeres-Objekt**, geben Sie ihm einen passenden Namen, z **. b. 3dobjectcollection**, und positionieren Sie es an einem geeigneten Speicherort, z. b. X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="575ce-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="575ce-131">Navigieren Sie im Projektfenster zu **Assets** > **mrtk. Tutorials. GettingStarted** > **Prefabs** **und dann die** folgenden Prefabs der **3dobjectcollection**übergeordnet:</span><span class="sxs-lookup"><span data-stu-id="575ce-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **Parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="575ce-132">Käse</span><span class="sxs-lookup"><span data-stu-id="575ce-132">Cheese</span></span>
* <span data-ttu-id="575ce-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="575ce-133">CoffeeCup</span></span>
* <span data-ttu-id="575ce-134">Erdkern</span><span class="sxs-lookup"><span data-stu-id="575ce-134">EarthCore</span></span>
* <span data-ttu-id="575ce-135">Octacore</span><span class="sxs-lookup"><span data-stu-id="575ce-135">Octa</span></span>
* <span data-ttu-id="575ce-136">Platonic</span><span class="sxs-lookup"><span data-stu-id="575ce-136">Platonic</span></span>
* <span data-ttu-id="575ce-137">Das Modul</span><span class="sxs-lookup"><span data-stu-id="575ce-137">TheModule</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="575ce-139">Erstellen Sie im Fenster Hierarchie **drei Cubes** als untergeordnete Objekte der **3dobjectcollection** , und legen Sie Ihre Transformations **Skala** auf X = 0,15, Y = 0,15, Z = 0,15 fest:</span><span class="sxs-lookup"><span data-stu-id="575ce-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> <span data-ttu-id="575ce-141">Eine Erinnerung, wie Sie die oben aufgeführten Schritte ausführen, finden Sie im Tutorial Erstellen von [Benutzeroberflächen und Konfigurieren von Mixed Reality Toolkit](mrlearning-base-ch2.md) .</span><span class="sxs-lookup"><span data-stu-id="575ce-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="575ce-142">Positionieren Sie die Cubes neu, damit Sie jeden Cube sehen können:</span><span class="sxs-lookup"><span data-stu-id="575ce-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="575ce-144">Navigieren Sie im Projektfenster zu **Assets** > **mixedrealitytoolkit. SDK** > **standardassets** > **Material** , um die Materialien anzuzeigen, die mit dem mrtk bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="575ce-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="575ce-145">**Klicken und ziehen Sie** ein geeignetes Material auf die mesrenderer **Materials** Element 0-Eigenschaft jedes Cubes, z. b.:</span><span class="sxs-lookup"><span data-stu-id="575ce-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="575ce-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="575ce-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="575ce-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="575ce-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="575ce-148">MRTK_Standard_Green:</span><span class="sxs-lookup"><span data-stu-id="575ce-148">MRTK_Standard_Green:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="575ce-150">2. hinzufügen und Konfigurieren der Raster Objekt-Sammlungs Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="575ce-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="575ce-151">Fügen Sie dem 3dobjectcollection-Objekt eine Komponente für eine **Raster Objekt Auflistung (Skript)** hinzu, und konfigurieren Sie Sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="575ce-151">Add a **Grid Object Collection (Script)** component to the 3DObjectCollection object, and configure it as follows:</span></span>

* <span data-ttu-id="575ce-152">Ändern Sie den **Sortierungstyp** in die untergeordnete Reihenfolge, um sicherzustellen, dass die untergeordneten Objekte in der Reihenfolge sortiert werden, in der Sie</span><span class="sxs-lookup"><span data-stu-id="575ce-152">Change **Sort Type** to Child Order to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="575ce-153">Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren** , um die neue Konfiguration zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="575ce-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="575ce-155">Bearbeiten von 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="575ce-155">Manipulating 3D objects</span></span>

<span data-ttu-id="575ce-156">In diesem Abschnitt fügen Sie die Möglichkeit hinzu, alle 3D-Objekte in dem Bereich zu bearbeiten, den Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="575ce-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="575ce-157">Außerdem können Sie für die Prefab-Objekte es Benutzern ermöglichen, diese Objekte mit nach verfolgten Händen zu erreichen und zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="575ce-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="575ce-158">Anschließend werden Sie einige Manipulations Verhalten untersuchen, die Sie auf Ihre Objekte anwenden können.</span><span class="sxs-lookup"><span data-stu-id="575ce-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="575ce-159">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="575ce-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="575ce-160">Hinzufügen der Bearbeitungs Handler-Komponente (Skript) zu allen Objekten</span><span class="sxs-lookup"><span data-stu-id="575ce-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="575ce-161">Hinzufügen der fast-interaktionsgrabbable-Komponente (Skript) zu den Prefab-Objekten</span><span class="sxs-lookup"><span data-stu-id="575ce-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="575ce-162">Konfigurieren der Manipulations Handler-Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="575ce-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="575ce-163">Um **ein Objekt bearbeiten**zu können, muss das-Objekt über die folgenden Komponenten verfügen:</span><span class="sxs-lookup"><span data-stu-id="575ce-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="575ce-164">**Collider** -Komponente, z. b. ein Box-Collider</span><span class="sxs-lookup"><span data-stu-id="575ce-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="575ce-165">**Bearbeitungs Handler (Skript)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="575ce-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="575ce-166">**Damit ein Objekt mit nach verfolgten Händen**bearbeitet und gezogen werden kann, muss das-Objekt über die folgenden Komponenten verfügen:</span><span class="sxs-lookup"><span data-stu-id="575ce-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="575ce-167">**Collider** -Komponente, z. b. ein Box-Collider</span><span class="sxs-lookup"><span data-stu-id="575ce-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="575ce-168">**Bearbeitungs Handler (Skript)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="575ce-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="575ce-169">**Near-Interaktion (Skript-)** Komponente</span><span class="sxs-lookup"><span data-stu-id="575ce-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="575ce-170">1. Fügen Sie die Bearbeitungs Handlerkomponente (Skript) allen Objekten hinzu.</span><span class="sxs-lookup"><span data-stu-id="575ce-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="575ce-171">Wählen Sie im Fenster Hierarchie das **Käse** Objekt aus, halten Sie die **UMSCHALT** Taste gedrückt, und wählen Sie dann das Cube-Objekt **()** aus, und fügen Sie die **Bearbeitungs Handlerkomponente (Skript)** allen Objekten hinzu:</span><span class="sxs-lookup"><span data-stu-id="575ce-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube ()** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="575ce-173">Im Rahmen dieses Tutorials wurden den Prefabs bereits Colliders hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="575ce-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="575ce-174">Für Unity-primitive, z. b. die Cubeobjekte, wird die Collider-Komponente automatisch hinzugefügt, wenn das-Objekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="575ce-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="575ce-175">In der obigen Abbildung werden die Kollisionen durch die grünen Gliederungen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="575ce-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="575ce-176">Weitere Informationen zu Kollisionen finden Sie in der <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> -Dokumentation von Unity.</span><span class="sxs-lookup"><span data-stu-id="575ce-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="575ce-177">2. Hinzufügen der fast-interaktionsgrabbable-Komponente (Skript) zu den Prefab-Objekten</span><span class="sxs-lookup"><span data-stu-id="575ce-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="575ce-178">Wählen Sie im Fenster Hierarchie das **Käse** Objekt aus, halten Sie die **UMSCHALT** Taste gedrückt, und wählen Sie dann das Objekt "- **Modul** " aus, und fügen Sie die Komponente " **near Interaktion grabbable (Skript)** " zu allen Objekten hinzu:</span><span class="sxs-lookup"><span data-stu-id="575ce-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="575ce-180">3. Konfigurieren der Manipulations Handler-Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="575ce-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="575ce-181">Standard Manipulation</span><span class="sxs-lookup"><span data-stu-id="575ce-181">Default manipulation</span></span>

<span data-ttu-id="575ce-182">Belassen Sie für das **Cube** -Objekt standardmäßig alle Eigenschaften, damit das Standardverhalten der Manipulation angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="575ce-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="575ce-184">Wenn Sie eine Komponente auf die Standardwerte zurücksetzen möchten, können Sie das Einstellungssymbol der Komponente auswählen und auf Zurücksetzen klicken.</span><span class="sxs-lookup"><span data-stu-id="575ce-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="575ce-185">Beschränken der Bearbeitung auf die Skalierung</span><span class="sxs-lookup"><span data-stu-id="575ce-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="575ce-186">Ändern Sie für das Cube-Objekt **(1)** den **zwei handungstyp** für die Bearbeitung in "Scale", sodass der Benutzer nur die Größe des Objekts ändern kann:</span><span class="sxs-lookup"><span data-stu-id="575ce-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to Scale to only allow the user to change the object's size:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="575ce-188">Beschränken Sie die Bewegung auf einen eingeschränkten Abstand vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="575ce-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="575ce-189">Ändern Sie für das Cube-Objekt **(2)** die **Einschränkung bei der Bewegung** , um die Entfernung vom Kopf zu korrigieren, sodass beim Verschieben des Objekts der gleiche Abstand zum Benutzer besteht:</span><span class="sxs-lookup"><span data-stu-id="575ce-189">For the **Cube (2)** object, change **Constraint On Movement** to Fix Distance From Head so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="575ce-191">Standardmäßige abbrechbare Manipulation</span><span class="sxs-lookup"><span data-stu-id="575ce-191">Default grabbable manipulation</span></span>

<span data-ttu-id="575ce-192">Belassen Sie für die Objekte " **Käse**", " **coffecup**" und " **Erdkern** " standardmäßig alle Eigenschaften, um das Standardverhalten für die abrechenbare Manipulation zu erleben:</span><span class="sxs-lookup"><span data-stu-id="575ce-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="575ce-194">Entfernen der Funktion für eine lange Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="575ce-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="575ce-195">Deaktivieren Sie für das **Octa** -Objekt das Kontrollkästchen **lange Bearbeitung zulassen** , damit der Benutzer nur mit dem Objekt direkt über verfolgte Hände interagieren kann:</span><span class="sxs-lookup"><span data-stu-id="575ce-195">For the **Octa** object, uncheck the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="575ce-197">Drehen eines Objekts um seinen Mittelpunkt</span><span class="sxs-lookup"><span data-stu-id="575ce-197">Make an object rotate around its center</span></span>

<span data-ttu-id="575ce-198">Ändern Sie für das **platonische** Objekt den **1-Hand-Rotationsmodus in der Nähe** und den Modus für die manuelle **Drehung** , um das Objekt Center zu drehen, um dies zu ermöglichen, wenn der Benutzer das Objekt mit einer Hand dreht, dreht es sich um den Mittelpunkt des Objekts:</span><span class="sxs-lookup"><span data-stu-id="575ce-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to Rotate About Object Center to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a><span data-ttu-id="575ce-200">Bewegung nach Veröffentlichung des Objekts verhindern</span><span class="sxs-lookup"><span data-stu-id="575ce-200">Prevent movement after object is released</span></span>

<span data-ttu-id="575ce-201">Ändern Sie für das Objekt "- **Modul** " das **Freigabe Verhalten** in "Nothing", damit das Objekt nicht mehr verschoben wird, sobald es von der Hand des Benutzers freigegeben wird:</span><span class="sxs-lookup"><span data-stu-id="575ce-201">For the **TheModule** object, change **Release Behavior** to Nothing so that once the object is released from the user's hand, it doesn’t continue to move:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="575ce-203">Weitere Informationen zur handlerhandlerkomponente und den zugehörigen Eigenschaften finden Sie im Handbuch mit [Manipulations Handlern](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="575ce-203">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="575ce-204">Hinzufügen von Begrenzungs Feldern</span><span class="sxs-lookup"><span data-stu-id="575ce-204">Adding bounding boxes</span></span>

<span data-ttu-id="575ce-205">Begrenzungs Felder vereinfachen und intuitiver das Bearbeiten von Objekten mit einer Hand für die Near-und Far-Interaktion durch Bereitstellen von Handles, die für die Skalierung und Rotation verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="575ce-205">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="575ce-206">In diesem Beispiel fügen Sie dem erdcore-Objekt ein Begrenzungsfeld hinzu, damit dieses Objekt nun mit der Objekt Bearbeitung, die Sie im vorherigen Abschnitt konfiguriert haben, interagiert und mithilfe der umgebenden Feld Handles skaliert und gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="575ce-206">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="575ce-207">Um ein **Begrenzungsfeld**verwenden zu können, muss das-Objekt über die folgenden Komponenten verfügen:</span><span class="sxs-lookup"><span data-stu-id="575ce-207">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="575ce-208">**Collider** -Komponente, z. b. ein Box-Collider</span><span class="sxs-lookup"><span data-stu-id="575ce-208">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="575ce-209">**Begrenzungs Box-Komponente (Skript)**</span><span class="sxs-lookup"><span data-stu-id="575ce-209">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="575ce-210">1. Hinzufügen der umgebenden Box-Komponente (Skript) zum Erdkern Objekt</span><span class="sxs-lookup"><span data-stu-id="575ce-210">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="575ce-211">Wählen Sie im Inspektor-Fenster das **Erdkern** Objekt aus, und fügen Sie die Komponente für das umgebende **Feld (Skript)** dem Objekt "Erdkern" hinzu:</span><span class="sxs-lookup"><span data-stu-id="575ce-211">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="575ce-213">Die Visualisierungen des umgebenden Felds werden zur Laufzeit erstellt und daher nicht angezeigt, bevor Sie in den Spielmodus wechseln.</span><span class="sxs-lookup"><span data-stu-id="575ce-213">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="575ce-214">2. visualisieren und testen Sie das umgebende Feld mithilfe der in-Editor-Simulation.</span><span class="sxs-lookup"><span data-stu-id="575ce-214">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="575ce-215">Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben.</span><span class="sxs-lookup"><span data-stu-id="575ce-215">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="575ce-216">Halten Sie die Leertaste gedrückt, um die Hand zu bringen, und verwenden Sie die Maus, um mit dem umgebenden Feld zu interagieren:</span><span class="sxs-lookup"><span data-stu-id="575ce-216">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="575ce-218">Weitere Informationen zur Begrenzungsfeld Komponente und den zugehörigen Eigenschaften finden Sie im Leitfaden für [Begrenzungs](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) Felder im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="575ce-218">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="575ce-219">Hinzufügen von Berührungs Effekten</span><span class="sxs-lookup"><span data-stu-id="575ce-219">Adding touch effects</span></span>

<span data-ttu-id="575ce-220">In diesem Beispiel werden Ereignisse aktiviert, die ausgelöst werden, wenn Sie ein Objekt mit der Hand berühren.</span><span class="sxs-lookup"><span data-stu-id="575ce-220">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="575ce-221">Insbesondere konfigurieren Sie das Octa-Objekt so, dass es einen Soundeffekt spielt, wenn der Benutzer es berührt.</span><span class="sxs-lookup"><span data-stu-id="575ce-221">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="575ce-222">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="575ce-222">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="575ce-223">Fügen Sie dem-Objekt eine audioquellkomponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="575ce-223">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="575ce-224">Fügen Sie dem-Objekt die touchable-Komponente der Near-Interaktion (Skript) hinzu.</span><span class="sxs-lookup"><span data-stu-id="575ce-224">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="575ce-225">Fügen Sie die Komponente "Hand Interaktion (Skript)" zum Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="575ce-225">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="575ce-226">Implementieren des Ereignisses on Touchscreen Started</span><span class="sxs-lookup"><span data-stu-id="575ce-226">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="575ce-227">Testen der Berührungs Interaktion mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="575ce-227">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="575ce-228">Damit **Berührungs Ereignisse auslöst**werden können, muss das-Objekt über die folgenden Komponenten verfügen:</span><span class="sxs-lookup"><span data-stu-id="575ce-228">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="575ce-229">**Collider** -Komponente, vorzugsweise ein Box-Collider</span><span class="sxs-lookup"><span data-stu-id="575ce-229">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="575ce-230">**Touchable-Komponente der Near-Interaktion (Skript)**</span><span class="sxs-lookup"><span data-stu-id="575ce-230">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="575ce-231">**Hand Interaktion (Skript)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="575ce-231">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="575ce-232">Die Komponente "Hand Interaktion (Skript)" ist nicht Bestandteil von mrtk.</span><span class="sxs-lookup"><span data-stu-id="575ce-232">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="575ce-233">Es wurde mit den Assets dieses Lernprogramms importiert und ursprünglich Teil des mixedreality Toolkit Unity-Beispielen.</span><span class="sxs-lookup"><span data-stu-id="575ce-233">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="575ce-234">1. Fügen Sie dem Objekt eine audioquellkomponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="575ce-234">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="575ce-235">Wählen Sie im Fenster Hierarchie das **Octa** -Objekt aus, fügen Sie dem Octa-Objekt eine **audioquellkomponente** hinzu, und ändern Sie dann **räumliche Blend** in 1, um räumliche Audiodaten zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="575ce-235">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="575ce-237">2. Hinzufügen der Near-interaktionstouchable-Komponente (Skript) zum Objekt</span><span class="sxs-lookup"><span data-stu-id="575ce-237">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="575ce-238">Wenn das **Octa** -Objekt noch ausgewählt ist, fügen Sie dem Octa-Objekt die touchable-Komponente der **near-Interaktion (Script)** hinzu, und klicken Sie dann auf die Schaltflächen **fixbegrenzungen** und **Fix Center** , um die Eigenschaften des lokalen Centers und der Begrenzungen der Near-interaktionstouchable (Script) zu aktualisieren</span><span class="sxs-lookup"><span data-stu-id="575ce-238">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="575ce-240">3. Fügen Sie dem Objekt die Komponente "Hand Interaktion (Skript)" hinzu.</span><span class="sxs-lookup"><span data-stu-id="575ce-240">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="575ce-241">Wenn das **Octa** -Objekt noch ausgewählt ist, fügen Sie dem Octa-Objekt die Komponente " **Hand Interaktion (Skript)** " hinzu:</span><span class="sxs-lookup"><span data-stu-id="575ce-241">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="575ce-243">4. implementieren Sie das Ereignis "on Touchscreen Started".</span><span class="sxs-lookup"><span data-stu-id="575ce-243">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="575ce-244">Klicken Sie in der Komponente Hand Interaktion (Skript) auf das kleine **+** Symbol, um ein neues **on Touchscreen-Ereignis ()** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="575ce-244">On the Hand Interaction Touch (Script) component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="575ce-245">Konfigurieren Sie dann das **Octa** -Objekt so, dass es das Ereignis empfängt, und definieren Sie **audiosource. playoneshot** als Aktion, die ausgelöst werden soll:</span><span class="sxs-lookup"><span data-stu-id="575ce-245">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="575ce-247">Navigieren Sie zu **Assets** > **mixedrealitytoolkit. SDK** > **standardassets** > Material, um Audioclips anzuzeigen, die mit dem mrtk bereitgestellt werden, und weisen Sie dann dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. den MRTK_Gem Audioclip:</span><span class="sxs-lookup"><span data-stu-id="575ce-247">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="575ce-249">Eine Erinnerung, wie Ereignisse implementiert werden können, finden Sie in den Anweisungen [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="575ce-249">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="575ce-250">5. Testen der Berührungs Interaktion mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="575ce-250">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="575ce-251">Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben.</span><span class="sxs-lookup"><span data-stu-id="575ce-251">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="575ce-252">Halten Sie die Leertaste gedrückt, um die Hand zu bringen, und verwenden Sie die Maus, um das Octa-Objekt zu berühren und den Soundeffekt zu initiieren:</span><span class="sxs-lookup"><span data-stu-id="575ce-252">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="575ce-254">Wie Sie gesehen haben, als Sie die Berührungs Interaktion getestet haben, und wie in der obigen Abbildung gezeigt, wurde die Octa-Objekt Farbe während der Arbeit gepultet.</span><span class="sxs-lookup"><span data-stu-id="575ce-254">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="575ce-255">Dieser Effekt ist in der Komponente "Hand Interaktion berühren (Skript)" hart codiert und ist nicht das Ergebnis der Ereignis Konfiguration, die Sie in den obigen Schritten abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="575ce-255">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="575ce-256">Wenn Sie diesen Effekt deaktivieren möchten, können Sie z. b. "targetrenderer = getcomponentinchildren<Renderer>();" auskommentieren oder Zeile 32, was dazu führt, dass der targetrenderer NULL bleibt und die Farbe nicht pullt wird.</span><span class="sxs-lookup"><span data-stu-id="575ce-256">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="575ce-257">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="575ce-257">Congratulations</span></span>

<span data-ttu-id="575ce-258">In diesem Tutorial haben Sie erfahren, wie Sie 3D-Objekte in einer Raster Auflistung organisieren und wie Sie diese Objekte (Skalieren, drehen und verschieben) mithilfe der Near-Interaktion (direkt mit nach verfolgten Händen) und der äußersten Interaktion (mit Blick-und Handzeichen) bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="575ce-258">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="575ce-259">Sie haben auch gelernt, wie sie umgebende Felder um 3D-Objekte platzieren und wie Sie die Handles in den Begrenzungs Feldern verwenden und anpassen können.</span><span class="sxs-lookup"><span data-stu-id="575ce-259">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="575ce-260">Schließlich haben Sie erfahren, wie Sie beim Berühren eines Objekts Ereignisse auslösen können.</span><span class="sxs-lookup"><span data-stu-id="575ce-260">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="575ce-261">Nächste Lektion: 6. untersuchen der erweiterten Eingabeoptionen</span><span class="sxs-lookup"><span data-stu-id="575ce-261">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
