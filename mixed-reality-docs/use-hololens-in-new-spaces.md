---
title: Verwenden von hololens in neuen Leerzeichen
description: Hololens erfährt, wie ein Raum im Laufe der Zeit aussieht. Benutzer können diesen Prozess vereinfachen, indem Sie die hololens auf bestimmte Weise über den Raum verschieben.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, räumliche Zuordnung, hololens, Oberflächenrekonstruktion, Mesh, Head Tracking, Mapping
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566019"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="b9d0b-105">Verwenden von hololens in neuen Leerzeichen</span><span class="sxs-lookup"><span data-stu-id="b9d0b-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="b9d0b-106">Hololensordnet Informationen zu Ihrer Umgebung zu oder erfährt diese, wenn der Benutzer sich um ein Leerzeichen bewegt.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="b9d0b-107">Im Laufe der Zeit erstellt der hololens eine *räumliche Karte* aller Teile der Umgebung, die beobachtet wurden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="b9d0b-108">Hololens aktualisiert die Karte, wenn Änderungen in der Umgebung beobachtet werden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="b9d0b-109">Diese Überprüfung wird automatisch zwischen App-Starts beibehalten.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="b9d0b-110">Hololens erstellt und aktualisiert Zuordnungen, solange das Gerät eingeschaltet ist und ein Benutzer angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="b9d0b-111">Wenn Sie das Gerät mit den Kameras halten, die auf ein Leerzeichen zeigen, wird das Gerät versuchen, den Bereich zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="b9d0b-112">Obwohl die hololens im Laufe der Zeit ein Leerzeichen erlernen, stehen Ihnen Tipps und Tricks zur Verfügung, mit denen Sie den Raum schneller und effizienter zuordnen können.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="b9d0b-113">Wenn Ihre hololens Ihren Speicherplatz nicht zuordnen können oder nicht.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="b9d0b-114">Im eingeschränkten Modus können Sie holograms nicht in Ihrer Umgebung platzieren.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="b9d0b-115">Tipps und Tricks zum Mapping von Leerzeichen</span><span class="sxs-lookup"><span data-stu-id="b9d0b-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="b9d0b-116">Stellen Sie sicher, dass der Speicherplatz für die gemischte Realität eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="b9d0b-117">Funktionen in einer Umgebung können es den hololens erschweren, ein Leerzeichen zu interpretieren.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="b9d0b-118">Helle Ebenen, Materialien im Raum, das Layout von Objekten und mehr können beeinflussen, wie hololens einen Bereich zuordnet.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="b9d0b-119">Tipps zum Einrichten Ihres Speicherplatzes für hololens und andere gemischte Reality-Geräte finden Sie unter [Überlegungen zur Umgebung für hololens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="b9d0b-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="b9d0b-120">Verstehen der Szenarien für den Bereich</span><span class="sxs-lookup"><span data-stu-id="b9d0b-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="b9d0b-121">Es ist wichtig, dass Sie die meiste Zeit aufwenden, in der Sie die hololens verwenden, damit die Karte relevant und fertig ist.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="b9d0b-122">Wenn z. b. ein Benutzer Szenario für hololens von Punkt a zu Punkt B wechselt, führen Sie diesen Pfad zwei bis drei Mal aus, und suchen Sie in allen Richtungen nach dem verschieben.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="b9d0b-123">Gehen Sie langsam um den Bereich.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-123">Walk slowly around the space</span></span>

<span data-ttu-id="b9d0b-124">Wenn Sie den Bereich zu schnell durchlaufen, ist es wahrscheinlich, dass die hololens zuordnungsbereiche übersehen werden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="b9d0b-125">Gehen Sie langsam um den Raum, und beenden Sie alle 5-8 Meter, um sich in Ihrer Umgebung anzusehen.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="b9d0b-126">Smooth Movement unterstützt auch die Zuordnung von hololens.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="b9d0b-127">In alle Richtungen suchen</span><span class="sxs-lookup"><span data-stu-id="b9d0b-127">Look in all directions</span></span>

<span data-ttu-id="b9d0b-128">Wenn Sie den Leerraum Zuordnungen, werden den hololens mehr Daten angezeigt, in denen sich Punkte relativ zueinander befinden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="b9d0b-129">Wenn Sie z. b. nicht nachschlagen, wissen die hololens möglicherweise nicht, wo die Obergrenze in einem Raum liegt.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="b9d0b-130">Vergessen Sie nicht, auf dem Boden zu suchen, während Sie das Leerzeichen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="b9d0b-131">Wichtige Bereiche mehrmals abdecken</span><span class="sxs-lookup"><span data-stu-id="b9d0b-131">Cover key areas multiple times</span></span>

<span data-ttu-id="b9d0b-132">Wenn Sie einen Bereich mehrmals durchlaufen, können Sie Features auswählen, die Sie in der ersten exemplarischen Vorgehensweise übersehen haben.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="b9d0b-133">Versuchen Sie, einen Bereich von zwei bis drei Mal zu durchlaufen, um eine ideale Karte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="b9d0b-134">Wenn dies möglich ist, können Sie sich beim Wiederholen dieser Bewegungen Zeit um einen Bereich in einer Richtung machen und dann die Art und Weise wiederholen, wie Sie es kam.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="b9d0b-135">Nehmen Sie die Zeit für die Zuordnung des Bereichs</span><span class="sxs-lookup"><span data-stu-id="b9d0b-135">Take your time mapping the area</span></span>

<span data-ttu-id="b9d0b-136">Es kann zwischen 15 und 20 Minuten dauern, bis der hololens vollständig zugeordnet ist und sich an seine Umgebung anpasst.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="b9d0b-137">Wenn Sie über ein Leerzeichen verfügen, in dem Sie regelmäßig ein hololens verwenden möchten, können Sie das Problem später vermeiden, indem Sie diese Zeit zum Zuordnen des Speicherplatzes verwenden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="b9d0b-138">Mögliche Fehler in der räumlichen Karte</span><span class="sxs-lookup"><span data-stu-id="b9d0b-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="b9d0b-139">Fehler bei räumlichen Zuordnungsdaten lassen sich in eine von drei Kategorien unterteilen:</span><span class="sxs-lookup"><span data-stu-id="b9d0b-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="b9d0b-140">*Löcher*: In den räumlichen Mapping-Daten fehlen reale Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="b9d0b-141">*Halluerationen*: In den räumlichen Mapping-Daten, die nicht in der realen Welt vorhanden sind, sind Oberflächen vorhanden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="b9d0b-142">*Wurmlöcher*: Hololens "verliert" einen Teil der räumlichen Zuordnung, indem er denkt, dass er sich in einem anderen Teil der Karte befindet, als er tatsächlich ist.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="b9d0b-143">*Bias*: Oberflächen in den räumlichen Zuordnungsdaten sind unpassend an realen Oberflächen ausgerichtet, die entweder per pushübertragung oder ausgecheckt werden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="b9d0b-144">Viele dieser Fehler können durch [Löschen der Hologramme](environment-considerations-for-hololens.md) und Neuzuordnung des Speicherplatzes verringert werden.</span><span class="sxs-lookup"><span data-stu-id="b9d0b-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>