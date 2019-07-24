---
title: 'Fallstudie: Erweitern der räumlichen Mapping-Funktionen von hololens'
description: Beim Erstellen unserer ersten Apps für Microsoft hololens waren wir gespannt darauf zu sehen, wie weit wir die Grenzen der räumlichen Zuordnung auf dem Gerät Übertragung konnten.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, räumliche Zuordnung
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522692"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="7fd4c-104">Fallstudie: Erweitern der räumlichen Mapping-Funktionen von hololens</span><span class="sxs-lookup"><span data-stu-id="7fd4c-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="7fd4c-105">Beim Erstellen unserer ersten Apps für Microsoft hololens waren wir gespannt darauf zu sehen, wie weit wir die Grenzen der räumlichen Zuordnung auf dem Gerät Übertragung konnten.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="7fd4c-106">Jeff evertt, ein Softwareentwickler bei Microsoft Studio, erläutert, wie eine neue Technologie entwickelt wurde, um mehr Kontrolle über die Platzierung von holograms in der realen Umgebung eines Benutzers zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="7fd4c-107">Video ansehen</span><span class="sxs-lookup"><span data-stu-id="7fd4c-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="7fd4c-108">Über räumliche Zuordnung hinaus</span><span class="sxs-lookup"><span data-stu-id="7fd4c-108">Beyond spatial mapping</span></span>

<span data-ttu-id="7fd4c-109">Beim Arbeiten an [Fragmenten](https://www.microsoft.com/p/fragments/9nblggh5ggm8) und [jungen](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)den ersten spielen für hololens stellten wir fest, dass wir bei der prozeduralen Platzierung von holograms in der physischen Welt ein höheres Maß an Kenntnissen benötigten. Umgebung.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="7fd4c-110">Jedes Spiel hat seine eigenen speziellen Platzierungs Anforderungen: In Fragmenten soll beispielsweise zwischen verschiedenen Oberflächen – z. b. dem Boden oder einer Tabelle – unterschieden werden können, um Anhaltspunkte an relevanten Orten zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="7fd4c-111">Wir wollten auch in der Lage sein, Oberflächen zu identifizieren, auf denen holografische Zeichen in der Größe, z. b. ein Couch oder ein Stuhl, angeordnet werden können.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="7fd4c-112">Wir wollten, dass sich der zusammengesetzte und seine Angreifer in der Groß-und klein Sprache eines Players als Plattformen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="7fd4c-113">[Asobo Studio](http://www.asobostudio.com/index.html), unser Entwicklungspartner für diese Spiele, stieß auf dieses Problem und erstellte eine Technologie, die die räumlichen Zuordnungsfunktionen von hololens erweitert.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="7fd4c-114">Dabei konnten wir den Raum eines Players analysieren und Oberflächen wie Wände, Tabellen, Stühle und Fußböden identifizieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="7fd4c-115">Außerdem haben wir die Möglichkeit, eine Reihe von Einschränkungen zu optimieren, um die beste Platzierung für Holographic-Objekte zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="7fd4c-116">Der räumliche Verständnis Code</span><span class="sxs-lookup"><span data-stu-id="7fd4c-116">The spatial understanding code</span></span>

<span data-ttu-id="7fd4c-117">Wir haben den ursprünglichen Code von Asobo erstellt und eine Bibliothek erstellt, die diese Technologie kapselt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="7fd4c-118">Microsoft und Asobo haben nun diesen Code geöffnet und auf [mixedrealitytoolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) zur Verfügung gestellt, sodass Sie Sie in ihren eigenen Projekten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="7fd4c-119">Der gesamte Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und die Verbesserungen für die Community freigeben können.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="7fd4c-120">Der Code für den C++ Solver wurde in eine UWP-dll umschließt und Unity mit einem in [mixedrealitytoolkit enthaltenen Drop-in-Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="7fd4c-121">Im Unity-Beispiel sind viele nützliche Abfragen enthalten, die es Ihnen ermöglichen, leere Leerzeichen auf Wänden zu finden, Objekte an der Oberfläche zu platzieren, Objekte auf der Oberfläche zu platzieren, Positionen für die Platzierung von Zeichen zu ermitteln und unzählige andere Abfragen für räumliche Abfragen durchzusetzen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="7fd4c-122">Die von hololens bereitgestellte räumliche Mappinglösung ist so konzipiert, dass Sie so generisch genug ist, dass Sie die Anforderungen der gesamten Bereiche von Problembereichen erfüllt, das räumliche Verständnis Modul wurde erstellt, um die Anforderungen von zwei bestimmten spielen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="7fd4c-123">Daher wird die Lösung um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="7fd4c-124">**Playspace mit fester Größe**: Der Benutzer gibt die maximale Wiedergabe leergröße im Init-Befehl an.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="7fd4c-125">**Einmal Scanvorgang**: Der Prozess erfordert eine diskrete Überprüfungsphase, bei der der Benutzer durchläuft und den Playspace definiert.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="7fd4c-126">Abfragefunktionen funktionieren erst, nachdem die Überprüfung abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="7fd4c-127">**Benutzergesteuerte Playspace-"zeichnen"** : Während der Überprüfungsphase wird der Benutzer die Wiedergabe Fläche bewegt und durchsucht. Dadurch werden die Bereiche, die eingeschlossen werden sollen, tatsächlich gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="7fd4c-128">Das generierte Mesh ist wichtig, um Benutzer Feedback in dieser Phase bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="7fd4c-129">**Startseite oder Office-Setup**: Die Abfragefunktionen werden um flache Flächen und Wände in der rechten Ecke entworfen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="7fd4c-130">Dies ist eine weiche Einschränkung.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-130">This is a soft limitation.</span></span> <span data-ttu-id="7fd4c-131">Während der Scan Phase wird jedoch eine primäre Achsen Analyse abgeschlossen, um das Gitter Mosaik entlang der Haupt-und der Nebenachse zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="7fd4c-132">Raum Scanprozess</span><span class="sxs-lookup"><span data-stu-id="7fd4c-132">Room Scanning Process</span></span>

<span data-ttu-id="7fd4c-133">Wenn Sie das Modul für räumliche Kenntnisse laden, müssen Sie zuerst Ihren Platz überprüfen, sodass alle verwendbaren Oberflächen, – z. b. die Boden-, Ceiling-und Wände –, identifiziert und gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="7fd4c-134">Während des Scanvorgangs sehen Sie sich Ihren Raum an und zeichnen die Bereiche, die in die Überprüfung eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="7fd4c-135">Das Mesh, das in dieser Phase gesehen wird, ist ein wichtiges visuelles Feedback, mit dem Benutzer wissen können, welche Teile des Raums gescannt werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="7fd4c-136">Die DLL für das Spatial Understanding-Modul speichert den Playspace intern als Raster von Voxel-Cubes mit 8 cm.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="7fd4c-137">Während des ersten Teils der Überprüfung wird eine Analyse der primären Komponenten abgeschlossen, um die Achsen des Raums zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="7fd4c-138">Intern speichert Sie seinen Voxel-Bereich, der auf diese Achsen ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="7fd4c-139">Ein Mesh wird ungefähr jede Sekunde generiert, indem die Isofläche aus dem Voxel-Volume extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Räumliche Zuordnung in weiß und verstehen des Playspace-Mesh in grün](images/spatial-mapping-500px.png)

<span data-ttu-id="7fd4c-141">Räumliche Zuordnung in weiß und verstehen des Playspace-Mesh in grün</span><span class="sxs-lookup"><span data-stu-id="7fd4c-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="7fd4c-142">Die enthaltene SpatialUnderstanding.cs-Datei verwaltet den Scan Phasen Prozess.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="7fd4c-143">Die folgenden Funktionen werden aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-143">It calls the following functions:</span></span>
* <span data-ttu-id="7fd4c-144">**SpatialUnderstanding_Init**: Wird einmal am Anfang aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="7fd4c-145">**GeneratePlayspace_InitScan**: Gibt an, dass die scanphase beginnen soll.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="7fd4c-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Wird jedes Frame aufgerufen, um den Scanvorgang zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="7fd4c-147">Die Kameraposition und-Ausrichtung wird weitergegeben und wird für den oben beschriebenen Zeichnungsprozess von Playspace verwendet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="7fd4c-148">**GeneratePlayspace_RequestFinish**: Wird aufgerufen, um den Playspace abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="7fd4c-149">Dabei werden die Bereiche "gezeichnet" während der Überprüfungsphase verwendet, um den Playspace zu definieren und zu sperren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="7fd4c-150">Die Anwendung kann während der Überprüfungsphase Statistiken Abfragen und das benutzerdefinierte Mesh zum Bereitstellen von Benutzer Feedback Abfragen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="7fd4c-151">**Import_UnderstandingMesh**: Während der Überprüfung fragt das von dem-Modul bereitgestellte **spatialverhalingcustommesh** -Verhalten und das Einverständnis der Prefab in regelmäßigen Abständen das vom Prozess generierte benutzerdefinierte Mesh ab.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="7fd4c-152">Außerdem wird dies nach Abschluss der Überprüfung noch einmal durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="7fd4c-153">Der Scanvorgang, der vom **spatialunderstanding** -Verhalten gesteuert wird, ruft **initscan**auf und **aktualisiert** dann jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="7fd4c-154">Wenn die Statistik Abfrage eine angemessene Abdeckung meldet, kann der Benutzer auf " **requestfinish** " antippen, um das Ende der Scan Phase anzugeben.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="7fd4c-155">**Updatescan** wird weiterhin aufgerufen, bis der Rückgabewert angibt, dass die dll die Verarbeitung abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="7fd4c-156">Die Abfragen</span><span class="sxs-lookup"><span data-stu-id="7fd4c-156">The queries</span></span>

<span data-ttu-id="7fd4c-157">Nachdem die Überprüfung durchgeführt wurde, können Sie auf drei verschiedene Arten von Abfragen in der Schnittstelle zugreifen:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="7fd4c-158">**Topologieabfragen**: Dabei handelt es sich um schnelle Abfragen, die auf der Topologie des gescannten Raums basieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="7fd4c-159">**Shape-Abfragen**: Diese verwenden die Ergebnisse der Topologieabfragen, um horizontale Oberflächen zu suchen, die für benutzerdefinierte Formen geeignet sind, die Sie definieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="7fd4c-160">**Objekt Platzierungs Abfragen**: Dabei handelt es sich um komplexere Abfragen, die die am besten geeignete Position basierend auf einem Satz von Regeln und Einschränkungen für das Objekt finden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="7fd4c-161">Zusätzlich zu den drei primären Abfragen gibt es eine Raycasting-Schnittstelle, die verwendet werden kann, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes wasserdichtes Raum Mesh kann kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="7fd4c-162">Topologieabfragen</span><span class="sxs-lookup"><span data-stu-id="7fd4c-162">Topology queries</span></span>

<span data-ttu-id="7fd4c-163">Innerhalb der DLL übernimmt der topologiemanager die Bezeichnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="7fd4c-164">Wie bereits erwähnt, werden viele der Daten in Surfels gespeichert, die in einem Voxel-Volume enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="7fd4c-165">Außerdem wird die **playspaceinfos** -Struktur zum Speichern von Informationen über den Playspace verwendet, einschließlich der Welt Ausrichtung (weitere Details hierzu finden Sie unten), der Boden-und der Ceiling-Höhe.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="7fd4c-166">Heuristiken werden zum Bestimmen von Boden, Ceiling und Wänden verwendet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="7fd4c-167">Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Größe von mehr als 1 m2 als Floor betrachtet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="7fd4c-168">Beachten Sie, dass der Kamerapfad während des Scanvorgangs auch in diesem Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="7fd4c-169">Eine Teilmenge der Abfragen, die vom topologiemanager verfügbar gemacht werden, wird über die dll verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="7fd4c-170">Die verfügbar gemachten Topologieabfragen lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="7fd4c-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="7fd4c-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="7fd4c-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="7fd4c-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="7fd4c-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="7fd4c-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="7fd4c-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="7fd4c-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="7fd4c-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="7fd4c-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="7fd4c-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="7fd4c-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="7fd4c-177">Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="7fd4c-178">Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die minimale Platzierungs Höhe oberhalb der Etage und den minimalen Abstand vor dem Volume an.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="7fd4c-179">Alle Messungen befinden sich in Meter.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="7fd4c-180">Jede dieser Abfragen nimmt ein vorab zugeordenes Array von **topologyresult** -Strukturen an.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="7fd4c-181">Der **locationcount** -Parameter gibt die Länge des übergebenen Arrays an.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="7fd4c-182">Der Rückgabewert meldet die Anzahl der zurückgegebenen Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="7fd4c-183">Diese Zahl ist nie größer als der übergebenen **locationcount** -Parameter.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="7fd4c-184">Das **topologyresult** enthält die Mittelpunkt Position des zurückgegebenen Volumes, die Richtung (d. h. Normal) und die Dimensionen des gefundenen Speicherplatzes.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="7fd4c-185">Beachten Sie, dass im Unity-Beispiel jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="7fd4c-186">Im Beispiel werden die Parameter für jede dieser Abfragen in angemessene Werte fest codiert.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="7fd4c-187">Weitere Beispiele finden Sie unter *SpaceVisualizer.cs* im Beispielcode.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="7fd4c-188">Shape-Abfragen</span><span class="sxs-lookup"><span data-stu-id="7fd4c-188">Shape queries</span></span>

<span data-ttu-id="7fd4c-189">Innerhalb der dll verwendet der Shape Analyzer (**ShapeAnalyzer_W**) die topologieanalyse, um mit den vom benutzerdefinierten benutzerdefinierten Formen zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="7fd4c-190">Das Unity-Beispiel verfügt über eine vordefinierte Gruppe von Formen, die im Menü Abfrage auf der Registerkarte Form angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="7fd4c-191">Beachten Sie, dass die Formanalyse nur auf horizontalen Oberflächen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="7fd4c-192">Eine Couch wird z. b. durch die flache Arbeitsplatz Oberfläche und den flachen oberen Rand der Couch zurückgelegt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="7fd4c-193">Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, wobei die beiden Oberflächen ausgerichtet und verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="7fd4c-194">Mithilfe der APIs-Terminologie sind der Couch-und der obere Rand des Couch Form Komponenten, und die Ausrichtungs Anforderungen sind Shape-Komponenten Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="7fd4c-195">Eine Beispiel Abfrage, die im Unity-Beispiel (**ShapeDefinition.cs**) für "sitfähige" Objekte definiert ist, lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="7fd4c-196">Jede Shape-Abfrage wird durch einen Satz von Form Komponenten definiert, die jeweils über einen Satz von Komponenten Einschränkungen und einen Satz von Form Einschränkungen verfügen, der Abhängigkeiten zwischen den Komponenten auflistet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="7fd4c-197">Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponenten Definition und keine Formen Einschränkungen zwischen Komponenten (da nur eine Komponente vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="7fd4c-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="7fd4c-198">Im Gegensatz dazu hat die Form "Couch" zwei Form Komponenten und vier Form Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="7fd4c-199">Beachten Sie, dass die Komponenten durch ihren Index in der Komponentenliste des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="7fd4c-200">Wrapper Funktionen werden im Unity-Modul bereitgestellt, um eine einfache Erstellung benutzerdefinierter Formen Definitionen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="7fd4c-201">Die vollständige Liste der Komponenten-und Shape-Einschränkungen finden Sie in **SpatialUnderstandingDll.cs** innerhalb der **shapecomponenteinschränkung** und der **shapeconstraint** -Strukturen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![Mit dem blauen Rechteck werden die Ergebnisse der Form Abfrage "Stuhl" hervorgehoben.](images/chair-shape-query-500px.png)

<span data-ttu-id="7fd4c-203">Mit dem blauen Rechteck werden die Ergebnisse der Form Abfrage "Stuhl" hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="7fd4c-204">Objektplatzierungs-Solver</span><span class="sxs-lookup"><span data-stu-id="7fd4c-204">Object placement solver</span></span>

<span data-ttu-id="7fd4c-205">Objekt Platzierungs Abfragen können verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, um die Objekte zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="7fd4c-206">Der Solver findet den Standort mit der optimalen Anpassung anhand der Objekt Regeln und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="7fd4c-207">Außerdem bleiben Objekt Abfragen so lange erhalten, bis das Objekt mit **Solver_RemoveObject** -oder **Solver_RemoveAllObjects** -aufrufen entfernt wird, sodass die eingeschränkte Platzierung von mehreren Objekten ermöglicht wird.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="7fd4c-208">Objekt Platzierungs Abfragen bestehen aus drei Teilen: Platzierungs Typ mit Parametern, eine Liste von Regeln und eine Liste von Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="7fd4c-209">Verwenden Sie die folgende API, um eine Abfrage auszuführen:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-209">To run a query, use the following API:</span></span>




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
<span data-ttu-id="7fd4c-210">Diese Funktion nimmt einen Objektnamen, eine Platzierungs Definition und eine Liste von Regeln und Einschränkungen an.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="7fd4c-211">Die C# Wrapper stellen Konstruktions Hilfsfunktionen zur Verfügung, um die Erstellung von Regeln und Einschränkungen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="7fd4c-212">Die Platzierungs Definition enthält den Abfragetyp – d. h. einen der folgenden:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-212">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="7fd4c-213">Jeder der Platzierungs Typen hat eine Reihe von Parametern, die für den Typ eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="7fd4c-214">Die **objectplacementdefinition** -Struktur enthält einen Satz statischer Hilfsfunktionen zum Erstellen dieser Definitionen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="7fd4c-215">Wenn Sie z. b. einen Speicherort zum Platzieren eines Objekts im Boden finden möchten, können Sie die folgende Funktion verwenden:</span><span class="sxs-lookup"><span data-stu-id="7fd4c-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="7fd4c-216">Zusätzlich zum Platzierungs Typ können Sie einen Satz von Regeln und Einschränkungen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="7fd4c-217">Regeln können nicht verletzt werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-217">Rules cannot be violated.</span></span> <span data-ttu-id="7fd4c-218">Mögliche Platzierungs Speicherorte, die den Typ und die Regeln erfüllen, werden dann anhand des Satzes von Einschränkungen optimiert, um den optimalen Speicherort für die Platzierung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="7fd4c-219">Alle Regeln und Einschränkungen können von den bereitgestellten statischen Erstellungs Funktionen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="7fd4c-220">Eine Beispiel Regel und eine Einschränkungs Erstellungs Funktion finden Sie unten.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="7fd4c-221">Die nachstehende Objekt Platzierungs Abfrage sucht nach einem Ort, an dem der Rand einer Oberfläche von anderen zuvor angehalgten Objekten und nahe der Mitte des Raums entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="7fd4c-222">Bei erfolgreicher Ausführung wird eine **objectplacementresult** -Struktur mit der Platzierungsposition, den Dimensionen und der Ausrichtung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="7fd4c-223">Außerdem wird die Platzierung der internen Liste der platzierten Objekte der dll hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="7fd4c-224">Bei nachfolgenden Platzierungs Abfragen wird dieses Objekt berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="7fd4c-225">Die **LevelSolver.cs** -Datei im Unity-Beispiel enthält weitere Beispielabfragen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![In den blauen Feldern wird das Ergebnis von drei Stellen in Floor-Abfragen mit der Regel "Weg von der Kameraposition" angezeigt.](images/away-from-camera-position-500px.png)

<span data-ttu-id="7fd4c-227">In den blauen Feldern wird das Ergebnis von drei Stellen in Floor-Abfragen mit der Regel "Weg von der Kameraposition" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="7fd4c-228">**Chti**</span><span class="sxs-lookup"><span data-stu-id="7fd4c-228">**Tips:**</span></span>
* <span data-ttu-id="7fd4c-229">Wenn Sie den Speicherort für die Platzierung mehrerer für ein ebenenszenario oder ein Anwendungsszenario benötigtes Objekte auflösen, lösen Sie zunächst unentbehrliche und große Objekte aus, um die Wahrscheinlichkeit zu maximieren, dass ein Speicherplatz</span><span class="sxs-lookup"><span data-stu-id="7fd4c-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="7fd4c-230">Die Platzierungs Reihenfolge ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-230">Placement order is important.</span></span> <span data-ttu-id="7fd4c-231">Wenn die Platzierung von Objekten nicht gefunden werden kann, versuchen Sie es mit weniger eingeschränkten Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="7fd4c-232">Eine Reihe von Fall Back Konfigurationen ist wichtig für die Unterstützung von Funktionen in vielen Raum Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="7fd4c-233">Strahl Umwandlung</span><span class="sxs-lookup"><span data-stu-id="7fd4c-233">Ray casting</span></span>

<span data-ttu-id="7fd4c-234">Zusätzlich zu den drei primären Abfragen kann eine Strahl Umwandlungs Schnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes, wasserdichtes Playspace-Mesh kann nach dem Scannen und Fertigstellen des Raums kopiert werden. Bezeichnungen werden intern für Oberflächen wie die Fußboden, Ceiling und Wände.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="7fd4c-235">Die **playspaceraycast** -Funktion nimmt einen Strahl an und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert. wenn dies der Fall ist, werden Informationen über diese Oberfläche in Form von " **raycastresult**" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="7fd4c-236">Intern wird der raycast anhand der berechneten Voxel-Darstellung im 8cm-Format des Playspace berechnet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="7fd4c-237">Jeder Voxel enthält einen Satz von Oberflächenelementen mit verarbeiteten Topologiedaten (auch als Surfels bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="7fd4c-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="7fd4c-238">Der Surfels, der in der überschneidenden Voxel-Zelle enthalten ist, wird verglichen und die beste Entsprechung für die Suche nach den Topologieinformationen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="7fd4c-239">Diese Topologieinformationen enthalten die Bezeichnung, die in Form der **surfacetypes** -Aufzählung zurückgegeben wird, sowie den Oberflächen Bereich der überschneidenden Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="7fd4c-240">Im Unity-Beispiel wandelt der Cursor einen Strahl in jedem Frame um.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="7fd4c-241">Zuerst für Unity-Kollisionen; Zweitens, mit der Welt Darstellung des Understanding-Moduls und schließlich für die Elemente der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="7fd4c-242">In dieser Anwendung erhält die Benutzeroberfläche Priorität, dann das Verständnis Ergebnis und schließlich Unity-Kollisionen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="7fd4c-243">Der **surfaketype** wird als Text neben dem Cursor gemeldet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Schnittmenge der raycast-ergebnisberichterstattung mit dem Boden.](images/raycast-result-500px.jpg)

<span data-ttu-id="7fd4c-245">Schnittmenge der raycast-ergebnisberichterstattung mit dem Boden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="7fd4c-246">Abrufen des Codes</span><span class="sxs-lookup"><span data-stu-id="7fd4c-246">Get the code</span></span>

<span data-ttu-id="7fd4c-247">Der Open Source-Code ist in [mixedrealitytoolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="7fd4c-248">Informieren Sie uns in den [hololens-Entwickler Foren](https://forums.hololens.com/) , wenn Sie den Code in einem Projekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="7fd4c-249">Wir können nicht warten, um zu sehen, was Sie mit Ihnen tun!</span><span class="sxs-lookup"><span data-stu-id="7fd4c-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="7fd4c-250">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="7fd4c-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="7fd4c-251"><b>Jeff evertt</b> ist ein Software Entwicklungsleiter, der seit den frühen Tagen an hololens gearbeitet hat, von der Inkubation bis hin zur Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="7fd4c-252">Vor hololens arbeitete er an der Xbox kinect und in der Spielebranche auf einer Vielzahl von Plattformen und spielen.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="7fd4c-253">Jeff ist mit der Robotik, Grafik und den Dingen mit den Beleuchtung von Beleuchtung ausgestattet.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="7fd4c-254">Er lernt neue Dinge und arbeitet an Software, Hardware und besonders in dem Bereich, in dem sich die beiden überschneiden.</span><span class="sxs-lookup"><span data-stu-id="7fd4c-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="7fd4c-255">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7fd4c-255">See also</span></span>
* [<span data-ttu-id="7fd4c-256">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="7fd4c-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="7fd4c-257">Gestaltung von räumlicher Abbildung</span><span class="sxs-lookup"><span data-stu-id="7fd4c-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="7fd4c-258">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="7fd4c-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="7fd4c-259">Mixedrealitytoolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="7fd4c-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="7fd4c-260">Asobo Studio: Lektionen aus der an vorderster Front der hololens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="7fd4c-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
