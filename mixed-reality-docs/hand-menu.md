---
title: Handmenü
description: Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren. Dies sind unsere bewährten Methoden und Empfehlungen für Hand-Menüs.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, schnell Zugriff, Layout
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061167"
---
# <a name="hand-menu"></a><span data-ttu-id="86d64-105">Handmenü</span><span class="sxs-lookup"><span data-stu-id="86d64-105">Hand menu</span></span>

![Ulnar Seitenposition](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="86d64-107">Das Menü "Hand" ist eines der einzig testen UX-Muster in hololens 2.</span><span class="sxs-lookup"><span data-stu-id="86d64-107">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="86d64-108">Mit dieser Option können Sie schnell Hand anfügende Benutzeroberflächen einrichten.</span><span class="sxs-lookup"><span data-stu-id="86d64-108">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="86d64-109">Da es jederzeit zugänglich ist und leicht angezeigt und ausgeblendet werden kann, ist es hervorragend für schnelle Aktionen geeignet.</span><span class="sxs-lookup"><span data-stu-id="86d64-109">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="86d64-110">Sie finden unsere empfohlenen bewährten Methoden für die Arbeit mit Hand Menüs in der folgenden Liste.</span><span class="sxs-lookup"><span data-stu-id="86d64-110">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="86d64-111">Sie finden auch eine Beispiel Szene, die das Hand Menü in [mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)demonstriert.</span><span class="sxs-lookup"><span data-stu-id="86d64-111">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>


---

## <a name="best-practices"></a><span data-ttu-id="86d64-112">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="86d64-112">Best practices</span></span>
<span data-ttu-id="86d64-113">**Anzahl von Schaltflächen klein halten**</span><span class="sxs-lookup"><span data-stu-id="86d64-113">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="86d64-114">Aufgrund der engen Entfernung zwischen einem Hand gesperrten Menü und den Augen und der Tendenz des Benutzers, sich jederzeit auf einen relativ kleinen visuellen Bereich zu konzentrieren (der Teilnehmer Kegel ist ungefähr 10 Grad), empfiehlt es sich, die Anzahl der Schaltflächen gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="86d64-114">Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="86d64-115">Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem der gesamte Inhalt in der Ansicht (FOV) beibehalten wird, auch wenn ein Benutzer seine Hände in den Mittelpunkt des FOV verschiebt.</span><span class="sxs-lookup"><span data-stu-id="86d64-115">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="86d64-116">**Verwenden des Hand Menüs für die schnelle Aktion**</span><span class="sxs-lookup"><span data-stu-id="86d64-116">**Utilize hand menu for quick action**</span></span> 

<span data-ttu-id="86d64-117">Das Auslösen eines Arm und das Aufrechterhalten der Position könnte leicht eine Arm-Müdigkeit verursachen.</span><span class="sxs-lookup"><span data-stu-id="86d64-117">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="86d64-118">Verwenden Sie eine Hand gesperrte Methode für das Menü, das eine kurze Interaktion erfordert.</span><span class="sxs-lookup"><span data-stu-id="86d64-118">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="86d64-119">Wenn Ihr Menü Komplex ist und erweiterte Interaktions Zeiten erfordert, sollten Sie stattdessen "World-Locked" oder "Body-Lock" verwenden.</span><span class="sxs-lookup"><span data-stu-id="86d64-119">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="86d64-120">**Schaltflächen-/Panel-Winkel**</span><span class="sxs-lookup"><span data-stu-id="86d64-120">**Button / Panel angle**</span></span>

<span data-ttu-id="86d64-121">Menüs sollten in der gegenüberliegenden Schulter und der Mitte des Kopfes angezeigt werden: Dadurch kann eine natürliche Handbewegung mit dem Menü mit umgekehrter Hand interagieren und alle umständlichen oder unbequemen Handpositionen beim Berühren von Schaltflächen vermeiden.</span><span class="sxs-lookup"><span data-stu-id="86d64-121">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="86d64-122">**In Erwägung gezogen, ein-oder frei Hand Vorgang zu unterstützen.**</span><span class="sxs-lookup"><span data-stu-id="86d64-122">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="86d64-123">Gehen Sie nicht davon aus, dass beide Hände des Benutzers stets verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="86d64-123">Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="86d64-124">Stellen Sie sich einen großen Bereich von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihre Entwurfs Konten für diese Situationen sind.</span><span class="sxs-lookup"><span data-stu-id="86d64-124">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="86d64-125">Um ein eindimensionales Menü zu unterstützen, können Sie versuchen, die Menü Platzierung von Hand gesperrt auf die gesperrte Seite zu übertragen, wenn die Hand kippt (in den Blättern).</span><span class="sxs-lookup"><span data-stu-id="86d64-125">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="86d64-126">Bei praktischen Szenarios sollten Sie einen Sprachbefehl verwenden, um das Menü "Hand" aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="86d64-126">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="86d64-127">**Vermeiden Sie das Hinzufügen von Schaltflächen in der Nähe der Hand**</span><span class="sxs-lookup"><span data-stu-id="86d64-127">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="86d64-128">Wenn die Menü Schaltflächen "Hand" zu nah an der Start Schaltfläche platziert werden, kann Sie versehentlich bei der Interaktion mit dem Menü "Hand" auftreten.</span><span class="sxs-lookup"><span data-stu-id="86d64-128">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="86d64-129">Hand Menü mit großen und komplexen UI-Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="86d64-129">Hand menu with large and complex UI controls</span></span>
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="86d64-130">Es wird empfohlen, die Anzahl der Schaltflächen oder UI-Steuerelemente in Hand anfügenden Menüs einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="86d64-130">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="86d64-131">Dies liegt daran, dass die erweiterte Interaktion mit einer großen Anzahl von Benutzeroberflächen Elementen eine Arm-Müdigkeit verursachen kann.</span><span class="sxs-lookup"><span data-stu-id="86d64-131">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="86d64-132">Wenn Ihre Benutzerumgebung ein großes Menü erfordert, stellen Sie dem Benutzer eine einfache Möglichkeit zur Verfügung, um das Menü zu sperren.</span><span class="sxs-lookup"><span data-stu-id="86d64-132">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="86d64-133">Eine Methode, die wir empfehlen, ist die Welt, in der das Menü angezeigt wird, wenn das Handumdrehen vom Benutzer gelöscht oder umgekehrt wird.</span><span class="sxs-lookup"><span data-stu-id="86d64-133">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="86d64-134">Ein zweites Verfahren besteht darin, dem Benutzer zu gestatten, das Menü direkt mit der anderen Seite zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="86d64-134">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="86d64-135">Wenn der Benutzer das Menü loslässt, sollte das Menü auf der ganzen Welt gesperrt werden.</span><span class="sxs-lookup"><span data-stu-id="86d64-135">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="86d64-136">Auf diese Weise kann ein Benutzer über einen längeren Zeitraum bequem und sicher mit verschiedenen Benutzeroberflächen Elementen interagieren.</span><span class="sxs-lookup"><span data-stu-id="86d64-136">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="86d64-137">Wenn das Menü weltweit gesperrt ist, stellen Sie sicher, dass Sie eine Möglichkeit zum Verschieben des Menüs und zum Schließen des Menüs haben, wenn es nicht mehr benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="86d64-137">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="86d64-138">Legen Sie die Position des Menüs durch Bereitstellen von Handles auf den Seiten oder dem oberen Rand des Menüs auf den</span><span class="sxs-lookup"><span data-stu-id="86d64-138">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="86d64-139">Fügen Sie eine Schaltfläche Schließen hinzu, um das Schließen des Menüs zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="86d64-139">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="86d64-140">Hiermit wird zugelassen, dass das Menü erneut an die Hand angefügt wird, wenn der Benutzer die Hand hat.</span><span class="sxs-lookup"><span data-stu-id="86d64-140">Allow for the menu to re-attach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="86d64-141">Außerdem wird empfohlen, dass die Benutzer die Benutzer überprüfen, um falsche Aktivierungen zu verhindern (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="86d64-141">We also recommend requiring that the users gazes at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="86d64-142">**Großes Menü, das ein Problem mit der Benutzerfreundlichkeit anzeigt**</span><span class="sxs-lookup"><span data-stu-id="86d64-142">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="86d64-143">**Weltweit gesperrtes Menü im Handschlag**</span><span class="sxs-lookup"><span data-stu-id="86d64-143">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="86d64-144">**Manueller Abruf & Pullvorgang an der Welt: Sperren Sie das Menü.**</span><span class="sxs-lookup"><span data-stu-id="86d64-144">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="86d64-145">Verhindern der falsch Aktivierung</span><span class="sxs-lookup"><span data-stu-id="86d64-145">How to prevent false activation</span></span>

<span data-ttu-id="86d64-146">Wenn Sie nur die Option "Palm-up" als Ereignis verwenden, um das Menü "Hand" zu starten, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv), da Personen die Hände absichtlich (für die Kommunikation und Objekt Bearbeitung) und unbeabsichtigt verschieben.</span><span class="sxs-lookup"><span data-stu-id="86d64-146">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="86d64-147">Um falsche Aktivierungen zu reduzieren, fügen Sie neben dem Palm-up-Ereignis einen zusätzlichen Schritt hinzu, um das Menü "Hand" (z. b. vollständig geöffnete Finger) aufzurufen</span><span class="sxs-lookup"><span data-stu-id="86d64-147">To reduce false activations, add an additional step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="86d64-148">**Flache Palme erforderlich**</span><span class="sxs-lookup"><span data-stu-id="86d64-148">**Require Flat Palm**</span></span>

<span data-ttu-id="86d64-149">Wenn Sie eine flache öffnende Hand benötigen, können Sie die falsche Aktivierung verhindern, die auftreten kann, wenn der Benutzer während der Kommunikation innerhalb einer Umgebung Objekte oder Gesten bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="86d64-149">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="86d64-150">**Blick erfordern**</span><span class="sxs-lookup"><span data-stu-id="86d64-150">**Require Gaze**</span></span>

<span data-ttu-id="86d64-151">Durch den Benutzer, der die Hand hat (entweder mit dem Augenblick oder dem Kopf), werden falsche Aktivierungen verhindert, da der Benutzer absichtlich seine Aufmerksamkeit als sekundären Aktivierungs Schritt (mit einem anpassbaren Entfernungs Schwellenwert, der für die Benutzerfreundlichkeit verwendet wird) an die Hand weiterleiten muss.</span><span class="sxs-lookup"><span data-stu-id="86d64-151">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations due to the user having to intentionally direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="86d64-152">Bewährte Methoden für die Platzierung von Hand Menüs</span><span class="sxs-lookup"><span data-stu-id="86d64-152">Hand menu placement best practices</span></span>

<span data-ttu-id="86d64-153">Bei der menschlichen Anatomie ist der ulnar-Nerv ein Nerv, der in der Nähe des Ulna-knochenverläuft.</span><span class="sxs-lookup"><span data-stu-id="86d64-153">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="86d64-154">Die Ulna ist ein langer Ring in der forearm, der vom Bogen zum kleinsten Finger reicht.</span><span class="sxs-lookup"><span data-stu-id="86d64-154">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="86d64-155">Im folgenden finden Sie zwei empfohlene Platzierungen, die auf unseren Explorationen basieren:</span><span class="sxs-lookup"><span data-stu-id="86d64-155">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="86d64-156">![Ulnar Seitenposition](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="86d64-156">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="86d64-157">**Ein. ulnar in der Palme**</span><span class="sxs-lookup"><span data-stu-id="86d64-157">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="86d64-158">Diese Position ist zuverlässig, da die Hände einander nicht überlappen.</span><span class="sxs-lookup"><span data-stu-id="86d64-158">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="86d64-159">Dies ist wichtig für die genaue Erkennung und Nachverfolgung von Hand.</span><span class="sxs-lookup"><span data-stu-id="86d64-159">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="86d64-160">![Ulnar Seitenposition](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="86d64-160">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="86d64-161">**B. ulnar oberhalb der Hand**</span><span class="sxs-lookup"><span data-stu-id="86d64-161">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="86d64-162">Dieser Speicherort ist für Benutzer praktisch, da Sie den Arm nicht zu groß machen müssen, um mit dem Hand Menü zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="86d64-162">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="86d64-163">Es empfiehlt sich, die Menüs **13 cm** oberhalb der Palme zu platzieren und die Schaltflächen innerhalb der ulnar-Palme auszurichten.</span><span class="sxs-lookup"><span data-stu-id="86d64-163">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="86d64-164">Weitere Informationen zur optimalen Schaltflächen Größe</span><span class="sxs-lookup"><span data-stu-id="86d64-164">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="86d64-165">Aus technischen Gründen wird dieser Speicherort mit einer erforderlichen Implementierung empfohlen: der Entwickler muss das Menü fixieren, wenn die gegenüberliegende Seite des Benutzers in der Nähe der Interaktion mit dem Benutzer steht.</span><span class="sxs-lookup"><span data-stu-id="86d64-165">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="86d64-166">Dadurch wird die überlappende Hände von jitterität vermieden, und es ist auch möglich, dass die Schaltflächen schneller ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="86d64-166">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="86d64-167">Hololens 2 Kameras identifizieren Hände genau, wenn Sie voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="86d64-167">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="86d64-168">Überlappende Hände können dazu führen, dass Hand Menüs von der Ankerposition Weg wechseln.</span><span class="sxs-lookup"><span data-stu-id="86d64-168">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="86d64-169">Nicht empfohlene Menü Positionen</span><span class="sxs-lookup"><span data-stu-id="86d64-169">Menu positions that are not recommended</span></span>
<span data-ttu-id="86d64-170">Wir haben die Benutzer Forschung mit verschiedenen Menüs und Standorten durchgeführt. die folgenden Menü Positionen werden **nicht empfohlen**. Sie finden die Nachteile der einzelnen nachfolgenden Nachforschungen:</span><span class="sxs-lookup"><span data-stu-id="86d64-170">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="86d64-171">![Oberhalb von Arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="86d64-171">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="86d64-172">**Oberhalb der Arm**</span><span class="sxs-lookup"><span data-stu-id="86d64-172">**Above the arm**</span></span><br>
        <span data-ttu-id="86d64-173">1: schwer zu verwaltender guter Hand Verfolgung</span><span class="sxs-lookup"><span data-stu-id="86d64-173">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="86d64-174">2: verursacht eine Benutzer Müdigkeit aufgrund der unnatürlichen Position.</span><span class="sxs-lookup"><span data-stu-id="86d64-174">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="86d64-175">![Über Fingern](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="86d64-175">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="86d64-176">**Über Fingern**</span><span class="sxs-lookup"><span data-stu-id="86d64-176">**Above fingers**</span></span><br>
        <span data-ttu-id="86d64-177">eine Hand Müdigkeit aufgrund einer langen Zeitüberschreitung</span><span class="sxs-lookup"><span data-stu-id="86d64-177">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="86d64-178">2-Hand-nach Verfolgungs Probleme bei Index-und mittelfingern</span><span class="sxs-lookup"><span data-stu-id="86d64-178">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="86d64-179">![Oberhalb der mittleren Palme](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="86d64-179">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="86d64-180">**Oberhalb-Mittelpunkt**</span><span class="sxs-lookup"><span data-stu-id="86d64-180">**Above-center palm**</span></span><br>
        <span data-ttu-id="86d64-181">1-Hand-nach Verfolgungs Probleme aufgrund von überlappenden Händen</span><span class="sxs-lookup"><span data-stu-id="86d64-181">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="86d64-182">zwei Hand Müdigkeit aufgrund der langen Zeit für die Interaktion mit Menüs</span><span class="sxs-lookup"><span data-stu-id="86d64-182">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="86d64-183">![Top Fingertip ](images/TopFingerTip.gif) **Top Fingertip**</span><span class="sxs-lookup"><span data-stu-id="86d64-183">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="86d64-184">1-Hand-nach Verfolgungs Probleme</span><span class="sxs-lookup"><span data-stu-id="86d64-184">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="86d64-185">2-Hand Müdigkeit von Hand über normalem Status</span><span class="sxs-lookup"><span data-stu-id="86d64-185">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="86d64-186">3: Fehler beim Drücken von Schaltflächen mit anderen Fingern aufgrund von eingeschränktem Leerraum zwischen Fingern.</span><span class="sxs-lookup"><span data-stu-id="86d64-186">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="86d64-187">![Zurück zum Arm](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="86d64-187">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="86d64-188">**Zurück zum Arm**</span><span class="sxs-lookup"><span data-stu-id="86d64-188">**Back of the arm**</span></span><br>
        <span data-ttu-id="86d64-189">1: Start Schaltfläche nach einem Unfall</span><span class="sxs-lookup"><span data-stu-id="86d64-189">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="86d64-190">2-keine natürliche oder bequeme Position</span><span class="sxs-lookup"><span data-stu-id="86d64-190">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="86d64-191">Hand Menü im mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="86d64-191">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="86d64-192">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Beispiel Szenen für das Hand Menü bereit.</span><span class="sxs-lookup"><span data-stu-id="86d64-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="86d64-193">Das handeinschränintpalmup-Solver-Skript ermöglicht es Ihnen, alle Objekte mit verschiedenen konfigurierbaren Optionen an die Hände anzufügen.</span><span class="sxs-lookup"><span data-stu-id="86d64-193">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="86d64-194">Die Hand Menü Beispiele von mrtk enthalten nützliche Optionen, wie z. b. eine flache Palme und eine Blick Anforderung zum Verhindern der falschen Aktivierung.</span><span class="sxs-lookup"><span data-stu-id="86d64-194">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="86d64-195">Hand Menü-Documentationen</span><span class="sxs-lookup"><span data-stu-id="86d64-195">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="86d64-196">Beispiel Szene für Hand Menü</span><span class="sxs-lookup"><span data-stu-id="86d64-196">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="86d64-197">Sie können die Menü Beispiele in hololens 2 mit der mrtk examples Hub-App ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="86d64-197">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="86d64-198">Hand Menü Szene im mrtk-Beispiel-Hub</span><span class="sxs-lookup"><span data-stu-id="86d64-198">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a><span data-ttu-id="86d64-199">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="86d64-199">See also</span></span>

* [<span data-ttu-id="86d64-200">Cursor</span><span class="sxs-lookup"><span data-stu-id="86d64-200">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="86d64-201">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="86d64-201">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="86d64-202">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="86d64-202">Button</span></span>](button.md)
* [<span data-ttu-id="86d64-203">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="86d64-203">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="86d64-204">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="86d64-204">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="86d64-205">Manipulation</span><span class="sxs-lookup"><span data-stu-id="86d64-205">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="86d64-206">Handmenü</span><span class="sxs-lookup"><span data-stu-id="86d64-206">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="86d64-207">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="86d64-207">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="86d64-208">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="86d64-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="86d64-209">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="86d64-209">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="86d64-210">Tastatur</span><span class="sxs-lookup"><span data-stu-id="86d64-210">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="86d64-211">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="86d64-211">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="86d64-212">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="86d64-212">Slate</span></span>](slate.md)
* [<span data-ttu-id="86d64-213">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="86d64-213">Slider</span></span>](slider.md)
* [<span data-ttu-id="86d64-214">Shader</span><span class="sxs-lookup"><span data-stu-id="86d64-214">Shader</span></span>](shader.md)
* [<span data-ttu-id="86d64-215">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="86d64-215">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="86d64-216">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="86d64-216">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="86d64-217">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="86d64-217">Surface magnetism</span></span>](surface-magnetism.md)
