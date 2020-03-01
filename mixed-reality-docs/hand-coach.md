---
title: Hand Coach
description: 3D-Hände, die ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt, um Sie zu unterstützen.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Hand Coach, immersives Headset, mrtk, Hände, Unterstützung von Hand
ms.openlocfilehash: c5f0a0c241ff71dc93f370a5a8caa627128bfb1a
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202735"
---
# <a name="hand-coach"></a><span data-ttu-id="39ed9-104">Hand Coach</span><span class="sxs-lookup"><span data-stu-id="39ed9-104">Hand coach</span></span>

<span data-ttu-id="39ed9-105">Hand Coach ist 3D-modellierte Hände, die ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt.</span><span class="sxs-lookup"><span data-stu-id="39ed9-105">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="39ed9-106">Dies wird als "Lehr Komponente" implementiert, die den Benutzer unterstützt, wenn die Geste nicht gelehrt wurde.</span><span class="sxs-lookup"><span data-stu-id="39ed9-106">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="39ed9-107">Wenn Benutzer die angegebene Geste für einen Zeitraum nicht durchgeführt haben, wird die Hand mit einer Verzögerung Schleife.</span><span class="sxs-lookup"><span data-stu-id="39ed9-107">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="39ed9-108">Der handbus könnte verwendet werden, um das Drücken einer Schaltfläche oder das Auswählen eines holograms darzustellen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-108">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  


<span data-ttu-id="39ed9-109">![Beispiel: Hand Coach](images/HandCoach/MRTK_handCoach.jpg)</span><span class="sxs-lookup"><span data-stu-id="39ed9-109">![Example: Hand coach](images/HandCoach/MRTK_handCoach.jpg)</span></span><br>
<span data-ttu-id="39ed9-110">*Handbus Beispiel von mrtk*</span><span class="sxs-lookup"><span data-stu-id="39ed9-110">*HandCoach Example from MRTK*</span></span>

## <a name="hand-coach-provided"></a><span data-ttu-id="39ed9-111">Hand Trainer bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="39ed9-111">Hand coach provided</span></span>

<span data-ttu-id="39ed9-112">Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gesten Steuerelementen dar, wie z. b. Scrollen, weite Auswahl und Near Tap.</span><span class="sxs-lookup"><span data-stu-id="39ed9-112">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="39ed9-113">Im folgenden finden Sie eine vollständige Liste der in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> mrtk</a>bereitgestellten Handgesten:</span><span class="sxs-lookup"><span data-stu-id="39ed9-113">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="39ed9-114">![Beispiel für Near Select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-114">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="39ed9-115">**Beispiel für Near Select-used anzeigen auswählen von Schaltflächen oder Schließen von Objekten mit Interaktionen**</span><span class="sxs-lookup"><span data-stu-id="39ed9-115">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="39ed9-116">![Beispiel für Air Tap](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-116">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="39ed9-117">**Beispiel für Air Tap: wird verwendet, um zu zeigen, wie Objekte, die weit entfernt sind, ausgewählt werden.**</span><span class="sxs-lookup"><span data-stu-id="39ed9-117">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="39ed9-118">![Beispiel für Move](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-118">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="39ed9-119">**Beispiel für das Verschieben eines Objekts im Raum: wird verwendet, um zu veranschaulichen, wie ein – Hologramm in den Raum verschoben wird.**</span><span class="sxs-lookup"><span data-stu-id="39ed9-119">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="39ed9-120">![Beispiel für das Drehen](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-120">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="39ed9-121">**Beispiel für drehen: wird verwendet, um zu zeigen, wie Hologramme oder Objekte gedreht werden.**</span><span class="sxs-lookup"><span data-stu-id="39ed9-121">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="39ed9-122">![Beispiel für Skalierungs](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-122">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="39ed9-123">**Beispiel für "Scale-used", um zu veranschaulichen, wie die Manipulation von holograms größer oder kleiner wird**</span><span class="sxs-lookup"><span data-stu-id="39ed9-123">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="39ed9-124">![Beispiel für die](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-124">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="39ed9-125">**Beispiel für eine zusammen Fläche – Empfohlene Verwendung, um die Menüs aufzurufenden**</span><span class="sxs-lookup"><span data-stu-id="39ed9-125">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="39ed9-126">![Beispiel für ein handflip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-126">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="39ed9-127">**Exahorn von Hand Flip – eine andere Möglichkeit zum Einrichten von Menüs**</span><span class="sxs-lookup"><span data-stu-id="39ed9-127">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="39ed9-128">![Beispiel für Scroll](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-128">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="39ed9-129">**Beispiel für einen Scroll–, der zum Scrollen einer Liste oder eines langen Dokuments verwendet wird**</span><span class="sxs-lookup"><span data-stu-id="39ed9-129">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="39ed9-130">Entwurfskonzepte</span><span class="sxs-lookup"><span data-stu-id="39ed9-130">Design concepts</span></span>

<span data-ttu-id="39ed9-131">Für Hololens2 haben wir die manuellen Interaktionen auf der Grundlage von instanziellen und natürlichen Handbewegungen entworfen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-131">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="39ed9-132">Wir sind der Meinung, dass diese für die meisten Benutzer intuitiv sind und daher keine dedizierten Gesten lernmomente geschaffen haben.</span><span class="sxs-lookup"><span data-stu-id="39ed9-132">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="39ed9-133">Stattdessen haben wir den Hand-Bus erstellt, um Benutzer zu unterstützen, die möglicherweise hängen bleiben oder mit der Interaktion mit holograms nicht vertraut sind. Weitere Informationen zu diesen Gesten</span><span class="sxs-lookup"><span data-stu-id="39ed9-133">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="39ed9-134">Ohne einen Lern Moment haben wir gespürt, dass Benutzern angezeigt wird, wie Sie eine Aktion durchführen können, indem Sie Ihnen zeigen, dass Sie die beste Option ist.</span><span class="sxs-lookup"><span data-stu-id="39ed9-134">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="39ed9-135">In unseren Studien stellten wir fest, dass Benutzer in der Lage waren, die Geste herauszufinden, aber eine kleine Anleitung benötigten.</span><span class="sxs-lookup"><span data-stu-id="39ed9-135">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="39ed9-136">Wenn Sie feststellen, dass ein Benutzer für einen bestimmten Zeitraum nicht mit einem Objekt interagiert, wird ein Hand Trainer ausgelöst, der die korrekte Hand-und Finger Platzierung demonstriert.</span><span class="sxs-lookup"><span data-stu-id="39ed9-136">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="39ed9-137">Intuitiven</span><span class="sxs-lookup"><span data-stu-id="39ed9-137">Intuitive</span></span>

<span data-ttu-id="39ed9-138">Bei der Animation sollte es offensichtlich sein, und es kann zu Verwirrung führen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-138">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="39ed9-139">Die Animation der Hände ist eine Darstellung der Geste, die Sie dem Benutzer zur Veranschaulichung des Zwecks des zwecks vermitteln möchten.</span><span class="sxs-lookup"><span data-stu-id="39ed9-139">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="39ed9-140">Wenn Sie z. b. möchten, dass ein Benutzer auf eine Schaltfläche klickt, wird eine Hand Taste gedrückt.</span><span class="sxs-lookup"><span data-stu-id="39ed9-140">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="39ed9-141">![Beispiel: Hand Coach near Tap](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-141">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="39ed9-142">*Hand Coach, der das Tippen auf einen gem tippen zeigt*</span><span class="sxs-lookup"><span data-stu-id="39ed9-142">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="39ed9-143">Hand Skala</span><span class="sxs-lookup"><span data-stu-id="39ed9-143">Hand scale</span></span>

<span data-ttu-id="39ed9-144">Wir haben verschiedene Hand Größen mit den Menüs für die Benutzeroberfläche getestet, und Sie fühlten, dass Sie, wenn die Hände für die Größe zutreffen, eine wohlwollende Vorstellung hatten, aber wenn Sie zu klein waren, war es schwierig, die Geste zu erkennen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-144">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="39ed9-145">**Voice-over und Hand**</span><span class="sxs-lookup"><span data-stu-id="39ed9-145">**Voice over and hands**</span></span>

<span data-ttu-id="39ed9-146">Sie sollten nicht erwarten, dass Benutzer eine Reihe von Anweisungen über eine Stimme überwachen und andere Anweisungen über den Hand-Bus ansehen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="39ed9-147">Sequenzieren Sie Ihre Anweisungen, um Benutzern den Fokus zu erleichtern und um Ihre Aufmerksamkeit zu unterstützen, um die Sensor Überlastung</span><span class="sxs-lookup"><span data-stu-id="39ed9-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="39ed9-148">Kann ich meine eigene erstellen?</span><span class="sxs-lookup"><span data-stu-id="39ed9-148">Can I create my own?</span></span>

<span data-ttu-id="39ed9-149">Ja,</span><span class="sxs-lookup"><span data-stu-id="39ed9-149">Yes!</span></span> <span data-ttu-id="39ed9-150">Wir empfehlen Ihnen, eine eigene, einzigartige Geste für Ihr Spiel zu erstellen und zur Community beizutragen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="39ed9-151">Wir haben eine Maya-Datei für eine manipulierte Hand bereitgestellt, die für Ihre APP verwendet werden kann. Sie können hier heruntergeladen werden: <a href="files/HandCoach_MRTK.zip">Download HandCoach_MRTK. zip</a></span><span class="sxs-lookup"><span data-stu-id="39ed9-151">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="39ed9-152">![Beispiel für animierte Hände in Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="39ed9-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="39ed9-153">*Beispiel für ein animiertes Hand Zeichen in Maya*</span><span class="sxs-lookup"><span data-stu-id="39ed9-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="39ed9-154">**Empfohlenes Authoring Tool**</span><span class="sxs-lookup"><span data-stu-id="39ed9-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="39ed9-155">Bei 3D-Künstlern entscheiden sich viele für die Verwendung [von Autodesk Maya, die wiederum hololens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) zum Transformieren der Art und Weise der Erstellung von Assets verwenden können.</span><span class="sxs-lookup"><span data-stu-id="39ed9-155">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="39ed9-156">Die angegebene handdatei ist eine Maya-Binärdatei. Daher empfiehlt es sich, Maya zu verwenden, um die Hände zu animieren und zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="39ed9-156">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="39ed9-157">Wenn Sie lieber ein anderes 3D-Programm verwenden möchten, finden Sie hier eine <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Laden Sie HandCoachMRTK_FBX. zip herunter</a> , um Ihre eigene Controller Einrichtung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-157">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="39ed9-158">Wenn Sie die herunterladbare Maya-handdatei verwenden, wird empfohlen, die Hände in Unity auf 0,6 zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="39ed9-158">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="39ed9-159">![Beispiel: Hand Coach rig in Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="39ed9-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="39ed9-160">*Manipulierte Hände*</span><span class="sxs-lookup"><span data-stu-id="39ed9-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="39ed9-161">Technische Spezifikationen</span><span class="sxs-lookup"><span data-stu-id="39ed9-161">Technical Specs</span></span>

*   <span data-ttu-id="39ed9-162">Zwei über gebene Dateien sind im Maya ASCII-Format verfügbar.</span><span class="sxs-lookup"><span data-stu-id="39ed9-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="39ed9-163">Rechts und Links sind im Format "Maya Binary" verfügbar.</span><span class="sxs-lookup"><span data-stu-id="39ed9-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="39ed9-164">Festlegen der Maya-Datei auf 24 fps</span><span class="sxs-lookup"><span data-stu-id="39ed9-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="39ed9-165">Innerhalb der Datei gibt es eine linke und Rechte Seite, die für zwei Hand-oder einstellige Gesten verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="39ed9-165">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="39ed9-166">Die Rechte Seite ist standardmäßig nur sichtbar.</span><span class="sxs-lookup"><span data-stu-id="39ed9-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="39ed9-167">Es wird empfohlen, einen Puffer mit ungefähr 10 Frames am Anfang und am Ende für die gestreamungen zu belassen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-167">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="39ed9-168">Wenn Sie ein-Objekt mit einem angegebenen Ziel animieren, empfiehlt es sich, ein Standardfeld zu animieren oder NULL zu animieren.</span><span class="sxs-lookup"><span data-stu-id="39ed9-168">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="39ed9-169">Wenn die Hand ein physisches Objekt, wie z. b. ein Feld, animiert, empfiehlt es sich, die Übersetzung nicht in Maya zu animieren, sondern in Unity oder im Code zu animieren.</span><span class="sxs-lookup"><span data-stu-id="39ed9-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="39ed9-170">Die sichtbare Animation sollte 1,5 Sekunden sein, damit aussagekräftige Informationen übermittelt werden können.</span><span class="sxs-lookup"><span data-stu-id="39ed9-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="39ed9-171">Wenn Sie mit ihrer Animation zufrieden sind:</span><span class="sxs-lookup"><span data-stu-id="39ed9-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="39ed9-172">Alle Gelenke auswählen und Keyframes Backen</span><span class="sxs-lookup"><span data-stu-id="39ed9-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="39ed9-173">Löschen Sie die Controller, wählen Sie die Gelenke und das Mesh aus, und exportieren Sie Sie als eine andere</span><span class="sxs-lookup"><span data-stu-id="39ed9-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="39ed9-174">Wenn mehrere Animationen vorhanden sind, können Sie das integrierte Game Exporter von Maya verwenden: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="39ed9-174">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="39ed9-175">Exportieren aus Maya</span><span class="sxs-lookup"><span data-stu-id="39ed9-175">Exporting from Maya</span></span>

<span data-ttu-id="39ed9-176">Nachdem Sie mit ihrer Animation zufrieden sind</span><span class="sxs-lookup"><span data-stu-id="39ed9-176">After you are satisfied with your animation</span></span>
* <span data-ttu-id="39ed9-177">Alle Gelenke auswählen: Wählen Sie > Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="39ed9-177">Select all joints: Select > Hierarchy</span></span>

     ![Beispiel: Menü Position](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="39ed9-179">Animation der Animation: Wechseln Sie zur Animation > Key > Animation.</span><span class="sxs-lookup"><span data-stu-id="39ed9-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Beispiel: Menü Position](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="39ed9-181">Löschen Sie das Controller-Rig: Outliner-> MainR_Grp oder MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="39ed9-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Beispiel: Menü Position](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="39ed9-183">Exportieren als FBX: Wählen Sie JNT + Mesh: File > Export Selection (Optionsfeld) > Export Auswahl aus.</span><span class="sxs-lookup"><span data-stu-id="39ed9-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Beispiel: Menü Position](images/HandCoach/OptionBox.png)<br>

     ![Beispiel: Menü Position](images/HandCoach/SelectionExport.png)<br>

     ![Beispiel: Menü Position](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="39ed9-187">Wenn Sie als FBX exportieren und in Unity integriert sind, Skalieren Sie die Hände auf 0,6.</span><span class="sxs-lookup"><span data-stu-id="39ed9-187">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="39ed9-188">Wir haben festgestellt, dass dies das perfekte Gleichgewicht für die Anzeige der Hände ist.</span><span class="sxs-lookup"><span data-stu-id="39ed9-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="39ed9-189">![Beispiel: Unity-Einstellungen](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="39ed9-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="39ed9-190">*Unity-Einstellungen für HandCoach_R-präfab in mrtk*</span><span class="sxs-lookup"><span data-stu-id="39ed9-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="39ed9-191">Implementieren von Hand in Ihr Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="39ed9-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="39ed9-192">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="39ed9-192">Best practices</span></span>
*    <span data-ttu-id="39ed9-193">Es wird empfohlen, die Hände in Unity auf 0,6 zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="39ed9-193">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="39ed9-194">Hände sollten zweimal abgespielt werden und, wenn Sie nicht abgeschlossen ist, bis zum Abschluss der Bewegung fortlaufend.</span><span class="sxs-lookup"><span data-stu-id="39ed9-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="39ed9-195">Die Hände sollten zweimal Schleifen, um sicherzustellen, dass der Benutzer Zeit hat, sich zu registrieren und die Geste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="39ed9-196">Die Hände sollten Zwischenschleifen ein-und ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="39ed9-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="39ed9-197">Wenn Benutzer Hände durch HL2-Kameras sichtbar sind, die Benutzer jedoch nicht die erforderliche Interaktion durchlaufen, werden die Hände nach 10 Sekunden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="39ed9-197">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="39ed9-198">Wenn Benutzer Hände nicht durch HL2 Kameras sichtbar sind, werden die Hände nach 5 Sekunden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="39ed9-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="39ed9-199">Wenn Benutzer Hände in der Mitte der Animation von HL2-Kameras sichtbar sind, wird die Animation vervollständigt und ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="39ed9-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="39ed9-200">Wenn Sie Voice over einschließen, empfehlen wir, dass es der Handbewegung entspricht.</span><span class="sxs-lookup"><span data-stu-id="39ed9-200">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="39ed9-201">Wenn Sie die Hände mindestens einmal gelehrt haben, wiederholen Sie die Geste nur, wenn Sie festgestellt hat, dass der Benutzer nicht mehr vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="39ed9-201">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="39ed9-202">Wenn bestimmte Finger-/uhrzeitanpositionen kritisch sind, stellen Sie sicher, dass Benutzer diese Nuancen in der Animation eindeutig sehen können.</span><span class="sxs-lookup"><span data-stu-id="39ed9-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="39ed9-203">Probieren Sie die Hände, damit die wichtigsten Teile klar sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="39ed9-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="39ed9-204">Wenn Sie auf eine gewisse Verzerrung achten, müssen Sie die Qualitätseinstellungen der Unity erhöhen, um die Menge der Knochen zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="39ed9-205">Wechseln Sie zu Unity-> Projekteinstellungen > Quality > Andere > Blend-Gewichtungen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="39ed9-206">Stellen Sie sicher, dass "4 Knochen" ausgewählt sind, um glatte Gelenke anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Beispiel: Menü Position](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="39ed9-208">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="39ed9-208">What to avoid</span></span>
* <span data-ttu-id="39ed9-209">Skalieren der Hände zu groß</span><span class="sxs-lookup"><span data-stu-id="39ed9-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="39ed9-210">die Hände werden dem Benutzer zu nah platziert.</span><span class="sxs-lookup"><span data-stu-id="39ed9-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="39ed9-211">Hände sollten nur einmal vermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="39ed9-211">Hands should only be taught once.</span></span> <span data-ttu-id="39ed9-212">Über lehrungen können Verwirrung und Verwirrung verursachen.</span><span class="sxs-lookup"><span data-stu-id="39ed9-212">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="39ed9-213">Wenn Sie ihn in Unity einbinden, laden Sie den aktuellen mrtk hier herunter: https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="39ed9-213">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="39ed9-214">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="39ed9-214">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="39ed9-215">Skripts: siehe mrtk Guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">mrtk Hand Coach</a></span><span class="sxs-lookup"><span data-stu-id="39ed9-215">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="39ed9-216">Pro-Projekt-Einstellung</span><span class="sxs-lookup"><span data-stu-id="39ed9-216">Per- project setting</span></span>
        *   <span data-ttu-id="39ed9-217">Szene, die auf UWP festgelegt ist: Anweisungen finden Sie im [Unity-Projekt](Configure-Unity-Project.md) für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="39ed9-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="39ed9-218">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="39ed9-218">See also</span></span>
* [<span data-ttu-id="39ed9-219">Interaktion: Grundlagen</span><span class="sxs-lookup"><span data-stu-id="39ed9-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="39ed9-220">Asset-Erstellungs Prozess</span><span class="sxs-lookup"><span data-stu-id="39ed9-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="39ed9-221">Gesten</span><span class="sxs-lookup"><span data-stu-id="39ed9-221">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="39ed9-222">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="39ed9-222">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="39ed9-223">Unity-Projekt konfigurieren</span><span class="sxs-lookup"><span data-stu-id="39ed9-223">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="39ed9-224">Unity-Entwicklung – Übersicht</span><span class="sxs-lookup"><span data-stu-id="39ed9-224">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="39ed9-225">Mrtk 101</span><span class="sxs-lookup"><span data-stu-id="39ed9-225">MRTK 101</span></span>](mrtk-101.md)
