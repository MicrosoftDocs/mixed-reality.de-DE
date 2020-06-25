---
title: Hand Coach
description: 3D-Hände, die ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt, um Sie zu unterstützen.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Hand Coach, immersives Headset, mrtk, Hände, Unterstützung von Hand
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345664"
---
# <a name="hand-coach"></a><span data-ttu-id="15bbd-104">Hand Coach</span><span class="sxs-lookup"><span data-stu-id="15bbd-104">Hand coach</span></span>
![Beispiel: Hand Trainer](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="15bbd-106">Hand Coach ist 3D-modellierte Hände, die ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt.</span><span class="sxs-lookup"><span data-stu-id="15bbd-106">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="15bbd-107">Dies wird als "Lehr Komponente" implementiert, die den Benutzer unterstützt, wenn die Geste nicht gelehrt wurde.</span><span class="sxs-lookup"><span data-stu-id="15bbd-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="15bbd-108">Wenn Benutzer die angegebene Geste für einen Zeitraum nicht durchgeführt haben, wird die Hand mit einer Verzögerung Schleife.</span><span class="sxs-lookup"><span data-stu-id="15bbd-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="15bbd-109">Der handbus könnte verwendet werden, um das Drücken einer Schaltfläche oder das Auswählen eines holograms darzustellen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="15bbd-110">Hand Trainer bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="15bbd-110">Hand coach provided</span></span>

<span data-ttu-id="15bbd-111">Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gesten Steuerelementen dar, wie z. b. Scrollen, weite Auswahl und Near Tap.</span><span class="sxs-lookup"><span data-stu-id="15bbd-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="15bbd-112">Im folgenden finden Sie eine vollständige Liste der in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> mrtk</a>bereitgestellten Handgesten:</span><span class="sxs-lookup"><span data-stu-id="15bbd-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="15bbd-113">![Beispiel für Near SELECT](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="15bbd-114">**Beispiel für Near Select-used anzeigen auswählen von Schaltflächen oder Schließen von Objekten mit Interaktionen**</span><span class="sxs-lookup"><span data-stu-id="15bbd-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15bbd-115">![Beispiel für Luft tippen](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="15bbd-116">**Beispiel für Air Tap: wird verwendet, um zu zeigen, wie Objekte, die weit entfernt sind, ausgewählt werden.**</span><span class="sxs-lookup"><span data-stu-id="15bbd-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15bbd-117">![Beispiel für Move](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="15bbd-118">**Beispiel für das Verschieben eines Objekts im Raum: wird verwendet, um zu veranschaulichen, wie ein – Hologramm in den Raum verschoben wird.**</span><span class="sxs-lookup"><span data-stu-id="15bbd-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15bbd-119">![Beispiel für Drehung](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="15bbd-120">**Beispiel für drehen: wird verwendet, um zu zeigen, wie Hologramme oder Objekte gedreht werden.**</span><span class="sxs-lookup"><span data-stu-id="15bbd-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="15bbd-121">![Beispiel für Skalierung](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="15bbd-122">**Beispiel für "Scale-used", um zu veranschaulichen, wie die Manipulation von holograms größer oder kleiner wird**</span><span class="sxs-lookup"><span data-stu-id="15bbd-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15bbd-123">![Beispiel für eine Palm-up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="15bbd-124">**Beispiel für eine zusammen Fläche – Empfohlene Verwendung, um die Menüs aufzurufenden**</span><span class="sxs-lookup"><span data-stu-id="15bbd-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15bbd-125">![Beispiel für ein handflip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="15bbd-126">**Exahorn von Hand Flip – eine andere Möglichkeit zum Einrichten von Menüs**</span><span class="sxs-lookup"><span data-stu-id="15bbd-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15bbd-127">![Beispiel für einen Bildlauf](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="15bbd-128">**Beispiel für einen Scroll–, der zum Scrollen einer Liste oder eines langen Dokuments verwendet wird**</span><span class="sxs-lookup"><span data-stu-id="15bbd-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="15bbd-129">Entwurfskonzepte</span><span class="sxs-lookup"><span data-stu-id="15bbd-129">Design concepts</span></span>

<span data-ttu-id="15bbd-130">Für Hololens2 haben wir die manuellen Interaktionen auf der Grundlage von instanziellen und natürlichen Handbewegungen entworfen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="15bbd-131">Wir sind der Meinung, dass diese für die meisten Benutzer intuitiv sind und daher keine dedizierten Gesten lernmomente geschaffen haben.</span><span class="sxs-lookup"><span data-stu-id="15bbd-131">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="15bbd-132">Stattdessen haben wir den Hand-Bus erstellt, um Benutzer zu unterstützen, die möglicherweise hängen bleiben oder mit der Interaktion mit holograms nicht vertraut sind. Weitere Informationen zu diesen Gesten</span><span class="sxs-lookup"><span data-stu-id="15bbd-132">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="15bbd-133">Ohne einen Lern Moment haben wir gespürt, dass Benutzern angezeigt wird, wie Sie eine Aktion durchführen können, indem Sie Ihnen zeigen, dass Sie die beste Option ist.</span><span class="sxs-lookup"><span data-stu-id="15bbd-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="15bbd-134">In unseren Studien stellten wir fest, dass Benutzer in der Lage waren, die Geste herauszufinden, aber eine kleine Anleitung benötigten.</span><span class="sxs-lookup"><span data-stu-id="15bbd-134">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="15bbd-135">Wenn Sie feststellen, dass ein Benutzer für einen bestimmten Zeitraum nicht mit einem Objekt interagiert, wird ein Hand Trainer ausgelöst, der die korrekte Hand-und Finger Platzierung demonstriert.</span><span class="sxs-lookup"><span data-stu-id="15bbd-135">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="15bbd-136">Intuitiven</span><span class="sxs-lookup"><span data-stu-id="15bbd-136">Intuitive</span></span>

<span data-ttu-id="15bbd-137">Bei der Animation sollte es offensichtlich sein, und es kann zu Verwirrung führen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-137">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="15bbd-138">Die Animation der Hände ist eine Darstellung der Geste, die Sie dem Benutzer zur Veranschaulichung des Zwecks des zwecks vermitteln möchten.</span><span class="sxs-lookup"><span data-stu-id="15bbd-138">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="15bbd-139">Wenn Sie z. b. möchten, dass ein Benutzer auf eine Schaltfläche klickt, wird eine Hand Taste gedrückt.</span><span class="sxs-lookup"><span data-stu-id="15bbd-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="15bbd-140">![Beispiel: Hand-Bus near Tap](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="15bbd-141">*Hand Coach, der das Tippen auf einen gem tippen zeigt*</span><span class="sxs-lookup"><span data-stu-id="15bbd-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="15bbd-142">Hand Skala</span><span class="sxs-lookup"><span data-stu-id="15bbd-142">Hand scale</span></span>

<span data-ttu-id="15bbd-143">Wir haben verschiedene Hand Größen mit den Menüs für die Benutzeroberfläche getestet, und Sie fühlten, dass Sie, wenn die Hände für die Größe zutreffen, eine wohlwollende Vorstellung hatten, aber wenn Sie zu klein waren, war es schwierig, die Geste zu erkennen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="15bbd-144">**Voice-over und Hand**</span><span class="sxs-lookup"><span data-stu-id="15bbd-144">**Voice over and hands**</span></span>

<span data-ttu-id="15bbd-145">Sie sollten nicht erwarten, dass Benutzer eine Reihe von Anweisungen über eine Stimme überwachen und andere Anweisungen über den Hand-Bus ansehen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-145">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="15bbd-146">Sequenzieren Sie Ihre Anweisungen, um Benutzern den Fokus zu erleichtern und um Ihre Aufmerksamkeit zu unterstützen, um die Sensor Überlastung</span><span class="sxs-lookup"><span data-stu-id="15bbd-146">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="15bbd-147">Kann ich meine eigene erstellen?</span><span class="sxs-lookup"><span data-stu-id="15bbd-147">Can I create my own?</span></span>

<span data-ttu-id="15bbd-148">Ja!</span><span class="sxs-lookup"><span data-stu-id="15bbd-148">Yes!</span></span> <span data-ttu-id="15bbd-149">Wir empfehlen Ihnen, eine eigene, einzigartige Geste für Ihr Spiel zu erstellen und zur Community beizutragen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-149">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="15bbd-150">Wir haben eine Maya-Datei für eine manipulierte Hand bereitgestellt, die für Ihre APP verwendet werden kann. Sie können hier heruntergeladen werden: <a href="files/HandCoach_MRTK.zip">Download HandCoach_MRTK.zip</a></span><span class="sxs-lookup"><span data-stu-id="15bbd-150">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="15bbd-151">![Beispiel für animierte Hände in Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="15bbd-151">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="15bbd-152">*Beispiel für ein animiertes Hand Zeichen in Maya*</span><span class="sxs-lookup"><span data-stu-id="15bbd-152">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="15bbd-153">**Empfohlenes Authoring Tool**</span><span class="sxs-lookup"><span data-stu-id="15bbd-153">**Recommended authoring tool**</span></span>

<span data-ttu-id="15bbd-154">Bei 3D-Künstlern entscheiden sich viele für die Verwendung [von Autodesk Maya, die wiederum hololens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) zum Transformieren der Art und Weise der Erstellung von Assets verwenden können.</span><span class="sxs-lookup"><span data-stu-id="15bbd-154">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="15bbd-155">Die angegebene handdatei ist eine Maya-Binärdatei. Daher empfiehlt es sich, Maya zu verwenden, um die Hände zu animieren und zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="15bbd-155">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="15bbd-156">Wenn Sie lieber ein anderes 3D-Programm verwenden möchten, finden Sie hier eine <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Laden Sie HandCoachMRTK_FBX.zipherunter</a> , um ein eigenes Controller-Setup zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-156">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="15bbd-157">Wenn Sie die herunterladbare Maya-handdatei verwenden, wird empfohlen, die Hände in Unity auf 0,6 zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="15bbd-157">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="15bbd-158">![Beispiel: Hand Bus rig in Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="15bbd-158">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="15bbd-159">*Manipulierte Hände*</span><span class="sxs-lookup"><span data-stu-id="15bbd-159">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="15bbd-160">Technische Spezifikationen</span><span class="sxs-lookup"><span data-stu-id="15bbd-160">Technical Specs</span></span>

*   <span data-ttu-id="15bbd-161">Zwei über gebene Dateien sind im Maya ASCII-Format verfügbar.</span><span class="sxs-lookup"><span data-stu-id="15bbd-161">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="15bbd-162">Rechts und Links sind im Format "Maya Binary" verfügbar.</span><span class="sxs-lookup"><span data-stu-id="15bbd-162">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="15bbd-163">Festlegen der Maya-Datei auf 24 fps</span><span class="sxs-lookup"><span data-stu-id="15bbd-163">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="15bbd-164">Innerhalb der Datei gibt es eine linke und Rechte Seite, die für zwei Hand-oder einstellige Gesten verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="15bbd-164">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="15bbd-165">Die Rechte Seite ist standardmäßig nur sichtbar.</span><span class="sxs-lookup"><span data-stu-id="15bbd-165">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="15bbd-166">Es wird empfohlen, einen Puffer mit ungefähr 10 Frames am Anfang und am Ende für die gestreamungen zu belassen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-166">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="15bbd-167">Wenn Sie ein-Objekt mit einem angegebenen Ziel animieren, empfiehlt es sich, ein Standardfeld zu animieren oder NULL zu animieren.</span><span class="sxs-lookup"><span data-stu-id="15bbd-167">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="15bbd-168">Wenn die Hand ein physisches Objekt, wie z. b. ein Feld, animiert, empfiehlt es sich, die Übersetzung nicht in Maya zu animieren, sondern in Unity oder im Code zu animieren.</span><span class="sxs-lookup"><span data-stu-id="15bbd-168">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="15bbd-169">Die sichtbare Animation sollte 1,5 Sekunden sein, damit aussagekräftige Informationen übermittelt werden können.</span><span class="sxs-lookup"><span data-stu-id="15bbd-169">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="15bbd-170">Wenn Sie mit ihrer Animation zufrieden sind:</span><span class="sxs-lookup"><span data-stu-id="15bbd-170">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="15bbd-171">Alle Gelenke auswählen und Keyframes Backen</span><span class="sxs-lookup"><span data-stu-id="15bbd-171">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="15bbd-172">Löschen Sie die Controller, wählen Sie die Gelenke und das Mesh aus, und exportieren Sie Sie als eine andere</span><span class="sxs-lookup"><span data-stu-id="15bbd-172">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="15bbd-173">Wenn mehrere Animationen vorhanden sind, können Sie das integrierte Game Exporter von Maya verwenden:https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="15bbd-173">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="15bbd-174">Exportieren aus Maya</span><span class="sxs-lookup"><span data-stu-id="15bbd-174">Exporting from Maya</span></span>

<span data-ttu-id="15bbd-175">Nachdem Sie mit ihrer Animation zufrieden sind</span><span class="sxs-lookup"><span data-stu-id="15bbd-175">After you are satisfied with your animation</span></span>
* <span data-ttu-id="15bbd-176">Alle Gelenke auswählen: Wählen Sie > Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="15bbd-176">Select all joints: Select > Hierarchy</span></span>

     ![Beispiel: Menü Position](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="15bbd-178">Animation der Animation: Wechseln Sie zur Animation > Key > Animation.</span><span class="sxs-lookup"><span data-stu-id="15bbd-178">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Beispiel: Menü Position](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="15bbd-180">Löschen Sie das Controller-Rig: Outliner-> MainR_Grp oder MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="15bbd-180">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Beispiel: Menü Position](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="15bbd-182">Exportieren als FBX: Wählen Sie JNT + Mesh: File > Export Selection (Optionsfeld) > Export Auswahl aus.</span><span class="sxs-lookup"><span data-stu-id="15bbd-182">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Beispiel: Menü Position](images/HandCoach/OptionBox.png)<br>

     ![Beispiel: Menü Position](images/HandCoach/SelectionExport.png)<br>

     ![Beispiel: Menü Position](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="15bbd-186">Wenn Sie als FBX exportieren und in Unity integriert sind, Skalieren Sie die Hände auf 0,6.</span><span class="sxs-lookup"><span data-stu-id="15bbd-186">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="15bbd-187">Wir haben festgestellt, dass dies das perfekte Gleichgewicht für die Anzeige der Hände ist.</span><span class="sxs-lookup"><span data-stu-id="15bbd-187">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="15bbd-188">![Beispiel: Unity-Einstellungen](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="15bbd-188">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="15bbd-189">*Unity-Einstellungen für HandCoach_R-präfab in mrtk*</span><span class="sxs-lookup"><span data-stu-id="15bbd-189">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="15bbd-190">Implementieren von Hand in Ihr Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="15bbd-190">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="15bbd-191">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="15bbd-191">Best practices</span></span>
*    <span data-ttu-id="15bbd-192">Es wird empfohlen, die Hände in Unity auf 0,6 zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="15bbd-192">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="15bbd-193">Hände sollten zweimal abgespielt werden und, wenn Sie nicht abgeschlossen ist, bis zum Abschluss der Bewegung fortlaufend.</span><span class="sxs-lookup"><span data-stu-id="15bbd-193">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="15bbd-194">Die Hände sollten zweimal Schleifen, um sicherzustellen, dass der Benutzer Zeit hat, sich zu registrieren und die Geste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-194">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="15bbd-195">Die Hände sollten Zwischenschleifen ein-und ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="15bbd-195">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="15bbd-196">Wenn Benutzer Hände durch HL2-Kameras sichtbar sind, die Benutzer jedoch nicht die erforderliche Interaktion durchlaufen, werden die Hände nach 10 Sekunden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="15bbd-196">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="15bbd-197">Wenn Benutzer Hände nicht durch HL2 Kameras sichtbar sind, werden die Hände nach 5 Sekunden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="15bbd-197">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="15bbd-198">Wenn Benutzer Hände in der Mitte der Animation von HL2-Kameras sichtbar sind, wird die Animation vervollständigt und ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="15bbd-198">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="15bbd-199">Wenn Sie Voice over einschließen, empfehlen wir, dass es der Handbewegung entspricht.</span><span class="sxs-lookup"><span data-stu-id="15bbd-199">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="15bbd-200">Wenn Sie die Hände mindestens einmal gelehrt haben, wiederholen Sie die Geste nur, wenn Sie festgestellt hat, dass der Benutzer nicht mehr vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="15bbd-200">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="15bbd-201">Wenn bestimmte Finger-/uhrzeitanpositionen kritisch sind, stellen Sie sicher, dass Benutzer diese Nuancen in der Animation eindeutig sehen können.</span><span class="sxs-lookup"><span data-stu-id="15bbd-201">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="15bbd-202">Probieren Sie die Hände, damit die wichtigsten Teile klar sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="15bbd-202">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="15bbd-203">Wenn Sie auf eine gewisse Verzerrung achten, müssen Sie die Qualitätseinstellungen der Unity erhöhen, um die Menge der Knochen zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-203">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="15bbd-204">Wechseln Sie zu Unity-> Projekteinstellungen > Quality > andere > Blend-Gewichtungen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-204">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="15bbd-205">Stellen Sie sicher, dass "4 Knochen" ausgewählt sind, um glatte Gelenke anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-205">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Beispiel: Menü Position](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="15bbd-207">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="15bbd-207">What to avoid</span></span>
* <span data-ttu-id="15bbd-208">Skalieren der Hände zu groß</span><span class="sxs-lookup"><span data-stu-id="15bbd-208">Scaling the Hands too large</span></span>
* <span data-ttu-id="15bbd-209">die Hände werden dem Benutzer zu nah platziert.</span><span class="sxs-lookup"><span data-stu-id="15bbd-209">placing the Hands too close to the user</span></span>
* <span data-ttu-id="15bbd-210">Hände sollten nur einmal vermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="15bbd-210">Hands should only be taught once.</span></span> <span data-ttu-id="15bbd-211">Über lehrungen können Verwirrung und Verwirrung verursachen.</span><span class="sxs-lookup"><span data-stu-id="15bbd-211">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="15bbd-212">Wenn Sie es in Unity einbinden möchten, laden Sie den aktuellen mrtk hier herunter:https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="15bbd-212">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="15bbd-213">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="15bbd-213">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="15bbd-214">Skripts: siehe mrtk Guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">mrtk Hand Coach</a></span><span class="sxs-lookup"><span data-stu-id="15bbd-214">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="15bbd-215">Pro-Projekt-Einstellung</span><span class="sxs-lookup"><span data-stu-id="15bbd-215">Per- project setting</span></span>
        *   <span data-ttu-id="15bbd-216">Szene, die auf UWP festgelegt ist: Anweisungen finden Sie im [Unity-Projekt](Configure-Unity-Project.md) für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="15bbd-216">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="15bbd-217">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="15bbd-217">See also</span></span>
* [<span data-ttu-id="15bbd-218">Interaktion: Grundlagen</span><span class="sxs-lookup"><span data-stu-id="15bbd-218">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="15bbd-219">Asset-Erstellungs Prozess</span><span class="sxs-lookup"><span data-stu-id="15bbd-219">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="15bbd-220">Gesten</span><span class="sxs-lookup"><span data-stu-id="15bbd-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="15bbd-221">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="15bbd-221">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="15bbd-222">Unity-Projekt konfigurieren</span><span class="sxs-lookup"><span data-stu-id="15bbd-222">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="15bbd-223">Unity-Entwicklung – Übersicht</span><span class="sxs-lookup"><span data-stu-id="15bbd-223">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="15bbd-224">Mrtk 101</span><span class="sxs-lookup"><span data-stu-id="15bbd-224">MRTK 101</span></span>](mrtk-101.md)
