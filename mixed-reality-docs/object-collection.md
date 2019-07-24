---
title: Objektsammlung
description: Die Objekt Auflistung ist ein Layoutsteuerelement, das Ihnen hilft, ein Array von Objekten in einer vordefinierten dreidimensionalen Form zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Steuerelemente, Entwurf
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813885"
---
# <a name="object-collection"></a><span data-ttu-id="0967d-104">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="0967d-104">Object collection</span></span>

<span data-ttu-id="0967d-105">Die Objekt Auflistung ist ein Layoutsteuerelement, das Ihnen hilft, ein Array von Objekten in einer vordefinierten dreidimensionalen Form zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0967d-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="0967d-106">Es unterstützt verschiedene Oberflächen Stile: **Ebene, Zylinder, Kugel** und **radiale**.</span><span class="sxs-lookup"><span data-stu-id="0967d-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="0967d-107">Sie können den RADIUS und die Größe der Objekte sowie den Leerraum zwischen Ihnen anpassen.</span><span class="sxs-lookup"><span data-stu-id="0967d-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="0967d-108">Die Objekt Auflistung unterstützt ein beliebiges Objekt aus Unity (2D und 3D).</span><span class="sxs-lookup"><span data-stu-id="0967d-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="0967d-109">Im **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** haben wir ein Unity-Skript und Beispiele erstellt, die Sie beim Erstellen einer Objektsammlung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0967d-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="0967d-110">![Objektsammlung, die in der periodischen Tabelle der Elements-App verwendet wird.](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0967d-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="0967d-111">*Beispiele für die Verwendung der Objektsammlung*</span><span class="sxs-lookup"><span data-stu-id="0967d-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="0967d-112">Beispiele für die Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="0967d-112">Object collection examples</span></span>

<span data-ttu-id="0967d-113">[Die periodische Tabelle der-Elemente](periodic-table-of-the-elements.md) ist eine Beispiel-APP, die die Funktionsweise der Objekt Auflistung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="0967d-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="0967d-114">Sie verwendet die Objekt Auflistung, um 3D-Elemente für das chemische Element in verschiedenen Formen anzuordnen.</span><span class="sxs-lookup"><span data-stu-id="0967d-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="0967d-115">![Beispiele für die Objektsammlung, die in der periodischen Tabelle der Elements-App angezeigt werden](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0967d-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="0967d-116">*Beispiele für die Objektsammlung, die in der periodischen Tabelle der Beispiel-App für Elemente angezeigt werden*</span><span class="sxs-lookup"><span data-stu-id="0967d-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="0967d-117">3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="0967d-117">3D objects</span></span>

<span data-ttu-id="0967d-118">Sie können die Objekt Auflistung verwenden, um importierte 3D-Objekte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="0967d-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="0967d-119">Das folgende Beispiel zeigt eine Ebene und ein Zylinder Layout für einige 3D-Stuhl Objekte.</span><span class="sxs-lookup"><span data-stu-id="0967d-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="0967d-120">![Beispiele für die Ebenen-und zylindrischen Layouts von 3D-Objekten](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0967d-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="0967d-121">*Beispiele für die Ebenen-und zylindrischen Layouts von 3D-Objekten*</span><span class="sxs-lookup"><span data-stu-id="0967d-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="0967d-122">2D-Objekte</span><span class="sxs-lookup"><span data-stu-id="0967d-122">2D objects</span></span>

<span data-ttu-id="0967d-123">Sie können auch 2D-Images mit der Objektsammlung verwenden.</span><span class="sxs-lookup"><span data-stu-id="0967d-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="0967d-124">In den folgenden Beispielen wird veranschaulicht, wie 2D-images in einem Raster angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="0967d-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Beispiel für 2D-Bilder mit Objekt Auflistung](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="0967d-126">![Beispiel für 2D-Bilder mit Objekt Auflistung](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="0967d-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="0967d-127">*Beispiele für die Verwendung der Objektsammlung mit 2D-images*</span><span class="sxs-lookup"><span data-stu-id="0967d-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="0967d-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0967d-128">See also</span></span>
* [<span data-ttu-id="0967d-129">Skripts und Prefabs für die Objektsammlung im Mixed Reality Toolkit auf GitHub</span><span class="sxs-lookup"><span data-stu-id="0967d-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="0967d-130">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="0967d-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0967d-131">Begrenzungs Fenster</span><span class="sxs-lookup"><span data-stu-id="0967d-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
