---
title: Es-Objekt
description: Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt. In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Benutzeroberfläche, ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594761"
---
# <a name="interactable-object"></a><span data-ttu-id="6c102-105">Es-Objekt</span><span class="sxs-lookup"><span data-stu-id="6c102-105">Interactable object</span></span>

<span data-ttu-id="6c102-106">Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt.</span><span class="sxs-lookup"><span data-stu-id="6c102-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="6c102-107">In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="6c102-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="6c102-108">Alles möglich ein **es Objekt** , die ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="6c102-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="6c102-109">Ein Objekt es kann als etwas von einer Tasse Kaffee für die Tabelle, eine Gleitkommazahl in der Luft Sprechblase dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6c102-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="6c102-110">Wir weiterhin die Stelle, mit der herkömmlichen Schaltflächen in bestimmten Situation wie Dialogfeld Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="6c102-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="6c102-111">Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.</span><span class="sxs-lookup"><span data-stu-id="6c102-111">The visual representation of the button depends on the context.</span></span>

![Interactible Objekt Hero-Bild](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="6c102-113">In der  **[Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, wir haben eine Reihe von Unity-Skripts erstellt und prefabs (Vorlagen), mit denen Sie es Objekte erstellen.</span><span class="sxs-lookup"><span data-stu-id="6c102-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="6c102-114">Sie können diese verwenden, um jede Art von Objekt zu erstellen, die der Benutzer mit dem Sie interagieren können diese Zustände standard Interaktion mit: Beobachtung, als Ziel dienen und gedrückt.</span><span class="sxs-lookup"><span data-stu-id="6c102-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="6c102-115">Sie können das visuelle Design problemlos in Ihre eigenen Ressourcen anpassen.</span><span class="sxs-lookup"><span data-stu-id="6c102-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="6c102-116">Ausführliche Animationen können angepasst werden, durch das Erstellen und Zuweisen der entsprechenden Animation-Clips für die Interaktion-Zustände, in der Unity Animationscontroller oder Offset und Skalierung.</span><span class="sxs-lookup"><span data-stu-id="6c102-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="6c102-117">Visuelles Feedback für die Interaktion mit anderen Eingabe-Status</span><span class="sxs-lookup"><span data-stu-id="6c102-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="6c102-118">In mixed Reality da die holographic Objekte mit der realen Umgebung gemischt werden ist möglicherweise schwer zu verstehen, welche Objekte, es sind.</span><span class="sxs-lookup"><span data-stu-id="6c102-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="6c102-119">Für es Objekte in Ihrer Umgebung ist es wichtig, um differenzierte visuelles Feedback bereitzustellen, für jede Zustand.</span><span class="sxs-lookup"><span data-stu-id="6c102-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="6c102-120">Dadurch werden die Benutzer wissen, welcher Teil Ihrer Erfahrung ist es, und macht den Benutzer mit konsistenten Interaktion Methode sicher.</span><span class="sxs-lookup"><span data-stu-id="6c102-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="6c102-121">Für alle Objekte kann dieser Benutzer mit interagieren wird empfohlen, um verschiedene visuelles Feedback zu erhalten, für die anderen drei Zustände Eingabe:</span><span class="sxs-lookup"><span data-stu-id="6c102-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="6c102-122">**Beobachtung**: Im Leerlauf Standardzustand des Objekts.</span><span class="sxs-lookup"><span data-stu-id="6c102-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="6c102-123">**Ziel**: Wenn das Objekt mit Blicke Cursor gerichtet ist, finger Nähe oder der Bewegungsqualität Controllers Zeiger.</span><span class="sxs-lookup"><span data-stu-id="6c102-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="6c102-124">**Gedrückt**: Wenn das Objekt mit der tippbewegung Geste, drücken Sie die Finger oder während der Übertragung des Controllers auswählen-Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="6c102-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="6c102-125">![Schaltfläche "holographic"](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c102-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="6c102-126">*Beobachtung Zustand, Status ausgerichtet und gedrückt-Status*</span><span class="sxs-lookup"><span data-stu-id="6c102-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="6c102-127">In Windows Mixed Reality finden Sie die Beispiele für Eingabe Zustände im Startmenü und Schaltflächen der Anwendungsleiste visualisieren.</span><span class="sxs-lookup"><span data-stu-id="6c102-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="6c102-128">Sie können Techniken wie z. B. Hervorhebung oder Skalierung verwenden, von visuellem Feedback auf Eingabe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="6c102-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="6c102-129">HoloLens-2 da dieser vollständig angezeigte manuell nachverfolgen Eingabe unterstützt können wir zusätzliche visueller Hinweise auf der Grundlage der Nähe an die Hand bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6c102-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="6c102-130">Die [-Schaltfläche in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) wird in diesem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="6c102-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Schaltfläche "pressable"](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="6c102-132">Beispiele für die es-Objekt</span><span class="sxs-lookup"><span data-stu-id="6c102-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="6c102-133">Mesh-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="6c102-133">Mesh button</span></span>

![Mesh-Schaltfläche](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="6c102-135">Hierbei handelt es sich um Beispiele für die Verwendung von primitiven und importierten 3D-Gitterobjekten als es Objekte.</span><span class="sxs-lookup"><span data-stu-id="6c102-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="6c102-136">Sie können ganz einfach verschiedene skalieren "," Offset "und" Color-Werte auf jeder Eingabe Interaktionszustand reagieren zuweisen.</span><span class="sxs-lookup"><span data-stu-id="6c102-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="6c102-137">Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="6c102-137">Toolbar</span></span>

![Symbolleiste](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="6c102-139">Eine Symbolleiste ist ein häufig verwendetes Muster in mixed Reality-Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="6c102-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="6c102-140">Es ist eine einfache Auflistung von Schaltflächen mit zusätzlichen Verhaltensweisen wie z. B. [Billboarding und Tag-along](billboarding-and-tag-along.md).</span><span class="sxs-lookup"><span data-stu-id="6c102-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="6c102-141">Dieses Beispiel verwendet ein Billboarding und Tag-along-Skript aus dem MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="6c102-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="6c102-142">Sie können steuern, ausführliche Verhaltensweisen einschließlich Entfernung, Geschwindigkeit und Schwellenwerte verschieben.</span><span class="sxs-lookup"><span data-stu-id="6c102-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="6c102-143">Herkömmliches Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="6c102-143">Traditional button</span></span>

![Herkömmliches Schaltflächen](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="6c102-145">Dieses Beispiel zeigt eine herkömmliche 2D-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="6c102-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="6c102-146">Jeder Eingabe Status verfügt über eine etwas andere Tiefe und Animationseigenschaft.</span><span class="sxs-lookup"><span data-stu-id="6c102-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="6c102-147">Weitere Beispiele</span><span class="sxs-lookup"><span data-stu-id="6c102-147">Other examples</span></span>

<span data-ttu-id="6c102-148">![Schaltfläche](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c102-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="6c102-149">*Schaltfläche*</span><span class="sxs-lookup"><span data-stu-id="6c102-149">*Push button*</span></span>
<br>
<span data-ttu-id="6c102-150">![Echten Leben-Objekt](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c102-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="6c102-151">*Reale-Objekt*</span><span class="sxs-lookup"><span data-stu-id="6c102-151">*Real life object*</span></span>

<span data-ttu-id="6c102-152">Mit HoloLens können Sie die physischen Speicherplatz nutzen.</span><span class="sxs-lookup"><span data-stu-id="6c102-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="6c102-153">Angenommen Sie, eine Schaltfläche an einer Wand physischen holographic.</span><span class="sxs-lookup"><span data-stu-id="6c102-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="6c102-154">Oder wie etwa einen Kaffee Cup für eine echte Tabelle?</span><span class="sxs-lookup"><span data-stu-id="6c102-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="6c102-155">Importiert aus Modellieren von Software-3D-Modelle können wir ein es Objekt erstellen, die reale Objekt ähnelt.</span><span class="sxs-lookup"><span data-stu-id="6c102-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="6c102-156">Da es sich um ein digitales Objekt ist, können wir magische Interaktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6c102-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="6c102-157">Es Objekt in Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="6c102-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="6c102-158">Sie finden die [Beispiele Interactable Objekt in Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="6c102-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="6c102-159">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6c102-159">See also</span></span>
* [<span data-ttu-id="6c102-160">Pressable Schaltfläche in Mixed Reality-Toolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="6c102-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="6c102-161">Eine objektauflistung</span><span class="sxs-lookup"><span data-stu-id="6c102-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6c102-162">Billboarding und tag-along</span><span class="sxs-lookup"><span data-stu-id="6c102-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
