---
title: Interactable object
description: A button has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Controls, interaction, ui, ux
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143259"
---
# <a name="interactable-object"></a><span data-ttu-id="e7925-105">Interactable object</span><span class="sxs-lookup"><span data-stu-id="e7925-105">Interactable object</span></span>

![Interactible objects](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="e7925-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span><span class="sxs-lookup"><span data-stu-id="e7925-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="e7925-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span><span class="sxs-lookup"><span data-stu-id="e7925-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="e7925-109">Anything can be an **interactable object** that triggers an event.</span><span class="sxs-lookup"><span data-stu-id="e7925-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="e7925-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span><span class="sxs-lookup"><span data-stu-id="e7925-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="e7925-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span><span class="sxs-lookup"><span data-stu-id="e7925-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="e7925-112">The visual representation of the button depends on the context.</span><span class="sxs-lookup"><span data-stu-id="e7925-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="e7925-113">Important properties of the interactable object</span><span class="sxs-lookup"><span data-stu-id="e7925-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="e7925-114">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="e7925-114">Visual cues</span></span>

<span data-ttu-id="e7925-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span><span class="sxs-lookup"><span data-stu-id="e7925-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="e7925-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span><span class="sxs-lookup"><span data-stu-id="e7925-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="e7925-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span><span class="sxs-lookup"><span data-stu-id="e7925-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="e7925-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span><span class="sxs-lookup"><span data-stu-id="e7925-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="e7925-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span><span class="sxs-lookup"><span data-stu-id="e7925-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="e7925-120">Far interactions</span><span class="sxs-lookup"><span data-stu-id="e7925-120">Far interactions</span></span>

<span data-ttu-id="e7925-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span><span class="sxs-lookup"><span data-stu-id="e7925-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e7925-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="e7925-123">**Default (Observation) state**</span><span class="sxs-lookup"><span data-stu-id="e7925-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="e7925-124">Default idle state of the object.</span><span class="sxs-lookup"><span data-stu-id="e7925-124">Default idle state of the object.</span></span>
    <span data-ttu-id="e7925-125">The cursor is not on the object.</span><span class="sxs-lookup"><span data-stu-id="e7925-125">The cursor is not on the object.</span></span> <span data-ttu-id="e7925-126">Hand is not detected.</span><span class="sxs-lookup"><span data-stu-id="e7925-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e7925-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="e7925-128">**Targeted (Hover) state**</span><span class="sxs-lookup"><span data-stu-id="e7925-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="e7925-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span><span class="sxs-lookup"><span data-stu-id="e7925-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="e7925-130">The cursor is on the object.</span><span class="sxs-lookup"><span data-stu-id="e7925-130">The cursor is on the object.</span></span> <span data-ttu-id="e7925-131">Hand is detected, ready.</span><span class="sxs-lookup"><span data-stu-id="e7925-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e7925-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="e7925-133">**Pressed state**</span><span class="sxs-lookup"><span data-stu-id="e7925-133">**Pressed state**</span></span><br>
        <span data-ttu-id="e7925-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span><span class="sxs-lookup"><span data-stu-id="e7925-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="e7925-135">The cursor is on the object.</span><span class="sxs-lookup"><span data-stu-id="e7925-135">The cursor is on the object.</span></span> <span data-ttu-id="e7925-136">Hand is detected, air tapped.</span><span class="sxs-lookup"><span data-stu-id="e7925-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="e7925-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span><span class="sxs-lookup"><span data-stu-id="e7925-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="e7925-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span><span class="sxs-lookup"><span data-stu-id="e7925-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="e7925-139">Here is what these states look like on a **holographic button**:</span><span class="sxs-lookup"><span data-stu-id="e7925-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e7925-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="e7925-141">**Default (Observation) state**</span><span class="sxs-lookup"><span data-stu-id="e7925-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e7925-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="e7925-143">**Targeted (Hover) state**</span><span class="sxs-lookup"><span data-stu-id="e7925-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e7925-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="e7925-145">**Pressed state**</span><span class="sxs-lookup"><span data-stu-id="e7925-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="e7925-146">Near interactions (direct)</span><span class="sxs-lookup"><span data-stu-id="e7925-146">Near interactions (direct)</span></span> 

<span data-ttu-id="e7925-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span><span class="sxs-lookup"><span data-stu-id="e7925-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="e7925-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span><span class="sxs-lookup"><span data-stu-id="e7925-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="e7925-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span><span class="sxs-lookup"><span data-stu-id="e7925-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="e7925-150">Use visual feedback to communicate the following:</span><span class="sxs-lookup"><span data-stu-id="e7925-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="e7925-151">**Default (Observation)** : Default idle state of the object.</span><span class="sxs-lookup"><span data-stu-id="e7925-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="e7925-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span><span class="sxs-lookup"><span data-stu-id="e7925-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="e7925-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span><span class="sxs-lookup"><span data-stu-id="e7925-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="e7925-154">**Kontakt beginnt**: Ändern der visuellen Elemente (hell, Farbe), um zu kommunizieren, dass eine Fingereingabe aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="e7925-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="e7925-155">**Verstanden**: Ändern von visuellen Elementen (hell, Farbe), wenn das Objekt erfasst wird</span><span class="sxs-lookup"><span data-stu-id="e7925-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="e7925-156">**Kontakt Ende**: Ändern der visuellen Elemente (hell, Farbe), wenn die Fingereingabe beendet wurde</span><span class="sxs-lookup"><span data-stu-id="e7925-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="e7925-157">![Hover (weit)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="e7925-158">**Hover (weit)**</span><span class="sxs-lookup"><span data-stu-id="e7925-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="e7925-159">Hervorhebung basierend auf der Nähe der Hand.</span><span class="sxs-lookup"><span data-stu-id="e7925-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e7925-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="e7925-161">**Hover (in der Nähe)**</span><span class="sxs-lookup"><span data-stu-id="e7925-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="e7925-162">Die Größenänderungen werden basierend auf der Entfernung zur Hand hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="e7925-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="e7925-163">![berühren/drücken](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="e7925-164">**Berühren/drücken**</span><span class="sxs-lookup"><span data-stu-id="e7925-164">**Touch / press**</span></span><br>
        <span data-ttu-id="e7925-165">Feedback zu Visual Plus-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="e7925-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e7925-166">![verstanden](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="e7925-167">**Gespür**</span><span class="sxs-lookup"><span data-stu-id="e7925-167">**Grasp**</span></span><br>
        <span data-ttu-id="e7925-168">Feedback zu Visual Plus-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="e7925-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="e7925-169">Eine [Schaltfläche in hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) ist ein Beispiel dafür, wie die verschiedenen Eingabe Interaktions Zustände visualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="e7925-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e7925-170">Standard ![](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="e7925-171">**Vorgegebene**</span><span class="sxs-lookup"><span data-stu-id="e7925-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e7925-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="e7925-173">**Hocker**</span><span class="sxs-lookup"><span data-stu-id="e7925-173">**Hover**</span></span><br>
        <span data-ttu-id="e7925-174">Zeigen Sie einen near-basierten Beleuchtungs Effekt an.</span><span class="sxs-lookup"><span data-stu-id="e7925-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="e7925-175">![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="e7925-176">**Toucheingabe**</span><span class="sxs-lookup"><span data-stu-id="e7925-176">**Touch**</span></span><br>
        <span data-ttu-id="e7925-177">Ripple-Effekt anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e7925-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e7925-178">![drücken](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="e7925-179">**Drückt**</span><span class="sxs-lookup"><span data-stu-id="e7925-179">**Press**</span></span><br>
        <span data-ttu-id="e7925-180">Verschieben Sie die Vorderseite.</span><span class="sxs-lookup"><span data-stu-id="e7925-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="e7925-181">Der visuelle Hinweis "Ring" auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="e7925-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="e7925-182">Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e7925-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="e7925-183">Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst.</span><span class="sxs-lookup"><span data-stu-id="e7925-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="e7925-184">Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="e7925-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="e7925-185">Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.</span><span class="sxs-lookup"><span data-stu-id="e7925-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="e7925-186">*Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*</span><span class="sxs-lookup"><span data-stu-id="e7925-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e7925-187">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e7925-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e7925-188">![Sie visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="e7925-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="e7925-189">Audiohinweise</span><span class="sxs-lookup"><span data-stu-id="e7925-189">Audio cues</span></span>

<span data-ttu-id="e7925-190">Bei direkter Hand Interaktion kann das richtige Audiofeedback die Benutzer Leistung erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="e7925-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="e7925-191">Verwenden Sie Audiofeedback, um Folgendes zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="e7925-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="e7925-192">**Kontakt beginnt**: Sound abspielen, wenn der Fingerabdruck beginnt</span><span class="sxs-lookup"><span data-stu-id="e7925-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="e7925-193">**Kontakt**Ende: Sound am Touchscreen abspielen</span><span class="sxs-lookup"><span data-stu-id="e7925-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="e7925-194">**Beginn**: Sound abspielen, wenn der Start beginnt</span><span class="sxs-lookup"><span data-stu-id="e7925-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="e7925-195">Aufnahme **Ende**: Sound wiedergeben, wenn der Griff endet</span><span class="sxs-lookup"><span data-stu-id="e7925-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="e7925-196">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="e7925-196">Voice commanding</span></span><br>
        <span data-ttu-id="e7925-197">Bei allen Objekt übergreifenden Objekten ist es wichtig, Alternative Interaktions Optionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e7925-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="e7925-198">Standardmäßig wird empfohlen, dass [sprach](voice-design.md) Befehle für alle Objekte unterstützt werden, die interacbar sind.</span><span class="sxs-lookup"><span data-stu-id="e7925-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="e7925-199">Um die Auffindbarkeit zu verbessern, können Sie auch eine QuickInfo für den Hover-Zustand bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e7925-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="e7925-200">*Bild: QuickInfo für den Voice-Befehl*</span><span class="sxs-lookup"><span data-stu-id="e7925-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![Sprachbefehl](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="e7925-202">Empfehlungen zur Größenanpassung</span><span class="sxs-lookup"><span data-stu-id="e7925-202">Sizing recommendations</span></span> 

<span data-ttu-id="e7925-203">Um sicherzustellen, dass alle austauschbaren Objekte problemlos von Benutzern berührt werden können, sollten Sie sicherstellen, dass die Interaktionen eine minimale Größe (den visuellen Winkel, der häufig in Grad des visuellen Bogens gemessen wird) basierend auf der Entfernung des Benutzers erfüllt.</span><span class="sxs-lookup"><span data-stu-id="e7925-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="e7925-204">Der visuelle Winkel basiert auf der Entfernung zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels möglicherweise ändert, wenn sich der Abstand vom Benutzer ändert.</span><span class="sxs-lookup"><span data-stu-id="e7925-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="e7925-205">Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung des Benutzers zu bestimmen, versuchen Sie, einen visuellen Winkel Rechner wie [diesen](https://elvers.us/perception/visualAngle/)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e7925-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="e7925-206">Im folgenden finden Sie die Empfehlungen für die Mindestgröße von Interaktionen-Inhalten.</span><span class="sxs-lookup"><span data-stu-id="e7925-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="e7925-207">Zielgröße für direkte Interaktion</span><span class="sxs-lookup"><span data-stu-id="e7925-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="e7925-208">Flüge</span><span class="sxs-lookup"><span data-stu-id="e7925-208">Distance</span></span> | <span data-ttu-id="e7925-209">Anzeige Winkel</span><span class="sxs-lookup"><span data-stu-id="e7925-209">Viewing angle</span></span> | <span data-ttu-id="e7925-210">Größe</span><span class="sxs-lookup"><span data-stu-id="e7925-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="e7925-211">45cm</span><span class="sxs-lookup"><span data-stu-id="e7925-211">45cm</span></span>  | <span data-ttu-id="e7925-212">nicht kleiner als 2 °</span><span class="sxs-lookup"><span data-stu-id="e7925-212">no smaller than 2°</span></span> | <span data-ttu-id="e7925-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="e7925-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="e7925-214">![Zielgröße für die direkte Interaktion](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="e7925-215">*Zielgröße für direkte Interaktion*</span><span class="sxs-lookup"><span data-stu-id="e7925-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="e7925-216">Zielgröße für Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="e7925-216">Target size for buttons</span></span>

<span data-ttu-id="e7925-217">Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass genügend Speicherplatz vorhanden ist, um ein Symbol und potenziell einen Text zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="e7925-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="e7925-218">Flüge</span><span class="sxs-lookup"><span data-stu-id="e7925-218">Distance</span></span> | <span data-ttu-id="e7925-219">Mindestgröße</span><span class="sxs-lookup"><span data-stu-id="e7925-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="e7925-220">45cm</span><span class="sxs-lookup"><span data-stu-id="e7925-220">45cm</span></span>  | <span data-ttu-id="e7925-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="e7925-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="e7925-222">![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="e7925-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="e7925-223">*Zielgröße für die Schaltflächen*</span><span class="sxs-lookup"><span data-stu-id="e7925-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="e7925-224">Zielgröße für die Hand Strahl-oder Blick Interaktion</span><span class="sxs-lookup"><span data-stu-id="e7925-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="e7925-225">Flüge</span><span class="sxs-lookup"><span data-stu-id="e7925-225">Distance</span></span> | <span data-ttu-id="e7925-226">Anzeige Winkel</span><span class="sxs-lookup"><span data-stu-id="e7925-226">Viewing angle</span></span> | <span data-ttu-id="e7925-227">Größe</span><span class="sxs-lookup"><span data-stu-id="e7925-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="e7925-228">2 min</span><span class="sxs-lookup"><span data-stu-id="e7925-228">2m</span></span>  | <span data-ttu-id="e7925-229">nicht kleiner als 1 °</span><span class="sxs-lookup"><span data-stu-id="e7925-229">no smaller than 1°</span></span> | <span data-ttu-id="e7925-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="e7925-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="e7925-231">![Zielgröße für die Hand Strahl-oder Blick Interaktion](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="e7925-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="e7925-232">*Zielgröße für die Hand Strahl-oder Blick Interaktion*</span><span class="sxs-lookup"><span data-stu-id="e7925-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a><span data-ttu-id="e7925-233">Interactable-Objekt in mrtk (Mixed Reality Toolkit) für Unit</span><span class="sxs-lookup"><span data-stu-id="e7925-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span></span>

<span data-ttu-id="e7925-234">In **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie das Skript [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, damit Objekte auf verschiedene Typen von Eingabe Interaktions Zuständen reagieren.</span><span class="sxs-lookup"><span data-stu-id="e7925-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="e7925-235">Es unterstützt verschiedene Arten von Themen, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie Farbe, Größe, Material und Shader steuern.</span><span class="sxs-lookup"><span data-stu-id="e7925-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="e7925-236">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e7925-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="e7925-237">Button</span><span class="sxs-lookup"><span data-stu-id="e7925-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="e7925-238">Beispiel Szenen für Hand Interaktion</span><span class="sxs-lookup"><span data-stu-id="e7925-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="e7925-239">Der Standard-Shader von mixedrealitytoolkit bietet verschiedene Optionen, wie z. b. **near Light** , mit denen Sie visuelle und Audiohinweise erstellen können.</span><span class="sxs-lookup"><span data-stu-id="e7925-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="e7925-240">Mrtk-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="e7925-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="e7925-241">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="e7925-241">See also</span></span>

* [<span data-ttu-id="e7925-242">Cursor</span><span class="sxs-lookup"><span data-stu-id="e7925-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e7925-243">Hand Strahl</span><span class="sxs-lookup"><span data-stu-id="e7925-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e7925-244">Button</span><span class="sxs-lookup"><span data-stu-id="e7925-244">Button</span></span>](button.md)
* [<span data-ttu-id="e7925-245">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="e7925-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e7925-246">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="e7925-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e7925-247">Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="e7925-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e7925-248">Handmenü</span><span class="sxs-lookup"><span data-stu-id="e7925-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e7925-249">Near-Menü</span><span class="sxs-lookup"><span data-stu-id="e7925-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e7925-250">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="e7925-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e7925-251">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="e7925-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e7925-252">Tastatur</span><span class="sxs-lookup"><span data-stu-id="e7925-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e7925-253">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="e7925-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e7925-254">Tafel</span><span class="sxs-lookup"><span data-stu-id="e7925-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="e7925-255">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="e7925-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="e7925-256">Shader</span><span class="sxs-lookup"><span data-stu-id="e7925-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="e7925-257">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="e7925-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e7925-258">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="e7925-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e7925-259">Oberflächen Magnetismus</span><span class="sxs-lookup"><span data-stu-id="e7925-259">Surface magnetism</span></span>](surface-magnetism.md)
