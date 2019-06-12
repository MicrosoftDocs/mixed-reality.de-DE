---
title: Die Überprüfung Visualisierung Platz
description: Anwendungen, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Design, HoloLens, Raum Scan, räumliche Zuordnung Wiederaufbau, surface mesh
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829912"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="dd914-104">Die Überprüfung Visualisierung Platz</span><span class="sxs-lookup"><span data-stu-id="dd914-104">Room scan visualization</span></span>

<span data-ttu-id="dd914-105">Anwendungen, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv.</span><span class="sxs-lookup"><span data-stu-id="dd914-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="dd914-106">Der Vollständigkeit und die Qualität der Daten hängt von einer Reihe von Faktoren wie der Menge der, die der Benutzer ausgeführt hat, wie viel Zeit verstrichen ist, da die Auswertung und gibt an, ob die Objekte, z. B. Möbel und Türen verschoben haben, da das Gerät über den Bereich überprüft.</span><span class="sxs-lookup"><span data-stu-id="dd914-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="dd914-107">Um nützliche räumliche Zuordnungsdaten zu gewährleisten, haben Anwendungsentwickler für mehrere Optionen:</span><span class="sxs-lookup"><span data-stu-id="dd914-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="dd914-108">Abhängig, was bereits gesammelt wurden.</span><span class="sxs-lookup"><span data-stu-id="dd914-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="dd914-109">Diese Daten können ursprünglich unvollständig sein.</span><span class="sxs-lookup"><span data-stu-id="dd914-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="dd914-110">Bitten Sie den Benutzer mit, dass die Bewegung Bloom lernen Sie die Windows Mixed Reality-home und sehen Sie sich dann den Bereich, die, den Sie für die Umgebung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="dd914-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="dd914-111">Sie können die tippbewegung verwenden, um sicherzustellen, dass alle erforderlichen Bereich, auf dem Gerät bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="dd914-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="dd914-112">Erstellen Sie eine benutzerdefinierte Auswertung Erfahrung in seiner eigenen Anwendung.</span><span class="sxs-lookup"><span data-stu-id="dd914-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="dd914-113">Beachten Sie, dass in all diesen Fällen die tatsächlichen Daten, die während der Auswertung durch das System gespeichert ist und die Anwendung nicht dazu muss.</span><span class="sxs-lookup"><span data-stu-id="dd914-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="dd914-114">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="dd914-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dd914-115"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="dd914-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="dd914-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd914-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="dd914-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd914-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dd914-118">Die Überprüfung Visualisierung Platz</span><span class="sxs-lookup"><span data-stu-id="dd914-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="dd914-119">✔️</span><span class="sxs-lookup"><span data-stu-id="dd914-119">✔️</span></span></td>
        <td><span data-ttu-id="dd914-120">❌</span><span class="sxs-lookup"><span data-stu-id="dd914-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="dd914-121">Erstellen eine benutzerdefinierte Überprüfung Erfahrung</span><span class="sxs-lookup"><span data-stu-id="dd914-121">Building a custom scanning experience</span></span>

<span data-ttu-id="dd914-122">Anwendungen können auf den analizar los datos räumliche Zuordnung zu Beginn der Umgebung zu beurteilen, ob sie möchten, dass die Benutzer auf die zusätzlichen Schritte ausführen, um die Vollständigkeit und Qualität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="dd914-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="dd914-123">Wenn Analysen weisen darauf hin, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung für die Überlagerung auf der ganzen Welt an bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="dd914-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="dd914-124">Wie viel von der Gesamtgröße des Datenträgers in der Nähe der Benutzer muss in der Umgebung sein.</span><span class="sxs-lookup"><span data-stu-id="dd914-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="dd914-125">In denen der Benutzer zur Verbesserung der Daten gespeichert werden sollen</span><span class="sxs-lookup"><span data-stu-id="dd914-125">Where the user should go to improve data</span></span>

<span data-ttu-id="dd914-126">Benutzer ist nicht bekannt macht eine Überprüfung "good".</span><span class="sxs-lookup"><span data-stu-id="dd914-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="dd914-127">Sie müssen angezeigt werden oder usw. mitgeteilt, wonach gesucht werden soll, wenn sie aufgefordert werden, einen Scan – Flachheit, Entfernung von der tatsächlichen Wände, ausgewertet. Der Entwickler muss eine Feedbackschleife implementieren, die enthält, die räumliche Zuordnung datenaktualisierung während der Phase Scannen oder durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="dd914-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="dd914-128">In vielen Fällen ist es möglicherweise am besten, die dem Benutzer mitzuteilen, was sie (z. B. die Obergrenze suchen hinter Möbel ansehen), um die Überprüfung der erforderlichen Qualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="dd914-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="dd914-129">Zwischenspeicherung im Vergleich zu fortlaufenden räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="dd914-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="dd914-130">Die Daten für die räumliche Zuordnung ist die am häufigsten hohes Gewicht, Data Source-Anwendungen nutzen können.</span><span class="sxs-lookup"><span data-stu-id="dd914-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="dd914-131">Um Leistungsprobleme zu vermeiden, z. B. abfallende Frames oder Stottern erfüllt, Verbrauch dieser Daten muss sorgfältig durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="dd914-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="dd914-132">Aktive scannen, während eine Benutzeroberfläche kann sowohl nützlich oder gleichzeitiger Aufrufe nachteilig auswirken und die Entwickler müssen Sie festlegen, die zu verwendende Methode abhängig von der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="dd914-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="dd914-133">Zwischengespeicherte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="dd914-133">Cached spatial mapping</span></span>

<span data-ttu-id="dd914-134">Im Fall von zwischengespeicherten räumliche Zuordnung, wird die Anwendung in der Regel eine Momentaufnahme der Daten räumliche Zuordnung, und diese Momentaufnahme für die Dauer der Benutzeroberfläche verwendet.</span><span class="sxs-lookup"><span data-stu-id="dd914-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="dd914-135">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="dd914-135">**Benefits**</span></span>
* <span data-ttu-id="dd914-136">Gemeinkosten auf dem System während die Oberfläche führende, auf eindrucksvolle Stromversorgung, temperaturüberwachung ausgeführt wird und cpu-Leistung erzielt.</span><span class="sxs-lookup"><span data-stu-id="dd914-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="dd914-137">Eine einfachere Implementierung der main-Umgebung, da er nicht von Änderungen in den räumlichen Daten unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="dd914-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="dd914-138">Ein einzelnes einmal, die Kosten für die räumlichen Daten für Physik, Grafiken und andere Zwecke verarbeitet Post.</span><span class="sxs-lookup"><span data-stu-id="dd914-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="dd914-139">**Drawbacks**</span><span class="sxs-lookup"><span data-stu-id="dd914-139">**Drawbacks**</span></span>
* <span data-ttu-id="dd914-140">Das Verschieben von realen Objekten oder Personen, die nicht durch die zwischengespeicherten Daten wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="dd914-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="dd914-141">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="dd914-141">E.g.</span></span> <span data-ttu-id="dd914-142">die Anwendung ggf. eine Tür geöffnet, wenn sie nun geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="dd914-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="dd914-143">Möglicherweise weitere Anwendungsspeicher auf die zwischengespeicherte Version der Daten zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="dd914-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="dd914-144">Ein überzeugendes Argument für diese Methode ist einer kontrollierten Umgebung oder eine Tabelle, die Top-Spiel.</span><span class="sxs-lookup"><span data-stu-id="dd914-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="dd914-145">Fortlaufende räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="dd914-145">Continuous spatial mapping</span></span>

<span data-ttu-id="dd914-146">Bestimmte Anwendungen basieren möglicherweise auf weiterhin Scans aus, um die räumliche Zuordnungsdaten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dd914-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="dd914-147">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="dd914-147">**Benefits**</span></span>
* <span data-ttu-id="dd914-148">Sie müssen nicht in einer separaten Scannen oder Durchsuchen Benutzeroberfläche schon im Vorfeld in Ihrer Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="dd914-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="dd914-149">Die Verschiebung der realen Welt Objekte kann durch das Spiel auch mit der eine Verzögerung wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="dd914-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="dd914-150">**Drawbacks**</span><span class="sxs-lookup"><span data-stu-id="dd914-150">**Drawbacks**</span></span>
* <span data-ttu-id="dd914-151">Höhere Komplexität in der Implementierung der main-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="dd914-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="dd914-152">Potenzielle Aufwand für die zusätzliche Verarbeitung für Grafik oder Physik als Änderungen inkrementell von diesen Systemen erfasst werden müssen.</span><span class="sxs-lookup"><span data-stu-id="dd914-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="dd914-153">Höhere Leistung, thermischer und Auswirkung auf die CPU.</span><span class="sxs-lookup"><span data-stu-id="dd914-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="dd914-154">Ein überzeugendes Argument für diese Methode ist eine Hologramme werden, in denen erwartet, für die Interaktion mit dem Verschieben von Objekten, z. B. ein holographic Auto, die Laufwerke auf dem Boden ordnungsgemäß in eine Tür abhängig davon, ob sie offene oder geschlossene erhöhen möchten.</span><span class="sxs-lookup"><span data-stu-id="dd914-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd914-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dd914-155">See also</span></span>
* [<span data-ttu-id="dd914-156">Gestaltung von räumlicher Abbildung</span><span class="sxs-lookup"><span data-stu-id="dd914-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="dd914-157">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="dd914-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="dd914-158">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="dd914-158">Spatial sound design</span></span>](spatial-sound-design.md)
