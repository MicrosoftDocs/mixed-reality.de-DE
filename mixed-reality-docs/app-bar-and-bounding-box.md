---
title: Begrenzungs Bereich und App-Leiste
description: Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungs Bereich
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437053"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="901e1-104">Begrenzungs Bereich und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="901e1-104">Bounding box and App bar</span></span>
![Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="901e1-106">Was ist das umgebende Feld?</span><span class="sxs-lookup"><span data-stu-id="901e1-106">What is the Bounding box?</span></span>

<span data-ttu-id="901e1-107">Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="901e1-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="901e1-108">Der Benutzer erhält eine Kosten, die das Objekt momentan anpassbar ist.</span><span class="sxs-lookup"><span data-stu-id="901e1-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="901e1-109">Bei hololens 2 funktioniert das umgebende Feld mit direkter Hand Manipulation und antwortet auf die Nähe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="901e1-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="901e1-110">Es zeigt visuelles Feedback, um dem Benutzer zu helfen, den Abstand zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="901e1-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="901e1-111">Skalieren eines Objekts</span><span class="sxs-lookup"><span data-stu-id="901e1-111">Scaling an object</span></span><br>
        <span data-ttu-id="901e1-112">In den Ecken des umgebenden Felds wird dem Benutzer mitgeteilt, dass das Objekt skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="901e1-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="901e1-113">Die Handles folgen einem weit verbreiteten Muster zur Anpassung der Skalierung.</span><span class="sxs-lookup"><span data-stu-id="901e1-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="901e1-114">Diese visuelle Visualisierung zeigt Benutzern den gesamten Bereich des Objekts an – auch dann, wenn Sie außerhalb eines Anpassungsmodus nicht sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="901e1-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="901e1-115">Dies ist besonders wichtig, da das Objekt, das an ein anderes Objekt oder eine andere Oberfläche angedockt ist, sich so verhält, als ob es sich um ein Leerzeichen handelt, das nicht vorhanden sein sollte.</span><span class="sxs-lookup"><span data-stu-id="901e1-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="901e1-116">*Video Schleife: Skalieren eines Objekts per Begrenzungs Rahmen*</span><span class="sxs-lookup"><span data-stu-id="901e1-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="901e1-117">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="901e1-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="901e1-118">![hololens zeigt das Skalieren eines Objekts über das Begrenzungsfeld an](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="901e1-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="901e1-119">Drehen eines Objekts</span><span class="sxs-lookup"><span data-stu-id="901e1-119">Rotating an object</span></span><br>
        <span data-ttu-id="901e1-120">Die vertikalen rechteckigen Anlagen an den Rändern des umgebenden Felds sind Rotations Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="901e1-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="901e1-121">Dies ermöglicht dem Benutzer eine präzisere Anpassung der platzierten holograms.</span><span class="sxs-lookup"><span data-stu-id="901e1-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="901e1-122">Sie können nicht nur angepasst und skaliert werden, sondern auch jetzt drehen.</span><span class="sxs-lookup"><span data-stu-id="901e1-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="901e1-123">*Video Schleife: Drehen eines Objekts über das umgebende Feld*</span><span class="sxs-lookup"><span data-stu-id="901e1-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="901e1-124">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="901e1-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="901e1-125">![hololens-Sicht, die das Drehen eines Objekts über das umgebende Feld](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="901e1-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="901e1-126">Visuelles Feedback in der Nähe von hololens 2</span><span class="sxs-lookup"><span data-stu-id="901e1-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="901e1-127">Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützt.</span><span class="sxs-lookup"><span data-stu-id="901e1-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="901e1-128">Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst.</span><span class="sxs-lookup"><span data-stu-id="901e1-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="901e1-129">Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="901e1-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="901e1-130">Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.</span><span class="sxs-lookup"><span data-stu-id="901e1-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="901e1-131">*Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*</span><span class="sxs-lookup"><span data-stu-id="901e1-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="901e1-132">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="901e1-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="901e1-133">![Sie visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="901e1-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="901e1-134">**Informationen zur Entwicklung von Unity-apps finden Sie im Abschnitt zum umgebenden [Feld im Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="901e1-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="901e1-135">Was ist die APP-Leiste?</span><span class="sxs-lookup"><span data-stu-id="901e1-135">What is the App bar?</span></span>

<span data-ttu-id="901e1-136">Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="901e1-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="901e1-137">Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von holograms zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="901e1-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="901e1-138">Die APP-Leiste wurde primär als eine Möglichkeit zum Verwalten von platzierten Objekten in der Umgebung eines Benutzers entwickelt.</span><span class="sxs-lookup"><span data-stu-id="901e1-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="901e1-139">In Verbindung mit dem umgebenden Feld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in gemischter Realität ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="901e1-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="901e1-140">Die APP-Leiste folgt dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="901e1-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="901e1-141">Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die APP-Leiste immer auf der Seite der Objekte angezeigt, die dem Benutzer am nächsten ist, wenn sich der Benutzer um das Objekt bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="901e1-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="901e1-142">Obwohl dies kein Abgleich ist, erzielt es effektiv dasselbe Ergebnis. verhindern, dass die Position eines Benutzers Funktionen sperrt oder blockiert, die andernfalls an einem anderen Speicherort in Ihrer Umgebung verfügbar wären.</span><span class="sxs-lookup"><span data-stu-id="901e1-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="901e1-143">*Video Schleife: Durchlaufen eines Hologram, der APP-Leiste folgt*</span><span class="sxs-lookup"><span data-stu-id="901e1-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="901e1-144">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="901e1-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="901e1-145">![durchlaufen eines holograms.</span><span class="sxs-lookup"><span data-stu-id="901e1-145">![Walking around a hologram.</span></span> <span data-ttu-id="901e1-146">Die APP-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="901e1-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>



<span data-ttu-id="901e1-147">**Informationen zur Entwicklung von Unity-apps finden Sie [in der APP-Leiste im Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span><span class="sxs-lookup"><span data-stu-id="901e1-147">**For Unity app development, see [App bar in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="901e1-148">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="901e1-148">See also</span></span>
* [<span data-ttu-id="901e1-149">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="901e1-149">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="901e1-150">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="901e1-150">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="901e1-151">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="901e1-151">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="901e1-152">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="901e1-152">Displaying progress</span></span>](progress.md)
