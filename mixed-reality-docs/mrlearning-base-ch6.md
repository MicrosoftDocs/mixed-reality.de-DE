---
title: 'Tutorials zu den ersten Schritten: 7 Erstellen einer Beispielanwendung für eine Mondlandefähre (Lunar Module)'
description: In dieser Lektion kombinieren Sie mehrere Konzepte, die Sie in früheren Lektionen kennengelernt haben, um eine einzigartige Beispielerfahrung zu schaffen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031561"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="82a87-105">7. Erstellen einer Beispielanwendung für eine Mondlandefähre (Lunar Module)</span><span class="sxs-lookup"><span data-stu-id="82a87-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="82a87-106">In diesem Tutorial werden mehrere Konzepte aus früheren Lektionen kombiniert, um eine einzigartige Beispielerfahrung zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="82a87-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="82a87-107">Sie erfahren, wie Sie eine Anwendung zur Montage von Teilen erstellen, bei der ein Benutzer mit nachverfolgten Händen Teile aufnehmen und versuchen muss, eine Mondlandefähre zu montieren.</span><span class="sxs-lookup"><span data-stu-id="82a87-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="82a87-108">Sie verwenden drückbare Schaltflächen, um Platzierungshinweise ein- und auszuschalten, die Umgebung zurückzusetzen und die Mondlandefähre in den Weltraum zu befördern.</span><span class="sxs-lookup"><span data-stu-id="82a87-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="82a87-109">In zukünftigen Tutorials können Sie auf dieser Umgebung aufbauen, einschließlich leistungsfähiger Anwendungsfälle für mehrere Benutzer, die Azure Spatial Anchors für die räumliche Ausrichtung nutzen.</span><span class="sxs-lookup"><span data-stu-id="82a87-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="82a87-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="82a87-110">Objectives</span></span>

* <span data-ttu-id="82a87-111">Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen</span><span class="sxs-lookup"><span data-stu-id="82a87-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="82a87-112">Informationen zum Umschalten von Objekten</span><span class="sxs-lookup"><span data-stu-id="82a87-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="82a87-113">Auslösen komplexer Ereignisse über drückbare Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="82a87-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="82a87-114">Verwenden der physischen Effekte und Kräfte von Starrkörpern</span><span class="sxs-lookup"><span data-stu-id="82a87-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="82a87-115">Erkunden der Verwendung von QuickInfos</span><span class="sxs-lookup"><span data-stu-id="82a87-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="82a87-116">Übersicht über die Komponenten der Mondlandefähre</span><span class="sxs-lookup"><span data-stu-id="82a87-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="82a87-117">In diesem Abschnitt erstellen Sie eine einfache Montageaufgabe, bei der das Ziel für den Benutzer darin besteht, fünf Teile, die auf dem Tisch verteilt sind, an der richtigen Stelle der Mondlandefähre zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="82a87-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="82a87-118">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="82a87-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="82a87-119">Hinzufügen des Rocket Launcher-Prefabs (Raketenstartanlage) zur Szene</span><span class="sxs-lookup"><span data-stu-id="82a87-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="82a87-120">Aktivieren der Objektmanipulation für alle Teile</span><span class="sxs-lookup"><span data-stu-id="82a87-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="82a87-121">Hinzufügen und Konfigurieren der Part Assembly Demo (Script)-Komponente (Teilemontagedemo (Skript))</span><span class="sxs-lookup"><span data-stu-id="82a87-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="82a87-122">Die Komponente „Part Assembly Demo (Script)“ ist nicht Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="82a87-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="82a87-123">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="82a87-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="82a87-124">1. Hinzufügen des Rocket Launcher-Prefabs (Raketenstartanlage) zur Szene</span><span class="sxs-lookup"><span data-stu-id="82a87-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="82a87-125">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, ziehen Sie das Prefab **RocketLauncher** in das Hierarchiefenster, um es Ihrer Szene hinzuzufügen, und platzieren Sie es dann an einem passenden Ort, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="82a87-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="82a87-126">Transformationsposition X = 1,5, Y = -0,4, Z = 0, so dass es sich rechts vom Benutzer auf Hüfthöhe befindet</span><span class="sxs-lookup"><span data-stu-id="82a87-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="82a87-127">Transformationsrotation X = 0, Y = 180, Z = 0, sodass die Hauptfeatures des Experiments dem Benutzer zugewandt sind</span><span class="sxs-lookup"><span data-stu-id="82a87-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="82a87-129">2. Aktivieren der Objektmanipulation für alle Teile</span><span class="sxs-lookup"><span data-stu-id="82a87-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="82a87-130">Suchen Sie im Hierarchiefenster das Objekt „RocketLauncher > **LunarModuleParts**“, wählen Sie alle **untergeordneten Objekte** aus, fügen Sie die **Manipulation Handler (Script)** -Komponente und die **Near Interaction Grabbable (Script)** -Komponente hinzu, und konfigurieren Sie dann Manipulation Handler (Script) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="82a87-131">Deaktivieren Sie das Kontrollkästchen **Allow Far Manipulation** (Fern-Manipulation zulassen), um nur Nah-Interaktion zuzulassen</span><span class="sxs-lookup"><span data-stu-id="82a87-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="82a87-132">Ändern Sie **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) in **Move Rotate** (Bewegen Drehen), sodass das Ändern der Größe deaktiviert ist</span><span class="sxs-lookup"><span data-stu-id="82a87-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="82a87-134">Wenn Sie eine Auffrischung zu den Schrittanleitungen zum Implementieren der Objektmanipulation benötigen, lesen Sie die Anweisungen zum [Manipulieren von 3D-Objekten](mrlearning-base-ch4.md#manipulating-3d-objects).</span><span class="sxs-lookup"><span data-stu-id="82a87-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="82a87-135">3. Hinzufügen und Konfigurieren der Part Assembly Demo (Script)-Komponente (Teilemontagedemo (Skript))</span><span class="sxs-lookup"><span data-stu-id="82a87-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="82a87-136">Fügen Sie eine **Audio Source**-Komponente (Audioquelle) hinzu, während alle untergeordneten Objekte von LunarModuleParts noch ausgewählt sind, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="82a87-137">Weisen Sie dem Feld **AudioClip** einen passenden Audioclip zu, beispielsweise „MRKT_Scale_Start“</span><span class="sxs-lookup"><span data-stu-id="82a87-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="82a87-138">Deaktivieren Sie das Kontrollkästchen **Play On Awake** (Nach Laden wiedergeben), sodass der Audioclip nach dem Laden der Szene nicht automatisch wiedergegeben wird</span><span class="sxs-lookup"><span data-stu-id="82a87-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="82a87-139">Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1, um räumliche Audiowiedergabe zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="82a87-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="82a87-141">Fügen Sie bei immer noch ausgewählten untergeordneten Objekten von LunarModuleParts die Komponente **Part Assembly Demo (Script)** hinzu:</span><span class="sxs-lookup"><span data-stu-id="82a87-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="82a87-143">Wählen Sie im Hierarchiefenster das **RoverEnclosure**-Objekt aus, und konfigurieren Sie dessen **Part Assembly Demo (Script)** -Komponente folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="82a87-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="82a87-144">Weisen Sie dem Feld **Object To Place** (Zu platzierendes Objekt) das Objekt **selbst** zu, in diesem Fall das RoverEnclosure-Objekt</span><span class="sxs-lookup"><span data-stu-id="82a87-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="82a87-145">Weisen Sie dem Feld **Location To Place** (Ort für Platzierung) das entsprechende **PlacementHints**-Objekt zu, in diesem Fall das RoverEnclosure_PlacementHint-Objekt</span><span class="sxs-lookup"><span data-stu-id="82a87-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="82a87-146">Weisen Sie dem **Tool Tip Object**-Feld (QuickInfo-Objekt) den entsprechenden **ToolTip** (QuickInfo) zu, in diesem Fall das RoverEnclosure_ToolTip-Objekt</span><span class="sxs-lookup"><span data-stu-id="82a87-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="82a87-147">Weisen Sie dem Feld **Audio Source** (Audioquelle) das Objekt **selbst** zu, in diesem Fall das RoverEnclosure-Objekt</span><span class="sxs-lookup"><span data-stu-id="82a87-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="82a87-149">**Wiederholen** Sie diese Schritte für jedes der anderen untergeordneten LunarModuleParts-Objekte, d. h. FuelTank (Treibstofftank), EnergyCell (Batteriezelle), DockingPortal (Andockportal) und ExternalSensor (externer Sensor).</span><span class="sxs-lookup"><span data-stu-id="82a87-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="82a87-150">Wenn Sie jetzt in den Spielmodus wechseln und ein 'Object To Place' (Zu platzierendes Objekt) in die Nähe seiner 'Location To Place' (Ort für die Platzierung) bewegen, werden Sie Folgendes bemerken:</span><span class="sxs-lookup"><span data-stu-id="82a87-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="82a87-151">Das Objekt rastet am Ort ein und wird dem LunarModule-Objekt untergeordnet, sodass es Teil des Mondlandemoduls wird</span><span class="sxs-lookup"><span data-stu-id="82a87-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="82a87-152">Die Audio Source des Objekts gibt den zugewiesenen Audioclip an der Position des Objekts wieder</span><span class="sxs-lookup"><span data-stu-id="82a87-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="82a87-153">Das entsprechende QuickInfo-Objekt wird ausgeblendet</span><span class="sxs-lookup"><span data-stu-id="82a87-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="82a87-155">Wenn Sie eine Auffrischung zum Verwenden der in den Editor integrierten Eingabesimulation benötigen, lesen Sie den Leitfaden [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) (Verwenden der in den Editor integrierten Handeingabesimulation zum Testen einer Szene) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="82a87-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="82a87-156">Konfigurieren der Mondlandefähre</span><span class="sxs-lookup"><span data-stu-id="82a87-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="82a87-157">In diesem Abschnitt fügen Sie der Rocket Launcher-Anwendung weitere Funktionen hinzu, damit der Benutzer Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="82a87-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="82a87-158">Mit dem Mondlandemodul interagieren</span><span class="sxs-lookup"><span data-stu-id="82a87-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="82a87-159">Das Mondlandemodul ins All starten und beim Start einen Soundeffekt wiedergeben</span><span class="sxs-lookup"><span data-stu-id="82a87-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="82a87-160">Die Anwendung zurücksetzen, sodass das Mondlandemodul und alle seine Teile wieder an ihrer ursprünglichen Position platziert werden</span><span class="sxs-lookup"><span data-stu-id="82a87-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="82a87-161">Die Platzierungshinweise ausblenden, um die Aufgabe der Teilemontage zu erschweren.</span><span class="sxs-lookup"><span data-stu-id="82a87-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="82a87-162">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="82a87-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="82a87-163">Aktivieren der Objektmanipulation</span><span class="sxs-lookup"><span data-stu-id="82a87-163">Enable object manipulation</span></span>
2. <span data-ttu-id="82a87-164">Aktivieren von physikalischen Wirkungen</span><span class="sxs-lookup"><span data-stu-id="82a87-164">Enable physics</span></span>
3. <span data-ttu-id="82a87-165">Hinzufügen einer Audioquellenkomponente</span><span class="sxs-lookup"><span data-stu-id="82a87-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="82a87-166">Hinzufügen und Konfigurieren der Launch Lunar Module (Script)-Komponente (Mondlandemodul starten (Skript))</span><span class="sxs-lookup"><span data-stu-id="82a87-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="82a87-167">Hinzufügen und Konfigurieren der Toggle Placement Hints (Script)-Komponente (Platzierungshinweise ein-/ausschalten (Skripts))</span><span class="sxs-lookup"><span data-stu-id="82a87-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="82a87-168">Die Launch Lunar Module (Script)-Komponente und die Toggle Placement Hints (Script)-Komponente sind nicht Bestandteil von MRTK.</span><span class="sxs-lookup"><span data-stu-id="82a87-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="82a87-169">Sie wurden zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="82a87-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="82a87-170">1. Aktivieren der Objektmanipulation</span><span class="sxs-lookup"><span data-stu-id="82a87-170">1. Enable object manipulation</span></span>

<span data-ttu-id="82a87-171">Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > **LunarModule**“ aus, fügen Sie die **Manipulation Handler (Script)** -Komponente und die **Near Interaction Grabbable (Script)** -Komponente hinzu, und konfigurieren Sie dann Manipulation Handler (Script) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="82a87-172">Deaktivieren Sie das Kontrollkästchen **Allow Far Manipulation** (Fern-Manipulation zulassen), um nur Nah-Interaktion zuzulassen</span><span class="sxs-lookup"><span data-stu-id="82a87-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="82a87-173">Ändern Sie **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) in Move Rotate (Bewegen Drehen), sodass das Ändern der Größe deaktiviert ist</span><span class="sxs-lookup"><span data-stu-id="82a87-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="82a87-175">2. Aktivieren von physikalischen Wirkungen</span><span class="sxs-lookup"><span data-stu-id="82a87-175">2. Enable physics</span></span>

<span data-ttu-id="82a87-176">Fügen Sie bei immer noch ausgewähltem Objekt „RocketLauncher > **LunarModule**“ eine **Rigidbody**-Komponente hinzu, und konfigurieren Sie sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="82a87-177">Deaktivieren Sie das Kontrollkästchen **Use Gravity** (Schwerkraft verwenden), damit das Mondlandemodul nicht der Schwerkraft unterliegt</span><span class="sxs-lookup"><span data-stu-id="82a87-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="82a87-178">Aktivieren Sie das **Is Kinematic**-Kontrollkästchen, sodass im Ausgangszustand keine physikalischen Kräfte auf das Mondlandemodul wirken</span><span class="sxs-lookup"><span data-stu-id="82a87-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="82a87-180">3. Hinzufügen einer Audioquellenkomponente</span><span class="sxs-lookup"><span data-stu-id="82a87-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="82a87-181">Fügen Sie eine **Audio Source**-Komponente (Audioquelle) hinzu, während das „RocketLauncher > **LunarModule**“-Objekt noch ausgewählt ist, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="82a87-182">Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1, um räumliche Audiowiedergabe zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="82a87-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="82a87-184">4. Hinzufügen und Konfigurieren der Launch Lunar Module (Script)-Komponente (Mondlandemodul starten (Skript))</span><span class="sxs-lookup"><span data-stu-id="82a87-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="82a87-185">Fügen Sie die **Launch Lunar Module (Script)** -Komponente hinzu, während das „RocketLauncher > **LunarModule**“-Objekt noch ausgewählt ist, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="82a87-186">Ändern Sie den **Thrust**-Wert (Schub), damit sich das Lunar Module beim Start ansprechend erhebt, beispielsweise auf 0,01</span><span class="sxs-lookup"><span data-stu-id="82a87-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="82a87-188">5. Hinzufügen und Konfigurieren der Toggle Placement Hints (Script)-Komponente (Platzierungshinweise ein-/ausschalten (Skripts))</span><span class="sxs-lookup"><span data-stu-id="82a87-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="82a87-189">Fügen Sie die **Toggle Placement Hints (Script)** -Komponente hinzu, während das „RocketLauncher > **LunarModule**“-Objekt noch ausgewählt ist, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a87-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="82a87-190">Legen Sie die Eigenschaft **Size** (Größe) von Game Object Array auf 5 fest</span><span class="sxs-lookup"><span data-stu-id="82a87-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="82a87-191">Weisen Sie jedes der **untergeordneten Objekte** des „RocketLauncher > LunarModule > **PlacementHints**“-Objekts einem **Element**-Feld im Game Object Array zu:</span><span class="sxs-lookup"><span data-stu-id="82a87-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="82a87-193">Konfigurieren der Startschaltfläche</span><span class="sxs-lookup"><span data-stu-id="82a87-193">Configuring the Launch button</span></span>

<span data-ttu-id="82a87-194">Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > Buttons > **LaunchButton**“ aus, erstellen Sie dann für die Komponente **Pressable Button (Script)** ein neues Ereignis **Button Pressed ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **LaunchLunarModule.StartThruster** als die auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="82a87-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="82a87-196">Falls Sie eine Auffrischung zum Implementieren von Ereignissen benötigen, lesen Sie die Anweisungen unter [Gesten für Hand-Tracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="82a87-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="82a87-197">Erstellen Sie mit immer noch ausgewähltem Objekt „RocketLauncher > Buttons > **LaunchButton**“ für die Komponente „**Pressable Button (Script)** “ ein neues **Button Pressed ()** -Ereignis, konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, definieren Sie **AudioSource.PlayOneShot** als die auszulösende Aktion, und weisen Sie dem Feld **Audio Clip** einen passenden Audioclip zu, beispielsweise den Audioclip „MRTK_Gem“:</span><span class="sxs-lookup"><span data-stu-id="82a87-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="82a87-199">Erstellen Sie mit immer noch ausgewähltem Objekt „RocketLauncher > Buttons > **LaunchButton**“ für die Komponente **Pressable Button (Script)** ein neues Ereignis **Touch End ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **LaunchLunarModule.StopThruster** als die auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="82a87-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="82a87-201">Wenn Sie jetzt in den Spielmodus wechseln und die Startschaltfläche drücken, hören Sie, wie der Audioclip wiedergegeben wird, und wenn Sie die Startschaltfläche etwa eine Sekunde oder länger gedrückt halten, sehen Sie, wie das Mondlandemodul ins All startet:</span><span class="sxs-lookup"><span data-stu-id="82a87-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="82a87-203">Konfigurieren der Schaltfläche zum Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="82a87-203">Configuring the Reset button</span></span>

<span data-ttu-id="82a87-204">Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > Buttons > **ResetButton**“ aus, erstellen Sie dann für die Komponente **Pressable Button (Script)** ein neues Ereignis **Button Pressed ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **LaunchLunarModule.ResetModule** als die auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="82a87-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="82a87-206">Erstellen Sie mit immer noch ausgewähltem Objekt „RocketLauncher > Buttons > **ResetButton**“ für die Komponente **Pressable Button (Script)** ein neues **Button Pressed ()** -Ereignis, konfigurieren Sie das **RocketLauncher**-Objekt für den Empfang des Ereignisses, definieren Sie **GameObject.BroadcastMessage** als auszulösende Aktion, und geben Sie im Nachrichtenfeld **ResetPlacement** ein:</span><span class="sxs-lookup"><span data-stu-id="82a87-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="82a87-208">Die Aktion GameObject.BroadcastMessage sendet die ResetPlacement-Nachricht vom RocketLauncher-Objekt an alle dessen untergeordneten Objekte.</span><span class="sxs-lookup"><span data-stu-id="82a87-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="82a87-209">Jedes untergeordnete Objekt, das über die ResetPlacement-Funktion verfügt, die in der Komponente „Part Assembly Demo (Script)“ definiert ist, die Sie allen untergeordneten Objekten von LunarModuleParts hinzugefügt haben, ruft die ResetPlacement-Funktion auf, die die Platzierung des betreffenden untergeordneten Objekts zurücksetzt.</span><span class="sxs-lookup"><span data-stu-id="82a87-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="82a87-210">Wenn Sie jetzt in den Spielmodus wechseln, einige Teile bewegen und/oder das Mondlandemodul starten und dann die Zurücksetzen-Schaltfläche drücken, sehen Sie, dass die Teile und/oder das Mondlandemodul auf ihre Ausgangsposition zurückgesetzt werden:</span><span class="sxs-lookup"><span data-stu-id="82a87-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="82a87-212">Konfigurieren der Placement Hints-Schaltfläche (Platzierungshinweise)</span><span class="sxs-lookup"><span data-stu-id="82a87-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="82a87-213">Wählen Sie im Hierarchiefenster das Objekt „RocketLauncher > Buttons > **HintsButton**“ aus, erstellen Sie dann für die Komponente **Pressable Button (Script)** ein neues Ereignis **Button Pressed ()** , konfigurieren Sie das **LunarModule**-Objekt für den Empfang des Ereignisses, und definieren Sie **TogglePlacementHints.ToggleGameObjects** als die auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="82a87-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="82a87-215">Wenn Sie jetzt in den Spielmodus wechseln, stellen Sie fest, dass die durchscheinenden Platzierungshinweise standardmäßig deaktiviert sind, dass Sie sie aber ein- und ausschalten können, indem Sie die Hints-Schaltfläche (Hinweise) drücken:</span><span class="sxs-lookup"><span data-stu-id="82a87-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="82a87-217">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="82a87-217">Congratulations</span></span>

<span data-ttu-id="82a87-218">Sie haben diese Anwendung vollständig konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="82a87-218">You have fully configured this application.</span></span> <span data-ttu-id="82a87-219">Jetzt ermöglicht es Ihnen Ihre Anwendung, das Mondlandemodul vollständig zu montieren, das Mondlandemodul zu starten, Hinweise umzuschalten und die Anwendung wieder auf Start zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="82a87-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
