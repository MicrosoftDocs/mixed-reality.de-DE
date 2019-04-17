---
title: 'Fallstudie: erweitern die räumlichen Funktionen für die Zuordnung von HoloLens'
description: Beim Erstellen von unserem ersten apps für Microsoft HoloLens konnten wir sehr daran interessiert, finden, wie weit wir die Grenzen der räumliche Zuordnung auf dem Gerät mithilfe von Push übertragen können.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, räumliche Zuordnung
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595754"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="72323-104">Fallstudie: erweitern die räumlichen Funktionen für die Zuordnung von HoloLens</span><span class="sxs-lookup"><span data-stu-id="72323-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="72323-105">Beim Erstellen von unserem ersten apps für Microsoft HoloLens konnten wir sehr daran interessiert, finden, wie weit wir die Grenzen der räumliche Zuordnung auf dem Gerät mithilfe von Push übertragen können.</span><span class="sxs-lookup"><span data-stu-id="72323-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="72323-106">Jeff Evertt, Software Engineer bei Microsoft Studios, wird erläutert, wie eine neue Technologie entwickelt wurde, aus die Notwendigkeit zur besseren Steuerung, wie Hologramme, in die reale Umgebung des Benutzers platziert werden.</span><span class="sxs-lookup"><span data-stu-id="72323-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="72323-107">Video ansehen</span><span class="sxs-lookup"><span data-stu-id="72323-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="72323-108">Über die räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="72323-108">Beyond spatial mapping</span></span>

<span data-ttu-id="72323-109">Während wir arbeiteten [Fragmente](https://www.microsoft.com/p/fragments/9nblggh5ggm8) und [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), zwei der ersten Spiele für HoloLens, wir festgestellt, dass wenn wir mit Anleitungen Platzierung Hologramme in der realen Welt ausführen, wir eine höhere Sicherheitsstufe erforderlich Kenntnisse über die Umgebung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="72323-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="72323-110">Jedes Spiel musste eine eigene Anforderungen der jeweiligen Platzierung: In Fragmenten, z. B. wollten wir zwischen verschiedenen Oberflächen unterscheiden können, z. B. dem Boden oder eine Tabelle – Hinweise in Orten zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="72323-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="72323-111">Wir wollten auch in der Lage Oberflächen zu identifizieren, die zweifachen der Originalgröße holographic Zeichen, z. B. ein Sofa oder einen Stuhl befinden können.</span><span class="sxs-lookup"><span data-stu-id="72323-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="72323-112">In Conker Young wollten wir Conker und seine Gegner ausgelöste Flächen in des Spielers Raum als Plattformen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="72323-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="72323-113">[Asobo Studios](http://www.asobostudio.com/index.html), unsere Entwicklungspartner dieser Spiele, treffen Sie uns dieses Problem, und erstellt Sie eine Technologie, die die räumlichen Funktionen für die Zuordnung von HoloLens erweitert.</span><span class="sxs-lookup"><span data-stu-id="72323-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="72323-114">Anhand dieser konnten wir Analysieren des Spielers Platz und Oberflächen wie z. B. Wände, Tabellen, Stühle und Stockwerken identifizieren.</span><span class="sxs-lookup"><span data-stu-id="72323-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="72323-115">Auch haben wir die Möglichkeit, anhand einer Reihe von Einschränkungen, um zu bestimmen, den besten Unterbringungsort für holographic Objekte zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="72323-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="72323-116">Der räumliche verstehen von code</span><span class="sxs-lookup"><span data-stu-id="72323-116">The spatial understanding code</span></span>

<span data-ttu-id="72323-117">Wir haben Asobos ursprünglichen Codes und erstellt eine Bibliothek, die diese Technologie kapselt.</span><span class="sxs-lookup"><span data-stu-id="72323-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="72323-118">Microsoft und Asobo jetzt diesen Code als Open Source und auf zur Verfügung gestellt haben [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) in Ihren eigenen Projekten verwenden.</span><span class="sxs-lookup"><span data-stu-id="72323-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="72323-119">Der gesamte Quellcode ist enthalten, sodass Sie an Ihre Anforderungen anpassen und Ihrer Verbesserungen mit der Community teilen.</span><span class="sxs-lookup"><span data-stu-id="72323-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="72323-120">Der Code für die C++ Solver umschlossen in eine UWP-DLL und für Unity mit verfügbar gemacht wurde eine [direkter Prefab MixedRealityToolkit enthaltenen](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="72323-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="72323-121">Es gibt viele nützliche Abfragen, die das Unity-Beispiel, mit denen Sie Leerzeichen Wände finden, fügen Sie Objekte aus, an der Decke oder große Speicherplätze auf dem Boden, stellen für Zeichen befindet und unzählige andere Abfragen räumlicher Grundlegendes zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="72323-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="72323-122">Zwar allgemein genug, um die Anforderungen die gesamte Palette von Problembereiche werden räumliche Zuordnung-Lösung von HoloLens ausgelegt ist, wurde das räumliche Verständnis-Modul erstellt, um die Anforderungen von zwei bestimmte Spiele zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="72323-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="72323-123">Daher ist die Lösung für einen bestimmten Prozess und eine Reihe von Annahmen strukturiert:</span><span class="sxs-lookup"><span data-stu-id="72323-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="72323-124">**Feste Größe Playspace**: Der Benutzer gibt die maximale Playspace-Größe in der Init-Aufruf.</span><span class="sxs-lookup"><span data-stu-id="72323-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="72323-125">**Einmalige Überprüfung**: Der Prozess erfordert eine diskrete Phase, in denen der Benutzer, um führt, zu überprüfen, die Playspace definieren.</span><span class="sxs-lookup"><span data-stu-id="72323-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="72323-126">Abfragefunktionen funktionieren nicht erst, nachdem die Überprüfung abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="72323-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="72323-127">**Benutzergesteuerte Playspace "Zeichnen"**: Während der Überprüfungsphase wird der Benutzer wechselt und sieht sich die Playspace, für die tatsächlich Zeichnen der Bereiche, die einbezogen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="72323-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="72323-128">Das generierte Netz ist wichtig, Feedback von Benutzern bereitzustellen, während dieser Phase.</span><span class="sxs-lookup"><span data-stu-id="72323-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="72323-129">**In geschlossenen Räumen Heim- oder Setup**: Die Abfragefunktionen werden für flache Flächen und Wände rechtwinklig konzipiert.</span><span class="sxs-lookup"><span data-stu-id="72323-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="72323-130">Dies ist eine weiche Einschränkung.</span><span class="sxs-lookup"><span data-stu-id="72323-130">This is a soft limitation.</span></span> <span data-ttu-id="72323-131">Jedoch wird während der Überprüfungsphase, eine Analyse der primären Achse abgeschlossen, um das Netz Mosaik Haupt- und Nebenversionsnummern Achse zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="72323-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="72323-132">Raum Scanningprozess</span><span class="sxs-lookup"><span data-stu-id="72323-132">Room Scanning Process</span></span>

<span data-ttu-id="72323-133">Wenn Sie das Modul räumliche Grundlegendes zu laden, das erste, was Sie tun wird Ihrem Bereich, also die verwendbaren Oberflächen zu überprüfen, wie z. B. die Floor, Ceiling und Wände – identifiziert und gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="72323-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="72323-134">Während des Scanvorgangs, suchen Sie Ihr Platz und "Farbe" der Bereiche, die in die Überprüfung enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="72323-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="72323-135">Das Netz während dieser Phase ist ein wichtiger Bestandteil von visuellem Feedback, mit dem Benutzer wissen, welche Teile des Raums gescannt werden.</span><span class="sxs-lookup"><span data-stu-id="72323-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="72323-136">Die DLL für das räumliche Grundlegendes zu Modul speichert intern die Playspace als ein Raster aus 8cm Größe Voxel Cubes.</span><span class="sxs-lookup"><span data-stu-id="72323-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="72323-137">Während des ersten Teils Scannen ist eine Hauptkomponente Analyse abgeschlossen, um zu bestimmen, die Achsen des Raums.</span><span class="sxs-lookup"><span data-stu-id="72323-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="72323-138">Sie speichert intern Voxel Speicherplatzes ausgerichtet, diese Achsen.</span><span class="sxs-lookup"><span data-stu-id="72323-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="72323-139">Ein Mesh wird ungefähr pro Sekunde generiert, mit dem Extrahieren der Isofläche aus dem Voxel Volume.</span><span class="sxs-lookup"><span data-stu-id="72323-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Räumliche Zuordnung Mesh in Weiß und Verstehen von Playspace mesh in Grün](images/spatial-mapping-500px.png)

<span data-ttu-id="72323-141">Räumliche Zuordnung Mesh in Weiß und Verstehen von Playspace mesh in Grün</span><span class="sxs-lookup"><span data-stu-id="72323-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="72323-142">Der eingebundenen Datei SpatialUnderstanding.cs verwaltet den Scanvorgang-Phase.</span><span class="sxs-lookup"><span data-stu-id="72323-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="72323-143">Es ruft die folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="72323-143">It calls the following functions:</span></span>
* <span data-ttu-id="72323-144">**SpatialUnderstanding_Init**: Am Anfang einmal aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="72323-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="72323-145">**GeneratePlayspace_InitScan**: Gibt an, dass die Scan-Phase beginnen soll.</span><span class="sxs-lookup"><span data-stu-id="72323-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="72323-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Wird aufgerufen, jeden Frame aus, um die Suche zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="72323-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="72323-147">Die Position (Kamera) und die Ausrichtung übergeben wird, und wird für den Playspace zeichnen, oben beschriebenen Prozess verwendet.</span><span class="sxs-lookup"><span data-stu-id="72323-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="72323-148">**GeneratePlayspace_RequestFinish**: Wird aufgerufen, um die Playspace abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="72323-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="72323-149">Hierbei werden die Bereiche "gezeichnet", während der Überprüfung-Phase definieren und die Playspace Sperren verwendet.</span><span class="sxs-lookup"><span data-stu-id="72323-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="72323-150">Statistiken kann von die Anwendung während der Überprüfung Phase sowie Abfrage benutzerdefinierte Mesh für die Bereitstellung von Feedback von Benutzern Abfragen.</span><span class="sxs-lookup"><span data-stu-id="72323-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="72323-151">**Import_UnderstandingMesh**: Während des Scanvorgangs, der **SpatialUnderstandingCustomMesh** Verhalten, die vom Modul bereitgestellt, und klicken Sie auf das Prefab Verständnis platziert wird vom Prozess generierten benutzerdefinierte Mesh in regelmäßigen Abständen abgefragt.</span><span class="sxs-lookup"><span data-stu-id="72323-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="72323-152">Darüber hinaus dies einmal erfolgt nach der Überprüfung beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="72323-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="72323-153">Der Scan Flow, hängt von der **SpatialUnderstanding** Verhaltenaufrufe **InitScan**, klicken Sie dann **UpdateScan** jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="72323-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="72323-154">Wenn die Abfrage Statistiken angemessenen Coverage meldet, wird der Benutzer kann Airtap aufzurufende **RequestFinish** an das Ende der Überprüfungsphase.</span><span class="sxs-lookup"><span data-stu-id="72323-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="72323-155">**UpdateScan** weiterhin aufgerufen werden, bis sie die Rückgabe ist der Wert gibt an, dass die DLL die Verarbeitung abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="72323-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="72323-156">Die Abfragen</span><span class="sxs-lookup"><span data-stu-id="72323-156">The queries</span></span>

<span data-ttu-id="72323-157">Sobald die Überprüfung abgeschlossen ist, werden Sie drei verschiedene Typen von Abfragen in der Benutzeroberfläche zugreifen:</span><span class="sxs-lookup"><span data-stu-id="72323-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="72323-158">**Abfragen der Topologie**: Hierbei handelt es sich um schnelle Abfragen, die auf die Topologie der überprüften Raum basieren.</span><span class="sxs-lookup"><span data-stu-id="72323-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="72323-159">**Form von Abfragen**: Diese nutzen die Ergebnisse der Abfragen Topologie zur horizontalen Oberflächen zu finden, die eine gute Übereinstimmung benutzerdefinierte Formen sind, die Sie definieren.</span><span class="sxs-lookup"><span data-stu-id="72323-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="72323-160">**Objektabfragen für die Platzierung**: Hierbei handelt es sich um eine komplexere Abfragen, die den Fallback mit ähnlichen Speicherort basierend auf einem Satz von Regeln und Einschränkungen für das Objekt zu suchen.</span><span class="sxs-lookup"><span data-stu-id="72323-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="72323-161">Zusätzlich zu den drei primären Abfragen eine feinheiten beim Raycasting Schnittstelle, mit dem markierte Oberflächentypen abgerufen werden kann, und einem benutzerdefinierten wasserdichte Platz Mesh kopiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="72323-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="72323-162">Abfragen der Topologie</span><span class="sxs-lookup"><span data-stu-id="72323-162">Topology queries</span></span>

<span data-ttu-id="72323-163">In der DLL behandelt Topologie-Manager die Bezeichnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="72323-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="72323-164">Wie oben erwähnt, wird ein Großteil der Daten in Surfels, gespeichert, die innerhalb eines Volumes Voxel enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="72323-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="72323-165">Darüber hinaus die **PlaySpaceInfos** Struktur wird zum Speichern von Informationen zu den Playspace, einschließlich der Welt, Ausrichtung (Weitere Einzelheiten hierzu finden Sie nachstehend), Floor und Ceiling Höhe.</span><span class="sxs-lookup"><span data-stu-id="72323-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="72323-166">Heuristik beim Ermitteln der werden verwendet, um zu bestimmen, Floor, Ceiling und Wänden.</span><span class="sxs-lookup"><span data-stu-id="72323-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="72323-167">Beispielsweise gilt die größte und niedrigste horizontale Oberfläche mit mehr als 1 m2 Oberfläche den Boden.</span><span class="sxs-lookup"><span data-stu-id="72323-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="72323-168">Beachten Sie, dass der Pfad "Kamera" während des Scanvorgangs auch in diesem Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="72323-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="72323-169">Eine Teilmenge der Abfragen, die von der Topologie-Manager verfügbar gemacht werden über die DLL bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="72323-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="72323-170">Die verfügbar gemachten Topologie-Abfragen sind wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="72323-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="72323-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="72323-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="72323-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="72323-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="72323-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="72323-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="72323-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="72323-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="72323-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="72323-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="72323-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="72323-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="72323-177">Alle Abfragen verfügt über einen Satz von Parametern, die spezifisch für den Abfragetyp.</span><span class="sxs-lookup"><span data-stu-id="72323-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="72323-178">Im folgenden Beispiel gibt den Benutzer, die minimale Höhe und Breite der gewünschte Volume, minimale Platzierung Höhe über dem Boden und die Mindestmenge an sicherheitsbestätigung vor dem Volume.</span><span class="sxs-lookup"><span data-stu-id="72323-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="72323-179">Alle Messungen sind in Meter.</span><span class="sxs-lookup"><span data-stu-id="72323-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="72323-180">Jeder dieser Abfragen akzeptiert ein vorab zugeordnete Array von **TopologyResult** Strukturen.</span><span class="sxs-lookup"><span data-stu-id="72323-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="72323-181">Die **LocationCount** Parameter gibt die Länge des übergebenen Arrays an.</span><span class="sxs-lookup"><span data-stu-id="72323-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="72323-182">Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="72323-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="72323-183">Diese Zahl ist niemals größer als der übergegebenen **LocationCount** Parameter.</span><span class="sxs-lookup"><span data-stu-id="72323-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="72323-184">Die **TopologyResult** enthält die zentrierte Textposition des zurückgegebenen Volumes, die zugänglichen Richtung (d. h. normal), und die Abmessungen des Bereich gefunden.</span><span class="sxs-lookup"><span data-stu-id="72323-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="72323-185">Beachten Sie, dass in der Unity-Beispiel, jeder dieser Abfragen sich auf eine Schaltfläche in der virtuellen Benutzeroberflächen-Panel verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="72323-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="72323-186">Das Beispiel schwer-codes die Parameter für jede dieser Abfragen für Sie geeignete Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="72323-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="72323-187">Finden Sie unter *SpaceVisualizer.cs* im Beispielcode Weitere Beispiele.</span><span class="sxs-lookup"><span data-stu-id="72323-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="72323-188">Shape-Abfragen</span><span class="sxs-lookup"><span data-stu-id="72323-188">Shape queries</span></span>

<span data-ttu-id="72323-189">Innerhalb der DLL, die dem Shape-Analyzer (**ShapeAnalyzer_W**) verwendet den Topologie-Analyzer für den Abgleich von benutzerdefinierter Formen, die vom Benutzer definiert.</span><span class="sxs-lookup"><span data-stu-id="72323-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="72323-190">Im Unity-Beispiel verfügt über einen vordefinierten Satz von Formen, die Sie im Abfragemenü auf der Registerkarte "Form" gezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="72323-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="72323-191">Beachten Sie, dass die Form-Analyse auf nur horizontale Oberflächen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="72323-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="72323-192">Ein Sofa, wird z. B. durch die Flatfile-Arbeitsplatz-Oberfläche und flache Anfang den Garten wieder definiert.</span><span class="sxs-lookup"><span data-stu-id="72323-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="72323-193">Shape-Abfrage sucht nach zwei Oberflächen von einer bestimmten Größe, Höhe und Aspekt-Bereich mit den beiden Oberflächen ausgerichtet und verbunden.</span><span class="sxs-lookup"><span data-stu-id="72323-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="72323-194">Verwenden die APIs Terminologie, sind Sofa Sitz und dem oberen Rand am Ende den Garten shape-Komponenten und die Ausrichtung, die Anforderungen sind Form Beschränkungen hinsichtlich der Komponenten.</span><span class="sxs-lookup"><span data-stu-id="72323-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="72323-195">Eine Beispielabfrage, die in der Unity-Beispiel definiert (**ShapeDefinition.cs**) für "sittable"-Objekte wie folgt:</span><span class="sxs-lookup"><span data-stu-id="72323-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="72323-196">Jedes Shape-Abfrage wird definiert durch eine Reihe von Komponenten der Form, jeweils eine Reihe von Beschränkungen hinsichtlich der Komponenten und einer Reihe von Form-Einschränkungen, die Abhängigkeiten zwischen den Komponenten aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="72323-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="72323-197">Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponente-Definition und keine Einschränkungen der Form zwischen Komponenten, (wie es nur eine Komponente ist).</span><span class="sxs-lookup"><span data-stu-id="72323-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="72323-198">Im Gegensatz dazu verfügt über die Form Sofa, zwei Shape-Komponenten und Einschränkungen für vier Form.</span><span class="sxs-lookup"><span data-stu-id="72323-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="72323-199">Beachten Sie, dass Komponenten anhand ihres Indexes in der Liste der Komponenten des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="72323-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="72323-200">Wrapperfunktionen werden zur einfachen Erstellung von Definitionen für benutzerdefinierte Form, die im Unity-Modul bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="72323-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="72323-201">Die vollständige Liste der Komponente und Form-Einschränkungen finden Sie **SpatialUnderstandingDll.cs** innerhalb der **ShapeComponentConstraint** und **ShapeConstraint** Strukturen sind.</span><span class="sxs-lookup"><span data-stu-id="72323-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![Das blaue Rechteck hervorgehoben, die Ergebnisse der Stuhl Shape-Abfrage.](images/chair-shape-query-500px.png)

<span data-ttu-id="72323-203">Das blaue Rechteck hervorgehoben, die Ergebnisse der Stuhl Shape-Abfrage.</span><span class="sxs-lookup"><span data-stu-id="72323-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="72323-204">Die Platzierung Solver Objekt</span><span class="sxs-lookup"><span data-stu-id="72323-204">Object placement solver</span></span>

<span data-ttu-id="72323-205">Objektabfragen für die Platzierung können verwendet werden, um ideal Orte im physischen Raum platzieren Ihrer Objekte zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="72323-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="72323-206">Der Solver findet den Fallback mit ähnlichen Speicherort, die Objektregeln und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="72323-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="72323-207">Darüber hinaus Objektabfragen beibehalten, bis das Objekt entfernt wird, mit **Solver_RemoveObject** oder **Solver_RemoveAllObjects** aufrufen, sodass eingeschränkte Platzierung Multi-Objekts.</span><span class="sxs-lookup"><span data-stu-id="72323-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="72323-208">Platzierung von Objektabfragen bestehen aus drei Teilen: die Platzierungstyp mit Parametern, eine Liste der Regeln und eine Liste der Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="72323-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="72323-209">Verwenden Sie zum Ausführen einer Abfrage, die folgende API:</span><span class="sxs-lookup"><span data-stu-id="72323-209">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="72323-210">Diese Funktion akzeptiert ein Objektname, Platzierungsdefinition und eine Liste von Regeln und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="72323-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="72323-211">Die C# Wrapper erstellen-bereitstellen-Hilfsfunktionen, damit die Regel oder Einschränkung Erstellung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="72323-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="72323-212">Die Platzierungsdefinition enthält den Abfragetyp, d. h. eine der folgenden:</span><span class="sxs-lookup"><span data-stu-id="72323-212">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="72323-213">Alle Platzierungstypen, hat es sich um einen Satz von Parametern, die nur für den Typ.</span><span class="sxs-lookup"><span data-stu-id="72323-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="72323-214">Die **ObjectPlacementDefinition** Struktur enthält eine Reihe von statischen Hilfsfunktionen für diese Definitionen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="72323-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="72323-215">Um einer bestimmten Stelle ablegen ein Objekts auf dem Boden zu suchen, können Sie z. B. die folgende Funktion verwenden:</span><span class="sxs-lookup"><span data-stu-id="72323-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="72323-216">Zusätzlich zu die Platzierungstyp können Sie einen Satz von Regeln und Einschränkungen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="72323-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="72323-217">Regeln können nicht verletzt werden.</span><span class="sxs-lookup"><span data-stu-id="72323-217">Rules cannot be violated.</span></span> <span data-ttu-id="72323-218">Mögliche Platzierung von Standorten, die den Typ und die Regeln erfüllen werden dann anhand des Satzes von Einschränkungen, um den Speicherort für die optimale Platzierung auszuwählen optimiert.</span><span class="sxs-lookup"><span data-stu-id="72323-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="72323-219">Alle Regeln und Einschränkungen kann von den Funktionen für die angegebene statische Erstellung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="72323-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="72323-220">Eine Beispiel-Regel und die Einschränkung der Konstruktorfunktion wird unten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="72323-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="72323-221">Die Platzierung-Objektabfrage, die folgenden sucht nach einem Ort zu versetzen, einen Cube Hälfte Verbrauchseinheit am Rand einer Oberfläche, von anderen Objekten zuvor platzieren in der Nähe der Mitte des Raums.</span><span class="sxs-lookup"><span data-stu-id="72323-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="72323-222">Bei erfolgreicher Ausführung einen **ObjectPlacementResult** -Struktur mit der Platzierungsposition, die Dimensionen und die Ausrichtung wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="72323-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="72323-223">Darüber hinaus wird die Platzierung des DLL interne Liste der platzierten Objekte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="72323-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="72323-224">Platzierung der nachfolgenden Abfragen werden dieses Objekt zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="72323-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="72323-225">Die **LevelSolver.cs** -Datei im Unity-Beispiel enthält weitere Beispiele für Abfragen.</span><span class="sxs-lookup"><span data-stu-id="72323-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Die blauen Felder zeigen das Ergebnis von drei direkt auf Floor-Abfragen mit "Weg von der Position (Kamera)" Regeln.](images/away-from-camera-position-500px.png)

<span data-ttu-id="72323-227">Die blauen Felder zeigen das Ergebnis von drei direkt auf Floor-Abfragen mit "Weg von der Position (Kamera)" Regeln.</span><span class="sxs-lookup"><span data-stu-id="72323-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="72323-228">**Tipps:**</span><span class="sxs-lookup"><span data-stu-id="72323-228">**Tips:**</span></span>
* <span data-ttu-id="72323-229">Bei der Lösung für die Platzierung-Speicherort, der mehrere Objekte, die für ein Szenario Ebene oder eine Anwendung erforderlich sind, lösen Sie zuerst unerlässlich, und große Objekte, um die Wahrscheinlichkeit zu maximieren, die ein Leerzeichen befinden.</span><span class="sxs-lookup"><span data-stu-id="72323-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="72323-230">Platzierung Reihenfolge ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="72323-230">Placement order is important.</span></span> <span data-ttu-id="72323-231">Wenn das Objekt Platzierungen nicht gefunden wird, versuchen Sie es weniger eingeschränkte Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="72323-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="72323-232">Eine Reihe von Konfigurationen ist entscheidend für die Unterstützung von Funktionen in vielen Konfigurationen von Platz.</span><span class="sxs-lookup"><span data-stu-id="72323-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="72323-233">Chow Umwandlung</span><span class="sxs-lookup"><span data-stu-id="72323-233">Ray casting</span></span>

<span data-ttu-id="72323-234">Zusätzlich zu den drei primären Abfragen kann eine Chow Umwandlung-Schnittstelle zum Abrufen von markierter Oberflächentypen verwendet werden und einem benutzerdefinierten wasserdichte Playspace Mesh kopiert werden kann, nachdem Raum überprüft und -Kundenbetreuungsteam abgewickelt, Bezeichnungen werden intern generiert für Oberflächen wie die Floor, Ceiling und Wände.</span><span class="sxs-lookup"><span data-stu-id="72323-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="72323-235">Die **PlayspaceRaycast** Funktion akzeptiert ein Strahl und gibt Sie zurück, wenn der Strahl mit einer bekannten Oberfläche verursacht einen Konflikt, und wenn dies der Fall ist, Informationen, die dann in Form einer **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="72323-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="72323-236">Die Raycast wird intern für die berechnete 8 cm hoch drei Voxel Darstellung der Playspace berechnet.</span><span class="sxs-lookup"><span data-stu-id="72323-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="72323-237">Jede Voxel enthält einen Satz von Surface-Elementen mit verarbeiteten Topologiedaten (auch bekannt als Surfels).</span><span class="sxs-lookup"><span data-stu-id="72323-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="72323-238">Die in der Zelle überschneidungen Voxel enthaltenen Surfels verglichen werden, und die beste Übereinstimmung verwendet, um die Topologieinformationen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="72323-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="72323-239">Diese Topologiedaten enthalten die Bezeichnung in der Form des zurückgegebenen der **SurfaceTypes** Enum, sowie die Oberfläche der überschneidungen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="72323-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="72323-240">Im Unity-Beispiel wird der Cursor jeder Frame ein Strahl umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="72323-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="72323-241">Zunächst anhand von Unity-collider; Zweitens: für das Verständnis des Moduls-Welt-Darstellung; und schließlich für die Elemente der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="72323-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="72323-242">In dieser Anwendung ruft ab die Benutzeroberfläche, Priorität, und klicken Sie dann das Ergebnis verstehen und schließlich von Unity-collider.</span><span class="sxs-lookup"><span data-stu-id="72323-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="72323-243">Die **SurfaceType** wird als Text neben dem Cursor gemeldet.</span><span class="sxs-lookup"><span data-stu-id="72323-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast Ergebnisse Schnittmenge mit dem Boden.](images/raycast-result-500px.jpg)

<span data-ttu-id="72323-245">Raycast Ergebnisse Schnittmenge mit dem Boden.</span><span class="sxs-lookup"><span data-stu-id="72323-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="72323-246">Code abrufen</span><span class="sxs-lookup"><span data-stu-id="72323-246">Get the code</span></span>

<span data-ttu-id="72323-247">Der Open-Source-Code ist verfügbar in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="72323-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="72323-248">Lassen Sie uns auf die [HoloLens-Entwicklerforen](https://forums.hololens.com/) , wenn Sie den Code in einem Projekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="72323-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="72323-249">Wir können nicht warten, um festzustellen, was Sie damit tun!</span><span class="sxs-lookup"><span data-stu-id="72323-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="72323-250">Der Autor</span><span class="sxs-lookup"><span data-stu-id="72323-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="72323-251"><b>Jeff Evertt</b> ist leitender Softwareentwicklung, der seit den Anfängen von Inkubation in die Entwicklung für HoloLens gearbeitet hat.</span><span class="sxs-lookup"><span data-stu-id="72323-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="72323-252">Bevor Sie HoloLens arbeitete er auf der Xbox Kinect und in der Branche Spiele auf einer Vielzahl von Plattformen und Spiele.</span><span class="sxs-lookup"><span data-stu-id="72323-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="72323-253">Tyge ist Leidenschaft Robotics, Grafiken und Aufgaben mit blinkenden Lichter, die akustisches Signal gesendet.</span><span class="sxs-lookup"><span data-stu-id="72323-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="72323-254">Er genießt neue Dinge lernen, und arbeiten auf Software, Hardware, und zwar insbesondere in den Speicherplatz, auf denen sich die beiden überschneiden.</span><span class="sxs-lookup"><span data-stu-id="72323-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="72323-255">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="72323-255">See also</span></span>
* [<span data-ttu-id="72323-256">Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="72323-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="72323-257">Räumliche Zuordnung entwerfen</span><span class="sxs-lookup"><span data-stu-id="72323-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="72323-258">Die Überprüfung Visualisierung Platz</span><span class="sxs-lookup"><span data-stu-id="72323-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="72323-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="72323-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="72323-260">Asobo Studio: Lektionen aus dem Front der Entwicklung für HoloLens</span><span class="sxs-lookup"><span data-stu-id="72323-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
