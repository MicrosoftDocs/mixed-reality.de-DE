---
title: 2. Initialisieren des Projekts und der ersten Anwendung
description: Teil 2 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: e8f03a87ec6b92e4c62cf3f88f519146254e7387
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330345"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="4785b-104">2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="4785b-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="4785b-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4785b-105">Overview</span></span>

<span data-ttu-id="4785b-106">In diesem ersten Tutorial beginnen Sie mit einer neuen Unreal-Anwendung für HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4785b-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="4785b-107">Dies beinhaltet das Hinzufügen des HoloLens-Plug-Ins, das Erstellen und Einleuchten eines Levels und das Bestücken des Levels mit einem Spielbrett und einer Schachfigur.</span><span class="sxs-lookup"><span data-stu-id="4785b-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="4785b-108">Sie verwenden vorgefertigte Medienobjekte für die 3D-Schachfigur und Objektmaterialien, Sie brauchen also nichts von Grund auf neu zu modellieren.</span><span class="sxs-lookup"><span data-stu-id="4785b-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="4785b-109">Am Ende dieses Tutorials verfügen Sie über einen leeren Zeichenbereich, der für Mixed Reality bereit ist.</span><span class="sxs-lookup"><span data-stu-id="4785b-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="4785b-110">Bevor Sie fortfahren, stellen Sie sicher, dass alle auf der Seite [Erste Schritte](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) genannten Voraussetzungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="4785b-110">Before continuing, make sure you have all the prerequisite from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="4785b-111">Ziele</span><span class="sxs-lookup"><span data-stu-id="4785b-111">Objectives</span></span>
* <span data-ttu-id="4785b-112">Konfigurieren eines Unreal-Projekt für die HoloLens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="4785b-112">Configuring an Unreal projet for HoloLens development</span></span>
* <span data-ttu-id="4785b-113">Importieren von Medienobjekten und Einrichten einer Szene</span><span class="sxs-lookup"><span data-stu-id="4785b-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="4785b-114">Erstellen von Akteuren und Ereignissen auf Skriptebene mithilfe von Blaupausen</span><span class="sxs-lookup"><span data-stu-id="4785b-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="4785b-115">Erstellen eines neuen Unreal-Projekts</span><span class="sxs-lookup"><span data-stu-id="4785b-115">Creating a new Unreal project</span></span>
<span data-ttu-id="4785b-116">Als erstes benötigen Sie ein Projekt, mit dem Sie arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="4785b-116">The first thing you need is a project to work with.</span></span>

1. <span data-ttu-id="4785b-117">Starten der Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="4785b-117">Launch Unreal Engine</span></span>

2. <span data-ttu-id="4785b-118">Wählen Sie unter **New Project Categories** (Kategorien für neues Projekt) die Option **Games** (Spiele) aus, und klicken Sie auf **Next** (Weiter).</span><span class="sxs-lookup"><span data-stu-id="4785b-118">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Wählen Sie die Projektvorlage „Games“ (Spiele) aus.](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="4785b-120">Wählen Sie die **Leere** Vorlage aus, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="4785b-120">Select the **Blank** Template and click **Next**.</span></span> 

![Auswählen einer leeren Vorlage](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="4785b-122">Legen Sie **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Skalierbares 3D oder 2D, Mobilgerät/Tablet) und **No Starter Content** (Keine Startinhalte) als Ihre **Projekteinstellungen** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-122">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="4785b-123">Wählen Sie einen Speicherort aus, und klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="4785b-123">Choose a save location and click **Create Project**.</span></span> 

![Anfängliche Projekteinstellungen](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="4785b-125">Das Projekt sollte automatisch im Unreal Editor geöffnet werden, und damit sind Sie für den nächsten Abschnitt bereit.</span><span class="sxs-lookup"><span data-stu-id="4785b-125">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="4785b-126">Aktivieren der erforderlichen Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="4785b-126">Enabling required plugins</span></span>
<span data-ttu-id="4785b-127">Bevor Sie mit dem Hinzufügen von Objekten zur Szene beginnen, müssen Sie zwei Plug-Ins aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4785b-127">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="4785b-128">Öffnen Sie **Edit > Plugins** (Bearbeiten > Plug-Ins), und wählen Sie in der Liste der integrierten Optionen **Augmented Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="4785b-128">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="4785b-129">Scrollen Sie nach unten zu **HoloLens**, und aktivieren Sie **Enabled** (Aktiviert).</span><span class="sxs-lookup"><span data-stu-id="4785b-129">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Aktivieren der HoloLens-Plugins](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="4785b-131">Wählen Sie in der Liste der integrierten Optionen **Virtual Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="4785b-131">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="4785b-132">Scrollen Sie nach unten zu **Microsoft Windows Mixed Reality**, aktivieren Sie **Enabled** (Aktiviert), und starten Sie den Editor neu.</span><span class="sxs-lookup"><span data-stu-id="4785b-132">Scroll down to **Microsoft Windows Mixed Reality**., check **Enabled**, and restart your editor.</span></span> 

![Aktivieren des Windows Mixed Reality-Plug-Ins](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="4785b-134">Beide Plug-Ins werden für die Entwicklung für HoloLens 2 benötigt.</span><span class="sxs-lookup"><span data-stu-id="4785b-134">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="4785b-135">Nachdem dies erledigt ist, ist Ihr leeres Level jetzt bereit, belebt zu werden.</span><span class="sxs-lookup"><span data-stu-id="4785b-135">With that done you're empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="4785b-136">Erstellen eines Levels</span><span class="sxs-lookup"><span data-stu-id="4785b-136">Creating a level</span></span>
<span data-ttu-id="4785b-137">Ihre nächste Aufgabe besteht darin, ein einfaches Player-Setup mit einem Startpunkt und einem Würfel als Referenz und Maßstab zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4785b-137">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="4785b-138">Wählen Sie **File > New Level** (Datei > Neues Level) und dann **Empty Level** (Leeres Level) aus.</span><span class="sxs-lookup"><span data-stu-id="4785b-138">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="4785b-139">Die Standardszene im Viewport sollte nun leer sein.</span><span class="sxs-lookup"><span data-stu-id="4785b-139">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="4785b-140">Wählen Sie auf der Registerkarte **Modes** (Modi) **Basic** (Einfach) aus, und ziehen Sie **PlayerStart** auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="4785b-140">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="4785b-141">Legen Sie auf der Registerkarte **Details** **Location** (Position) auf **X = 0**, **Y = 0** und **Z = 0** fest. Dadurch wird der Benutzer beim Start der App in der Mitte der Szene platziert.</span><span class="sxs-lookup"><span data-stu-id="4785b-141">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![Viewport mit „PlayerStart“](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="4785b-143">Ziehen Sie einen **Würfel** von der Registerkarte **Basic** (Einfach) auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="4785b-143">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="4785b-144">Legen Sie **Location** (Position) auf **X = 50**, **Y = 0** und **Z = 0** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-144">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="4785b-145">Dadurch wird der Würfel beim Start 50 cm vom Spieler entfernt platziert.</span><span class="sxs-lookup"><span data-stu-id="4785b-145">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="4785b-146">Ändern Sie **Scale** (Maßstab) in **X = 0,2**, **Y = 0,2** und **Z = 0,2**, um den Würfel zu verkleinern.</span><span class="sxs-lookup"><span data-stu-id="4785b-146">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="4785b-147">Sie können den Würfel erst sehen, wenn Sie Ihrer Szene eine Lichtquelle hinzufügen, und das ist Ihre letzte Aufgabe vor dem Testen der Szene.</span><span class="sxs-lookup"><span data-stu-id="4785b-147">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="4785b-148">Wechseln Sie im Bereich **Modes** (Modi) zur Registerkarte **Lights** (Lichtquellen), und ziehen Sie ein **Directional Light** (Gerichtetes Licht) auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="4785b-148">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="4785b-149">Positionieren Sie das Licht oberhalb von **PlayerStart**, sodass Sie es sehen können.</span><span class="sxs-lookup"><span data-stu-id="4785b-149">Position the light above **PlayerStart** so you can see it.</span></span>

![Viewport mit hinzugefügtem Licht](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="4785b-151">Navigieren Sie zu **File > Save Current** (Datei > Aktuelle speichern), benennen Sie Ihr Level **Main** (Hauptlevel), und klicken Sie auf **Save** (Speichern).</span><span class="sxs-lookup"><span data-stu-id="4785b-151">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="4785b-152">Nachdem die Szene jetzt festgelegt ist, drücken Sie auf **Play** (Wiedergabe) in der Symbolleiste, um den Würfel in Aktion zu sehen!</span><span class="sxs-lookup"><span data-stu-id="4785b-152">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="4785b-153">Wenn Sie Ihre Arbeit genügend gewürdigt haben, drücken Sie **Esc**, um die Anwendung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="4785b-153">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Ein Würfel im Viewport](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="4785b-155">Nachdem die Szene nun eingerichtet ist, können Sie damit beginnen, das Schachbrett und die Schachfigur hinzuzufügen, um die Anwendungsumgebung abzurunden.</span><span class="sxs-lookup"><span data-stu-id="4785b-155">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="4785b-156">Importieren von Medienobjekten</span><span class="sxs-lookup"><span data-stu-id="4785b-156">Importing assets</span></span>
<span data-ttu-id="4785b-157">Die Szene sieht momentan etwas leer aus, aber das beheben Sie, indem Sie die vorgefertigten Medienobjekte in das Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="4785b-157">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="4785b-158">Laden Sie den Medienobjektordner von [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) herunter, und entpacken Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="4785b-158">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="4785b-159">Klicken Sie im **Inhaltsbrowser** auf **Add New > New Folder** (Neu hinzufügen > Neuer Ordner), und benennen Sie ihn **ChessAssets** (Schachobjekte).</span><span class="sxs-lookup"><span data-stu-id="4785b-159">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="4785b-160">Doppelklicken Sie auf den neuen Ordner – dies ist der Ort, in den Sie die 3D-Medienobjekte importieren.</span><span class="sxs-lookup"><span data-stu-id="4785b-160">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![Anzeigen oder Ausblenden des Quellenbereichs](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="4785b-162">Klicken Sie im **Inhaltsbrowser**auf **Importieren**, wählen Sie im Ordner mit den entpackten Medienobjekten alle Elemente aus, und klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="4785b-162">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="4785b-163">Dieser Ordner enthält die Gittermodelle der 3D-Objekte für das Schachbrett und Teile im FBX-Format sowie Strukturschemas im TGA-Format, die Sie für Materialien verwenden.</span><span class="sxs-lookup"><span data-stu-id="4785b-163">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="4785b-164">Wenn das Fenster mit den FBX-Importoptionen eingeblendet wird, klappen Sie den Abschnitt **Material** auf, und ändern Sie die **Material Import Method** (Methode für den Materialimport) in **Do Not Create Material** (Kein Material erstellen).</span><span class="sxs-lookup"><span data-stu-id="4785b-164">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="4785b-165">Klicken Sie auf **Import All** (Alle importieren).</span><span class="sxs-lookup"><span data-stu-id="4785b-165">Click **Import All**.</span></span>

![FBX-Importoptionen](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="4785b-167">Mehr müssen Sie für die Medienobjekte nicht unternehmen.</span><span class="sxs-lookup"><span data-stu-id="4785b-167">That's all you need to do for the assets.</span></span> <span data-ttu-id="4785b-168">In der nächsten Reihe von Aufgaben befassen Sie sich mit dem Erstellen der Bausteine der Anwendung mithilfe von Blaupausen.</span><span class="sxs-lookup"><span data-stu-id="4785b-168">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="4785b-169">Hinzufügen von Blaupausen</span><span class="sxs-lookup"><span data-stu-id="4785b-169">Adding blueprints</span></span>

1. <span data-ttu-id="4785b-170">Klicken Sie im **Inhaltsbrowser** auf **Add New > New Folder** (Neu hinzufügen > Neuer Ordner), und benennen Sie ihn **Content Browser** (Inhaltsbrowser).</span><span class="sxs-lookup"><span data-stu-id="4785b-170">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="4785b-171">Falls Sie [Blaupausen](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) noch nicht kennen – bei ihnen handelt es sich um spezielle Medienobjekte, die eine knotenbasierte Oberfläche bieten, über die neue Arten von Akteuren und Ereignissen auf der Skriptebene erstellt werden können.</span><span class="sxs-lookup"><span data-stu-id="4785b-171">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="4785b-172">Doppelklicken Sie auf den Ordner **Blaupausen**, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Blueprint Class** (Blaupausenklasse) aus.</span><span class="sxs-lookup"><span data-stu-id="4785b-172">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="4785b-173">Wählen Sie **Actor** (Akteur) aus, und benennen Sie die Blaupause **Board** (Brett).</span><span class="sxs-lookup"><span data-stu-id="4785b-173">Select **Actor** and name the blueprint **Board**.</span></span> 

![Auswählen einer übergeordneten Klasse für Ihre Blaupause](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="4785b-175">Die neue **Board**-Blaupause wird nun im Ordner **Blueprints** (Blaupausen) angezeigt, wie im folgenden Screenshot zu sehen.</span><span class="sxs-lookup"><span data-stu-id="4785b-175">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Die neue Blaupause „Board“](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="4785b-177">Sie sind jetzt bereit, den erstellten Objekten Materialien hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4785b-177">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="4785b-178">Arbeiten mit Materialien</span><span class="sxs-lookup"><span data-stu-id="4785b-178">Working with materials</span></span>
<span data-ttu-id="4785b-179">Die Objekte, die Sie erstellt haben, sind standardgrau, was visuell nicht viel hermacht.</span><span class="sxs-lookup"><span data-stu-id="4785b-179">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="4785b-180">Das Hinzufügen von Materialien und Gittermodellen zu Ihren Objekten ist der letzte Satz von Aufgaben in diesem Tutorial.</span><span class="sxs-lookup"><span data-stu-id="4785b-180">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="4785b-181">Doppelklicken Sie auf **Board**, um den Blaupausen-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="4785b-181">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="4785b-182">Klicken Sie im Bereich **Components** (Komponenten) auf **Add Component > Scene** (Komponente hinzufügen > Szene), und benennen Sie sie **Root** (Stamm).</span><span class="sxs-lookup"><span data-stu-id="4785b-182">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="4785b-183">Beachten Sie, dass **Root** im Screenshot unten als untergeordnetes Element von **DefaultSceneRoot** dargestellt ist:</span><span class="sxs-lookup"><span data-stu-id="4785b-183">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Ersetzen des Stamms](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="4785b-185">Klicken Sie, und ziehen Sie **Root** auf **DefaultSceneRoot**, um es zu ersetzen und die Kugel im Viewport zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="4785b-185">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Ersetzen des Stamms](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="4785b-187">Klicken Sie im Bereich **Components** (Komponenten) auf **Add Component > Static Mesh** (Komponente hinzufügen > Statisches Gittermodell), und benennen Sie es **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="4785b-187">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="4785b-188">Es wird als untergeordnetes Objekt unter **Root** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4785b-188">It will appear as a child object under **Root**.</span></span>

![Hinzufügen eines statischen Gitters](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="4785b-190">Klicken Sie auf **SM_Board**, scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Static Mesh** (Statisches Gittermodell), und wählen Sie in der Dropdownliste **ChessBoard** aus.</span><span class="sxs-lookup"><span data-stu-id="4785b-190">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Das Schachbrettgitter im Viewport](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="4785b-192">Klappen Sie, wiederum im Bereich **Details** den Abschnitt **Materials** (Materialien) auf, und klicken Sie in der Dropdownliste auf **Create New Asset > Material** (Neues Medienobjekt erstellen > Material).</span><span class="sxs-lookup"><span data-stu-id="4785b-192">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="4785b-193">Benennen Sie das Material **M_ChessBoard**, und speichern Sie es im Ordner **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="4785b-193">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Erstellen eines neuen Materials](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="4785b-195">Doppelklicken Sie auf das Bild des Materials **M_ChessBoard**, um den Material-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="4785b-195">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Geöffneter Material-Editor](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="4785b-197">Klicken Sie im Material-Editor mit der rechten Maustaste, und suchen Sie nach **Texture Sample** (Texturbeispiel).</span><span class="sxs-lookup"><span data-stu-id="4785b-197">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="4785b-198">Klappen Sie im Bereich **Details** den Abschnitt **Material Expression Texture Base** (Texturbasis für Materialausdruck) auf, und legen Sie **Texture** (Textur) auf **ChessBoard_Albedo** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-198">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="4785b-199">Ziehen Sie den **RGB**-Ausgabepin auf den Basisfarbpin von **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="4785b-199">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Festlegen der Basisfarbe](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="4785b-201">Wiederholen Sie den vorherigen Schritt, um vier weitere Knoten **Texture Sample** (Texturbeispiel) mit den folgenden Einstellungen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="4785b-201">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="4785b-202">Legen Sie **Texture** (Textur) auf **ChessBoard_AO** fest, und verknüpfen Sie **RGB** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung).</span><span class="sxs-lookup"><span data-stu-id="4785b-202">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="4785b-203">Legen Sie **Texture** (Textur) auf **ChessBoard_Metal** fest, und verknüpfen Sie **RGB** mit dem Pin **Metallic** (Metallisch).</span><span class="sxs-lookup"><span data-stu-id="4785b-203">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="4785b-204">Legen Sie **Texture** (Textur) auf **ChessBoard_Normal** fest, und verknüpfen Sie **RGB** mit dem Pin **Normal**.</span><span class="sxs-lookup"><span data-stu-id="4785b-204">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="4785b-205">Legen Sie **Texture** (Textur) auf **ChessBoard_Rough** fest, und verknüpfen Sie **RGB** mit dem Pin **Roughness** (Rauheit).</span><span class="sxs-lookup"><span data-stu-id="4785b-205">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="4785b-206">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="4785b-206">Click **Save**.</span></span> 

![Verbinden der restlichen Texturen](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="4785b-208">Vergewissern Sie sich, dass Ihre Materialeinrichtung wie der Screenshot oben aussieht, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="4785b-208">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="4785b-209">Auffüllen der Szene</span><span class="sxs-lookup"><span data-stu-id="4785b-209">Populating the scene</span></span>
<span data-ttu-id="4785b-210">Wenn Sie zur Blaupause **Board** (Brett) zurückkehren, sehen Sie, dass Ihr soeben erstelltes Material übernommen wurde.</span><span class="sxs-lookup"><span data-stu-id="4785b-210">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="4785b-211">Jetzt müssen Sie nur noch die Szene einrichten!</span><span class="sxs-lookup"><span data-stu-id="4785b-211">All that's left is setting up the scene!</span></span> <span data-ttu-id="4785b-212">Ändern Sie zunächst die folgenden Eigenschaften, um sicherzustellen, dass das Brett eine sinnvolle Größe aufweist und in richtigen Winkel in der Szene platziert wird:</span><span class="sxs-lookup"><span data-stu-id="4785b-212">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="4785b-213">Legen Sie **Scale** (Maßstab) auf **(0,05, 0,05, 0,05)** und **Z Rotation** (Z-Drehung) auf **90** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-213">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="4785b-214">Klicken Sie in der oberen Symbolleiste auf **Compile** (Kompilieren), dann auf **Save** (Speichern), und kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="4785b-214">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Schachbrett mit angewendetem Material](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="4785b-216">Klicken Sie mit der rechten Maustaste auf **Cube > Edit > Delete** (Würfel > Bearbeiten > Löschen), und ziehen Sie **Board** (Brett) aus dem **Content Browser** (Inhaltsbrowser) in den Viewport.</span><span class="sxs-lookup"><span data-stu-id="4785b-216">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="4785b-217">Legen Sie **Location** (Position) auf **X = 80**, **Y = 0** und **Z = -20** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-217">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="4785b-218">Klicken Sie auf die Schaltfläche **Play** (Wiedergabe), um das neue Brett im Level anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4785b-218">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="4785b-219">Drücken Sie **ESC**, um zum Editor zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="4785b-219">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="4785b-220">Führen Sie nun die folgenden Schritte aus, um eine Schachfigur zu erstellen, so wie Sie das Brett erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="4785b-220">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="4785b-221">Wechseln Sie zum Ordner **Blueprints** (Blaupausen), klicken Sie mit der rechten Maustaste auf **Blueprint Class** (Blaupausenklasse), wählen Sie sie aus, und wählen Sie dann **Actor** (Akteur) aus.</span><span class="sxs-lookup"><span data-stu-id="4785b-221">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="4785b-222">Nennen Sie den Akteur **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="4785b-222">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="4785b-223">Doppelklicken Sie auf **WhiteKing**, um ihn im Blaupausen-Editor zu öffnen, klicken Sie auf **Add Component > Scene** (Komponente hinzufügen > Szene), und benennen Sie sie **Root** (Stamm).</span><span class="sxs-lookup"><span data-stu-id="4785b-223">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="4785b-224">Ziehen Sie **Root** auf **DefaultSceneRoot**, um sie zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="4785b-224">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="4785b-225">Klicken Sie auf **Add Component > Static Mesh** (Komponente hinzufügen > Statisches Gittermodell), und benennen Sie es **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="4785b-225">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="4785b-226">Legen Sie im Detailbereich die Option **Static Mesh** (Statisches Gittermodell) auf **Chess_King** und die Option **Material** auf ein neues Material mit dem Namen **M_ChessWhite** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-226">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="4785b-227">Öffnen Sie **M_ChessWhite** im Material-Editor, und verbinden Sie die folgenden **Texture Sample**-Knoten (Texturbeispiel) in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="4785b-227">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="4785b-228">Legen Sie **Texture** (Textur) auf **ChessWhite_AO** fest, und verknüpfen Sie **RGB** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung).</span><span class="sxs-lookup"><span data-stu-id="4785b-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="4785b-229">Legen Sie **Texture** (Textur) auf **ChessWihte_Metal** fest, und verknüpfen Sie **RGB** mit dem Pin **Metallic** (Metallisch).</span><span class="sxs-lookup"><span data-stu-id="4785b-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="4785b-230">Legen Sie **Texture** (Textur) auf **ChessWhite_Normal** fest, und verknüpfen Sie **RGB** mit dem Stift **Normal**.</span><span class="sxs-lookup"><span data-stu-id="4785b-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="4785b-231">Legen Sie **Texture** (Textur) auf **ChessWhite_Rough** fest, und verknüpfen Sie **RGB** mit dem Pin **Roughness** (Rauheit).</span><span class="sxs-lookup"><span data-stu-id="4785b-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="4785b-232">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="4785b-232">Click **Save**.</span></span> 

<span data-ttu-id="4785b-233">Ihr **M_ChessKing**-Material sollte wie die folgende Abbildung aussehen, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="4785b-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Erstellen des Materials für den König (Schachfigur)](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="4785b-235">Sie haben es fast geschafft, wir müssen jetzt nur noch der Szene die neue Schachfigur hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4785b-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="4785b-236">Öffnen Sie die **WhiteKing**-Blaupause, ändern Sie den **Scale** (Maßstab) in **(0,05, 0,05, 0,05)** und **Z Rotation** (Z_Drehung) in **90**.</span><span class="sxs-lookup"><span data-stu-id="4785b-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="4785b-237">Kompilieren und speichern Sie die Blaupause, und kehren Sie anschließend wieder zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="4785b-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="4785b-238">Ziehen Sie **WhiteKing** in den Viewport, wechseln Sie zum **World Outliner** (Gliederungs-Editor), und ziehen Sie **WhiteKing** auf **Board**, um ihn zum untergeordneten Objekt zu machen.</span><span class="sxs-lookup"><span data-stu-id="4785b-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Gliederungs-Editor](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="4785b-240">Legen Sie im Bereich **Details** unter **Transform** (Transformieren) die **Location** (Position) von **WhiteKing** auf **X = -26**, **Y = 4** und **Z = 0** fest.</span><span class="sxs-lookup"><span data-stu-id="4785b-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="4785b-241">Das wäre geschafft!</span><span class="sxs-lookup"><span data-stu-id="4785b-241">That's a wrap!</span></span> <span data-ttu-id="4785b-242">Klicken Sie auf **Play** (Wiedergabe), um Ihr aufgefülltes Level in Aktion zu sehen, und drücken Sie **Esc**, wenn Sie die Szene beenden möchten.</span><span class="sxs-lookup"><span data-stu-id="4785b-242">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="4785b-243">In diesem Tutorial wurde das Erstellen eines einfachen Projekts ausführlich erläutert, aber Ihr Projekt ist für die Umstellung auf den nächsten Teil der Reihe bereit: Einrichten für Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4785b-243">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="4785b-244">Nächster Abschnitt: 3. Einrichten Ihres Projekts für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4785b-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)