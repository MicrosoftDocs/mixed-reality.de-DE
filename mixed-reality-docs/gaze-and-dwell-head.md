---
title: Anvisieren mit dem Kopf und Verweilen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Verweilen“
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Verweilen, Interaktion, Entwurf
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439311"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="67ea8-104">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="67ea8-104">Head-gaze and dwell</span></span>

<span data-ttu-id="67ea8-105">Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein.</span><span class="sxs-lookup"><span data-stu-id="67ea8-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="67ea8-106">Sprachbefehle können wie Gesten in bestimmten Kontexten unzuverlässig sein, z. B. unter zu lauten Umgebungsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="67ea8-107">Darüber hinaus ist der Einsatz der Stimme zur Steuerung von Computern nicht überall üblich, aber seine Bedeutung nimmt sicherlich zu.</span><span class="sxs-lookup"><span data-stu-id="67ea8-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="67ea8-108">„Anvisieren mit dem Kopf und Verweilen“ bietet den bekanntesten und einfach zu bedienenden Mechanismus für das freihändige Heads-Up-Arbeiten mit der HoloLens.</span><span class="sxs-lookup"><span data-stu-id="67ea8-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="67ea8-109">Darüber hinaus ist das Modell „Anvisieren mit dem Kopf und Verweilen“ unabhängig von Störgeräuschen und Ruheeinschränkungen in der Betriebssystemumgebung zu 100 % zuverlässig.</span><span class="sxs-lookup"><span data-stu-id="67ea8-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="67ea8-110">Szenarien</span><span class="sxs-lookup"><span data-stu-id="67ea8-110">Scenarios</span></span>

<span data-ttu-id="67ea8-111">In Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, ist der Kopf-und sprach Einstieg hervorragend, und die Stimme ist aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig oder nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="67ea8-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="67ea8-112">Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern.</span><span class="sxs-lookup"><span data-stu-id="67ea8-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="67ea8-113">Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt.</span><span class="sxs-lookup"><span data-stu-id="67ea8-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="67ea8-114">Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet.</span><span class="sxs-lookup"><span data-stu-id="67ea8-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="67ea8-115">In der Kopfzeile und im Leben kann die Person, die die hololens verwendet, sicher in Ihrem Referenzmaterial navigieren, ohne den Workflow zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="67ea8-116">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="67ea8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="67ea8-117"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="67ea8-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="67ea8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="67ea8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="67ea8-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="67ea8-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="67ea8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="67ea8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="67ea8-121">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="67ea8-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="67ea8-122">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="67ea8-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="67ea8-123">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="67ea8-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="67ea8-124">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="67ea8-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="67ea8-125">Designprinzipien</span><span class="sxs-lookup"><span data-stu-id="67ea8-125">Design principles</span></span>

<span data-ttu-id="67ea8-126">**Vermeiden Sie "Blick als Waffe".**</span><span class="sxs-lookup"><span data-stu-id="67ea8-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="67ea8-127">„Anvisieren mit dem Kopf und Verweilen“ erfordert ein intuitives visuelles Feedback, aber zu viel Feedback kann beklemmend wirken.</span><span class="sxs-lookup"><span data-stu-id="67ea8-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="67ea8-128">Das Feedback sollte einem Benutzer helfen sein Ziel zu erkennen, aber das Ziel nicht gegen seinen Willen automatisch auswählen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="67ea8-129">Das Lesen von Text, Symbolen und Beschriftungen erfordert eine zusätzliche Berücksichtigung, um einer Person den Raum zu geben, die Informationen vor der Auswahl zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="67ea8-130">**Durchsuchen der Goldilocks-Geschwindigkeit**</span><span class="sxs-lookup"><span data-stu-id="67ea8-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="67ea8-131">Verweilinteraktionen können je nach Auswirkung der Navigation unterschiedliche Timer aufweisen – häufiger verwendete Funktionen profitieren in der Regel von schnelleren Füllzeiten, während konsequentere Funktionen von längeren Füllzeiten profitieren können.</span><span class="sxs-lookup"><span data-stu-id="67ea8-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="67ea8-132">Bei der Verwendung eines Fülleffekts zur Darstellung dieser Timer können Animationskurven der Füllfarbe das Gefühl schnellerer Füllzeiten positiv beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="67ea8-133">Es sollte erwogen werden, dem Benutzer die Möglichkeit zu bieten, sich für eine schnelle, mittlere und langsame Füllgeschwindigkeit zu entscheiden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="67ea8-134">**"No-No to Yo-Yo Effect"**</span><span class="sxs-lookup"><span data-stu-id="67ea8-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="67ea8-135">Der Jo-Jo-Effekt ist ein unangenehmes Muster der Kopfbewegung, das entstehen kann, wenn die Positionierung von Inhalten und die Steuerung durch „Anvisieren mit dem Kopf und Verweilen“ die Personen zwingt, ständig auf und ab zu schauen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="67ea8-136">Beispielsweise löst ein Listen Navigationsbereich mit der Schaltfläche "Head-Blick" und "Wohnen" am unteren Rand eine Schleife von "-Look down" aus, um zu leben, nach Ergebnissen zu suchen, zu warten, usw. Dieses resultierende Muster ist unbequem und sollte vermieden werden, indem Navigations Steuerelemente an einem zentralisierten Speicherort platziert werden, der weniger hin und her erfordert.</span><span class="sxs-lookup"><span data-stu-id="67ea8-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="67ea8-137">Die Positionierung der Schaltflächen zum Verweilen in Bezug auf ihre Wirkung wird für den Tragekomfort wichtig.</span><span class="sxs-lookup"><span data-stu-id="67ea8-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="67ea8-138">Richtlinien und bewährte Methoden für die Benutzerumgebung</span><span class="sxs-lookup"><span data-stu-id="67ea8-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="67ea8-139">Zielgrößen</span><span class="sxs-lookup"><span data-stu-id="67ea8-139">Target sizes</span></span>
  <span data-ttu-id="67ea8-140">Um auf einfache Weise zugänglich zu sein, müssen die Haupt-und zielziele groß genug sein, um sich bequem anzusehen und einen Head-stabilen auf dem Ziel für den vorgeschriebenen Zeitraum zu halten.</span><span class="sxs-lookup"><span data-stu-id="67ea8-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="67ea8-141">Wir empfehlen eine minimale Zielgröße von 2 Grad, um die komfortablere Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="67ea8-142">Visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="67ea8-142">Visual feedback</span></span>

<span data-ttu-id="67ea8-143">Wenn Sie eine radiale Füllung zur Darstellung des Timers für das Verweilen verwenden, beginnen Sie in der Mitte der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="67ea8-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="67ea8-144">Eine konsistente Reaktion ist weniger irritierend als vollständig unterschiedliche Richtungen auf verschiedenen Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="67ea8-145">Diese Regel kann jedoch für direktionale Interaktionen (z. B. Navigation nach oben/unten/links/rechts usw.) missachtet werden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="67ea8-146">Microsoft Dynamics 365-Handbücher machen z. B. eine Ausnahme, wenn WEITER/ZURÜCK von links nach rechts ausgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="67ea8-147">Erwägen Sie für Szenarien wie das Umschalten einer Schaltfläche, die radiale Füllung von außen zu invertieren.</span><span class="sxs-lookup"><span data-stu-id="67ea8-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="67ea8-148">Das gegenläufige Gefühl beim Drücken einer Schaltfläche ist ein angenehmes visuelles Muster, das beibehalten werden sollte.</span><span class="sxs-lookup"><span data-stu-id="67ea8-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="67ea8-149">Schrittweise Offenlegung</span><span class="sxs-lookup"><span data-stu-id="67ea8-149">Progressive disclosure</span></span>

<span data-ttu-id="67ea8-150">„Schrittweise Offenlegung“ bedeutet, dass nur so viele Details angezeigt werden, wie in den einzelnen Phasen einer Interaktion relevant sind.</span><span class="sxs-lookup"><span data-stu-id="67ea8-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="67ea8-151">Für das Verweilen bedeutet dies, dass das Verweilziel beim Hervorheben (z. B. in einem Listensteuerelement) offengelegt wird.</span><span class="sxs-lookup"><span data-stu-id="67ea8-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="67ea8-152">Überdimensionale Ziele</span><span class="sxs-lookup"><span data-stu-id="67ea8-152">Oversized targets</span></span>
<span data-ttu-id="67ea8-153">Der Verweilbereich kann größer als das inaktive Symbol sein, um die Verwendung zu erleichtern, wie die Schaltfläche „Zurück“ in Microsoft Dynamics 365-Handbüchern.</span><span class="sxs-lookup"><span data-stu-id="67ea8-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="67ea8-154">Vermeiden von Flimmern durch verzögertes Feedback</span><span class="sxs-lookup"><span data-stu-id="67ea8-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="67ea8-155">Verwenden Sie eine kurze Verzögerung, bevor Sie mit dem visuellen Feedback beginnen, um ein Flimmern zu vermeiden, wenn ein Benutzer ein Verweilziel überquert.</span><span class="sxs-lookup"><span data-stu-id="67ea8-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="67ea8-156">Halten Sie für Schaltflächen, mit denen häufig interagiert wird, die Verzögerung sehr kurz, damit die Anwendung reaktiv ist.</span><span class="sxs-lookup"><span data-stu-id="67ea8-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="67ea8-157">Für Schaltflächen, die nur selten behandelt werden, kann eine längere Verzögerung sinnvoll sein, um die Schnittstelle zu vermeiden, die twitlapp ist.</span><span class="sxs-lookup"><span data-stu-id="67ea8-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="67ea8-158">Muster der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="67ea8-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="67ea8-159">Schaltflächen mit häufiger Interaktion</span><span class="sxs-lookup"><span data-stu-id="67ea8-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="67ea8-160">Schaltflächen mit hoher Frequenz sind Schaltflächen, die in der Regel in einer Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="67ea8-161">Ein gutes Beispiel hierfür sind die Schaltflächen „Weiter“ und „Zurück“ in Microsoft Dynamics 365-Handbüchern.</span><span class="sxs-lookup"><span data-stu-id="67ea8-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="67ea8-162">**Empfehlungen**</span><span class="sxs-lookup"><span data-stu-id="67ea8-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="67ea8-163">Die Schaltflächen mit hoher Frequenz sollten groß sein, und es ist einfacher, mit dem Kopf zu erreichen</span><span class="sxs-lookup"><span data-stu-id="67ea8-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="67ea8-164">Bleiben Sie in der Nähe der Augen, um eine ergonomische Überlastung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="67ea8-165">*Bild: Microsoft Dynamics 365 Guides Schaltfläche "weiter"*</span><span class="sxs-lookup"><span data-stu-id="67ea8-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Schaltfläche "Microsoft Dynamics 365 Guides Next"](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="67ea8-167">Schaltflächen mit seltener Interaktion</span><span class="sxs-lookup"><span data-stu-id="67ea8-167">Low frequency buttons</span></span>
<span data-ttu-id="67ea8-168">Schaltflächen mit seltener Interaktion sind Schaltflächen, mit denen in der Anwendung nicht so häufig interagiert wird.</span><span class="sxs-lookup"><span data-stu-id="67ea8-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="67ea8-169">Ein gutes Beispiel könnte eine Schaltfläche für den Zugriff auf das Einstellungsmenü oder eine Schaltfläche zum Löschen der gesamten Arbeit sein.</span><span class="sxs-lookup"><span data-stu-id="67ea8-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="67ea8-170">Versuchen Sie, diese Schaltflächen von häufig genutzten Pfaden zum Anvisieren mit dem Kopf fernzuhalten, um eine versehentliche Aktivierung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="67ea8-171">Bestätigungen</span><span class="sxs-lookup"><span data-stu-id="67ea8-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="67ea8-172">Wenn eine Aktion erhebliche Auswirkungen hat, wie das Aufladen von Geld, das Löschen von Arbeit oder das Starten eines zeitintensiven Prozesses, ist es sinnvoll, die Auswahl einer Schaltfläche durch eine Person bestätigen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="67ea8-173">**Empfehlungen**</span><span class="sxs-lookup"><span data-stu-id="67ea8-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="67ea8-174">Auswahlhervorhebung auf Hauptschaltfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="67ea8-175">Verweilziel gleichzeitig mit der Auswahlhervorhebung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="67ea8-176">Verweilziel für die sekundäre Schaltfläche beim Anvisieren mit dem Kopf anzeigen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="67ea8-177">*Bild: Microsoft Dynamics 365-Führungslinien Bestätigungs Dialogfeld*</span><span class="sxs-lookup"><span data-stu-id="67ea8-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Bestätigungs Dialogfeld für Microsoft Dynamics 365-Anleitungen](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="67ea8-179">Umschalter</span><span class="sxs-lookup"><span data-stu-id="67ea8-179">Toggle buttons</span></span>
<span data-ttu-id="67ea8-180">Umschalter erfordern eine differenzierte Logik, um ordnungsgemäß zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="67ea8-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="67ea8-181">Wenn eine Person auf einem Umschalter verweilt und ihn aktiviert, muss sie die Schaltfläche verlassen und dann zurückkehren, um die Verweillogik neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="67ea8-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="67ea8-182">Es ist wichtig, dass die umschaltbaren Schaltflächen einen eindeutigen aktiven und inaktiven Zustand aufweisen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="67ea8-183">Listenansichten</span><span class="sxs-lookup"><span data-stu-id="67ea8-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="67ea8-184">Listenansichten stellen eine besondere Herausforderung für Kopf-und eingabeeingaben dar.</span><span class="sxs-lookup"><span data-stu-id="67ea8-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="67ea8-185">Benutzer müssen in der Lage sein, den Inhalt zu scannen, ohne das Gefühl zu haben, dass sie sich in der Nähe der Verweilziele besonders vorsichtig bewegen müssen.</span><span class="sxs-lookup"><span data-stu-id="67ea8-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="67ea8-186">**Empfehlungen**</span><span class="sxs-lookup"><span data-stu-id="67ea8-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="67ea8-187">Lassen Sie die ganze Zeile hervorheben, wenn Sie in den Kopf-und Ausgangspunkt steht</span><span class="sxs-lookup"><span data-stu-id="67ea8-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="67ea8-188">Zeigt nur das Ziel an, wenn die Zeile hervorgehoben wird, um das visuelle Rauschen zu verringern.</span><span class="sxs-lookup"><span data-stu-id="67ea8-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="67ea8-189">Sie sollten klar und konsistent mit der Position von "Dwell Targets" sein.</span><span class="sxs-lookup"><span data-stu-id="67ea8-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="67ea8-190">Zeigen Sie nicht alle Ziele auf einmal an, um sich wiederholende Benutzeroberflächen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="67ea8-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="67ea8-191">Verwenden Sie das gleiche Muster so oft wie möglich, um die Benutzerfreundlichkeit der UX zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="67ea8-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="67ea8-192">*Abbildung: Liste der Microsoft Dynamics 365-Leitfäden*</span><span class="sxs-lookup"><span data-stu-id="67ea8-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Liste der Microsoft Dynamics 365-Leitfäden](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="67ea8-194">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="67ea8-194">See also</span></span>
* [<span data-ttu-id="67ea8-195">Blick und Commit</span><span class="sxs-lookup"><span data-stu-id="67ea8-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="67ea8-196">Bearbeitung von Hand direkt</span><span class="sxs-lookup"><span data-stu-id="67ea8-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="67ea8-197">Handgesten</span><span class="sxs-lookup"><span data-stu-id="67ea8-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="67ea8-198">"Hand Punkt" und "Commit"</span><span class="sxs-lookup"><span data-stu-id="67ea8-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="67ea8-199">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="67ea8-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="67ea8-200">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="67ea8-200">Voice input</span></span>](voice-input.md)
