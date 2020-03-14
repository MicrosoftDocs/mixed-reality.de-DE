---
title: System Geste
description: System Geste, um das Startmenü aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf
ms.openlocfilehash: 9cfee1104cb9b8135dae51bea73850062fadd25c
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375907"
---
# <a name="system-gesture"></a><span data-ttu-id="6c8cd-104">System Geste</span><span class="sxs-lookup"><span data-stu-id="6c8cd-104">System gesture</span></span>

<span data-ttu-id="6c8cd-105">Die System Geste ist eine Handbewegung, mit der das Startmenü aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="6c8cd-106">Dies entspricht dem Drücken der Windows-Taste auf der Tastatur, der Xbox-Schaltfläche auf einem Xbox-Controller oder der Windows-Taste auf dem immersiven Headset-Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="6c8cd-107">Es ist wichtig zu verstehen, welche Gesten für das System auf jedem gemischten Reality-Gerät reserviert sind, um Konflikte beim Entwerfen Ihrer Interaktionen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="6c8cd-108">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="6c8cd-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6c8cd-109"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="6c8cd-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6c8cd-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c8cd-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6c8cd-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6c8cd-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6c8cd-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c8cd-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6c8cd-113">Blütezeit</span><span class="sxs-lookup"><span data-stu-id="6c8cd-113">Bloom</span></span></td>
        <td><span data-ttu-id="6c8cd-114">✔️</span><span class="sxs-lookup"><span data-stu-id="6c8cd-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="6c8cd-115">Handgelenk Taste</span><span class="sxs-lookup"><span data-stu-id="6c8cd-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6c8cd-116">✔️</span><span class="sxs-lookup"><span data-stu-id="6c8cd-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="6c8cd-117">Eye-und Palmen Pfeil nach oben</span><span class="sxs-lookup"><span data-stu-id="6c8cd-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6c8cd-118">✔️</span><span class="sxs-lookup"><span data-stu-id="6c8cd-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="6c8cd-119">Blütezeit</span><span class="sxs-lookup"><span data-stu-id="6c8cd-119">Bloom</span></span>
<span data-ttu-id="6c8cd-120">Um das Startmenü in hololens (1. Generation) aufzurufen, haben wir "Bloom" entworfen, das eine symbolische Geste zum imitieren der Blüten Blüte ist.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="6c8cd-121">Es ist für die Interaktion mit untergeordneten Elementen, die einfache Durchführung und die schnelle Erinnerung.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="6c8cd-122">Um die Blüte Bewegung auf hololens (1. Generation) durchzuführen, halten Sie Ihre Hand an Ihre Hand, um Sie zu öffnen, und öffnen Sie dann die Hand, indem Sie Ihre Finger verteilen.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6c8cd-123">![](images/bloom-close.png) schließen.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="6c8cd-124">**Schritt 1: überschreiten der Hand.**</span><span class="sxs-lookup"><span data-stu-id="6c8cd-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6c8cd-125">![Blüte geöffnet](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="6c8cd-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="6c8cd-126">**Schritt 2: überschreiten der handbreiten Verteilung**</span><span class="sxs-lookup"><span data-stu-id="6c8cd-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="6c8cd-127">Start Geste</span><span class="sxs-lookup"><span data-stu-id="6c8cd-127">Start gesture</span></span>
<span data-ttu-id="6c8cd-128">In hololens 2 haben wir die Blüte Bewegung durch eine virtuelle Handgelenk Schaltfläche ersetzt, die mehr instanzielle Interaktionen ermöglicht, die keine zusätzliche Lehre erfordern.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="6c8cd-129">Wenn die Benutzer die Schaltfläche auf dem Handgelenk anzeigt, können Sie sie intuitiv erreichen und mit der anderen Seite drücken.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6c8cd-130">![Hand Tasten](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="6c8cd-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="6c8cd-131">**Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**</span><span class="sxs-lookup"><span data-stu-id="6c8cd-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6c8cd-132">Drücken Sie ![Hand Tasten](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="6c8cd-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="6c8cd-133">**Schritt 2: Klicken Sie auf das Handgelenk.**</span><span class="sxs-lookup"><span data-stu-id="6c8cd-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="6c8cd-134">Einstufige Start Geste</span><span class="sxs-lookup"><span data-stu-id="6c8cd-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c8cd-135">Damit die einstufige Start Geste funktioniert:</span><span class="sxs-lookup"><span data-stu-id="6c8cd-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="6c8cd-136">Sie müssen ein Update auf das Update von November 2019 (Build 18363,1039) oder höher durch haben.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="6c8cd-137">Die Augen müssen auf dem Gerät so kalibriert werden, dass die Eye-Nachverfolgung ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="6c8cd-138">Wenn Sie keine Umkreis Punkte um das Start Symbol sehen, wenn Sie es betrachten, werden die Augen nicht auf dem Gerät gekalibriert.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="6c8cd-139">Sie können die Start Geste auch nur mit einer Hand ausführen.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="6c8cd-140">Halten Sie zu diesem Zweck ihre Hand mit Ihrer Hand, und sehen Sie sich das **Start Symbol** auf Ihrem inneren Handgelenk an.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="6c8cd-141">**Wenn Sie das Symbol gedrückt halten**, können Sie den Ziehpunkt und den Finger des Indexes zusammenhalten.</span><span class="sxs-lookup"><span data-stu-id="6c8cd-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="6c8cd-142">![Hand Tasten](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="6c8cd-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="6c8cd-143">**Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**</span><span class="sxs-lookup"><span data-stu-id="6c8cd-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6c8cd-144">![-Schaltflächen-Pinsel](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="6c8cd-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="6c8cd-145">**Schritt 2: Augenblick auf die Schaltfläche und dann auf die Schaltfläche**</span><span class="sxs-lookup"><span data-stu-id="6c8cd-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="6c8cd-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6c8cd-146">See also</span></span>

* [<span data-ttu-id="6c8cd-147">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="6c8cd-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6c8cd-148">Anvisieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="6c8cd-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="6c8cd-149">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="6c8cd-149">Voice input</span></span>](voice-input.md)
