---
title: Spracheingabe
description: Die Spracheingabe ist eine Kern Eingabe für hololens und Windows Mixed Reality-immersive Headsets. Voice kann für Befehle, Diktat, Cortana usw. verwendet werden.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, Input
ms.openlocfilehash: 78ff63f2f794bb2b3a4868e38ccaff0582ccca8c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345700"
---
# <a name="voice-input"></a><span data-ttu-id="2a2aa-105">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a2aa-105">Voice input</span></span>

![Spracheingabe](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="2a2aa-107">Die Stimme ist eine der wichtigsten Formen der Eingabe für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="2a2aa-108">Damit können Sie ein – Hologramm direkt aufrufen, ohne [Handgesten](gaze-and-commit.md#composite-gestures)verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="2a2aa-109">Die Spracheingabe kann eine natürliche Art sein, Ihre Absichten zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="2a2aa-110">Voice eignet sich besonders gut für die Durchführung komplexer Schnittstellen, da Benutzer mit einem Befehl die Möglichkeit haben, die Verwendung von Netz Menüs zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="2a2aa-111">Die Spracheingabe wird von [derselben Engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) unterstützt, die Sprache in allen anderen _universellen Windows-apps_unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="2a2aa-112">Bei hololens funktioniert die Spracherkennung immer in der in den Einstellungen konfigurierten Windows-Anzeige Sprache.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="2a2aa-113">Sprach-und Blick</span><span class="sxs-lookup"><span data-stu-id="2a2aa-113">Voice and gaze</span></span>

<span data-ttu-id="2a2aa-114">Wenn Sprachbefehle verwendet werden, wird der Cursor (Head-oder Eye) in der Regel als Ziel Ziel Mechanismus verwendet, egal ob mit einem Cursor ("Select") oder implizit, um Ihren Befehl an eine Anwendung zu leiten, die Sie sich ansehen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="2a2aa-115">Hierfür ist es möglicherweise gar nicht erforderlich, einen Cursor Cursor anzuzeigen _("Weitere_Informationen" anzeigen).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="2a2aa-116">Natürlich benötigen einige Sprachbefehle überhaupt kein Ziel, z. b. "Gehe zu Start" oder "Hey Cortana".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="2a2aa-117">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="2a2aa-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2a2aa-118"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="2a2aa-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2a2aa-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a2aa-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2a2aa-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2a2aa-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2a2aa-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a2aa-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2a2aa-122">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a2aa-122">Voice input</span></span></td>
        <td><span data-ttu-id="2a2aa-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2a2aa-123">✔️</span></span></td>
        <td><span data-ttu-id="2a2aa-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2a2aa-124">✔️</span></span></td>
        <td><span data-ttu-id="2a2aa-125">✔️ (mit Mikrofon)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="2a2aa-126">Der Befehl "Select"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-126">The "select" command</span></span>

<span data-ttu-id="2a2aa-127">**HoloLens (1. Generation)**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="2a2aa-128">Auch wenn Sie Ihrer APP keine Sprachunterstützung hinzufügen, können Ihre Benutzer holograms aktivieren, indem Sie einfach den System Sprachbefehl "Select" sagen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="2a2aa-129">Dies verhält sich wie eine [Luft](gaze-and-commit.md#composite-gestures) Abzweigung in hololens, das Drücken der Schaltfläche "auswählen" auf dem [hololens-Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)oder das Drücken des Auslösers auf einem [Windows Mixed Reality Motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="2a2aa-130">Sie werden einen Sound hören und sehen, dass eine QuickInfo mit "Select" als Bestätigung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="2a2aa-131">"Select" wird durch einen Algorithmus für die Erkennung eines niedrigen Leistungs Worts aktiviert, sodass Sie jederzeit mit minimalen Auswirkungen auf die Akku Lebensdauer jederzeit angezeigt werden können. Dies gilt auch für Ihre Hände.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="2a2aa-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="2a2aa-133">Um den "Select"-Befehl "Stimme" in hololens 2 zu verwenden, müssen Sie zuerst den Cursor Cursor zur Verwendung als Zeiger einrichten.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="2a2aa-134">Der Befehl zur Eingabe ist leicht zu merken, einfach "Select".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="2a2aa-135">Um den Modus zu beenden, verwenden Sie einfach wieder die Hände, entweder durch Tippen auf eine Maustaste, eine Schaltfläche mit Ihren Fingern oder mithilfe der System Bewegung.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="2a2aa-136">*Bild: "Select", um den Voice-Befehl für die Auswahl zu verwenden*</span><span class="sxs-lookup"><span data-stu-id="2a2aa-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Ein Benutzer kann "Select" (auswählen) verwenden, um den Voice-Befehl für eine Auswahl zu verwenden.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="2a2aa-138">Hallo, Cortana</span><span class="sxs-lookup"><span data-stu-id="2a2aa-138">Hey Cortana</span></span>

<span data-ttu-id="2a2aa-139">Sie können auch "Hey Cortana" sagen, um Cortana jederzeit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="2a2aa-140">Sie müssen nicht warten, bis Sie angezeigt wird, um Ihre Frage zu stellen oder eine Anweisung zu geben, z. b. "Hey Cortana, was ist das Wetter?".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="2a2aa-141">als einzelner Satz.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-141">as a single sentence.</span></span> <span data-ttu-id="2a2aa-142">Weitere Informationen zu Cortana und den Möglichkeiten, die Sie tun können, finden Sie einfach!</span><span class="sxs-lookup"><span data-stu-id="2a2aa-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="2a2aa-143">Sagen Sie: "Hey Cortana, was kann ich sagen?"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="2a2aa-144">und Sie werden eine Liste der funktionierenden und vorgeschlagenen Befehle abrufen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="2a2aa-145">Wenn Sie sich bereits in der Cortana-App befinden, können Sie auch auf die **?**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="2a2aa-146">Symbol auf der Rand Leiste, um das gleiche Menü zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="2a2aa-147">**Hololens-spezifische Befehle**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="2a2aa-148">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="2a2aa-148">"What can I say?"</span></span>
* <span data-ttu-id="2a2aa-149">"Gehe zu Start"-anstelle von " [Bloom](system-gesture.md#bloom) ", um zum [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu gelangen</span><span class="sxs-lookup"><span data-stu-id="2a2aa-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="2a2aa-150">"Starten <app> "</span><span class="sxs-lookup"><span data-stu-id="2a2aa-150">"Launch <app>"</span></span>
* <span data-ttu-id="2a2aa-151">" <app> Hier verschieben"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-151">"Move <app> here"</span></span>
* <span data-ttu-id="2a2aa-152">"Bild nehmen"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-152">"Take a picture"</span></span>
* <span data-ttu-id="2a2aa-153">"Aufzeichnung starten"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-153">"Start recording"</span></span>
* <span data-ttu-id="2a2aa-154">"Aufzeichnung anhalten"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-154">"Stop recording"</span></span>
* <span data-ttu-id="2a2aa-155">"Erhöhen der Helligkeit"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-155">"Increase the brightness"</span></span>
* <span data-ttu-id="2a2aa-156">"Die Helligkeit verringern"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="2a2aa-157">"Volume vergrößern"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-157">"Increase the volume"</span></span>
* <span data-ttu-id="2a2aa-158">"Volume verkleinern"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-158">"Decrease the volume"</span></span>
* <span data-ttu-id="2a2aa-159">"Stumm schalten" oder "unstumm schalten"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="2a2aa-160">"Gerät Herunterfahren"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-160">"Shut down the device"</span></span>
* <span data-ttu-id="2a2aa-161">"Gerät neu starten"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-161">"Restart the device"</span></span>
* <span data-ttu-id="2a2aa-162">"Gehe zu Standbymodus"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-162">"Go to sleep"</span></span>
* <span data-ttu-id="2a2aa-163">"Welche Zeit ist es?"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-163">"What time is it?"</span></span>
* <span data-ttu-id="2a2aa-164">"Wie viel Akku habe ich verbleiben?"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="2a2aa-165">"Weitere Informationen"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="2a2aa-166">Hololens hat eine "See it"-Modell für die Spracheingabe, bei der Bezeichnungen auf Schaltflächen den Benutzern mitteilen, welche Sprachbefehle Sie auch sagen können.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="2a2aa-167">Wenn Sie z. b. ein App-Fenster in hololens (1st Gen) betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="2a2aa-168">*Image: ein Benutzer kann den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP anzupassen.*</span><span class="sxs-lookup"><span data-stu-id="2a2aa-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="2a2aa-169">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="2a2aa-170">![Wenn Sie ein App-Fenster oder Hologram betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="2a2aa-171">Wenn apps diese Regel befolgen, können Benutzer leicht erkennen, was zum Steuern des Systems zu sagen ist.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="2a2aa-172">Um dies zu verstärken, wird bei der Betrachtung einer Schaltfläche in hololens (1st Gen) eine QuickInfo angezeigt, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprach fähig ist, und zeigt den Befehl an, um zu sprechen, um Sie zu "drücken".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="2a2aa-173">Um voicemailtipps in hololens 2 anzuzeigen, zeigen Sie den sprach Cursor an, indem Sie "Select" oder "Was kann ich sagen" (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="2a2aa-174">*Bild: "sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.*</span><span class="sxs-lookup"><span data-stu-id="2a2aa-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="2a2aa-176">Sprachbefehle für schnelle – Hologramm-Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="2a2aa-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="2a2aa-177">Es gibt eine Reihe von Sprachbefehlen, die Sie bei der Betrachtung eines holograms zum schnellen Ausführen von Bearbeitungsaufgaben sagen können.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="2a2aa-178">Diese Sprachbefehle funktionieren sowohl bei App-Fenstern als auch bei 3D-Objekten, die Sie in der Welt abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="2a2aa-179">**Hologram-Bearbeitungsbefehle**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="2a2aa-180">Gesicht</span><span class="sxs-lookup"><span data-stu-id="2a2aa-180">Face me</span></span>
* <span data-ttu-id="2a2aa-181">Größer | Verbessern</span><span class="sxs-lookup"><span data-stu-id="2a2aa-181">Bigger | Enhance</span></span>
* <span data-ttu-id="2a2aa-182">Geringeren</span><span class="sxs-lookup"><span data-stu-id="2a2aa-182">Smaller</span></span>

<span data-ttu-id="2a2aa-183">Auf hololens 2 können Sie auch natürlichere Interaktionen in Kombination mit Eye-Blick erstellen, die implizit Kontextinformationen über das, auf das Sie verweisen, bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="2a2aa-184">Sie könnten z. b. einfach ein Hologramm betrachten und dann auf "put _this_" ("put this") und _dann überprüfen_, wo Sie es platzieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="2a2aa-185">Oder Sie können sich einen Holographic-Teil auf einem komplexen Computer ansehen und sagen: "Weitere Informationen zu _diesem_".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="2a2aa-186">Erkennen von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="2a2aa-186">Discovering voice commands</span></span>

<span data-ttu-id="2a2aa-187">Einige Befehle, wie z. b. die Befehle für die schnelle Bearbeitung, können ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="2a2aa-188">Um zu erfahren, welche Befehle Sie verwenden können, schauen Sie sich das Objekt an, und sagen Sie: "Was kann ich sagen?".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="2a2aa-189">Eine Liste möglicher Befehle wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-189">A list of possible commands pops up.</span></span> <span data-ttu-id="2a2aa-190">Sie können auch den Cursor Cursor verwenden, um die voicemailtipps für die einzelnen Schaltflächen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="2a2aa-191">Wenn Sie eine vollständige Liste erhalten möchten, sagen Sie einfach "alle Befehle anzeigen".</span><span class="sxs-lookup"><span data-stu-id="2a2aa-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="2a2aa-192">Diktieren</span><span class="sxs-lookup"><span data-stu-id="2a2aa-192">Dictation</span></span>

<span data-ttu-id="2a2aa-193">Anstatt eine Typisierung mit [Luft](gaze-and-commit.md#composite-gestures)Eingaben durchführen zu können, kann es effizienter sein, Text in eine APP einzugeben.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="2a2aa-194">Dadurch kann die Eingabe erheblich beschleunigt werden, sodass der Benutzer weniger Aufwand hat.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="2a2aa-195">![Sprach Diktat beginnt mit der Schaltfläche Mikrofon](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="2a2aa-196">*Sprach Diktat beginnt mit der Schaltfläche Mikrofon auf der Tastatur*</span><span class="sxs-lookup"><span data-stu-id="2a2aa-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="2a2aa-197">Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktat Modus wechseln, anstatt einzugeben.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="2a2aa-198">Wählen Sie das Mikrofon auf der Seite des Texteingabe Felds aus, um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="2a2aa-199">Hinzufügen von Sprachbefehlen zu Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="2a2aa-199">Adding voice commands to your app</span></span>

<span data-ttu-id="2a2aa-200">Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="2a2aa-201">Die Spracheingabe ist eine leistungsstarke und komfortable Möglichkeit zur Steuerung von System und Apps.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="2a2aa-202">Da Benutzer mit einer Vielzahl von Dialekten und Akzenten sprechen, stellt die richtige Auswahl der Schlüsselwörter für die Spracherkennung sicher, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="2a2aa-203">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="2a2aa-203">Best practices</span></span>

<span data-ttu-id="2a2aa-204">Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="2a2aa-205">**Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="2a2aa-206">Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="2a2aa-207">Beispiel: "Video abspielen" ist besser als "das aktuell ausgewählte Video abspielen"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="2a2aa-208">**Verwenden eines einfachen Vokabulars** -Beispiel: "Show Note" ist besser als "Placard anzeigen"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="2a2aa-209">**Sicherstellen, dass Befehle nicht destruktiv sind**: Stellen Sie sicher, dass alle Aktionen, die von einem Spracherkennungsbefehl ausgeführt werden können, nicht destruktiv sind und leicht rückgängig gemacht werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="2a2aa-210">**Ähnlich klingende Befehle vermeiden**: Vermeiden Sie es, mehrere Spracherkennungsbefehle zu registrieren, die sehr ähnlich klingen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="2a2aa-211">Beispiel: "mehr anzeigen" und "Store anzeigen" kann sehr ähnlich klingen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="2a2aa-212">**Registrierung der App aufheben, wenn sie nicht verwendet wird**: Wenn sich Ihre Anwendung nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung der App aufheben, damit andere Befehle nicht mit diesem verwechselt werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="2a2aa-213">**Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="2a2aa-214">**Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="2a2aa-215">**Verwendung von Systembefehlen vermeiden**: Die folgenden Sprachbefehle sind für das System reserviert.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="2a2aa-216">Diese sollten nicht von Anwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="2a2aa-217">„Hey Cortana“</span><span class="sxs-lookup"><span data-stu-id="2a2aa-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="2a2aa-218">„Auswählen“</span><span class="sxs-lookup"><span data-stu-id="2a2aa-218">"Select"</span></span>
   * <span data-ttu-id="2a2aa-219">"Gehe zu Start"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="2a2aa-220">Vorteile von Spracheingaben</span><span class="sxs-lookup"><span data-stu-id="2a2aa-220">Advantages of voice input</span></span>

<span data-ttu-id="2a2aa-221">Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="2a2aa-222">Voice ist besonders gut für Schnittstellen **Traversale** geeignet, da Sie Benutzern dabei helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen (ein Benutzer könnte bei der Betrachtung einer Webseite auf die Schaltfläche "zurück" klicken, anstatt auf die Schaltfläche "zurück" in der APP zu gelangen).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="2a2aa-223">Diese kleine Zeitersparnis wirkt sich **negativ** auf die Wahrnehmung der Benutzerfreundlichkeit durch den Benutzer aus und bietet Ihnen einen kleinen Wert für die Super Arbeit.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="2a2aa-224">Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="2a2aa-225">Auf Geräten, auf denen die Eingabe auf einer Tastatur schwierig ist, kann die **sprach Diktat** -Methode eine effiziente Alternative zum Eingeben von Text sein.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="2a2aa-226">In einigen Fällen, in denen der **Genauigkeits Bereich** für den Blick und die Bewegung eingeschränkt ist, kann Voice Ihnen helfen, die Absicht des Benutzers zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="2a2aa-227">**Vorteile der Spracheingabe für den Benutzer**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="2a2aa-228">Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="2a2aa-229">Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="2a2aa-230">Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="2a2aa-231">Sie ist sozialverträglich – sie sollte sich in Bezug auf das Verhalten in die gesellschaftlichen Normen einfügen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="2a2aa-232">Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="2a2aa-233">Herausforderungen bei der Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a2aa-233">Challenges for voice input</span></span>

<span data-ttu-id="2a2aa-234">Obwohl die Spracheingabe für viele verschiedene Anwendungen hervorragend ist, stellt Sie auch mehrere Herausforderungen dar.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="2a2aa-235">Wenn Sie sowohl die Vorteile als auch die Herausforderungen von Spracheingaben verstanden haben, können App-Entwickler intelligentere Entscheidungen treffen, wie und wann Spracheingaben verwendet werden sollen und wie Sie Ihre Benutzer gut gestalten können.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="2a2aa-236">**Spracheingabe für kontinuierliches Eingabe Steuer** Element Eine differenzierte Steuerung ist eine davon.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="2a2aa-237">Beispielsweise kann ein Benutzer sein Volume in der Musik-App ändern.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="2a2aa-238">Sie kann einfach "lauter" sagen, aber es ist nicht klar, wie viel lauter das System das Volume machen soll.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="2a2aa-239">Der Benutzer könnte sagen: "machen Sie es etwas lauter", aber "ein wenig" ist schwierig zu quantifizieren.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="2a2aa-240">Das Verschieben oder Skalieren von holograms mit Stimme ist ähnlich schwierig.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="2a2aa-241">**Zuverlässigkeit der Spracheingabe Erkennung** Obwohl Spracheingabe Systeme besser und besser werden, werden Sie möglicherweise fälschlicherweise einen Sprachbefehl hören und interpretieren.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="2a2aa-242">Der Schlüssel besteht darin, dieser Herausforderung in Ihrer Anwendung zu begegnen, indem er dem Benutzer Feedback zur Verfügung stellt, wenn das System lauscht, und was das System verstanden hat, um Klarheit über potenzielle Probleme bei der ordnungsgemäßen Verwendung des Benutzers zu schaffen</span><span class="sxs-lookup"><span data-stu-id="2a2aa-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="2a2aa-243">**Spracheingabe in freigegebenen Leerzeichen** Die Stimme ist möglicherweise nicht in den Bereichen, die Sie für andere Personen freigeben, akzeptabel.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="2a2aa-244">Hier sind einige Beispiele:</span><span class="sxs-lookup"><span data-stu-id="2a2aa-244">Here are a few examples:</span></span>
* <span data-ttu-id="2a2aa-245">Der Benutzer möchte möglicherweise keine anderen Personen stören (z. b. in einer stillen Bibliothek oder einem freigegebenen Büro).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="2a2aa-246">Benutzer sind vielleicht nicht in der Öffentlichkeit,</span><span class="sxs-lookup"><span data-stu-id="2a2aa-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="2a2aa-247">Ein Benutzer ist möglicherweise unbequem, wenn er eine persönliche oder vertrauliche Nachricht (einschließlich Kenn Wörtern) einhört, während andere Benutzer lauschen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="2a2aa-248">**Spracheingabe von eindeutigen oder unbekannten Wörtern** Probleme bei der Spracheingabe werden auch angezeigt, wenn Benutzer Wörter, die möglicherweise dem System unbekannt sind, wie z. b. Spitznamen, bestimmte slang-Wörter oder Abkürzungen, eingeben.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="2a2aa-249">**Erlernen von Sprachbefehlen** Das ultimative Ziel ist es, sich auf natürliche Weise mit Ihrem System zu Konversation, häufig verlassen sich apps jedoch auf bestimmte vordefinierte Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="2a2aa-250">Eine Herausforderung, die mit einem großen Satz von Sprachbefehlen verknüpft ist, besteht darin, Sie zu unterstützen, ohne den Benutzer zu überlasten und den Benutzern zu helfen, Sie beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="2a2aa-251">Statusangaben für Spracherkennungsfeedback</span><span class="sxs-lookup"><span data-stu-id="2a2aa-251">Voice feedback states</span></span>

<span data-ttu-id="2a2aa-252">Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="2a2aa-253">Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="2a2aa-254">Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="2a2aa-255">![1. regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="2a2aa-256">**1. regulärer Cursor Zustand**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2a2aa-257">![2. kommuniziert Feedback und verschwindet dann](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="2a2aa-258">**2. kommuniziert Feedback und verschwindet dann**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2a2aa-259">![€.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-259">![\*3.</span></span> <span data-ttu-id="2a2aa-260">Regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a2aa-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="2a2aa-261">**3. zurück zum regulären Cursor Zustand**</span><span class="sxs-lookup"><span data-stu-id="2a2aa-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="2a2aa-262">Wichtige Informationen zur Spracherkennung in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2a2aa-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="2a2aa-263">Sagen Sie **„Auswählen“**, während Sie eine Schaltfläche anvisieren (Sie können dies überall verwenden, um auf eine Schaltfläche zu klicken).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="2a2aa-264">Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="2a2aa-265">Beim Betrachten einer App kann ein Benutzer z. B. den Befehl „Entfernen“ sagen, um die App aus der Umgebung zu entfernen (das spart Zeit, da die App nicht mit der Hand angeklickt werden muss).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="2a2aa-266">Sie können initiieren, dass Cortana zuhört, indem Sie **„Hey Cortana“** sagen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="2a2aa-267">Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="2a2aa-268">Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a2aa-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="2a2aa-269">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="2a2aa-269">What can I say?</span></span>
* <span data-ttu-id="2a2aa-270">Woher weiß ich, ob das System mich richtig verstanden hat?</span><span class="sxs-lookup"><span data-stu-id="2a2aa-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="2a2aa-271">Das System versteht meine Sprachbefehle immer wieder falsch.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="2a2aa-272">Es reagiert nicht, wenn ich einen Sprachbefehl erteile.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="2a2aa-273">Es reagiert falsch, wenn ich einen Sprachbefehl erteile.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="2a2aa-274">Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?</span><span class="sxs-lookup"><span data-stu-id="2a2aa-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="2a2aa-275">Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?</span><span class="sxs-lookup"><span data-stu-id="2a2aa-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="2a2aa-276">Kommunikation</span><span class="sxs-lookup"><span data-stu-id="2a2aa-276">Communication</span></span>

<span data-ttu-id="2a2aa-277">Für Anwendungen, die die von hololens bereitgestellten angepassten audioeingabeverarbeitungs-Optionen nutzen möchten, ist es wichtig, die verschiedenen [audiostreamkategorien](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) zu verstehen, die Ihre APP nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="2a2aa-278">Windows 10 unterstützt mehrere verschiedene streamingkategorien, und hololens nutzt drei dieser Möglichkeiten, um die benutzerdefinierte Verarbeitung zu ermöglichen, um die Qualität der Mikrofon Audioqualität zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist. diese kann für Umgebungs Umgebungs audioerfassungs Szenarien (d.h. "Camcorder") verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="2a2aa-279">Die AudioCategory_Communications Stream-Kategorie wird für Anruf Qualität und-Erzähl Szenarien angepasst und stellt dem Client einen 16-Bit-Mono-Mono-Audiostream der Stimme des Benutzers zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="2a2aa-280">Die AudioCategory_Speech Stream-Kategorie ist für die Sprach-Engine hololens (Windows) angepasst und bietet einen 16-Bit-Mono-Mono-Datenstrom der Stimme des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="2a2aa-281">Diese Kategorie kann bei Bedarf von Sprachmodulen von Drittanbietern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="2a2aa-282">Die AudioCategory_Other Stream-Kategorie ist für die Audioaufzeichnung der Umgebungsumgebung angepasst und stellt dem Client einen Stereo-Audiostream mit 48 kHz 24 Bit bereit.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="2a2aa-283">Die gesamte Audioverarbeitung ist Hardware beschleunigt. Dies bedeutet, dass die Features viel weniger Leistung als bei der Verarbeitung der hololens-CPU benötigen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="2a2aa-284">Vermeiden Sie die Ausführung einer anderen audioeingabeverarbeitung auf der CPU, um die Akku Lebensdauer zu maximieren und die integrierte, offloaded audioeingabeverarbeitung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="2a2aa-285">Sprachen</span><span class="sxs-lookup"><span data-stu-id="2a2aa-285">Languages</span></span>

<span data-ttu-id="2a2aa-286">Hololens 2 [unterstützt mehrere Sprachen](https://docs.microsoft.com/hololens/hololens2-language-support).</span><span class="sxs-lookup"><span data-stu-id="2a2aa-286">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="2a2aa-287">Beachten Sie, dass Sprachbefehle immer in der Anzeige Sprache des Systems ausgeführt werden, auch wenn mehrere Tastaturen installiert sind oder wenn apps versuchen, eine Spracherkennung in einer anderen Sprache zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2a2aa-288">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="2a2aa-288">Troubleshooting</span></span>

<span data-ttu-id="2a2aa-289">Wenn Sie Probleme bei der Verwendung von "Select" und "Hey Cortana" haben, versuchen Sie, zu einem ruhigeren Bereich zu wechseln, die Ursache für Rauschen zu machen oder lauter zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="2a2aa-290">Zu diesem Zeitpunkt wird die Spracherkennung in hololens speziell für systemeigene Sprecher von USA Englisch optimiert und optimiert.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="2a2aa-291">Für Windows Mixed Reality Developer Edition, Version 2017, funktioniert die audioendpunkt-Verwaltungs Logik problemlos (immer), nachdem Sie sich nach der anfänglichen HMD-Verbindung beim PC-Desktop abgemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="2a2aa-292">Vor dem ersten Abmelden/in-Ereignis nach dem Durchlaufen von WMR OOBE könnte der Benutzer verschiedene Probleme mit der Audiofunktionalität aufweisen, von denen kein audiowechsel bis hin zu keinem audiowechsel stattfindet, je nachdem, wie das System vor dem ersten Herstellen einer Verbindung mit dem HMD eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2a2aa-293">Spracheingabe in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="2a2aa-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="2a2aa-294">Mit **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie den Voice-Befehl problemlos für beliebige Objekte zuweisen.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="2a2aa-295">Verwenden Sie das **Spracheingabe Profil** von mrtk, um Ihre Schlüsselwörter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="2a2aa-296">Indem Sie das Skript " **speechinputhandler** " zuweisen, können Sie festlegen, dass jedes Objekt auf die im Spracheingabe Profil definierten Schlüsselwörter antwortet.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="2a2aa-297">Der speechinputhandler bietet auch eine Bezeichnung für die sprach Bestätigung, um das Vertrauen des Benutzers zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="2a2aa-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="2a2aa-298">Befehl "mrtk-Voice"</span><span class="sxs-lookup"><span data-stu-id="2a2aa-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="2a2aa-299">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2a2aa-299">See also</span></span>
* [<span data-ttu-id="2a2aa-300">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="2a2aa-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2a2aa-301">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="2a2aa-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2a2aa-302">MR-Eingabe 212: Sprache</span><span class="sxs-lookup"><span data-stu-id="2a2aa-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="2a2aa-303">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="2a2aa-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="2a2aa-304">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="2a2aa-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
