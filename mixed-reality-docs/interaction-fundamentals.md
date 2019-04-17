---
title: Grundlagen der Interaktion
description: Wie wir Umgebungen für HoloLens erstellt haben (der 1. Generation), HoloLens 2 und immersive Headsets, haben wir begonnen, Schreiben Sie einige Dinge freigeben nützlich herausgestellt.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität Interaktion, Entwerfen
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593245"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="01054-104">Grundlagen der Interaktion</span><span class="sxs-lookup"><span data-stu-id="01054-104">Interaction fundamentals</span></span>

<span data-ttu-id="01054-105">Wie wir Umgebungen für HoloLens und immersive Headsets erstellt haben, haben wir begonnen, Schreiben Sie einige Dinge, die es nützlich, um die Freigabe gefunden.</span><span class="sxs-lookup"><span data-stu-id="01054-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="01054-106">Stellen Sie sich diese als die grundlegenden Bausteine für den Entwurf für die Interaktion von mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="01054-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="01054-107">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="01054-107">Device support</span></span>

<span data-ttu-id="01054-108">Hier ist eine Gliederung verfügbaren Interaktion Entwurf Artikeln und der Typ des Geräts oder Typen zu gelten.</span><span class="sxs-lookup"><span data-stu-id="01054-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="01054-109"><strong>Eingabe</strong></span><span class="sxs-lookup"><span data-stu-id="01054-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="01054-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="01054-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="01054-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="01054-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="01054-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="01054-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="01054-113"><a href="gestures.md">Umrissene Händen</a></span><span class="sxs-lookup"><span data-stu-id="01054-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="01054-114">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="01054-115"><a href="gaze-targeting.md">Auge als Ziel</a></span><span class="sxs-lookup"><span data-stu-id="01054-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="01054-116">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="01054-117"><a href="gaze-targeting.md">Blicke für</a></span><span class="sxs-lookup"><span data-stu-id="01054-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="01054-118">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-119">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-120">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="01054-121"><a href="gestures.md">Gesten</a></span><span class="sxs-lookup"><span data-stu-id="01054-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="01054-122">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-123">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="01054-124"><a href="voice-design.md">Voice-Entwurf</a></span><span class="sxs-lookup"><span data-stu-id="01054-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="01054-125">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-126">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-127">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="01054-128">Gamepad</span><span class="sxs-lookup"><span data-stu-id="01054-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-129">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-130">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-131">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="01054-132"><a href="motion-controllers.md">Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="01054-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="01054-133">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="01054-134"><strong>Vorstellung und räumliche Funktionen</strong></span><span class="sxs-lookup"><span data-stu-id="01054-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="01054-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="01054-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="01054-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="01054-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="01054-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="01054-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="01054-138"><a href="spatial-sound-design.md">Räumliche Entwurf</a></span><span class="sxs-lookup"><span data-stu-id="01054-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="01054-139">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-140">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-141">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="01054-142"><a href="spatial-mapping-design.md">Räumliche Zuordnung entwerfen</a></span><span class="sxs-lookup"><span data-stu-id="01054-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="01054-143">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-144">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="01054-145"><a href="hologram.md">Holograms</a></span><span class="sxs-lookup"><span data-stu-id="01054-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="01054-146">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="01054-147">✔️</span><span class="sxs-lookup"><span data-stu-id="01054-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="01054-148">Der Benutzer ist der Kamera</span><span class="sxs-lookup"><span data-stu-id="01054-148">The user is the camera</span></span>

![Benutzer wird die Kamera](images/useriscamera-640px.jpg)

<span data-ttu-id="01054-150">Denken Sie immer zum Entwurf für die Sicht des Benutzers, wie sie über die reellen und virtuelle Welten verschieben.</span><span class="sxs-lookup"><span data-stu-id="01054-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="01054-151">**Einige Fragen**</span><span class="sxs-lookup"><span data-stu-id="01054-151">**Some questions to ask**</span></span>
* <span data-ttu-id="01054-152">Wird der Benutzer befindet, reclining, ständigen oder Schritt für Schritt bei der Verwendung von Ihren Erfahrungen?</span><span class="sxs-lookup"><span data-stu-id="01054-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="01054-153">Wie anpassen Ihre Inhalte an andere Positionen?</span><span class="sxs-lookup"><span data-stu-id="01054-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="01054-154">Kann der Benutzer es werden angepasst?</span><span class="sxs-lookup"><span data-stu-id="01054-154">Can the user adjust it?</span></span>
* <span data-ttu-id="01054-155">Wird der Benutzer Ihre app mit der Anwendung vertraut sein?</span><span class="sxs-lookup"><span data-stu-id="01054-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="01054-156">**Empfohlene Methoden**</span><span class="sxs-lookup"><span data-stu-id="01054-156">**Best practices**</span></span>
* <span data-ttu-id="01054-157">Der Benutzer die Kamera und steuern sie die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="01054-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="01054-158">Sie steuern können.</span><span class="sxs-lookup"><span data-stu-id="01054-158">Let them drive.</span></span>
* <span data-ttu-id="01054-159">Wenn Sie praktisch den Benutzer übertragen müssen, werden Sie Probleme vestibular angefasst.</span><span class="sxs-lookup"><span data-stu-id="01054-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="01054-160">Verwenden Sie kürzere Animationen</span><span class="sxs-lookup"><span data-stu-id="01054-160">Use shorter animations</span></span>
* <span data-ttu-id="01054-161">Animieren von nach unten/links/rechts, oder blenden Sie im, anstelle von Z</span><span class="sxs-lookup"><span data-stu-id="01054-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="01054-162">Verlangsamen der zeitlichen Steuerung</span><span class="sxs-lookup"><span data-stu-id="01054-162">Slow down timing</span></span>
* <span data-ttu-id="01054-163">Zulassen, dass Benutzer die Welt im Hintergrund finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="01054-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="01054-164">**Was Sie vermeiden sollten**</span><span class="sxs-lookup"><span data-stu-id="01054-164">**What to avoid**</span></span>
* <span data-ttu-id="01054-165">Bewegen die Kamera oder Sperren Sie es absichtlich 3DOF nicht (nur Ausrichtung, keine Übersetzung), unbequem können Benutzer vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="01054-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="01054-166">Keine abrupte Verschiebung.</span><span class="sxs-lookup"><span data-stu-id="01054-166">No abrupt movement.</span></span> <span data-ttu-id="01054-167">Wenn Sie Inhalte zum oder vom Benutzer bringen möchten, verschieben Sie sie langsam und reibungslos in diese Richtung für optimalen Komfort.</span><span class="sxs-lookup"><span data-stu-id="01054-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="01054-168">Benutzer werden auf großen Menüs, die Ihnen bald zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="01054-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="01054-169">Nicht beschleunigen oder des Benutzers Kamera zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="01054-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="01054-170">Benutzer sind anfällig für Beschleunigung (angular und translatorische).</span><span class="sxs-lookup"><span data-stu-id="01054-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="01054-171">Nutzen Sie die Sicht des Benutzers</span><span class="sxs-lookup"><span data-stu-id="01054-171">Leverage the user's perspective</span></span>

<span data-ttu-id="01054-172">Benutzer sehen die Welt von mixed Reality über zeigt auf immersive und holographic-Geräten.</span><span class="sxs-lookup"><span data-stu-id="01054-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="01054-173">Klicken Sie auf die HoloLens, diese Anzeige heißt die [holographic Frame](holographic-frame.md).</span><span class="sxs-lookup"><span data-stu-id="01054-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="01054-174">Entwicklung von 2D können häufig verwendete Inhalte und Einstellungen in den Ecken des Bildschirms, um sie leicht zugänglich zu machen platziert werden.</span><span class="sxs-lookup"><span data-stu-id="01054-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="01054-175">In holographic apps kann Inhalt in die Ecken aus Sicht der Benutzer jedoch unbequem für den Zugriff auf sein.</span><span class="sxs-lookup"><span data-stu-id="01054-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="01054-176">In diesem Fall ist die Mitte des Frames, holographic die wichtigste Quelle für Inhalte.</span><span class="sxs-lookup"><span data-stu-id="01054-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="01054-177">Der Benutzer müssen möglicherweise geführt werden, um das Auffinden von wichtigen Ereignissen oder Objekte außerhalb ihrer unmittelbaren anzeigen.</span><span class="sxs-lookup"><span data-stu-id="01054-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="01054-178">Sie können die Pfeile, light-Trails, Zeichen Bewegungen, Sprechblasen, Zeiger, räumliche Sound und Sprachansagen um zu unterstützen, den Benutzer auf wichtige Inhalte in Ihrer app verwenden.</span><span class="sxs-lookup"><span data-stu-id="01054-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="01054-179">Es wird keine Sperre Inhalt auf dem Bildschirm des Benutzers aus Annehmlichkeitsgründen empfohlen.</span><span class="sxs-lookup"><span data-stu-id="01054-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="01054-180">Wenn Sie in einer Ansicht Inhalt beibehalten möchten, fügen Sie ihn in der ganzen Welt, und machen Sie den Inhalt "Tag-along", z. B. das Startmenü.</span><span class="sxs-lookup"><span data-stu-id="01054-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="01054-181">Inhalte, die zusammen mit der Sicht des Benutzers basisteilkonfiguration werden in der Umgebung natürlichere fühlen.</span><span class="sxs-lookup"><span data-stu-id="01054-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="01054-182">![Die Ansicht des Benutzers im Startmenü befolgt werden, wenn der Rand des Frames erreicht](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="01054-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="01054-183">*Die Ansicht des Benutzers im Startmenü befolgt werden, wenn der Rand des Frames erreicht*</span><span class="sxs-lookup"><span data-stu-id="01054-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="01054-184">Für HoloLens können Hologramme real, wenn sie innerhalb des Rahmens holographic passen, da sie abgeschnitten abrufen nicht.</span><span class="sxs-lookup"><span data-stu-id="01054-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="01054-185">Benutzer werden verschoben, um zu sehen, das die Begrenzungen des ggf. ein Hologramm innerhalb des Rahmens.</span><span class="sxs-lookup"><span data-stu-id="01054-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="01054-186">Für HoloLens ist es wichtig, die Benutzeroberfläche in die Ansicht des Benutzers passen, und behalten Sie den Fokus auf die Hauptaktion vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="01054-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="01054-187">Für immersive Headsets ist es wichtig, den Eindruck einer persistenten virtuellen Welt innerhalb des Geräts Sichtfeld zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="01054-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="01054-188">Benutzerkomfort</span><span class="sxs-lookup"><span data-stu-id="01054-188">User comfort</span></span>

<span data-ttu-id="01054-189">Um sicherzustellen, dass maximal [bequem](comfort.md) auf Head-eingebunden angezeigt, und es ist wichtig für Designer und Entwickler zum Erstellen und zeigen den Inhalt in einer Weise, die imitiert, wie Menschen 3D-Formen und die relative Position von Objekten in der natürlichen interpretieren World.</span><span class="sxs-lookup"><span data-stu-id="01054-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="01054-190">Hinsichtlich der physischen ist es auch wichtig, Inhalte zu entwickeln, die keine fatiguing Bewegungen des trichterhalses oder Arms erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="01054-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="01054-191">Ob für HoloLens oder immersive Headsets entwickeln zu können, ist es wichtig, um Darstellung für beide Augen zu rendern.</span><span class="sxs-lookup"><span data-stu-id="01054-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="01054-192">Ein Heads-Up-Display in ein Auge rendern kann nur eine Schnittstelle schwer zu verstehen sind, sowie Uneasiness des Benutzers Augen und Brain-Problem verursacht, vornehmen.</span><span class="sxs-lookup"><span data-stu-id="01054-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="01054-193">Teilen Sie Ihre Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="01054-193">Share your experience</span></span>

<span data-ttu-id="01054-194">Mithilfe von [mixed Reality-Erfassung](mixed-reality-capture.md), Benutzer können eines Fotos oder Videos des Benutzererlebnisses zu einem beliebigen Zeitpunkt erfassen.</span><span class="sxs-lookup"><span data-stu-id="01054-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="01054-195">Erwägen Sie die Umgebungen in Ihrer app, in dem Sie Momentaufnahmen oder Videos empfehlen möchten.</span><span class="sxs-lookup"><span data-stu-id="01054-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="01054-196">Nutzen Sie die Windows Mixed Reality home basic UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="01054-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="01054-197">Genau wie die Windows-PC-Umgebung mit dem Desktop gestartet wird, startet Windows Mixed Reality, mit der Startseite.</span><span class="sxs-lookup"><span data-stu-id="01054-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="01054-198">Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) nutzt unsere ausgeprägten besser zu verstehen, und navigieren 3D stellen.</span><span class="sxs-lookup"><span data-stu-id="01054-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="01054-199">Mit HoloLens ist Ihre Startseite Ihrer physischen Raum.</span><span class="sxs-lookup"><span data-stu-id="01054-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="01054-200">Mit immersive Headsets ist Ihre Startseite einen virtuellen Ort.</span><span class="sxs-lookup"><span data-stu-id="01054-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="01054-201">Ihre Startseite ist auch, in dem Sie verwenden des Startmenüs zu öffnen, und platzieren Sie apps und Inhalt.</span><span class="sxs-lookup"><span data-stu-id="01054-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="01054-202">Können Sie Ihre Startseite mit mixed Reality-Inhalt füllen und Multitasking mit mehreren apps zur gleichen Zeit.</span><span class="sxs-lookup"><span data-stu-id="01054-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="01054-203">Die Dinge, die Sie in Ihrem Haus platzieren bleiben, selbst wenn Sie Ihr Gerät neu starten.</span><span class="sxs-lookup"><span data-stu-id="01054-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="01054-204">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="01054-204">See also</span></span>
* [<span data-ttu-id="01054-205">Blicke für</span><span class="sxs-lookup"><span data-stu-id="01054-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="01054-206">Gesten</span><span class="sxs-lookup"><span data-stu-id="01054-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="01054-207">Voice-Entwurf</span><span class="sxs-lookup"><span data-stu-id="01054-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="01054-208">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="01054-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="01054-209">Räumliche Entwurf</span><span class="sxs-lookup"><span data-stu-id="01054-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="01054-210">Räumliche Zuordnung entwerfen</span><span class="sxs-lookup"><span data-stu-id="01054-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="01054-211">Comfort</span><span class="sxs-lookup"><span data-stu-id="01054-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="01054-212">Navigieren Sie in der Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="01054-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
