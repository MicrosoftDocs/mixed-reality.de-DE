---
title: Zeigen und Ausführen mit den Händen
description: Übersicht über das Eingabemodell „Zeigen und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Interaktion, Design, HoloLens, Hände, fern, Zeigen und Ausführen
ms.openlocfilehash: 77c596f5250240d436529e879434a8f508b06732
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105997"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="35e19-104">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="35e19-104">Point and commit with hands</span></span>

![Cursor](images/UX/UX_Hero_HandRay.jpg)

<span data-ttu-id="35e19-106">„Zeigen und Ausführen mit den Händen“ ist ein Eingabemodell, mit dem Benutzer auf 2D-Inhalte und 3D-Objekte zielen, die außerhalb der Reichweite liegen, diese auswählen und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="35e19-106">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="35e19-107">Diese „ferne“ Interaktionstechnik gibt es nur in der Mixed Reality-Umgebung; sie entspricht nicht der Art und Weise, in der Menschen normalerweise mit der realen Welt in Interaktion treten.</span><span class="sxs-lookup"><span data-stu-id="35e19-107">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="35e19-108">Im Superhelden-Film *X-Men* beispielsweise kann die Figur [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) mit seinen Händen aus der Entfernung nach einem fernen Objekt greifen und dieses manipulieren.</span><span class="sxs-lookup"><span data-stu-id="35e19-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="35e19-109">Dies ist etwas, was Menschen in der Realität nicht können.</span><span class="sxs-lookup"><span data-stu-id="35e19-109">This is not something humans can do in reality.</span></span> <span data-ttu-id="35e19-110">In HoloLens (AR) und Mixed Reality (MR) statten wir Benutzer mit diesen magischen Kräften aus und setzen dabei die Grenzen der Physik in der realen Welt außer Kraft. Ziel ist nicht nur ein positives Erlebnis mit holografischen Inhalten, sondern auch eine effektivere und effizientere Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="35e19-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="35e19-111">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="35e19-111">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="35e19-112"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="35e19-112"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="35e19-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="35e19-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="35e19-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="35e19-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="35e19-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="35e19-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="35e19-116">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="35e19-116">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="35e19-117">❌ Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="35e19-117">❌ Not supported</span></span></td>
     <td><span data-ttu-id="35e19-118">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="35e19-118">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="35e19-119">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="35e19-119">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="35e19-120">_„Zeigen und Ausführen mit Händen“_ ist eines der neuen Features, welches das neue bewegliche Handverfolgungssystem verwendet.</span><span class="sxs-lookup"><span data-stu-id="35e19-120">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="35e19-121">Dieses Eingabemodell ist auch das primäre Eingabemodell bei immersiven Headsets und Verwendung von Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="35e19-121">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="35e19-122">Handlichtstrahl</span><span class="sxs-lookup"><span data-stu-id="35e19-122">Hand rays</span></span>

<span data-ttu-id="35e19-123">In HoloLens 2 haben wir einen Lichtstrahl erzeugt, der aus der Mitte der Handfläche des Benutzers schießt.</span><span class="sxs-lookup"><span data-stu-id="35e19-123">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="35e19-124">Dieser Lichtstrahl wird als Erweiterung der Hand behandelt.</span><span class="sxs-lookup"><span data-stu-id="35e19-124">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="35e19-125">Ein ringförmiger Cursor befindet sich am Ende des Strahls, um den Punkt anzugeben, an dem der Strahl das Zielobjekt schneidet.</span><span class="sxs-lookup"><span data-stu-id="35e19-125">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="35e19-126">Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen.</span><span class="sxs-lookup"><span data-stu-id="35e19-126">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="35e19-127">Dieser grundlegende gestische Befehl wird mit dem Daumen und dem Zeigefinger ausgelöst, um das Tippen in die Luft auszuführen.</span><span class="sxs-lookup"><span data-stu-id="35e19-127">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="35e19-128">Mithilfe des Handstrahls zum Zeigen und dem Tippen in die Luft zum Ausführen kann der Benutzer eine Schaltfläche oder einen Link aktivieren.</span><span class="sxs-lookup"><span data-stu-id="35e19-128">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="35e19-129">Mit weiteren zusammengesetzten Gesten kann der Benutzer durch Webinhalte navigieren und 3D-Objekte aus der Entfernung bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="35e19-129">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="35e19-130">Das visuelle Design des Handlichtstrahls sollte auch auf die Zustände beim Zeigen und Ausführen reagieren, wie nachstehend beschrieben und gezeigt:</span><span class="sxs-lookup"><span data-stu-id="35e19-130">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="35e19-131">![Zeigen mit Handstrahlen](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-131">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="35e19-132">**Status „Zeigen“**</span><span class="sxs-lookup"><span data-stu-id="35e19-132">**Pointing state**</span></span><br>
        <span data-ttu-id="35e19-133">Im Status *Zeigen* ist der Lichtstrahl eine gestrichelte Linie, und der Cursor hat die Form eines Rings.</span><span class="sxs-lookup"><span data-stu-id="35e19-133">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="35e19-134">![Ausführen mit Handstrahlen](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-134">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="35e19-135">**Status „Ausführen“**</span><span class="sxs-lookup"><span data-stu-id="35e19-135">**Commit state**</span></span><br>
        <span data-ttu-id="35e19-136">Im Status *Ausführen* wird der Lichtstrahl zu einer durchgezogenen Linie, und der Cursor wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="35e19-136">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="35e19-137">Übergang zwischen nah und fern</span><span class="sxs-lookup"><span data-stu-id="35e19-137">Transition between near and far</span></span>

<span data-ttu-id="35e19-138">Statt bestimmte Gesten zu verwenden (z. B. „Zeigen mit dem Zeigefinger" zum Richten des Lichtstrahls), haben wir den Lichtstrahl so entworfen, dass er aus der Mitte der Handfläche kommt, wodurch die fünf Finger frei gehalten und für manipulativere Gesten (z. B. Finger zusammenführen und greifen) reserviert werden konnten.</span><span class="sxs-lookup"><span data-stu-id="35e19-138">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="35e19-139">Mit diesem Entwurf erstellen wir nur ein mentales Modell. Derselbe Satz von Gesten wird für nahe und ferne Interaktionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="35e19-139">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="35e19-140">So können Sie die gleiche Greifgeste zum Bearbeiten von Objekten aus unterschiedlichen Entfernungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="35e19-140">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="35e19-141">Der Aufruf des Lichtstrahls erfolgt automatisch und basiert auf der Entfernung, wie folgt:</span><span class="sxs-lookup"><span data-stu-id="35e19-141">The invocation of the rays is automatic and proximity based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="35e19-142">![Manipulation in der Nähe](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-142">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="35e19-143">**Manipulation in der Nähe**</span><span class="sxs-lookup"><span data-stu-id="35e19-143">**Near manipulation**</span></span><br>
        <span data-ttu-id="35e19-144">Wenn sich ein Objekt in Armeslänge befindet (ungefähr 50 cm), wird der Lichtstrahl automatisch deaktiviert und regt so die Interaktion aus der Nähe an.</span><span class="sxs-lookup"><span data-stu-id="35e19-144">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="35e19-145">![Manipulation in der Ferne](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-145">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="35e19-146">**Manipulation in der Ferne**</span><span class="sxs-lookup"><span data-stu-id="35e19-146">**Far manipulation**</span></span><br>
        <span data-ttu-id="35e19-147">Wenn das Objekt mehr als 50 cm entfernt ist, wird der Lichtstrahl aktiviert.</span><span class="sxs-lookup"><span data-stu-id="35e19-147">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="35e19-148">Der Übergang sollte reibungslos und nahtlos erfolgen.</span><span class="sxs-lookup"><span data-stu-id="35e19-148">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="35e19-149">2D-Tafel – Interaktion</span><span class="sxs-lookup"><span data-stu-id="35e19-149">2D slate interaction</span></span>

<span data-ttu-id="35e19-150">Eine 2D-Tafel ist ein holografischer Container, der 2D-App-Inhalte hostet (z. B. einen Webbrowser).</span><span class="sxs-lookup"><span data-stu-id="35e19-150">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="35e19-151">Das Entwurfskonzept für die ferne Interaktion mit einer 2D-Tafel verwendet den Handlichtstrahl zum Zielen und das Tippen in die Luft zum Auswählen.</span><span class="sxs-lookup"><span data-stu-id="35e19-151">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="35e19-152">Nach dem Zielen mit dem Handlichtstrahl kann der Benutzer in die Luft tippen, um einen Link oder eine Schaltfläche auszulösen.</span><span class="sxs-lookup"><span data-stu-id="35e19-152">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="35e19-153">Sie können eine Hand zum „Tippen in die Luft und Ziehen“ verwenden, um den Inhalt einer Tafel nach oben und unten zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="35e19-153">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="35e19-154">Mit der relativen Bewegung und der Verwendung von zwei Händen zum „Tippen in die Luft und Ziehen“ können Sie den Inhalt der Tafel vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="35e19-154">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="35e19-155">Wenn Sie mit dem Handlichtstrahl in die Ecken und auf die Kanten zielen, wird das naheliegendste Bearbeitungsangebot angezeigt.</span><span class="sxs-lookup"><span data-stu-id="35e19-155">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="35e19-156">Mit den Bearbeitungsangeboten „Greifen und Ziehen“ kann der Benutzer über das Eckenangebot eine einheitliche Skalierung ausführen und über das Kantenangebot die Tafel neu formatieren.</span><span class="sxs-lookup"><span data-stu-id="35e19-156">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="35e19-157">Durch Greifen und Ziehen der Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.</span><span class="sxs-lookup"><span data-stu-id="35e19-157">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="35e19-158">![2D-Tafel – Interaktion „Klicken“](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-158">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="35e19-159">**Klicken**</span><span class="sxs-lookup"><span data-stu-id="35e19-159">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="35e19-160">![2D-Tafel – Interaktion „Scrollen“](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-160">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="35e19-161">**Scrollen**</span><span class="sxs-lookup"><span data-stu-id="35e19-161">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="35e19-162">![2D-Tafel – Interaktion „Zoomen“](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-162">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="35e19-163">**Zoomen**</span><span class="sxs-lookup"><span data-stu-id="35e19-163">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="35e19-164">**So bearbeiten Sie die 2D-Tafel**</span><span class="sxs-lookup"><span data-stu-id="35e19-164">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="35e19-165">Der Benutzer zeigt mit dem Handlichtstrahl in die Ecken oder auf die Kanten, um das naheliegendste Bearbeitungsangebot anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="35e19-165">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="35e19-166">Durch das Anwenden einer Bearbeitungsgeste kann der Benutzer über das Eckenangebot eine einheitliche Skalierung und über das Kantenangebot eine Formatierung der Tafel vornehmen.</span><span class="sxs-lookup"><span data-stu-id="35e19-166">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="35e19-167">Durch das Anwenden einer Bearbeitungsgeste auf die Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.</span><span class="sxs-lookup"><span data-stu-id="35e19-167">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="35e19-168">3D-Objektbearbeitung</span><span class="sxs-lookup"><span data-stu-id="35e19-168">3D object manipulation</span></span>

<span data-ttu-id="35e19-169">Bei der direkten Bearbeitung hat der Benutzer zwei Möglichkeiten zum Bearbeiten von 3D-Objekten: angebotsbasierte Bearbeitung und Bearbeitung ohne Angebot.</span><span class="sxs-lookup"><span data-stu-id="35e19-169">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="35e19-170">Beim Modell „Zeigen und Ausführen“ kann der Benutzer genau die gleichen Aufgaben über den Handlichtstrahl ausführen.</span><span class="sxs-lookup"><span data-stu-id="35e19-170">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="35e19-171">Es ist keine zusätzliche Schulung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="35e19-171">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="35e19-172">Angebotsbasierte Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="35e19-172">Affordance-based manipulation</span></span>
<span data-ttu-id="35e19-173">Der Benutzer verwendet den Handlichtstrahl zum Zeigen und Anzeigen des Begrenzungsrahmens und der Bearbeitungsangebote.</span><span class="sxs-lookup"><span data-stu-id="35e19-173">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="35e19-174">Der Benutzer kann die Bearbeitungsgeste auf den Begrenzungsrahmen anwenden, um das gesamte Objekt zu verschieben, auf die Kantenangebote, um das Objekt zu drehen, und auf die Eckenangebote, um eine einheitliche Skalierung vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="35e19-174">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="35e19-175">![3D-Objektbearbeitung – Verschieben aus größerer Entfernung](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-175">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="35e19-176">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="35e19-176">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="35e19-177">![3D-Objektbearbeitung – Drehen aus größerer Entfernung](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-177">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="35e19-178">**Drehen**</span><span class="sxs-lookup"><span data-stu-id="35e19-178">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="35e19-179">![3D-Objektbearbeitung – Skalieren aus größerer Entfernung](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-179">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="35e19-180">**Skalieren**</span><span class="sxs-lookup"><span data-stu-id="35e19-180">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="35e19-181">Bearbeitung ohne Angebot</span><span class="sxs-lookup"><span data-stu-id="35e19-181">Non-affordance based manipulation</span></span>
<span data-ttu-id="35e19-182">Der Benutzer zeigt mit dem Handlichtstrahl, um den Begrenzungsrahmen anzuzeigen, und wendet dann direkt Bearbeitungsgesten darauf an.</span><span class="sxs-lookup"><span data-stu-id="35e19-182">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="35e19-183">Mit einer Hand sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="35e19-183">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="35e19-184">Mit zwei Händen kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.</span><span class="sxs-lookup"><span data-stu-id="35e19-184">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="35e19-185">Instinktive Gesten</span><span class="sxs-lookup"><span data-stu-id="35e19-185">Instinctual gestures</span></span>
<span data-ttu-id="35e19-186">Das Konzept der instinktiven Gesten für „Zeigen und Ausführen“ entspricht dem für die [direkte Bearbeitung mit den Händen](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="35e19-186">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="35e19-187">Die Gesten, die der Benutzer bei einem 3D-Objekt ausführt, werden über das Design der Benutzeroberflächenangebote gesteuert.</span><span class="sxs-lookup"><span data-stu-id="35e19-187">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="35e19-188">Ein kleiner Steuerpunkt beispielsweise kann den Benutzer motivieren, Daumen und Zeigefinger zusammenzuführen, während ein anderer Benutzer möglicherweise ein größeres Objekt mit allen fünf Fingern greifen möchte.</span><span class="sxs-lookup"><span data-stu-id="35e19-188">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="35e19-189">![Instinktive Gesten – Kleines Objekt aus größerer Entfernung](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-189">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="35e19-190">**Kleines Objekt**</span><span class="sxs-lookup"><span data-stu-id="35e19-190">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="35e19-191">![Instinktive Gesten – Mittelgroßes Objekt aus größerer Entfernung](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-191">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="35e19-192">**Mittelgroßes Objekt**</span><span class="sxs-lookup"><span data-stu-id="35e19-192">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="35e19-193">![Instinktive Gesten – Großes Objekt aus größerer Entfernung](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-193">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="35e19-194">**Großes Objekt**</span><span class="sxs-lookup"><span data-stu-id="35e19-194">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="35e19-195">Symmetrisches Design für Händen und Controller mit 6 Freiheitsgraden</span><span class="sxs-lookup"><span data-stu-id="35e19-195">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="35e19-196">Das Konzept „Zeigen und Ausführen“ für die ferne Interaktion wurde anfänglich für das Mixed Reality-Portal (MRP) erstellt, in dem ein Benutzer ein immersives Headset trägt und über Motion-Controller mit 3D-Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="35e19-196">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="35e19-197">Zum Zeigen auf und Bearbeiten von fernen Objekten schießen die Motion-Controller einen Lichtstrahl ab.</span><span class="sxs-lookup"><span data-stu-id="35e19-197">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="35e19-198">zum Ausführen weiterer unterschiedlicher Aktionen gibt es Tasten auf den Controllern.</span><span class="sxs-lookup"><span data-stu-id="35e19-198">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="35e19-199">Wir nutzen das Interaktionsmodell des Lichtstrahls und haben dieses mit den beiden Händen verbunden.</span><span class="sxs-lookup"><span data-stu-id="35e19-199">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="35e19-200">Bei diesem symmetrischen Entwurf braucht der Benutzer, der sich mit MRP auskennt, kein anderes Interaktionsmodell für das Zeigen auf und Bearbeiten von fernen Objekten zu lernen, wenn er HoloLen 2 verwendet (und umgekehrt).</span><span class="sxs-lookup"><span data-stu-id="35e19-200">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="35e19-201">![Symmetrischer Entwurf für Lichtstrahlen mit Controllern](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-201">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="35e19-202">**Controllerlichtstrahlen**</span><span class="sxs-lookup"><span data-stu-id="35e19-202">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="35e19-203">![Symmetrischer Entwurf für Lichtstrahlen mit Händen](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="35e19-203">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="35e19-204">**Handlichtstrahl**</span><span class="sxs-lookup"><span data-stu-id="35e19-204">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="35e19-205">Handlichtstrahl in MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="35e19-205">Hand ray in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="35e19-206">Standardmäßig stellt das MRTK einen vorkonfigurierten Handlichtstrahl ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) zur Verfügung, der den gleichen visuellen Status wie der System-Handlichtstrahl der Shell aufweist.</span><span class="sxs-lookup"><span data-stu-id="35e19-206">By default, MRTK provides a hand ray prefab([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="35e19-207">Er wird im Eingabeprofil des MRTK unter „Pointers“ (Zeiger) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="35e19-207">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="35e19-208">In Windows Mixed Reality (immersives Headset) werden dieselben Strahlen auch für die Motion-Controller verwendet.</span><span class="sxs-lookup"><span data-stu-id="35e19-208">In Windows Mixed Reality immersive headset, the same rays are used for the motion controllers as well.</span></span>

* [<span data-ttu-id="35e19-209">MRTK – Zeigerprofil</span><span class="sxs-lookup"><span data-stu-id="35e19-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="35e19-210">MRTK – Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="35e19-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="35e19-211">MRTK – Zeiger</span><span class="sxs-lookup"><span data-stu-id="35e19-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="35e19-212">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="35e19-212">See also</span></span>
* [<span data-ttu-id="35e19-213">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="35e19-213">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="35e19-214">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="35e19-214">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="35e19-215">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="35e19-215">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="35e19-216">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="35e19-216">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="35e19-217">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="35e19-217">Instinctual interactions</span></span>](interaction-fundamentals.md)