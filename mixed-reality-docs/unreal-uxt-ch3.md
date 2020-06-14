---
title: 3. Einrichten Ihres Projekts für Mixed Reality
description: Teil 3 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330289"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="7391d-104">3. Einrichten Ihres Projekts für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7391d-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="7391d-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7391d-105">Overview</span></span>

<span data-ttu-id="7391d-106">Im vorherigen Tutorial haben Sie Zeit für das Einrichten des Schach-App-Projekts aufgewendet.</span><span class="sxs-lookup"><span data-stu-id="7391d-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="7391d-107">Dieser Abschnitt führt Sie durch das Einrichten der App für die Mixed Reality-Entwicklung, was konkret das Hinzufügen einer AR-Sitzung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="7391d-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="7391d-108">Sie verwenden für diese Aufgabe ein ARSessionConfig-Datenobjekt, das viele nützliche AR-Einstellungen wie räumliche Abbildung und Verdeckung aufweist.</span><span class="sxs-lookup"><span data-stu-id="7391d-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="7391d-109">Wenn Sie tiefer einsteigen möchten, finden Sie in der Dokumentation zur Unreal Engine weitere Details zum Medienobjekt [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) und der Klasse [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="7391d-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="7391d-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="7391d-110">Objectives</span></span>
* <span data-ttu-id="7391d-111">Arbeiten mit den AR-Einstellungen der Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="7391d-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="7391d-112">Verwenden eines ARSessionConfig-Datenobjekts</span><span class="sxs-lookup"><span data-stu-id="7391d-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="7391d-113">Einrichten eines Pawns und des Spielemodus</span><span class="sxs-lookup"><span data-stu-id="7391d-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="7391d-114">Hinzufügen des Sitzungsobjekts</span><span class="sxs-lookup"><span data-stu-id="7391d-114">Adding the session asset</span></span>
<span data-ttu-id="7391d-115">AR-Sitzungen in Unreal kommen nicht aus dem Nichts zustande.</span><span class="sxs-lookup"><span data-stu-id="7391d-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="7391d-116">Um eine Sitzung zu verwenden, benötigen Sie ein ARSessionConfig-Datenobjekt, mit dem Sie arbeiten können, und das ist Ihre nächste Aufgabe:</span><span class="sxs-lookup"><span data-stu-id="7391d-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="7391d-117">Klicken Sie im **Content Browser** (Inhaltsbrowser) auf **Add New > Miscellaneous > Data Asset** (Neu hinzufügen > Sonstiges > Datenobjekt).</span><span class="sxs-lookup"><span data-stu-id="7391d-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="7391d-118">Achten Sie darauf, dass Sie sich auf der Stammebene des Ordners **Content** befinden.</span><span class="sxs-lookup"><span data-stu-id="7391d-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="7391d-119">Wählen Sie **ARSessionConfig** aus, klicken Sie auf **Select** (Auswählen), und geben Sie dem Objekt den Namen **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="7391d-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Erstellen einer Datenressource](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="7391d-121">Doppelklicken Sie auf **ARSessionConfig**, um es zu öffnen, lassen Sie die Standardeinstellungen unverändert, und klicken Sie auf **Save** (Speichern).</span><span class="sxs-lookup"><span data-stu-id="7391d-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="7391d-122">Kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="7391d-122">Return to the Main window.</span></span> 

![AR-Sitzungskonfiguration](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="7391d-124">Nachdem dies erledigt ist, überzeugen Sie sich im nächsten Schritt davon, dass die AR-Sitzung beim Laden des Levels gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="7391d-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="7391d-125">Glücklicherweise verfügt Unreal über eine spezielle Art Blaupause, die als **Level Blueprint** (Levelblaupause) bezeichnet wird und als levelweites globales Ereignisdiagramm fungiert.</span><span class="sxs-lookup"><span data-stu-id="7391d-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="7391d-126">Durch das Verbinden des ARSessionConfig-Medienobjekts mit der **Level Blueprint** wird sichergestellt, dass die AR-Sitzung ordnungsgemäß ausgelöst wird, wenn das Spiel beginnt.</span><span class="sxs-lookup"><span data-stu-id="7391d-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="7391d-127">Klicken Sie in der Editor-Symbolleiste auf **Blueprints > Open Level Blueprint** (Blaupausen > Levelblaupause öffnen):</span><span class="sxs-lookup"><span data-stu-id="7391d-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Geöffnete Levelblaupause](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="7391d-129">Ziehen Sie den Ausführungsknoten (nach links gerichtetes Pfeilsymbol) von **Event BeginPlay** (BeginPlay-Ereignis) herunter, und geben Sie ihn frei.</span><span class="sxs-lookup"><span data-stu-id="7391d-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="7391d-130">Suchen Sie nach **Start AR Session** (AR-Sitzung starten), und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="7391d-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="7391d-131">Klicken Sie unter **Session Config** (Sitzungskonfiguration) auf die Dropdownliste **Select Asset** (Medienobjekt auswählen), und wählen Sie das Medienobjekt **ARSessionConfig** aus.</span><span class="sxs-lookup"><span data-stu-id="7391d-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="7391d-132">Klicken Sie auf **Compile** (Kompilieren), **speichern** Sie Ihre Arbeit, und kehren Sie dann zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="7391d-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Starten der AR-Sitzung](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="7391d-134">Erstellen eines Pawns</span><span class="sxs-lookup"><span data-stu-id="7391d-134">Create a Pawn</span></span>
<span data-ttu-id="7391d-135">An diesem Punkt benötigt das Projekt noch immer ein Playerobjekt.</span><span class="sxs-lookup"><span data-stu-id="7391d-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="7391d-136">In Unreal stellt ein **Pawn** den Benutzer im Spiel dar, aber in diesem Fall handelt es sich um die HoloLens 2-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="7391d-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="7391d-137">Klicken Sie im Ordner **Content** (Inhalt) auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), und klappen Sie unten den Abschnitt **All Classes** (Alle Klassen) auf.</span><span class="sxs-lookup"><span data-stu-id="7391d-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="7391d-138">Suchen Sie nach **DefaultPawn**, klicken Sie auf **Select** (Auswählen), und doppelklicken Sie auf das Medienobjekt, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7391d-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![Erstellen eines neuen Pawns, das von „DefaultPawn“ erbt](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="7391d-140">Standardmäßig verfügen Pawns über Gittermodell- und Kollisionskomponenten.</span><span class="sxs-lookup"><span data-stu-id="7391d-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="7391d-141">In den meisten Unreal-Projekten handelt es sich bei Pawns um feste Objekte, die mit anderen Komponenten zusammenstoßen können.</span><span class="sxs-lookup"><span data-stu-id="7391d-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="7391d-142">Da das Pawn und der Benutzer im Fall von Mixed Reality das Gleiche sind, möchten Sie imstande sein, Hologramme ohne Zusammenstoß zu durchschreiten.</span><span class="sxs-lookup"><span data-stu-id="7391d-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="7391d-143">Wählen Sie im Bereich **Components** (Komponenten) **CollisionComponent** aus, und scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Collision** (Kollision).</span><span class="sxs-lookup"><span data-stu-id="7391d-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="7391d-144">Klicken Sie auf die Dropdownliste **Collision Presets** (Kollisionseinstellung), und ändern Sie den Wert in **NoCollision** (Keine Kollision).</span><span class="sxs-lookup"><span data-stu-id="7391d-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="7391d-145">Führen Sie die gleichen Schritte für **MeshComponent** aus, und **kompilieren** und **speichern** Sie dann die Blaupause.</span><span class="sxs-lookup"><span data-stu-id="7391d-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![Anpassen der Kollisionsvoreinstellungen des Pawns](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="7391d-147">Nachdem Sie Ihre Arbeit hier erledigt haben, kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="7391d-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="7391d-148">Erstellen eines Spielmodus</span><span class="sxs-lookup"><span data-stu-id="7391d-148">Create a Game Mode</span></span>
<span data-ttu-id="7391d-149">Das letzte Puzzleteil der Mixed Reality-Einrichtung ist der Spielemodus.</span><span class="sxs-lookup"><span data-stu-id="7391d-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="7391d-150">Der Spielemodus bestimmt eine Reihe von Einstellungen für das Spiel oder die Umgebung, zu denen unter anderem auch das zu verwendende Standard-Pawn gehört.</span><span class="sxs-lookup"><span data-stu-id="7391d-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="7391d-151">Klicken Sie im Ordner **Content** (Inhalt) auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), und klappen Sie unten den Abschnitt **All Classes** (Alle Klassen) auf.</span><span class="sxs-lookup"><span data-stu-id="7391d-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="7391d-152">Suchen Sie nach **Game Mode Base** (Spielemodusbasis), benennen Sie sie **MRGameMode**, und doppelklicken Sie dann darauf, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7391d-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![„MRGameMode“ im Inhaltsbrowser](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="7391d-154">Navigieren Sie im Bereich **Details** zum Abschnitt **Classes** (Klassen), und ändern Sie die **Default Pawn Class** (Pawn-Standardklasse) in **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="7391d-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="7391d-155">Klicken Sie auf **Compile** (Kompilieren), **speichern** Sie Ihre Arbeit, und kehren Sie dann zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="7391d-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Festlegen der Standard-Pawn-Klasse](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="7391d-157">Wählen Sie **Edit > Projects Settings** (Bearbeiten > Projekteinstellungen) aus, und klicken Sie in der Liste auf der linken Seite auf **Maps & Modes** (Zuordnungen und Modi).</span><span class="sxs-lookup"><span data-stu-id="7391d-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="7391d-158">Klappen Sie **Default Modes** (Standardmodi) auf, und ändern Sie **Default Game Mode** (Standardspielemodus) in **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="7391d-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="7391d-159">Klappen Sie **Default Maps** (Standardzuordnungen) auf, und ändern Sie sowohl **EditorStartupMap** als auch **GameDefaultMap** in **Main**.</span><span class="sxs-lookup"><span data-stu-id="7391d-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="7391d-160">Wenn Sie den Editor schließen und wieder öffnen oder das Spiel spielen, wird auf diese Weise standardmäßig die Hauptzuordnung ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="7391d-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Projekteinstellungen: Zuordnungen und Modi](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="7391d-162">Mit dem jetzt vollständig für Mixed Reality eingerichteten Projekt können Sie jetzt mit dem nächsten Tutorial fortfahren und damit beginnen, der Szene Benutzereingaben hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7391d-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="7391d-163">Nächster Abschnitt: 4. Interaktives Gestalten der Szene</span><span class="sxs-lookup"><span data-stu-id="7391d-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)