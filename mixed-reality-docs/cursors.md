---
title: Cursor
description: Ein Cursor oder Indikator Ihres Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, was hololens über seine Absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens (1. Gen), hololens 2, gemischte Realität, Cursor, Zielvorgabe, Blick, Gesten
ms.openlocfilehash: ef011d8400de1e23db3d6fb4b0f2a853d787ae86
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435753"
---
# <a name="cursors"></a><span data-ttu-id="3199f-104">Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-104">Cursors</span></span>

<span data-ttu-id="3199f-105">Ein Cursor oder Indikator Ihres aktuellen Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, wo das Headset seinen aktuellen Fokus hat.</span><span class="sxs-lookup"><span data-stu-id="3199f-105">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="3199f-106">Der Cursor ermöglicht dem Benutzer das Verständnis seines aktuellen Zielpunkts und fungiert als Feedback, um anzugeben, welcher Bereich, welches Hologramm oder welcher Punkt auf die Eingabe reagiert.</span><span class="sxs-lookup"><span data-stu-id="3199f-106">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="3199f-107">Dabei handelt es sich um die digitale Darstellung von, bei der das Gerät die Aufmerksamkeit des Benutzers versteht (obwohl dies möglicherweise nicht der gleiche ist wie das Ermitteln von Informationen über ihre Absichten).</span><span class="sxs-lookup"><span data-stu-id="3199f-107">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="3199f-108">Das vom Cursor bereitgestellte Feedback bietet Benutzern die Möglichkeit, zu sehen, wie das System antwortet, und verwendet dieses Signal als Feedback, um ihre Absicht an das Gerät besser zu vermitteln, und schließlich ist es sicherer, sich über ihre Interaktionen zu informieren.</span><span class="sxs-lookup"><span data-stu-id="3199f-108">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="3199f-109">Es gibt drei Arten von Cursorn: **Finger, Ray**und **Head-Gaze**.</span><span class="sxs-lookup"><span data-stu-id="3199f-109">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="3199f-110">Diese zeigenden Cursor funktionieren mit unterschiedlichen Eingabe Modalitäten für hololens, hololens 2 und immersive Headsets.</span><span class="sxs-lookup"><span data-stu-id="3199f-110">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="3199f-111">Im folgenden finden Sie Anleitungen dazu, welche Art von Cursor für die einzelnen Typen von Headset-und Interaktions Modellen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3199f-111">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="3199f-112">Im Mixed Reality Toolkit (mrtk) haben wir Drag & amp; Drop-cursormodule erstellt, um Sie bei der Erstellung der richtigen Zeige Erfahrung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="3199f-112">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="3199f-113">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="3199f-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3199f-114"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="3199f-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3199f-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3199f-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3199f-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3199f-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3199f-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="3199f-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3199f-118">Finger Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-118">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3199f-119">✔️</span><span class="sxs-lookup"><span data-stu-id="3199f-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="3199f-120">Strahl Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-120">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3199f-121">✔️</span><span class="sxs-lookup"><span data-stu-id="3199f-121">✔️</span></span></td>
        <td><span data-ttu-id="3199f-122">✔️</span><span class="sxs-lookup"><span data-stu-id="3199f-122">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3199f-123">Cursor Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-123">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="3199f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="3199f-124">✔️</span></span></td>
        <td><span data-ttu-id="3199f-125">✔️</span><span class="sxs-lookup"><span data-stu-id="3199f-125">✔️</span></span></td>
        <td><span data-ttu-id="3199f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="3199f-126">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="3199f-127">Finger Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-127">Finger cursor</span></span>
<span data-ttu-id="3199f-128">Der Finger Cursor ist nur in den hololens 2 verfügbar, um den Interaktionsmodus "[direkte Bearbeitung von Hand](direct-manipulation.md)" zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="3199f-128">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="3199f-129">Um besser zu verstehen, wo der Finger zeigt, haben wir Ringe an die Tipps beider Index Fingern angefügt.</span><span class="sxs-lookup"><span data-stu-id="3199f-129">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="3199f-130">Die Ring Größe basiert auf der Nähe des Fingers und der UI-Oberfläche (je näher der Finger, der kleinere Ring) und wird zu einer punkteform verkleinert, wenn der Finger den Kontakt mit der Benutzeroberfläche herstellt.</span><span class="sxs-lookup"><span data-stu-id="3199f-130">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="3199f-131">![fingercursor](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="3199f-131">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="3199f-132">**Visuelle Feedback Zustände von Finger Cursor** 1: der Ring wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="3199f-132">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="3199f-133">2: der Ring richtet sich nach der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="3199f-133">2: The ring aligns with surface.</span></span> <span data-ttu-id="3199f-134">3: der Ring ist senkrecht zum Finger Vektor.</span><span class="sxs-lookup"><span data-stu-id="3199f-134">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="3199f-135">4: kein Ring.</span><span class="sxs-lookup"><span data-stu-id="3199f-135">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="3199f-136">Strahl Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-136">Ray cursor</span></span>
<span data-ttu-id="3199f-137">Ray-Cursors werden an das Ende von weit zeigenden Strahlen angehängt, um die Bearbeitung von Objekten zu ermöglichen, die nicht in der Hand reich sind.</span><span class="sxs-lookup"><span data-stu-id="3199f-137">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="3199f-138">In immersiven Headsets werden die Strahlen von Bewegungs Controllern abgeraten und mit Punkt Cursorn enden.</span><span class="sxs-lookup"><span data-stu-id="3199f-138">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="3199f-139">In hololens 2 nutzen wir das geistige Modell dieser Bewegungs Controller-Strahlen und entworfenen Hand Striche, die aus den Palmen stammen und mit den bei der direkten Bearbeitung verwendeten fingercursorn enden.</span><span class="sxs-lookup"><span data-stu-id="3199f-139">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="3199f-140">![Ray-Cursor Controller](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="3199f-140">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="3199f-141">**Strahl Cursor von Bewegungs Controllern**</span><span class="sxs-lookup"><span data-stu-id="3199f-141">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3199f-142">![Ray-Cursor Hand](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="3199f-142">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="3199f-143">**Strahl Cursor von Händen**</span><span class="sxs-lookup"><span data-stu-id="3199f-143">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="3199f-144">Cursor Cursor</span><span class="sxs-lookup"><span data-stu-id="3199f-144">Head-gaze cursor</span></span>
<span data-ttu-id="3199f-145">Der Head-Gaze-Cursor ist ein Punkt, der an das Ende eines unsichtbaren Kopf Zeigers angefügt wird, der die Position und Drehung des Kopfes verwendet, um zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="3199f-145">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="3199f-146">Zum Ausführen von Aktionen wird dieser Zeige Cursor mit verschiedenen Commit-Eingaben gekoppelt, wie z. b. Air Tap, Voice Commands, Dwell und Button Press.</span><span class="sxs-lookup"><span data-stu-id="3199f-146">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="3199f-147">In hololens 2 ist der Head-Blick am besten mit allen Commit-Eingaben gekoppelt, die nicht per Luft tippen verwendet werden, da es einen Interaktions Konflikt zwischen Luft tippen und fern Strahlen gibt.</span><span class="sxs-lookup"><span data-stu-id="3199f-147">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="3199f-148">![Cursor Hand](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="3199f-148">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="3199f-149">**Cursor Cursor mit Handbewegung**</span><span class="sxs-lookup"><span data-stu-id="3199f-149">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3199f-150">![Head-Gaze-Cursor Stimme](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="3199f-150">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="3199f-151">**Kopf zeiligen Cursor mit Sprachbefehl**</span><span class="sxs-lookup"><span data-stu-id="3199f-151">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="3199f-152">Empfehlungen für die Cursor Anpassung</span><span class="sxs-lookup"><span data-stu-id="3199f-152">Cursor customization recommendations</span></span>
<span data-ttu-id="3199f-153">Wenn Sie das Verhalten und den Anschein von Cursor Feedback anpassen möchten, finden Sie hier einige Entwurfs Empfehlungen:</span><span class="sxs-lookup"><span data-stu-id="3199f-153">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="3199f-154">Cursor Skala</span><span class="sxs-lookup"><span data-stu-id="3199f-154">Cursor scale</span></span>
* <span data-ttu-id="3199f-155">Der Cursor sollte nicht größer sein als die verfügbaren Ziele, sodass Benutzer problemlos mit dem Inhalt interagieren und ihn anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="3199f-155">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="3199f-156">Abhängig von der Umgebung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer aussieht, auch ein wichtiger Aspekt.</span><span class="sxs-lookup"><span data-stu-id="3199f-156">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="3199f-157">Beispielsweise sollte der Cursor nicht zu klein werden, da der Benutzer nicht mehr zu klein ist, sodass er verloren geht.</span><span class="sxs-lookup"><span data-stu-id="3199f-157">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="3199f-158">Beim Skalieren des Cursors sollten Sie eine weiche Animation darauf anwenden, während Sie skaliert wird, um ihr ein organisches Gefühl zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="3199f-158">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="3199f-159">Vermeiden Sie das Blockieren von Inhalt.</span><span class="sxs-lookup"><span data-stu-id="3199f-159">Avoid obstructing content.</span></span> <span data-ttu-id="3199f-160">Holograms machen das Erlebnis als unvergesslich, und der Cursor sollte nicht davon entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="3199f-160">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="3199f-161">Direktionlose Cursor Form</span><span class="sxs-lookup"><span data-stu-id="3199f-161">Directionless cursor shape</span></span>
* <span data-ttu-id="3199f-162">Obwohl es keine Rechte Cursor Form gibt, empfiehlt es sich, eine direktionlose Form wie einen "Tor" zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3199f-162">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="3199f-163">Ein Cursor, der in einer Richtung zeigt (z. b. ein herkömmlicher Pfeilcursor), kann den Benutzer so verwechseln, dass er immer auf diese Weise aussieht.</span><span class="sxs-lookup"><span data-stu-id="3199f-163">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="3199f-164">Eine Ausnahme besteht darin, dass der Cursor verwendet wird, um dem Benutzer Interaktions Anweisungen mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="3199f-164">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="3199f-165">Wenn z. b. Hologramme im Mixed Reality-Betriebssystem skaliert werden, schließt der Cursor temporär Pfeile ein, die den Benutzer darüber informiert, wie Sie seine Hand verschieben, um das Hologram zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="3199f-165">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="3199f-166">Aussehen und Gefühl</span><span class="sxs-lookup"><span data-stu-id="3199f-166">Look and feel</span></span>
* <span data-ttu-id="3199f-167">Ein Ring Diagramm oder ein mit einem Tor gegeformter Cursor funktioniert für viele Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="3199f-167">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="3199f-168">Wählen Sie eine Farbe und eine Form aus, die die von Ihnen erstellten Funktionen am besten repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="3199f-168">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="3199f-169">Cursor sind besonders anfällig für die [Trennung von Farben](hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="3199f-169">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="3199f-170">Ein kleiner Cursor mit ausgewogener Deckkraft sorgt dafür, dass er informativ ist, ohne die visuelle Hierarchie zu dominieren.</span><span class="sxs-lookup"><span data-stu-id="3199f-170">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="3199f-171">Sie sollten die Verwendung von Shadowing oder Highlights hinter dem Cursor erkennen, da Sie Inhalte behindern und von der Aufgabe ablendieren können.</span><span class="sxs-lookup"><span data-stu-id="3199f-171">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="3199f-172">Cursor sollten sich an den Oberflächen in der APP ausrichten und Sie anspiegeln. Dadurch erhält der Benutzer ein Gefühl, dass das System sehen kann, wo er aussieht, aber auch, dass das System seine Umgebung kennt.</span><span class="sxs-lookup"><span data-stu-id="3199f-172">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="3199f-173">Im Mixed Reality-Betriebssystem richtet sich der Cursor z. b. an den Oberflächen der Benutzer Welt, wodurch ein Gefühl der Kenntnis der Welt entsteht, auch wenn der Benutzer nicht direkt in einem Hologram sucht.</span><span class="sxs-lookup"><span data-stu-id="3199f-173">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="3199f-174">Das magnetisch Sperren des Cursors an ein interaktives Element, wenn es sich innerhalb der Nähe befindet, kann dabei helfen, das Vertrauen zu verbessern, dass der Benutzer mit diesem Element interagiert, wenn eine Auswahl Aktion ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="3199f-174">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="3199f-175">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="3199f-175">Visual cues</span></span>
* <span data-ttu-id="3199f-176">Wenn Sie sich auf ein einzelnes Hologramm konzentrieren, sollte Ihr Cursor nur dieses – Hologramm ausrichten und die Form ändern, wenn Sie von diesem – Hologramm Weg gehen.</span><span class="sxs-lookup"><span data-stu-id="3199f-176">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="3199f-177">Dies kann dem Benutzer vermitteln, dass das – Hologramm handlungsfähig ist und mit ihm interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="3199f-177">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="3199f-178">Wenn Ihre Anwendung eine räumliche Zuordnung verwendet, könnte der Cursor jede sichtbare Oberfläche ausrichten und umarmen.</span><span class="sxs-lookup"><span data-stu-id="3199f-178">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="3199f-179">Dadurch erhalten die Benutzer Feedback, dass hololens und Ihre Anwendung Ihren Speicherplatz sehen können.</span><span class="sxs-lookup"><span data-stu-id="3199f-179">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="3199f-180">Dadurch wird die Tatsache verstärkt, dass holograms Real und in unserer Welt sind und die Lücke zwischen Real und Virtual überbrücken.</span><span class="sxs-lookup"><span data-stu-id="3199f-180">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="3199f-181">Sehen Sie sich an, was der Cursor tun soll, wenn keine holograms oder Oberflächen in der Ansicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="3199f-181">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="3199f-182">Eine Möglichkeit besteht darin, den Benutzer in einem vordefinierten Abstand vor dem Benutzer zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="3199f-182">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="3199f-183">Mögliche Aktionen</span><span class="sxs-lookup"><span data-stu-id="3199f-183">Possible actions</span></span>
* <span data-ttu-id="3199f-184">Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein – Hologramm ausführen kann, z. b. Skalierung oder Drehung.</span><span class="sxs-lookup"><span data-stu-id="3199f-184">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="3199f-185">Fügen Sie dem Cursor nur dann zusätzliche Informationen hinzu, wenn er etwas für den Benutzer bedeutet.</span><span class="sxs-lookup"><span data-stu-id="3199f-185">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="3199f-186">Andernfalls bemerken die Benutzer möglicherweise nicht, dass sich der Status ändert, oder Sie werden durch den Cursor verwirrt.</span><span class="sxs-lookup"><span data-stu-id="3199f-186">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="3199f-187">Eingabe Status</span><span class="sxs-lookup"><span data-stu-id="3199f-187">Input state</span></span>
* <span data-ttu-id="3199f-188">Der Cursor kann verwendet werden, um den Eingabe Zustand oder die Absicht des Benutzers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3199f-188">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="3199f-189">Beispielsweise könnte ein Symbol angezeigt werden, das dem Benutzer mitteilt, dass das System seinen Hand Zustand hat und die Anwendung weiß, dass Sie bereit sind, Maßnahmen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="3199f-189">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="3199f-190">Wir könnten auch den Cursor verwenden, um Benutzern anzuzeigen, dass Sprachbefehle vom System über eine vorübergehende Farbe changehört wurden.</span><span class="sxs-lookup"><span data-stu-id="3199f-190">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="3199f-191">Die folgenden Cursor Zustände können auf unterschiedliche Weise implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="3199f-191">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="3199f-192">Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustands Automat modellieren.</span><span class="sxs-lookup"><span data-stu-id="3199f-192">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="3199f-193">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3199f-193">For example:</span></span>
    * <span data-ttu-id="3199f-194">Im Leerlaufzustand wird der Standard Cursor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3199f-194">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="3199f-195">Der Status "bereit" ist, wenn Sie festgestellt haben, dass die Benutzer die Hand in der Bereitschaft haben.</span><span class="sxs-lookup"><span data-stu-id="3199f-195">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="3199f-196">Der Interaktions Zustand ist, wenn der Benutzer eine bestimmte Interaktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="3199f-196">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="3199f-197">Der Status "mögliche Aktionen" oder "Hover" ist, wenn Sie mögliche Aktionen übermitteln, die für ein Hologram ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="3199f-197">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="3199f-198">Sie können diese Zustände auch auf die gleiche Weise implementieren, sodass Sie unterschiedliche Kunstobjekte anzeigen können, wenn verschiedene Zustände erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="3199f-198">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="3199f-199">"Cursor frei"</span><span class="sxs-lookup"><span data-stu-id="3199f-199">Going "cursor-free"</span></span>
<span data-ttu-id="3199f-200">Das Entwerfen ohne Cursor wird empfohlen, wenn das Eintauchen eine wichtige Komponente einer-Funktion ist und wenn für das zeigen von Interaktionen (durchschauen und Gesten) keine hohe Genauigkeit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="3199f-200">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="3199f-201">Das System muss immer noch die Anforderungen erfüllen, die normalerweise von einem Cursor erfüllt werden, indem Benutzern Kontinuierliches Feedback zum Verständnis des Systems bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="3199f-201">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="3199f-202">Dies kann durch andere spürbare Zustandsänderungen erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="3199f-202">This may be achievable through other noticeable state changes.</span></span>

<br>

---


## <a name="see-also"></a><span data-ttu-id="3199f-203">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="3199f-203">See also</span></span>
* [<span data-ttu-id="3199f-204">Gesten</span><span class="sxs-lookup"><span data-stu-id="3199f-204">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="3199f-205">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="3199f-205">Head-gaze and commit</span></span>](gaze-and-commit.md)
