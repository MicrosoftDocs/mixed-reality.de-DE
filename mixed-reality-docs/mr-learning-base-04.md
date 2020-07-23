---
title: 'Tutorials zu den ersten Schritten: 4 Positionieren von Objekten in der Szene'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 356bfa788cd28e8c763a45a2d44c3a1241b8467e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305514"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="203aa-105">4. Positionieren von Objekten in der Szene</span><span class="sxs-lookup"><span data-stu-id="203aa-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="203aa-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="203aa-106">Overview</span></span>

<span data-ttu-id="203aa-107">In diesem Tutorial importieren Sie die Medienobjekte für das Tutorial und positionieren die bereitgestellten Objekte in der Szene.</span><span class="sxs-lookup"><span data-stu-id="203aa-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="203aa-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="203aa-108">Objectives</span></span>

* <span data-ttu-id="203aa-109">Erfahren, wie Objekte in der Szene positioniert werden</span><span class="sxs-lookup"><span data-stu-id="203aa-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="203aa-110">Erfahren, wie die Rasterobjektsammlung des MRTK verwendet wird</span><span class="sxs-lookup"><span data-stu-id="203aa-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="203aa-111">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="203aa-111">Importing the tutorial assets</span></span>

<span data-ttu-id="203aa-112">Laden Sie das folgende benutzerdefinierte Unity-Paket herunter, und importieren Sie es:</span><span class="sxs-lookup"><span data-stu-id="203aa-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="203aa-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="203aa-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="203aa-114">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="203aa-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="203aa-116">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="203aa-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="203aa-117">Erstellen des übergeordneten Objekts</span><span class="sxs-lookup"><span data-stu-id="203aa-117">Creating the parent object</span></span>

<span data-ttu-id="203aa-118">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="203aa-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="203aa-120">Um Ihr Szenen- und Spielfenster nebeneinander anzuzeigen, wie in der Abbildung oben dargestellt, ziehen Sie das Spielfenster rechts neben das Szenenfenster.</span><span class="sxs-lookup"><span data-stu-id="203aa-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="203aa-121">Weitere Informationen zum Anpassen Ihres Arbeitsbereichs finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="203aa-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="203aa-122">Klicken Sie mit der rechten Maustaste auf das neu erstellte Objekt, wählen Sie **Umbenennen** aus, und ändern Sie den Namen in **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="203aa-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="203aa-124">Konfigurieren Sie bei immer noch ausgewähltem RoverExplorer-Objekt im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="203aa-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="203aa-125">**Position**: X = 0, Y = -0,6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="203aa-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="203aa-126">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="203aa-127">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="203aa-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="203aa-129">Die Kamera stellt den Kopf des Benutzers dar und befindet sich am Ursprung, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="203aa-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="203aa-130">Im Allgemeinen entspricht 1 Einheit in Unity ungefähr einem Meter in der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="203aa-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="203aa-131">Es gibt jedoch Ausnahmen, z. B. wenn Objekte untergeordnete Objekte von skalierten Objekten sind.</span><span class="sxs-lookup"><span data-stu-id="203aa-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="203aa-132">Im Szenario oben ist der RoverExplorer 2 Meter vor und 0,6 Meter unterhalb des Kopfs des Benutzers positioniert.</span><span class="sxs-lookup"><span data-stu-id="203aa-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="203aa-133">Hinzufügen der Prefabs für das Tutorial</span><span class="sxs-lookup"><span data-stu-id="203aa-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="203aa-134">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GEttingStarted** > **Prefabs**:</span><span class="sxs-lookup"><span data-stu-id="203aa-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="203aa-136">Ein <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> ist ein vorkonfiguriertes GameObject, das als Unity-Ressource gespeichert ist und durchgängig im Projekt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="203aa-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="203aa-137">Klicken Sie im Projektfenster auf das **Table**-Prefab (Tabelle), und ziehen Sie es aus dem Projektfenster auf das **RoverExplorer**-Objekt, um es zu einem untergeordneten Objekt des RoverExplorer-Objekts zu machen. Konfigurieren Sie dann im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="203aa-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="203aa-138">**Position**: X = 0, Y = -0,005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="203aa-139">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="203aa-140">**Skalierung**: X = 1,2, Y = 0,01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="203aa-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="203aa-142">Um Ihre Szene so anzuzeigen, wie Sie in der Abbildung oben dargestellt ist, verwenden Sie den <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, der sich in der oberen rechten Ecke des Szenenfensters befindet, um den Betrachtungswinkel so anzupassen, dass er entlang der vorwärtsgerichteten Z-Achse verläuft, doppelklicken Sie auf das MixedRealityPlayspace-Objekt, um den Fokus auf die Kamera zu legen, und zoomen Sie nach Bedarf herein.</span><span class="sxs-lookup"><span data-stu-id="203aa-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="203aa-143">Klicken Sie im Projektfenster auf das **RoverAssembly**-Prefab, und ziehen Sie es auf das **RoverExplorer**-Objekt, um es zu einem untergeordneten Objekt des RoverExplorer-Objekts zu machen. Konfigurieren Sie dann im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="203aa-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="203aa-144">**Position**: X = -0,1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="203aa-145">**Drehung**: X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="203aa-146">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="203aa-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="203aa-148">Organisieren von Objekten in einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="203aa-148">Organizing objects in a collection</span></span>

<span data-ttu-id="203aa-149">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **RoverExplorer**-Objekt, und wählen Sie **Create Empty** (Leer erstellen) aus, um ein leeres Objekt als untergeordnetes Objekt des RoverExplorers hinzuzufügen, benennen Sie das Objekt **RoverParts**, und konfigurieren Sie die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="203aa-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="203aa-150">**Position**: X = 0, Y = 0,06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="203aa-151">**Drehung**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="203aa-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="203aa-152">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="203aa-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="203aa-154">Wählen Sie im Hierarchiefenster mithilfe von „RoverExplorer > RoverAssembly > RoverModel > **Parts**“ (...> Teile) alle untergeordneten Objekte aus, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Duplicate** (Duplizieren) aus, um eine Kopie aller Teile zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="203aa-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="203aa-156">Um mehrere angrenzende Objekte auszuwählen, drücken Sie die UMSCHALTTASTE, und halten Sie sie gedrückt, während Sie die Maus verwenden, um das erste und das letzte Objekt auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="203aa-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="203aa-157">Klicken Sie auf die noch ausgewählten neu duplizierten untergeordneten Teileobjekte, und ziehen Sie sie auf das **RoverParts**-Objekts, um sie als untergeordnete Objekte des RoverParts-Objekts festzulegen:</span><span class="sxs-lookup"><span data-stu-id="203aa-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="203aa-159">Um das Arbeiten mit Ihrer Szene zu vereinfachen, klicken Sie im Hierarchiefenster auf das **Augensymbol** links neben dem Objekt, um die **Scene Visibility** (Sichtbarkeit in der Szene) für das **RoverExplorer**-Objekt auszuschalten.</span><span class="sxs-lookup"><span data-stu-id="203aa-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverExplorer** object off.</span></span> <span data-ttu-id="203aa-160">Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne Auswirkungen auf seine Sichtbarkeit im Spiel:</span><span class="sxs-lookup"><span data-stu-id="203aa-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="203aa-162">Mehr zu den Steuerelementen für die Sichtbarkeit in der Szene und ihre Verwendung zum Optimieren Ihrer Szenenansicht und Ihres Workflows finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene).</span><span class="sxs-lookup"><span data-stu-id="203aa-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="203aa-163">Bereinigen Sie im Hierarchiefenster die Namen der untergeordneten RoverParts-Objekte, indem Sie die angefügte **(1)** durch **_Part** ersetzen:</span><span class="sxs-lookup"><span data-stu-id="203aa-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="203aa-165">Wählen Sie im Hierarchiefenster das **RoverParts**-Objekt aus, klicken Sie dann im Inspektorfenster auf die Schaltfläche **Add Component** (Komponente hinzufügen), suchen Sie nach **GridObjectCollection**, und wählen Sie sie aus, um die GridObjectCollection-Komponente zum RoverParts-Objekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="203aa-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="203aa-167">Konfigurieren Sie die Werte der **GridObjectCollection**-Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="203aa-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="203aa-168">**Sortierungstyp**: Alphabetisch</span><span class="sxs-lookup"><span data-stu-id="203aa-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="203aa-169">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="203aa-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="203aa-170">**Zellenbreite**: 0,25</span><span class="sxs-lookup"><span data-stu-id="203aa-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="203aa-171">**Abstand vom übergeordneten Element**: 0,38</span><span class="sxs-lookup"><span data-stu-id="203aa-171">**Distance from parent**: 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="203aa-173">Klicken Sie dann auf die Schaltfläche **Update Collection** (Sammlung aktualisieren), um die Position der untergeordneten RoverParts-Objekte zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="203aa-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="203aa-175">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="203aa-175">Congratulations</span></span>

<span data-ttu-id="203aa-176">In diesem Tutorial haben Sie gelernt, wie Objekte relativ zum Benutzer in der Szene positioniert werden und wie das Feature Rasterobjektsammlung des MRTK verwendet wird, um Objekte in einer Sammlung zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="203aa-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="203aa-177">Nächstes Tutorial: 5. Erstellen dynamischer Inhalte mithilfe von Solvern</span><span class="sxs-lookup"><span data-stu-id="203aa-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
