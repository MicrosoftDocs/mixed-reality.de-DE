---
title: Begrenzungs Bereich und App-Leiste
description: Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungs Bereich
ms.openlocfilehash: 97afc0df02fd8460547e955d4fcf3e33a4e9f566
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105758"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="411eb-104">Begrenzungs Bereich und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="411eb-104">Bounding box and App bar</span></span>
<span data-ttu-id="411eb-105">![umgebenden ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.](images/640px-boundingbox-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="411eb-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/640px-boundingbox-hero.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="411eb-106">Was ist das umgebende Feld?</span><span class="sxs-lookup"><span data-stu-id="411eb-106">What is the Bounding box?</span></span>

<span data-ttu-id="411eb-107">Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="411eb-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="411eb-108">Der Benutzer erhält eine Kosten, die das Objekt momentan anpassbar ist.</span><span class="sxs-lookup"><span data-stu-id="411eb-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="411eb-109">Bei hololens 2 funktioniert das umgebende Feld mit direkter Hand Manipulation und antwortet auf die Nähe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="411eb-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="411eb-110">Es zeigt visuelles Feedback, um dem Benutzer zu helfen, den Abstand zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="411eb-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="411eb-111">Skalieren eines Objekts</span><span class="sxs-lookup"><span data-stu-id="411eb-111">Scaling an object</span></span><br>
        <span data-ttu-id="411eb-112">In den Ecken des umgebenden Felds wird dem Benutzer mitgeteilt, dass das Objekt skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="411eb-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="411eb-113">Die Handles folgen einem weit verbreiteten Muster zur Anpassung der Skalierung.</span><span class="sxs-lookup"><span data-stu-id="411eb-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="411eb-114">Diese visuelle Visualisierung zeigt Benutzern den gesamten Bereich des Objekts an – auch dann, wenn Sie außerhalb eines Anpassungsmodus nicht sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="411eb-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="411eb-115">Dies ist besonders wichtig, da das Objekt, das an ein anderes Objekt oder eine andere Oberfläche angedockt ist, sich so verhält, als ob es sich um ein Leerzeichen handelt, das nicht vorhanden sein sollte.</span><span class="sxs-lookup"><span data-stu-id="411eb-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="411eb-116">*Video Schleife: Skalieren eines Objekts per Begrenzungs Rahmen*</span><span class="sxs-lookup"><span data-stu-id="411eb-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="411eb-117">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="411eb-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="411eb-118">![hololens zeigt das Skalieren eines Objekts über das Begrenzungsfeld an](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="411eb-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="411eb-119">Drehen eines Objekts</span><span class="sxs-lookup"><span data-stu-id="411eb-119">Rotating an object</span></span><br>
        <span data-ttu-id="411eb-120">Die vertikalen rechteckigen Anlagen an den Rändern des umgebenden Felds sind Rotations Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="411eb-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="411eb-121">Dies ermöglicht dem Benutzer eine präzisere Anpassung der platzierten holograms.</span><span class="sxs-lookup"><span data-stu-id="411eb-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="411eb-122">Sie können nicht nur angepasst und skaliert werden, sondern auch jetzt drehen.</span><span class="sxs-lookup"><span data-stu-id="411eb-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="411eb-123">*Video Schleife: Drehen eines Objekts über das umgebende Feld*</span><span class="sxs-lookup"><span data-stu-id="411eb-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="411eb-124">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="411eb-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="411eb-125">![hololens-Sicht, die das Drehen eines Objekts über das umgebende Feld](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="411eb-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="411eb-126">Visuelles Feedback in der Nähe von hololens 2</span><span class="sxs-lookup"><span data-stu-id="411eb-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="411eb-127">Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützt.</span><span class="sxs-lookup"><span data-stu-id="411eb-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="411eb-128">Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst.</span><span class="sxs-lookup"><span data-stu-id="411eb-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="411eb-129">Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="411eb-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="411eb-130">Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.</span><span class="sxs-lookup"><span data-stu-id="411eb-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="411eb-131">*Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*</span><span class="sxs-lookup"><span data-stu-id="411eb-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="411eb-132">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="411eb-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="411eb-133">![Sie visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="411eb-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="411eb-134">**Informationen zur Entwicklung von Unity-apps finden Sie im Abschnitt zum umgebenden [Feld im Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="411eb-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="411eb-135">Was ist die APP-Leiste?</span><span class="sxs-lookup"><span data-stu-id="411eb-135">What is the App bar?</span></span>

<span data-ttu-id="411eb-136">Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="411eb-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="411eb-137">Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von holograms zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="411eb-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="411eb-138">Die APP-Leiste wurde primär als eine Möglichkeit zum Verwalten von platzierten Objekten in der Umgebung eines Benutzers entwickelt.</span><span class="sxs-lookup"><span data-stu-id="411eb-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="411eb-139">In Verbindung mit dem umgebenden Feld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in gemischter Realität ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="411eb-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="411eb-140">Die APP-Leiste folgt dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="411eb-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="411eb-141">Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die APP-Leiste immer auf der Seite der Objekte angezeigt, die dem Benutzer am nächsten ist, wenn sich der Benutzer um das Objekt bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="411eb-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="411eb-142">Obwohl dies kein Abgleich ist, erzielt es effektiv dasselbe Ergebnis. verhindern, dass die Position eines Benutzers Funktionen sperrt oder blockiert, die andernfalls an einem anderen Speicherort in Ihrer Umgebung verfügbar wären.</span><span class="sxs-lookup"><span data-stu-id="411eb-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="411eb-143">*Video Schleife: Durchlaufen eines Hologram, der APP-Leiste folgt*</span><span class="sxs-lookup"><span data-stu-id="411eb-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="411eb-144">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="411eb-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="411eb-145">![durchlaufen eines holograms.</span><span class="sxs-lookup"><span data-stu-id="411eb-145">![Walking around a hologram.</span></span> <span data-ttu-id="411eb-146">Die APP-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="411eb-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="411eb-147">Begrenzungsfeld in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="411eb-147">Bounding box in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="411eb-148">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Prefabs für das umgebende Feld und die APP-Leiste bereit.</span><span class="sxs-lookup"><span data-stu-id="411eb-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="411eb-149">Sie können ein Begrenzungsfeld hinzufügen, indem Sie das BoundingBox.cs-Skript einfach einem beliebigen Objekt zuweisen.</span><span class="sxs-lookup"><span data-stu-id="411eb-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="411eb-150">Mrtk-Begrenzungsfeld</span><span class="sxs-lookup"><span data-stu-id="411eb-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="411eb-151">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="411eb-151">See also</span></span>

* [<span data-ttu-id="411eb-152">Cursor</span><span class="sxs-lookup"><span data-stu-id="411eb-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="411eb-153">Hand Strahl</span><span class="sxs-lookup"><span data-stu-id="411eb-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="411eb-154">Button</span><span class="sxs-lookup"><span data-stu-id="411eb-154">Button</span></span>](button.md)
* [<span data-ttu-id="411eb-155">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="411eb-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="411eb-156">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="411eb-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="411eb-157">Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="411eb-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="411eb-158">Handmenü</span><span class="sxs-lookup"><span data-stu-id="411eb-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="411eb-159">Near-Menü</span><span class="sxs-lookup"><span data-stu-id="411eb-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="411eb-160">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="411eb-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="411eb-161">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="411eb-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="411eb-162">Tastatur</span><span class="sxs-lookup"><span data-stu-id="411eb-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="411eb-163">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="411eb-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="411eb-164">Tafel</span><span class="sxs-lookup"><span data-stu-id="411eb-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="411eb-165">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="411eb-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="411eb-166">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="411eb-166">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="411eb-167">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="411eb-167">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="411eb-168">Oberflächen Magnetismus</span><span class="sxs-lookup"><span data-stu-id="411eb-168">Surface magnetism</span></span>](surface-magnetism.md)