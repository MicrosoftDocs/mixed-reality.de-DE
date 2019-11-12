---
title: App-Qualitätskriterien
description: In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, gemischte Realität, Mixed Reality-App
ms.openlocfilehash: d167e141b536f9247d22e40afefa718ecc399f5a
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926589"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="4efd5-104">App-Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-104">App quality criteria</span></span>

<span data-ttu-id="4efd5-105">In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.</span><span class="sxs-lookup"><span data-stu-id="4efd5-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="4efd5-106">Für jeden Faktor werden die folgenden Informationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="4efd5-107">Übersicht – eine kurze Beschreibung des Qualitäts Faktors und deren Wichtigkeit.</span><span class="sxs-lookup"><span data-stu-id="4efd5-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="4efd5-108">Geräte Auswirkung: der Typ des Windows Mixed Reality-Geräts ist beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="4efd5-109">Qualitätskriterien – Auswerten des Qualitäts Faktors.</span><span class="sxs-lookup"><span data-stu-id="4efd5-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="4efd5-110">So messen Sie –-Methoden, um das Problem zu messen (oder zu erleben).</span><span class="sxs-lookup"><span data-stu-id="4efd5-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="4efd5-111">Empfehlungen – Zusammenfassung der Ansätze, um eine bessere Benutzer Leistung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="4efd5-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="4efd5-112">Ressourcen – relevante Entwickler-und Entwurfs Ressourcen, die nützlich sind, um bessere App-Erfahrungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="4efd5-113">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="4efd5-113">Frame rate</span></span>

<span data-ttu-id="4efd5-114">Die Framerate ist die erste Säule der – Hologramm-Stabilität und des Benutzer Komforts.</span><span class="sxs-lookup"><span data-stu-id="4efd5-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="4efd5-115">Die Frame Rate unterhalb der empfohlenen Ziele kann dazu führen, dass holograms Jittery werden, was sich negativ auf die glaub Fähigkeit der Funktionalität auswirkt und möglicherweise Augen Müdigkeit auslöst.</span><span class="sxs-lookup"><span data-stu-id="4efd5-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="4efd5-116">Die zielframeworkrate für Ihre Benutzeroberflächen in Windows Mixed Reality-immersiven Headsets ist entweder 60Hz oder 90Hz, je nachdem, welche Windows Mixed Reality-kompatiblen PCs Sie unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="4efd5-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="4efd5-117">Bei hololens beträgt die zielframeworkrate 60Hz.</span><span class="sxs-lookup"><span data-stu-id="4efd5-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-118">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-121">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-121">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-122">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-123">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-123">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-124">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-124">Best</span></span>  |  <span data-ttu-id="4efd5-125">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-125">Meets</span></span> |  <span data-ttu-id="4efd5-126">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="4efd5-127">Die APP erfüllt konstant Frames pro Sekunde (fps) für Zielgerät: 60fps on hololens; 90fps auf ultrapcs; und 60fps auf gängigen PCs.</span><span class="sxs-lookup"><span data-stu-id="4efd5-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="4efd5-128">Die APP verfügt über zeitweilig auftretende Frame-Abstürze, die die Kernfunktionen nicht behindern. oder FPS ist konstant niedriger als das gewünschte Ziel, verhindert jedoch die APP-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="4efd5-129">In der APP tritt im Durchschnitt alle zehn Sekunden eine Dropdown-Rate auf.</span><span class="sxs-lookup"><span data-stu-id="4efd5-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-130">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-130">How to measure</span></span>

* <span data-ttu-id="4efd5-131">Ein Echtzeit-Frameraten Diagramm wird durch das [Windows-Geräte Portal](using-the-windows-device-portal.md#system-performance) unter "System Leistung" bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="4efd5-132">Fügen Sie für das Entwicklungs Debuggen der APP einen framerraten-diagnosecounter hinzu.</span><span class="sxs-lookup"><span data-stu-id="4efd5-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="4efd5-133">Einen Beispiel Zählers finden Sie unter Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="4efd5-134">Die abfrageate können auf dem Gerät auftreten, während die app ausgeführt wird, indem Sie Ihren Kopf von der Seite zu Seite wechseln.</span><span class="sxs-lookup"><span data-stu-id="4efd5-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="4efd5-135">Wenn das – Hologramm unerwartete gezittert-Bewegung anzeigt, ist die niedrige Framerate oder die Stabilitäts Ebene wahrscheinlich die Ursache.</span><span class="sxs-lookup"><span data-stu-id="4efd5-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-136">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-136">Recommendations</span></span>

* <span data-ttu-id="4efd5-137">Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.</span><span class="sxs-lookup"><span data-stu-id="4efd5-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="4efd5-138">Änderungen, die eine Ablage in der Framerate verursachen, sollten ausgewertet und als Leistungsfehler entsprechend aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-139">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-140">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-140">Documentation</span></span>

* [<span data-ttu-id="4efd5-141">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="4efd5-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4efd5-142">Hologram Stabilität und Framerate</span><span class="sxs-lookup"><span data-stu-id="4efd5-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="4efd5-143">Asset Performance Budget</span><span class="sxs-lookup"><span data-stu-id="4efd5-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="4efd5-144">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-145">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-145">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-146">Mrtoolkit, FPS-Counter-Anzeige</span><span class="sxs-lookup"><span data-stu-id="4efd5-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="4efd5-147">Mrtoolkit, Shaders</span><span class="sxs-lookup"><span data-stu-id="4efd5-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="4efd5-148">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="4efd5-148">External references</span></span>

* [<span data-ttu-id="4efd5-149">Unity, optimieren mobiler Anwendungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="4efd5-150">Hologram-Stabilität</span><span class="sxs-lookup"><span data-stu-id="4efd5-150">Hologram stability</span></span>

<span data-ttu-id="4efd5-151">Stabile Hologramme verbessern die Benutzerfreundlichkeit und Glaubwürdigkeit Ihrer APP und sorgen für einen komfortableren Anzeige Vorgang für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4efd5-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="4efd5-152">Die Qualität der – Hologramm-Stabilität ist das Ergebnis einer guten App-Entwicklung und der Fähigkeit des Geräts, die Umgebung zu verstehen (nachverfolgen).</span><span class="sxs-lookup"><span data-stu-id="4efd5-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="4efd5-153">Obwohl die Framerate die erste Säule der Stabilität ist, können sich andere Faktoren auf die Stabilität auswirken, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="4efd5-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="4efd5-154">Verwendung der Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="4efd5-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="4efd5-155">Entfernung zu räumlichen Ankern</span><span class="sxs-lookup"><span data-stu-id="4efd5-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="4efd5-156">Paletten</span><span class="sxs-lookup"><span data-stu-id="4efd5-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-157">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-160">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-161">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-161">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-162">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-162">Best</span></span>  |  <span data-ttu-id="4efd5-163">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-163">Meets</span></span> |  <span data-ttu-id="4efd5-164">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-165">Holograms werden konsistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="4efd5-166">Der sekundäre Inhalt zeigt unerwartete Verschiebungen an; oder unerwartete Verschiebungen beeinträchtigen nicht die gesamte App-Leistung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="4efd5-167">Primärer Inhalt in Frame zeigt unerwartete Bewegung an.</span><span class="sxs-lookup"><span data-stu-id="4efd5-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-168">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-168">How to measure</span></span>

<span data-ttu-id="4efd5-169">Beim Ausführen des Geräts und Anzeigen der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="4efd5-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="4efd5-170">Bewegen Sie den Kopf von der Seite zur Seite, wenn die holograms unerwartete Verschiebungen anzeigen, dann ist die niedrige Framerate oder die falsche Ausrichtung der Stabilitäts Ebene auf die Fokusebene die wahrscheinliche Ursache.</span><span class="sxs-lookup"><span data-stu-id="4efd5-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="4efd5-171">Navigieren Sie in den holograms und in der Umgebung, und suchen Sie nach Verhaltensweisen wie z. b. Schwimmen und Sprung</span><span class="sxs-lookup"><span data-stu-id="4efd5-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="4efd5-172">Diese Art von Bewegung wird wahrscheinlich dadurch verursacht, dass das Gerät die Umgebung nicht nachverfolgt, oder die Entfernung zum räumlichen Anker.</span><span class="sxs-lookup"><span data-stu-id="4efd5-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="4efd5-173">Wenn sich große oder mehrere holograms im Frame befinden, beobachten Sie das – Hologramm-Verhalten in unterschiedlichen Tiefen, während Sie die Kopfzeile von der Seite zu Seite bewegen, wenn die Schattierung auftritt, wird dies wahrscheinlich durch die Stabilisierungs Ebene verursacht.</span><span class="sxs-lookup"><span data-stu-id="4efd5-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-174">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-174">Recommendations</span></span>

* <span data-ttu-id="4efd5-175">Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.</span><span class="sxs-lookup"><span data-stu-id="4efd5-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="4efd5-176">Verwenden Sie die Stabilisierungs Ebene.</span><span class="sxs-lookup"><span data-stu-id="4efd5-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="4efd5-177">Sie sollten immer verankert Hologramme innerhalb von drei Metern Ihres Ankers darstellen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="4efd5-178">Stellen Sie sicher, dass Ihre Umgebung für die ordnungsgemäße Überwachung eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="4efd5-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="4efd5-179">Entwerfen Sie Ihre Benutzeroberflächen, um Hologramme auf verschiedenen Schwerpunkt Ebenen innerhalb des Rahmens zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-180">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-181">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-181">Documentation</span></span>

* [<span data-ttu-id="4efd5-182">Hologram Stabilität und Framerate</span><span class="sxs-lookup"><span data-stu-id="4efd5-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="4efd5-183">Fallstudie mithilfe der Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="4efd5-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="4efd5-184">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="4efd5-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4efd5-185">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="4efd5-186">Raumanker</span><span class="sxs-lookup"><span data-stu-id="4efd5-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="4efd5-187">Behandeln von nach Verfolgungs Fehlern</span><span class="sxs-lookup"><span data-stu-id="4efd5-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="4efd5-188">Stationärer Frame des Verweises</span><span class="sxs-lookup"><span data-stu-id="4efd5-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-189">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-189">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-190">Mr Companion Kit, kinect IPD</span><span class="sxs-lookup"><span data-stu-id="4efd5-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="4efd5-191">Holograms-Position auf realen Oberflächen</span><span class="sxs-lookup"><span data-stu-id="4efd5-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="4efd5-192">Falsche Abweichungen von holograms mit physischen Objekten (wenn Sie in Beziehung zueinander gesetzt werden sollen) sind ein eindeutiger Hinweis auf die nicht-Union von holograms und der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="4efd5-193">Die Genauigkeit der Platzierung sollte in Relation zu den Anforderungen des Szenarios liegen. Beispielsweise kann bei der allgemeinen Oberflächen Platzierung die räumliche Karte verwendet werden, aber eine genauere Platzierung erfordert die Verwendung von Markern und die Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-194">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-197">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-198">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-198">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-199">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-199">Best</span></span>  |  <span data-ttu-id="4efd5-200">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-200">Meets</span></span> |  <span data-ttu-id="4efd5-201">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="4efd5-202">Holograms werden an der Oberfläche ausgerichtet, die sich in der Regel im Bereich von Zentimetern bis Zoll</span><span class="sxs-lookup"><span data-stu-id="4efd5-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="4efd5-203">Wenn mehr Genauigkeit erforderlich ist, sollte die APP eine effiziente Möglichkeit zur Zusammenarbeit innerhalb der gewünschten App-Spezifikation bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="4efd5-204">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="4efd5-204">NA</span></span> | <span data-ttu-id="4efd5-205">Die Hologramme werden mit dem physischen Zielobjekt nicht ausgerichtet angezeigt, indem die Oberfläche unterbrochen wird oder die Fläche von der Oberfläche entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="4efd5-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="4efd5-206">Wenn die Genauigkeit erforderlich ist, sollten holograms die Näherungs Spezifikation des Szenarios erfüllen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-207">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-207">How to measure</span></span>

* <span data-ttu-id="4efd5-208">Holograms, die auf räumlicher Zuordnung platziert werden, sollten nicht zu einem dramatischen Gleit Komma Wert oberhalb oder unterhalb der Oberfläche erscheinen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="4efd5-209">Holograms, die eine exakte Platzierung erfordern, sollten eine Form von Marker-und Kalibrierungs Systemen aufweisen, die auf die Anforderungen des Szenarios zutreffen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-210">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-210">Recommendations</span></span>

* <span data-ttu-id="4efd5-211">Die räumliche Zuordnung eignet sich zum Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="4efd5-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="4efd5-212">Verwenden Sie zum Festlegen der optimalen Genauigkeit Marker oder Poster, um die holograms und einen Xbox-Controller (oder einen manuellen Ausrichtungs Mechanismus) für die endgültige Kalibrierung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="4efd5-213">Es empfiehlt sich, zusätzliche große Hologramme in logische Teile zu zerlegen und die einzelnen Teile an der Oberfläche auszurichten.</span><span class="sxs-lookup"><span data-stu-id="4efd5-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="4efd5-214">Nicht ordnungsgemäß festgelegten interpupillary Distance (IPD) können auch die Ausrichtung von holograms beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="4efd5-215">Konfigurieren Sie hololens immer für die IPD des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="4efd5-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-216">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-217">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-217">Documentation</span></span>

* [<span data-ttu-id="4efd5-218">Platzierung räumlicher Zuordnung</span><span class="sxs-lookup"><span data-stu-id="4efd5-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="4efd5-219">Raum Scanprozess</span><span class="sxs-lookup"><span data-stu-id="4efd5-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="4efd5-220">Bewährte Methoden für räumliche Anker</span><span class="sxs-lookup"><span data-stu-id="4efd5-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="4efd5-221">Behandeln von nach Verfolgungs Fehlern</span><span class="sxs-lookup"><span data-stu-id="4efd5-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="4efd5-222">Räumliche Abbildung in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="4efd5-223">Übersicht über die vuforia-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="4efd5-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-224">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-224">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-225">Räumliche Daten 230: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="4efd5-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="4efd5-226">Mr Toolkit, Bibliotheken für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="4efd5-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="4efd5-227">Mr Companion Kit, Poster-Kalibrierungs Beispiel</span><span class="sxs-lookup"><span data-stu-id="4efd5-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="4efd5-228">Mr Companion Kit, kinect IPD</span><span class="sxs-lookup"><span data-stu-id="4efd5-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="4efd5-229">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="4efd5-229">External references</span></span>

* [<span data-ttu-id="4efd5-230">Lowes-Fallstudie, Genauigkeits Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="4efd5-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="4efd5-231">Anzeigen der Komfortzone</span><span class="sxs-lookup"><span data-stu-id="4efd5-231">Viewing zone of comfort</span></span>

<span data-ttu-id="4efd5-232">App-Entwickler steuern, wohin die Augen der Benutzer konvergiert werden, indem Sie Inhalte und Hologramme in verschiedenen Tiefen platzieren.</span><span class="sxs-lookup"><span data-stu-id="4efd5-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="4efd5-233">Benutzer, die hololens durchführen, unterstützen immer 2.0 m, um ein klares Bild zu erhalten, da hololens in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer korrigiert werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="4efd5-234">Eine nicht ordnungsgemäße Inhalts Tiefe kann zu einem visuellen Unbehagen oder Müdigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-235">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-238">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-239">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="4efd5-240">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="4efd5-241">Platzieren Sie den Inhalt bei 2 m.</span><span class="sxs-lookup"><span data-stu-id="4efd5-241">Place content at 2m.</span></span></li><li><span data-ttu-id="4efd5-242">Wenn holograms bei 2 m nicht platziert werden können und Konflikte zwischen Konvergenz und Unterbringung nicht vermieden werden können, liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m.</span><span class="sxs-lookup"><span data-stu-id="4efd5-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="4efd5-243">In jedem Fall sollten Designer Inhalte strukturieren, um Benutzern die Interaktion von 1 + m zu empfehlen (z. b. Anpassen von Inhalts Größe und Standard Platzierungs Parametern).</span><span class="sxs-lookup"><span data-stu-id="4efd5-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="4efd5-244">Sofern dies nicht speziell für das Szenario erforderlich ist, sollte eine Clippingebene mit "FadeOut" implementiert werden, beginnend bei 1 Mio.</span><span class="sxs-lookup"><span data-stu-id="4efd5-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="4efd5-245">In Fällen, in denen eine genauere Betrachtung eines sehr großen holograms erforderlich ist, sollte der Inhalt nicht kleiner als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="4efd5-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="4efd5-246">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-246">Meets</span></span></td><td> <span data-ttu-id="4efd5-247">Der Inhalt befindet sich in der Anzeige-und Bewegungs Anleitung, aber nicht ordnungsgemäß oder ohne Verwendung der Clippingebene.</span><span class="sxs-lookup"><span data-stu-id="4efd5-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4efd5-248">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-248">Fail</span></span> </td><td> <span data-ttu-id="4efd5-249">Der Inhalt wird zu nah dargestellt (in der Regel &lt;1,25 Mio.), oder &lt;50 cm für stationäre Hologramme, die eine genauere Beobachtung erfordern.</span><span class="sxs-lookup"><span data-stu-id="4efd5-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-250">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-250">How to measure</span></span>

* <span data-ttu-id="4efd5-251">Der Inhalt sollte in der Regel 2 Mio., aber nicht größer als 1,25 oder größer als 5 Mio. sein.</span><span class="sxs-lookup"><span data-stu-id="4efd5-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="4efd5-252">Mit wenigen Ausnahmen sollte die Länge des Clipping-renderingrenderwerts auf. 85 cm festgelegt werden, wobei die faout-Inhalte beginnend bei 1 Mio. liegen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="4efd5-253">Wenden Sie sich an den Inhalt, und notieren Sie sich die Ausschneide Ebene.</span><span class="sxs-lookup"><span data-stu-id="4efd5-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="4efd5-254">Stationärer Inhalt sollte nicht kleiner als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="4efd5-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-255">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-255">Recommendations</span></span>

* <span data-ttu-id="4efd5-256">Entwerfen Sie den Inhalt für die optimale Anzeige Distanz von 2 m.</span><span class="sxs-lookup"><span data-stu-id="4efd5-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="4efd5-257">Legen Sie die Entfernungs-renderingdistanz auf 85 cm mit dem faout-Inhalt ab 1 Mio. fest.</span><span class="sxs-lookup"><span data-stu-id="4efd5-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="4efd5-258">Bei stationären Hologrammen, die näher betrachtet werden müssen, sollte die Clippingebene nicht größer als 30 cm sein, und Fadeout sollte mindestens 10 cm von der Clippingebene ausgehen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-259">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-259">Resources</span></span>

* [<span data-ttu-id="4efd5-260">Rendering-Entfernung</span><span class="sxs-lookup"><span data-stu-id="4efd5-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="4efd5-261">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="4efd5-262">Experimentieren mit der Skala</span><span class="sxs-lookup"><span data-stu-id="4efd5-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="4efd5-263">Text, Empfohlene Schriftgröße</span><span class="sxs-lookup"><span data-stu-id="4efd5-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="4efd5-264">Tiefen Wechsel</span><span class="sxs-lookup"><span data-stu-id="4efd5-264">Depth switching</span></span>

<span data-ttu-id="4efd5-265">Unabhängig von der Anzeige Zone von Komfort Problemen kann es sein, dass der Benutzer häufig oder schnell zwischen Near-und Far-Fokus Objekten (einschließlich holograms und realen Inhalten) wechselt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-266">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-269">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-269">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-270">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-271">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-271">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-272">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-272">Best</span></span>  |  <span data-ttu-id="4efd5-273">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-273">Meets</span></span> |  <span data-ttu-id="4efd5-274">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-275">Eingeschränkter oder natürlicher tiefen Wechsel, der nicht bewirkt, dass sich der Benutzer nicht ganz natürlich neu konzentriert.</span><span class="sxs-lookup"><span data-stu-id="4efd5-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="4efd5-276">Abrupter tiefen Wechsel hierbei handelt es sich um einen Kern, der in die APP-Umgebung integriert wird, oder um einen abrupten Wechsel, der durch unerwartete reale Inhalte verursacht wurde.</span><span class="sxs-lookup"><span data-stu-id="4efd5-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="4efd5-277">Der konsistente tiefen Wechsel oder der abrupte, nicht erforderliche Wechsel oder Kern der APP-Leistung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-278">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-278">How to measure</span></span>

* <span data-ttu-id="4efd5-279">Wenn die APP erfordert, dass der Benutzer den tiefen Fokus konsistent und/oder abrupt ändert, liegt ein Problem mit dem tiefen Wechsel vor.</span><span class="sxs-lookup"><span data-stu-id="4efd5-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-280">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-280">Recommendations</span></span>

* <span data-ttu-id="4efd5-281">Behalten Sie primären Inhalt in einer konsistenten Fokusebene, und stellen Sie sicher, dass die Stabilisierungs Ebene mit der Fokusebene übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="4efd5-282">Dadurch wird die oomotor-Müdigkeit und unerwartete – Hologramm-Bewegung verringert.</span><span class="sxs-lookup"><span data-stu-id="4efd5-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-283">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-283">Resources</span></span>

* [<span data-ttu-id="4efd5-284">Rendering-Entfernung</span><span class="sxs-lookup"><span data-stu-id="4efd5-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="4efd5-285">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="4efd5-286">Verwendung von räumlichem Sound</span><span class="sxs-lookup"><span data-stu-id="4efd5-286">Use of spatial sound</span></span>

<span data-ttu-id="4efd5-287">In Windows Mixed Reality bietet die Audioengine die Audiowiedergabe-Komponente der gemischten Realität, indem 3D-Sounds mithilfe von Richtungs-, Entfernungs-und Umgebungs Simulationen simuliert werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="4efd5-288">Die Verwendung von räumlichem Sound in einer Anwendung ermöglicht Entwicklern das überzeugend Platzieren von Sounds in einem dreidimensionalen Raum (Kugel), der sich alle um den Benutzer dreht.</span><span class="sxs-lookup"><span data-stu-id="4efd5-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="4efd5-289">Diese Sounds erscheinen dann so, als wären Sie von echten physischen Objekten oder den Mixed Reality holograms in der Benutzerumgebung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="4efd5-290">Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-291">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-294">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-294">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-295">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-296">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-296">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-297">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-297">Best</span></span>  |  <span data-ttu-id="4efd5-298">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-298">Meets</span></span> |  <span data-ttu-id="4efd5-299">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-300">Sound ist logisch räumlich, und die UX verwendet den Sound entsprechend, um die Objekt Ermittlung und das Benutzer Feedback zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="4efd5-301">Sound ist naturgemäß und relevant für Objekte und wird im gesamten Szenario normalisiert.</span><span class="sxs-lookup"><span data-stu-id="4efd5-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="4efd5-302">Räumliche Audiodaten werden in angemessener Weise verwendet, um Benutzer Feedback und Auffindbarkeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="4efd5-303">Sound ist nicht erwartungsgemäß räumlich und/oder ungenügender Ton, um Benutzer innerhalb der UX zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="4efd5-304">Das räumliche audiobild wurde im Entwurf des Szenarios nicht berücksichtigt oder verwendet.</span><span class="sxs-lookup"><span data-stu-id="4efd5-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-305">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-305">How to measure</span></span>

* <span data-ttu-id="4efd5-306">Im Allgemeinen sollten relevante Sounds aus Ziel-holograms (z. b. "Bark Sound" von Holographic Dog) ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="4efd5-307">Sound Hinweise sollten in der gesamten Benutzeroberfläche verwendet werden, um dem Benutzer Feedback oder das Bewusstsein von Aktionen außerhalb des Holographic Frame zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-308">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-308">Recommendations</span></span>

* <span data-ttu-id="4efd5-309">Verwenden Sie räumliche Audiodaten, um die Objekt Ermittlung und Benutzeroberflächen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="4efd5-310">Echte Sounds funktionieren besser als synthetisieren oder unnatürlicher Sound.</span><span class="sxs-lookup"><span data-stu-id="4efd5-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="4efd5-311">Die meisten Sounds sollten räumlich behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="4efd5-312">Vermeiden Sie unsichtbare Emitter.</span><span class="sxs-lookup"><span data-stu-id="4efd5-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="4efd5-313">Vermeiden Sie die räumliche Maskierung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="4efd5-314">Normalisieren Sie alle Sounds.</span><span class="sxs-lookup"><span data-stu-id="4efd5-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-315">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-316">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-316">Documentation</span></span>

* [<span data-ttu-id="4efd5-317">Raumklang</span><span class="sxs-lookup"><span data-stu-id="4efd5-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="4efd5-318">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="4efd5-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="4efd5-319">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="4efd5-320">Fallstudie, räumlicher Sound für holotour</span><span class="sxs-lookup"><span data-stu-id="4efd5-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="4efd5-321">Fallstudie mit räumlichem Sound in roboraid</span><span class="sxs-lookup"><span data-stu-id="4efd5-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-322">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-322">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-323">Mr Spatial 220: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="4efd5-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="4efd5-324">Mrtoolkit, räumliche Audiodaten</span><span class="sxs-lookup"><span data-stu-id="4efd5-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="4efd5-325">Fokus auf Holographic Frame-Grenzen (FOV)</span><span class="sxs-lookup"><span data-stu-id="4efd5-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="4efd5-326">Gut gestaltete Benutzeroberflächen können den nützlichen Kontext der virtuellen Umgebung erstellen und verwalten, die sich um die Benutzer erstreckt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="4efd5-327">Das Verringern der Auswirkungen der FOV-Grenzen umfasst einen durchdachten Entwurf der Inhalts Skala und des Kontexts, die Verwendung räumlicher Audiodaten, Leitfäden und die Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="4efd5-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="4efd5-328">Wenn dies der Fall ist, wird der Benutzer durch die FOV-Grenzen weniger beeinträchtigt, während er eine bequeme App-Erfahrung bietet.</span><span class="sxs-lookup"><span data-stu-id="4efd5-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-329">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-332">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-333">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-333">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-334">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-334">Best</span></span>  |  <span data-ttu-id="4efd5-335">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-335">Meets</span></span> |  <span data-ttu-id="4efd5-336">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-337">Der Benutzer verliert nie den Kontext, und die Anzeige ist bequem.</span><span class="sxs-lookup"><span data-stu-id="4efd5-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="4efd5-338">Für große Objekte wird Kontextunterstützung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="4efd5-339">Ermittelbarkeits-und Anzeige Anleitungen werden für Objekte außerhalb des Frames bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="4efd5-340">Im Allgemeinen sind Bewegungs Entwurf und Skalierung der holograms für eine bequeme Anzeige geeignet.</span><span class="sxs-lookup"><span data-stu-id="4efd5-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="4efd5-341">Der Benutzer verliert den Kontext nie, aber in bestimmten Situationen ist möglicherweise eine zusätzliche Nacken Bewegung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4efd5-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="4efd5-342">In einer begrenzten Situation bewirkt die Skalierung, dass holograms entweder den vertikalen oder horizontalen Rahmen unterbrechen, was dazu führt, dass die Bewegung holograms durch einen Hals</span><span class="sxs-lookup"><span data-stu-id="4efd5-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="4efd5-343">Der Benutzer verliert wahrscheinlich den Kontext und/oder eine konsistente Hals Bewegung zum Anzeigen von holograms.</span><span class="sxs-lookup"><span data-stu-id="4efd5-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="4efd5-344">Keine Kontext Leit Fäden für große Holographic-Objekte, die das Verschieben von Objekten außerhalb des Frames ohne auffindbarkeits Leit Fäden vereinfachen, oder die Verwendung von hohen holograms erfordert eine reguläre Hals Bewegung zum anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-345">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-345">How to measure</span></span>

* <span data-ttu-id="4efd5-346">Der Kontext für ein (großes) – Hologramm geht verloren oder wird nicht verstanden, weil er an den Begrenzungen abgeschnitten wurde.</span><span class="sxs-lookup"><span data-stu-id="4efd5-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="4efd5-347">Der Speicherort von holograms ist schwierig zu finden, da es sich nicht um die Aufmerksamkeit von Regisseuren oder Inhalten handelt, die sich schnell in den Holographic-Frame bewegen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="4efd5-348">Das Szenario erfordert reguläre und wiederkehrende aufruhenden aufruhenden Bewegung, um ein – Hologramm vollständig zu sehen</span><span class="sxs-lookup"><span data-stu-id="4efd5-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-349">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-349">Recommendations</span></span>

* <span data-ttu-id="4efd5-350">Starten Sie die Arbeit mit kleinen Objekten, die für den FOV geeignet sind, und wechseln Sie dann mit visuellen Cues in größere Versionen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="4efd5-351">Verwenden Sie die Directors für räumliche Audiodaten und Aufmerksamkeit, um dem Benutzer zu helfen, Inhalte außerhalb des FOV zu finden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="4efd5-352">Vermeiden Sie so weit wie möglich Hologramme, die den FOV vertikal abschneiden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="4efd5-353">Stellen Sie dem Benutzer einen in-App-Leitfaden für den optimalen Anzeige Speicherort zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-354">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-355">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-355">Documentation</span></span>

* [<span data-ttu-id="4efd5-356">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="4efd5-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="4efd5-357">Fallstudie, Entwicklung von holostudio-UI und Interaktions Entwurf</span><span class="sxs-lookup"><span data-stu-id="4efd5-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="4efd5-358">Skalieren von Objekten und Umgebungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="4efd5-359">Cursor, visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="4efd5-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="4efd5-360">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="4efd5-360">External references</span></span>

* [<span data-ttu-id="4efd5-361">Viel ADO zum FOV</span><span class="sxs-lookup"><span data-stu-id="4efd5-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="4efd5-362">Inhalt reagiert auf Benutzer Position</span><span class="sxs-lookup"><span data-stu-id="4efd5-362">Content reacts to user position</span></span>

<span data-ttu-id="4efd5-363">Holograms sollten auf ungefähr die gleiche Weise wie "echte" Objekte auf die Benutzer Position reagieren.</span><span class="sxs-lookup"><span data-stu-id="4efd5-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="4efd5-364">Ein wichtiger Entwurfs Aspekt sind Benutzeroberflächen Elemente, die nicht unbedingt annehmen können, dass die Position eines Benutzers stationär ist und sich an die Bewegung des Benutzers anpasst.</span><span class="sxs-lookup"><span data-stu-id="4efd5-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="4efd5-365">Das Entwerfen einer APP, die sich ordnungsgemäß an die Benutzer Position anpasst, führt zu einer besseren Benutzerfreundlichkeit und erleichtert die Verwendung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-366">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-369">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-369">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-370">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-371">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="4efd5-372">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-372">Best</span></span> </td><td> <span data-ttu-id="4efd5-373">Der Inhalt und die Benutzeroberfläche werden an Benutzer Positionen angepasst, damit Benutzer im Bereich der erwarteten Benutzer Bewegung natürlich mit Inhalten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="4efd5-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4efd5-374">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-374">Meets</span></span> </td><td> <span data-ttu-id="4efd5-375">Die Benutzeroberfläche passt sich an die Benutzer Position an, kann jedoch die Ansicht von Schlüssel Inhalten behindern, die den Benutzer zum Anpassen Ihrer Position benötigen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4efd5-376">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="4efd5-377">Benutzeroberflächen Elemente gehen verloren oder sind während der Bewegung gesperrt, sodass der Benutzer nicht auf natürliche Weise zu den Steuerelementen zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="4efd5-378">Elemente der Benutzeroberfläche beschränken die Ansicht von primärem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="4efd5-379">Die UI-Verschiebung ist nicht für die Anzeige von Distance und Impulsen vor allem mit <a href="billboarding-and-tag-along.md">tagbasierten</a> Benutzeroberflächen Elementen optimiert.</span><span class="sxs-lookup"><span data-stu-id="4efd5-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-380">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-380">How to measure</span></span>

* <span data-ttu-id="4efd5-381">Alle Messungen sollten innerhalb eines angemessenen Umfangs des Szenarios durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="4efd5-382">Während die Benutzer Bewegung variieren kann, versuchen Sie nicht, die APP mit extremer Benutzer Bewegung zu täuschen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="4efd5-383">Für Elemente der Benutzeroberfläche sollten relevante Steuerelemente unabhängig von der Benutzer Bewegung verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="4efd5-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="4efd5-384">Wenn der Benutzer z. b. eine 3D-Karte mit Zoom anzeigen und durchläuft, sollte das Zoom Steuerelement dem Benutzer unabhängig von der Position sofort verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="4efd5-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-385">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-385">Recommendations</span></span>

* <span data-ttu-id="4efd5-386">Der Benutzer ist die Kamera und steuert die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="4efd5-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="4efd5-387">Das können Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="4efd5-387">Let them drive.</span></span>
* <span data-ttu-id="4efd5-388">Ziehen Sie die Abrechnung für Text-und menuingsysteme in Erwägung, die andernfalls in der Welt gesperrt oder verdeckt werden, wenn sich ein Benutzer bewegen würde.</span><span class="sxs-lookup"><span data-stu-id="4efd5-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="4efd5-389">Verwenden Sie tagzusammen für Inhalte, die dem Benutzer folgen müssen, während der Benutzer weiterhin sehen kann, was vor ihm steht.</span><span class="sxs-lookup"><span data-stu-id="4efd5-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-390">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-391">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-391">Documentation</span></span>

* [<span data-ttu-id="4efd5-392">Interaktions Entwurf</span><span class="sxs-lookup"><span data-stu-id="4efd5-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="4efd5-393">Farbe, Licht und Material</span><span class="sxs-lookup"><span data-stu-id="4efd5-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="4efd5-394">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="4efd5-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4efd5-395">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="4efd5-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4efd5-396">Selbst Bewegung und Benutzer Bewegung</span><span class="sxs-lookup"><span data-stu-id="4efd5-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-397">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-397">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-398">Mr-Eingabe 210: Blick</span><span class="sxs-lookup"><span data-stu-id="4efd5-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="4efd5-399">Klarheit der Eingabe Interaktion</span><span class="sxs-lookup"><span data-stu-id="4efd5-399">Input interaction clarity</span></span>

<span data-ttu-id="4efd5-400">Die Übersichtlichkeit der Eingabe Interaktion ist wichtig für die Benutzerfreundlichkeit einer APP und umfasst Eingabe Konsistenz, genehmigende Zulässigkeit, Auffindbarkeit von Interaktions Methoden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="4efd5-401">Der Benutzer sollte in der Lage sein, plattformweite allgemeine Interaktionen ohne Relearning zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="4efd5-402">Wenn die APP benutzerdefinierte Eingaben hat, sollte Sie eindeutig kommuniziert und demonstriert werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-403">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-406">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-406">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-407">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-408">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-408">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-409">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-409">Best</span></span>  |  <span data-ttu-id="4efd5-410">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-410">Meets</span></span> |  <span data-ttu-id="4efd5-411">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-412">Eingabe Interaktions Methoden sind mit der von Windows Mixed Reality bereitgestellten [Anleitung](interaction-fundamentals.md)konsistent.</span><span class="sxs-lookup"><span data-stu-id="4efd5-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="4efd5-413">Jede benutzerdefinierte Eingabe sollte nicht mit Standard Eingaben redundant sein (sondern eher die Standard Interaktion verwenden), und Sie muss für den Benutzer eindeutig kommuniziert und demonstriert werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="4efd5-414">Ähnlich wie die beste, aber benutzerdefinierte Eingaben sind bei Standardeingabe Methoden redundant.</span><span class="sxs-lookup"><span data-stu-id="4efd5-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="4efd5-415">Der Benutzer kann das Ziel und den Fortschritt auch über die App-Benutzer Leistung erreichen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="4efd5-416">Das Verständnis der Eingabemethode oder der Schaltflächen Zuordnung ist schwierig.</span><span class="sxs-lookup"><span data-stu-id="4efd5-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="4efd5-417">Die Eingabe ist stark angepasst, bietet keine Unterstützung für Standard Eingaben, keine Anweisungen, oder es werden wahrscheinlich Ermüdungs-und komfortprobleme verursacht.</span><span class="sxs-lookup"><span data-stu-id="4efd5-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-418">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-418">How to measure</span></span>

* <span data-ttu-id="4efd5-419">Die APP verwendet konsistente [Standardeingabe Methoden.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="4efd5-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="4efd5-420">Wenn die APP über benutzerdefinierte Eingaben verfügt, wird Sie eindeutig übermittelt:</span><span class="sxs-lookup"><span data-stu-id="4efd5-420">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="4efd5-421">Erstmaligen Testlauf</span><span class="sxs-lookup"><span data-stu-id="4efd5-421">First-run experience</span></span>
* <span data-ttu-id="4efd5-422">Einführungs Bildschirme</span><span class="sxs-lookup"><span data-stu-id="4efd5-422">Introductory screens</span></span>
* <span data-ttu-id="4efd5-423">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="4efd5-423">Tooltips</span></span>
* <span data-ttu-id="4efd5-424">Hand Coach</span><span class="sxs-lookup"><span data-stu-id="4efd5-424">Hand coach</span></span>
* <span data-ttu-id="4efd5-425">Hilfe Abschnitt</span><span class="sxs-lookup"><span data-stu-id="4efd5-425">Help section</span></span>
* <span data-ttu-id="4efd5-426">Voice-over</span><span class="sxs-lookup"><span data-stu-id="4efd5-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-427">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-427">Recommendations</span></span>

* <span data-ttu-id="4efd5-428">Verwenden Sie nach Möglichkeit immer Standardeingabe Methoden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="4efd5-429">Stellen Sie Demonstrationen, Tutorials und Quick Infos für nicht standardmäßige Eingabemethoden bereit.</span><span class="sxs-lookup"><span data-stu-id="4efd5-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="4efd5-430">Verwenden Sie in der gesamten App ein konsistentes Interaktionsmodell.</span><span class="sxs-lookup"><span data-stu-id="4efd5-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-431">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-432">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-432">Documentation</span></span>

* [<span data-ttu-id="4efd5-433">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="4efd5-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4efd5-434">Interactable-Objekte</span><span class="sxs-lookup"><span data-stu-id="4efd5-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="4efd5-435">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="4efd5-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4efd5-436">Cursor</span><span class="sxs-lookup"><span data-stu-id="4efd5-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4efd5-437">Komfort und Blick</span><span class="sxs-lookup"><span data-stu-id="4efd5-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="4efd5-438">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="4efd5-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="4efd5-439">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="4efd5-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="4efd5-440">Leitfaden für Eingabeportierung für Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="4efd5-441">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="4efd5-442">Anvisieren in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="4efd5-443">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="4efd5-444">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="4efd5-445">Tastatur-, Maus- und Controllereingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="4efd5-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="4efd5-446">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="4efd5-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="4efd5-447">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="4efd5-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="4efd5-448">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="4efd5-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-449">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-449">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-450">Fallstudie: die Verfolgung von mehr persönlichen Computing</span><span class="sxs-lookup"><span data-stu-id="4efd5-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="4efd5-451">Umwandlungs Studie: Entwicklung von holostudio-UI-und Interaktions Entwürfen</span><span class="sxs-lookup"><span data-stu-id="4efd5-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="4efd5-452">Beispiel-App: periodische Tabelle der Elemente</span><span class="sxs-lookup"><span data-stu-id="4efd5-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="4efd5-453">Beispiel-App: Mond Modul</span><span class="sxs-lookup"><span data-stu-id="4efd5-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="4efd5-454">Mr-Eingabe 210: Blick</span><span class="sxs-lookup"><span data-stu-id="4efd5-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="4efd5-455">Mr-Eingabe 211: Gesten</span><span class="sxs-lookup"><span data-stu-id="4efd5-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="4efd5-456">Mr-Eingabe 212: Stimme</span><span class="sxs-lookup"><span data-stu-id="4efd5-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="4efd5-457">Interactable-Objekte</span><span class="sxs-lookup"><span data-stu-id="4efd5-457">Interactable objects</span></span>

<span data-ttu-id="4efd5-458">Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4efd5-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="4efd5-459">In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="4efd5-460">Dabei kann es sich um ein Objekt handeln, das ein Objekt ist, das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="4efd5-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="4efd5-461">Ein Objekt, das sich in der Tabelle befindet, kann als beliebiger von einem Kaffeebecher in der Tabelle dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="4efd5-462">Unabhängig vom Formular sollte der Benutzer durch visuelle und Audiohinweise eindeutig erkennbar sein.</span><span class="sxs-lookup"><span data-stu-id="4efd5-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-463">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-466">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-466">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-467">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-468">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-468">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-469">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-469">Best</span></span>  |  <span data-ttu-id="4efd5-470">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-470">Meets</span></span> |  <span data-ttu-id="4efd5-471">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-472">Unabhängig von der Form sind Interaktionen-Objekte durch visuelle und Audiohinweise in drei Zuständen erkennbar: im Leerlauf, gezielt und ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="4efd5-473">"Wie Sie sehen, ist es klar und in der gesamten gesamten Darstellung verwendet.</span><span class="sxs-lookup"><span data-stu-id="4efd5-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="4efd5-474">Objekte werden skaliert und verteilt, um eine fehlerfreie Zielversion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="4efd5-475">Der Benutzer kann das Objekt als Interaktionen durch Audiomaterial oder visuelles Feedback erkennen und das Objekt auf das Objekt ausrichten und aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4efd5-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="4efd5-476">Wenn keine visuellen oder Audiohinweise angezeigt werden, kann der Benutzer ein Objekt mit Interaktionen nicht erkennen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="4efd5-477">Interaktionen sind aufgrund der Objekt Skala oder der Entfernung zwischen Objekten fehleranfällig.</span><span class="sxs-lookup"><span data-stu-id="4efd5-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-478">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-478">How to measure</span></span>

* <span data-ttu-id="4efd5-479">Interactable-Objekte sind als "interactable" erkennbar. einschließen von Schaltflächen, Menüs und App-spezifischem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="4efd5-480">Als Faustregel gilt, dass ein visueller und audiohinweis vorhanden sein sollte, wenn Sie auf Objekte mit Interaktionen abzielen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-481">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-481">Recommendations</span></span>

* <span data-ttu-id="4efd5-482">Verwenden Sie visuelles und Audiofeedback für Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="4efd5-483">Visuelles Feedback sollte für jeden Eingabe Status unterschieden werden (im Leerlauf, gezielt, ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="4efd5-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="4efd5-484">Interactable-Objekte sollten skaliert und für fehlerfreie Zielgruppen vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="4efd5-485">Gruppierte Interaktionen-Objekte (z. b. eine Menüleiste oder Liste) sollten über den richtigen Abstand zum Ziel verfügen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="4efd5-486">Schaltflächen und Menüs, die den Voice-Befehl unterstützen, sollten Text Bezeichnungen für das Befehls Schlüsselwort bereitstellen ("siehe IT, sagen Sie")</span><span class="sxs-lookup"><span data-stu-id="4efd5-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-487">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-488">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-488">Documentation</span></span>

* [<span data-ttu-id="4efd5-489">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="4efd5-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4efd5-490">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="4efd5-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="4efd5-491">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="4efd5-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4efd5-492">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="4efd5-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-493">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-493">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-494">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="4efd5-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="4efd5-495">Raum Überprüfung</span><span class="sxs-lookup"><span data-stu-id="4efd5-495">Room scanning</span></span>

<span data-ttu-id="4efd5-496">Apps, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht.</span><span class="sxs-lookup"><span data-stu-id="4efd5-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="4efd5-497">Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich überprüft hat.</span><span class="sxs-lookup"><span data-stu-id="4efd5-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="4efd5-498">Viele apps analysieren die räumlichen Zuordnungs Daten zu Beginn der Benutzer Darstellung, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen muss, um die Vollständigkeit und Qualität der räumlichen Karte zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="4efd5-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="4efd5-499">Wenn der Benutzer die Umgebung scannen muss, sollten Sie während der Überprüfung eine klare Anleitung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4efd5-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-500">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-503">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-504">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-504">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-505">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-505">Best</span></span>  |  <span data-ttu-id="4efd5-506">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-506">Meets</span></span> |  <span data-ttu-id="4efd5-507">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-508">Die Visualisierung des räumlichen Netzes weist auf die Überprüfung von Benutzern hin.</span><span class="sxs-lookup"><span data-stu-id="4efd5-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="4efd5-509">Der Benutzer weiß eindeutig, was zu tun ist und wann die Überprüfung gestartet und beendet wird.</span><span class="sxs-lookup"><span data-stu-id="4efd5-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="4efd5-510">Die Visualisierung des räumlichen Netzes wird bereitgestellt, aber der Benutzer weiß möglicherweise nicht, was zu tun ist, und es werden keine Fortschrittsinformationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="4efd5-511">Keine Visualisierung von Mesh.</span><span class="sxs-lookup"><span data-stu-id="4efd5-511">No visualization of mesh.</span></span> <span data-ttu-id="4efd5-512">Für den Benutzer werden keine Leitfäden bezüglich des abzurufenden oder zum Starten/Beenden der Überprüfung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-513">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-513">How to measure</span></span>

* <span data-ttu-id="4efd5-514">Während eines erforderlichen Raum Scans werden visuelle und audioanleitungen bereitgestellt, die angeben, wo gesucht werden soll und wann das Scannen gestartet und beendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="4efd5-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-515">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-515">Recommendations</span></span>

* <span data-ttu-id="4efd5-516">Geben Sie an, wie viel des gesamten Volumes in der Benutzerumgebung in der Umgebung enthalten sein muss.</span><span class="sxs-lookup"><span data-stu-id="4efd5-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="4efd5-517">Kommunizieren, wenn die Überprüfung gestartet und beendet wird, z. b. eine Statusanzeige.</span><span class="sxs-lookup"><span data-stu-id="4efd5-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="4efd5-518">Verwenden Sie während des Scanvorgangs eine Visualisierung des Netzes.</span><span class="sxs-lookup"><span data-stu-id="4efd5-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="4efd5-519">Stellen Sie visuelle und Audiohinweise bereit, um den Benutzer zu unterstützen, um den Raum zu sehen und zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="4efd5-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="4efd5-520">Informieren Sie den Benutzer, wohin Sie die Daten verbessern möchten.</span><span class="sxs-lookup"><span data-stu-id="4efd5-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="4efd5-521">In vielen Fällen kann es am besten sein, den Benutzern mitzuteilen, was Sie tun müssen (z. b. die Obergrenze, das Aussehen hinter den Möbeln), um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4efd5-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-522">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="4efd5-523">Unterlagen</span><span class="sxs-lookup"><span data-stu-id="4efd5-523">Documentation</span></span>

* [<span data-ttu-id="4efd5-524">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="4efd5-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="4efd5-525">Fallstudie: Erweitern der Funktionen für räumliche Zuordnung von hololens</span><span class="sxs-lookup"><span data-stu-id="4efd5-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="4efd5-526">Fallstudie: räumliches Sound Design für holotour</span><span class="sxs-lookup"><span data-stu-id="4efd5-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="4efd5-527">Fallstudie: Erstellen eines immersiven Erlebnisses in Fragmenten</span><span class="sxs-lookup"><span data-stu-id="4efd5-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="4efd5-528">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="4efd5-528">Tools and tutorials</span></span>

* [<span data-ttu-id="4efd5-529">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="4efd5-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="4efd5-530">Direktionale Indikatoren</span><span class="sxs-lookup"><span data-stu-id="4efd5-530">Directional indicators</span></span>

<span data-ttu-id="4efd5-531">In einer Mixed Reality-App kann es sein, dass sich Inhalte außerhalb des Felds befinden oder durch reale Objekte verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="4efd5-532">Eine gut entworfene App vereinfacht das Auffinden nicht sichtbarer Inhalte durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4efd5-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="4efd5-533">Direktionale Indikatoren warnen einen Benutzer für wichtige Inhalte und bieten Anleitungen für den Inhalt in Bezug auf die Position des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="4efd5-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="4efd5-534">Anleitungen für nicht sichtbare Inhalte können als audioemitter, direktionale Pfeile oder direkte visuelle Hinweise genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-535">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-538">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-538">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-539">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-540">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-540">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-541">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-541">Best</span></span>  |  <span data-ttu-id="4efd5-542">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-542">Meets</span></span> |  <span data-ttu-id="4efd5-543">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-544">Visuelle und Audiohinweise leiten den Benutzer direkt an relevante Inhalte außerhalb des Felds der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="4efd5-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="4efd5-545">Ein Pfeil oder ein Indikator, der den Benutzer in der allgemeinen Richtung des Inhalts zeigt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="4efd5-546">Relevante Inhalte sind nicht in der Ansicht enthalten, und dem Benutzer wird ein schlechter oder kein Orts Leit Faden bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-547">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-547">How to measure</span></span>

* <span data-ttu-id="4efd5-548">Relevante Inhalte außerhalb des Benutzer Felds können durch visuelle und/oder Audiohinweise erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-549">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-549">Recommendations</span></span>

* <span data-ttu-id="4efd5-550">Wenn relevante Inhalte außerhalb des Benutzer Felds liegen, verwenden Sie richtungsindikatoren und Audiohinweise, um den Benutzer zum Inhalt zu leiten.</span><span class="sxs-lookup"><span data-stu-id="4efd5-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="4efd5-551">In vielen Fällen wird ein direkter visueller Leitfaden als direktionale Pfeile bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="4efd5-552">Direktionale Indikatoren sollten nicht in den Cursor integriert werden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-553">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-553">Resources</span></span>

* [<span data-ttu-id="4efd5-554">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="4efd5-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="4efd5-555">Laden von Daten</span><span class="sxs-lookup"><span data-stu-id="4efd5-555">Data loading</span></span>

<span data-ttu-id="4efd5-556">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4efd5-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="4efd5-557">Dies kann bedeuten, dass der Benutzer nicht mit der APP interagieren kann, wenn die Statusanzeige sichtbar ist, und auch angeben kann, wie lange die Wartezeit dauern kann.</span><span class="sxs-lookup"><span data-stu-id="4efd5-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="4efd5-558">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="4efd5-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4efd5-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4efd5-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4efd5-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4efd5-561">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-561">✔️</span></span></td>
        <td><span data-ttu-id="4efd5-562">✔️</span><span class="sxs-lookup"><span data-stu-id="4efd5-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="4efd5-563">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="4efd5-563">Quality criteria</span></span>

|  <span data-ttu-id="4efd5-564">Best</span><span class="sxs-lookup"><span data-stu-id="4efd5-564">Best</span></span>  |  <span data-ttu-id="4efd5-565">Findet</span><span class="sxs-lookup"><span data-stu-id="4efd5-565">Meets</span></span> |  <span data-ttu-id="4efd5-566">UN</span><span class="sxs-lookup"><span data-stu-id="4efd5-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="4efd5-567">Animierter visueller Indikator in Form einer Statusanzeige oder eines Rings, der den Fortschritt beim Laden oder Verarbeiten von Daten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="4efd5-568">Der visuelle Indikator gibt eine Anleitung dazu, wie lange der Warte Vorgang sein könnte.</span><span class="sxs-lookup"><span data-stu-id="4efd5-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="4efd5-569">Der Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird. es gibt jedoch keinen Hinweis darauf, wie lange der Warte Vorgang sein könnte.</span><span class="sxs-lookup"><span data-stu-id="4efd5-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="4efd5-570">Das Laden von Daten oder das Verarbeiten von Indikatoren für den Task dauert länger als 5 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="4efd5-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="4efd5-571">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="4efd5-571">How to measure</span></span>

* <span data-ttu-id="4efd5-572">Vergewissern Sie sich beim Laden von Daten, dass es für mehr als 5 Sekunden keinen leeren Zustand gibt.</span><span class="sxs-lookup"><span data-stu-id="4efd5-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="4efd5-573">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4efd5-573">Recommendations</span></span>

* <span data-ttu-id="4efd5-574">Stellen Sie eine Animation zum Laden von Daten bereit, die den Fortschritt in jeder Situation anzeigt, in der der Benutzer diese APP möglicherweise als angehalten oder abstürzt</span><span class="sxs-lookup"><span data-stu-id="4efd5-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="4efd5-575">Eine vernünftige Faustregel ist jede "Lade Aktivität", die mehr als 5 Sekunden in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="4efd5-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="4efd5-576">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4efd5-576">Resources</span></span>

* [<span data-ttu-id="4efd5-577">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="4efd5-577">Displaying progress</span></span>](progress.md)
