---
title: Zeigen und Ausführen mit den Händen
description: Übersicht über das Eingabemodell „Zeigen und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Interaktion, Design, HoloLens, Hände, fern, Zeigen und Ausführen
ms.openlocfilehash: e454b7f26b402d5c168323762865d10f7feb8a17
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437638"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="c360b-104">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="c360b-104">Point and commit with hands</span></span>

<span data-ttu-id="c360b-105">„Zeigen und Ausführen mit den Händen“ ist ein Eingabemodell, mit dem Benutzer auf 2D-Inhalte und 3D-Objekte zielen, die außerhalb der Reichweite liegen, diese auswählen und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="c360b-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="c360b-106">Diese „ferne“ Interaktionstechnik gibt es nur in der Mixed Reality-Umgebung; sie entspricht nicht der Art und Weise, in der Menschen normalerweise mit der realen Welt in Interaktion treten.</span><span class="sxs-lookup"><span data-stu-id="c360b-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="c360b-107">Im Superhelden-Film *X-Men* beispielsweise kann die Figur [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) mit seinen Händen aus der Entfernung nach einem fernen Objekt greifen und dieses manipulieren.</span><span class="sxs-lookup"><span data-stu-id="c360b-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="c360b-108">Dies ist etwas, was Menschen in der Realität nicht können.</span><span class="sxs-lookup"><span data-stu-id="c360b-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="c360b-109">In HoloLens (AR) und Mixed Reality (MR) statten wir Benutzer mit diesen magischen Kräften aus und setzen dabei die Grenzen der Physik in der realen Welt außer Kraft. Ziel ist nicht nur ein positives Erlebnis mit holografischen Inhalten, sondern auch eine effektivere und effizientere Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="c360b-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="c360b-110">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="c360b-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="c360b-111"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="c360b-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="c360b-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c360b-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="c360b-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c360b-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="c360b-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="c360b-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="c360b-115">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="c360b-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="c360b-116">❌ Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="c360b-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="c360b-117">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="c360b-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="c360b-118">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="c360b-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="c360b-119">_„Zeigen und Ausführen mit Händen“_ ist eines der neuen Features, welches das neue bewegliche Handverfolgungssystem verwendet.</span><span class="sxs-lookup"><span data-stu-id="c360b-119">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="c360b-120">Dieses Eingabemodell ist auch das primäre Eingabemodell bei immersiven Headsets und Verwendung von Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="c360b-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="c360b-121">Handlichtstrahl</span><span class="sxs-lookup"><span data-stu-id="c360b-121">Hand rays</span></span>

<span data-ttu-id="c360b-122">In HoloLens 2 haben wir einen Lichtstrahl erzeugt, der aus der Mitte der Handfläche des Benutzers schießt.</span><span class="sxs-lookup"><span data-stu-id="c360b-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="c360b-123">Dieser Lichtstrahl wird als Erweiterung der Hand behandelt.</span><span class="sxs-lookup"><span data-stu-id="c360b-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="c360b-124">Ein ringförmiger Cursor befindet sich am Ende des Strahls, um den Punkt anzugeben, an dem der Strahl das Zielobjekt schneidet.</span><span class="sxs-lookup"><span data-stu-id="c360b-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="c360b-125">Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen.</span><span class="sxs-lookup"><span data-stu-id="c360b-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="c360b-126">Dieser grundlegende gestische Befehl wird mit dem Daumen und dem Zeigefinger ausgelöst, um das Tippen in die Luft auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c360b-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="c360b-127">Mithilfe des Handstrahls zum Zeigen und dem Tippen in die Luft zum Ausführen kann der Benutzer eine Schaltfläche oder einen Link aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c360b-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="c360b-128">Mit weiteren zusammengesetzten Gesten kann der Benutzer durch Webinhalte navigieren und 3D-Objekte aus der Entfernung bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="c360b-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="c360b-129">Das visuelle Design des Handlichtstrahls sollte auch auf die Zustände beim Zeigen und Ausführen reagieren, wie nachstehend beschrieben und gezeigt:</span><span class="sxs-lookup"><span data-stu-id="c360b-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="c360b-130">![Zeigen mit Handstrahlen](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-130">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="c360b-131">**Status „Zeigen“**</span><span class="sxs-lookup"><span data-stu-id="c360b-131">**Pointing state**</span></span><br>
        <span data-ttu-id="c360b-132">Im Status *Zeigen* ist der Lichtstrahl eine gestrichelte Linie, und der Cursor hat die Form eines Rings.</span><span class="sxs-lookup"><span data-stu-id="c360b-132">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c360b-133">![Ausführen mit Handstrahlen](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-133">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="c360b-134">**Status „Ausführen“**</span><span class="sxs-lookup"><span data-stu-id="c360b-134">**Commit state**</span></span><br>
        <span data-ttu-id="c360b-135">Im Status *Ausführen* wird der Lichtstrahl zu einer durchgezogenen Linie, und der Cursor wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="c360b-135">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="c360b-136">Übergang zwischen nah und fern</span><span class="sxs-lookup"><span data-stu-id="c360b-136">Transition between near and far</span></span>

<span data-ttu-id="c360b-137">Statt bestimmte Gesten zu verwenden (z. B. „Zeigen mit dem Zeigefinger" zum Richten des Lichtstrahls), haben wir den Lichtstrahl so entworfen, dass er aus der Mitte der Handfläche kommt, wodurch die fünf Finger frei gehalten und für manipulativere Gesten (z. B. Finger zusammenführen und greifen) reserviert werden konnten.</span><span class="sxs-lookup"><span data-stu-id="c360b-137">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="c360b-138">Mit diesem Entwurf erstellen wir nur ein mentales Modell. Derselbe Satz von Gesten wird für nahe und ferne Interaktionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="c360b-138">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="c360b-139">So können Sie die gleiche Greifgeste zum Bearbeiten von Objekten aus unterschiedlichen Entfernungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="c360b-139">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="c360b-140">Der Aufruf des Lichtstrahls erfolgt automatisch und basiert auf der Entfernung, wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c360b-140">The invocation of the rays is automatic and proximity based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c360b-141">![Manipulation in der Nähe](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-141">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="c360b-142">**Manipulation in der Nähe**</span><span class="sxs-lookup"><span data-stu-id="c360b-142">**Near manipulation**</span></span><br>
        <span data-ttu-id="c360b-143">Wenn sich ein Objekt in Armeslänge befindet (ungefähr 50 cm), wird der Lichtstrahl automatisch deaktiviert und regt so die Interaktion aus der Nähe an.</span><span class="sxs-lookup"><span data-stu-id="c360b-143">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c360b-144">![Manipulation in der Ferne](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-144">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="c360b-145">**Manipulation in der Ferne**</span><span class="sxs-lookup"><span data-stu-id="c360b-145">**Far manipulation**</span></span><br>
        <span data-ttu-id="c360b-146">Wenn das Objekt mehr als 50 cm entfernt ist, wird der Lichtstrahl aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c360b-146">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="c360b-147">Der Übergang sollte reibungslos und nahtlos erfolgen.</span><span class="sxs-lookup"><span data-stu-id="c360b-147">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="c360b-148">2D-Tafel – Interaktion</span><span class="sxs-lookup"><span data-stu-id="c360b-148">2D slate interaction</span></span>

<span data-ttu-id="c360b-149">Eine 2D-Tafel ist ein holografischer Container, der 2D-App-Inhalte hostet (z. B. einen Webbrowser).</span><span class="sxs-lookup"><span data-stu-id="c360b-149">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="c360b-150">Das Entwurfskonzept für die ferne Interaktion mit einer 2D-Tafel verwendet den Handlichtstrahl zum Zielen und das Tippen in die Luft zum Auswählen.</span><span class="sxs-lookup"><span data-stu-id="c360b-150">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="c360b-151">Nach dem Zielen mit dem Handlichtstrahl kann der Benutzer in die Luft tippen, um einen Link oder eine Schaltfläche auszulösen.</span><span class="sxs-lookup"><span data-stu-id="c360b-151">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="c360b-152">Sie können eine Hand zum „Tippen in die Luft und Ziehen“ verwenden, um den Inhalt einer Tafel nach oben und unten zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="c360b-152">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="c360b-153">Mit der relativen Bewegung und der Verwendung von zwei Händen zum „Tippen in die Luft und Ziehen“ können Sie den Inhalt der Tafel vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="c360b-153">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="c360b-154">Wenn Sie mit dem Handlichtstrahl in die Ecken und auf die Kanten zielen, wird das naheliegendste Bearbeitungsangebot angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c360b-154">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="c360b-155">Mit den Bearbeitungsangeboten „Greifen und Ziehen“ kann der Benutzer über das Eckenangebot eine einheitliche Skalierung ausführen und über das Kantenangebot die Tafel neu formatieren.</span><span class="sxs-lookup"><span data-stu-id="c360b-155">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="c360b-156">Durch Greifen und Ziehen der Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.</span><span class="sxs-lookup"><span data-stu-id="c360b-156">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c360b-157">![2D-Tafel – Interaktion „Klicken“](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-157">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="c360b-158">**Klicken**</span><span class="sxs-lookup"><span data-stu-id="c360b-158">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c360b-159">![2D-Tafel – Interaktion „Scrollen“](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-159">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="c360b-160">**Scrollen**</span><span class="sxs-lookup"><span data-stu-id="c360b-160">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c360b-161">![2D-Tafel – Interaktion „Zoomen“](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-161">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="c360b-162">**Zoomen**</span><span class="sxs-lookup"><span data-stu-id="c360b-162">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="c360b-163">**So bearbeiten Sie die 2D-Tafel**</span><span class="sxs-lookup"><span data-stu-id="c360b-163">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="c360b-164">Der Benutzer zeigt mit dem Handlichtstrahl in die Ecken oder auf die Kanten, um das naheliegendste Bearbeitungsangebot anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c360b-164">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="c360b-165">Durch das Anwenden einer Bearbeitungsgeste kann der Benutzer über das Eckenangebot eine einheitliche Skalierung und über das Kantenangebot eine Formatierung der Tafel vornehmen.</span><span class="sxs-lookup"><span data-stu-id="c360b-165">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="c360b-166">Durch das Anwenden einer Bearbeitungsgeste auf die Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.</span><span class="sxs-lookup"><span data-stu-id="c360b-166">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="c360b-167">3D-Objektbearbeitung</span><span class="sxs-lookup"><span data-stu-id="c360b-167">3D object manipulation</span></span>

<span data-ttu-id="c360b-168">Bei der direkten Bearbeitung hat der Benutzer zwei Möglichkeiten zum Bearbeiten von 3D-Objekten: angebotsbasierte Bearbeitung und Bearbeitung ohne Angebot.</span><span class="sxs-lookup"><span data-stu-id="c360b-168">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="c360b-169">Beim Modell „Zeigen und Ausführen“ kann der Benutzer genau die gleichen Aufgaben über den Handlichtstrahl ausführen.</span><span class="sxs-lookup"><span data-stu-id="c360b-169">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="c360b-170">Es ist keine zusätzliche Schulung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c360b-170">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="c360b-171">Angebotsbasierte Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="c360b-171">Affordance-based manipulation</span></span>
<span data-ttu-id="c360b-172">Der Benutzer verwendet den Handlichtstrahl zum Zeigen und Anzeigen des Begrenzungsrahmens und der Bearbeitungsangebote.</span><span class="sxs-lookup"><span data-stu-id="c360b-172">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="c360b-173">Der Benutzer kann die Bearbeitungsgeste auf den Begrenzungsrahmen anwenden, um das gesamte Objekt zu verschieben, auf die Kantenangebote, um das Objekt zu drehen, und auf die Eckenangebote, um eine einheitliche Skalierung vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="c360b-173">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="c360b-174">![3D-Objektbearbeitung – Verschieben aus größerer Entfernung](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-174">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="c360b-175">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="c360b-175">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c360b-176">![3D-Objektbearbeitung – Drehen aus größerer Entfernung](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-176">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="c360b-177">**Drehen**</span><span class="sxs-lookup"><span data-stu-id="c360b-177">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c360b-178">![3D-Objektbearbeitung – Skalieren aus größerer Entfernung](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-178">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="c360b-179">**Skalieren**</span><span class="sxs-lookup"><span data-stu-id="c360b-179">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="c360b-180">Bearbeitung ohne Angebot</span><span class="sxs-lookup"><span data-stu-id="c360b-180">Non-affordance based manipulation</span></span>
<span data-ttu-id="c360b-181">Der Benutzer zeigt mit dem Handlichtstrahl, um den Begrenzungsrahmen anzuzeigen, und wendet dann direkt Bearbeitungsgesten darauf an.</span><span class="sxs-lookup"><span data-stu-id="c360b-181">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="c360b-182">Mit einer Hand sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="c360b-182">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="c360b-183">Mit zwei Händen kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.</span><span class="sxs-lookup"><span data-stu-id="c360b-183">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="c360b-184">Instinktive Gesten</span><span class="sxs-lookup"><span data-stu-id="c360b-184">Instinctual gestures</span></span>
<span data-ttu-id="c360b-185">Das Konzept der instinktiven Gesten für „Zeigen und Ausführen“ entspricht dem für die [direkte Bearbeitung mit den Händen](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="c360b-185">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="c360b-186">Die Gesten, die der Benutzer bei einem 3D-Objekt ausführt, werden über das Design der Benutzeroberflächenangebote gesteuert.</span><span class="sxs-lookup"><span data-stu-id="c360b-186">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="c360b-187">Ein kleiner Steuerpunkt beispielsweise kann den Benutzer motivieren, Daumen und Zeigefinger zusammenzuführen, während ein anderer Benutzer möglicherweise ein größeres Objekt mit allen fünf Fingern greifen möchte.</span><span class="sxs-lookup"><span data-stu-id="c360b-187">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c360b-188">![Instinktive Gesten – Kleines Objekt aus größerer Entfernung](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-188">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="c360b-189">**Kleines Objekt**</span><span class="sxs-lookup"><span data-stu-id="c360b-189">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c360b-190">![Instinktive Gesten – Mittelgroßes Objekt aus größerer Entfernung](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-190">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="c360b-191">**Mittelgroßes Objekt**</span><span class="sxs-lookup"><span data-stu-id="c360b-191">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c360b-192">![Instinktive Gesten – Großes Objekt aus größerer Entfernung](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-192">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="c360b-193">**Großes Objekt**</span><span class="sxs-lookup"><span data-stu-id="c360b-193">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="c360b-194">Symmetrisches Design für Händen und Controller mit 6 Freiheitsgraden</span><span class="sxs-lookup"><span data-stu-id="c360b-194">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="c360b-195">Das Konzept „Zeigen und Ausführen“ für die ferne Interaktion wurde anfänglich für das Mixed Reality-Portal (MRP) erstellt, in dem ein Benutzer ein immersives Headset trägt und über Motion-Controller mit 3D-Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="c360b-195">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="c360b-196">Zum Zeigen auf und Bearbeiten von fernen Objekten schießen die Motion-Controller einen Lichtstrahl ab.</span><span class="sxs-lookup"><span data-stu-id="c360b-196">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="c360b-197">zum Ausführen weiterer unterschiedlicher Aktionen gibt es Tasten auf den Controllern.</span><span class="sxs-lookup"><span data-stu-id="c360b-197">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="c360b-198">Wir nutzen das Interaktionsmodell des Lichtstrahls und haben dieses mit den beiden Händen verbunden.</span><span class="sxs-lookup"><span data-stu-id="c360b-198">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="c360b-199">Bei diesem symmetrischen Entwurf braucht der Benutzer, der sich mit MRP auskennt, kein anderes Interaktionsmodell für das Zeigen auf und Bearbeiten von fernen Objekten zu lernen, wenn er HoloLen 2 verwendet (und umgekehrt).</span><span class="sxs-lookup"><span data-stu-id="c360b-199">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="c360b-200">![Symmetrischer Entwurf für Lichtstrahlen mit Controllern](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-200">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="c360b-201">**Controllerlichtstrahlen**</span><span class="sxs-lookup"><span data-stu-id="c360b-201">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c360b-202">![Symmetrischer Entwurf für Lichtstrahlen mit Händen](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="c360b-202">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="c360b-203">**Handlichtstrahl**</span><span class="sxs-lookup"><span data-stu-id="c360b-203">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="c360b-204">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c360b-204">See also</span></span>
* [<span data-ttu-id="c360b-205">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="c360b-205">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c360b-206">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="c360b-206">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c360b-207">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="c360b-207">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c360b-208">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="c360b-208">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="c360b-209">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="c360b-209">Instinctual interactions</span></span>](interaction-fundamentals.md)