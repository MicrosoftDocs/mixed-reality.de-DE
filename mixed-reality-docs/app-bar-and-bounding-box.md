---
title: Begrenzungs Bereich und App-Leiste
description: Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungs Bereich
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829685"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="23768-104">Begrenzungs Bereich und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="23768-104">Bounding box and App bar</span></span>
![Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="23768-106">Was ist das umgebende Feld?</span><span class="sxs-lookup"><span data-stu-id="23768-106">What is the Bounding box?</span></span>

<span data-ttu-id="23768-107">Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="23768-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="23768-108">Der Benutzer erhält eine Kosten, die das Objekt momentan anpassbar ist.</span><span class="sxs-lookup"><span data-stu-id="23768-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="23768-109">In den Ecken wird dem Benutzer mitgeteilt, dass das Objekt auch skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="23768-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="23768-110">Diese visuelle Visualisierung zeigt Benutzern den gesamten Bereich des Objekts an – auch dann, wenn Sie außerhalb eines Anpassungsmodus nicht sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="23768-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="23768-111">Dies ist besonders wichtig, da das Objekt, das an ein anderes Objekt oder eine andere Oberfläche angedockt ist, sich so verhält, als ob es sich um ein Leerzeichen handelt, das nicht vorhanden sein sollte.</span><span class="sxs-lookup"><span data-stu-id="23768-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="23768-112">Bei hololens 2 funktioniert das umgebende Feld mit direkter Hand Manipulation und antwortet auf die Nähe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="23768-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="23768-113">Es zeigt visuelles Feedback, um dem Benutzer zu helfen, den Abstand zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="23768-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="23768-114">![Hololens zeigt das Skalieren eines Objekts über ein Begrenzungsfeld an](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="23768-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="23768-115">*Skalieren eines Objekts per Begrenzungs Rahmen*</span><span class="sxs-lookup"><span data-stu-id="23768-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="23768-116">Die Handles in den Ecken des umgebenden Felds folgen einem weit verbreiteten Muster zur Anpassung der Skalierung.</span><span class="sxs-lookup"><span data-stu-id="23768-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="23768-117">![Hololens-Sicht der Drehung eines Objekts über das umgebende Feld](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="23768-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="23768-118">*Drehen eines Objekts über ein Begrenzungs Fenster*</span><span class="sxs-lookup"><span data-stu-id="23768-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="23768-119">![Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="23768-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="23768-120">*Visuelles Feedback basierend auf der Nähe*</span><span class="sxs-lookup"><span data-stu-id="23768-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="23768-121">Die vertikalen rechteckigen Anlagen an den Rändern des umgebenden Felds sind Rotations Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="23768-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="23768-122">Dies ermöglicht dem Benutzer eine präzisere Anpassung der platzierten holograms.</span><span class="sxs-lookup"><span data-stu-id="23768-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="23768-123">Sie können nicht nur angepasst und skaliert werden, sondern auch jetzt drehen.</span><span class="sxs-lookup"><span data-stu-id="23768-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="23768-124">Informationen zur Entwicklung von Unity-apps finden Sie [im Thema zum umgebenden Feld in Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="23768-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="23768-125">Was ist die APP-Leiste?</span><span class="sxs-lookup"><span data-stu-id="23768-125">What is the App bar?</span></span>

<span data-ttu-id="23768-126">Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23768-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="23768-127">Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von holograms zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="23768-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="23768-128">Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die APP-Leiste immer auf der Seite der Objekte angezeigt, die dem Benutzer am nächsten ist, wenn sich der Benutzer um das Objekt bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="23768-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="23768-129">Obwohl dies kein Abgleich ist, erzielt es effektiv dasselbe Ergebnis. verhindern, dass die Position eines Benutzers Funktionen sperrt oder blockiert, die andernfalls an einem anderen Speicherort in Ihrer Umgebung verfügbar wären.</span><span class="sxs-lookup"><span data-stu-id="23768-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="23768-130">![Durchlaufen eines holograms.</span><span class="sxs-lookup"><span data-stu-id="23768-130">![Walking around a hologram.</span></span> <span data-ttu-id="23768-131">Die APP-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="23768-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="23768-132">*Wenn Sie ein Hologramm durchlaufen, folgt die APP-Leiste.*</span><span class="sxs-lookup"><span data-stu-id="23768-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="23768-133">Die APP-Leiste wurde primär als eine Möglichkeit zum Verwalten von platzierten Objekten in der Umgebung eines Benutzers entwickelt.</span><span class="sxs-lookup"><span data-stu-id="23768-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="23768-134">In Verbindung mit dem umgebenden Feld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in gemischter Realität ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="23768-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="23768-135">Informationen zur Entwicklung von Unity-apps finden Sie [in der APP-Leiste unter Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="23768-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="23768-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="23768-136">See also</span></span>
* [<span data-ttu-id="23768-137">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="23768-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="23768-138">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="23768-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="23768-139">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="23768-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="23768-140">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="23768-140">Displaying progress</span></span>](progress.md)
