---
title: 5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen
description: Teil 5 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: e81da5a4550f258b629443df9b2b655d81108c21
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376362"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="3266a-104">5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen</span><span class="sxs-lookup"><span data-stu-id="3266a-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="3266a-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="3266a-105">Overview</span></span>

<span data-ttu-id="3266a-106">Im vorhergehenden Tutorial haben Sie den Pawn- und Manipulatorkomponenten Handinteraktionsakteure auf dem Schachbrett hinzugefügt, um eine Interaktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3266a-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="3266a-107">In diesem Abschnitt verwenden Sie weiterhin das UX Tools-Plug-In des Reality Toolkit, um die Funktionen der Schach-App zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="3266a-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="3266a-108">Dabei erstellen Sie eine neue Funktion und erfahren, wie Sie Verweise auf Akteure in einer Blaupause abrufen.</span><span class="sxs-lookup"><span data-stu-id="3266a-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="3266a-109">Am Ende dieses Abschnitts können Sie die Mixed Reality-App verpacken und auf einem Gerät oder in einem Emulator bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3266a-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="3266a-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="3266a-110">Objectives</span></span>

* <span data-ttu-id="3266a-111">Hinzufügen einer interaktiven Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="3266a-111">Adding an interactive button</span></span>
* <span data-ttu-id="3266a-112">Erstellen einer Funktion zum Zurücksetzen der Position der Figuren</span><span class="sxs-lookup"><span data-stu-id="3266a-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="3266a-113">Verknüpfen der Schaltfläche, damit die Funktion beim Tippen auf die Schaltfläche ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="3266a-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="3266a-114">Erstellen einer Funktion zum Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="3266a-114">Creating a reset function</span></span>
<span data-ttu-id="3266a-115">Ihre erste Aufgabe besteht darin, eine Funktionsblaupause zu erstellen, mit der die Position einer Schachfigur auf die ursprüngliche Position in der Szene zurückgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="3266a-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="3266a-116">Öffnen Sie **WhiteKing**, klicken Sie auf das Symbol **+** unter **My Blueprint** (Meine Blaupause) neben dem Abschnitt **Functions** (Funktionen), und geben Sie ihr den Namen **Reset Location** (Position zurücksetzen).</span><span class="sxs-lookup"><span data-stu-id="3266a-116">Open **WhiteKing**, click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span> 

2.  <span data-ttu-id="3266a-117">Ziehen Sie die Ausführung aus **Reset Location** auf das Blaupausenraster, um den Knoten **SetActorRelativeTransform** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3266a-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="3266a-118">Durch diese Funktion wird die Transformation (Position, Rotation und Skalierung) eines Akteurs relativ zum übergeordneten Element festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3266a-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="3266a-119">Sie verwenden diese Funktion, um die Position des Königs auf dem Schachbrett zurückzusetzen, auch wenn sich dieses nicht mehr an seiner ursprünglichen Position befindet.</span><span class="sxs-lookup"><span data-stu-id="3266a-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="3266a-120">Klicken Sie mit der rechten Maustaste auf eine Stelle im Ereignisdiagramm, wählen Sie **Make Transform** (Transformation erstellen) aus, und ändern Sie **Location** (Position) in **X = -26**, **Y = 4**, **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="3266a-120">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="3266a-121">Verbinden Sie **Return Value** (Rückgabewert) mit dem Pin **New Relative Transform** (Neue relative Transformation) in **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="3266a-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span> 

![Funktion zum Zurücksetzen der Position](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="3266a-123">**Kompilieren** und **speichern** Sie das Projekt, bevor Sie zum Hauptfenster zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="3266a-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="3266a-124">Hinzufügen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="3266a-124">Adding a button</span></span>
<span data-ttu-id="3266a-125">Nachdem die Funktion nun ordnungsgemäß eingerichtet wurde, besteht die nächste Aufgabe darin, eine Schaltfläche zu erstellen, die ausgelöst wird, sobald sie berührt wird.</span><span class="sxs-lookup"><span data-stu-id="3266a-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 

1.  <span data-ttu-id="3266a-126">Klicken Sie auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), erweitern Sie den Abschnitt **All Classes** (Alle Klassen), und suchen Sie nach **SimpleButton** (Einfache Schaltfläche).</span><span class="sxs-lookup"><span data-stu-id="3266a-126">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **SimpleButton**.</span></span> 
    * <span data-ttu-id="3266a-127">Geben Sie Ihr den Namen **ResetButton**, und doppelklicken Sie darauf, um die Blaupause zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3266a-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="3266a-128">**SimpleButton** ist ein Blaupausenakteur in Form einer 3D-Schaltfläche, die im UX Tools-Plug-In enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="3266a-128">**SimpleButton** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span> <span data-ttu-id="3266a-129">.</span><span class="sxs-lookup"><span data-stu-id="3266a-129">.</span></span> 

![Verwenden der neuen Blaupause als Unterklasse von „SimpleButton“](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="3266a-131">Klicken Sie im Bereich **Components** auf **PressableButton (Inherited)** (Drückbare Schaltfläche (geerbt)), und scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Events** (Ereignisse).</span><span class="sxs-lookup"><span data-stu-id="3266a-131">Click **Pressable Button (Inherited)** from the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="3266a-132">Klicken Sie neben **On Button Pressed** (Beim Drücken der Schaltfläche) auf das grüne **+** , um dem Ereignisdiagramm ein Ereignis hinzuzufügen, das aufgerufen wird, wenn die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="3266a-132">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="3266a-133">Hier soll die Funktion **Reset Location** für **WhiteKing** aufgerufen werden. Dazu ist ein Verweis auf den Akteur **WhiteKing** im Level erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3266a-133">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

1.  <span data-ttu-id="3266a-134">Navigieren Sie im Bereich **My Blueprint** (Meine Blaupause) zum Abschnitt **Variables** (Variablen), klicken Sie auf die Schaltfläche **+** , und geben Sie der Variablen den Namen **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="3266a-134">In the **My Blueprint** panel, navigate to the **Variables** section , click the **+** button and name the variable **WhiteKing**.</span></span> 
    * <span data-ttu-id="3266a-135">Wählen Sie im Bereich **Details** die Dropdownliste neben **Variable Type** (Variablentyp) aus, suchen Sie nach **WhiteKing**, und wählen Sie **Object Reference** (Objektverweis) aus.</span><span class="sxs-lookup"><span data-stu-id="3266a-135">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span> 
    * <span data-ttu-id="3266a-136">Aktivieren Sie das Kontrollkästchen neben **Instance Editable** (Bearbeitbare Instanz).</span><span class="sxs-lookup"><span data-stu-id="3266a-136">Check the box next to **Instance Editable**.</span></span> <span data-ttu-id="3266a-137">Dadurch kann die Variable von der Hauptebene aus festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="3266a-137">This will allow the variable to be set from the Main Level.</span></span> 

![Erstellen einer Variablen](images/unreal-uxt/5-var.PNG)

2.  <span data-ttu-id="3266a-139">Ziehen Sie die Variable „WhiteKing“ aus **My Blueprint > Variables** (Meine Blaupause > Variablen) auf das Ereignisdiagramm für die Schaltfläche „Reset“, und wählen Sie **Get WhiteKing** aus.</span><span class="sxs-lookup"><span data-stu-id="3266a-139">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="3266a-140">Auslösen der Funktion</span><span class="sxs-lookup"><span data-stu-id="3266a-140">Firing the function</span></span>
<span data-ttu-id="3266a-141">Jetzt muss nur noch die Funktion zum Zurücksetzen ausgelöst werden, wenn die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="3266a-141">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="3266a-142">Ziehen Sie den Ausgabepin von „WhiteKing“, und lassen Sie ihn los, um einen neuen Knoten zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="3266a-142">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="3266a-143">Wählen Sie die Funktion **Reset Location** (Position zurücksetzen) aus.</span><span class="sxs-lookup"><span data-stu-id="3266a-143">Select the **Reset Location** function.</span></span> <span data-ttu-id="3266a-144">Ziehen Sie abschließend den ausgehenden Ausführungspin von **On Button Pressed** (Beim Drücken des Schalters) zum eingehenden Ausführungspin von **Reset Location** (Position zurücksetzen).</span><span class="sxs-lookup"><span data-stu-id="3266a-144">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="3266a-145">**Kompilieren** und **speichern** Sie die Blaupause „ResetButton“, und kehren Sie anschließend zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="3266a-145">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Aufrufen der Funktion zum Zurücksetzen der Position über „On Button Pressed“ (Beim Drücken des Schalters)](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="3266a-147">Ziehen Sie **ResetButton** in den Viewport, und legen Sie die Position auf **X = 50**, **Y = -25** und **Z = 10** fest.</span><span class="sxs-lookup"><span data-stu-id="3266a-147">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="3266a-148">Legen Sie unter **Default** (Standard) den Wert der Variablen **WhiteKing** auf **WhiteKing** fest.</span><span class="sxs-lookup"><span data-stu-id="3266a-148">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Festlegen der Variablen](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="3266a-150">Führen Sie die App aus, verschieben Sie die Schachfigur an eine neue Position, und tippen Sie auf die große pinkfarbene Schaltfläche, um die Logik zum Zurücksetzen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3266a-150">Run the app, move the chess piece to a new location, and press the big pink button to see the reset logic in action!</span></span>

<span data-ttu-id="3266a-151">Sie verfügen nun über eine Mixed Reality-App mit einer interaktiven Schachfigur und einem Schachbrett sowie mit einer funktionsfähigen Schaltfläche, mit der die Position der Schachfigur zurückgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3266a-151">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="3266a-152">Die bis hier hin fertige App finden Sie im [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp)-Repository.</span><span class="sxs-lookup"><span data-stu-id="3266a-152">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="3266a-153">Sie können gerne noch einen Schritt weitergehen und die restlichen Schachfiguren einrichten, sodass das gesamte Schachbrett zurückgesetzt wird, wenn die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="3266a-153">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="3266a-155">Sie können nun mit dem letzten Abschnitt dieses Tutorials fortfahren, in dem Sie erfahren, wie Sie die App ordnungsgemäß verpacken und auf einem Gerät oder in einem Emulator bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3266a-155">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

[<span data-ttu-id="3266a-156">Nächster Abschnitt: 6. Verpacken und Bereitstellen auf einem Gerät oder Emulator</span><span class="sxs-lookup"><span data-stu-id="3266a-156">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
