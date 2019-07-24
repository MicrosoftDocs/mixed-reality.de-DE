---
title: Spracheingabe
description: Die Spracheingabe ist eine Kern Eingabe für hololens und Windows Mixed Reality-immersive Headsets. Voice kann für Befehle, Diktat, Cortana usw. verwendet werden.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, Input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829947"
---
# <a name="voice-input"></a><span data-ttu-id="b4293-105">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="b4293-105">Voice input</span></span>

<span data-ttu-id="b4293-106">Voice ist eine der drei wichtigen Formen der Eingabe in hololens.</span><span class="sxs-lookup"><span data-stu-id="b4293-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="b4293-107">Damit können Sie ein – Hologramm direkt aufrufen, ohne [Gesten](gestures.md)verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="b4293-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="b4293-108">Sie betrachten [einfach ein](gaze.md) – Hologramm und sprechen Ihren Befehl.</span><span class="sxs-lookup"><span data-stu-id="b4293-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="b4293-109">Die Spracheingabe kann eine natürliche Möglichkeit sein, ihre Absicht zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="b4293-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="b4293-110">Die Spracheingabe eignet sich besonders gut für die Durchführung komplexer Schnittstellen, da Benutzer mit einem Befehl die Möglichkeit haben, die Verwendung von Netz Menüs zu</span><span class="sxs-lookup"><span data-stu-id="b4293-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="b4293-111">Die Spracheingabe wird von [derselben Engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) unterstützt, die Sprache in allen anderen universellen Windows-Apps unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b4293-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="b4293-112">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="b4293-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4293-113"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="b4293-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b4293-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4293-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b4293-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b4293-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b4293-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4293-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4293-117">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="b4293-117">Voice input</span></span></td>
        <td><span data-ttu-id="b4293-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b4293-118">✔️</span></span></td>
        <td><span data-ttu-id="b4293-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b4293-119">✔️</span></span></td>
        <td><span data-ttu-id="b4293-120">✔️ (mit Mikrofon)</span><span class="sxs-lookup"><span data-stu-id="b4293-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="b4293-121">Der Befehl "Select"</span><span class="sxs-lookup"><span data-stu-id="b4293-121">The "select" command</span></span>

<span data-ttu-id="b4293-122">Selbst wenn Sie Ihrer APP keine Sprachunterstützung hinzufügen, können Ihre Benutzer Hologramme einfach durch das sagen von "Select" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b4293-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="b4293-123">Dies verhält sich wie eine [Luft](gestures.md#air-tap) Abzweigung in hololens, das Drücken der Schaltfläche "auswählen" auf dem [hololens-Clicker](hardware-accessories.md#hololens-clicker)oder das Drücken des Auslösers auf einem [Windows Mixed Reality Motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="b4293-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="b4293-124">Sie werden einen Sound hören und sehen, dass eine QuickInfo mit "Select" als Bestätigung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b4293-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="b4293-125">"Select" wird durch einen Algorithmus für die Erkennung eines niedrigen Leistungs Worts aktiviert, sodass Sie jederzeit mit minimalen Auswirkungen auf die Akku Lebensdauer jederzeit angezeigt werden können. Dies gilt auch für Ihre Hände.</span><span class="sxs-lookup"><span data-stu-id="b4293-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="b4293-126">Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b4293-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="b4293-127">!["Select" (auswählen), um den Sprachbefehl zur Auswahl zu verwenden](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="b4293-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="b4293-128">*"Select" (auswählen), um den Sprachbefehl zur Auswahl zu verwenden*</span><span class="sxs-lookup"><span data-stu-id="b4293-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="b4293-129">Hallo, Cortana</span><span class="sxs-lookup"><span data-stu-id="b4293-129">Hey Cortana</span></span>

<span data-ttu-id="b4293-130">Sie können auch "Hey Cortana" sagen, um Cortana jederzeit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b4293-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="b4293-131">Sie müssen nicht warten, bis Sie angezeigt wird, um Ihre Frage zu stellen oder eine Anweisung zu geben, z. b. "Hey Cortana What es Weather?".</span><span class="sxs-lookup"><span data-stu-id="b4293-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="b4293-132">als einzelner Satz.</span><span class="sxs-lookup"><span data-stu-id="b4293-132">as a single sentence.</span></span> <span data-ttu-id="b4293-133">Weitere Informationen zu Cortana und den Möglichkeiten, die Sie tun können, finden Sie einfach!</span><span class="sxs-lookup"><span data-stu-id="b4293-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="b4293-134">Sagen Sie "Hallo Cortana was kann ich sagen?"</span><span class="sxs-lookup"><span data-stu-id="b4293-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="b4293-135">und Sie werden eine Liste der funktionierenden und vorgeschlagenen Befehle abrufen.</span><span class="sxs-lookup"><span data-stu-id="b4293-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="b4293-136">Wenn Sie sich bereits in der Cortana-App befinden, können Sie auch auf die **?**</span><span class="sxs-lookup"><span data-stu-id="b4293-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="b4293-137">Symbol auf der Rand Leiste, um das gleiche Menü zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="b4293-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="b4293-138">**Hololens-spezifische Befehle**</span><span class="sxs-lookup"><span data-stu-id="b4293-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="b4293-139">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="b4293-139">"What can I say?"</span></span>
* <span data-ttu-id="b4293-140">"Go Home" oder "Gehe zu Start"-anstelle von " [Bloom](gestures.md#bloom) ", um zum [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu gelangen</span><span class="sxs-lookup"><span data-stu-id="b4293-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="b4293-141">"Starten <app>"</span><span class="sxs-lookup"><span data-stu-id="b4293-141">"Launch <app>"</span></span>
* <span data-ttu-id="b4293-142">"Hier <app> verschieben"</span><span class="sxs-lookup"><span data-stu-id="b4293-142">"Move <app> here"</span></span>
* <span data-ttu-id="b4293-143">"Bild nehmen"</span><span class="sxs-lookup"><span data-stu-id="b4293-143">"Take a picture"</span></span>
* <span data-ttu-id="b4293-144">"Aufzeichnung starten"</span><span class="sxs-lookup"><span data-stu-id="b4293-144">"Start recording"</span></span>
* <span data-ttu-id="b4293-145">"Aufzeichnung anhalten"</span><span class="sxs-lookup"><span data-stu-id="b4293-145">"Stop recording"</span></span>
* <span data-ttu-id="b4293-146">"Erhöhen der Helligkeit"</span><span class="sxs-lookup"><span data-stu-id="b4293-146">"Increase the brightness"</span></span>
* <span data-ttu-id="b4293-147">"Die Helligkeit verringern"</span><span class="sxs-lookup"><span data-stu-id="b4293-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="b4293-148">"Volume vergrößern"</span><span class="sxs-lookup"><span data-stu-id="b4293-148">"Increase the volume"</span></span>
* <span data-ttu-id="b4293-149">"Volume verkleinern"</span><span class="sxs-lookup"><span data-stu-id="b4293-149">"Decrease the volume"</span></span>
* <span data-ttu-id="b4293-150">"Stumm schalten" oder "unstumm schalten"</span><span class="sxs-lookup"><span data-stu-id="b4293-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="b4293-151">"Gerät Herunterfahren"</span><span class="sxs-lookup"><span data-stu-id="b4293-151">"Shut down the device"</span></span>
* <span data-ttu-id="b4293-152">"Gerät neu starten"</span><span class="sxs-lookup"><span data-stu-id="b4293-152">"Restart the device"</span></span>
* <span data-ttu-id="b4293-153">"Gehe zu Standbymodus"</span><span class="sxs-lookup"><span data-stu-id="b4293-153">"Go to sleep"</span></span>
* <span data-ttu-id="b4293-154">"Welche Zeit ist es?"</span><span class="sxs-lookup"><span data-stu-id="b4293-154">"What time is it?"</span></span>
* <span data-ttu-id="b4293-155">"Wie viel Akku habe ich verbleiben?"</span><span class="sxs-lookup"><span data-stu-id="b4293-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="b4293-156">"Anrufen <contact>" (erfordert Skype für hololens)</span><span class="sxs-lookup"><span data-stu-id="b4293-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="b4293-157">"Weitere Informationen"</span><span class="sxs-lookup"><span data-stu-id="b4293-157">"See It, Say It"</span></span>

<span data-ttu-id="b4293-158">Hololens hat eine "See it"-Modell für die Spracheingabe, bei der Bezeichnungen auf Schaltflächen den Benutzern mitteilen, welche Sprachbefehle Sie auch sagen können.</span><span class="sxs-lookup"><span data-stu-id="b4293-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="b4293-159">Wenn Sie z. b. eine 2D-App betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.</span><span class="sxs-lookup"><span data-stu-id="b4293-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Wenn Sie sich eine 2D-APP oder ein Hologram ansehen, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.](images/microphone-600px.png)

<span data-ttu-id="b4293-161">Wenn apps diese Regel befolgen, können Benutzer leicht erkennen, was zum Steuern des Systems zu sagen ist.</span><span class="sxs-lookup"><span data-stu-id="b4293-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="b4293-162">Um dies zu verstärken, sehen Sie die QuickInfo, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprach fähig ist, und zeigt den Befehl an, um zu sprechen, um die Schaltfläche zu "drücken".</span><span class="sxs-lookup"><span data-stu-id="b4293-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="b4293-163">![Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="b4293-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="b4293-164">*"Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.*</span><span class="sxs-lookup"><span data-stu-id="b4293-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="b4293-165">Sprachbefehle für schnelle Hologram-Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="b4293-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="b4293-166">Es gibt auch eine Reihe von Sprachbefehlen, die Sie bei der Betrachtung eines holograms zum schnellen Ausführen von Bearbeitungsaufgaben sagen können.</span><span class="sxs-lookup"><span data-stu-id="b4293-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="b4293-167">Diese Sprachbefehle funktionieren sowohl für 2D-Apps als auch für 3D-Objekte, die Sie in der Welt abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="b4293-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="b4293-168">**Hologram-Bearbeitungsbefehle**</span><span class="sxs-lookup"><span data-stu-id="b4293-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="b4293-169">Gesicht</span><span class="sxs-lookup"><span data-stu-id="b4293-169">Face me</span></span>
* <span data-ttu-id="b4293-170">Größer | Verbessern</span><span class="sxs-lookup"><span data-stu-id="b4293-170">Bigger | Enhance</span></span>
* <span data-ttu-id="b4293-171">Geringeren</span><span class="sxs-lookup"><span data-stu-id="b4293-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="b4293-172">Diktieren</span><span class="sxs-lookup"><span data-stu-id="b4293-172">Dictation</span></span>

<span data-ttu-id="b4293-173">Anstatt eine Typisierung mit [Luft](gestures.md#air-tap)Eingaben durchführen zu können, kann es effizienter sein, Text in eine APP einzugeben.</span><span class="sxs-lookup"><span data-stu-id="b4293-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="b4293-174">Dadurch kann die Eingabe erheblich beschleunigt werden, sodass der Benutzer weniger Aufwand hat.</span><span class="sxs-lookup"><span data-stu-id="b4293-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="b4293-175">![Sprach Diktat beginnt mit der Schaltfläche Mikrofon](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="b4293-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="b4293-176">*Sprach Diktat beginnt mit der Schaltfläche Mikrofon auf der Tastatur*</span><span class="sxs-lookup"><span data-stu-id="b4293-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="b4293-177">Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktat Modus wechseln, anstatt einzugeben.</span><span class="sxs-lookup"><span data-stu-id="b4293-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="b4293-178">Wählen Sie das Mikrofon auf der Seite des Texteingabe Felds aus, um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="b4293-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="b4293-179">Kommunikation</span><span class="sxs-lookup"><span data-stu-id="b4293-179">Communication</span></span>

<span data-ttu-id="b4293-180">Für Anwendungen, die die von hololens bereitgestellten angepassten audioeingabeverarbeitungs-Optionen nutzen möchten, ist es wichtig, die verschiedenen [audiostreamkategorien](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) zu verstehen, die Ihre APP nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="b4293-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="b4293-181">Windows 10 unterstützt mehrere verschiedene streamkategorien, und hololens nutzt drei dieser Möglichkeiten, um die benutzerdefinierte Verarbeitung zur Optimierung der Mikrofon Audioqualität zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist und für Umgebungs Umgebungs Audiodaten verwendet werden kann. Erfassungs Szenarien (d.h. "Camcorder").</span><span class="sxs-lookup"><span data-stu-id="b4293-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="b4293-182">Die Kategorie AudioCategory_Communications Stream ist für die Sprach-und Erzähl Szenarios angepasst und stellt dem Client einen 16-Bit-Mono-Mono-Audiostream der Stimme des Benutzers zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b4293-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="b4293-183">Die Kategorie AudioCategory_Speech Stream ist für die Sprach-Engine hololens (Windows) angepasst und bietet einen 16-Bit-Mono-Mono-Datenstrom der Stimme des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="b4293-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="b4293-184">Diese Kategorie kann bei Bedarf von Sprachmodulen von Drittanbietern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b4293-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="b4293-185">Die AudioCategory_Other Stream-Kategorie ist für die Audioaufzeichnung in Umgebungs Umgebungen angepasst und stellt dem Client einen Stereo-Audiostream mit 48 kHz 24 Bit bereit.</span><span class="sxs-lookup"><span data-stu-id="b4293-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="b4293-186">Die gesamte Audioverarbeitung ist Hardware beschleunigt. Dies bedeutet, dass die Features viel weniger Leistung als bei der Verarbeitung der hololens-CPU benötigen.</span><span class="sxs-lookup"><span data-stu-id="b4293-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="b4293-187">Vermeiden Sie die Ausführung einer anderen audioeingabeverarbeitung auf der CPU, um die Akku Lebensdauer zu maximieren und die integrierte, offloaded audioeingabeverarbeitung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="b4293-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b4293-188">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="b4293-188">Troubleshooting</span></span>

<span data-ttu-id="b4293-189">Wenn Sie Probleme bei der Verwendung von "Select" und "Hey Cortana" haben, versuchen Sie, zu einem ruhigeren Bereich zu wechseln, die Ursache für Rauschen zu machen oder lauter zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="b4293-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="b4293-190">Zu diesem Zeitpunkt wird die Spracherkennung in hololens speziell für systemeigene Sprecher von USA Englisch optimiert und optimiert.</span><span class="sxs-lookup"><span data-stu-id="b4293-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="b4293-191">Für Windows Mixed Reality Developer Edition, Version 2017, funktioniert die audioendpunkt-Verwaltungs Logik problemlos (immer), nachdem Sie sich nach der anfänglichen HMD-Verbindung beim PC-Desktop abgemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="b4293-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="b4293-192">Vor dem ersten Abmelden/in-Ereignis nach dem Durchlaufen von WMR OOBE könnte der Benutzer verschiedene Probleme mit der Audiofunktionalität aufweisen, von denen kein audiowechsel bis hin zu keinem audiowechsel stattfindet, je nachdem, wie das System vor dem ersten Herstellen einer Verbindung mit dem HMD eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="b4293-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4293-193">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b4293-193">See also</span></span>
* [<span data-ttu-id="b4293-194">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="b4293-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="b4293-195">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="b4293-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="b4293-196">MR-Eingabe 212: Sprache</span><span class="sxs-lookup"><span data-stu-id="b4293-196">MR Input 212: Voice</span></span>](holograms-212.md)
