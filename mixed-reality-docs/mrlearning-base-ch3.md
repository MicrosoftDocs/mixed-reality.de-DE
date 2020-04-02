---
title: 'Tutorials zu den ersten Schritten: 4 Platzieren dynamischer Inhalte und Verwenden von Solvern'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362041"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="a8ae7-105">4. Platzieren dynamischer Inhalte und Verwenden von Solvern</span><span class="sxs-lookup"><span data-stu-id="a8ae7-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="a8ae7-106">Hologramme werden in HoloLens 2 lebendig, wenn sie dem Benutzer intuitiv folgen und in der physischen Umgebung so platziert werden, dass die Interaktion reibungslos und stilvoll verläuft.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="a8ae7-107">In diesem Tutorial untersuchen wir Möglichkeiten zur dynamischen Platzierung von Hologrammen mit den verfügbaren Platzierungstools des MRTK, den so genannten Solvern, um Szenarien mit komplexer räumlicher Platzierung zu lösen.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="a8ae7-108">Im MRTK bilden Solver ein System aus Skripts und Verhaltensweisen, mit deren Hilfe es Benutzeroberflächenelementen ermöglicht wird, dem Benutzer oder anderen Spielobjekten in der Szene zu folgen.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="a8ae7-109">Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="a8ae7-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="a8ae7-110">Objectives</span></span>

* <span data-ttu-id="a8ae7-111">Einführen der MRTK-Solver</span><span class="sxs-lookup"><span data-stu-id="a8ae7-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="a8ae7-112">Verwenden von Solvern, um eine Sammlung von Schaltflächen dem Benutzer folgen zu lassen</span><span class="sxs-lookup"><span data-stu-id="a8ae7-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="a8ae7-113">Verwenden von Solvern, um ein Spielobjekt den nachverfolgten Händen des Benutzers folgen zu lassen</span><span class="sxs-lookup"><span data-stu-id="a8ae7-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="a8ae7-114">Speicherort der Solver im MRTK</span><span class="sxs-lookup"><span data-stu-id="a8ae7-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="a8ae7-115">Die Solver des MRTK befinden sich im MRTK SDK-Ordner.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="a8ae7-116">Um die verfügbaren Solver in Ihrem Projekt anzuzeigen, navigieren Sie im Projektfenster zu **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="a8ae7-118">In diesem Tutorial behandeln wir die Implementierung der Solver „Orbital“ und „Radial View“.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="a8ae7-119">Weitere Informationen zur ganzen Bandbreite der im MRTK verfügbaren Solver finden Sie im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="a8ae7-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="a8ae7-120">Verwenden eines Solvers zum Folgen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="a8ae7-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="a8ae7-121">In diesem Abschnitt erweitern Sie die Schaltflächensammlung, die Sie im vorherigen Tutorial erstellt haben, sodass sie der Blickrichtung des Benutzers folgt.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="a8ae7-122">Darüber hinaus konfigurieren Sie den Solver so, dass Folgendes immer auf die Schaltflächensammlung zutrifft:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="a8ae7-123">Sie wird parallel zur Leserichtung des Benutzers gedreht, für natürliches Lesen von links nach rechts</span><span class="sxs-lookup"><span data-stu-id="a8ae7-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="a8ae7-124">Sie wird unterhalb der horizontalen Blickrichtung des Benutzers positioniert, sodass die anderen Objekte, die später in diesem Tutorial hinzugefügt werden, nicht verdeckt werden</span><span class="sxs-lookup"><span data-stu-id="a8ae7-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="a8ae7-125">Sie wird ungefähr eine halbe Armlänge vom Benutzer entfernt, sodass die Schaltflächen leicht gedrückt werden können</span><span class="sxs-lookup"><span data-stu-id="a8ae7-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="a8ae7-126">Hierzu verwenden Sie den **Orbital-Solver**, der das Objekt fest an einer angegebenen Position und einem Offset vom Bezugsobjekt verankert.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="a8ae7-127">1. Hinzufügen des Orbital-Solvers</span><span class="sxs-lookup"><span data-stu-id="a8ae7-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="a8ae7-128">Wählen Sie im Hierarchiefenster das **ButtonCollection**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem ButtonCollection-Objekt die Komponente **Orbital (Script)** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="a8ae7-129">Wenn Sie einen Solver hinzufügen, in diesem Fall die Komponente „Orbital (Script)“, wird die Solver Handler (Script)-Komponente automatisch hinzugefügt, weil diese vom Solver benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="a8ae7-130">2. Konfigurieren des Orbital-Solvers</span><span class="sxs-lookup"><span data-stu-id="a8ae7-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="a8ae7-131">Konfigurieren Sie die **Solver Handler (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="a8ae7-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="a8ae7-132">Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) auf **Head** (Kopf) festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="a8ae7-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="a8ae7-133">Konfigurieren Sie die **Orbital (Script)** -Komponente:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="a8ae7-134">Vergewissern Sie sich, dass der **Orientation Type** (Ausrichtungstyp) auf **Follow Tracked Object** (Nachverfolgtem Objekt folgen) festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="a8ae7-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="a8ae7-135">Setzen Sie **Local Offset** auf X = 0, Y = 0, Z = 0 zurück</span><span class="sxs-lookup"><span data-stu-id="a8ae7-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="a8ae7-136">Ändern Sie **World Offset** auf X = 0, Y = -0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="a8ae7-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="a8ae7-138">3. Testen des Orbital-Solvers mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="a8ae7-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="a8ae7-139">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken und halten Sie dann die rechte Maustaste, um Ihre Blickrichtung zu drehen, und achten Sie auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="a8ae7-140">Die Transformationsposition der ButtonCollection wird jetzt durch die Solver-Einstellungen gesteuert</span><span class="sxs-lookup"><span data-stu-id="a8ae7-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="a8ae7-141">Der Würfel, der nicht vom Solver beeinflusst wird, bleibt an der gleichen Position.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="a8ae7-143">Wenn Sie in Ihrem Szenefenster den Kamerastrahl nicht sehen, vergewissern Sie sich, dass Ihr Gizmos-Menü aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="a8ae7-144">Weitere Informationen zum Gizmos-Menü und dessen Verwendung zur Optimierung Ihrer Szenenansicht finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos-Menü</a>.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="a8ae7-145">Um Ihr Szenen- und Spielfenster nebeneinander anzuzeigen, wie in der Abbildung oben dargestellt, ziehen Sie einfach das Spielfenster rechts neben das Szenenfenster.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="a8ae7-146">Weitere Informationen zum Anpassen Ihres Arbeitsbereichs finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="a8ae7-147">Objekten das Folgen von nachverfolgten Händen ermöglichen</span><span class="sxs-lookup"><span data-stu-id="a8ae7-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="a8ae7-148">In diesem Abschnitt konfigurieren Sie das Würfelobjekt, das Sie im vorherigen Tutorial erstellt haben, so, dass es den nachverfolgten Händen des Benutzers folgt, insbesondere dem rechten Handgelenk.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="a8ae7-149">Darüber hinaus konfigurieren Sie den Solver so, dass Folgendes auf den Würfel zutrifft:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="a8ae7-150">Er ändert die Ausrichtung mit der Handdrehung des Benutzers</span><span class="sxs-lookup"><span data-stu-id="a8ae7-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="a8ae7-151">Er ist auf dem Handgelenk des Benutzers positioniert</span><span class="sxs-lookup"><span data-stu-id="a8ae7-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="a8ae7-152">Zu diesem Zweck verwenden Sie den **Radial View Solver** (Radialansichts-Solver), der das Objekt innerhalb eines Ansichtskegels hält, der vom Bezugsobjekt projiziert wird.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="a8ae7-153">1. Hinzufügen des Radial View-Solvers</span><span class="sxs-lookup"><span data-stu-id="a8ae7-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="a8ae7-154">Wählen Sie im Hierarchiefenster das **Würfelobjekt** aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Würfelobjekt die Komponente **Radial View (Script)** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="a8ae7-155">2. Konfigurieren des Radial View-Solvers</span><span class="sxs-lookup"><span data-stu-id="a8ae7-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="a8ae7-156">Konfigurieren Sie die **Solver Handler (Script)** -Komponente:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="a8ae7-157">Ändern Sie **Tracked Target Type** (Typ des nachverfolgten Ziels) in **Gelenk der Hand**</span><span class="sxs-lookup"><span data-stu-id="a8ae7-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="a8ae7-158">Ändern Sie **Tracked Handness** (nachverfolgte Händischkeit) in **Right**</span><span class="sxs-lookup"><span data-stu-id="a8ae7-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="a8ae7-159">Ändern Sie **Tracked Hand Joint** (Nachverfolgtes Gelenk der Hand) in **Wrist** (Handgelenk)</span><span class="sxs-lookup"><span data-stu-id="a8ae7-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="a8ae7-160">Konfigurieren Sie die **Radial View (Script)** -Komponente:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="a8ae7-161">Ändern Sie **Reference Direction** (Bezugsrichtung) in **Object Oriented** (Objektorientiert), und aktivieren Sie dann das Kontrollkästchen **Orient To Reference Direction** (An Bezugsrichtung ausrichten)</span><span class="sxs-lookup"><span data-stu-id="a8ae7-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="a8ae7-162">Ändern Sie **Min Distance** (Minimalabstand) und **Max Distance** (Maximalabstand) in 0</span><span class="sxs-lookup"><span data-stu-id="a8ae7-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="a8ae7-164">3. Testen des Radial View-Solvers mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="a8ae7-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="a8ae7-165">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, und halten Sie dann die LEERTASTE gedrückt, um die Hand anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="a8ae7-166">Bewegen Sie den Mauszeiger, um die Hand zu bewegen, und klicken und halten Sie die linke Maustaste, um die Hand zu drehen:</span><span class="sxs-lookup"><span data-stu-id="a8ae7-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="a8ae7-168">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a8ae7-168">Congratulations</span></span>

<span data-ttu-id="a8ae7-169">In diesem Tutorial haben Sie erfahren, wie Sie die MRTK-Solver verwenden können, damit eine Benutzeroberfläche intuitiv dem Benutzer folgt.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="a8ae7-170">Sie haben auch erfahren, wie Sie einen Solver an ein Objekt (d. h. Würfel) anfügen, um den nachverfolgten Händen des Benutzers zu folgen.</span><span class="sxs-lookup"><span data-stu-id="a8ae7-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="a8ae7-171">Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="a8ae7-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="a8ae7-172">Nächstes Tutorial: 5. Interagieren mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="a8ae7-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
