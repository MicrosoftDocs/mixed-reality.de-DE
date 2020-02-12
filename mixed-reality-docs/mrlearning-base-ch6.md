---
title: Tutorials zu den ersten Schritten-7. Erstellen einer Beispielanwendung für ein Mond Modul
description: In dieser Lektion kombinieren Sie mehrere Konzepte, die Sie aus vorherigen Lektionen gelernt haben, um eine einzigartige Stichprobe zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129441"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="5764a-105">7. Erstellen einer Beispielanwendung für ein Mond Modul</span><span class="sxs-lookup"><span data-stu-id="5764a-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="5764a-106">In diesem Tutorial werden mehrere Konzepte aus früheren Lektionen kombiniert, um ein eindeutiges Beispiel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5764a-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="5764a-107">Sie erfahren, wie Sie eine teilassemblyanwendung erstellen, in der ein Benutzer überwachte Hände verwenden muss, um Teile zu erfassen und zu versuchen, ein Mond Modul zusammenzustellen.</span><span class="sxs-lookup"><span data-stu-id="5764a-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="5764a-108">Mithilfe von druckbaren Schaltflächen können Sie Platzierungs Hinweise ein-und ausschalten, die Leistung zurücksetzen und das Mond Modul in den Raum bringen!</span><span class="sxs-lookup"><span data-stu-id="5764a-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="5764a-109">In zukünftigen Tutorials werden Sie weiterhin auf dieser Benutzer Funktionalität aufbauen, die leistungsstarke mehr Benutzer Anwendungsfälle umfasst, die räumliche Azure-Anker für räumliche Ausrichtung nutzen.</span><span class="sxs-lookup"><span data-stu-id="5764a-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="5764a-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="5764a-110">Objectives</span></span>

* <span data-ttu-id="5764a-111">Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen</span><span class="sxs-lookup"><span data-stu-id="5764a-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="5764a-112">Informationen zum Umschalten von Objekten</span><span class="sxs-lookup"><span data-stu-id="5764a-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="5764a-113">Auslösen komplexer Ereignisse über drückbare Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="5764a-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="5764a-114">Verwenden der physischen Effekte und Kräfte von Starrkörpern</span><span class="sxs-lookup"><span data-stu-id="5764a-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="5764a-115">Erkunden der Verwendung von QuickInfos</span><span class="sxs-lookup"><span data-stu-id="5764a-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="5764a-116">Übersicht über die Komponenten von Mond Modulen</span><span class="sxs-lookup"><span data-stu-id="5764a-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="5764a-117">In diesem Abschnitt erstellen Sie eine einfache teilassemblyherausforderung, bei der das Ziel des Benutzers darin besteht, fünf Teile, die in der Tabelle verteilt sind, am richtigen Speicherort im Mond Modul zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="5764a-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="5764a-118">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="5764a-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5764a-119">Hinzufügen der Prefab für das Raketenstart Programm zur Szene</span><span class="sxs-lookup"><span data-stu-id="5764a-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="5764a-120">Aktivieren der Objekt Bearbeitung für alle Teile</span><span class="sxs-lookup"><span data-stu-id="5764a-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="5764a-121">Hinzufügen und Konfigurieren der Komponente "Part Assembly Demo (Skript)"</span><span class="sxs-lookup"><span data-stu-id="5764a-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="5764a-122">Die Komponente "Part Assembly Demo (Skript)" ist nicht Bestandteil von mrtk.</span><span class="sxs-lookup"><span data-stu-id="5764a-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="5764a-123">Es wurde mit den Assets dieses Tutorials bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="5764a-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="5764a-124">1. Fügen Sie der Szene die Prefab des Raketenstart Programms hinzu.</span><span class="sxs-lookup"><span data-stu-id="5764a-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="5764a-125">Navigieren Sie im Projektfenster zu den **Assets** > **mrtk. Tutorials. GettingStarted** > Ordner **Prefabs** > **RocketLauncher** , ziehen Sie den **RocketLauncher** -Prefab in das Hierarchie Fenster, um ihn Ihrer Szene hinzuzufügen, und positionieren Sie ihn dann an einem geeigneten Speicherort, z. b.:</span><span class="sxs-lookup"><span data-stu-id="5764a-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="5764a-126">Transformations Position X = 1,5, Y =-0,4, Z = 0, sodass Sie auf der rechten Seite des Benutzers bei der Taillenhöhe positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="5764a-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="5764a-127">Transformations Drehung X = 0, Y = 180, Z = 0, sodass die Hauptfunktionen der Benutzeroberflächen dem Benutzer ausgesetzt sind</span><span class="sxs-lookup"><span data-stu-id="5764a-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="5764a-129">2. Aktivieren Sie die Objekt Bearbeitung für alle Teile.</span><span class="sxs-lookup"><span data-stu-id="5764a-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="5764a-130">Suchen Sie im Fenster Hierarchie nach dem Objekt RocketLauncher > **lunarmoduleparts** , und wählen Sie alle untergeordneten **Objekte**aus. Fügen Sie dann die Komponente **Manipulations Handler (Skript)** und **near Interaktion grabbable (Script)** hinzu, und konfigurieren Sie dann den Manipulations Handler (Skript) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="5764a-131">Ändern von **zwei handungstyp** zum Verschieben ändern, sodass die Skalierung deaktiviert ist</span><span class="sxs-lookup"><span data-stu-id="5764a-131">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="5764a-132">Deaktivieren Sie das Kontrollkästchen " **lange Bearbeitung zulassen** ", um nur die Near-Interaktion zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="5764a-132">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="5764a-134">Eine Erinnerung, eine Schritt-für-Schritt-Anleitung zur Implementierung der Objekt Bearbeitung, finden Sie in den Anweisungen zum Bearbeiten von [3D-Objekten](mrlearning-base-ch4.md#manipulating-3d-objects) .</span><span class="sxs-lookup"><span data-stu-id="5764a-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="5764a-135">3. hinzufügen und Konfigurieren der Komponente "Part Assembly Demo (Skript)"</span><span class="sxs-lookup"><span data-stu-id="5764a-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="5764a-136">Wenn alle untergeordneten Objekte von lunarmoduleparts noch ausgewählt sind, fügen Sie eine **audioquellkomponente** hinzu, und konfigurieren Sie Sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="5764a-137">Weisen Sie dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="5764a-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="5764a-138">Deaktivieren Sie das Kontrollkästchen **Play on wacht** , sodass der Audioclip beim Laden der Szene nicht automatisch wiedergegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5764a-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="5764a-139">**Räumliche Blend** in 1 ändern, um räumliche Audiodaten zu ermöglichen</span><span class="sxs-lookup"><span data-stu-id="5764a-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="5764a-141">Wenn alle untergeordneten Objekte von lunarmoduleparts weiterhin ausgewählt sind, fügen Sie die Komponente **Part Assembly Demo (Skript)** hinzu:</span><span class="sxs-lookup"><span data-stu-id="5764a-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="5764a-143">Wählen Sie im Fenster "Hierarchie" das **roverenclosure** -Objekt aus, und konfigurieren Sie die Komponente " **Part Assembly Demo (Skript)** " wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="5764a-144">Weisen Sie das Objekt selbst, in diesem Fall das **roverenclosure** -Objekt, dem Objekt **zu platzieren** .</span><span class="sxs-lookup"><span data-stu-id="5764a-144">To the **Object To Place** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>
* <span data-ttu-id="5764a-145">Weisen Sie im Feld **Speicherort** die entsprechenden Platzhalter Objekte zu, in diesem Fall das **RoverEnclosure_PlacementHints** Objekt.</span><span class="sxs-lookup"><span data-stu-id="5764a-145">To the **Location To Place** field, assign the corresponding PlacementHints object, in this case, the **RoverEnclosure_PlacementHints** object</span></span>
* <span data-ttu-id="5764a-146">Weisen Sie im Feld QuickInfo- **Objekt** das entsprechende tooltipobject-Objekt zu, in diesem Fall das **RoverEnclosure_ToolTip** Objekt.</span><span class="sxs-lookup"><span data-stu-id="5764a-146">To the **Tool Tip Object** field, assign the corresponding ToolTipObject, in this case, the **RoverEnclosure_ToolTip** object</span></span>
* <span data-ttu-id="5764a-147">Weisen Sie das Objekt selbst (in diesem Fall das **roverenclosure** -Objekt) dem Feld **Audioquelle** zu.</span><span class="sxs-lookup"><span data-stu-id="5764a-147">To the **Audio Source** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="5764a-149">**Wiederholen** Sie diesen Schritt für jedes der anderen untergeordneten lunarmoduleparts-Objekte, z. b. fueltank, energycell, dockingportal und externalsensor.</span><span class="sxs-lookup"><span data-stu-id="5764a-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="5764a-150">Wenn Sie nun in den Spielmodus wechseln und ein ' Objekt an den Ort ' in der Nähe von ' Location to Place ' verschieben, werden Sie Folgendes bemerken:</span><span class="sxs-lookup"><span data-stu-id="5764a-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="5764a-151">Das Objekt wird an der Stelle ausgerichtet und unter dem lunarmodule-Objekt untergeordnet, sodass es Teil des mondmoduls wird.</span><span class="sxs-lookup"><span data-stu-id="5764a-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="5764a-152">Die Audioquelle des Objekts übernimmt den zugewiesenen Audioclip an der Position des Objekts.</span><span class="sxs-lookup"><span data-stu-id="5764a-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="5764a-153">Das entsprechende QuickInfo-Objekt wird ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="5764a-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="5764a-155">Eine Erinnerung zur Verwendung der in-Editor-Eingabe Simulation finden Sie unter [Verwenden der in-Editor-Hand Eingabe Simulation zum Testen eines Szenen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Handbuchs im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="5764a-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="5764a-156">Konfigurieren der Mondlandefähre</span><span class="sxs-lookup"><span data-stu-id="5764a-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="5764a-157">In diesem Abschnitt fügen Sie der Anwendung für das Raketenstart Programm zusätzliche Features hinzu, damit der Benutzer folgende Aktionen ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="5764a-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="5764a-158">Interagieren mit dem Lunar-Modul</span><span class="sxs-lookup"><span data-stu-id="5764a-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="5764a-159">Starten Sie das Mond Modul, und geben Sie einen Sound wieder, wenn es gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="5764a-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="5764a-160">Setzen Sie die Anwendung zurück, damit das Mond Modul und der gesamte Teil wieder an der ursprünglichen Position abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="5764a-160">Reset the application so the Lunar Module and all the part are placed back to their original position</span></span>
* <span data-ttu-id="5764a-161">Blenden Sie die Platzierungs Hinweise aus, um die Herausforderung der Teile Assembly zu erschweren.</span><span class="sxs-lookup"><span data-stu-id="5764a-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="5764a-162">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="5764a-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5764a-163">Objekt Bearbeitung aktivieren</span><span class="sxs-lookup"><span data-stu-id="5764a-163">Enable object manipulation</span></span>
2. <span data-ttu-id="5764a-164">Aktivieren der Physik</span><span class="sxs-lookup"><span data-stu-id="5764a-164">Enable physics</span></span>
3. <span data-ttu-id="5764a-165">Hinzufügen einer audioquellkomponente</span><span class="sxs-lookup"><span data-stu-id="5764a-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="5764a-166">Hinzufügen und Konfigurieren der Komponente "Launch Lunar Module (Script)"</span><span class="sxs-lookup"><span data-stu-id="5764a-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="5764a-167">Hinzufügen und Konfigurieren der Komponente zum Umschalten der Platzierungs Hinweise (Skript)</span><span class="sxs-lookup"><span data-stu-id="5764a-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="5764a-168">Die Komponente Launch Lunar Module (Script) und die Funktion zum Umschalten der Platzierungs Hinweise (Skript) sind nicht Teil von mrtk.</span><span class="sxs-lookup"><span data-stu-id="5764a-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="5764a-169">Sie wurden mit den Assets dieses Tutorials bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="5764a-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="5764a-170">1. Aktivieren der Objekt Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="5764a-170">1. Enable object manipulation</span></span>

<span data-ttu-id="5764a-171">Wählen Sie im Fenster Hierarchie das Objekt RocketLauncher > **lunarmodule** aus, fügen Sie die Komponente **Manipulations Handler (Skript)** und **near Interaktion grabbable (Skript)** hinzu, und konfigurieren Sie dann den Manipulations Handler (Skript) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="5764a-172">Ändern von **zwei handungstyp** zum Verschieben ändern, sodass die Skalierung deaktiviert ist</span><span class="sxs-lookup"><span data-stu-id="5764a-172">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="5764a-173">Deaktivieren Sie das Kontrollkästchen " **lange Bearbeitung zulassen** ", um nur die Near-Interaktion zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="5764a-173">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="5764a-175">2. Aktivieren der Physik</span><span class="sxs-lookup"><span data-stu-id="5764a-175">2. Enable physics</span></span>

<span data-ttu-id="5764a-176">Wenn das RocketLauncher > **lunarmodule** -Objekt noch ausgewählt ist, fügen Sie eine Rigidbody-Komponente hinzu, und konfigurieren Sie Sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-176">With the RocketLauncher > **LunarModule** object still selected, add a Rigidbody component and then configure it as follows:</span></span>

* <span data-ttu-id="5764a-177">Deaktivieren Sie das Kontrollkästchen **use Gravity** , damit das Lunar-Modul nicht von der Schwerkraft betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="5764a-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="5764a-178">Aktivieren Sie das Kontrollkästchen **ist Kinematic** , damit das Mond Modul anfänglich nicht von Physic-Kräften betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="5764a-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="5764a-180">3. Hinzufügen einer audioquellkomponente</span><span class="sxs-lookup"><span data-stu-id="5764a-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="5764a-181">Wenn das Objekt RocketLauncher > **lunarmodule** noch ausgewählt ist, fügen Sie eine **audioquellkomponente** hinzu, und konfigurieren Sie Sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="5764a-182">Ändern von **Spatial Blend** in 1 zum Aktivieren räumlicher Audiodaten</span><span class="sxs-lookup"><span data-stu-id="5764a-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="5764a-184">4. hinzufügen und Konfigurieren der Komponente "Launch Lunar Module (Script)"</span><span class="sxs-lookup"><span data-stu-id="5764a-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="5764a-185">Wenn das Objekt RocketLauncher > **lunarmodule** noch ausgewählt ist, fügen Sie die Komponente **Launch Lunar Module (Script)** hinzu, und konfigurieren Sie Sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="5764a-186">Ändern **Sie** den Werte Wert, damit das Mond Modul beim Start ordnungsgemäß gestartet wird, z. b. in 0,01</span><span class="sxs-lookup"><span data-stu-id="5764a-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="5764a-188">5. hinzufügen und Konfigurieren der Komponente zum Umschalten der Platzierungs Hinweise (Skript)</span><span class="sxs-lookup"><span data-stu-id="5764a-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="5764a-189">Wenn das Objekt RocketLauncher > **lunarmodule** noch ausgewählt ist, fügen Sie die Komponente zum **Umschalten der Platzierungs Hinweise (Skript)** hinzu, und konfigurieren Sie Sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5764a-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="5764a-190">Legen Sie die Eigenschaft "Spielobjekt Array **Größe** " auf 5 fest.</span><span class="sxs-lookup"><span data-stu-id="5764a-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="5764a-191">Weisen Sie jedes der untergeordneten **Objekte** des **placementhints** -Objekts dem **Element** Feld im Spielobjekt Array zu:</span><span class="sxs-lookup"><span data-stu-id="5764a-191">Assign each of the **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="5764a-193">Konfigurieren der Schaltfläche "starten"</span><span class="sxs-lookup"><span data-stu-id="5764a-193">Configuring the Launch button</span></span>

<span data-ttu-id="5764a-194">Wählen Sie im Fenster Hierarchie die > Schaltflächen RocketLauncher > **launchbutton** -Objekt aus, und erstellen Sie dann auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Button-Ereignis **()** , und konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, und erstellen Sie **launchlunarmodule. startthruster** als auszulösenden Aktion</span><span class="sxs-lookup"><span data-stu-id="5764a-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="5764a-196">Eine Erinnerung, wie Ereignisse implementiert werden können, finden Sie in den Anweisungen [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="5764a-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="5764a-197">Wenn die Schaltflächen RocketLauncher > > **launchbutton** -Objekt noch ausgewählt ist, erstellen Sie auf der **Schaltfläche "Druck Bare Schaltfläche (Skript)** " ein neues Button-Ereignis **()** , konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, definieren Sie **audiosource. playoneshot** als auszulösenden Aktion, und weisen Sie dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. den MRTK_Gem Audioclip:</span><span class="sxs-lookup"><span data-stu-id="5764a-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="5764a-199">Wenn die Schaltflächen RocketLauncher > > **launchbutton** -Objekt noch ausgewählt ist, erstellen Sie auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Fingerabdruck Ereignis **()** , konfigurieren Sie das **lunarmodule** -Objekt für den Empfang des Ereignisses, und definieren Sie **launchlunarmodule. stopthruster** als Aktion, die ausgelöst werden soll:</span><span class="sxs-lookup"><span data-stu-id="5764a-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch Ended ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="5764a-201">Wenn Sie jetzt den Spielmodus eingeben und auf die Schaltfläche "Start" klicken, wird der Audioclip abgespielt. Wenn Sie die Schaltfläche "Start" für ungefähr eine Sekunde oder länger gedrückt halten, sehen Sie, dass das Mond Modul in den Speicherplatz wechselt:</span><span class="sxs-lookup"><span data-stu-id="5764a-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="5764a-203">Konfigurieren der Schaltfläche Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="5764a-203">Configuring the Reset button</span></span>

<span data-ttu-id="5764a-204">Wählen Sie im Fenster Hierarchie die Schaltflächen RocketLauncher > > **ResetButton** -Objekt aus, und erstellen Sie dann auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Button-Ereignis **()** , und konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen. Legen Sie **launchlunarmodule. resetmodule als auszulösenden** Aktion fest</span><span class="sxs-lookup"><span data-stu-id="5764a-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="5764a-206">Wenn die Schaltflächen RocketLauncher > **> ResetButton** -Objekt noch ausgewählt ist, erstellen Sie auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Button-Ereignis **()** , konfigurieren Sie das " **RocketLauncher** "-Objekt, um das Ereignis zu empfangen, legen Sie " **gameobject. broadcastmessage** " als auszulösenden **Aktion** fest</span><span class="sxs-lookup"><span data-stu-id="5764a-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="5764a-208">Die Aktion "gameobject. broadcastmessage" sendet die resetplacement-Nachricht vom "RocketLauncher"-Objekt an das gesamte untergeordnete Objekt.</span><span class="sxs-lookup"><span data-stu-id="5764a-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="5764a-209">Jedes untergeordnete Objekt, das über die resetplacement-Funktion verfügt, die in der Komponente Part Assembly Demo (Skript) definiert ist, die Sie allen untergeordneten Objekten von lunarmoduleparts hinzugefügt haben, ruft die resetplacement-Funktion auf, die die Platzierung des untergeordneten Objekts zurücksetzt.</span><span class="sxs-lookup"><span data-stu-id="5764a-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="5764a-210">Wenn Sie jetzt den Spielmodus eingeben und auf die Schaltfläche "Zurücksetzen" klicken, werden Sie sehen, dass der Audioclip wiedergegeben wird, und dass das Mond Modul in den Bereich "</span><span class="sxs-lookup"><span data-stu-id="5764a-210">If you now enter Game mode and press the Reset button you will hear the audio clip being played and see the Lunar Module being launched into space:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="5764a-212">Konfigurieren der Schaltfläche Platzierungs Hinweise</span><span class="sxs-lookup"><span data-stu-id="5764a-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="5764a-213">Wählen Sie im Fenster Hierarchie die Schaltflächen RocketLauncher > > **hinzbutton** -Objekt aus, und erstellen Sie dann auf der **Schaltfläche mit der druckbaren Schaltfläche (Skript)** ein neues Ereignis mit der Tastendruck **Taste ()** , konfigurieren Sie das **lunarmodule** -Objekt, um das Ereignis zu empfangen, und definieren Sie " **deggleplacementhints. Token.**</span><span class="sxs-lookup"><span data-stu-id="5764a-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** the action to be triggered:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="5764a-215">Wenn Sie jetzt den Spielmodus eingeben, werden Sie feststellen, dass die über sichtigen Platzierungs Hinweise standardmäßig deaktiviert sind. Sie können Sie jedoch durch Drücken der Schaltfläche "Hinweise" aktivieren und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="5764a-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning: Basis](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="5764a-217">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="5764a-217">Congratulations</span></span>

<span data-ttu-id="5764a-218">Sie haben diese Anwendung vollständig konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="5764a-218">You have fully configured this application.</span></span> <span data-ttu-id="5764a-219">Nun können Benutzer mit Ihrer Anwendung das Mond Modul vollständig Assemblieren, das Mond Modul starten, Hinweise umschalten und die Anwendung zurücksetzen, damit Sie erneut gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="5764a-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
