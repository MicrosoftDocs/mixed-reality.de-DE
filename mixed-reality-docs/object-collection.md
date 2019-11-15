---
title: Objektsammlung
description: Die Objekt Auflistung ist ein Layoutsteuerelement, das Ihnen hilft, ein Array von Objekten in einer vordefinierten dreidimensionalen Form zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Steuerelemente, Entwurf
ms.openlocfilehash: 98fec76558502658511faf3f18d623bfa5a49dc2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106004"
---
# <a name="object-collection"></a><span data-ttu-id="4254b-104">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="4254b-104">Object collection</span></span>

![Objektsammlung, die in der periodischen Tabelle der Elements-App verwendet wird.](images/UX/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="4254b-106">Die Objekt Auflistung ist ein Layoutsteuerelement, das Ihnen hilft, ein Array von Objekten in einer vordefinierten dreidimensionalen Form zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4254b-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="4254b-107">Es unterstützt verschiedene Oberflächen Stile: **Ebene, Zylinder, Kugel** und **radiale**.</span><span class="sxs-lookup"><span data-stu-id="4254b-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="4254b-108">Sie können den RADIUS und die Größe der Objekte sowie den Leerraum zwischen Ihnen anpassen.</span><span class="sxs-lookup"><span data-stu-id="4254b-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="4254b-109">Die Objekt Auflistung unterstützt ein beliebiges Objekt aus Unity (2D und 3D).</span><span class="sxs-lookup"><span data-stu-id="4254b-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="4254b-110">Im **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** haben wir ein Unity-Skript und Beispiele erstellt, die Sie beim Erstellen einer Objektsammlung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4254b-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="4254b-111">Beispiele für die Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="4254b-111">Object collection examples</span></span>

<span data-ttu-id="4254b-112">[Die periodische Tabelle der-Elemente](periodic-table-of-the-elements.md) ist eine Beispiel-APP, die die Funktionsweise der Objekt Auflistung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="4254b-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="4254b-113">Sie verwendet die Objekt Auflistung, um 3D-Elemente für das chemische Element in verschiedenen Formen anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="4254b-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="4254b-114">![Beispiele für die Objektsammlung, die in der periodischen Tabelle der Elements-App angezeigt werden](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4254b-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="4254b-115">*Beispiele für die Objektsammlung, die in der periodischen Tabelle der Beispiel-App für Elemente angezeigt werden*</span><span class="sxs-lookup"><span data-stu-id="4254b-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="4254b-116">3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="4254b-116">3D objects</span></span>

<span data-ttu-id="4254b-117">Sie können die Objekt Auflistung verwenden, um importierte 3D-Objekte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="4254b-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="4254b-118">Das folgende Beispiel zeigt eine Ebene und ein Zylinder Layout für einige 3D-Stuhl Objekte.</span><span class="sxs-lookup"><span data-stu-id="4254b-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="4254b-119">![Beispiele für Ebenen-und zylindrische Layouts von 3D-Objekten](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4254b-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="4254b-120">*Beispiele für die Ebenen-und zylindrischen Layouts von 3D-Objekten*</span><span class="sxs-lookup"><span data-stu-id="4254b-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="4254b-121">2D-Objekte</span><span class="sxs-lookup"><span data-stu-id="4254b-121">2D objects</span></span>

<span data-ttu-id="4254b-122">Sie können auch 2D-Images mit der Objektsammlung verwenden.</span><span class="sxs-lookup"><span data-stu-id="4254b-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="4254b-123">In den folgenden Beispielen wird veranschaulicht, wie 2D-images in einem Raster angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="4254b-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Beispiel für 2D-Bilder mit Objekt Auflistung](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="4254b-125">![ein Beispiel für 2D-Images mit Objektsammlung](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="4254b-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="4254b-126">*Beispiele für die Verwendung der Objektsammlung mit 2D-images*</span><span class="sxs-lookup"><span data-stu-id="4254b-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="4254b-127">Objektsammlung in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="4254b-127">Object collection in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="4254b-128">Mrtk-Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="4254b-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="4254b-129">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="4254b-129">See also</span></span>

* [<span data-ttu-id="4254b-130">Cursor</span><span class="sxs-lookup"><span data-stu-id="4254b-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4254b-131">Hand Strahl</span><span class="sxs-lookup"><span data-stu-id="4254b-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="4254b-132">Button</span><span class="sxs-lookup"><span data-stu-id="4254b-132">Button</span></span>](button.md)
* [<span data-ttu-id="4254b-133">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="4254b-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4254b-134">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="4254b-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4254b-135">Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="4254b-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4254b-136">Handmenü</span><span class="sxs-lookup"><span data-stu-id="4254b-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="4254b-137">Near-Menü</span><span class="sxs-lookup"><span data-stu-id="4254b-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="4254b-138">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="4254b-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4254b-139">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="4254b-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="4254b-140">Tastatur</span><span class="sxs-lookup"><span data-stu-id="4254b-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="4254b-141">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="4254b-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="4254b-142">Tafel</span><span class="sxs-lookup"><span data-stu-id="4254b-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="4254b-143">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="4254b-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="4254b-144">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="4254b-144">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4254b-145">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="4254b-145">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="4254b-146">Oberflächen Magnetismus</span><span class="sxs-lookup"><span data-stu-id="4254b-146">Surface magnetism</span></span>](surface-magnetism.md)
