---
title: Interactable-Objekt
description: Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird. In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, UI, UX
ms.openlocfilehash: 36ca1feeba0e3bf028c64fe7b559d263a8088b96
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438645"
---
# <a name="interactable-object"></a><span data-ttu-id="e4d6b-105">Interactable-Objekt</span><span class="sxs-lookup"><span data-stu-id="e4d6b-105">Interactable object</span></span>

![Objekte mit Interaktivität](images/InteractableExamples.png)

<span data-ttu-id="e4d6b-107">Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="e4d6b-108">In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="e4d6b-109">Dabei kann es sich um ein Objekt handeln, das ein **Objekt** ist, das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="e4d6b-110">Ein Objekt, das sich in der Tabelle befindet, kann als beliebiger von einem Kaffeebecher in der Tabelle dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="e4d6b-111">Wir verwenden weiterhin herkömmliche Schaltflächen in bestimmten Situationen, z. b. in der Dialogfeld Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="e4d6b-112">Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="e4d6b-113">Wichtige Eigenschaften des Interaktionen-Objekts</span><span class="sxs-lookup"><span data-stu-id="e4d6b-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="e4d6b-114">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="e4d6b-114">Visual cues</span></span>

<span data-ttu-id="e4d6b-115">Visuelle Hinweise sind sensorische Hinweise, die vom visuellen System während der visuellen Darstellung vom visuellen System empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="e4d6b-116">Da das visuelle System in vielen Arten, insbesondere bei Menschen, dominant ist, stellen visuelle Hinweise eine große Informationsquelle dar, in der die Welt wahrgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="e4d6b-117">Da die Holographic-Objekte in gemischter Realität mit der realen Umgebung kombiniert werden, kann es schwierig sein, die Objekte zu verstehen, mit denen Sie interagieren können.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="e4d6b-118">Für alle Objekte, die sich in der Benutzersprache befinden, ist es wichtig, für jeden Eingabe Zustand differenzierte visuelle Hinweise bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="e4d6b-119">Dadurch kann der Benutzer verstehen, welcher Teil ihrer Benutzeroberflächen Interaktionen ist, und der Benutzer wird mit einer konsistenten Interaktions Methode vertraut.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="e4d6b-120">Weite Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e4d6b-120">Far interactions</span></span>

<span data-ttu-id="e4d6b-121">Für alle Objekte, die der Benutzer mit dem Blick auf "Blick", "Hand Ray" und "Motion Controller" interagieren kann, empfiehlt es sich, einen anderen visuellen Hinweis auf die drei Eingabe Zustände zu haben:</span><span class="sxs-lookup"><span data-stu-id="e4d6b-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e4d6b-122">![interactibleobject-States-default](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="e4d6b-123">**Standardzustand (Überwachung)**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="e4d6b-124">Der standardmäßige Leerlauf Status des Objekts.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-124">Default idle state of the object.</span></span>
    <span data-ttu-id="e4d6b-125">Der Cursor befindet sich nicht im-Objekt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-125">The cursor is not on the object.</span></span> <span data-ttu-id="e4d6b-126">Hand wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4d6b-127">![](images/interactibleobject-states-targeted.jpg) mit interactibleobjektzuständen</span><span class="sxs-lookup"><span data-stu-id="e4d6b-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-128">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="e4d6b-129">, Wenn das Objekt mit dem Cursor Cursor, der fingernähe oder dem Bewegungs Controller Zeiger ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="e4d6b-130">Der Cursor befindet sich auf dem-Objekt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-130">The cursor is on the object.</span></span> <span data-ttu-id="e4d6b-131">Hand ist erkannt, bereit.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4d6b-132">!["interactibleobject-States-Pressed"](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="e4d6b-133">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-133">**Pressed state**</span></span><br>
        <span data-ttu-id="e4d6b-134">Wenn das Objekt mit einer Tastenkombination gedrückt wird, drücken Sie die Schaltfläche "auswählen" von Finger oder Motion Controller.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="e4d6b-135">Der Cursor befindet sich auf dem-Objekt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-135">The cursor is on the object.</span></span> <span data-ttu-id="e4d6b-136">Hand ist erkannt, Air tippt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="e4d6b-137">Sie können Techniken wie z. b. Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabe Zustand des Benutzers bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="e4d6b-138">In gemischter Realität finden Sie die Beispiele für die Visualisierung unterschiedlicher Eingabe Zustände im Startmenü und mit den Schaltflächen der APP-Leiste.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="e4d6b-139">So sehen diese Zustände auf einer **Holographic-Schaltfläche**aus:</span><span class="sxs-lookup"><span data-stu-id="e4d6b-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e4d6b-140">![interactibleobject-States-default](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="e4d6b-141">**Standardzustand (Überwachung)**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4d6b-142">![](images/MRTK_InteractableState-targeted.jpg) mit interactibleobjektzuständen</span><span class="sxs-lookup"><span data-stu-id="e4d6b-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-143">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4d6b-144">!["interactibleobject-States-Pressed"](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="e4d6b-145">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="e4d6b-146">Near Interaktionen (Direct)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-146">Near interactions (direct)</span></span> 

<span data-ttu-id="e4d6b-147">Hololens 2 unterstützt die Eingabe von Handgelenk Nachverfolgung, mit der Sie mit Objekten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="e4d6b-148">Ohne haptisches Feedback und eine perfekte Tiefe Wahrnehmung kann es manchmal schwierig sein zu wissen, wie weit die Hand von einem Objekt entfernt ist oder ob Sie es berühren.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="e4d6b-149">Es ist wichtig, genügend visuelle Hinweise bereitzustellen, um den Status des Objekts und insbesondere den Zustand ihrer Hände in Bezug auf das Objekt zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="e4d6b-150">Verwenden Sie visuelles Feedback, um Folgendes zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="e4d6b-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="e4d6b-151">**Default (Observation)** : standardmäßiger Leerlauf Status des Objekts.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="e4d6b-152">**Hover**: Wenn eine Hand sich in der Nähe eines Hologramms befindet, ändern Sie die visuellen Elemente, um zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="e4d6b-153">**Entfernung und Punkt der Interaktion**: Wenn die Hand ein Hologramm nähert, entwerfen Sie das Feedback, um den projizierten Interaktionspunkt zu kommunizieren, und wie weit von dem Objekt der Finger ist.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="e4d6b-154">**Kontakt beginnt**: Ändern der visuellen Elemente (hell, Farbe), um zu kommunizieren, dass eine Fingereingabe aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="e4d6b-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="e4d6b-155">**Verstanden**: Ändern von visuellen Elementen (hell, Farbe), wenn das Objekt erfasst wird</span><span class="sxs-lookup"><span data-stu-id="e4d6b-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="e4d6b-156">**Kontakt Ende**: Ändern der visuellen Elemente (hell, Farbe), wenn die Fingereingabe beendet wurde</span><span class="sxs-lookup"><span data-stu-id="e4d6b-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="e4d6b-157">![Hover (weit)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-158">**Hover (weit)**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="e4d6b-159">Hervorhebung basierend auf der Nähe der Hand.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e4d6b-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-161">**Hover (in der Nähe)**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="e4d6b-162">Die Größenänderungen werden basierend auf der Entfernung zur Hand hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="e4d6b-163">![berühren/drücken](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-164">**Berühren/drücken**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-164">**Touch / press**</span></span><br>
        <span data-ttu-id="e4d6b-165">Feedback zu Visual Plus-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e4d6b-166">![verstanden](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-167">**Gespür**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-167">**Grasp**</span></span><br>
        <span data-ttu-id="e4d6b-168">Feedback zu Visual Plus-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="e4d6b-169">Eine [Schaltfläche in hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) ist ein Beispiel dafür, wie die verschiedenen Eingabe Interaktions Zustände visualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="e4d6b-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e4d6b-170">Standard ![](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-171">**Vorgegebene**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e4d6b-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-173">**Hocker**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-173">**Hover**</span></span><br>
        <span data-ttu-id="e4d6b-174">Zeigen Sie einen near-basierten Beleuchtungs Effekt an.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="e4d6b-175">![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-176">**Toucheingabe**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-176">**Touch**</span></span><br>
        <span data-ttu-id="e4d6b-177">Ripple-Effekt anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e4d6b-178">![drücken](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="e4d6b-179">**Drückt**</span><span class="sxs-lookup"><span data-stu-id="e4d6b-179">**Press**</span></span><br>
        <span data-ttu-id="e4d6b-180">Verschieben Sie die Vorderseite.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="e4d6b-181">Der visuelle Hinweis "Ring" auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="e4d6b-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="e4d6b-182">Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="e4d6b-183">Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="e4d6b-184">Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="e4d6b-185">Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="e4d6b-186">*Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*</span><span class="sxs-lookup"><span data-stu-id="e4d6b-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e4d6b-187">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e4d6b-188">![Sie visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="e4d6b-189">Audiohinweise</span><span class="sxs-lookup"><span data-stu-id="e4d6b-189">Audio cues</span></span>

<span data-ttu-id="e4d6b-190">Bei direkter Hand Interaktion kann das richtige Audiofeedback die Benutzer Leistung erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="e4d6b-191">Verwenden Sie Audiofeedback, um Folgendes zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="e4d6b-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="e4d6b-192">**Kontakt beginnt**: Sound abspielen, wenn der Fingerabdruck beginnt</span><span class="sxs-lookup"><span data-stu-id="e4d6b-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="e4d6b-193">**Kontakt**Ende: Sound am Touchscreen abspielen</span><span class="sxs-lookup"><span data-stu-id="e4d6b-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="e4d6b-194">**Beginn**: Sound abspielen, wenn der Start beginnt</span><span class="sxs-lookup"><span data-stu-id="e4d6b-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="e4d6b-195">Aufnahme **Ende**: Sound wiedergeben, wenn der Griff endet</span><span class="sxs-lookup"><span data-stu-id="e4d6b-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="e4d6b-196">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="e4d6b-196">Voice commanding</span></span><br>
        <span data-ttu-id="e4d6b-197">Bei allen Objekt übergreifenden Objekten ist es wichtig, Alternative Interaktions Optionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="e4d6b-198">Standardmäßig wird empfohlen, dass [sprach](voice-design.md) Befehle für alle Objekte unterstützt werden, die interacbar sind.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="e4d6b-199">Um die Auffindbarkeit zu verbessern, können Sie auch eine QuickInfo für den Hover-Zustand bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="e4d6b-200">*Bild: QuickInfo für den Voice-Befehl*</span><span class="sxs-lookup"><span data-stu-id="e4d6b-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![Sprachbefehl](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="e4d6b-202">Empfehlungen zur Größenanpassung</span><span class="sxs-lookup"><span data-stu-id="e4d6b-202">Sizing recommendations</span></span> 

<span data-ttu-id="e4d6b-203">Um sicherzustellen, dass alle austauschbaren Objekte problemlos von Benutzern berührt werden können, sollten Sie sicherstellen, dass die Interaktionen eine minimale Größe (den visuellen Winkel, der häufig in Grad des visuellen Bogens gemessen wird) basierend auf der Entfernung des Benutzers erfüllt.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="e4d6b-204">Der visuelle Winkel basiert auf der Entfernung zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels möglicherweise ändert, wenn sich der Abstand vom Benutzer ändert.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="e4d6b-205">Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung des Benutzers zu bestimmen, versuchen Sie, einen visuellen Winkel Rechner wie [diesen](https://elvers.us/perception/visualAngle/)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="e4d6b-206">Im folgenden finden Sie die Empfehlungen für die Mindestgröße von Interaktionen-Inhalten.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="e4d6b-207">Zielgröße für direkte Interaktion</span><span class="sxs-lookup"><span data-stu-id="e4d6b-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="e4d6b-208">Flüge</span><span class="sxs-lookup"><span data-stu-id="e4d6b-208">Distance</span></span> | <span data-ttu-id="e4d6b-209">Anzeige Winkel</span><span class="sxs-lookup"><span data-stu-id="e4d6b-209">Viewing angle</span></span> | <span data-ttu-id="e4d6b-210">Größe</span><span class="sxs-lookup"><span data-stu-id="e4d6b-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="e4d6b-211">45cm</span><span class="sxs-lookup"><span data-stu-id="e4d6b-211">45cm</span></span>  | <span data-ttu-id="e4d6b-212">nicht kleiner als 2 °</span><span class="sxs-lookup"><span data-stu-id="e4d6b-212">no smaller than 2°</span></span> | <span data-ttu-id="e4d6b-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="e4d6b-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="e4d6b-214">![Zielgröße für die direkte Interaktion](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="e4d6b-215">*Zielgröße für direkte Interaktion*</span><span class="sxs-lookup"><span data-stu-id="e4d6b-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="e4d6b-216">Zielgröße für Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="e4d6b-216">Target size for buttons</span></span>

<span data-ttu-id="e4d6b-217">Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass genügend Speicherplatz vorhanden ist, um ein Symbol und potenziell einen Text zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="e4d6b-218">Flüge</span><span class="sxs-lookup"><span data-stu-id="e4d6b-218">Distance</span></span> | <span data-ttu-id="e4d6b-219">Mindestgröße</span><span class="sxs-lookup"><span data-stu-id="e4d6b-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="e4d6b-220">45cm</span><span class="sxs-lookup"><span data-stu-id="e4d6b-220">45cm</span></span>  | <span data-ttu-id="e4d6b-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="e4d6b-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="e4d6b-222">![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="e4d6b-223">*Zielgröße für die Schaltflächen*</span><span class="sxs-lookup"><span data-stu-id="e4d6b-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="e4d6b-224">Zielgröße für die Hand Strahl-oder Blick Interaktion</span><span class="sxs-lookup"><span data-stu-id="e4d6b-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="e4d6b-225">Flüge</span><span class="sxs-lookup"><span data-stu-id="e4d6b-225">Distance</span></span> | <span data-ttu-id="e4d6b-226">Anzeige Winkel</span><span class="sxs-lookup"><span data-stu-id="e4d6b-226">Viewing angle</span></span> | <span data-ttu-id="e4d6b-227">Größe</span><span class="sxs-lookup"><span data-stu-id="e4d6b-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="e4d6b-228">2 min</span><span class="sxs-lookup"><span data-stu-id="e4d6b-228">2m</span></span>  | <span data-ttu-id="e4d6b-229">nicht kleiner als 1 °</span><span class="sxs-lookup"><span data-stu-id="e4d6b-229">no smaller than 1°</span></span> | <span data-ttu-id="e4d6b-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="e4d6b-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="e4d6b-231">![Zielgröße für die Hand Strahl-oder Blick Interaktion](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="e4d6b-232">*Zielgröße für die Hand Strahl-oder Blick Interaktion*</span><span class="sxs-lookup"><span data-stu-id="e4d6b-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="e4d6b-233">Erstellen eines Interaktionen-Objekts mit Mixed Reality Toolkit (mrtk)</span><span class="sxs-lookup"><span data-stu-id="e4d6b-233">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="e4d6b-234">Im **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** finden Sie die Reihe der Unity-Skripts und-präfaben, die Sie beim Erstellen von Objekt übergreifenden Objekten unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-234">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="e4d6b-235">Sie können diese verwenden, um zu ermöglichen, dass Objekte auf verschiedene Typen von Eingabe Interaktions Zuständen reagieren.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-235">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="e4d6b-236">Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e4d6b-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="e4d6b-237">Button</span><span class="sxs-lookup"><span data-stu-id="e4d6b-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="e4d6b-238">Beispiel Szenen für Hand Interaktion</span><span class="sxs-lookup"><span data-stu-id="e4d6b-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="e4d6b-239">Der Standard-Shader von mixedrealitytoolkit bietet verschiedene Optionen, wie z. b. **near Light** , mit denen Sie visuelle und Audiohinweise erstellen können.</span><span class="sxs-lookup"><span data-stu-id="e4d6b-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="e4d6b-240">Mrtk-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="e4d6b-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---

## <a name="see-also"></a><span data-ttu-id="e4d6b-241">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="e4d6b-241">See also</span></span>

* [<span data-ttu-id="e4d6b-242">Begrenzungs Fenster</span><span class="sxs-lookup"><span data-stu-id="e4d6b-242">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e4d6b-243">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="e4d6b-243">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e4d6b-244">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="e4d6b-244">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e4d6b-245">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e4d6b-245">Voice input</span></span>](voice-input.md)
