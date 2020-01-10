---
title: Cursor
description: Ein Cursor oder Indikator Ihres Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, was hololens über seine Absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens (1. Gen), hololens 2, gemischte Realität, Cursor, Zielvorgabe, Blick, Gesten
ms.openlocfilehash: 969906cb09e100dbdd289d78baba722a4bd32537
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723239"
---
# <a name="cursors"></a><span data-ttu-id="1e646-104">Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-104">Cursors</span></span>

![Cursor](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="1e646-106">Ein Cursor oder Indikator Ihres aktuellen Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, wo das Headset seinen aktuellen Fokus hat.</span><span class="sxs-lookup"><span data-stu-id="1e646-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="1e646-107">Der Cursor ermöglicht dem Benutzer das Verständnis seines aktuellen Zielpunkts und fungiert als Feedback, um anzugeben, welcher Bereich, welches Hologramm oder welcher Punkt auf die Eingabe reagiert.</span><span class="sxs-lookup"><span data-stu-id="1e646-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="1e646-108">Dabei handelt es sich um die digitale Darstellung von, bei der das Gerät die Aufmerksamkeit des Benutzers versteht (obwohl dies möglicherweise nicht der gleiche ist wie das Ermitteln von Informationen über ihre Absichten).</span><span class="sxs-lookup"><span data-stu-id="1e646-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="1e646-109">Das vom Cursor bereitgestellte Feedback bietet Benutzern die Möglichkeit, zu sehen, wie das System antwortet, und verwendet dieses Signal als Feedback, um ihre Absicht an das Gerät besser zu vermitteln, und schließlich ist es sicherer, sich über ihre Interaktionen zu informieren.</span><span class="sxs-lookup"><span data-stu-id="1e646-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="1e646-110">Es gibt drei Arten von Cursorn: **Finger, Ray**und **Head-Gaze**.</span><span class="sxs-lookup"><span data-stu-id="1e646-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="1e646-111">Diese zeigenden Cursor funktionieren mit unterschiedlichen Eingabe Modalitäten für hololens, hololens 2 und immersive Headsets.</span><span class="sxs-lookup"><span data-stu-id="1e646-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="1e646-112">Im folgenden finden Sie Anleitungen dazu, welche Art von Cursor für die einzelnen Typen von Headset-und Interaktions Modellen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1e646-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="1e646-113">Im Mixed Reality Toolkit (mrtk) haben wir Drag & amp; Drop-cursormodule erstellt, um Sie bei der Erstellung der richtigen Zeige Erfahrung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1e646-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="1e646-114">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="1e646-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1e646-115"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="1e646-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1e646-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1e646-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1e646-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1e646-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1e646-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="1e646-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1e646-119">Finger Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1e646-120">✔️</span><span class="sxs-lookup"><span data-stu-id="1e646-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="1e646-121">Strahl Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1e646-122">✔️</span><span class="sxs-lookup"><span data-stu-id="1e646-122">✔️</span></span></td>
        <td><span data-ttu-id="1e646-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1e646-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1e646-124">Cursor Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="1e646-125">✔️</span><span class="sxs-lookup"><span data-stu-id="1e646-125">✔️</span></span></td>
        <td><span data-ttu-id="1e646-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1e646-126">✔️</span></span></td>
        <td><span data-ttu-id="1e646-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1e646-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="1e646-128">Finger Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-128">Finger cursor</span></span>
<span data-ttu-id="1e646-129">Der Finger Cursor ist nur in den hololens 2 verfügbar, um den Interaktionsmodus "[direkte Bearbeitung von Hand](direct-manipulation.md)" zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="1e646-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="1e646-130">Um besser zu verstehen, wo der Finger zeigt, haben wir Ringe an die Tipps beider Index Fingern angefügt.</span><span class="sxs-lookup"><span data-stu-id="1e646-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="1e646-131">Die Ring Größe basiert auf der Nähe des Fingers und der UI-Oberfläche (je näher der Finger, der kleinere Ring) und wird zu einer punkteform verkleinert, wenn der Finger den Kontakt mit der Benutzeroberfläche herstellt.</span><span class="sxs-lookup"><span data-stu-id="1e646-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="1e646-132">![fingercursor](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="1e646-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="1e646-133">**Visuelle Feedback Zustände von Finger Cursor** 1: der Ring wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="1e646-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="1e646-134">2: der Ring richtet sich nach der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="1e646-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="1e646-135">3: der Ring ist senkrecht zum Finger Vektor.</span><span class="sxs-lookup"><span data-stu-id="1e646-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="1e646-136">4: kein Ring.</span><span class="sxs-lookup"><span data-stu-id="1e646-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="1e646-137">Strahl Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-137">Ray cursor</span></span>
<span data-ttu-id="1e646-138">Ray-Cursors werden an das Ende von weit zeigenden Strahlen angehängt, um die Bearbeitung von Objekten zu ermöglichen, die nicht in der Hand reich sind.</span><span class="sxs-lookup"><span data-stu-id="1e646-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="1e646-139">In immersiven Headsets werden die Strahlen von Bewegungs Controllern abgeraten und mit Punkt Cursorn enden.</span><span class="sxs-lookup"><span data-stu-id="1e646-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="1e646-140">In hololens 2 nutzen wir das geistige Modell dieser Bewegungs Controller-Strahlen und entworfenen Hand Striche, die aus den Palmen stammen und mit den bei der direkten Bearbeitung verwendeten fingercursorn enden.</span><span class="sxs-lookup"><span data-stu-id="1e646-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="1e646-141">![Ray-Cursor Controller](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="1e646-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="1e646-142">**Strahl Cursor von Bewegungs Controllern**</span><span class="sxs-lookup"><span data-stu-id="1e646-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e646-143">![Ray-Cursor Hand](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="1e646-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="1e646-144">**Strahl Cursor von Händen**</span><span class="sxs-lookup"><span data-stu-id="1e646-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="1e646-145">Cursor Cursor</span><span class="sxs-lookup"><span data-stu-id="1e646-145">Head-gaze cursor</span></span>
<span data-ttu-id="1e646-146">Der Head-Gaze-Cursor ist ein Punkt, der an das Ende eines unsichtbaren Kopf Zeigers angefügt wird, der die Position und Drehung des Kopfes verwendet, um zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="1e646-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="1e646-147">Zum Ausführen von Aktionen wird dieser Zeige Cursor mit verschiedenen Commit-Eingaben gekoppelt, wie z. b. Air Tap, Voice Commands, Dwell und Button Press.</span><span class="sxs-lookup"><span data-stu-id="1e646-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="1e646-148">In hololens 2 ist der Head-Blick am besten mit allen Commit-Eingaben gekoppelt, die nicht per Luft tippen verwendet werden, da es einen Interaktions Konflikt zwischen Luft tippen und fern Strahlen gibt.</span><span class="sxs-lookup"><span data-stu-id="1e646-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="1e646-149">![Cursor Hand](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="1e646-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="1e646-150">**Cursor Cursor mit Handbewegung**</span><span class="sxs-lookup"><span data-stu-id="1e646-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e646-151">![Head-Gaze-Cursor Stimme](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="1e646-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="1e646-152">**Kopf zeiligen Cursor mit Sprachbefehl**</span><span class="sxs-lookup"><span data-stu-id="1e646-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="1e646-153">Empfehlungen für die Cursor Anpassung</span><span class="sxs-lookup"><span data-stu-id="1e646-153">Cursor customization recommendations</span></span>
<span data-ttu-id="1e646-154">Wenn Sie das Verhalten und den Anschein von Cursor Feedback anpassen möchten, finden Sie hier einige Entwurfs Empfehlungen:</span><span class="sxs-lookup"><span data-stu-id="1e646-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="1e646-155">Cursor Skala</span><span class="sxs-lookup"><span data-stu-id="1e646-155">Cursor scale</span></span>
* <span data-ttu-id="1e646-156">Der Cursor sollte nicht größer sein als die verfügbaren Ziele, sodass Benutzer problemlos mit dem Inhalt interagieren und ihn anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="1e646-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="1e646-157">Abhängig von der Umgebung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer aussieht, auch ein wichtiger Aspekt.</span><span class="sxs-lookup"><span data-stu-id="1e646-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="1e646-158">Beispielsweise sollte der Cursor nicht zu klein werden, da der Benutzer nicht mehr zu klein ist, sodass er verloren geht.</span><span class="sxs-lookup"><span data-stu-id="1e646-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="1e646-159">Beim Skalieren des Cursors sollten Sie eine weiche Animation darauf anwenden, während Sie skaliert wird, um ihr ein organisches Gefühl zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="1e646-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="1e646-160">Vermeiden Sie das Blockieren von Inhalt.</span><span class="sxs-lookup"><span data-stu-id="1e646-160">Avoid obstructing content.</span></span> <span data-ttu-id="1e646-161">Holograms machen das Erlebnis als unvergesslich, und der Cursor sollte nicht davon entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="1e646-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="1e646-162">Direktionlose Cursor Form</span><span class="sxs-lookup"><span data-stu-id="1e646-162">Directionless cursor shape</span></span>
* <span data-ttu-id="1e646-163">Obwohl es keine Rechte Cursor Form gibt, empfiehlt es sich, eine direktionlose Form wie einen "Tor" zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1e646-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="1e646-164">Ein Cursor, der in einer Richtung zeigt (z. b. ein herkömmlicher Pfeilcursor), kann den Benutzer so verwechseln, dass er immer auf diese Weise aussieht.</span><span class="sxs-lookup"><span data-stu-id="1e646-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="1e646-165">Eine Ausnahme besteht darin, dass der Cursor verwendet wird, um dem Benutzer Interaktions Anweisungen mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="1e646-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="1e646-166">Wenn z. b. Hologramme im Mixed Reality-Betriebssystem skaliert werden, schließt der Cursor temporär Pfeile ein, die den Benutzer darüber informiert, wie Sie seine Hand verschieben, um das Hologram zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="1e646-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="1e646-167">Aussehen und Gefühl</span><span class="sxs-lookup"><span data-stu-id="1e646-167">Look and feel</span></span>
* <span data-ttu-id="1e646-168">Ein Ring Diagramm oder ein mit einem Tor gegeformter Cursor funktioniert für viele Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="1e646-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="1e646-169">Wählen Sie eine Farbe und eine Form aus, die die von Ihnen erstellten Funktionen am besten repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="1e646-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="1e646-170">Cursor sind besonders anfällig für die [Trennung von Farben](hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="1e646-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="1e646-171">Ein kleiner Cursor mit ausgewogener Deckkraft sorgt dafür, dass er informativ ist, ohne die visuelle Hierarchie zu dominieren.</span><span class="sxs-lookup"><span data-stu-id="1e646-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="1e646-172">Sie sollten die Verwendung von Shadowing oder Highlights hinter dem Cursor erkennen, da Sie Inhalte behindern und von der Aufgabe ablendieren können.</span><span class="sxs-lookup"><span data-stu-id="1e646-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="1e646-173">Cursor sollten sich an den Oberflächen in der APP ausrichten und Sie anspiegeln. Dadurch erhält der Benutzer ein Gefühl, dass das System sehen kann, wo er aussieht, aber auch, dass das System seine Umgebung kennt.</span><span class="sxs-lookup"><span data-stu-id="1e646-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="1e646-174">Im Mixed Reality-Betriebssystem richtet sich der Cursor z. b. an den Oberflächen der Benutzer Welt, wodurch ein Gefühl der Kenntnis der Welt entsteht, auch wenn der Benutzer nicht direkt in einem Hologram sucht.</span><span class="sxs-lookup"><span data-stu-id="1e646-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="1e646-175">Das magnetisch Sperren des Cursors an ein interaktives Element, wenn es sich innerhalb der Nähe befindet, kann dabei helfen, das Vertrauen zu verbessern, dass der Benutzer mit diesem Element interagiert, wenn eine Auswahl Aktion ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="1e646-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="1e646-176">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="1e646-176">Visual cues</span></span>
* <span data-ttu-id="1e646-177">Wenn Sie sich auf ein einzelnes Hologramm konzentrieren, sollte Ihr Cursor nur dieses – Hologramm ausrichten und die Form ändern, wenn Sie von diesem – Hologramm Weg gehen.</span><span class="sxs-lookup"><span data-stu-id="1e646-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="1e646-178">Dies kann dem Benutzer vermitteln, dass das – Hologramm handlungsfähig ist und mit ihm interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="1e646-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="1e646-179">Wenn Ihre Anwendung eine räumliche Zuordnung verwendet, könnte der Cursor jede sichtbare Oberfläche ausrichten und umarmen.</span><span class="sxs-lookup"><span data-stu-id="1e646-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="1e646-180">Dadurch erhalten die Benutzer Feedback, dass hololens und Ihre Anwendung Ihren Speicherplatz sehen können.</span><span class="sxs-lookup"><span data-stu-id="1e646-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="1e646-181">Dadurch wird die Tatsache verstärkt, dass holograms Real und in unserer Welt sind und die Lücke zwischen Real und Virtual überbrücken.</span><span class="sxs-lookup"><span data-stu-id="1e646-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="1e646-182">Sehen Sie sich an, was der Cursor tun soll, wenn keine holograms oder Oberflächen in der Ansicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="1e646-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="1e646-183">Eine Möglichkeit besteht darin, den Benutzer in einem vordefinierten Abstand vor dem Benutzer zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="1e646-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="1e646-184">Mögliche Aktionen</span><span class="sxs-lookup"><span data-stu-id="1e646-184">Possible actions</span></span>
* <span data-ttu-id="1e646-185">Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein – Hologramm ausführen kann, z. b. Skalierung oder Drehung.</span><span class="sxs-lookup"><span data-stu-id="1e646-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="1e646-186">Fügen Sie dem Cursor nur dann zusätzliche Informationen hinzu, wenn er etwas für den Benutzer bedeutet.</span><span class="sxs-lookup"><span data-stu-id="1e646-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="1e646-187">Andernfalls bemerken die Benutzer möglicherweise nicht, dass sich der Status ändert, oder Sie werden durch den Cursor verwirrt.</span><span class="sxs-lookup"><span data-stu-id="1e646-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="1e646-188">Eingabe Status</span><span class="sxs-lookup"><span data-stu-id="1e646-188">Input state</span></span>
* <span data-ttu-id="1e646-189">Der Cursor kann verwendet werden, um den Eingabe Zustand oder die Absicht des Benutzers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1e646-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="1e646-190">Beispielsweise könnte ein Symbol angezeigt werden, das dem Benutzer mitteilt, dass das System seinen Hand Zustand hat und die Anwendung weiß, dass Sie bereit sind, Maßnahmen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="1e646-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="1e646-191">Wir könnten auch den Cursor verwenden, um Benutzern anzuzeigen, dass Sprachbefehle vom System über eine vorübergehende Farbe changehört wurden.</span><span class="sxs-lookup"><span data-stu-id="1e646-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="1e646-192">Die folgenden Cursor Zustände können auf unterschiedliche Weise implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="1e646-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="1e646-193">Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustands Automat modellieren.</span><span class="sxs-lookup"><span data-stu-id="1e646-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="1e646-194">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1e646-194">For example:</span></span>
    * <span data-ttu-id="1e646-195">Im Leerlaufzustand wird der Standard Cursor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1e646-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="1e646-196">Der Status "bereit" ist, wenn Sie festgestellt haben, dass die Benutzer die Hand in der Bereitschaft haben.</span><span class="sxs-lookup"><span data-stu-id="1e646-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="1e646-197">Der Interaktions Zustand ist, wenn der Benutzer eine bestimmte Interaktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="1e646-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="1e646-198">Der Status "mögliche Aktionen" oder "Hover" ist, wenn Sie mögliche Aktionen übermitteln, die für ein Hologram ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="1e646-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="1e646-199">Sie können diese Zustände auch auf die gleiche Weise implementieren, sodass Sie unterschiedliche Kunstobjekte anzeigen können, wenn verschiedene Zustände erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="1e646-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="1e646-200">"Cursor frei"</span><span class="sxs-lookup"><span data-stu-id="1e646-200">Going "cursor-free"</span></span>
<span data-ttu-id="1e646-201">Das Entwerfen ohne Cursor wird empfohlen, wenn das Eintauchen eine wichtige Komponente einer-Funktion ist und wenn für das zeigen von Interaktionen (durchschauen und Gesten) keine hohe Genauigkeit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="1e646-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="1e646-202">Das System muss immer noch die Anforderungen erfüllen, die normalerweise von einem Cursor erfüllt werden, indem Benutzern Kontinuierliches Feedback zum Verständnis des Systems bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1e646-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="1e646-203">Dies kann durch andere spürbare Zustandsänderungen erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="1e646-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1e646-204">Cursor im mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="1e646-204">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="1e646-205">Standardmäßig stellt [mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) eine Cursor-vorfab ([DefaultCursor. Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) bereit, die denselben visuellen Zustand aufweist wie der System Cursor der Shell.</span><span class="sxs-lookup"><span data-stu-id="1e646-205">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="1e646-206">Er wird im Eingabeprofil des MRTK unter „Pointers“ (Zeiger) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="1e646-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="1e646-207">Sie können diesen Cursor für Ihre Benutzeroberflächen ersetzen/anpassen.</span><span class="sxs-lookup"><span data-stu-id="1e646-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="1e646-208">Für die Verwendung von Eye-Tracking-Eingaben bietet mrtk auch den "eyegazecursor", der über eine feine Visualisierung verfügt, um die Ablenkung zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="1e646-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="1e646-209">MRTK – Zeigerprofil</span><span class="sxs-lookup"><span data-stu-id="1e646-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="1e646-210">MRTK – Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="1e646-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="1e646-211">MRTK – Zeiger</span><span class="sxs-lookup"><span data-stu-id="1e646-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="1e646-212">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="1e646-212">See also</span></span>
* [<span data-ttu-id="1e646-213">Gesten</span><span class="sxs-lookup"><span data-stu-id="1e646-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="1e646-214">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="1e646-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
