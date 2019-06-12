---
title: Umgebendes Feld und App-Leiste
description: Die App-Leiste ist ein auf Objektebene Menü mit einer Reihe von Schaltflächen, die auf dem unteren Rand der ggf. ein Hologramm Begrenzungen angezeigt.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, umgebendes Feld
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829685"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="b53f4-104">Umgebendes Feld und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="b53f4-104">Bounding box and App bar</span></span>
![Begrenzen, ist die Standardschnittstelle für die Bearbeitung des Objekts in Mixed Reality.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="b53f4-106">Was ist das umgebende Feld?</span><span class="sxs-lookup"><span data-stu-id="b53f4-106">What is the Bounding box?</span></span>

<span data-ttu-id="b53f4-107">Begrenzen, ist die Standardschnittstelle für die Bearbeitung des Objekts in Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b53f4-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="b53f4-108">Es bietet dem Benutzer eine Unterstützung, dass das Objekt derzeit überhaupt angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="b53f4-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="b53f4-109">Die Ecken, wird dem Benutzer mitgeteilt, dass das Objekt auch skalieren kann.</span><span class="sxs-lookup"><span data-stu-id="b53f4-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="b53f4-110">Dieser visuelle Unterstützung zeigt Benutzer die Gesamtfläche des Objekts – auch wenn es nicht außerhalb einer Anpassung Modus angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b53f4-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="b53f4-111">Dies ist besonders wichtig, da ein Objekt, das an einem anderen Objekt oder Fläche Rasterlinie ausgerichtet, wenn er nicht vorhanden wäre, so verhält, als gäbe Platz um es herum, die es sollte nicht angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b53f4-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="b53f4-112">HoloLens-2 das umgebende Feld arbeitet mit direkten manuell bearbeiten und reagiert auf dem Finger des Benutzers die Nähe.</span><span class="sxs-lookup"><span data-stu-id="b53f4-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="b53f4-113">Es zeigt visuelles Feedback den Benutzer, der den Abstand zwischen dem Objekt wahrnehmen können.</span><span class="sxs-lookup"><span data-stu-id="b53f4-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="b53f4-114">![HoloLens-von-Sicht der Skalierung eines Objekts über umgebendes Feld](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="b53f4-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="b53f4-115">*Die Skalierung eines Objekts über umgebendes Feld*</span><span class="sxs-lookup"><span data-stu-id="b53f4-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="b53f4-116">Die Handles in den Ecken des Begrenzungsrahmens führen Sie ein allgemein verstanden Muster für die Skalierung anpassen.</span><span class="sxs-lookup"><span data-stu-id="b53f4-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="b53f4-117">![HoloLens-von-Sicht der Drehen eines Objekts über umgebendes Feld](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="b53f4-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="b53f4-118">*Drehen eines Objekts über umgebendes Feld*</span><span class="sxs-lookup"><span data-stu-id="b53f4-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="b53f4-119">![Visuelles Feedback auf der Hand NEAR](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="b53f4-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="b53f4-120">*Visuelles Feedback auf der Grundlage der Nähe*</span><span class="sxs-lookup"><span data-stu-id="b53f4-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="b53f4-121">Die vertikale rechteckigen visueller Hinweise an den Rändern des umgebenden Felds handelt es sich um Drehung Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="b53f4-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="b53f4-122">Dadurch erhalten Benutzer weitere Feineinstellung über ihre Hologramme platziert.</span><span class="sxs-lookup"><span data-stu-id="b53f4-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="b53f4-123">Nicht nur können sie anpassen und skalieren, aber jetzt auch drehen.</span><span class="sxs-lookup"><span data-stu-id="b53f4-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="b53f4-124">Unity-app-Entwicklung, finden Sie unter [umgebendes Feld auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="b53f4-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="b53f4-125">Was ist der App-Leiste?</span><span class="sxs-lookup"><span data-stu-id="b53f4-125">What is the App bar?</span></span>

<span data-ttu-id="b53f4-126">Die App-Leiste ist ein auf Objektebene Menü mit einer Reihe von Schaltflächen, die auf dem unteren Rand der ggf. ein Hologramm Begrenzungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b53f4-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="b53f4-127">Dieses Muster wird häufig verwendet, um Benutzern die Möglichkeit, zu entfernen, und passen Sie Hologramme zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b53f4-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="b53f4-128">Da dieses Muster mit Objekten, die Welt gesperrt verwendet wird, wie ein Benutzer auf das Objekt bewegt wird die App-Leiste immer auf der Objekte neben dem Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b53f4-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="b53f4-129">Während dies billboarding nicht ist, wird das gleiche Ergebnis effektiv erreicht; verhindert, dass Position verdeckt eines Benutzers oder der Block-Funktionen, die andernfalls von einem anderen Speicherort in ihrer Umgebung zur Verfügung stehen würden.</span><span class="sxs-lookup"><span data-stu-id="b53f4-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="b53f4-130">![Um ggf. ein Hologramm durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="b53f4-130">![Walking around a hologram.</span></span> <span data-ttu-id="b53f4-131">Die App-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="b53f4-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="b53f4-132">*Durchlaufen, um ggf. ein Hologramm, folgt die App-Leiste*</span><span class="sxs-lookup"><span data-stu-id="b53f4-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="b53f4-133">Die App-Leiste wurde in erster Linie als eine Möglichkeit zum Verwalten der platzierten Objekte in der Umgebung eines Benutzers entwickelt.</span><span class="sxs-lookup"><span data-stu-id="b53f4-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="b53f4-134">Gekoppelt mit das umgebende Feld, ein Benutzer verfügt über Vollzugriff auf, wo und wie Objekte in mixed Reality ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="b53f4-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="b53f4-135">Unity-app-Entwicklung, finden Sie unter [App-Leiste auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="b53f4-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="b53f4-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b53f4-136">See also</span></span>
* [<span data-ttu-id="b53f4-137">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="b53f4-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b53f4-138">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="b53f4-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="b53f4-139">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="b53f4-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b53f4-140">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="b53f4-140">Displaying progress</span></span>](progress.md)
