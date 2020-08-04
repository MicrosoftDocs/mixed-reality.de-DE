---
title: 'Tutorials zu den ersten Schritten: 5 Erstellen dynamischer Inhalte mithilfe von Solvern'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 1a5017d8bc18ef239db88ee62cb2b65c77b2ab6f
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376612"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="9b747-105">5. Erstellen dynamischer Inhalte mithilfe von Solvern</span><span class="sxs-lookup"><span data-stu-id="9b747-105">5. Creating dynamic content using Solvers</span></span>

## <a name="overview"></a><span data-ttu-id="9b747-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="9b747-106">Overview</span></span>

<span data-ttu-id="9b747-107">In diesem Tutorial lernen Sie Möglichkeiten zur dynamischen Platzierung von Hologrammen mit den verfügbaren Platzierungstools des MRTK kennen, den so genannten Solvern, um Szenarien mit komplexer räumlicher Platzierung zu lösen.</span><span class="sxs-lookup"><span data-stu-id="9b747-107">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="9b747-108">Im MRTK bilden Solver ein System aus Skripts und Verhaltensweisen, mit deren Hilfe Objekte dem Benutzer oder anderen Spielobjekten in der Szene folgen können.</span><span class="sxs-lookup"><span data-stu-id="9b747-108">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="9b747-109">Sie können auch verwendet werden, um an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver wird.</span><span class="sxs-lookup"><span data-stu-id="9b747-109">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="9b747-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="9b747-110">Objectives</span></span>

* <span data-ttu-id="9b747-111">Einführen der MRTK-Solver</span><span class="sxs-lookup"><span data-stu-id="9b747-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="9b747-112">Erfahren, wie Benutzer mithilfe von Solvern zu Objekten geführt werden.</span><span class="sxs-lookup"><span data-stu-id="9b747-112">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="9b747-113">Erfahren, wie Solver zum Neupositionieren von Objekten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9b747-113">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="9b747-114">Speicherort der Solver im MRTK</span><span class="sxs-lookup"><span data-stu-id="9b747-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="9b747-115">Die Solver des MRTK befinden sich im MRTK SDK-Ordner.</span><span class="sxs-lookup"><span data-stu-id="9b747-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="9b747-116">Um die verfügbaren Solver in Ihrem Projekt anzuzeigen, navigieren Sie im Projektfenster zu **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers** (Medienobjekte > MRTK > SDK > Features > Hilfsprogramme > Solver):</span><span class="sxs-lookup"><span data-stu-id="9b747-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="9b747-118">In diesem Tutorial behandeln wir die Implementierung des Solvers Directional Indicator (Richtungsanzeige) und des Solvers Tap To Place (Zum Platzieren tippen).</span><span class="sxs-lookup"><span data-stu-id="9b747-118">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="9b747-119">Weitere Informationen zur ganzen Bandbreite der im MRTK verfügbaren Solver finden Sie im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9b747-119">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!NOTE]
> <span data-ttu-id="9b747-120">Der Richtungsanzeige-Solver befindet sich nicht in den oben angegebenen Solver-Ordnern, sondern im Ordner „Assets“ > „MRTK“ > „SDK“ > „Experimental“ > „Features“ > „Utilities“ (Medienobjekte > MRTK > SDK > Experimentell > Features > Hilfsprogramme), da es sich um ein experimentelles Feature handelt.</span><span class="sxs-lookup"><span data-stu-id="9b747-120">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Assets > MRTK > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="9b747-121">Verwenden des Richtungsanzeige-Solvers, um den Benutzer zu Objekten zu führen</span><span class="sxs-lookup"><span data-stu-id="9b747-121">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="9b747-122">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs), klicken Sie auf das **Chevron**-Prefab (Winkel), ziehen Sie es auf das Hierarchiefenster, und legen Sie seine **Transformationsposition**auf X = 0, Y = 0, Z = 2 fest, um es in der Nähe des RoverExplorer-Objekts zu positionieren:</span><span class="sxs-lookup"><span data-stu-id="9b747-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="9b747-124">Wenn Sie feststellen, dass die Kamera oder andere Symbole in Ihrer Szene die Objekte verdecken oder störend wirken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a>, in die Aus-Position, wie in der Abbildung oben dargestellt.</span><span class="sxs-lookup"><span data-stu-id="9b747-124">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="9b747-125">Weitere Informationen zum Gizmos-Menü und dessen Verwendung zur Optimierung Ihrer Szenenansicht finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos-Menü</a>.</span><span class="sxs-lookup"><span data-stu-id="9b747-125">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="9b747-126">Benennen Sie das neu hinzugefügte Chevron-Objekt in **Indicator** um, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponenten **DirectionalIndicator** und **Directional Indicator Controller (Script)** (Richtungsanzeigesteuerung (Skript)) hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="9b747-126">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator** and the **Directional Indicator Controller (Script)** component:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="9b747-128">Wenn Sie einen Solver hinzufügen, in diesem Fall die Komponente „DirectionalIndicator“, wird die Solver Handler-Komponente automatisch hinzugefügt, weil der Solver sie benötigt.</span><span class="sxs-lookup"><span data-stu-id="9b747-128">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="9b747-129">Die Directional Indicator Controller (Script)-Komponente ist nicht Teil des MRTK sondern ist in den Medienobjekten des Tutorials enthalten.</span><span class="sxs-lookup"><span data-stu-id="9b747-129">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="9b747-130">Konfigurieren Sie die Komponenten DirectionalIndicator und SolverHandler wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9b747-130">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="9b747-131">Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) der **SoverHandler**-Komponente auf **Head** (Kopf) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="9b747-131">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="9b747-132">Weisen Sie den **RoverExplorer** dem **Directional Target** (Richtungsziel) der **DirectionalIndicator**-Komponente zu, indem Sie ihn aus dem Hierarchiefenster auf das **None (Transform)** -Feld (Ohne (Transformation)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="9b747-132">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="9b747-133">Ändern Sie den **View Offset** (Ansichtsversatz) in 0,2</span><span class="sxs-lookup"><span data-stu-id="9b747-133">Change the **View Offset** to 0.2</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="9b747-135">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken Sie dann die rechte Maustaste, und halten Sie sie gedrückt, während Sie die Maus nach rechts oder links bewegen, um Ihre Blickrichtung zu drehen. Beachten Sie dabei Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9b747-135">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="9b747-136">Wenn Sie vom RoverExplorer-Objekt weg blicken, wird das Indikatorobjekt angezeigt und zeigt in die Richtung des RoverExplorer-Objekts.</span><span class="sxs-lookup"><span data-stu-id="9b747-136">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="9b747-138">Wenn Sie in Ihrem Szenefenster den Kamerastrahl nicht sehen, vergewissern Sie sich, dass Ihr Gizmos-Menü aktiviert ist, wie in der Abbildung oben dargestellt.</span><span class="sxs-lookup"><span data-stu-id="9b747-138">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="9b747-139">Informationen zum Verwenden der in den Editor integrierten Eingabesimulation finden Sie im Leitfaden [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) (Verwenden der in den Editor integrierten Handeingabesimulation zum Testen einer Szene) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9b747-139">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!TIP]
> <span data-ttu-id="9b747-140">Wenn Ihr Computer ein Mikrofon aufweist, können Sie den Aktivitätszustand des Diagnosepanels, das im Spielfenster angezeigt wird, leicht umschalten, indem Sie den Sprachbefehl „toggle diagnostics“ (Diagnose umschalten) verwenden.</span><span class="sxs-lookup"><span data-stu-id="9b747-140">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="9b747-141">Alternativ können Sie es im MRTK-Konfigurationsprofil deaktivieren, „Profile“ > „Diagnostics“ > „Enable Diagnostics System“ (Profil > Diagnose > Diagnosesystem aktivieren).</span><span class="sxs-lookup"><span data-stu-id="9b747-141">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="9b747-142">Im allgemeinen empfiehlt es sich aber, das Diagnosesystem während der Entwicklung aktiviert zu lassen.</span><span class="sxs-lookup"><span data-stu-id="9b747-142">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="9b747-143">Verwenden des Tap to Place-Solvers, um die Positionierung von Objekten zu ändern</span><span class="sxs-lookup"><span data-stu-id="9b747-143">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="9b747-144">Wählen Sie im Hierarchiefenster das Objekt RoverExplorer > **RoverAssembly** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Tap To Place (Script)** (Zum Platzieren tippen (Skript)) hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9b747-144">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="9b747-145">Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) der **SoverHandler**-Komponente auf **Head** (Kopf) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="9b747-145">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="9b747-146">Aktivieren Sie das Kontrollkästchen **Keep Orientation Vertical** (Vertikale Ausrichtung beibehalten).</span><span class="sxs-lookup"><span data-stu-id="9b747-146">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="9b747-147">Deaktivieren Sie in der Dropdownliste **Magnetic Surfaces** > **Element 0** (Magnetische Oberflächen > Element 0) alle Optionen mit Ausnahme von **Spatial Awareness** (Räumliche Wahrnehmung).</span><span class="sxs-lookup"><span data-stu-id="9b747-147">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9b747-149">Die Einstellung „Magnetic Surfaces“ (Magnetische Oberflächen) bestimmt, welche Objekte von der Komponente Tap To Place (Script) beim Platzieren eines Objekts erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="9b747-149">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="9b747-150">Indem Sie die Einstellung nur zu Spatial Awareness (Räumliche Wahrnehmung) ändern, kann die Tap To Place (Script)-Komponente den Rover nur auf Objekten platzieren, die sich auf der Unity-Ebene mit dem Namen „Spatial Awareness“ befinden, und das ist standardmäßig das von HoloLens generierte Spatial Awareness Mesh (Gittermodell für räumliche Wahrnehmung).</span><span class="sxs-lookup"><span data-stu-id="9b747-150">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="9b747-151">Weitere Informationen zu Ebenen finden Sie in der Dokumentation zu <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Ebenen</a> von Unity.</span><span class="sxs-lookup"><span data-stu-id="9b747-151">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="9b747-152">Wenn Sie beim Testen der Tap to Place-Funktionalität das Gittermodell für räumliche Wahrnehmung sehen möchten, können Sie die Anzeigeoption des Spatial Mesh Observer auf „Visible“ (Sichtbar) festlegen.</span><span class="sxs-lookup"><span data-stu-id="9b747-152">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="9b747-153">Wenn Sie eine Auffrischung zum Ändern der Anzeigeoption benötigen, informieren Sie sich in den Anweisungen zum [Ändern der Anzeigeoptionen für räumliche Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="9b747-153">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="9b747-154">Während das RoverAssembly-Objekt noch im Hierarchiefenster ausgewählt ist, suchen Sie im Inspektorfenster das Ereignis **On Placing Started ()** (Bei Platzierung gestartet ()), und klicken Sie auf das **+** -Symbol, um ein neues Ereignis hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="9b747-154">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="9b747-156">Konfigurieren Sie das Ereignis wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9b747-156">Configure the event as follows:</span></span>

* <span data-ttu-id="9b747-157">Weisen Sie das **RoverAssembly**-Objekt als Listener für das On Placing Started ()-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="9b747-157">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="9b747-158">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **TapToPlace** > **float SurfaceNormalOffset** aus, um den Wert der Eigenschaft SurfaceNormalOffset zu aktualisieren, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="9b747-158">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="9b747-159">Vergewissern Sie sich, dass das Argument auf **0** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="9b747-159">Verify that the argument is set to **0**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="9b747-161">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, wählen Sie **3D Object** > **Cube** (3D-Objekt > Würfel) aus, um ein vorübergehendes Objekt zu erstellen, das den Boden darstellt, und konfigurieren Sie die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9b747-161">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="9b747-162">**Position**: X = 0, Y = -1,65, Z = 6</span><span class="sxs-lookup"><span data-stu-id="9b747-162">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="9b747-163">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="9b747-163">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="9b747-164">**Skalierung**: X = 10, Y = 0,2, Z = 10</span><span class="sxs-lookup"><span data-stu-id="9b747-164">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="9b747-166">Während der temporäre Würfel noch im Hierarchiefenster ausgewählt ist, verwenden Sie im Inspektorfenster die Dropdownliste **Layers** (Ebenen), um die Ebeneneinstellung des Würfels so zu ändern, dass sie nur die Ebene **Spatial Awareness** (Räumliche Wahrnehmung) enthält:</span><span class="sxs-lookup"><span data-stu-id="9b747-166">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="9b747-168">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken Sie dann die rechte Maustaste, und halten Sie sie gedrückt, während Sie Maus abwärts bewegen, bis der Blick auf das RoverAssembly-Objekt trifft:</span><span class="sxs-lookup"><span data-stu-id="9b747-168">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="9b747-170">Klicken Sie mit der linken Maustaste, um den Zum-Platzieren-tippen-Vorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="9b747-170">Click the left mouse button to start the tap-to-place process:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="9b747-172">Drücken Sie die rechte Maustaste, und halten Sie sie gedrückt, während Sie die Maus nach rechts oder links bewegen, um Ihre Blickrichtung zu drehen. Wenn Sie mit der Positionierung einverstanden sind, klicken Sie mit der linken Maustaste:</span><span class="sxs-lookup"><span data-stu-id="9b747-172">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="9b747-174">Wenn Sie das Testen des Features im Spielmodus abgeschlossen haben, klicken Sie mit der rechten Maustaste auf das Würfelobjekt, und wählen Sie **Löschen** aus, um es aus der Szene zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="9b747-174">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="9b747-176">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9b747-176">Congratulations</span></span>

<span data-ttu-id="9b747-177">In diesem Tutorial haben Sie gelernt, wie Sie den Richtungsindikator-Solver aus dem MRTK dazu verwenden können, den Benutzer durch ein Benutzeroberflächenelement intuitiv zu Objekten zu führen.</span><span class="sxs-lookup"><span data-stu-id="9b747-177">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="9b747-178">Sie haben darüber hinaus erfahren, wie der Zum-Platzieren-tippen-Solver verwendet wird, um die Position von Objekten auf einfache Weise zu ändern.</span><span class="sxs-lookup"><span data-stu-id="9b747-178">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="9b747-179">Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9b747-179">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="9b747-180">Nächstes Tutorial: 6. Erstellen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="9b747-180">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
