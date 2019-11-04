---
title: System Geste
description: System Geste, um das Startmenü aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf
ms.openlocfilehash: b46f642babb18387da2e76d5bdbb7631577c85de
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439821"
---
# <a name="system-gesture"></a><span data-ttu-id="5da1f-104">System Geste</span><span class="sxs-lookup"><span data-stu-id="5da1f-104">System gesture</span></span>

<span data-ttu-id="5da1f-105">Die System Geste ist eine Handbewegung, mit der das Startmenü aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5da1f-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="5da1f-106">Dies entspricht dem Drücken der Windows-Taste auf der Tastatur, der Xbox-Schaltfläche auf einem Xbox-Controller oder der Windows-Taste auf dem immersiven Headset-Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="5da1f-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="5da1f-107">Es ist wichtig zu verstehen, welche Gesten für das System auf jedem gemischten Reality-Gerät reserviert sind, um Konflikte beim Entwerfen Ihrer Interaktionen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="5da1f-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="5da1f-108">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="5da1f-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5da1f-109"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="5da1f-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5da1f-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5da1f-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5da1f-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="5da1f-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="5da1f-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="5da1f-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5da1f-113">Blütezeit</span><span class="sxs-lookup"><span data-stu-id="5da1f-113">Bloom</span></span></td>
        <td><span data-ttu-id="5da1f-114">✔️</span><span class="sxs-lookup"><span data-stu-id="5da1f-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="5da1f-115">Handgelenk Taste</span><span class="sxs-lookup"><span data-stu-id="5da1f-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="5da1f-116">✔️</span><span class="sxs-lookup"><span data-stu-id="5da1f-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="5da1f-117">Eye-und Palmen Pfeil nach oben</span><span class="sxs-lookup"><span data-stu-id="5da1f-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="5da1f-118">✔️</span><span class="sxs-lookup"><span data-stu-id="5da1f-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="5da1f-119">Blütezeit</span><span class="sxs-lookup"><span data-stu-id="5da1f-119">Bloom</span></span>
<span data-ttu-id="5da1f-120">Um das Startmenü in hololens (1. Generation) aufzurufen, haben wir "Bloom" entworfen, das eine symbolische Geste zum imitieren der Blüten Blüte ist.</span><span class="sxs-lookup"><span data-stu-id="5da1f-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="5da1f-121">Es ist für die Interaktion mit untergeordneten Elementen, die einfache Durchführung und die schnelle Erinnerung.</span><span class="sxs-lookup"><span data-stu-id="5da1f-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="5da1f-122">Um die Blüte Bewegung auf hololens (1. Generation) durchzuführen, halten Sie Ihre Hand an Ihre Hand, um Sie zu öffnen, und öffnen Sie dann die Hand, indem Sie Ihre Finger verteilen.</span><span class="sxs-lookup"><span data-stu-id="5da1f-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5da1f-123">![](images/bloom-close.png) schließen.</span><span class="sxs-lookup"><span data-stu-id="5da1f-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="5da1f-124">**Schritt 1: überschreiten der Hand.**</span><span class="sxs-lookup"><span data-stu-id="5da1f-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5da1f-125">![Blüte geöffnet](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="5da1f-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="5da1f-126">**Schritt 2: mit der Hand**</span><span class="sxs-lookup"><span data-stu-id="5da1f-126">**Step 2: Palm up with fingertips spreaded**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="5da1f-127">Handgelenk Taste</span><span class="sxs-lookup"><span data-stu-id="5da1f-127">Wrist button</span></span>
<span data-ttu-id="5da1f-128">In hololens 2 haben wir die Blüte Bewegung durch eine virtuelle Handgelenk Schaltfläche ersetzt, die mehr instanzielle Interaktionen ermöglicht, die keine zusätzliche Lehre erfordern.</span><span class="sxs-lookup"><span data-stu-id="5da1f-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="5da1f-129">Wenn die Benutzer die Schaltfläche auf dem Handgelenk anzeigt, können Sie sie intuitiv erreichen und mit der anderen Seite drücken.</span><span class="sxs-lookup"><span data-stu-id="5da1f-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5da1f-130">![Hand Tasten](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="5da1f-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="5da1f-131">**Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**</span><span class="sxs-lookup"><span data-stu-id="5da1f-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5da1f-132">Drücken Sie ![Hand Tasten](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="5da1f-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="5da1f-133">**Schritt 2: Klicken Sie auf das Handgelenk.**</span><span class="sxs-lookup"><span data-stu-id="5da1f-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="5da1f-134">"Augenblick" und "Palme"-Pinsel</span><span class="sxs-lookup"><span data-stu-id="5da1f-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="5da1f-135">Wir haben auch eine eindimensionale Lösung für den einfachen Zugriff in hololens 2 entwickelt.</span><span class="sxs-lookup"><span data-stu-id="5da1f-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="5da1f-136">Diese Geste erfordert, dass Benutzer auf die Handgelenk Schaltfläche zeigen. verwenden Sie dann dieselbe Hand, um mit dem Ziehpunkt und dem Index Finger eine Aufzieh Schaltfläche auszuführen.</span><span class="sxs-lookup"><span data-stu-id="5da1f-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="5da1f-137">![Hand Tasten](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="5da1f-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="5da1f-138">**Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**</span><span class="sxs-lookup"><span data-stu-id="5da1f-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5da1f-139">![-Schaltflächen-Pinsel](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="5da1f-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="5da1f-140">**Schritt: Augenblick auf die Schaltfläche und dann auf die Schaltfläche**</span><span class="sxs-lookup"><span data-stu-id="5da1f-140">**Step: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="5da1f-141">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="5da1f-141">See also</span></span>

* [<span data-ttu-id="5da1f-142">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="5da1f-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="5da1f-143">Anvisieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="5da1f-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="5da1f-144">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="5da1f-144">Voice input</span></span>](voice-input.md)
