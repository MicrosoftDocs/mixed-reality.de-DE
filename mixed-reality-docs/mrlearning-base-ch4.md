---
title: 'Tutorials zu den ersten Schritten: 5 Interagieren mit 3D-Objekten'
description: Erfahren Sie mehr über einfache 3D-Inhalte und-Benutzeroberflächen, z. B. das Organisieren von 3D-Objekten und Begrenzungsrahmen für einfache Bearbeitung.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 419b381c1240b2cc10708eab03245ed3aabfa859
ms.sourcegitcommit: 61291e83536c8cb2e8401a8e66060128ede35922
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416141"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="f2f72-105">5. Interagieren mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="f2f72-106">In diesem Tutorial erfahren Sie mehr über einfache 3D-Inhalte und Benutzeroberflächen, etwa das Organisieren von 3D-Objekten als Teil einer Sammlung, Begrenzungsrahmen für einfache Manipulation, Nah- und Ferninteraktion sowie Berührungs- und Greifgesten mit Hand-Tracking.</span><span class="sxs-lookup"><span data-stu-id="f2f72-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2f72-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="f2f72-107">Objectives</span></span>

* <span data-ttu-id="f2f72-108">Erstellen eines Bereichs von 3D-Objekten, die für die anderen Lernziele verwendet werden</span><span class="sxs-lookup"><span data-stu-id="f2f72-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="f2f72-109">Implementieren von Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="f2f72-109">Implement bounding boxes</span></span>
* <span data-ttu-id="f2f72-110">Konfigurieren von 3D-Objekten für grundlegende Manipulationen, wie etwa Bewegen, Drehen und Skalieren</span><span class="sxs-lookup"><span data-stu-id="f2f72-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="f2f72-111">Erkunden von nahen und fernen Interaktionen</span><span class="sxs-lookup"><span data-stu-id="f2f72-111">Explore near and far interaction</span></span>
* <span data-ttu-id="f2f72-112">Vermittlung von Informationen zu zusätzlichen Hand-Tracking-Gesten wie „Greifen“ und „Berühren“</span><span class="sxs-lookup"><span data-stu-id="f2f72-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f2f72-113">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="f2f72-113">Importing the tutorial assets</span></span>

<span data-ttu-id="f2f72-114">Laden Sie das benutzerdefinierte Unity-Paket herunter, und importieren Sie es:</span><span class="sxs-lookup"><span data-stu-id="f2f72-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="f2f72-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f2f72-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="f2f72-116">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="f2f72-118">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="f2f72-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="f2f72-119">Aufräumen der Szenenansicht</span><span class="sxs-lookup"><span data-stu-id="f2f72-119">Decluttering the scene view</span></span>

<span data-ttu-id="f2f72-120">Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die **scene visibility** (Sichtbarkeit in der Szene) für die Objekte **Cube** (Würfel) und **ButtonCollection** auf „Aus“ fest, indem Sie links neben den Objekten auf das **Augensymbol** klicken.</span><span class="sxs-lookup"><span data-stu-id="f2f72-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="f2f72-121">Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern:</span><span class="sxs-lookup"><span data-stu-id="f2f72-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="f2f72-123">Mehr zu den Steuerelementen für die Sichtbarkeit in der Szene und ihre Verwendung zum Optimieren Ihrer Szenenansicht und Ihres Workflows finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene).</span><span class="sxs-lookup"><span data-stu-id="f2f72-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="f2f72-124">Organisieren von 3D-Objekten in einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="f2f72-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="f2f72-125">In diesem Abschnitt erstellen Sie einen Bereich aus 3D-Objekten, die Sie beim Erforschen verschiedener Verfahren zur Interaktion mit 3D-Objekten in den folgenden Abschnitten dieses Tutorials verwenden.</span><span class="sxs-lookup"><span data-stu-id="f2f72-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="f2f72-126">Insbesondere konfigurieren Sie die 3D-Objekte, die in einem 3x3-Raster angeordnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f2f72-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="f2f72-127">Ähnlich wie beim [Erstellen eines Bereichs mit Schaltflächen](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection) sind dies die wichtigsten Schritte, die Sie dazu ausführen müssen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f2f72-128">Unterordnen der 3D-Objekte unter einem übergeordneten Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="f2f72-129">Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“</span><span class="sxs-lookup"><span data-stu-id="f2f72-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="f2f72-130">1. Unterordnen der 3D-Objekte unter einem übergeordneten Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="f2f72-131">Sie müssen im Hierarchiefenster **ein leeres Objekt erstellen**, ihm einen passenden Namen geben, beispielsweise **3DObjectCollection** und es an einer geeigneten Stelle positionieren, z. B. X = 0, Y = -0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="f2f72-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="f2f72-132">Navigieren Sie im Projektfenster zu **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Ressourcen > MRTK.Tutorials.GettingStarted > Prefabs), und **unterordnen** Sie die folgenden Prefabs unter die **3DObjectCollection**:</span><span class="sxs-lookup"><span data-stu-id="f2f72-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="f2f72-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="f2f72-133">Cheese</span></span>
* <span data-ttu-id="f2f72-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="f2f72-134">CoffeeCup</span></span>
* <span data-ttu-id="f2f72-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="f2f72-135">EarthCore</span></span>
* <span data-ttu-id="f2f72-136">Octa</span><span class="sxs-lookup"><span data-stu-id="f2f72-136">Octa</span></span>
* <span data-ttu-id="f2f72-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="f2f72-137">Platonic</span></span>
* <span data-ttu-id="f2f72-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="f2f72-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="f2f72-140">Sie müssen im Hierarchiefenster **drei Würfel erstellen**, als untergeordnete Objekte der **3DObjectCollection**, deren **Transformationsmaßstab** Sie auf X = 0,15, Y = 0,15 und Z = 0,15 festlegen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="f2f72-142">Falls Sie zur Ausführung der oben aufgeführten Schritte eine Auffrischung benötigen, lesen Sie das Tutorial [Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md).</span><span class="sxs-lookup"><span data-stu-id="f2f72-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="f2f72-143">Ordnen Sie die Würfel neu an, sodass Sie jeden Würfel sehen können:</span><span class="sxs-lookup"><span data-stu-id="f2f72-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="f2f72-145">Navigieren Sie im Projektfenster zu **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** (Ressourcen > MixedRealityToolkit.SDK > StandardAssets > Materialien), um die mit dem MRTK zur Verfügung gestellten Materialien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f2f72-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="f2f72-146">Bewegen Sie mithilfe von **Klicken und Ziehen** ein geeignetes Material auf die **Materials** Element 0-Eigenschaft des Gittermodell-Renderers jedes Würfels, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="f2f72-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="f2f72-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="f2f72-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="f2f72-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="f2f72-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="f2f72-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="f2f72-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="f2f72-151">2. Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“</span><span class="sxs-lookup"><span data-stu-id="f2f72-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="f2f72-152">Fügen Sie eine **Grid Object Collection (Script)** -Komponente (Rasterobjektsammlung (Skript)) zum **3DObjectCollection**-Objekt hinzu, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f2f72-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="f2f72-153">Ändern Sie den **Sort Type** (Sortierungstyp) in **Child Order** (Reihenfolge untergeordneter Elemente), um sicherzustellen, dass die untergeordneten Objekte in der Reihenfolge sortiert werden, in der Sie sie unter dem übergeordneten Objekt platziert haben</span><span class="sxs-lookup"><span data-stu-id="f2f72-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="f2f72-154">Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren**, um die neue Konfiguration zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="f2f72-156">Manipulieren von 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-156">Manipulating 3D objects</span></span>

<span data-ttu-id="f2f72-157">In diesem Abschnitt fügen Sie die Funktion zum Manipulieren aller 3D-Objekte in dem Bereich hinzu, den Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f2f72-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="f2f72-158">Darüber hinaus geben Sie den Benutzern für die Prefab-Objekte die Möglichkeit, nach diesen Objekten mit nachverfolgten Händen zu greifen und sie zu fassen.</span><span class="sxs-lookup"><span data-stu-id="f2f72-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="f2f72-159">Anschließend untersuchen Sie einige der Manipulationsverhaltensweisen, die Sie auf Ihre Objekte anwenden können.</span><span class="sxs-lookup"><span data-stu-id="f2f72-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="f2f72-160">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f2f72-161">Hinzufügen der Manipulation Handler (Script)-Komponente zu allen Objekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="f2f72-162">Hinzufügen der Near Interaction Grabbable (Script)-Komponente (Nah-Interaktion, berührbar (Skript)) zu den Prefab-Objekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="f2f72-163">Konfigurieren der Manipulation Handler (Script)-Komponente</span><span class="sxs-lookup"><span data-stu-id="f2f72-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2f72-164">Damit Sie **ein Objekt manipulieren** können, muss das Objekt die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="f2f72-165">**Collider**-Komponente, z. B. ein Feld-Collider</span><span class="sxs-lookup"><span data-stu-id="f2f72-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="f2f72-166">**Manipulation Handler (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="f2f72-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="f2f72-167">Damit Sie **ein Objekt manipulieren** und **mit nachverfolgten Händen greifen** können, muss das Objekt die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="f2f72-168">**Collider**-Komponente, z. B. ein Feld-Collider</span><span class="sxs-lookup"><span data-stu-id="f2f72-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="f2f72-169">**Manipulation Handler (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="f2f72-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="f2f72-170">**Near Interaction Grabbable (Script)** -Komponente (Nah-Interaktion, greifbar (Skript))</span><span class="sxs-lookup"><span data-stu-id="f2f72-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="f2f72-171">1. Hinzufügen der Manipulation Handler (Script)-Komponente zu allen Objekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="f2f72-172">Wählen Sie im Hierarchiefenster das Objekt **Cheese** (Käse) aus, halten Sie die **UMSCHALTTASTE** gedrückt, wählen Sie dann das **Cube () 2**-Objekt aus, und fügen Sie die **Manipulation Handler (Script)** -Komponente allen Objekten hinzu:</span><span class="sxs-lookup"><span data-stu-id="f2f72-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f2f72-174">Im Rahmen dieses Tutorials wurden den Prefabs bereits Collider hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f2f72-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="f2f72-175">Für Unity-Primitive, wie etwa die Cube-Objekte, wird die Collider-Komponente beim Erstellen des Objekts automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f2f72-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="f2f72-176">In der Abbildung oben sind die Collider durch grüne Umrisslinien dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f2f72-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="f2f72-177">Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.</span><span class="sxs-lookup"><span data-stu-id="f2f72-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="f2f72-178">2. Hinzufügen der Near Interaction Grabbable (Script)-Komponente (Nah-Interaktion, berührbar (Skript)) zu den Prefab-Objekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="f2f72-179">Wählen Sie im Hierarchiefenster das Objekt **Cheese** (Käse) aus, halten Sie die **UMSCHALTTASTE** gedrückt, wählen Sie dann das **TheModule**-Objekt aus, und fügen Sie die **Near Interaction Grabbable (Script)** -Komponente (Nah-Interaktion, greifbar (Skript)) allen Objekten hinzu:</span><span class="sxs-lookup"><span data-stu-id="f2f72-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="f2f72-181">3. Konfigurieren der Manipulation Handler (Script)-Komponente</span><span class="sxs-lookup"><span data-stu-id="f2f72-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="f2f72-182">Standardmanipulation</span><span class="sxs-lookup"><span data-stu-id="f2f72-182">Default manipulation</span></span>

<span data-ttu-id="f2f72-183">Belassen Sie für das **Cube**-Objekt alle Eigenschaften auf den Standardwerten, um das Standardmanipulationsverhalten zu erleben:</span><span class="sxs-lookup"><span data-stu-id="f2f72-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="f2f72-185">Um eine Komponente auf ihre Standardwerte zurückzusetzen, können Sie das Symbol „Einstellungen“ der Komponente auswählen und auf „Zurücksetzen“ klicken.</span><span class="sxs-lookup"><span data-stu-id="f2f72-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="f2f72-186">Einschränken der Manipulation nur auf die Größe</span><span class="sxs-lookup"><span data-stu-id="f2f72-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="f2f72-187">Ändern Sie für das **Cube (1)** -Objekt den **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) auf **Scale** (Maßstab), um dem Benutzer nur die Änderung der Objektgröße zu erlauben:</span><span class="sxs-lookup"><span data-stu-id="f2f72-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="f2f72-189">Einschränken der Bewegung auf einen festen Abstand vom Benutzer</span><span class="sxs-lookup"><span data-stu-id="f2f72-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="f2f72-190">Ändern Sie für das **Cube (2)** -Objekt **Constraint On Movement** (Bewegungseinschränkung) in **Fix Distance From Head** (Fester Abstand vom Kopf), sodass das Objekt, wenn es bewegt wird, immer den gleichen Abstand vom Benutzer beibehält:</span><span class="sxs-lookup"><span data-stu-id="f2f72-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="f2f72-192">Greifbar-Standardmanipulation</span><span class="sxs-lookup"><span data-stu-id="f2f72-192">Default grabbable manipulation</span></span>

<span data-ttu-id="f2f72-193">Belassen Sie für die Objekte **Cheese**, **CoffeeCup** und **EarthCore** alle Eigenschaften auf den Standardwerten, um das Greifbar-Standardmanipulationsverhalten zu erleben:</span><span class="sxs-lookup"><span data-stu-id="f2f72-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="f2f72-195">Entfernen der Möglichkeit zur Fernmanipulation</span><span class="sxs-lookup"><span data-stu-id="f2f72-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="f2f72-196">Deaktivieren Sie für das **Octa**-Objekt das Kontrollkästchen **Allow Far Manipulation** (Fern-Manipulation zulassen), um zu erreichen, dass der Benutzer mit dem Objekt nur direkt mithilfe der nachverfolgten Hände interagieren kann:</span><span class="sxs-lookup"><span data-stu-id="f2f72-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="f2f72-198">Drehen eines Objekts um seine Mitte</span><span class="sxs-lookup"><span data-stu-id="f2f72-198">Make an object rotate around its center</span></span>

<span data-ttu-id="f2f72-199">Ändern Sie für das **Platonic**-Objekt **One Hand Rotation Mode Near** (Einhanddrehungsmodus nah) und **One Hand Rotation Mode Far** (Einhanddrehungsmodus fern) in **Rotate About Object Center** (Drehung um Objektmitte), um zu erreichen, dass das Objekt sich um seine Mitte dreht, wenn der Benutzer es mit einer Hand dreht:</span><span class="sxs-lookup"><span data-stu-id="f2f72-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="f2f72-201">Beibehalten der Bewegung nach dem Freigeben des Objekts</span><span class="sxs-lookup"><span data-stu-id="f2f72-201">Keep movement after object is released</span></span>

<span data-ttu-id="f2f72-202">Fügen Sie für das **TheModule**-Objekt eine **Rigidbody**-Komponente hinzu, um physikalische Eigenschaften zu aktivieren, und deaktivieren Sie dann das Kontrollkästchen **Use Gravity** (Schwerkraft verwenden), damit das Objekt nicht durch Schwerkraft beeinflusst wird:</span><span class="sxs-lookup"><span data-stu-id="f2f72-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="f2f72-204">Überprüfen Sie in der Manipulation Handler (Script)-Komponente, dass für **Release Behavior** (Freigabeverhalten) sowohl **Keep Velocity** (Geschwindigkeit beibehalten) als auch **Keep Angular Velocity** (Winkelgeschwindigkeit beibehalten) aktiviert ist, sodass das Objekt seine Bewegung fortsetzt, wenn der Benutzer es mit seiner Hand freigibt:</span><span class="sxs-lookup"><span data-stu-id="f2f72-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="f2f72-206">Weitere Informationen über die Manipulationshandler-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zum [Manipulationshandler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="f2f72-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="f2f72-207">Hinzufügen von Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="f2f72-207">Adding bounding boxes</span></span>

<span data-ttu-id="f2f72-208">Begrenzungsrahmen machen das einhändige Manipulieren von Objekten sowohl für die Nah- als auch für die Ferninteraktion komfortabler und intuitiver, indem sie Ziehpunkte bereitstellen, die für die Änderung der Größe und zum Rotieren verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="f2f72-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="f2f72-209">In diesem Beispiel fügen Sie dem EarthCore-Objekt einen Begrenzungsrahmen hinzu, damit die Interaktion mit diesem Objekt nun mithilfe der Objektmanipulation erfolgen kann, die Sie im vorherigen Abschnitt konfiguriert haben. Außerdem kann es mithilfe der Ziehpunkte des Begrenzungsrahmens gedreht und in der Größe verändert werden.</span><span class="sxs-lookup"><span data-stu-id="f2f72-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2f72-210">Damit Sie **einen Begrenzungsrahmen** verwenden können, muss das Objekt die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="f2f72-211">**Collider**-Komponente, z. B. ein Feld-Collider</span><span class="sxs-lookup"><span data-stu-id="f2f72-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="f2f72-212">**Bounding Box (Script)** -Komponente (Begrenzungsrahmen (Skript))</span><span class="sxs-lookup"><span data-stu-id="f2f72-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="f2f72-213">1. Hinzufügen der Bounding Box (Script)-Komponente zum EarthCore-Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="f2f72-214">Wählen Sie im Inspektorfenster das **EarthCore**-Objekt aus, und fügen Sie ihm die **Bounding Box (Script)** -Komponente hinzu:</span><span class="sxs-lookup"><span data-stu-id="f2f72-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f2f72-216">Die Visualisierungen von Begrenzungsrahmen werden zur Laufzeit erstellt und sind daher erst sichtbar, wenn Sie in den Spielmodus wechseln.</span><span class="sxs-lookup"><span data-stu-id="f2f72-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="f2f72-217">2. Visualisieren und Testen des Begrenzungsrahmens mithilfe der in den Editor integrierten Simulation</span><span class="sxs-lookup"><span data-stu-id="f2f72-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="f2f72-218">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="f2f72-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="f2f72-219">Drücken und halten Sie dann die Leertaste, um die Hand anzuzeigen, und verwenden Sie die Maus, um mit dem Begrenzungsrahmen zu interagieren:</span><span class="sxs-lookup"><span data-stu-id="f2f72-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="f2f72-221">Weitere Informationen über die Bounding Box-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zur [Bounding Box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="f2f72-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="f2f72-222">Hinzufügen von Berührungseffekten</span><span class="sxs-lookup"><span data-stu-id="f2f72-222">Adding touch effects</span></span>

<span data-ttu-id="f2f72-223">In diesem Beispiel aktivieren Sie Ereignisse, die ausgelöst werden, wenn Sie ein Objekt mit der Hand berühren.</span><span class="sxs-lookup"><span data-stu-id="f2f72-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="f2f72-224">Insbesondere konfigurieren Sie das Octa-Objekt dafür, einen Soundeffekt wiederzugeben, wenn der Benutzer es berührt.</span><span class="sxs-lookup"><span data-stu-id="f2f72-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="f2f72-225">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f2f72-226">Hinzufügen einer Audioquellenkomponente zum Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="f2f72-227">Hinzufügen der Komponente „Near Interaction touchable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="f2f72-228">Hinzufügen der Komponente „Hand Interaction Touch (Script)“ (Handinteraktion, Berührung (Skript)) zum Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="f2f72-229">Implementieren des On Touch Started-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="f2f72-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="f2f72-230">Testen der Berührungsinteraktion mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="f2f72-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2f72-231">Damit Sie **Berührungsereignisse auslösen** können, muss das Objekt die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="f2f72-232">**Collider**-Komponente, vorzugsweise ein Feld-Collider</span><span class="sxs-lookup"><span data-stu-id="f2f72-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="f2f72-233">**Near Interaction touchable (Script)** -Komponente (Nah-Interaktion, berührbar (Skript))</span><span class="sxs-lookup"><span data-stu-id="f2f72-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="f2f72-234">**Hand Interaction Touch (Script)** -Komponente (Handinteraktion Berührung (Skript))</span><span class="sxs-lookup"><span data-stu-id="f2f72-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="f2f72-235">Die Komponente „Hand Interaction Touch (Script)“ (Handinteraktion Berührung (Skript)) ist nicht Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="f2f72-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="f2f72-236">Sie wurde zusammen mit den Ressourcen dieses Tutorials importiert und ist ursprünglich Teil der MixedReality Toolkit Unity-Beispiele.</span><span class="sxs-lookup"><span data-stu-id="f2f72-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="f2f72-237">1. Hinzufügen einer Audioquellenkomponente zum Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="f2f72-238">Wählen Sie im Hierarchiefenster das **Octa**-Objekt aus, fügen Sie ihm eine **Audioquelle**-Komponente hinzu, und ändern Sie dann **Spatial Blend** (Räumliche Mischung) in 1, um räumliche Audiowiedergabe zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="f2f72-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="f2f72-240">2. Hinzufügen der Komponente „Near Interaction touchable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="f2f72-241">Fügen Sie bei noch ausgewähltem **Octa**-Objekt dem Octa-Objekt die Komponente **Near Interaction Touchable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzu, und klicken Sie dann auf die Schaltflächen **Fix Bounds** (Begrenzungen fixieren) und **Fix Center** (Mitte fixieren), um die Eigenschaften „Local Center“ und „Bounds“ von Near Interaction Touchable (Script) so zu aktualisieren, dass sie mit dem Feld-Collider übereinstimmen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="f2f72-243">3. Hinzufügen der Komponente „Hand Interaction Touch (Script)“ (Handinteraktion Berührung (Skript)) zum Objekt</span><span class="sxs-lookup"><span data-stu-id="f2f72-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="f2f72-244">Fügen Sie bei immer noch ausgewähltem **Octa**-Objekt dem Octa-Objekt die **Hand Interaction Touch (Script)** -Komponente hinzu:</span><span class="sxs-lookup"><span data-stu-id="f2f72-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="f2f72-246">4. Implementieren des On Touch Started-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="f2f72-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="f2f72-247">Klicken Sie in der **Hand Interaction Touch (Script)** -Komponente auf das kleine **+** -Symbol, um ein neues **On Touch Started ()** -Ereignis zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2f72-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="f2f72-248">Konfigurieren Sie anschließend das **Octa**-Objekt für den Empfang des Ereignisses, und definieren Sie **AudioSource.PlayOneShot** als die auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="f2f72-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="f2f72-250">Navigieren Sie zu **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials (Ressourcen > MixedRealityToolkit.SDK > StandardAssets > Materialien), um die mit dem MRTK mitgelieferten Audioclips anzuzeigen, und weisen Sie dann dem Feld **Audio Clip** einen passenden Audioclip zu, beispielsweise den Audioclip „MRTK_Gem“:</span><span class="sxs-lookup"><span data-stu-id="f2f72-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="f2f72-252">Falls Sie eine Auffrischung zum Implementieren von Ereignissen benötigen, lesen Sie die Anweisungen unter [Gesten für Hand-Tracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="f2f72-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="f2f72-253">5. Testen der Berührungsinteraktion mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="f2f72-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="f2f72-254">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="f2f72-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="f2f72-255">Drücken und halten Sie dann die LEERTASTE, um die Hand anzuzeigen, und verwenden Sie die Maus, um das Octa-Objekt zu berühren und den Soundeffekt auszulösen:</span><span class="sxs-lookup"><span data-stu-id="f2f72-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="f2f72-257">Wie Sie beim Testen der Berührungsinteraktion gesehen haben und es in der Abbildung oben dargestellt ist, pulsierte die Farbe des Octa-Objekts, während es berührt wurde.</span><span class="sxs-lookup"><span data-stu-id="f2f72-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="f2f72-258">Dieser Effekt ist in der Hand Interaction Touch (Script)-Komponente hart codiert und kein Ergebnis der Ereigniskonfiguration, die Sie in den Schritten oben abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="f2f72-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="f2f72-259">Wenn Sie diesen Effekt deaktivieren möchten, können Sie beispielsweise Zeile 32 'TargetRenderer = GetComponentInChildren<Renderer>();' auskommentieren, was dazu führt, dass TargetRenderer den Wert null beibehält und die Farbe nicht pulsiert.</span><span class="sxs-lookup"><span data-stu-id="f2f72-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f2f72-260">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f2f72-260">Congratulations</span></span>

<span data-ttu-id="f2f72-261">In diesem Tutorial haben Sie erfahren, wie Sie 3D-Objekte in einer Rastersammlung organisieren und wie Sie diese Objekte durch Nah-Interaktion (direktes Greifen mit nachverfolgten Händen) und Fern-Interaktion (mit Lichtstrahlen zum Anvisieren oder Handstrahlen) manipulieren (Skalieren, Drehen und Bewegen) können.</span><span class="sxs-lookup"><span data-stu-id="f2f72-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="f2f72-262">Sie haben außerdem erfahren, wie Sie um 3D-Objekte herum Begrenzungsrahmen positionieren, und wie Sie die Ziehpunkte für die Begrenzungsrahmen verwenden und anpassen können.</span><span class="sxs-lookup"><span data-stu-id="f2f72-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="f2f72-263">Schließlich haben Sie erfahren, wie Sie beim Berühren eines Objekts Ereignisse auslösen können.</span><span class="sxs-lookup"><span data-stu-id="f2f72-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="f2f72-264">Nächste Lektion: 6. Untersuchen erweiterter Eingabeoptionen</span><span class="sxs-lookup"><span data-stu-id="f2f72-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
