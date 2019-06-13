---
title: Qualitätskriterien für die App
description: Dieses Dokument beschreibt die obersten Faktoren, die Auswirkungen auf die Qualität von mixed Reality-apps.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, mixed Reality, mixed Reality-app
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024497"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="9c785-104">Qualitätskriterien für die App</span><span class="sxs-lookup"><span data-stu-id="9c785-104">App quality criteria</span></span>

<span data-ttu-id="9c785-105">Dieses Dokument beschreibt die obersten Faktoren, die Auswirkungen auf die Qualität von mixed Reality-apps.</span><span class="sxs-lookup"><span data-stu-id="9c785-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="9c785-106">Für die einzelnen Faktoren ist die folgenden Informationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="9c785-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="9c785-107">Übersicht – eine kurze Beschreibung der Qualitätsfaktor und warum es wichtig ist.</span><span class="sxs-lookup"><span data-stu-id="9c785-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="9c785-108">Gerät Auswirkungen, – welche Art von Fenster Mixed Reality-Gerät betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="9c785-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="9c785-109">Qualitätskriterien – wie den Qualitätsfaktor ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="9c785-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="9c785-110">So messen – Methoden, um das Problem zu messen (oder auftreten).</span><span class="sxs-lookup"><span data-stu-id="9c785-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="9c785-111">Empfehlungen – Zusammenfassung der Ansätze für eine bessere Benutzeroberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="9c785-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="9c785-112">Ressourcen – relevanten Entwickler- und Design-Ressourcen, die zum Erstellen besserer Benutzeroberflächen nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="9c785-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="9c785-113">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="9c785-113">Frame rate</span></span>

<span data-ttu-id="9c785-114">Framerate ist die erste Säule des – Hologramm Stabilität Komfort für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9c785-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="9c785-115">Framerate oberhalb der empfohlenen Ziele kann dazu führen, dass Hologramme ganz nervös, negative Auswirkungen auf die Believability der Benutzeroberfläche und führte potenziell zu Eye Ermüdung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="9c785-116">60Hz oder 90Hz, je nachdem welche Windows Mixed Reality kompatibel PCs Sie unterstützen möchten, wird die Ziel-Framerate für Ihre Umgebung für immersive Headsets Windows Mixed Reality sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="9c785-117">Für HoloLens ist die Ziel-Framerate 60Hz.</span><span class="sxs-lookup"><span data-stu-id="9c785-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-118">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-121">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-121">✔️</span></span></td>
        <td><span data-ttu-id="9c785-122">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-123">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-123">Quality criteria</span></span>

|  <span data-ttu-id="9c785-124">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-124">Best</span></span>  |  <span data-ttu-id="9c785-125">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-125">Meets</span></span> |  <span data-ttu-id="9c785-126">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="9c785-127">Die app erfüllt konsistent Frames pro Sekunde (FPS)-Ziel für Zielgerät: 60fps im HoloLens; 90 f/s auf Ultra-PCs und 60fps auf gängige PCs.</span><span class="sxs-lookup"><span data-stu-id="9c785-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="9c785-128">Die app verfügt über periodische Frame löscht die Core-Umgebung nicht zu beeinträchtigen, oder f/s ist konsistent niedriger als der gewünschte Ziel, aber durch die app-Funktionalität nicht beeinträchtigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="9c785-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="9c785-129">Die app hat einen Abfall der Framerate, die im Durchschnitt alle zehn Sekunden oder weniger.</span><span class="sxs-lookup"><span data-stu-id="9c785-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9c785-130">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-130">How to measure</span></span>

* <span data-ttu-id="9c785-131">Ein in Echtzeit Frame Rate Diagramm erfolgt über von der [Windows Device Portal](using-the-windows-device-portal.md#system-performance) unter "System Performance".</span><span class="sxs-lookup"><span data-stu-id="9c785-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="9c785-132">Fügen Sie für die Entwicklung zu debuggen einen Frame Rate-Diagnose-Zähler der app hinzu.</span><span class="sxs-lookup"><span data-stu-id="9c785-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="9c785-133">Finden Sie Ressourcen für einen Beispiel-Indikator.</span><span class="sxs-lookup"><span data-stu-id="9c785-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="9c785-134">Frame Rate löscht können im Gerät auftreten können, während die app ausgeführt wird, durch das Verschieben der Kopf von rechts.</span><span class="sxs-lookup"><span data-stu-id="9c785-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="9c785-135">Wenn die Hologramm unerwartete ganz nervös Bewegung angezeigt wird, dann niedrigen Framerate oder die Stabilität-Ebene ist wahrscheinlich die Ursache.</span><span class="sxs-lookup"><span data-stu-id="9c785-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-136">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-136">Recommendations</span></span>

* <span data-ttu-id="9c785-137">Fügen Sie einen Frame Rate Zähler am Anfang der Entwicklungsarbeit hinzu.</span><span class="sxs-lookup"><span data-stu-id="9c785-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="9c785-138">Änderungen, die einen Abfall der Framerate entstehen, ausgewertet und als leistungsfehler entsprechend behoben.</span><span class="sxs-lookup"><span data-stu-id="9c785-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-139">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-140">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-140">Documentation</span></span>

* [<span data-ttu-id="9c785-141">Grundlegendes zur Leistung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9c785-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9c785-142">– Hologramm Stabilität und der Bildrate</span><span class="sxs-lookup"><span data-stu-id="9c785-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="9c785-143">Asset-Leistungsbudget</span><span class="sxs-lookup"><span data-stu-id="9c785-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="9c785-144">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-145">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-145">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-146">MRToolkit, f/s-Leistungsindikator-Anzeige</span><span class="sxs-lookup"><span data-stu-id="9c785-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="9c785-147">MRToolkit, Shadern</span><span class="sxs-lookup"><span data-stu-id="9c785-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="9c785-148">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="9c785-148">External references</span></span>

* [<span data-ttu-id="9c785-149">Unity und Optimieren von mobilen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="9c785-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="9c785-150">– Hologramm Stabilität</span><span class="sxs-lookup"><span data-stu-id="9c785-150">Hologram stability</span></span>

<span data-ttu-id="9c785-151">Stabile Hologramme werden erhöht die benutzerfreundlichkeit und Believability Ihrer App, und erstellen ein angenehmer Anzeigefunktionen für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9c785-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="9c785-152">Die Qualität der – Hologramm Stabilität ist das Ergebnis gute app-Entwicklung und die Fähigkeit des Geräts (Track) zu ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="9c785-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="9c785-153">Während der Framerate für die erste Säule des Stabilität ist, können andere Faktoren, einschließlich Stabilität auswirken:</span><span class="sxs-lookup"><span data-stu-id="9c785-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="9c785-154">Verwenden der Stabilisierung Ebene</span><span class="sxs-lookup"><span data-stu-id="9c785-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="9c785-155">Abstand und räumliche Anker</span><span class="sxs-lookup"><span data-stu-id="9c785-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="9c785-156">Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="9c785-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-157">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-160">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-160">✔️</span></span></td>
        <td><span data-ttu-id="9c785-161">❌</span><span class="sxs-lookup"><span data-stu-id="9c785-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-162">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-162">Quality criteria</span></span>

|  <span data-ttu-id="9c785-163">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-163">Best</span></span>  |  <span data-ttu-id="9c785-164">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-164">Meets</span></span> |  <span data-ttu-id="9c785-165">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-166">Hologramme werden konsistent stabile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9c785-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="9c785-167">Sekundärer Inhalt weist unerwartete Bewegung; oder unerwartete Bewegung allgemeine app-Benutzeroberfläche nicht behindern.</span><span class="sxs-lookup"><span data-stu-id="9c785-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="9c785-168">Hauptinhalt in Rahmen weist unerwartete verschieben.</span><span class="sxs-lookup"><span data-stu-id="9c785-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9c785-169">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-169">How to measure</span></span>

<span data-ttu-id="9c785-170">Während das Gerät steht, geteert und die zur Anzeige von:</span><span class="sxs-lookup"><span data-stu-id="9c785-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="9c785-171">Verschieben Kopf von rechts, die Hologramme unerwartete Bewegung angezeigt dann niedrigen Framerate oder eine fehlerhafte Ausrichtung der Stabilität Ebene auf dieser Ebene wird wahrscheinlich dadurch verursacht.</span><span class="sxs-lookup"><span data-stu-id="9c785-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="9c785-172">Verschieben Sie die Hologramme und die Umgebung, suchen Sie nach Verhaltensweisen wie verantwortlichkeitsbereichs und Jumpiness.</span><span class="sxs-lookup"><span data-stu-id="9c785-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="9c785-173">Diese Art von Motion wird wahrscheinlich durch das Gerät nicht die Umgebung oder die Entfernung verfolgt, auf den spatial Anker verursacht.</span><span class="sxs-lookup"><span data-stu-id="9c785-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="9c785-174">Bei einer großen oder mehrere Hologramme befinden sich in den Frame, – Hologramm-Verhalten in verschiedenen Ebenen zu beobachten, während Ihre Head Position von rechts, verschieben, wenn Shakiness angezeigt wird, dies ist wahrscheinlich der Stabilisierung Ebene zurückzuführen.</span><span class="sxs-lookup"><span data-stu-id="9c785-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="9c785-175">Recomendations</span><span class="sxs-lookup"><span data-stu-id="9c785-175">Recomendations</span></span>

* <span data-ttu-id="9c785-176">Fügen Sie einen Frame Rate Zähler am Anfang der Entwicklungsarbeit hinzu.</span><span class="sxs-lookup"><span data-stu-id="9c785-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="9c785-177">Verwenden Sie die Stabilisierung-Ebene.</span><span class="sxs-lookup"><span data-stu-id="9c785-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="9c785-178">Rendern Sie immer verankerten Hologramme innerhalb von 3 Messgeräten, die von ihren Anker.</span><span class="sxs-lookup"><span data-stu-id="9c785-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="9c785-179">Stellen Sie sicher, dass Ihre Umgebung eingerichtet, für die ordnungsgemäße Überwachung ist.</span><span class="sxs-lookup"><span data-stu-id="9c785-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="9c785-180">Entwerfen Sie Ihrer Erfahrung Hologramme auf verschiedenen als zentrales Tiefenebenen innerhalb des Rahmens zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9c785-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-181">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-182">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-182">Documentation</span></span>

* [<span data-ttu-id="9c785-183">– Hologramm Stabilität und der Bildrate</span><span class="sxs-lookup"><span data-stu-id="9c785-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="9c785-184">Fallstudie, die mit der Stabilisierung-Ebene</span><span class="sxs-lookup"><span data-stu-id="9c785-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="9c785-185">Grundlegendes zur Leistung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9c785-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9c785-186">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="9c785-187">Raumanker</span><span class="sxs-lookup"><span data-stu-id="9c785-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="9c785-188">Behandeln von Fehlern der nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="9c785-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="9c785-189">Feststehende Verweisrahmen</span><span class="sxs-lookup"><span data-stu-id="9c785-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-190">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-190">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-191">MR Companion Kit Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="9c785-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="9c785-192">Hologramme Position auf echten Oberflächen</span><span class="sxs-lookup"><span data-stu-id="9c785-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="9c785-193">Fehler im Alignment von Hologramme mit physischer Objekte (sofern aneinander platziert werden soll) ist ein eindeutiger Hinweis darauf, der nicht-Union-Hologramme und reale.</span><span class="sxs-lookup"><span data-stu-id="9c785-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="9c785-194">Genauigkeit der Platzierung sollte relativ zu den Anforderungen des Szenarios werden. z. B. allgemeine Oberfläche Platzierung räumliche Zuordnung verwenden kann, aber eine präzisere Platzierung benötigen einige mit markern und Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="9c785-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-195">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-198">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-198">✔️</span></span></td>
        <td><span data-ttu-id="9c785-199">❌</span><span class="sxs-lookup"><span data-stu-id="9c785-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-200">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-200">Quality criteria</span></span>

|  <span data-ttu-id="9c785-201">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-201">Best</span></span>  |  <span data-ttu-id="9c785-202">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-202">Meets</span></span> |  <span data-ttu-id="9c785-203">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="9c785-204">Hologramme Ausrichten der Entwurfsoberfläche in der Regel in der Zentimeter Zoll-Bereich.</span><span class="sxs-lookup"><span data-stu-id="9c785-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="9c785-205">Wenn eine größere Genauigkeit erforderlich ist, sollte die app eine effiziente Möglichkeit für die Zusammenarbeit in der Spezifikation für die gewünschte app bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9c785-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="9c785-206">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="9c785-206">NA</span></span> | <span data-ttu-id="9c785-207">Die Hologramme angezeigt mit der physischen Zielobjekt nicht ausgerichtete durch Unterbrechen der Surface-Ebene oder auf von der Oberfläche "float" angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="9c785-208">Wenn Genauigkeit erforderlich ist, sollte die Hologramme die NEAR-Spezifikation des Szenarios erfüllen.</span><span class="sxs-lookup"><span data-stu-id="9c785-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-209">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-209">How to measure</span></span>

* <span data-ttu-id="9c785-210">Hologramme, die auf den spatial Karte platziert werden sollten nicht auf deutlich oberhalb oder unterhalb der Oberfläche "float" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9c785-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="9c785-211">Hologramme, die korrekte Platzierung erfordern sollte es sich um eine Form, Marker und Kalibrierung System verfügen, die auf das Szenario für die Anforderung wird.</span><span class="sxs-lookup"><span data-stu-id="9c785-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-212">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-212">Recommendations</span></span>

* <span data-ttu-id="9c785-213">Räumliche Zuordnung ist nützlich für das Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9c785-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="9c785-214">Verwenden Sie für die beste Genauigkeit Marker oder Poster der Hologramme und eine Xbox-Controller (oder einen Mechanismus für die manuelle Ausrichtung) fest für die endgültige Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="9c785-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="9c785-215">Berücksichtigen Sie sehr große Hologramme in logische Teile aufteilen und Ausrichtung der einzelnen Teile der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="9c785-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="9c785-216">Nicht ordnungsgemäß auswirken festgelegten interpupilary Entfernung (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) kann auch – Hologramm Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="9c785-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="9c785-217">Konfigurieren Sie immer die HoloLens, Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="9c785-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-218">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-219">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-219">Documentation</span></span>

* [<span data-ttu-id="9c785-220">Räumliche Zuordnung-Platzierung</span><span class="sxs-lookup"><span data-stu-id="9c785-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="9c785-221">Raum Scanvorgang</span><span class="sxs-lookup"><span data-stu-id="9c785-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="9c785-222">Bewährte Methoden von räumlichen Anker</span><span class="sxs-lookup"><span data-stu-id="9c785-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="9c785-223">Behandeln von Fehlern der nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="9c785-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="9c785-224">Räumliche Abbildung in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="9c785-225">Übersicht über die Entwicklung von Vuforia</span><span class="sxs-lookup"><span data-stu-id="9c785-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-226">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-226">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-227">MR räumlich 230: Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="9c785-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="9c785-228">Räumliche Zuordnung Bibliotheken MR Toolkit</span><span class="sxs-lookup"><span data-stu-id="9c785-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="9c785-229">MR Companion Kit Poster Kalibrierung-Beispiel</span><span class="sxs-lookup"><span data-stu-id="9c785-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="9c785-230">MR Companion Kit Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="9c785-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="9c785-231">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="9c785-231">External references</span></span>

* [<span data-ttu-id="9c785-232">Fallstudie Lowes Genauigkeit Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="9c785-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="9c785-233">Anzeigen der Zone der Komfort</span><span class="sxs-lookup"><span data-stu-id="9c785-233">Viewing zone of comfort</span></span>

<span data-ttu-id="9c785-234">App-Entwickler-Steuerelement, in denen Benutzer Augen konvergieren, durch die Platzierung von Inhalt und Hologramme in verschiedenen Ebenen.</span><span class="sxs-lookup"><span data-stu-id="9c785-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="9c785-235">Benutzern steht, geteert HoloLens werden immer berücksichtigen, auf 2.0m zu verwalten, ein klares Bild da HoloLens angezeigt sind in einer optischen Abstand ungefähr 2.0m von der Benutzer fest.</span><span class="sxs-lookup"><span data-stu-id="9c785-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="9c785-236">Ungültige Content Tiefe kann visual angefasst oder Ermüdung führen.</span><span class="sxs-lookup"><span data-stu-id="9c785-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-237">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-240">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-240">✔️</span></span></td>
        <td><span data-ttu-id="9c785-241">❌</span><span class="sxs-lookup"><span data-stu-id="9c785-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-242">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="9c785-243">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="9c785-244">Legen Sie Inhalte auf 2m ein.</span><span class="sxs-lookup"><span data-stu-id="9c785-244">Place content at 2m.</span></span></li><li><span data-ttu-id="9c785-245">Wenn Hologramme können nicht auf 2m platziert werden und Konflikte zwischen Konvergenz und beeinflusst nicht vermieden werden, liegt die optimale Zone für die Platzierung von – Hologramm 1,25 m "und" 5 Min.</span><span class="sxs-lookup"><span data-stu-id="9c785-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="9c785-246">In jedem Fall sollte Designer Struktur Inhalt empfehlen Benutzern die Interaktion von 1 + m entfernt (z. B. Inhaltsgröße anpassen und die Positionierungsparameter des Standard).</span><span class="sxs-lookup"><span data-stu-id="9c785-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="9c785-247">Es sei denn, die explizit nicht von dem Szenario erforderlich ist, sollte eine Clippingebene implementieren mit Fadeout beginnend mit 1 Million.</span><span class="sxs-lookup"><span data-stu-id="9c785-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="9c785-248">In Fällen, in denen genauer Beobachtung von einem bewegungslos Hologramm erforderlich ist, sollte der Inhalt nicht als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="9c785-249">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-249">Meets</span></span></td><td> <span data-ttu-id="9c785-250">Der Inhalt ist in der Anleitung anzeigen und während der Übertragung, aber nicht ordnungsgemäße sprachnutzung oder keine Verwendung von den Clipping-Ebene.</span><span class="sxs-lookup"><span data-stu-id="9c785-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9c785-251">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-251">Fail</span></span> </td><td> <span data-ttu-id="9c785-252">Der Inhalt zu nahe dargestellt wird (in der Regel &lt;1,25 m oder &lt;50 cm für stationäre Hologramme genauer Beobachtung erfordern.)</span><span class="sxs-lookup"><span data-stu-id="9c785-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="9c785-253">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-253">How to measure</span></span>

* <span data-ttu-id="9c785-254">Der Inhalt muss in der Regel 2 m entfernt, jedoch nicht näher als 1,25 oder weiter als 5 Min. entsprechen.</span><span class="sxs-lookup"><span data-stu-id="9c785-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="9c785-255">Mit wenigen Ausnahmen sollte die HoloLens Clipping Render-Entfernung auf .85CM mit Fadeout von Inhalten, die beginnend bei 1 Mio. festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="9c785-256">Ansatz des Inhalts, und notieren Sie den Freistellungseffekt-Ebene.</span><span class="sxs-lookup"><span data-stu-id="9c785-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="9c785-257">Stationär Inhalt darf nicht als 50 cm entfernt sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-258">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-258">Recommendations</span></span>

* <span data-ttu-id="9c785-259">Entwerfen Sie Inhalte für die optimale Anzeige Entfernung 2 m ein.</span><span class="sxs-lookup"><span data-stu-id="9c785-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="9c785-260">Legen Sie die Entfernung des Clipping gerendert, auf 85cm mit Fadeout von Inhalten, die beginnend bei 1 Million.</span><span class="sxs-lookup"><span data-stu-id="9c785-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="9c785-261">Für stationäre Hologramme, die näher anzeigen, sollten die Clipping-Ebene nicht näher als 30cm und Fadeout sollte mindestens 10cm Weg von den Clipping-Ebene beginnen.</span><span class="sxs-lookup"><span data-stu-id="9c785-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-262">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-262">Resources</span></span>

* [<span data-ttu-id="9c785-263">Rendern von Abstand</span><span class="sxs-lookup"><span data-stu-id="9c785-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="9c785-264">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="9c785-265">Experimentieren mit der Skalierung</span><span class="sxs-lookup"><span data-stu-id="9c785-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="9c785-266">Text Schriftgrad empfohlen</span><span class="sxs-lookup"><span data-stu-id="9c785-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="9c785-267">Tiefe wechseln</span><span class="sxs-lookup"><span data-stu-id="9c785-267">Depth switching</span></span>

<span data-ttu-id="9c785-268">Unabhängig von der Zone der Komfort Probleme anzeigen fordert für den Benutzer häufig oder schnell wechseln, in der Nähe, und viel als zentrales Objekte (einschließlich Hologramme und den tatsächlichen Inhalt) oculomotor Fatigue und allgemeine angefasst führen können.</span><span class="sxs-lookup"><span data-stu-id="9c785-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-269">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-272">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-272">✔️</span></span></td>
        <td><span data-ttu-id="9c785-273">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-274">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-274">Quality criteria</span></span>

|  <span data-ttu-id="9c785-275">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-275">Best</span></span>  |  <span data-ttu-id="9c785-276">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-276">Meets</span></span> |  <span data-ttu-id="9c785-277">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-278">Eingeschränkte oder natürliche Tiefe wechseln, die nicht dazu führen, dass den Benutzer, neuer Nachklang Fokus.</span><span class="sxs-lookup"><span data-stu-id="9c785-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="9c785-279">Switch abrupten Tiefe, dies ist der Kern und in der app-Erfahrung konzipiert, oder abrupten Tiefe-Switch, der von unerwarteten realen Inhalt verursacht wird.</span><span class="sxs-lookup"><span data-stu-id="9c785-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="9c785-280">Einheitliche Tiefe Switch oder abrupten Tiefe wechseln, die nicht erforderlich ist oder Core, um die app-Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="9c785-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-281">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-281">How to measure</span></span>

* <span data-ttu-id="9c785-282">Wenn den Benutzer konsistent und/oder plötzlich Tiefe ändern Sie den Fokus von der app erforderlich sind, ist Tiefe Problem wechseln.</span><span class="sxs-lookup"><span data-stu-id="9c785-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-283">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-283">Recommendations</span></span>

* <span data-ttu-id="9c785-284">Behalten Sie Hauptinhalt an einer konsistenten als zentrales Ebene bei, und stellen Sie sicher, dass die Stabilisierung-Ebene auf dieser Ebene entspricht.</span><span class="sxs-lookup"><span data-stu-id="9c785-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="9c785-285">Dies lässt sich durch oculomotor Fatigue und unerwartete – Hologramm Bewegung beheben.</span><span class="sxs-lookup"><span data-stu-id="9c785-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-286">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-286">Resources</span></span>

* [<span data-ttu-id="9c785-287">Rendern von Abstand</span><span class="sxs-lookup"><span data-stu-id="9c785-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="9c785-288">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="9c785-289">Von räumlichen Sounds</span><span class="sxs-lookup"><span data-stu-id="9c785-289">Use of spatial sound</span></span>

<span data-ttu-id="9c785-290">In Windows Mixed Reality bietet das Audiomodul der sehen die mixed Reality-Erfahrung durch Simulieren von 3D sound mithilfe von environmental Simulationen, Entfernung und Richtung.</span><span class="sxs-lookup"><span data-stu-id="9c785-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="9c785-291">Verwenden von räumlichen Sound in einer Anwendung kann Entwickler convincingly Platzieren von Sounds in einem 3 dimensionalen Raum (Kugel) für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9c785-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="9c785-292">Diese Sounds werden dann erscheinen, als ob sie von echten physischen Objekten oder der mixed Reality-Hologramme in der benutzerumgebung gestellt würden.</span><span class="sxs-lookup"><span data-stu-id="9c785-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="9c785-293">Räumliche Sound ist ein leistungsstarkes Tool zum Immersion, Barrierefreiheit und UX-Entwurf in mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="9c785-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-294">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-297">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-297">✔️</span></span></td>
        <td><span data-ttu-id="9c785-298">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-299">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-299">Quality criteria</span></span>

|  <span data-ttu-id="9c785-300">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-300">Best</span></span>  |  <span data-ttu-id="9c785-301">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-301">Meets</span></span> |  <span data-ttu-id="9c785-302">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-303">Sound wird logisch spatialized und die UX entsprechend Sound verwendet, zur Unterstützung bei der Objekt-Ermittlung und Benutzerfeedback.</span><span class="sxs-lookup"><span data-stu-id="9c785-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="9c785-304">Sound ist die natürliche und auf Objekte relevant und eine normalisierte, über das Szenario.</span><span class="sxs-lookup"><span data-stu-id="9c785-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="9c785-305">Räumliche Audio ist entsprechend für Believability verwendet jedoch fehlen als Mittel, um Feedback von Benutzern und die Auffindbarkeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9c785-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="9c785-306">Sound wird nicht wie erwartet, spatialized und/oder fehlende Sound bei der Benutzer in der UX.</span><span class="sxs-lookup"><span data-stu-id="9c785-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="9c785-307">Räumliche Audio wurde oder nicht berücksichtigt, die in den Entwurf des Szenarios verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c785-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-308">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-308">How to measure</span></span>

* <span data-ttu-id="9c785-309">Im Allgemeinen sollte die relevanten Sounds von Ziel-Hologramme ausgeben (z. b., Rinde Sound holographic Hund stammen.)</span><span class="sxs-lookup"><span data-stu-id="9c785-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="9c785-310">Sound Hinweise sollten in der UX verwendet werden, um dem Benutzer Feedback oder Kenntnis der Aktionen außerhalb der holographic Frame zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9c785-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-311">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-311">Recommendations</span></span>

* <span data-ttu-id="9c785-312">Verwenden Sie räumliche Audio, zur Unterstützung bei der Ermittlung und Benutzer-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="9c785-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="9c785-313">Echte Sounds besser funktionieren als synthetisier oder unnatürlichen Sound.</span><span class="sxs-lookup"><span data-stu-id="9c785-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="9c785-314">Die meisten Sounds sollten spatialized sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="9c785-315">Vermeiden Sie unsichtbar korrekturemitter ab.</span><span class="sxs-lookup"><span data-stu-id="9c785-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="9c785-316">Vermeiden Sie räumliche Maskierung.</span><span class="sxs-lookup"><span data-stu-id="9c785-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="9c785-317">Alle Sounds zu normalisieren.</span><span class="sxs-lookup"><span data-stu-id="9c785-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-318">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-319">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-319">Documentation</span></span>

* [<span data-ttu-id="9c785-320">Raumklang</span><span class="sxs-lookup"><span data-stu-id="9c785-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="9c785-321">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="9c785-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="9c785-322">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="9c785-323">Fallstudie für HoloTour sound räumlich</span><span class="sxs-lookup"><span data-stu-id="9c785-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="9c785-324">Verwenden von räumlichen Sound in RoboRaid Fallstudie</span><span class="sxs-lookup"><span data-stu-id="9c785-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-325">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-325">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-326">MR räumlich 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="9c785-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="9c785-327">MRToolkit, Spatial Audio</span><span class="sxs-lookup"><span data-stu-id="9c785-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="9c785-328">Konzentrieren Sie sich an holographic Frame (Blickfeld) Grenzen</span><span class="sxs-lookup"><span data-stu-id="9c785-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="9c785-329">Gut gestaltete Benutzeroberflächen erstellen und Warten von nützlichen Kontext der virtuellen Umgebung, die über die Benutzer erweitert.</span><span class="sxs-lookup"><span data-stu-id="9c785-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="9c785-330">Einen durchdachten Entwurf Content skalierungs-und Kontext umfasst die Minderung der Auswirkungen der Blickfeld Grenzen, die räumliche Audio, Anleitungen, Systeme und Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="9c785-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="9c785-331">Wenn rechts durchgeführt wird, wird den Benutzer, dass weniger durch das Blickfeld Grenzen eingeschränkt, während Sie eine sich app-Erfahrung so aussehen.</span><span class="sxs-lookup"><span data-stu-id="9c785-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-332">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-335">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-335">✔️</span></span></td>
        <td><span data-ttu-id="9c785-336">❌</span><span class="sxs-lookup"><span data-stu-id="9c785-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-337">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-337">Quality criteria</span></span>

|  <span data-ttu-id="9c785-338">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-338">Best</span></span>  |  <span data-ttu-id="9c785-339">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-339">Meets</span></span> |  <span data-ttu-id="9c785-340">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-341">Benutzer verliert nie Kontext und Anzeigen von vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="9c785-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="9c785-342">Unterstützung der Kontext wird für große Objekte bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="9c785-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="9c785-343">Auffindbarkeit und Anzeigen von Anweisungen für Objekte außerhalb des Rahmens bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="9c785-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="9c785-344">Im Allgemeinen sind die Motion-Entwurf und die Skalierung der Hologramme für eine vertraut Anzeigefunktionen geeignet.</span><span class="sxs-lookup"><span data-stu-id="9c785-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="9c785-345">Benutzer werden niemals Kontext verliert, aber in bestimmten Situationen möglicherweise zusätzliche trichterhalses während der Übertragung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9c785-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="9c785-346">In bestimmten Situationen wird Skalierung Hologramme entweder vertikal oder horizontal Frames verursacht manche Bewegung trichterhalses Hologramme anzeigen zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="9c785-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="9c785-347">Wahrscheinlich Kontext und/oder konsistente trichterhalses Motion verlieren Benutzer ist erforderlich, um Hologramme anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9c785-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="9c785-348">Kein Kontext für große Objekte holographic, Verschieben von Objekten außerhalb des Rahmens ohne Erkennbarkeit Anleitungen oder hohe Hologramme verliert einfach gefordert regulären trichterhalses während der Übertragung an.</span><span class="sxs-lookup"><span data-stu-id="9c785-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-349">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-349">How to measure</span></span>

* <span data-ttu-id="9c785-350">Kontext für eine (groß) – Hologramm verloren geht oder aufgrund der an den Grenzen freigestellt wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="9c785-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="9c785-351">Speicherort der Hologramme sind schwer zu finden, die aufgrund des Mangels an Aufmerksamkeit Directors oder Inhalte, die schnell in und aus der holografischen Frame verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="9c785-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="9c785-352">Szenario erfordert regelmäßige und sich wiederholende nach oben oder unten Head während der Übertragung ein Hologramm, wodurch trichterhalses Ermüdung vollständig angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9c785-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-353">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-353">Recommendations</span></span>

* <span data-ttu-id="9c785-354">Starten Sie die Benutzeroberfläche, mit kleine Objekte, die das Blickfeld anpassen, mit visuellen Hinweise auf größeren Versionen wechseln.</span><span class="sxs-lookup"><span data-stu-id="9c785-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="9c785-355">Verwenden Sie räumliche Audio- und Aufmerksamkeit Directors, um Benutzerinhalte suchen, die sich das Blickfeld.</span><span class="sxs-lookup"><span data-stu-id="9c785-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="9c785-356">Vermeiden Sie so weit wie möglich, Hologramme, die das Blickfeld vertikal zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="9c785-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="9c785-357">Geben Sie dem Benutzer mit in-app-Anleitung für die optimale Anzeige Speicherort ein.</span><span class="sxs-lookup"><span data-stu-id="9c785-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-358">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-359">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-359">Documentation</span></span>

* [<span data-ttu-id="9c785-360">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="9c785-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="9c785-361">Fallstudie, HoloStudio UI und Interaktion entwerfen Erkenntnisse</span><span class="sxs-lookup"><span data-stu-id="9c785-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="9c785-362">Skalieren von Objekten und Umgebungen</span><span class="sxs-lookup"><span data-stu-id="9c785-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="9c785-363">Cursor, visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="9c785-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="9c785-364">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="9c785-364">External references</span></span>

* [<span data-ttu-id="9c785-365">ActiveX Data Objects und das Blickfeld</span><span class="sxs-lookup"><span data-stu-id="9c785-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="9c785-366">Inhalte reagiert an Benutzerposition</span><span class="sxs-lookup"><span data-stu-id="9c785-366">Content reacts to user position</span></span>

<span data-ttu-id="9c785-367">Hologramme sollte auf die Benutzerposition auf ungefähr die gleiche Weise reagieren, die "echten" Objekte.</span><span class="sxs-lookup"><span data-stu-id="9c785-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="9c785-368">Eine wichtige Design-Herausforderungen ist UI-Elemente, die unbedingt eines Benutzers Position können nicht davon ausgehen nicht bewegt wird und sich Anpassen des Benutzers während der Übertragung.</span><span class="sxs-lookup"><span data-stu-id="9c785-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="9c785-369">Das Entwerfen einer app, die ordnungsgemäß an Benutzerposition anpasst erstellt eine mehr glaubwürdig Erfahrung und einfacher zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9c785-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-370">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-373">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-373">✔️</span></span></td>
        <td><span data-ttu-id="9c785-374">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-375">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="9c785-376">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-376">Best</span></span> </td><td> <span data-ttu-id="9c785-377">Inhalt und die Benutzeroberfläche anpassen an Benutzerpositionen, die Benutzer auf natürliche Weise mit Inhalt innerhalb des Bereichs der erwarteten Benutzer datenverschiebung kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="9c785-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9c785-378">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-378">Meets</span></span> </td><td> <span data-ttu-id="9c785-379">Benutzeroberfläche passt sich an die Benutzerposition an, aber Sie können die Ansicht der Aufforderung des Benutzers zum Anpassen ihrer Position schlüsselinhalt behindern.</span><span class="sxs-lookup"><span data-stu-id="9c785-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9c785-380">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="9c785-381">UI-Elemente sind verloren gegangen oder gesperrt, während der Verschiebung zu Benutzer Steuerelemente Nachklang zurück zu (oder suchen).</span><span class="sxs-lookup"><span data-stu-id="9c785-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="9c785-382">UI-Elemente begrenzen, die Ansicht der Hauptinhalt.</span><span class="sxs-lookup"><span data-stu-id="9c785-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="9c785-383">UI-Bewegung ist nicht optimiert, für die Anzeige von Abstand und Momentum, insbesondere bei <a href="billboarding-and-tag-along.md">Tag-along</a> UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="9c785-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="9c785-384">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-384">How to measure</span></span>

* <span data-ttu-id="9c785-385">Alle Messungen sollte innerhalb eines angemessenen Bereichs des Szenarios ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="9c785-386">Während der Verschiebung des Benutzers variieren kann, versuchen Sie nicht dazu bringen, die app mit extremer Benutzer verschieben.</span><span class="sxs-lookup"><span data-stu-id="9c785-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="9c785-387">Für Benutzeroberflächenelemente sollte relevante Steuerelemente zur Verfügung, unabhängig von der Benutzer verschieben.</span><span class="sxs-lookup"><span data-stu-id="9c785-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="9c785-388">Z. B., wenn der Benutzer wird durchlaufen, um eine 3D Karte mit Zoom und zum Anzeigen, sollte das Zoomsteuerelement für den Benutzer unabhängig vom Standort sofort verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-389">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-389">Recommendations</span></span>

* <span data-ttu-id="9c785-390">Der Benutzer die Kamera und steuern sie die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="9c785-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="9c785-391">Sie steuern können.</span><span class="sxs-lookup"><span data-stu-id="9c785-391">Let them drive.</span></span>
* <span data-ttu-id="9c785-392">Betrachten Sie billboarding für Text und Menüs-Systeme, die andernfalls Welt gesperrt oder verdeckt wird, wenn ein Benutzer verschoben wurden.</span><span class="sxs-lookup"><span data-stu-id="9c785-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="9c785-393">Verwenden Sie Tag-along für Inhalte, die folgen dem Benutzer während nach wie vor den Benutzer angezeigt, was vorangestellt ist.</span><span class="sxs-lookup"><span data-stu-id="9c785-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-394">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-395">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-395">Documentation</span></span>

* [<span data-ttu-id="9c785-396">Entwerfen für</span><span class="sxs-lookup"><span data-stu-id="9c785-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="9c785-397">Farbe, Material und Licht</span><span class="sxs-lookup"><span data-stu-id="9c785-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="9c785-398">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="9c785-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9c785-399">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="9c785-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9c785-400">Self-motion und Benutzer Locomotion</span><span class="sxs-lookup"><span data-stu-id="9c785-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-401">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-401">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-402">MR-Eingabe 210: Anvisieren</span><span class="sxs-lookup"><span data-stu-id="9c785-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="9c785-403">Eingabe Interaktion Klarheit</span><span class="sxs-lookup"><span data-stu-id="9c785-403">Input interaction clarity</span></span>

<span data-ttu-id="9c785-404">Eingabe Interaktion Klarheit ist wichtig, zu der app-benutzerfreundlichkeit und umfassen Eingabe Konsistenz, Zugänglichkeit, Auffindbarkeit der Interaction-Methode.</span><span class="sxs-lookup"><span data-stu-id="9c785-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="9c785-405">Benutzer sollten plattformweiten allgemeine Aktivitäten ohne erlernen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="9c785-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="9c785-406">Wenn die app benutzerdefinierte Eingabe hat, muss klar kommuniziert und veranschaulicht werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-407">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-410">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-410">✔️</span></span></td>
        <td><span data-ttu-id="9c785-411">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-412">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-412">Quality criteria</span></span>

|  <span data-ttu-id="9c785-413">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-413">Best</span></span>  |  <span data-ttu-id="9c785-414">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-414">Meets</span></span> |  <span data-ttu-id="9c785-415">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-416">Eingabe Interaction-Methode sind konsistent mit den Windows Mixed Reality bereitgestellten [Anleitungen](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="9c785-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="9c785-417">Eine benutzerdefinierte Eingabe muss sollte nicht in Hinblick auf die Standardeingabe (stattdessen Verwendung standard Interaktion) werden deutlich kommuniziert und gezeigt, um den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9c785-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="9c785-418">Ähnlich wie bei der bewährten, aber benutzerdefinierte Eingaben, die mit standardmäßigen Eingabemethoden redundant sind.</span><span class="sxs-lookup"><span data-stu-id="9c785-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="9c785-419">Benutzer kann weiterhin die Ziel und den Fortschritt über die app-Funktionalität erreichen.</span><span class="sxs-lookup"><span data-stu-id="9c785-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="9c785-420">Schwierig, input Methode oder eine Schaltfläche-Zuordnung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="9c785-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="9c785-421">Eingabe stark angepasst wird, unterstützt nicht die Standardeingabe, keine Anweisungen oder Fatigue und Komfort Probleme verursachen.</span><span class="sxs-lookup"><span data-stu-id="9c785-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-422">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-422">How to measure</span></span>

* <span data-ttu-id="9c785-423">Die app verwendet einheitliche [Standard Eingabe Methoden.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="9c785-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="9c785-424">Wenn die app ist Eingabe hat, wird sie eindeutig über kommuniziert:</span><span class="sxs-lookup"><span data-stu-id="9c785-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="9c785-425">Eindrucks beim ersten Ausführen</span><span class="sxs-lookup"><span data-stu-id="9c785-425">First-run experience</span></span>
* <span data-ttu-id="9c785-426">Einführende Bildschirme</span><span class="sxs-lookup"><span data-stu-id="9c785-426">Introductory screens</span></span>
* <span data-ttu-id="9c785-427">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="9c785-427">Tooltips</span></span>
* <span data-ttu-id="9c785-428">Hand-coach</span><span class="sxs-lookup"><span data-stu-id="9c785-428">Hand coach</span></span>
* <span data-ttu-id="9c785-429">Hilfe</span><span class="sxs-lookup"><span data-stu-id="9c785-429">Help section</span></span>
* <span data-ttu-id="9c785-430">Voice-over</span><span class="sxs-lookup"><span data-stu-id="9c785-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-431">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-431">Recommendations</span></span>

* <span data-ttu-id="9c785-432">Verwenden Sie die standard-Eingabe-Methoden nach Möglichkeit.</span><span class="sxs-lookup"><span data-stu-id="9c785-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="9c785-433">Geben Sie Demos, Lernprogramme und QuickInfos für nicht standardmäßige Eingabemethoden an.</span><span class="sxs-lookup"><span data-stu-id="9c785-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="9c785-434">Verwenden Sie eine konsistente Interaktionsmodell in der gesamten app.</span><span class="sxs-lookup"><span data-stu-id="9c785-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-435">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-436">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-436">Documentation</span></span>

* [<span data-ttu-id="9c785-437">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="9c785-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9c785-438">Es Objekte</span><span class="sxs-lookup"><span data-stu-id="9c785-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="9c785-439">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="9c785-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9c785-440">Cursor</span><span class="sxs-lookup"><span data-stu-id="9c785-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9c785-441">Komfort und Blicke</span><span class="sxs-lookup"><span data-stu-id="9c785-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="9c785-442">Gesten</span><span class="sxs-lookup"><span data-stu-id="9c785-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="9c785-443">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="9c785-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="9c785-444">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="9c785-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="9c785-445">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="9c785-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="9c785-446">Leitfaden für Eingabeportierung für Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="9c785-447">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="9c785-448">Anvisieren in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="9c785-449">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="9c785-450">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="9c785-451">Tastatur-, Maus- und Controllereingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="9c785-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="9c785-452">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="9c785-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="9c785-453">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="9c785-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="9c785-454">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="9c785-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-455">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-455">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-456">Fallstudie: Das Streben nach persönlichere Datenverarbeitung</span><span class="sxs-lookup"><span data-stu-id="9c785-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="9c785-457">CAST-Studie: Entwerfen von HoloStudio UI und Interaktion Erkenntnisse</span><span class="sxs-lookup"><span data-stu-id="9c785-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="9c785-458">Beispiel-app: Periodisch-Tabelle der Elemente</span><span class="sxs-lookup"><span data-stu-id="9c785-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="9c785-459">Beispiel-app: Mondkalender-Modul</span><span class="sxs-lookup"><span data-stu-id="9c785-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="9c785-460">MR-Eingabe 210: Anvisieren</span><span class="sxs-lookup"><span data-stu-id="9c785-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="9c785-461">MR-Eingabe 211: Gesten</span><span class="sxs-lookup"><span data-stu-id="9c785-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="9c785-462">MR-Eingabe 212: Sprache</span><span class="sxs-lookup"><span data-stu-id="9c785-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="9c785-463">Es Objekte</span><span class="sxs-lookup"><span data-stu-id="9c785-463">Interactable objects</span></span>

<span data-ttu-id="9c785-464">Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt.</span><span class="sxs-lookup"><span data-stu-id="9c785-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="9c785-465">In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="9c785-466">Alles kann ein es Objekt sein, die ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="9c785-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="9c785-467">Ein Objekt es kann als etwas von einer Tasse Kaffee für die Tabelle, eine Gleitkommazahl in der Luft Sprechblase dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="9c785-468">Unabhängig von der Art sollte es Objekte vom Benutzer über SEH- und Hinweise klar erkennbar sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-469">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-472">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-472">✔️</span></span></td>
        <td><span data-ttu-id="9c785-473">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-474">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-474">Quality criteria</span></span>

|  <span data-ttu-id="9c785-475">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-475">Best</span></span>  |  <span data-ttu-id="9c785-476">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-476">Meets</span></span> |  <span data-ttu-id="9c785-477">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-478">Unabhängig von der Form, es Objekte sind über SEH- und Hinweise erkennbaren über drei Zustände: im Leerlauf, Ziel und ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="9c785-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="9c785-479">"Es noch einmal finden Sie unter" ist klarer und konsistent über die Umgebung verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c785-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="9c785-480">Objekte werden skaliert und verteilt, um für fehlerfrei zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="9c785-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="9c785-481">Benutzer können erkennen Objekt als es durch Audio- oder visuelle Feedback, und als Ziel und aktivieren Sie das Objekt.</span><span class="sxs-lookup"><span data-stu-id="9c785-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="9c785-482">Wenn kein visual oder audio-Hinweise, kann Benutzer ein Objekt es nicht erkennen.</span><span class="sxs-lookup"><span data-stu-id="9c785-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="9c785-483">Interaktionen sind Fehler aufgrund von Objekt skalieren oder den Abstand zwischen den Objekten entstehen.</span><span class="sxs-lookup"><span data-stu-id="9c785-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-484">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-484">How to measure</span></span>

* <span data-ttu-id="9c785-485">Es stehen nebenbei gesagt, immer "es"; bestimmte Schaltflächen, Menüs und app-Inhalte, einschließlich.</span><span class="sxs-lookup"><span data-stu-id="9c785-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="9c785-486">Als Faustregel dürfte eine Orientierungshilfe SEH- und wenn es Objekte.</span><span class="sxs-lookup"><span data-stu-id="9c785-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-487">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-487">Recommendations</span></span>

* <span data-ttu-id="9c785-488">Verwenden Sie SEH- und Feedback für Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="9c785-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="9c785-489">Visuelles Feedback sollte unterschieden werden, für jede Zustand (im Leerlauf, gezielte, ausgewählte)</span><span class="sxs-lookup"><span data-stu-id="9c785-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="9c785-490">Es Objekte skaliert, und für die Zielgruppenadressierung fehlerfrei platziert.</span><span class="sxs-lookup"><span data-stu-id="9c785-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="9c785-491">Gruppierte es Objekte (z. B. eine Menüleiste oder Liste) sollte die richtigen Abstand für die Zielplattform verfügen.</span><span class="sxs-lookup"><span data-stu-id="9c785-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="9c785-492">Schaltflächen und Menüs, die Stimme-Befehl unterstützen sollten die Beschriftungen bereitstellen, für das Befehl-Schlüsselwort ("angezeigt, das so sagen")</span><span class="sxs-lookup"><span data-stu-id="9c785-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-493">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-494">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-494">Documentation</span></span>

* [<span data-ttu-id="9c785-495">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="9c785-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9c785-496">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="9c785-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="9c785-497">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="9c785-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9c785-498">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="9c785-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-499">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-499">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-500">Mixed Reality-Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="9c785-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="9c785-501">Raum Scannen</span><span class="sxs-lookup"><span data-stu-id="9c785-501">Room scanning</span></span>

<span data-ttu-id="9c785-502">Apps, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv.</span><span class="sxs-lookup"><span data-stu-id="9c785-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="9c785-503">Der Vollständigkeit und die Qualität der Daten hängt von einer Reihe von Faktoren wie der Menge der, die der Benutzer ausgeführt hat, wie viel Zeit verstrichen ist, da die Auswertung und gibt an, ob die Objekte, z. B. Möbel und Türen verschoben haben, da das Gerät über den Bereich überprüft.</span><span class="sxs-lookup"><span data-stu-id="9c785-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="9c785-504">Viele apps werden analysiert, die räumliche Zuordnungsdaten zu Beginn der Umgebung zu beurteilen, ob der Benutzer zusätzliche Schritte zur Verbesserung der Vollständigkeit und die Qualität der räumliche Zuordnung ausführen soll.</span><span class="sxs-lookup"><span data-stu-id="9c785-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="9c785-505">Wenn der Benutzer erforderlich ist, um die Überprüfung der Umgebung, klar, dass während der Überprüfung Oberfläche Anleitungen bereitgestellt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="9c785-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-506">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-509">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-509">✔️</span></span></td>
        <td><span data-ttu-id="9c785-510">❌</span><span class="sxs-lookup"><span data-stu-id="9c785-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-511">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-511">Quality criteria</span></span>

|  <span data-ttu-id="9c785-512">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-512">Best</span></span>  |  <span data-ttu-id="9c785-513">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-513">Meets</span></span> |  <span data-ttu-id="9c785-514">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-515">Visualisierung der räumlichen Mesh erkennen Sie, dass Benutzer, die Überprüfung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="9c785-516">Benutzer werden eindeutig weiß, was zu tun ist und wenn die Überprüfung wird gestartet und angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="9c785-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="9c785-517">Visualisierung der räumlichen Mesh angegeben ist, ist aber der Benutzer wissen möglicherweise nicht klar, was zu tun ist und keine Statusinformationen.</span><span class="sxs-lookup"><span data-stu-id="9c785-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="9c785-518">Keine Visualisierung des Mesh.</span><span class="sxs-lookup"><span data-stu-id="9c785-518">No visualization of mesh.</span></span> <span data-ttu-id="9c785-519">Keine Informationen bereitgestellt, um dem Benutzer, wo Sie suchen, oder wenn die Überprüfung startet/beendet wird.</span><span class="sxs-lookup"><span data-stu-id="9c785-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9c785-520">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-520">How to measure</span></span>

* <span data-ttu-id="9c785-521">SEH- und bei der Überprüfung erforderlichen Platz bietet es Anleitungen, der angibt, wo gesucht werden soll, und wann starten und beenden zu scannen.</span><span class="sxs-lookup"><span data-stu-id="9c785-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-522">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-522">Recommendations</span></span>

* <span data-ttu-id="9c785-523">Geben Sie an, welcher Anteil der Gesamtgröße des Datenträgers in der Nähe der Benutzer muss in der Umgebung sein.</span><span class="sxs-lookup"><span data-stu-id="9c785-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="9c785-524">Wenn die Überprüfung wird gestartet und beendet werden, z. B. eine Statusanzeige zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="9c785-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="9c785-525">Verwenden Sie eine Visualisierung des Netzes während der Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="9c785-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="9c785-526">Geben Sie SEH- und Hinweise, um den Benutzern suchen, und bewegen den Raum empfehlen.</span><span class="sxs-lookup"><span data-stu-id="9c785-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="9c785-527">Informieren Sie den Benutzer, wohin Sie wechseln, um die Daten zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="9c785-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="9c785-528">In vielen Fällen ist es möglicherweise am besten, die dem Benutzer mitzuteilen, was sie (z. B. die Obergrenze suchen hinter Möbel ansehen), um die Überprüfung der erforderlichen Qualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9c785-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-529">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9c785-530">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9c785-530">Documentation</span></span>

* [<span data-ttu-id="9c785-531">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="9c785-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="9c785-532">Fallstudie: Erweitern die räumlichen Funktionen für die Zuordnung von HoloLens</span><span class="sxs-lookup"><span data-stu-id="9c785-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="9c785-533">Fallstudie: Räumliche Entwurf für HoloTour</span><span class="sxs-lookup"><span data-stu-id="9c785-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="9c785-534">Fallstudie: Erstellen ein Eintauchen in Fragmenten</span><span class="sxs-lookup"><span data-stu-id="9c785-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9c785-535">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="9c785-535">Tools and tutorials</span></span>

* [<span data-ttu-id="9c785-536">Mixed Reality-Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="9c785-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="9c785-537">Direktionale Indikatoren</span><span class="sxs-lookup"><span data-stu-id="9c785-537">Directional indicators</span></span>

<span data-ttu-id="9c785-538">In einer mixed Reality-app Inhalt möglicherweise außerhalb der Sichtfeld oder von realen Objekten okkludiert.</span><span class="sxs-lookup"><span data-stu-id="9c785-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="9c785-539">Eine wohlgeformte-app wird für den Benutzer nicht sichtbaren Inhalt erleichtern.</span><span class="sxs-lookup"><span data-stu-id="9c785-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="9c785-540">Direktionale Indikatoren warnen ein Benutzers auf wichtige Inhalte und bieten eine Anleitung, um den Inhalt relativ zur Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="9c785-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="9c785-541">Anleitungen, die nicht sichtbaren Inhalt kann es sich um die Form der sound korrekturemitter ab, mithilfe von Richtungspfeilen oder direkte visuelle Hinweise haben.</span><span class="sxs-lookup"><span data-stu-id="9c785-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-542">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-545">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-545">✔️</span></span></td>
        <td><span data-ttu-id="9c785-546">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-547">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-547">Quality criteria</span></span>

|  <span data-ttu-id="9c785-548">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-548">Best</span></span>  |  <span data-ttu-id="9c785-549">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-549">Meets</span></span> |  <span data-ttu-id="9c785-550">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-551">SEH- und Hinweise führen den Benutzer direkt zu den relevanten Inhalten außerhalb Blickfeld.</span><span class="sxs-lookup"><span data-stu-id="9c785-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="9c785-552">Ein Pfeil, oder einige Indikator, der der Benutzer in die allgemeine Richtung an, der den Inhalt verweist.</span><span class="sxs-lookup"><span data-stu-id="9c785-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="9c785-553">Relevante Inhalte außerhalb der Sichtfeld, und eine schlechte oder kein Speicherort enthält Anweisungen für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9c785-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9c785-554">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-554">How to measure</span></span>

* <span data-ttu-id="9c785-555">Relevante Inhalte außerhalb der Sicht des Benutzers ist visual und/oder Hinweise ermittelt.</span><span class="sxs-lookup"><span data-stu-id="9c785-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-556">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-556">Recommendations</span></span>

* <span data-ttu-id="9c785-557">Verwenden Sie, wenn außerhalb des Benutzers Sichtfeld relevanten Inhalt ist ein direktionaler Indikatoren und Audiohinweise an den Benutzer auf den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="9c785-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="9c785-558">In vielen Fällen wird eine direkte visuelle Anleitung über Richtungspfeile bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="9c785-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="9c785-559">Direktionale Indikatoren sollten in den Cursor nicht erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="9c785-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-560">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-560">Resources</span></span>

* [<span data-ttu-id="9c785-561">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="9c785-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="9c785-562">Laden von Daten</span><span class="sxs-lookup"><span data-stu-id="9c785-562">Data loading</span></span>

<span data-ttu-id="9c785-563">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9c785-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="9c785-564">Dies kann bedeuten, dass der Benutzer mit der app interagieren nicht möglich, wenn die Statusanzeige angezeigt wird und auch angeben kann, wie lange die Wartezeit möglicherweise.</span><span class="sxs-lookup"><span data-stu-id="9c785-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9c785-565">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="9c785-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9c785-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9c785-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="9c785-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9c785-568">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-568">✔️</span></span></td>
        <td><span data-ttu-id="9c785-569">✔️</span><span class="sxs-lookup"><span data-stu-id="9c785-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9c785-570">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="9c785-570">Quality criteria</span></span>

|  <span data-ttu-id="9c785-571">Am besten</span><span class="sxs-lookup"><span data-stu-id="9c785-571">Best</span></span>  |  <span data-ttu-id="9c785-572">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="9c785-572">Meets</span></span> |  <span data-ttu-id="9c785-573">Fehler</span><span class="sxs-lookup"><span data-stu-id="9c785-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9c785-574">Animierte visueller Indikator in Form einer Statusanzeige oder Ring, das Aufzeigen von Fortschritten bei der keine Daten laden oder zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9c785-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="9c785-575">Der visuelle Indikator enthält Anleitungen, wie lange die Wartezeit werden konnte.</span><span class="sxs-lookup"><span data-stu-id="9c785-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="9c785-576">Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird, aber es gibt keinen Hinweis dafür, wie lange die Wartezeit sein kann.</span><span class="sxs-lookup"><span data-stu-id="9c785-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="9c785-577">Kein Laden von Daten oder die Prozess-Indikatoren für die Aufgabe, die länger als 5 Sekunden dauert.</span><span class="sxs-lookup"><span data-stu-id="9c785-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9c785-578">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="9c785-578">How to measure</span></span>

* <span data-ttu-id="9c785-579">Stellen Sie sicher, dass es mehr als 5 Sekunden ist kein leerer Zustand, beim Laden der Daten.</span><span class="sxs-lookup"><span data-stu-id="9c785-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9c785-580">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9c785-580">Recommendations</span></span>

* <span data-ttu-id="9c785-581">Geben Sie eine Data Loading Animator-aufzeigen von Fortschritten in allen Fällen, wenn der Benutzer diese app abgestürzt ist oder die Beantwortung wahrnehmen könnten.</span><span class="sxs-lookup"><span data-stu-id="9c785-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="9c785-582">Eine gute Faustregel ist, alle "laden"-Aktivität, die mehr als 5 Sekunden dauern.</span><span class="sxs-lookup"><span data-stu-id="9c785-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="9c785-583">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="9c785-583">Resources</span></span>

* [<span data-ttu-id="9c785-584">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="9c785-584">Displaying progress</span></span>](progress.md)
