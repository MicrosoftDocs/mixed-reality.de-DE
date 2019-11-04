---
title: Objektsammlung
description: Die Objekt Auflistung ist ein Layoutsteuerelement, das Ihnen hilft, ein Array von Objekten in einer vordefinierten dreidimensionalen Form zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Steuerelemente, Entwurf
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438173"
---
# <a name="object-collection"></a><span data-ttu-id="617e6-104">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="617e6-104">Object collection</span></span>

![Objektsammlung, die in der periodischen Tabelle der Elements-App verwendet wird.](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="617e6-106">Die Objekt Auflistung ist ein Layoutsteuerelement, das Ihnen hilft, ein Array von Objekten in einer vordefinierten dreidimensionalen Form zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="617e6-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="617e6-107">Es unterstützt verschiedene Oberflächen Stile: **Ebene, Zylinder, Kugel** und **radiale**.</span><span class="sxs-lookup"><span data-stu-id="617e6-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="617e6-108">Sie können den RADIUS und die Größe der Objekte sowie den Leerraum zwischen Ihnen anpassen.</span><span class="sxs-lookup"><span data-stu-id="617e6-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="617e6-109">Die Objekt Auflistung unterstützt ein beliebiges Objekt aus Unity (2D und 3D).</span><span class="sxs-lookup"><span data-stu-id="617e6-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="617e6-110">Im **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** haben wir ein Unity-Skript und Beispiele erstellt, die Sie beim Erstellen einer Objektsammlung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="617e6-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="617e6-111">Beispiele für die Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="617e6-111">Object collection examples</span></span>

<span data-ttu-id="617e6-112">[Die periodische Tabelle der-Elemente](periodic-table-of-the-elements.md) ist eine Beispiel-APP, die die Funktionsweise der Objekt Auflistung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="617e6-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="617e6-113">Sie verwendet die Objekt Auflistung, um 3D-Elemente für das chemische Element in verschiedenen Formen anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="617e6-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="617e6-114">![Beispiele für die Objektsammlung, die in der periodischen Tabelle der Elements-App angezeigt werden](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="617e6-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="617e6-115">*Beispiele für die Objektsammlung, die in der periodischen Tabelle der Beispiel-App für Elemente angezeigt werden*</span><span class="sxs-lookup"><span data-stu-id="617e6-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="617e6-116">3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="617e6-116">3D objects</span></span>

<span data-ttu-id="617e6-117">Sie können die Objekt Auflistung verwenden, um importierte 3D-Objekte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="617e6-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="617e6-118">Das folgende Beispiel zeigt eine Ebene und ein Zylinder Layout für einige 3D-Stuhl Objekte.</span><span class="sxs-lookup"><span data-stu-id="617e6-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="617e6-119">![Beispiele für Ebenen-und zylindrische Layouts von 3D-Objekten](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="617e6-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="617e6-120">*Beispiele für die Ebenen-und zylindrischen Layouts von 3D-Objekten*</span><span class="sxs-lookup"><span data-stu-id="617e6-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="617e6-121">2D-Objekte</span><span class="sxs-lookup"><span data-stu-id="617e6-121">2D objects</span></span>

<span data-ttu-id="617e6-122">Sie können auch 2D-Images mit der Objektsammlung verwenden.</span><span class="sxs-lookup"><span data-stu-id="617e6-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="617e6-123">In den folgenden Beispielen wird veranschaulicht, wie 2D-images in einem Raster angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="617e6-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Beispiel für 2D-Bilder mit Objekt Auflistung](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="617e6-125">![ein Beispiel für 2D-Images mit Objektsammlung](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="617e6-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="617e6-126">*Beispiele für die Verwendung der Objektsammlung mit 2D-images*</span><span class="sxs-lookup"><span data-stu-id="617e6-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="617e6-127">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="617e6-127">See also</span></span>
* [<span data-ttu-id="617e6-128">Skripts und Prefabs für die Objektsammlung im Mixed Reality Toolkit auf GitHub</span><span class="sxs-lookup"><span data-stu-id="617e6-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="617e6-129">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="617e6-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="617e6-130">Begrenzungs Fenster</span><span class="sxs-lookup"><span data-stu-id="617e6-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
