---
title: Eine objektauflistung
description: Eine objektauflistung ist ein Layout-Steuerelement, dem Sie ein Array von Objekten in eine vordefinierte dreidimensionale Form anordnen kann.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Steuerelemente, Entwurf
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605014"
---
# <a name="object-collection"></a><span data-ttu-id="6bc51-104">Eine objektauflistung</span><span class="sxs-lookup"><span data-stu-id="6bc51-104">Object collection</span></span>

<span data-ttu-id="6bc51-105">Eine objektauflistung ist ein Layout-Steuerelement, dem Sie ein Array von Objekten in eine vordefinierte dreidimensionale Form anordnen kann.</span><span class="sxs-lookup"><span data-stu-id="6bc51-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="6bc51-106">Unterstützt vier verschiedene Oberfläche Formate - **Plane, Zylinder, Kugel** und **Punktdiagramm**.</span><span class="sxs-lookup"><span data-stu-id="6bc51-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="6bc51-107">Sie können die RADIUS- und die Größe der Objekte und den Abstand zwischen ihnen anpassen.</span><span class="sxs-lookup"><span data-stu-id="6bc51-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="6bc51-108">Eine objektauflistung unterstützt ein Objekt aus Unity – sowohl 2D- und 3D-Spiele.</span><span class="sxs-lookup"><span data-stu-id="6bc51-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="6bc51-109">In der  **[Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, wir haben die Unity-Skript erstellt und [Beispiel Szene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) Dies hilft Ihnen, eine objektauflistung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6bc51-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="6bc51-110">![Objektauflistung, die in der Tabelle periodisch Elemente-App verwendet](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6bc51-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="6bc51-111">*Objektauflistung, die in der Tabelle periodisch Elemente-Beispiel-App verwendet*</span><span class="sxs-lookup"><span data-stu-id="6bc51-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="6bc51-112">Beispiele für die Objekt-Auflistung</span><span class="sxs-lookup"><span data-stu-id="6bc51-112">Object collection examples</span></span>

<span data-ttu-id="6bc51-113">[Periodisch-Tabelle der Elemente](periodic-table-of-the-elements.md) ist eine Beispiel-app, die veranschaulicht die Funktionsweise der Objektsammlung.</span><span class="sxs-lookup"><span data-stu-id="6bc51-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="6bc51-114">Eine objektauflistung verwendet, um das Layout von chemischen-3D-Element-Felder in verschiedenen Formen.</span><span class="sxs-lookup"><span data-stu-id="6bc51-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="6bc51-115">![Objekt Auflistung Beispiele in der Tabelle periodisch Elemente-App](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6bc51-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="6bc51-116">*Objekt Auflistung Beispiele in der Tabelle periodisch Elemente-Beispiel-App*</span><span class="sxs-lookup"><span data-stu-id="6bc51-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="6bc51-117">3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="6bc51-117">3D objects</span></span>

<span data-ttu-id="6bc51-118">Sie können objektauflistung verwenden, um das Layout von importierten 3D-Objekte.</span><span class="sxs-lookup"><span data-stu-id="6bc51-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="6bc51-119">Das folgende Beispiel zeigt eine Ebene und ein Zylinder-Layout einiger 3D Stuhl-Objekte.</span><span class="sxs-lookup"><span data-stu-id="6bc51-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="6bc51-120">![Beispiele für Ebene und zylindrische Layouts von 3D-Objekten](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6bc51-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="6bc51-121">*Beispiele für Ebene und zylindrische Layouts von 3D-Objekten*</span><span class="sxs-lookup"><span data-stu-id="6bc51-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="6bc51-122">2D Objekte</span><span class="sxs-lookup"><span data-stu-id="6bc51-122">2D objects</span></span>

<span data-ttu-id="6bc51-123">Sie können auch mit objektauflistung 2D-Bilder verwenden.</span><span class="sxs-lookup"><span data-stu-id="6bc51-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="6bc51-124">Die folgenden Beispiele veranschaulichen, wie 2D-Bilder kann in einem Raster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6bc51-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Ein Beispiel für 2D-Bilder mit objektauflistung](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="6bc51-126">![Ein Beispiel für 2D-Bilder mit objektauflistung](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="6bc51-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="6bc51-127">*Beispiele für 2D-Bilder mit objektauflistung*</span><span class="sxs-lookup"><span data-stu-id="6bc51-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="6bc51-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6bc51-128">See also</span></span>
* [<span data-ttu-id="6bc51-129">Skripts und prefabs (Vorlagen) zum Sammeln von Objekten im Mixed Reality-Toolkit auf GitHub</span><span class="sxs-lookup"><span data-stu-id="6bc51-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="6bc51-130">Es-Objekt</span><span class="sxs-lookup"><span data-stu-id="6bc51-130">Interactable object</span></span>](interactable-object.md)
