---
title: 'Tutorials zu den ersten Schritten: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129321"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="14555-105">4. Platzieren von dynamischem Inhalt und Verwenden von Solvers</span><span class="sxs-lookup"><span data-stu-id="14555-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="14555-106">Holograms sind in hololens 2 zu leben, wenn Sie intuitiv dem Benutzer folgen und in der physischen Umgebung auf eine Weise platziert werden, die die Interaktion nahtlos und elegant macht.</span><span class="sxs-lookup"><span data-stu-id="14555-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="14555-107">In diesem Tutorial wird erläutert, wie Sie Hologramme dynamisch mithilfe der verfügbaren Platzierungs Tools von mrtk platzieren können, die als Solvers bezeichnet werden, um komplexe räumliche Platzierungs Szenarien zu lösen.</span><span class="sxs-lookup"><span data-stu-id="14555-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="14555-108">In den mrtk sind Solvers ein System aus Skripts und Verhalten, mit denen Benutzeroberflächen Elemente Ihnen, dem Benutzer oder anderen Spielobjekten in der Szene folgen können.</span><span class="sxs-lookup"><span data-stu-id="14555-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="14555-109">Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird.</span><span class="sxs-lookup"><span data-stu-id="14555-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="14555-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="14555-110">Objectives</span></span>

* <span data-ttu-id="14555-111">Einführen von mrtk-Solvers</span><span class="sxs-lookup"><span data-stu-id="14555-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="14555-112">Verwenden Sie Solvers, damit eine Auflistung von Schaltflächen auf den Benutzer folgt.</span><span class="sxs-lookup"><span data-stu-id="14555-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="14555-113">Verwenden Sie Solvers, damit ein Spielobjekt den nach verfolgten Händen des Benutzers folgt.</span><span class="sxs-lookup"><span data-stu-id="14555-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="14555-114">Speicherort der Solver in der mrtk</span><span class="sxs-lookup"><span data-stu-id="14555-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="14555-115">Die Solvers von mrtk befinden sich im Ordner "mrtk SDK".</span><span class="sxs-lookup"><span data-stu-id="14555-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="14555-116">Um die verfügbaren Solver in Ihrem Projekt anzuzeigen, navigieren Sie im Projektfenster zu **Assets** > **mixedrealitytoolkit. SDK** > **Features** > **Hilfsprogramme** > **Solvers**:</span><span class="sxs-lookup"><span data-stu-id="14555-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="14555-118">In diesem Tutorial überprüfen wir die Implementierung des "Orbital Solver" und des radivers für radiale Ansichten.</span><span class="sxs-lookup"><span data-stu-id="14555-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="14555-119">Weitere Informationen über die vollständige Palette der in der mrtk verfügbaren Solver finden Sie im Handbuch zu [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="14555-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="14555-120">Verwenden Sie einen Solver, um dem Benutzer zu folgen.</span><span class="sxs-lookup"><span data-stu-id="14555-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="14555-121">In diesem Abschnitt erweitern Sie die Schaltflächen Auflistung, die Sie im vorherigen Tutorial erstellt haben, damit Sie der Ausrichtung des Benutzers folgt.</span><span class="sxs-lookup"><span data-stu-id="14555-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="14555-122">Außerdem konfigurieren Sie den Solver so, dass die Schaltflächen Auflistung immer verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="14555-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="14555-123">Wird parallel zur Leserichtung des Benutzers gedreht, damit der Lesevorgang von links nach rechts durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="14555-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="14555-124">Wird etwas unterhalb der horizontalen bidirektionale Ausrichtung positioniert, sodass nicht die anderen Objekte blockiert werden, die Sie später in diesem Tutorial hinzufügen werden.</span><span class="sxs-lookup"><span data-stu-id="14555-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="14555-125">Der Benutzer hat ungefähr eine halbe Arm-Länge positioniert, sodass die Schaltflächen problemlos gedrückt werden können.</span><span class="sxs-lookup"><span data-stu-id="14555-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="14555-126">Hierzu verwenden Sie den " **Orbital Solver** ", der das Objekt an eine angegebene Position und einen Offset des Objekts sperrt, auf das verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="14555-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="14555-127">1. Fügen Sie den Orbital-Solver hinzu.</span><span class="sxs-lookup"><span data-stu-id="14555-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="14555-128">Wählen Sie im Fenster Hierarchie das **buttoncollection** -Objekt aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um dem buttoncollection-Objekt die Komponente " **Orbital (Skript)** " hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="14555-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="14555-129">Wenn Sie in diesem Fall einen Solver hinzufügen, wird die Komponente "Solver-Handler (Skript)" automatisch hinzugefügt, da Sie für den Solver erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="14555-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="14555-130">2. Konfigurieren des "Orbital Solver"</span><span class="sxs-lookup"><span data-stu-id="14555-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="14555-131">Konfigurieren der **Solver-Handlerkomponente (Skript)** :</span><span class="sxs-lookup"><span data-stu-id="14555-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="14555-132">Überprüfen, ob der **verfolgte Zieltyp** auf **Head** festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="14555-132">Verify that **Tracked Target Type**  is set to **Head**</span></span>

<span data-ttu-id="14555-133">Konfigurieren Sie die Komponente " **Orbital (Skript)** ":</span><span class="sxs-lookup"><span data-stu-id="14555-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="14555-134">Ändern des **Orientierungstyp** für das nach **verfolgte Objekt**</span><span class="sxs-lookup"><span data-stu-id="14555-134">Change **Orientation Type** to **Follow Tracked Object**</span></span>
* <span data-ttu-id="14555-135">Legen Sie **den lokalen Offset** auf X = 0, Y = 0, Z = 0 (null) zurück.</span><span class="sxs-lookup"><span data-stu-id="14555-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="14555-136">Ändern des **Welt Offsets** in X = 0, Y =-0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="14555-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="14555-138">3. Testen des Orbital-Solvers mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="14555-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="14555-139">Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben, und halten Sie die Rechte Maustaste gedrückt, um die Richtung des Blicks zu drehen, und beachten Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="14555-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="14555-140">Die Transformations Position der buttoncollection wird jetzt durch die Solver-Einstellungen gesteuert.</span><span class="sxs-lookup"><span data-stu-id="14555-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="14555-141">Der Cube, der vom Solver nicht betroffen ist, bleibt an derselben Position.</span><span class="sxs-lookup"><span data-stu-id="14555-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="14555-143">Wenn der Kamera Strahl in Ihrem Szenen Fenster nicht angezeigt wird, stellen Sie sicher, dass Ihr Gizmos-Menü aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="14555-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="14555-144">Weitere Informationen zum Gizmos-Menü und deren Verwendung zur Optimierung Ihrer Szenen Ansicht finden Sie in der <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos-Menü</a> Dokumentation von Unity.</span><span class="sxs-lookup"><span data-stu-id="14555-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="14555-145">Um die Szene und das Spielfenster nebeneinander anzuzeigen, wie in der Abbildung oben gezeigt, ziehen Sie einfach das Spielfenster auf die Rechte Seite des Fensters Szene.</span><span class="sxs-lookup"><span data-stu-id="14555-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="14555-146">Weitere Informationen zum Anpassen des Arbeitsbereichs finden Sie in der Dokumentation zum <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Anpassen Ihres Arbeits</a> Bereichs in Unity.</span><span class="sxs-lookup"><span data-stu-id="14555-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="14555-147">Aktivieren von Objekten für die Verfolgung von nach verfolgten Händen</span><span class="sxs-lookup"><span data-stu-id="14555-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="14555-148">In diesem Abschnitt Konfigurieren Sie das Cube-Objekt, das Sie im vorherigen Tutorial erstellt haben, damit es den nach verfolgten Händen des Benutzers folgt, insbesondere dem rechten Handgelenk.</span><span class="sxs-lookup"><span data-stu-id="14555-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="14555-149">Außerdem konfigurieren Sie den Solver auch so, dass der Cube:</span><span class="sxs-lookup"><span data-stu-id="14555-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="14555-150">Ändert die Ausrichtung mit der Hand Drehung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="14555-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="14555-151">Auf dem Handgelenk des Benutzers positioniert</span><span class="sxs-lookup"><span data-stu-id="14555-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="14555-152">Hierzu verwenden Sie den **radiver der radialen Ansicht** , der das Objekt innerhalb eines Ansichts Kegels speichert, das auf das Objekt verweist, auf das verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="14555-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="14555-153">1. Fügen Sie den Solver für radiale Ansichten hinzu</span><span class="sxs-lookup"><span data-stu-id="14555-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="14555-154">Wählen Sie im Fenster Hierarchie das Cubeobjekt aus, und verwenden Sie dann im Inspektor- **Fenster die Schalt** Fläche **Komponente hinzufügen** , um das Komponenten-Cubeobjekt der **radialen Ansicht (Skript)** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="14555-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="14555-155">2. Konfigurieren Sie den Solver für radiale Ansichten.</span><span class="sxs-lookup"><span data-stu-id="14555-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="14555-156">Konfigurieren der **Solver-Handlerkomponente (Skript)** :</span><span class="sxs-lookup"><span data-stu-id="14555-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="14555-157">Änderungs nach **verfolgten Zieltyp** in **Hand Gelenk** ändern</span><span class="sxs-lookup"><span data-stu-id="14555-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="14555-158">Geänderte **Handlichkeit** nach **Rechts** ändern</span><span class="sxs-lookup"><span data-stu-id="14555-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="14555-159">Nach **verfolgte Hand Gelenk** in Hand **Gelenk** ändern</span><span class="sxs-lookup"><span data-stu-id="14555-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="14555-160">Konfigurieren Sie die Komponente **radiale Ansicht (Skript)** :</span><span class="sxs-lookup"><span data-stu-id="14555-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="14555-161">Ändern Sie die **Verweis Richtung** in **objektorientiert**, und aktivieren Sie dann das Kontrollkästchen **an Verweis Richtung ausrichten** .</span><span class="sxs-lookup"><span data-stu-id="14555-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="14555-162">Ändern Sie die **minimale Entfernung** und den **maximalen Abstand** in 0.</span><span class="sxs-lookup"><span data-stu-id="14555-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="14555-164">3. Testen des Solver der radialen Ansicht mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="14555-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="14555-165">Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben, und halten Sie dann die Leertaste gedrückt, um die Hand zu machen.</span><span class="sxs-lookup"><span data-stu-id="14555-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="14555-166">Bewegen Sie den Mauszeiger um die Hand, und klicken Sie auf die linke Maustaste, um die Hand zu drehen:</span><span class="sxs-lookup"><span data-stu-id="14555-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="14555-168">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="14555-168">Congratulations</span></span>

<span data-ttu-id="14555-169">In diesem Tutorial haben Sie gelernt, wie Sie mit den Solvers von mrtk eine Benutzeroberfläche intuitiv auf den Benutzer anwenden können.</span><span class="sxs-lookup"><span data-stu-id="14555-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="14555-170">Außerdem haben Sie erfahren, wie Sie einen Solver an ein Objekt (d. h. einen Cube) anfügen, um die nach verfolgten Hände des Benutzers zu befolgen.</span><span class="sxs-lookup"><span data-stu-id="14555-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="14555-171">Weitere Informationen zu diesen und anderen in der mrtk enthaltenen Solvers finden Sie im Handbuch zu [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="14555-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="14555-172">Nächstes Tutorial: 5. Interaktion mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="14555-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
