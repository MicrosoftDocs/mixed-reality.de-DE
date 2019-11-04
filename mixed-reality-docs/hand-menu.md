---
title: Hand Menü
description: Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren. Dies sind unsere bewährten Methoden und Empfehlungen für Hand-Menüs.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, schnell Zugriff, Layout
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439251"
---
# <a name="hand-menu"></a><span data-ttu-id="ec614-105">Hand Menü</span><span class="sxs-lookup"><span data-stu-id="ec614-105">Hand menu</span></span>

![Ulnar Seitenposition](images/MRTK_UX_HandMenu.png)

<span data-ttu-id="ec614-107">Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ec614-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="ec614-108">Im folgenden finden Sie die bewährten Methoden, die wir für Hand Menüs gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="ec614-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="ec614-109">Sie finden auch eine Beispiel Szene, die das Hand Menü in [mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)demonstriert.</span><span class="sxs-lookup"><span data-stu-id="ec614-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="ec614-110">Bewährte Methoden für das Verhalten</span><span class="sxs-lookup"><span data-stu-id="ec614-110">Behavior best practices</span></span>
<span data-ttu-id="ec614-111">**A. behalten Sie die Anzahl der Schaltflächen gering:** aufgrund der engen Entfernung zwischen einem Hand gesperrten Menü und den Augen und der Tendenz des Benutzers, sich jederzeit auf einen relativ kleinen visuellen Bereich zu konzentrieren (der Teilnehmer Kegel ist ungefähr 10 Grad), wir empfehlen Ihnen Folgendes: halten Sie die Anzahl der Schaltflächen klein.</span><span class="sxs-lookup"><span data-stu-id="ec614-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="ec614-112">Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem der gesamte Inhalt in der Ansicht (FOV) beibehalten wird, auch wenn Benutzer ihre Hände in den Mittelpunkt des FOV verschieben.</span><span class="sxs-lookup"><span data-stu-id="ec614-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="ec614-113">**B. verwenden Sie das Hand Menü für die schnelle Aktion:** das Auslösen eines Arm und das Aufrechterhalten der Position kann die Arm-Müdigkeit leicht auslösen.</span><span class="sxs-lookup"><span data-stu-id="ec614-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="ec614-114">Verwenden Sie eine Hand gesperrte Methode für das Menü, das eine kurze Interaktion erfordert.</span><span class="sxs-lookup"><span data-stu-id="ec614-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="ec614-115">Wenn Ihr Menü Komplex ist und erweiterte Interaktions Zeiten erfordert, sollten Sie stattdessen "World-Locked" oder "Body-Lock" verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec614-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="ec614-116">**C. Schaltflächen-/Panel-Winkel:** Menüs sollten auf die entgegengesetzte Schulter und die Mitte des Kopfes hin-/ausblenden: Dadurch kann eine natürliche Handbewegung mit dem Menü mit umgekehrter Hand interagieren und alle umständlichen oder unbequemen Handpositionen beim berühren vermeiden. Parab.</span><span class="sxs-lookup"><span data-stu-id="ec614-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="ec614-117">**D. in Erwägung gezogen, dass ein-oder Freihand-Vorgang unterstützt** wird. gehen Sie nicht davon aus, dass die beiden Hände des Benutzers stets verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ec614-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="ec614-118">Stellen Sie sich einen großen Bereich von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihre Entwurfs Konten für diese Situationen sind.</span><span class="sxs-lookup"><span data-stu-id="ec614-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="ec614-119">Um ein eindimensionales Menü zu unterstützen, können Sie versuchen, die Menü Platzierung von Hand gesperrt auf die gesperrte Seite zu übertragen, wenn die Hand kippt (in den Blättern).</span><span class="sxs-lookup"><span data-stu-id="ec614-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="ec614-120">Bei praktischen Szenarien sollten Sie die Verwendung eines sprach Befehls zum Aufrufen der Menü Schaltflächen "Hand" in Erwägung gezogen haben.</span><span class="sxs-lookup"><span data-stu-id="ec614-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="ec614-121">**E. zweistufige Aufrufe:** Wenn Sie nur die Option "Palm-up" als Ereignis verwenden, um das Hand Menü zu aktivieren, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv) und unbeabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="ec614-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="ec614-122">Wenn Sie in Ihrer APP falsch positive Ergebnisse haben, können Sie zusätzlich zum Palm-up-Ereignis einen weiteren Schritt hinzufügen, um das Hand Menü aufzurufen, z. b. voll geöffnete Finger.</span><span class="sxs-lookup"><span data-stu-id="ec614-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="ec614-123">**F. vermeiden Sie das Hinzufügen von Schaltflächen in der Nähe des Handgelenks (System Starttaste):** wenn die Menü Schaltflächen "Hand" zu nah an der Start Schaltfläche platziert werden, wird Sie möglicherweise versehentlich bei der Interaktion mit dem</span><span class="sxs-lookup"><span data-stu-id="ec614-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="ec614-124">**G. testen, testen, testen:** Personen verfügen über unterschiedliche Texte mit unterschiedlichen Schwellenwerten für Komfort und Unbehagen usw. Stellen Sie sicher, dass Sie Ihr Design testen und Feedback von vielen verschiedenen Personen erhalten.</span><span class="sxs-lookup"><span data-stu-id="ec614-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="ec614-125">Bewährte Methoden für die Platzierung von Hand Menüs</span><span class="sxs-lookup"><span data-stu-id="ec614-125">Hand menu placement best practices</span></span>

<span data-ttu-id="ec614-126">Bei der menschlichen Anatomie ist der ulnar-Nerv ein Nerv, der in der Nähe des Ulna-knochenverläuft.</span><span class="sxs-lookup"><span data-stu-id="ec614-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="ec614-127">Die Ulna ist ein langer Ring in der forearm, der vom Bogen zum kleinsten Finger reicht.</span><span class="sxs-lookup"><span data-stu-id="ec614-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="ec614-128">Im folgenden finden Sie zwei empfohlene Platzierungen, die auf unseren Explorationen basieren:</span><span class="sxs-lookup"><span data-stu-id="ec614-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="ec614-129">![ulnar Seitenposition](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="ec614-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="ec614-130">**Ein. ulnar in der Palme**</span><span class="sxs-lookup"><span data-stu-id="ec614-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="ec614-131">Diese Position ist zuverlässig, da die Hände einander nicht überlappen.</span><span class="sxs-lookup"><span data-stu-id="ec614-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="ec614-132">Dies ist wichtig für die genaue Erkennung und Nachverfolgung von Hand.</span><span class="sxs-lookup"><span data-stu-id="ec614-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ec614-133">![ulnar Seitenposition](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="ec614-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="ec614-134">**B. ulnar oberhalb der Hand**</span><span class="sxs-lookup"><span data-stu-id="ec614-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="ec614-135">Dieser Speicherort ist für Benutzer praktisch, da Sie den Arm nicht zu groß machen müssen, um mit dem Hand Menü zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="ec614-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="ec614-136">Es empfiehlt sich, die Menüs **13 cm** oberhalb der Palme zu platzieren und die Schaltflächen innerhalb der ulnar-Palme auszurichten.</span><span class="sxs-lookup"><span data-stu-id="ec614-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="ec614-137">Weitere Informationen zur optimalen Schaltflächen Größe</span><span class="sxs-lookup"><span data-stu-id="ec614-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="ec614-138">Aus technischen Gründen wird dieser Speicherort mit einer erforderlichen Implementierung empfohlen: der Entwickler muss das Menü fixieren, wenn die gegenüberliegende Seite des Benutzers in der Nähe der Interaktion mit dem Benutzer steht.</span><span class="sxs-lookup"><span data-stu-id="ec614-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="ec614-139">Dadurch wird die überlappende Hände von jitterität vermieden, und es ist auch möglich, dass die Schaltflächen schneller ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="ec614-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="ec614-140">Hololens 2 Kameras identifizieren Hände genau, wenn Sie voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="ec614-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="ec614-141">Überlappende Hände können dazu führen, dass Hand Menüs von der Ankerposition Weg wechseln.</span><span class="sxs-lookup"><span data-stu-id="ec614-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="ec614-142">Nicht empfohlene Menü Positionen</span><span class="sxs-lookup"><span data-stu-id="ec614-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="ec614-143">Wir haben die Benutzer Forschung mit verschiedenen Menüs und Standorten durchgeführt. die folgenden Menü Positionen werden **nicht empfohlen**. Sie finden die Nachteile der einzelnen nachfolgenden Nachforschungen:</span><span class="sxs-lookup"><span data-stu-id="ec614-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="ec614-144">![oberhalb der Arm-](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="ec614-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="ec614-145">**Oberhalb der Arm**</span><span class="sxs-lookup"><span data-stu-id="ec614-145">**Above the arm**</span></span><br>
        <span data-ttu-id="ec614-146">1: schwer zu verwaltender guter Hand Verfolgung</span><span class="sxs-lookup"><span data-stu-id="ec614-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="ec614-147">2: verursacht eine Benutzer Müdigkeit aufgrund der unnatürlichen Position.</span><span class="sxs-lookup"><span data-stu-id="ec614-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ec614-148">![über Fingern](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="ec614-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="ec614-149">**Über Fingern**</span><span class="sxs-lookup"><span data-stu-id="ec614-149">**Above fingers**</span></span><br>
        <span data-ttu-id="ec614-150">1-Hand-Müdigkeit aufgrund von Handlanger Zeit</span><span class="sxs-lookup"><span data-stu-id="ec614-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="ec614-151">2-Hand-nach Verfolgungs Probleme bei Index und mittlerem Finger</span><span class="sxs-lookup"><span data-stu-id="ec614-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="ec614-152">![oberhalb der Center-Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="ec614-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="ec614-153">**Oberhalb-Mittelpunkt**</span><span class="sxs-lookup"><span data-stu-id="ec614-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="ec614-154">1-Hand-nach Verfolgungs Probleme aufgrund von überlappenden Händen</span><span class="sxs-lookup"><span data-stu-id="ec614-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="ec614-155">zwei Hand Müdigkeit aufgrund der langen Zeit für die Interaktion mit Menüs</span><span class="sxs-lookup"><span data-stu-id="ec614-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ec614-156">![Top Fingertip](images/TopFingerTip.gif) **Top Fingertip**</span><span class="sxs-lookup"><span data-stu-id="ec614-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="ec614-157">1-Hand-nach Verfolgungs Probleme</span><span class="sxs-lookup"><span data-stu-id="ec614-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="ec614-158">zwei Hand Müdigkeit mit Hand über normalem Status</span><span class="sxs-lookup"><span data-stu-id="ec614-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="ec614-159">3: Fehler beim Drücken von Schaltflächen mit anderen Fingern aufgrund von eingeschränktem Leerraum zwischen Fingern.</span><span class="sxs-lookup"><span data-stu-id="ec614-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="ec614-160">![Rückseite der Arm-](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="ec614-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="ec614-161">**Zurück zum Arm**</span><span class="sxs-lookup"><span data-stu-id="ec614-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="ec614-162">1: Start Schaltfläche nach einem Unfall</span><span class="sxs-lookup"><span data-stu-id="ec614-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="ec614-163">2-keine natürliche oder bequeme Position für Benutzer</span><span class="sxs-lookup"><span data-stu-id="ec614-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a><span data-ttu-id="ec614-164">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="ec614-164">See also</span></span>

* [<span data-ttu-id="ec614-165">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="ec614-165">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ec614-166">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="ec614-166">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ec614-167">Hände und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="ec614-167">Hands and motion controllers</span></span>](hands-and-tools.md)
