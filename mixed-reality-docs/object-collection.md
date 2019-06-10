---
title: Eine objektauflistung
description: Eine objektauflistung ist ein Layout-Steuerelement, dem Sie ein Array von Objekten in eine vordefinierte dreidimensionale Form anordnen kann.
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
# <a name="object-collection"></a><span data-ttu-id="58f5d-104">Eine objektauflistung</span><span class="sxs-lookup"><span data-stu-id="58f5d-104">Object collection</span></span>

<span data-ttu-id="58f5d-105">Eine objektauflistung ist ein Layout-Steuerelement, dem Sie ein Array von Objekten in eine vordefinierte dreidimensionale Form anordnen kann.</span><span class="sxs-lookup"><span data-stu-id="58f5d-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="58f5d-106">Es unterstützt verschiedene Formateigenschaften für Surface - **Plane, Zylinder, Kugel** und **radiale**.</span><span class="sxs-lookup"><span data-stu-id="58f5d-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="58f5d-107">Sie können die RADIUS- und die Größe der Objekte und den Abstand zwischen ihnen anpassen.</span><span class="sxs-lookup"><span data-stu-id="58f5d-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="58f5d-108">Eine objektauflistung unterstützt ein Objekt aus Unity – sowohl 2D- und 3D-Spiele.</span><span class="sxs-lookup"><span data-stu-id="58f5d-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="58f5d-109">In der  **[Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , wir haben die Unity-Skript erstellt und Beispiele, mit denen Sie erstellen eine objektauflistung.</span><span class="sxs-lookup"><span data-stu-id="58f5d-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="58f5d-110">![Objektauflistung, die in der Tabelle periodisch Elemente-App verwendet](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="58f5d-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="58f5d-111">*Beispiele für die Verwendung der Objektsammlung*</span><span class="sxs-lookup"><span data-stu-id="58f5d-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="58f5d-112">Beispiele für die Objekt-Auflistung</span><span class="sxs-lookup"><span data-stu-id="58f5d-112">Object collection examples</span></span>

<span data-ttu-id="58f5d-113">[Periodisch-Tabelle der Elemente](periodic-table-of-the-elements.md) ist eine Beispiel-app, die veranschaulicht die Funktionsweise der Objektsammlung.</span><span class="sxs-lookup"><span data-stu-id="58f5d-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="58f5d-114">Eine objektauflistung verwendet, um das Layout von chemischen-3D-Element-Felder in verschiedenen Formen.</span><span class="sxs-lookup"><span data-stu-id="58f5d-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="58f5d-115">![Objekt Auflistung Beispiele in der Tabelle periodisch Elemente-App](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="58f5d-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="58f5d-116">*Objekt Auflistung Beispiele in der Tabelle periodisch Elemente-Beispiel-App*</span><span class="sxs-lookup"><span data-stu-id="58f5d-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="58f5d-117">3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="58f5d-117">3D objects</span></span>

<span data-ttu-id="58f5d-118">Sie können objektauflistung verwenden, um das Layout von importierten 3D-Objekte.</span><span class="sxs-lookup"><span data-stu-id="58f5d-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="58f5d-119">Das folgende Beispiel zeigt eine Ebene und ein Zylinder-Layout einiger 3D Stuhl-Objekte.</span><span class="sxs-lookup"><span data-stu-id="58f5d-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="58f5d-120">![Beispiele für Ebene und zylindrische Layouts von 3D-Objekten](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="58f5d-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="58f5d-121">*Beispiele für Ebene und zylindrische Layouts von 3D-Objekten*</span><span class="sxs-lookup"><span data-stu-id="58f5d-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="58f5d-122">2D Objekte</span><span class="sxs-lookup"><span data-stu-id="58f5d-122">2D objects</span></span>

<span data-ttu-id="58f5d-123">Sie können auch mit objektauflistung 2D-Bilder verwenden.</span><span class="sxs-lookup"><span data-stu-id="58f5d-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="58f5d-124">Die folgenden Beispiele veranschaulichen, wie 2D-Bilder kann in einem Raster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="58f5d-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Ein Beispiel für 2D-Bilder mit objektauflistung](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="58f5d-126">![Ein Beispiel für 2D-Bilder mit objektauflistung](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="58f5d-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="58f5d-127">*Beispiele für die Verwendung der Objektsammlung mit 2D-Bildern*</span><span class="sxs-lookup"><span data-stu-id="58f5d-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="58f5d-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="58f5d-128">See also</span></span>
* [<span data-ttu-id="58f5d-129">Skripts und prefabs (Vorlagen) zum Sammeln von Objekten im Mixed Reality-Toolkit auf GitHub</span><span class="sxs-lookup"><span data-stu-id="58f5d-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="58f5d-130">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="58f5d-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="58f5d-131">Umgebendes Feld</span><span class="sxs-lookup"><span data-stu-id="58f5d-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
