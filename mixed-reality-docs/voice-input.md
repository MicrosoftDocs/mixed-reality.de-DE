---
title: Spracheingabe
description: Die Spracheingabe ist eine Kern Eingabe für hololens und Windows Mixed Reality-immersive Headsets. Voice kann für Befehle, Diktat, Cortana usw. verwendet werden.
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, Input
ms.openlocfilehash: 1b0a57ad680b7f779201e99dea24bfe746820c44
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437142"
---
# <a name="voice-input"></a><span data-ttu-id="e636e-105">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e636e-105">Voice input</span></span>

<span data-ttu-id="e636e-106">Voice ist eine der wichtigsten Formen der Eingabe in hololens.</span><span class="sxs-lookup"><span data-stu-id="e636e-106">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="e636e-107">Damit können Sie ein – Hologramm direkt aufrufen, ohne [Handgesten](gaze-and-commit.md#composite-gestures)verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="e636e-107">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="e636e-108">Die Spracheingabe kann eine natürliche Möglichkeit sein, ihre Absicht zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="e636e-108">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="e636e-109">Voice eignet sich besonders gut für die Durchführung komplexer Schnittstellen, da Benutzer mit einem Befehl die Möglichkeit haben, die Verwendung von Netz Menüs zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e636e-109">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="e636e-110">Die Spracheingabe wird von [derselben Engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) unterstützt, die Sprache in allen anderen _universellen Windows-apps_unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e636e-110">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="e636e-111">Bei hololens funktioniert die Spracherkennung immer in der in den Einstellungen konfigurierten Windows-Anzeige Sprache.</span><span class="sxs-lookup"><span data-stu-id="e636e-111">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="e636e-112">Sprach-und Blick</span><span class="sxs-lookup"><span data-stu-id="e636e-112">Voice and gaze</span></span>

<span data-ttu-id="e636e-113">Wenn Sprachbefehle verwendet werden, wird der Cursor (Head-oder Eye) in der Regel als Ziel Ziel Mechanismus verwendet, egal ob mit einem Cursor ("Select") oder implizit, um Ihren Befehl an eine Anwendung zu leiten, die Sie sich ansehen.</span><span class="sxs-lookup"><span data-stu-id="e636e-113">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="e636e-114">Hierfür ist es möglicherweise gar nicht erforderlich, einen Cursor Cursor anzuzeigen _("Weitere_Informationen" anzeigen).</span><span class="sxs-lookup"><span data-stu-id="e636e-114">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="e636e-115">Natürlich benötigen einige Sprachbefehle überhaupt kein Ziel, z. b. "Gehe zu Start" oder "Hey Cortana".</span><span class="sxs-lookup"><span data-stu-id="e636e-115">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="e636e-116">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="e636e-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e636e-117"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="e636e-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e636e-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e636e-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e636e-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e636e-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e636e-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="e636e-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e636e-121">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e636e-121">Voice input</span></span></td>
        <td><span data-ttu-id="e636e-122">✔️</span><span class="sxs-lookup"><span data-stu-id="e636e-122">✔️</span></span></td>
        <td><span data-ttu-id="e636e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="e636e-123">✔️</span></span></td>
        <td><span data-ttu-id="e636e-124">✔️ (mit Mikrofon)</span><span class="sxs-lookup"><span data-stu-id="e636e-124">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="e636e-125">Der Befehl "Select"</span><span class="sxs-lookup"><span data-stu-id="e636e-125">The "select" command</span></span>

<span data-ttu-id="e636e-126">**HoloLens (1. Generation)**</span><span class="sxs-lookup"><span data-stu-id="e636e-126">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="e636e-127">Auch wenn Sie Ihrer APP keine Sprachunterstützung hinzufügen, können Ihre Benutzer holograms aktivieren, indem Sie einfach den System Sprachbefehl "Select" sagen.</span><span class="sxs-lookup"><span data-stu-id="e636e-127">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="e636e-128">Dies verhält sich wie eine [Luft](gaze-and-commit.md#composite-gestures) Abzweigung in hololens, das Drücken der Schaltfläche "auswählen" auf dem [hololens-Clicker](hardware-accessories.md#hololens-clicker)oder das Drücken des Auslösers auf einem [Windows Mixed Reality Motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="e636e-128">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="e636e-129">Sie werden einen Sound hören und sehen, dass eine QuickInfo mit "Select" als Bestätigung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e636e-129">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="e636e-130">"Select" wird durch einen Algorithmus für die Erkennung eines niedrigen Leistungs Worts aktiviert, sodass Sie jederzeit mit minimalen Auswirkungen auf die Akku Lebensdauer jederzeit angezeigt werden können. Dies gilt auch für Ihre Hände.</span><span class="sxs-lookup"><span data-stu-id="e636e-130">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="e636e-131">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="e636e-131">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="e636e-132">Um den "Select"-Befehl "Stimme" in hololens 2 zu verwenden, müssen Sie zuerst den Cursor Cursor zur Verwendung als Zeiger einrichten.</span><span class="sxs-lookup"><span data-stu-id="e636e-132">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="e636e-133">Der Befehl zur Eingabe ist leicht zu merken, einfach "Select".</span><span class="sxs-lookup"><span data-stu-id="e636e-133">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="e636e-134">Um den Modus zu beenden, verwenden Sie einfach wieder die Hände, entweder durch Tippen auf eine Maustaste, eine Schaltfläche mit Ihren Fingern oder mithilfe der System Bewegung.</span><span class="sxs-lookup"><span data-stu-id="e636e-134">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="e636e-135">*Bild: "Select", um den Voice-Befehl für die Auswahl zu verwenden*</span><span class="sxs-lookup"><span data-stu-id="e636e-135">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Ein Benutzer kann "Select" (auswählen) verwenden, um den Voice-Befehl für eine Auswahl zu verwenden.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="e636e-137">Hallo, Cortana</span><span class="sxs-lookup"><span data-stu-id="e636e-137">Hey Cortana</span></span>

<span data-ttu-id="e636e-138">Sie können auch "Hey Cortana" sagen, um Cortana jederzeit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e636e-138">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="e636e-139">Sie müssen nicht warten, bis Sie angezeigt wird, um Ihre Frage zu stellen oder eine Anweisung zu geben, z. b. "Hey Cortana, was ist das Wetter?".</span><span class="sxs-lookup"><span data-stu-id="e636e-139">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="e636e-140">als einzelner Satz.</span><span class="sxs-lookup"><span data-stu-id="e636e-140">as a single sentence.</span></span> <span data-ttu-id="e636e-141">Weitere Informationen zu Cortana und den Möglichkeiten, die Sie tun können, finden Sie einfach!</span><span class="sxs-lookup"><span data-stu-id="e636e-141">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="e636e-142">Sagen Sie: "Hey Cortana, was kann ich sagen?"</span><span class="sxs-lookup"><span data-stu-id="e636e-142">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="e636e-143">und Sie werden eine Liste der funktionierenden und vorgeschlagenen Befehle abrufen.</span><span class="sxs-lookup"><span data-stu-id="e636e-143">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="e636e-144">Wenn Sie sich bereits in der Cortana-App befinden, können Sie auch auf die **?**</span><span class="sxs-lookup"><span data-stu-id="e636e-144">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="e636e-145">Symbol auf der Rand Leiste, um das gleiche Menü zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="e636e-145">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="e636e-146">**Hololens-spezifische Befehle**</span><span class="sxs-lookup"><span data-stu-id="e636e-146">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="e636e-147">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="e636e-147">"What can I say?"</span></span>
* <span data-ttu-id="e636e-148">"Gehe zu Start"-anstelle von " [Bloom](system-gesture.md#bloom) ", um zum [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu gelangen</span><span class="sxs-lookup"><span data-stu-id="e636e-148">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="e636e-149">"Launch <app>"</span><span class="sxs-lookup"><span data-stu-id="e636e-149">"Launch <app>"</span></span>
* <span data-ttu-id="e636e-150">"<app> hier verschieben"</span><span class="sxs-lookup"><span data-stu-id="e636e-150">"Move <app> here"</span></span>
* <span data-ttu-id="e636e-151">"Bild nehmen"</span><span class="sxs-lookup"><span data-stu-id="e636e-151">"Take a picture"</span></span>
* <span data-ttu-id="e636e-152">"Aufzeichnung starten"</span><span class="sxs-lookup"><span data-stu-id="e636e-152">"Start recording"</span></span>
* <span data-ttu-id="e636e-153">"Aufzeichnung anhalten"</span><span class="sxs-lookup"><span data-stu-id="e636e-153">"Stop recording"</span></span>
* <span data-ttu-id="e636e-154">"Erhöhen der Helligkeit"</span><span class="sxs-lookup"><span data-stu-id="e636e-154">"Increase the brightness"</span></span>
* <span data-ttu-id="e636e-155">"Die Helligkeit verringern"</span><span class="sxs-lookup"><span data-stu-id="e636e-155">"Decrease the brightness"</span></span>
* <span data-ttu-id="e636e-156">"Volume vergrößern"</span><span class="sxs-lookup"><span data-stu-id="e636e-156">"Increase the volume"</span></span>
* <span data-ttu-id="e636e-157">"Volume verkleinern"</span><span class="sxs-lookup"><span data-stu-id="e636e-157">"Decrease the volume"</span></span>
* <span data-ttu-id="e636e-158">"Stumm schalten" oder "unstumm schalten"</span><span class="sxs-lookup"><span data-stu-id="e636e-158">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="e636e-159">"Gerät Herunterfahren"</span><span class="sxs-lookup"><span data-stu-id="e636e-159">"Shut down the device"</span></span>
* <span data-ttu-id="e636e-160">"Gerät neu starten"</span><span class="sxs-lookup"><span data-stu-id="e636e-160">"Restart the device"</span></span>
* <span data-ttu-id="e636e-161">"Gehe zu Standbymodus"</span><span class="sxs-lookup"><span data-stu-id="e636e-161">"Go to sleep"</span></span>
* <span data-ttu-id="e636e-162">"Welche Zeit ist es?"</span><span class="sxs-lookup"><span data-stu-id="e636e-162">"What time is it?"</span></span>
* <span data-ttu-id="e636e-163">"Wie viel Akku habe ich verbleiben?"</span><span class="sxs-lookup"><span data-stu-id="e636e-163">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="e636e-164">"Weitere Informationen"</span><span class="sxs-lookup"><span data-stu-id="e636e-164">"See It, Say It"</span></span><br>
        <span data-ttu-id="e636e-165">Hololens hat eine "See it"-Modell für die Spracheingabe, bei der Bezeichnungen auf Schaltflächen den Benutzern mitteilen, welche Sprachbefehle Sie auch sagen können.</span><span class="sxs-lookup"><span data-stu-id="e636e-165">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="e636e-166">Wenn Sie z. b. ein App-Fenster in hololens (1st Gen) betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.</span><span class="sxs-lookup"><span data-stu-id="e636e-166">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="e636e-167">*Image: ein Benutzer kann den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP anzupassen.*</span><span class="sxs-lookup"><span data-stu-id="e636e-167">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e636e-168">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e636e-168">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="e636e-169">![bei der Betrachtung eines App-Fensters oder eines holograms kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der Welt anzupassen](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="e636e-169">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="e636e-170">Wenn apps diese Regel befolgen, können Benutzer leicht erkennen, was zum Steuern des Systems zu sagen ist.</span><span class="sxs-lookup"><span data-stu-id="e636e-170">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="e636e-171">Um dies zu verstärken, wird bei der Betrachtung einer Schaltfläche in hololens (1st Gen) eine QuickInfo angezeigt, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprach fähig ist, und zeigt den Befehl an, um zu sprechen, um Sie zu "drücken".</span><span class="sxs-lookup"><span data-stu-id="e636e-171">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="e636e-172">Um voicemailtipps in hololens 2 anzuzeigen, zeigen Sie den sprach Cursor an, indem Sie "Select" oder "Was kann ich sagen" (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="e636e-172">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="e636e-173">*Bild: "sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.*</span><span class="sxs-lookup"><span data-stu-id="e636e-173">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="e636e-175">Sprachbefehle für schnelle – Hologramm-Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="e636e-175">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="e636e-176">Es gibt eine Reihe von Sprachbefehlen, die Sie bei der Betrachtung eines holograms zum schnellen Ausführen von Bearbeitungsaufgaben sagen können.</span><span class="sxs-lookup"><span data-stu-id="e636e-176">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="e636e-177">Diese Sprachbefehle funktionieren sowohl bei App-Fenstern als auch bei 3D-Objekten, die Sie in der Welt abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="e636e-177">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="e636e-178">**Hologram-Bearbeitungsbefehle**</span><span class="sxs-lookup"><span data-stu-id="e636e-178">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="e636e-179">Gesicht</span><span class="sxs-lookup"><span data-stu-id="e636e-179">Face me</span></span>
* <span data-ttu-id="e636e-180">Größer | Verbessern</span><span class="sxs-lookup"><span data-stu-id="e636e-180">Bigger | Enhance</span></span>
* <span data-ttu-id="e636e-181">Geringeren</span><span class="sxs-lookup"><span data-stu-id="e636e-181">Smaller</span></span>

<span data-ttu-id="e636e-182">Auf hololens 2 können Sie auch natürlichere Interaktionen in Kombination mit Eye-Blick erstellen, die implizit Kontextinformationen über das, auf das Sie verweisen, bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="e636e-182">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="e636e-183">Sie könnten z. b. einfach ein Hologramm betrachten und dann auf "put _this_" ("put this") und _dann überprüfen_, wo Sie es platzieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e636e-183">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="e636e-184">Oder Sie können sich einen Holographic-Teil auf einem komplexen Computer ansehen und sagen: "Weitere Informationen zu _diesem_".</span><span class="sxs-lookup"><span data-stu-id="e636e-184">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="e636e-185">Erkennen von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="e636e-185">Discovering voice commands</span></span>

<span data-ttu-id="e636e-186">Einige Befehle, wie z. b. die Befehle für die schnelle Bearbeitung, können ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-186">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="e636e-187">Um zu erfahren, welche Befehle Sie verwenden können, schauen Sie sich das Objekt an, und sagen Sie: "Was kann ich sagen?".</span><span class="sxs-lookup"><span data-stu-id="e636e-187">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="e636e-188">Eine Liste möglicher Befehle wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e636e-188">A list of possible commands pops up.</span></span> <span data-ttu-id="e636e-189">Sie können auch den Cursor Cursor verwenden, um die voicemailtipps für die einzelnen Schaltflächen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e636e-189">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="e636e-190">Wenn Sie eine vollständige Liste erhalten möchten, sagen Sie einfach "alle Befehle anzeigen".</span><span class="sxs-lookup"><span data-stu-id="e636e-190">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="e636e-191">Diktieren</span><span class="sxs-lookup"><span data-stu-id="e636e-191">Dictation</span></span>

<span data-ttu-id="e636e-192">Anstatt eine Typisierung mit [Luft](gaze-and-commit.md#composite-gestures)Eingaben durchführen zu können, kann es effizienter sein, Text in eine APP einzugeben.</span><span class="sxs-lookup"><span data-stu-id="e636e-192">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="e636e-193">Dadurch kann die Eingabe erheblich beschleunigt werden, sodass der Benutzer weniger Aufwand hat.</span><span class="sxs-lookup"><span data-stu-id="e636e-193">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="e636e-194">Wenn ![Stimmen, klicken Sie auf die Schaltfläche Mikrofon](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="e636e-194">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="e636e-195">*Sprach Diktat beginnt mit der Schaltfläche Mikrofon auf der Tastatur*</span><span class="sxs-lookup"><span data-stu-id="e636e-195">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="e636e-196">Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktat Modus wechseln, anstatt einzugeben.</span><span class="sxs-lookup"><span data-stu-id="e636e-196">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="e636e-197">Wählen Sie das Mikrofon auf der Seite des Texteingabe Felds aus, um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="e636e-197">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="e636e-198">Hinzufügen von Sprachbefehlen zu Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="e636e-198">Adding voice commands to your app</span></span>

<span data-ttu-id="e636e-199">Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e636e-199">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="e636e-200">Die Spracheingabe ist eine leistungsstarke und komfortable Möglichkeit zur Steuerung von System und Apps.</span><span class="sxs-lookup"><span data-stu-id="e636e-200">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="e636e-201">Da Benutzer mit einer Vielzahl von Dialekten und Akzenten sprechen, stellt die richtige Auswahl der Schlüsselwörter für die Spracherkennung sicher, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-201">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="e636e-202">Bewährte Verfahren</span><span class="sxs-lookup"><span data-stu-id="e636e-202">Best practices</span></span>

<span data-ttu-id="e636e-203">Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e636e-203">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="e636e-204">**Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus.</span><span class="sxs-lookup"><span data-stu-id="e636e-204">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="e636e-205">Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-205">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="e636e-206">Beispiel: "Video abspielen" ist besser als "das aktuell ausgewählte Video abspielen"</span><span class="sxs-lookup"><span data-stu-id="e636e-206">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="e636e-207">**Verwenden eines einfachen Vokabulars** -Beispiel: "Show Note" ist besser als "Placard anzeigen"</span><span class="sxs-lookup"><span data-stu-id="e636e-207">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="e636e-208">**Sicherstellen, dass Befehle nicht destruktiv sind**: Stellen Sie sicher, dass alle Aktionen, die von einem Spracherkennungsbefehl ausgeführt werden können, nicht destruktiv sind und leicht rückgängig gemacht werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.</span><span class="sxs-lookup"><span data-stu-id="e636e-208">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="e636e-209">**Ähnlich klingende Befehle vermeiden**: Vermeiden Sie es, mehrere Spracherkennungsbefehle zu registrieren, die sehr ähnlich klingen.</span><span class="sxs-lookup"><span data-stu-id="e636e-209">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="e636e-210">Beispiel: "mehr anzeigen" und "Store anzeigen" kann sehr ähnlich klingen.</span><span class="sxs-lookup"><span data-stu-id="e636e-210">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="e636e-211">**Registrierung der App aufheben, wenn sie nicht verwendet wird**: Wenn sich Ihre Anwendung nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung der App aufheben, damit andere Befehle nicht mit diesem verwechselt werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-211">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="e636e-212">**Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.</span><span class="sxs-lookup"><span data-stu-id="e636e-212">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="e636e-213">**Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="e636e-213">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="e636e-214">**Verwendung von Systembefehlen vermeiden**: Die folgenden Sprachbefehle sind für das System reserviert.</span><span class="sxs-lookup"><span data-stu-id="e636e-214">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="e636e-215">Diese sollten nicht von Anwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-215">These should not be used by applications.</span></span>
   * <span data-ttu-id="e636e-216">„Hey Cortana“</span><span class="sxs-lookup"><span data-stu-id="e636e-216">"Hey Cortana"</span></span>
   * <span data-ttu-id="e636e-217">„Auswählen“</span><span class="sxs-lookup"><span data-stu-id="e636e-217">"Select"</span></span>
   * <span data-ttu-id="e636e-218">"Gehe zu Start"</span><span class="sxs-lookup"><span data-stu-id="e636e-218">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="e636e-219">Vorteile von Spracheingaben</span><span class="sxs-lookup"><span data-stu-id="e636e-219">Advantages of voice input</span></span>

<span data-ttu-id="e636e-220">Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="e636e-220">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="e636e-221">Voice ist besonders gut für Schnittstellen **Traversale** geeignet, da Sie Benutzern dabei helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen (ein Benutzer könnte bei der Betrachtung einer Webseite auf die Schaltfläche "zurück" klicken, anstatt auf die Schaltfläche "zurück" in der APP zu gelangen).</span><span class="sxs-lookup"><span data-stu-id="e636e-221">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="e636e-222">Diese kleine Zeitersparnis wirkt sich **negativ** auf die Wahrnehmung der Benutzerfreundlichkeit durch den Benutzer aus und bietet Ihnen einen kleinen Wert für die Super Arbeit.</span><span class="sxs-lookup"><span data-stu-id="e636e-222">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="e636e-223">Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen.</span><span class="sxs-lookup"><span data-stu-id="e636e-223">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="e636e-224">Auf Geräten, auf denen die Eingabe auf einer Tastatur schwierig ist, kann die **sprach Diktat** -Methode eine effiziente Alternative zum Eingeben von Text sein.</span><span class="sxs-lookup"><span data-stu-id="e636e-224">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="e636e-225">In einigen Fällen, in denen der **Genauigkeits Bereich** für den Blick und die Bewegung eingeschränkt ist, kann Voice Ihnen helfen, die Absicht des Benutzers zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="e636e-225">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="e636e-226">**Vorteile der Spracheingabe für den Benutzer**</span><span class="sxs-lookup"><span data-stu-id="e636e-226">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="e636e-227">Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-227">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="e636e-228">Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.</span><span class="sxs-lookup"><span data-stu-id="e636e-228">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="e636e-229">Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.</span><span class="sxs-lookup"><span data-stu-id="e636e-229">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="e636e-230">Sie ist sozialverträglich – sie sollte sich in Bezug auf das Verhalten in die gesellschaftlichen Normen einfügen.</span><span class="sxs-lookup"><span data-stu-id="e636e-230">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="e636e-231">Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-231">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="e636e-232">Herausforderungen bei der Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e636e-232">Challenges for voice input</span></span>

<span data-ttu-id="e636e-233">Obwohl die Spracheingabe für viele verschiedene Anwendungen hervorragend ist, stellt Sie auch mehrere Herausforderungen dar.</span><span class="sxs-lookup"><span data-stu-id="e636e-233">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="e636e-234">Wenn Sie sowohl die Vorteile als auch die Herausforderungen von Spracheingaben verstanden haben, können App-Entwickler intelligentere Entscheidungen treffen, wie und wann Spracheingaben verwendet werden sollen und wie Sie Ihre Benutzer gut gestalten können.</span><span class="sxs-lookup"><span data-stu-id="e636e-234">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="e636e-235">**Spracheingabe für kontinuierliches Eingabe Steuer** Element Eine differenzierte Steuerung ist eine davon.</span><span class="sxs-lookup"><span data-stu-id="e636e-235">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="e636e-236">Beispielsweise kann ein Benutzer sein Volume in der Musik-App ändern.</span><span class="sxs-lookup"><span data-stu-id="e636e-236">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="e636e-237">Sie kann einfach "lauter" sagen, aber es ist nicht klar, wie viel lauter das System das Volume machen soll.</span><span class="sxs-lookup"><span data-stu-id="e636e-237">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="e636e-238">Der Benutzer könnte sagen: "machen Sie es etwas lauter", aber "ein wenig" ist schwierig zu quantifizieren.</span><span class="sxs-lookup"><span data-stu-id="e636e-238">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="e636e-239">Das Verschieben oder Skalieren von holograms mit Stimme ist ähnlich schwierig.</span><span class="sxs-lookup"><span data-stu-id="e636e-239">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="e636e-240">**Zuverlässigkeit der Spracheingabe Erkennung** Obwohl Spracheingabe Systeme besser und besser werden, werden Sie möglicherweise fälschlicherweise einen Sprachbefehl hören und interpretieren.</span><span class="sxs-lookup"><span data-stu-id="e636e-240">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="e636e-241">Der Schlüssel besteht darin, dieser Herausforderung in Ihrer Anwendung zu begegnen, indem er dem Benutzer Feedback zur Verfügung stellt, wenn das System lauscht, und was das System verstanden hat, um Klarheit über potenzielle Probleme bei der ordnungsgemäßen Verwendung des Benutzers zu schaffen</span><span class="sxs-lookup"><span data-stu-id="e636e-241">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="e636e-242">**Spracheingabe in freigegebenen Leerzeichen** Die Stimme ist möglicherweise nicht in den Bereichen, die Sie für andere Personen freigeben, akzeptabel.</span><span class="sxs-lookup"><span data-stu-id="e636e-242">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="e636e-243">Hier finden Sie einige Beispiele:</span><span class="sxs-lookup"><span data-stu-id="e636e-243">Here are a few examples:</span></span>
* <span data-ttu-id="e636e-244">Der Benutzer möchte möglicherweise keine anderen Personen stören (z. b. in einer stillen Bibliothek oder einem freigegebenen Büro).</span><span class="sxs-lookup"><span data-stu-id="e636e-244">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="e636e-245">Benutzer sind vielleicht nicht in der Öffentlichkeit,</span><span class="sxs-lookup"><span data-stu-id="e636e-245">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="e636e-246">Ein Benutzer ist möglicherweise unbequem, wenn er eine persönliche oder vertrauliche Nachricht (einschließlich Kenn Wörtern) einhört, während andere Benutzer lauschen.</span><span class="sxs-lookup"><span data-stu-id="e636e-246">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="e636e-247">**Spracheingabe von eindeutigen oder unbekannten Wörtern** Probleme bei der Spracheingabe werden auch angezeigt, wenn Benutzer Wörter, die möglicherweise dem System unbekannt sind, wie z. b. Spitznamen, bestimmte slang-Wörter oder Abkürzungen, eingeben.</span><span class="sxs-lookup"><span data-stu-id="e636e-247">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="e636e-248">**Erlernen von Sprachbefehlen** Das ultimative Ziel ist es, sich auf natürliche Weise mit Ihrem System zu Konversation, häufig verlassen sich apps jedoch auf bestimmte vordefinierte Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="e636e-248">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="e636e-249">Eine Herausforderung, die mit einem großen Satz von Sprachbefehlen verknüpft ist, besteht darin, Sie zu unterstützen, ohne den Benutzer zu überlasten und den Benutzern zu helfen, Sie beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="e636e-249">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="e636e-250">Statusangaben für Spracherkennungsfeedback</span><span class="sxs-lookup"><span data-stu-id="e636e-250">Voice feedback states</span></span>

<span data-ttu-id="e636e-251">Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**.</span><span class="sxs-lookup"><span data-stu-id="e636e-251">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="e636e-252">Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="e636e-252">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="e636e-253">Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="e636e-253">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="e636e-254">![1. Regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="e636e-254">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="e636e-255">**1. regulärer Cursor Zustand**</span><span class="sxs-lookup"><span data-stu-id="e636e-255">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e636e-256">![2. Kommuniziert Sprachfeedback und verschwindet dann](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="e636e-256">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="e636e-257">**2. kommuniziert Feedback und verschwindet dann**</span><span class="sxs-lookup"><span data-stu-id="e636e-257">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e636e-258">![\* 3.</span><span class="sxs-lookup"><span data-stu-id="e636e-258">![\*3.</span></span> <span data-ttu-id="e636e-259">Regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="e636e-259">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="e636e-260">**3. zurück zum regulären Cursor Zustand**</span><span class="sxs-lookup"><span data-stu-id="e636e-260">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="e636e-261">Wichtige Informationen zur Spracherkennung in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e636e-261">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="e636e-262">Sagen Sie **„Auswählen“** , während Sie eine Schaltfläche anvisieren (Sie können dies überall verwenden, um auf eine Schaltfläche zu klicken).</span><span class="sxs-lookup"><span data-stu-id="e636e-262">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="e636e-263">Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e636e-263">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="e636e-264">Beim Betrachten einer App kann ein Benutzer z. B. den Befehl „Entfernen“ sagen, um die App aus der Umgebung zu entfernen (das spart Zeit, da die App nicht mit der Hand angeklickt werden muss).</span><span class="sxs-lookup"><span data-stu-id="e636e-264">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="e636e-265">Sie können initiieren, dass Cortana zuhört, indem Sie **„Hey Cortana“** sagen.</span><span class="sxs-lookup"><span data-stu-id="e636e-265">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="e636e-266">Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="e636e-266">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="e636e-267">Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e636e-267">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="e636e-268">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="e636e-268">What can I say?</span></span>
* <span data-ttu-id="e636e-269">Woher weiß ich, ob das System mich richtig verstanden hat?</span><span class="sxs-lookup"><span data-stu-id="e636e-269">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="e636e-270">Das System versteht meine Sprachbefehle immer wieder falsch.</span><span class="sxs-lookup"><span data-stu-id="e636e-270">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="e636e-271">Es reagiert nicht, wenn ich einen Sprachbefehl erteile.</span><span class="sxs-lookup"><span data-stu-id="e636e-271">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="e636e-272">Es reagiert falsch, wenn ich einen Sprachbefehl erteile.</span><span class="sxs-lookup"><span data-stu-id="e636e-272">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="e636e-273">Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?</span><span class="sxs-lookup"><span data-stu-id="e636e-273">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="e636e-274">Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?</span><span class="sxs-lookup"><span data-stu-id="e636e-274">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="e636e-275">Kommunikation</span><span class="sxs-lookup"><span data-stu-id="e636e-275">Communication</span></span>

<span data-ttu-id="e636e-276">Für Anwendungen, die die von hololens bereitgestellten angepassten audioeingabeverarbeitungs-Optionen nutzen möchten, ist es wichtig, die verschiedenen [audiostreamkategorien](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) zu verstehen, die Ihre APP nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="e636e-276">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="e636e-277">Windows 10 unterstützt mehrere verschiedene streamkategorien, und hololens nutzt drei dieser Möglichkeiten, um die benutzerdefinierte Verarbeitung zur Optimierung der Mikrofon Audioqualität zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist und für Umgebungs Umgebungs Audiodaten verwendet werden kann. Erfassungs Szenarien (d.h. "Camcorder").</span><span class="sxs-lookup"><span data-stu-id="e636e-277">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="e636e-278">Die Kategorie AudioCategory_Communications Stream ist für die Sprach-und Erzähl Szenarios angepasst und stellt dem Client einen 16-Bit-Mono-Mono-Audiostream der Stimme des Benutzers zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e636e-278">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="e636e-279">Die Kategorie AudioCategory_Speech Stream ist für die Sprach-Engine hololens (Windows) angepasst und bietet einen 16-Bit-Mono-Mono-Datenstrom der Stimme des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="e636e-279">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="e636e-280">Diese Kategorie kann bei Bedarf von Sprachmodulen von Drittanbietern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e636e-280">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="e636e-281">Die AudioCategory_Other Stream-Kategorie ist für die Audioaufzeichnung in Umgebungs Umgebungen angepasst und stellt dem Client einen Stereo-Audiostream mit 48 kHz 24 Bit bereit.</span><span class="sxs-lookup"><span data-stu-id="e636e-281">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="e636e-282">Die gesamte Audioverarbeitung ist Hardware beschleunigt. Dies bedeutet, dass die Features viel weniger Leistung als bei der Verarbeitung der hololens-CPU benötigen.</span><span class="sxs-lookup"><span data-stu-id="e636e-282">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="e636e-283">Vermeiden Sie die Ausführung einer anderen audioeingabeverarbeitung auf der CPU, um die Akku Lebensdauer zu maximieren und die integrierte, offloaded audioeingabeverarbeitung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="e636e-283">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="e636e-284">Sprachen</span><span class="sxs-lookup"><span data-stu-id="e636e-284">Languages</span></span>

<span data-ttu-id="e636e-285">Hololens 2 unterstützt auch weitere Sprachen.</span><span class="sxs-lookup"><span data-stu-id="e636e-285">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="e636e-286">Beachten Sie, dass Sprachbefehle immer in der Anzeige Sprache des Systems ausgeführt werden, auch wenn mehrere Tastaturen installiert sind oder wenn apps versuchen, eine Spracherkennung in einer anderen Sprache zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e636e-286">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e636e-287">Fehlerbehebung</span><span class="sxs-lookup"><span data-stu-id="e636e-287">Troubleshooting</span></span>

<span data-ttu-id="e636e-288">Wenn Sie Probleme bei der Verwendung von "Select" und "Hey Cortana" haben, versuchen Sie, zu einem ruhigeren Bereich zu wechseln, die Ursache für Rauschen zu machen oder lauter zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="e636e-288">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="e636e-289">Zu diesem Zeitpunkt wird die Spracherkennung in hololens speziell für systemeigene Sprecher von USA Englisch optimiert und optimiert.</span><span class="sxs-lookup"><span data-stu-id="e636e-289">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="e636e-290">Für Windows Mixed Reality Developer Edition, Version 2017, funktioniert die audioendpunkt-Verwaltungs Logik problemlos (immer), nachdem Sie sich nach der anfänglichen HMD-Verbindung beim PC-Desktop abgemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="e636e-290">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="e636e-291">Vor dem ersten Abmelden/in-Ereignis nach dem Durchlaufen von WMR OOBE könnte der Benutzer verschiedene Probleme mit der Audiofunktionalität aufweisen, von denen kein audiowechsel bis hin zu keinem audiowechsel stattfindet, je nachdem, wie das System vor dem ersten Herstellen einer Verbindung mit dem HMD eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="e636e-291">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e636e-292">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="e636e-292">See also</span></span>
* [<span data-ttu-id="e636e-293">Blick und Commit</span><span class="sxs-lookup"><span data-stu-id="e636e-293">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e636e-294">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e636e-294">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e636e-295">Mr-Eingabe 212: Stimme</span><span class="sxs-lookup"><span data-stu-id="e636e-295">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="e636e-296">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="e636e-296">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="e636e-297">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="e636e-297">Voice input in Unity</span></span>](voice-input-in-unity.md)
