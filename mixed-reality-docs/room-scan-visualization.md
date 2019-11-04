---
title: Raum Scan Visualisierung
description: Anwendungen, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, App-Muster, Entwurf, hololens, Raum Überprüfung, räumliche Zuordnung, Mesh
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437514"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="f3408-104">Raum Scan Visualisierung</span><span class="sxs-lookup"><span data-stu-id="f3408-104">Room scan visualization</span></span>

<span data-ttu-id="f3408-105">Anwendungen, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht.</span><span class="sxs-lookup"><span data-stu-id="f3408-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="f3408-106">Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich überprüft hat.</span><span class="sxs-lookup"><span data-stu-id="f3408-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="f3408-107">Anwendungsentwickler haben mehrere Möglichkeiten, um hilfreiche räumliche Daten zu gewährleisten:</span><span class="sxs-lookup"><span data-stu-id="f3408-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="f3408-108">Verlassen Sie sich darauf, was bereits gesammelt wurde.</span><span class="sxs-lookup"><span data-stu-id="f3408-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="f3408-109">Diese Daten sind anfänglich möglicherweise unvollständig.</span><span class="sxs-lookup"><span data-stu-id="f3408-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="f3408-110">Bitten Sie den Benutzer, mit der aufblühenden Bewegung den Windows Mixed Reality-Start zu verwenden und dann den Bereich zu erkunden, den Sie für die Benutzeroberfläche verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f3408-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="f3408-111">Mithilfe von Air-Tap können Sie überprüfen, ob dem Gerät der gesamte erforderliche Bereich bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="f3408-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="f3408-112">Erstellen Sie eine benutzerdefinierte Erkundung in ihrer eigenen Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f3408-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="f3408-113">Beachten Sie, dass in allen diesen Fällen die während der Durchsuchung gesammelten tatsächlichen Daten vom System gespeichert werden, und die Anwendung muss dies nicht tun.</span><span class="sxs-lookup"><span data-stu-id="f3408-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="f3408-114">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="f3408-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3408-115"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="f3408-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f3408-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3408-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3408-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3408-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3408-118">Raum Scan Visualisierung</span><span class="sxs-lookup"><span data-stu-id="f3408-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="f3408-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f3408-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="f3408-120">Entwickeln eines benutzerdefinierten Scanvorgangs</span><span class="sxs-lookup"><span data-stu-id="f3408-120">Building a custom scanning experience</span></span>

<span data-ttu-id="f3408-121">Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Umgebung analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen muss, um seine Vollständigkeit und Qualität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="f3408-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="f3408-122">Wenn die Analyse anzeigt, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung bereitstellen, um auf der ganzen Welt zu überlagern:</span><span class="sxs-lookup"><span data-stu-id="f3408-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="f3408-123">Der Anteil des Gesamtvolumens in der Benutzer Nähe muss Teil der Benutzerumgebung sein.</span><span class="sxs-lookup"><span data-stu-id="f3408-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="f3408-124">An welcher Stelle der Benutzerdaten verbessern sollte</span><span class="sxs-lookup"><span data-stu-id="f3408-124">Where the user should go to improve data</span></span>

<span data-ttu-id="f3408-125">Benutzer wissen nicht, was einen "guten" Scan vornimmt.</span><span class="sxs-lookup"><span data-stu-id="f3408-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="f3408-126">Sie müssen angezeigt werden, oder Sie müssen wissen, was Sie suchen müssen, wenn Sie aufgefordert werden, eine Überprüfung zu evaluieren – eine flache, eine Entfernung von tatsächlichen Wänden usw. Der Entwickler sollte eine Feedback Schleife implementieren, die das Aktualisieren der räumlichen Daten während der Scan-oder Auswertungs Phase umfasst.</span><span class="sxs-lookup"><span data-stu-id="f3408-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="f3408-127">In vielen Fällen kann es am besten sein, den Benutzern mitzuteilen, was Sie tun müssen (z. b. die Obergrenze, das Aussehen hinter den Möbeln), um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f3408-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="f3408-128">Zwischengespeicherte und fortlaufende räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f3408-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="f3408-129">Die räumlichen Daten sind die Daten, die von den Datenquellen Anwendungen mit hohem Gewicht beansprucht werden können.</span><span class="sxs-lookup"><span data-stu-id="f3408-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="f3408-130">Um Leistungsprobleme zu vermeiden, wie z. b. gelöschte Frames oder stutor-Daten, sollte die Nutzung dieser Daten sorgfältig erfolgen.</span><span class="sxs-lookup"><span data-stu-id="f3408-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="f3408-131">Die aktive Überprüfung während einer-Darstellung kann sowohl vorteilhaft als auch schädlich sein, und der Entwickler muss entscheiden, welche Methode basierend auf der-Methode verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="f3408-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="f3408-132">Zwischengespeicherte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f3408-132">Cached spatial mapping</span></span>

<span data-ttu-id="f3408-133">Bei einer zwischengespeicherten räumlichen Zuordnung erstellt die Anwendung in der Regel eine Momentaufnahme der räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme für die Dauer der Arbeit.</span><span class="sxs-lookup"><span data-stu-id="f3408-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="f3408-134">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="f3408-134">**Benefits**</span></span>
* <span data-ttu-id="f3408-135">Der geringere mehr Aufwand für das System, während die Ausführung ausgeführt wird, führt zu einer enormen Leistungssteigerung, zu Leistungseinbußen und CPU</span><span class="sxs-lookup"><span data-stu-id="f3408-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="f3408-136">Eine einfachere Implementierung des Haupt Erlebnisses, da diese nicht durch Änderungen in den räumlichen Daten unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="f3408-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="f3408-137">Ein einzelner Zeitaufwand für die Verarbeitung räumlicher Daten für Physik, Grafiken und andere Zwecke.</span><span class="sxs-lookup"><span data-stu-id="f3408-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="f3408-138">**Nachteil**</span><span class="sxs-lookup"><span data-stu-id="f3408-138">**Drawbacks**</span></span>
* <span data-ttu-id="f3408-139">Die Verschiebung von realen Objekten oder Personen wird von den zwischengespeicherten Daten nicht widergespiegelt.</span><span class="sxs-lookup"><span data-stu-id="f3408-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="f3408-140">z. B.</span><span class="sxs-lookup"><span data-stu-id="f3408-140">E.g.</span></span> <span data-ttu-id="f3408-141">die Anwendung wird möglicherweise eine Tür geöffnet, wenn Sie jetzt tatsächlich geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="f3408-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="f3408-142">Potenziell mehr Anwendungs Speicher, um die zwischengespeicherte Version der Daten beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="f3408-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="f3408-143">Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Top-Spiel der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="f3408-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="f3408-144">Fortlaufende räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f3408-144">Continuous spatial mapping</span></span>

<span data-ttu-id="f3408-145">Bestimmte Anwendungen verlassen sich möglicherweise auf das Fortsetzen des Scans, um räumliche Daten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f3408-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="f3408-146">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="f3408-146">**Benefits**</span></span>
* <span data-ttu-id="f3408-147">Sie müssen in Ihrer Anwendung nicht in einer separaten Überprüfung oder Durchsuchung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="f3408-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="f3408-148">Die Bewegung von realen Objekten kann durch das Spiel reflektiert werden, obwohl es sich um eine Verzögerung handelt.</span><span class="sxs-lookup"><span data-stu-id="f3408-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="f3408-149">**Nachteil**</span><span class="sxs-lookup"><span data-stu-id="f3408-149">**Drawbacks**</span></span>
* <span data-ttu-id="f3408-150">Höhere Komplexität bei der Implementierung des Haupt Erlebnisses.</span><span class="sxs-lookup"><span data-stu-id="f3408-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="f3408-151">Potenzieller mehr Aufwand für die zusätzliche Verarbeitung von Grafiken oder Physik, da Änderungen von diesen Systemen inkrementell erfasst werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f3408-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="f3408-152">Höhere Stromversorgung, thermische und CPU-Auswirkung.</span><span class="sxs-lookup"><span data-stu-id="f3408-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="f3408-153">Ein guter Fall für diese Methode ist eine Methode, bei der holograms mit verschiebenden Objekten interagieren soll, z. b. Wenn ein Holographic Car, das auf dem Boden ist, möglicherweise korrekt in eine Tür wechselt, je nachdem, ob es geöffnet oder geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="f3408-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3408-154">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f3408-154">See also</span></span>
* [<span data-ttu-id="f3408-155">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="f3408-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="f3408-156">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="f3408-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="f3408-157">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="f3408-157">Spatial sound design</span></span>](spatial-sound-design.md)
