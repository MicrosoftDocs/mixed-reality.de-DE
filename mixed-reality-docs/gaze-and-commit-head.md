---
title: Anvisieren mit dem Kopf und Ausführen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441097"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="7d02e-104">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7d02e-104">Head-gaze and commit</span></span>
<span data-ttu-id="7d02e-105">Der _Kopf-und Commit-_ Vorgang ist ein Sonderfall des "Blick"- [und](gaze-and-commit.md) "Commit"-Eingabe Modells, bei dem ein Objekt mit der Richtung ihrer Kopfzeile (Kopfzeile) als Ziel verwendet wird, und dann mit einer sekundären Eingabe, wie z. b. der Handgesten Luft, behandelt wird. Tippen Sie auf oder den Sprachbefehl "Select".</span><span class="sxs-lookup"><span data-stu-id="7d02e-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="7d02e-106">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="7d02e-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7d02e-107"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="7d02e-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="7d02e-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d02e-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7d02e-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7d02e-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7d02e-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d02e-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7d02e-111">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7d02e-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="7d02e-112">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="7d02e-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="7d02e-113">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="7d02e-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="7d02e-114">➕ Alternative Option</span><span class="sxs-lookup"><span data-stu-id="7d02e-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="7d02e-115">Skalieren von Zielen und Feedback</span><span class="sxs-lookup"><span data-stu-id="7d02e-115">Target sizing and feedback</span></span>
<span data-ttu-id="7d02e-116">Der Kopf Zeilenvektor wurde wiederholt angezeigt, um für die fein Ausrichtung geeignet zu sein. er eignet sich jedoch oft am besten für das erreichen von Brutto Zuweisungs zugriffung.</span><span class="sxs-lookup"><span data-stu-id="7d02e-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="7d02e-117">Die minimalen Zielgrößen von 1 bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7d02e-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="7d02e-118">Beachten Sie, dass die Größe, auf die der Benutzer ausgerichtet ist, auch für 3D-Elemente effektiv ein 2D-Bereich ist. Die ihm jeweils zugewandte Projektion sollte der Zielbereich sein.</span><span class="sxs-lookup"><span data-stu-id="7d02e-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="7d02e-119">Ein Hinweis darauf, dass ein Element "aktiv" ist (der der Benutzer als Ziel verwendet), ist äußerst hilfreich.</span><span class="sxs-lookup"><span data-stu-id="7d02e-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="7d02e-120">Dies kann z. b. z. b. sichtbare "Hover"-Effekte, audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.</span><span class="sxs-lookup"><span data-stu-id="7d02e-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="7d02e-121">![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d02e-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="7d02e-122">*Optimale Zielgröße im Abstand von 2 Metern*</span><span class="sxs-lookup"><span data-stu-id="7d02e-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="7d02e-123">![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d02e-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="7d02e-124">*Beispiel für die Hervorhebung eines anvisierten Objekts*</span><span class="sxs-lookup"><span data-stu-id="7d02e-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="7d02e-125">Zielpositionierung</span><span class="sxs-lookup"><span data-stu-id="7d02e-125">Target placement</span></span>
<span data-ttu-id="7d02e-126">Benutzer können häufig keine UI-Elemente finden, die in ihrer Ansicht sehr hoch oder sehr niedrig angeordnet sind. Sie konzentrieren sich auf Bereiche, die sich in der Nähe des Hauptfokus befinden, also ungefähr in der Perspektive.</span><span class="sxs-lookup"><span data-stu-id="7d02e-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="7d02e-127">Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen.</span><span class="sxs-lookup"><span data-stu-id="7d02e-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="7d02e-128">Angesichts der Tendenz, dass sich der Benutzer jeweils auf einen relativ kleinen visuellen Bereich konzentrieren kann (der Blickwinkel beträgt etwa 10 Grad), kann die Gruppierung von Benutzeroberflächenelementen in dem Maße, in dem sie konzeptionell verwandt sind, das Verhalten zum Kombinieren der Aufmerksamkeit von Element zu Element nutzen, wenn der Blick eines Benutzers durch einen Bereich schweift.</span><span class="sxs-lookup"><span data-stu-id="7d02e-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="7d02e-129">Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.</span><span class="sxs-lookup"><span data-stu-id="7d02e-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="7d02e-130">![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).</span><span class="sxs-lookup"><span data-stu-id="7d02e-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="7d02e-131">*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.</span><span class="sxs-lookup"><span data-stu-id="7d02e-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="7d02e-132">Verbessern des Verhaltens bei der Zielbestimmung</span><span class="sxs-lookup"><span data-stu-id="7d02e-132">Improving targeting behaviors</span></span>
<span data-ttu-id="7d02e-133">Wenn der Benutzer beabsichtigt ist, etwas als Ziel festzustellen, kann es sehr hilfreich sein, fast Fehlversuche bei der Interaktion zu akzeptieren, als wären Sie ordnungsgemäß als Ziel festgelegt.</span><span class="sxs-lookup"><span data-stu-id="7d02e-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="7d02e-134">Im folgenden finden Sie eine Reihe von erfolgreichen Methoden, die in gemischte Realität integriert werden können:</span><span class="sxs-lookup"><span data-stu-id="7d02e-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="7d02e-135">Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)</span><span class="sxs-lookup"><span data-stu-id="7d02e-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="7d02e-136">Dies sollte in den meisten Fällen oder in der Zeit aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="7d02e-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="7d02e-137">Diese Methode entfernt die natürlichen Kopf-und Hals Jitter, die Benutzer möglicherweise durch das Aussehen und Sprech Verhalten durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="7d02e-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="7d02e-138">Algorithmen für die engste Verbindung</span><span class="sxs-lookup"><span data-stu-id="7d02e-138">Closest link algorithms</span></span>
<span data-ttu-id="7d02e-139">Diese funktionieren am besten in Bereichen mit wenig interaktiven Inhalten.</span><span class="sxs-lookup"><span data-stu-id="7d02e-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="7d02e-140">Wenn eine hohe Wahrscheinlichkeit besteht, dass Sie bestimmen können, mit welchem Benutzer versucht wurde, zu interagieren, können Sie die Zielfunktionen ergänzen, indem Sie eine gewisse Absicht annehmen.</span><span class="sxs-lookup"><span data-stu-id="7d02e-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="7d02e-141">Sicherungs-und postdating-Aktionen</span><span class="sxs-lookup"><span data-stu-id="7d02e-141">Backdating and postdating actions</span></span>
<span data-ttu-id="7d02e-142">Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern.</span><span class="sxs-lookup"><span data-stu-id="7d02e-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="7d02e-143">Wenn ein Benutzer mit der Geschwindigkeit eine Reihe von Ziel-und Aktivierungs Manövern durchläuft, ist es sinnvoll, eine Absicht anzunehmen und versäumte Schritte zuzulassen, um auf Ziele zu reagieren, auf die sich der Benutzer vor oder nach dem tippen etwas bewegt hat (50 ms vor/nach war in EA wirksam). RLY-Tests).</span><span class="sxs-lookup"><span data-stu-id="7d02e-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="7d02e-144">Glättung</span><span class="sxs-lookup"><span data-stu-id="7d02e-144">Smoothing</span></span>
<span data-ttu-id="7d02e-145">Dieser Mechanismus eignet sich für die Bewegung von bewegungsbewegungen, wodurch das leichte Jitter und das Wackeln aufgrund natürlicher Kopf Verschiebungs Merkmale reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="7d02e-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="7d02e-146">Bei der Glättung von bewegungsbewegungen durch die Größe und die Entfernung von Bewegungen und nicht über die Zeit.</span><span class="sxs-lookup"><span data-stu-id="7d02e-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="7d02e-147">Magnetismus</span><span class="sxs-lookup"><span data-stu-id="7d02e-147">Magnetism</span></span>
<span data-ttu-id="7d02e-148">Dieser Mechanismus kann sich als allgemeinere Version der nächstgelegenen Verknüpfungs Algorithmen vorstellen: das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache erhöhen der Treffer Felder, egal ob sichtbar oder nicht, wenn Benutzer wahrscheinliche Ziele erreichen, indem Sie einige Kenntnisse des interaktiven Layouts verwenden, um eine bessere Herangehensweise an die Benutzer Absicht.</span><span class="sxs-lookup"><span data-stu-id="7d02e-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="7d02e-149">Dies kann insbesondere bei kleinen Zielen sehr wirkungsvoll sein.</span><span class="sxs-lookup"><span data-stu-id="7d02e-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="7d02e-150">Fokusbindung</span><span class="sxs-lookup"><span data-stu-id="7d02e-150">Focus stickiness</span></span>
<span data-ttu-id="7d02e-151">Wenn Sie bestimmen, auf welche nahe gelegenen interaktiven Elemente der Fokus gelegt werden soll, stellt die Fokus Bindung eine Abweichung für das Element bereit, das momentan fokussiert ist.</span><span class="sxs-lookup"><span data-stu-id="7d02e-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="7d02e-152">Dies trägt dazu bei, das Verhalten von erratischen Fokus Wechselverhalten zu verringern, wenn Sie in einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen schweben</span><span class="sxs-lookup"><span data-stu-id="7d02e-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="7d02e-153">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="7d02e-153">See also</span></span>
* [<span data-ttu-id="7d02e-154">Eye-basierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="7d02e-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="7d02e-155">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="7d02e-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7d02e-156">Bearbeitung von Hand direkt</span><span class="sxs-lookup"><span data-stu-id="7d02e-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7d02e-157">Handgesten</span><span class="sxs-lookup"><span data-stu-id="7d02e-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7d02e-158">"Hand Punkt" und "Commit"</span><span class="sxs-lookup"><span data-stu-id="7d02e-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="7d02e-159">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="7d02e-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7d02e-160">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="7d02e-160">Voice input</span></span>](voice-input.md)



