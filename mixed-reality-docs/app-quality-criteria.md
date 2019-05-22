---
title: Qualitätskriterien für die App
description: Dieses Dokument beschreibt die obersten Faktoren, die Auswirkungen auf die Qualität von mixed Reality-apps.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, mixed Reality, mixed Reality-app
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974748"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="75310-104">Qualitätskriterien für die App</span><span class="sxs-lookup"><span data-stu-id="75310-104">App quality criteria</span></span>

<span data-ttu-id="75310-105">Dieses Dokument beschreibt die obersten Faktoren, die Auswirkungen auf die Qualität von mixed Reality-apps.</span><span class="sxs-lookup"><span data-stu-id="75310-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="75310-106">Für die einzelnen Faktoren ist die folgenden Informationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="75310-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="75310-107">Übersicht – eine kurze Beschreibung der Qualitätsfaktor und warum es wichtig ist.</span><span class="sxs-lookup"><span data-stu-id="75310-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="75310-108">Gerät Auswirkungen, – welche Art von Fenster Mixed Reality-Gerät betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="75310-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="75310-109">Qualitätskriterien – wie den Qualitätsfaktor ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="75310-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="75310-110">So messen – Methoden, um das Problem zu messen (oder auftreten).</span><span class="sxs-lookup"><span data-stu-id="75310-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="75310-111">Empfehlungen – Zusammenfassung der Ansätze für eine bessere Benutzeroberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="75310-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="75310-112">Ressourcen – relevanten Entwickler- und Design-Ressourcen, die zum Erstellen besserer Benutzeroberflächen nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="75310-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="75310-113">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="75310-113">Frame rate</span></span>

<span data-ttu-id="75310-114">Framerate ist die erste Säule des – Hologramm Stabilität Komfort für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="75310-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="75310-115">Framerate oberhalb der empfohlenen Ziele kann dazu führen, dass Hologramme ganz nervös, negative Auswirkungen auf die Believability der Benutzeroberfläche und führte potenziell zu Eye Ermüdung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="75310-116">60Hz oder 90Hz, je nachdem welche Windows Mixed Reality kompatibel PCs Sie unterstützen möchten, wird die Ziel-Framerate für Ihre Umgebung für immersive Headsets Windows Mixed Reality sein.</span><span class="sxs-lookup"><span data-stu-id="75310-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="75310-117">Für HoloLens ist die Ziel-Framerate 60Hz.</span><span class="sxs-lookup"><span data-stu-id="75310-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-118">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-121">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-122">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-123">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-123">Quality criteria</span></span>

|  <span data-ttu-id="75310-124">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-124">Best</span></span>  |  <span data-ttu-id="75310-125">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-125">Meets</span></span> |  <span data-ttu-id="75310-126">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="75310-127">Die app erfüllt konsistent Frames pro Sekunde (FPS)-Ziel für Zielgerät: 60fps im HoloLens; 90 f/s auf Ultra-PCs und 60fps auf gängige PCs.</span><span class="sxs-lookup"><span data-stu-id="75310-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="75310-128">Die app verfügt über periodische Frame löscht die Core-Umgebung nicht zu beeinträchtigen, oder f/s ist konsistent niedriger als der gewünschte Ziel, aber durch die app-Funktionalität nicht beeinträchtigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="75310-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="75310-129">Die app hat einen Abfall der Framerate, die im Durchschnitt alle zehn Sekunden oder weniger.</span><span class="sxs-lookup"><span data-stu-id="75310-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="75310-130">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-130">How to measure</span></span>

* <span data-ttu-id="75310-131">Ein in Echtzeit Frame Rate Diagramm erfolgt über von der [Windows Device Portal](using-the-windows-device-portal.md#system-performance) unter "System Performance".</span><span class="sxs-lookup"><span data-stu-id="75310-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="75310-132">Fügen Sie für die Entwicklung zu debuggen einen Frame Rate-Diagnose-Zähler der app hinzu.</span><span class="sxs-lookup"><span data-stu-id="75310-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="75310-133">Finden Sie Ressourcen für einen Beispiel-Indikator.</span><span class="sxs-lookup"><span data-stu-id="75310-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="75310-134">Frame Rate löscht können im Gerät auftreten können, während die app ausgeführt wird, durch das Verschieben der Kopf von rechts.</span><span class="sxs-lookup"><span data-stu-id="75310-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="75310-135">Wenn die Hologramm unerwartete ganz nervös Bewegung angezeigt wird, dann niedrigen Framerate oder die Stabilität-Ebene ist wahrscheinlich die Ursache.</span><span class="sxs-lookup"><span data-stu-id="75310-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-136">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-136">Recommendations</span></span>

* <span data-ttu-id="75310-137">Fügen Sie einen Frame Rate Zähler am Anfang der Entwicklungsarbeit hinzu.</span><span class="sxs-lookup"><span data-stu-id="75310-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="75310-138">Änderungen, die einen Abfall der Framerate entstehen, ausgewertet und als leistungsfehler entsprechend behoben.</span><span class="sxs-lookup"><span data-stu-id="75310-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-139">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-140">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-140">Documentation</span></span>

* [<span data-ttu-id="75310-141">Grundlegendes zur Leistung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="75310-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="75310-142">– Hologramm Stabilität und der Bildrate</span><span class="sxs-lookup"><span data-stu-id="75310-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="75310-143">Asset-Leistungsbudget</span><span class="sxs-lookup"><span data-stu-id="75310-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="75310-144">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="75310-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-145">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-145">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-146">MRToolkit, f/s-Leistungsindikator-Anzeige</span><span class="sxs-lookup"><span data-stu-id="75310-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="75310-147">MRToolkit, Shadern</span><span class="sxs-lookup"><span data-stu-id="75310-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="75310-148">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="75310-148">External references</span></span>

* [<span data-ttu-id="75310-149">Unity und Optimieren von mobilen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="75310-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="75310-150">– Hologramm Stabilität</span><span class="sxs-lookup"><span data-stu-id="75310-150">Hologram stability</span></span>

<span data-ttu-id="75310-151">Stabile Hologramme werden erhöht die benutzerfreundlichkeit und Believability Ihrer App, und erstellen ein angenehmer Anzeigefunktionen für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="75310-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="75310-152">Die Qualität der – Hologramm Stabilität ist das Ergebnis gute app-Entwicklung und die Fähigkeit des Geräts (Track) zu ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="75310-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="75310-153">Während der Framerate für die erste Säule des Stabilität ist, können andere Faktoren, einschließlich Stabilität auswirken:</span><span class="sxs-lookup"><span data-stu-id="75310-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="75310-154">Verwenden der Stabilisierung Ebene</span><span class="sxs-lookup"><span data-stu-id="75310-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="75310-155">Abstand und räumliche Anker</span><span class="sxs-lookup"><span data-stu-id="75310-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="75310-156">Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="75310-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-157">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-160">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-161">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-161">Quality criteria</span></span>

|  <span data-ttu-id="75310-162">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-162">Best</span></span>  |  <span data-ttu-id="75310-163">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-163">Meets</span></span> |  <span data-ttu-id="75310-164">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-165">Hologramme werden konsistent stabile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75310-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="75310-166">Sekundärer Inhalt weist unerwartete Bewegung; oder unerwartete Bewegung allgemeine app-Benutzeroberfläche nicht behindern.</span><span class="sxs-lookup"><span data-stu-id="75310-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="75310-167">Hauptinhalt in Rahmen weist unerwartete verschieben.</span><span class="sxs-lookup"><span data-stu-id="75310-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="75310-168">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-168">How to measure</span></span>

<span data-ttu-id="75310-169">Während das Gerät steht, geteert und die zur Anzeige von:</span><span class="sxs-lookup"><span data-stu-id="75310-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="75310-170">Verschieben Kopf von rechts, die Hologramme unerwartete Bewegung angezeigt dann niedrigen Framerate oder eine fehlerhafte Ausrichtung der Stabilität Ebene auf dieser Ebene wird wahrscheinlich dadurch verursacht.</span><span class="sxs-lookup"><span data-stu-id="75310-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="75310-171">Verschieben Sie die Hologramme und die Umgebung, suchen Sie nach Verhaltensweisen wie verantwortlichkeitsbereichs und Jumpiness.</span><span class="sxs-lookup"><span data-stu-id="75310-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="75310-172">Diese Art von Motion wird wahrscheinlich durch das Gerät nicht die Umgebung oder die Entfernung verfolgt, auf den spatial Anker verursacht.</span><span class="sxs-lookup"><span data-stu-id="75310-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="75310-173">Bei einer großen oder mehrere Hologramme befinden sich in den Frame, – Hologramm-Verhalten in verschiedenen Ebenen zu beobachten, während Ihre Head Position von rechts, verschieben, wenn Shakiness angezeigt wird, dies ist wahrscheinlich der Stabilisierung Ebene zurückzuführen.</span><span class="sxs-lookup"><span data-stu-id="75310-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="75310-174">Recomendations</span><span class="sxs-lookup"><span data-stu-id="75310-174">Recomendations</span></span>

* <span data-ttu-id="75310-175">Fügen Sie einen Frame Rate Zähler am Anfang der Entwicklungsarbeit hinzu.</span><span class="sxs-lookup"><span data-stu-id="75310-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="75310-176">Verwenden Sie die Stabilisierung-Ebene.</span><span class="sxs-lookup"><span data-stu-id="75310-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="75310-177">Rendern Sie immer verankerten Hologramme innerhalb von 3 Messgeräten, die von ihren Anker.</span><span class="sxs-lookup"><span data-stu-id="75310-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="75310-178">Stellen Sie sicher, dass Ihre Umgebung eingerichtet, für die ordnungsgemäße Überwachung ist.</span><span class="sxs-lookup"><span data-stu-id="75310-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="75310-179">Entwerfen Sie Ihrer Erfahrung Hologramme auf verschiedenen als zentrales Tiefenebenen innerhalb des Rahmens zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="75310-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-180">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-181">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-181">Documentation</span></span>

* [<span data-ttu-id="75310-182">– Hologramm Stabilität und der Bildrate</span><span class="sxs-lookup"><span data-stu-id="75310-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="75310-183">Fallstudie, die mit der Stabilisierung-Ebene</span><span class="sxs-lookup"><span data-stu-id="75310-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="75310-184">Grundlegendes zur Leistung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="75310-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="75310-185">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="75310-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="75310-186">Raumanker</span><span class="sxs-lookup"><span data-stu-id="75310-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="75310-187">Behandeln von Fehlern der nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="75310-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="75310-188">Feststehende Verweisrahmen</span><span class="sxs-lookup"><span data-stu-id="75310-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-189">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-189">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-190">MR Companion Kit Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="75310-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="75310-191">Hologramme Position auf echten Oberflächen</span><span class="sxs-lookup"><span data-stu-id="75310-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="75310-192">Fehler im Alignment von Hologramme mit physischer Objekte (sofern aneinander platziert werden soll) ist ein eindeutiger Hinweis darauf, der nicht-Union-Hologramme und reale.</span><span class="sxs-lookup"><span data-stu-id="75310-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="75310-193">Genauigkeit der Platzierung sollte relativ zu den Anforderungen des Szenarios werden. z. B. allgemeine Oberfläche Platzierung räumliche Zuordnung verwenden kann, aber eine präzisere Platzierung benötigen einige mit markern und Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="75310-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-194">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-197">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-198">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-198">Quality criteria</span></span>

|  <span data-ttu-id="75310-199">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-199">Best</span></span>  |  <span data-ttu-id="75310-200">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-200">Meets</span></span> |  <span data-ttu-id="75310-201">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="75310-202">Hologramme Ausrichten der Entwurfsoberfläche in der Regel in der Zentimeter Zoll-Bereich.</span><span class="sxs-lookup"><span data-stu-id="75310-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="75310-203">Wenn eine größere Genauigkeit erforderlich ist, sollte die app eine effiziente Möglichkeit für die Zusammenarbeit in der Spezifikation für die gewünschte app bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="75310-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="75310-204">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="75310-204">NA</span></span> | <span data-ttu-id="75310-205">Die Hologramme angezeigt mit der physischen Zielobjekt nicht ausgerichtete durch Unterbrechen der Surface-Ebene oder auf von der Oberfläche "float" angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="75310-206">Wenn Genauigkeit erforderlich ist, sollte die Hologramme die NEAR-Spezifikation des Szenarios erfüllen.</span><span class="sxs-lookup"><span data-stu-id="75310-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-207">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-207">How to measure</span></span>

* <span data-ttu-id="75310-208">Hologramme, die auf den spatial Karte platziert werden sollten nicht auf deutlich oberhalb oder unterhalb der Oberfläche "float" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75310-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="75310-209">Hologramme, die korrekte Platzierung erfordern sollte es sich um eine Form, Marker und Kalibrierung System verfügen, die auf das Szenario für die Anforderung wird.</span><span class="sxs-lookup"><span data-stu-id="75310-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-210">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-210">Recommendations</span></span>

* <span data-ttu-id="75310-211">Räumliche Zuordnung ist nützlich für das Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="75310-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="75310-212">Verwenden Sie für die beste Genauigkeit Marker oder Poster der Hologramme und eine Xbox-Controller (oder einen Mechanismus für die manuelle Ausrichtung) fest für die endgültige Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="75310-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="75310-213">Berücksichtigen Sie sehr große Hologramme in logische Teile aufteilen und Ausrichtung der einzelnen Teile der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="75310-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="75310-214">Nicht ordnungsgemäß auswirken festgelegten interpupilary Entfernung (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) kann auch – Hologramm Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="75310-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="75310-215">Konfigurieren Sie immer die HoloLens, Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="75310-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-216">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-217">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-217">Documentation</span></span>

* [<span data-ttu-id="75310-218">Räumliche Zuordnung-Platzierung</span><span class="sxs-lookup"><span data-stu-id="75310-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="75310-219">Raum Scanvorgang</span><span class="sxs-lookup"><span data-stu-id="75310-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="75310-220">Bewährte Methoden von räumlichen Anker</span><span class="sxs-lookup"><span data-stu-id="75310-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="75310-221">Behandeln von Fehlern der nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="75310-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="75310-222">Räumliche Abbildung in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="75310-223">Übersicht über die Entwicklung von Vuforia</span><span class="sxs-lookup"><span data-stu-id="75310-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-224">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-224">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-225">MR räumlich 230: Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="75310-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="75310-226">Räumliche Zuordnung Bibliotheken MR Toolkit</span><span class="sxs-lookup"><span data-stu-id="75310-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="75310-227">MR Companion Kit Poster Kalibrierung-Beispiel</span><span class="sxs-lookup"><span data-stu-id="75310-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="75310-228">MR Companion Kit Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="75310-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="75310-229">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="75310-229">External references</span></span>

* [<span data-ttu-id="75310-230">Fallstudie Lowes Genauigkeit Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="75310-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="75310-231">Anzeigen der Zone der Komfort</span><span class="sxs-lookup"><span data-stu-id="75310-231">Viewing zone of comfort</span></span>

<span data-ttu-id="75310-232">App-Entwickler-Steuerelement, in denen Benutzer Augen konvergieren, durch die Platzierung von Inhalt und Hologramme in verschiedenen Ebenen.</span><span class="sxs-lookup"><span data-stu-id="75310-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="75310-233">Benutzern steht, geteert HoloLens werden immer berücksichtigen, auf 2.0m zu verwalten, ein klares Bild da HoloLens angezeigt sind in einer optischen Abstand ungefähr 2.0m von der Benutzer fest.</span><span class="sxs-lookup"><span data-stu-id="75310-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="75310-234">Ungültige Content Tiefe kann visual angefasst oder Ermüdung führen.</span><span class="sxs-lookup"><span data-stu-id="75310-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-235">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-238">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-239">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="75310-240">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="75310-241">Legen Sie Inhalte auf 2m ein.</span><span class="sxs-lookup"><span data-stu-id="75310-241">Place content at 2m.</span></span></li><li><span data-ttu-id="75310-242">Wenn Hologramme können nicht auf 2m platziert werden und Konflikte zwischen Konvergenz und beeinflusst nicht vermieden werden, liegt die optimale Zone für die Platzierung von – Hologramm 1,25 m "und" 5 Min.</span><span class="sxs-lookup"><span data-stu-id="75310-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="75310-243">In jedem Fall sollte Designer Struktur Inhalt empfehlen Benutzern die Interaktion von 1 + m entfernt (z. B. Inhaltsgröße anpassen und die Positionierungsparameter des Standard).</span><span class="sxs-lookup"><span data-stu-id="75310-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="75310-244">Es sei denn, die explizit nicht von dem Szenario erforderlich ist, sollte eine Clippingebene implementieren mit Fadeout beginnend mit 1 Million.</span><span class="sxs-lookup"><span data-stu-id="75310-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="75310-245">In Fällen, in denen genauer Beobachtung von einem bewegungslos Hologramm erforderlich ist, sollte der Inhalt nicht als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="75310-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="75310-246">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-246">Meets</span></span></td><td> <span data-ttu-id="75310-247">Der Inhalt ist in der Anleitung anzeigen und während der Übertragung, aber nicht ordnungsgemäße sprachnutzung oder keine Verwendung von den Clipping-Ebene.</span><span class="sxs-lookup"><span data-stu-id="75310-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="75310-248">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-248">Fail</span></span> </td><td> <span data-ttu-id="75310-249">Der Inhalt zu nahe dargestellt wird (in der Regel &lt;1,25 m oder &lt;50 cm für stationäre Hologramme genauer Beobachtung erfordern.)</span><span class="sxs-lookup"><span data-stu-id="75310-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="75310-250">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-250">How to measure</span></span>

* <span data-ttu-id="75310-251">Der Inhalt muss in der Regel 2 m entfernt, jedoch nicht näher als 1,25 oder weiter als 5 Min. entsprechen.</span><span class="sxs-lookup"><span data-stu-id="75310-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="75310-252">Mit wenigen Ausnahmen sollte die HoloLens Clipping Render-Entfernung auf .85CM mit Fadeout von Inhalten, die beginnend bei 1 Mio. festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="75310-253">Ansatz des Inhalts, und notieren Sie den Freistellungseffekt-Ebene.</span><span class="sxs-lookup"><span data-stu-id="75310-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="75310-254">Stationär Inhalt darf nicht als 50 cm entfernt sein.</span><span class="sxs-lookup"><span data-stu-id="75310-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-255">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-255">Recommendations</span></span>

* <span data-ttu-id="75310-256">Entwerfen Sie Inhalte für die optimale Anzeige Entfernung 2 m ein.</span><span class="sxs-lookup"><span data-stu-id="75310-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="75310-257">Legen Sie die Entfernung des Clipping gerendert, auf 85cm mit Fadeout von Inhalten, die beginnend bei 1 Million.</span><span class="sxs-lookup"><span data-stu-id="75310-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="75310-258">Für stationäre Hologramme, die näher anzeigen, sollten die Clipping-Ebene nicht näher als 30cm und Fadeout sollte mindestens 10cm Weg von den Clipping-Ebene beginnen.</span><span class="sxs-lookup"><span data-stu-id="75310-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-259">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-259">Resources</span></span>

* [<span data-ttu-id="75310-260">Rendern von Abstand</span><span class="sxs-lookup"><span data-stu-id="75310-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="75310-261">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="75310-262">Experimentieren mit der Skalierung</span><span class="sxs-lookup"><span data-stu-id="75310-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="75310-263">Text Schriftgrad empfohlen</span><span class="sxs-lookup"><span data-stu-id="75310-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="75310-264">Tiefe wechseln</span><span class="sxs-lookup"><span data-stu-id="75310-264">Depth switching</span></span>

<span data-ttu-id="75310-265">Unabhängig von der Zone der Komfort Probleme anzeigen fordert für den Benutzer häufig oder schnell wechseln, in der Nähe, und viel als zentrales Objekte (einschließlich Hologramme und den tatsächlichen Inhalt) oculomotor Fatigue und allgemeine angefasst führen können.</span><span class="sxs-lookup"><span data-stu-id="75310-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-266">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-269">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-270">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-271">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-271">Quality criteria</span></span>

|  <span data-ttu-id="75310-272">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-272">Best</span></span>  |  <span data-ttu-id="75310-273">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-273">Meets</span></span> |  <span data-ttu-id="75310-274">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-275">Eingeschränkte oder natürliche Tiefe wechseln, die nicht dazu führen, dass den Benutzer, neuer Nachklang Fokus.</span><span class="sxs-lookup"><span data-stu-id="75310-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="75310-276">Switch abrupten Tiefe, dies ist der Kern und in der app-Erfahrung konzipiert, oder abrupten Tiefe-Switch, der von unerwarteten realen Inhalt verursacht wird.</span><span class="sxs-lookup"><span data-stu-id="75310-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="75310-277">Einheitliche Tiefe Switch oder abrupten Tiefe wechseln, die nicht erforderlich ist oder Core, um die app-Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="75310-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-278">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-278">How to measure</span></span>

* <span data-ttu-id="75310-279">Wenn den Benutzer konsistent und/oder plötzlich Tiefe ändern Sie den Fokus von der app erforderlich sind, ist Tiefe Problem wechseln.</span><span class="sxs-lookup"><span data-stu-id="75310-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-280">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-280">Recommendations</span></span>

* <span data-ttu-id="75310-281">Behalten Sie Hauptinhalt an einer konsistenten als zentrales Ebene bei, und stellen Sie sicher, dass die Stabilisierung-Ebene auf dieser Ebene entspricht.</span><span class="sxs-lookup"><span data-stu-id="75310-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="75310-282">Dies lässt sich durch oculomotor Fatigue und unerwartete – Hologramm Bewegung beheben.</span><span class="sxs-lookup"><span data-stu-id="75310-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-283">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-283">Resources</span></span>

* [<span data-ttu-id="75310-284">Rendern von Abstand</span><span class="sxs-lookup"><span data-stu-id="75310-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="75310-285">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="75310-286">Von räumlichen Sounds</span><span class="sxs-lookup"><span data-stu-id="75310-286">Use of spatial sound</span></span>

<span data-ttu-id="75310-287">In Windows Mixed Reality bietet das Audiomodul der sehen die mixed Reality-Erfahrung durch Simulieren von 3D sound mithilfe von environmental Simulationen, Entfernung und Richtung.</span><span class="sxs-lookup"><span data-stu-id="75310-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="75310-288">Verwenden von räumlichen Sound in einer Anwendung kann Entwickler convincingly Platzieren von Sounds in einem 3 dimensionalen Raum (Kugel) für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="75310-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="75310-289">Diese Sounds werden dann erscheinen, als ob sie von echten physischen Objekten oder der mixed Reality-Hologramme in der benutzerumgebung gestellt würden.</span><span class="sxs-lookup"><span data-stu-id="75310-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="75310-290">Räumliche Sound ist ein leistungsstarkes Tool zum Immersion, Barrierefreiheit und UX-Entwurf in mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="75310-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-291">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-294">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-295">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-296">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-296">Quality criteria</span></span>

|  <span data-ttu-id="75310-297">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-297">Best</span></span>  |  <span data-ttu-id="75310-298">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-298">Meets</span></span> |  <span data-ttu-id="75310-299">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-300">Sound wird logisch spatialized und die UX entsprechend Sound verwendet, zur Unterstützung bei der Objekt-Ermittlung und Benutzerfeedback.</span><span class="sxs-lookup"><span data-stu-id="75310-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="75310-301">Sound ist die natürliche und auf Objekte relevant und eine normalisierte, über das Szenario.</span><span class="sxs-lookup"><span data-stu-id="75310-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="75310-302">Räumliche Audio ist entsprechend für Believability verwendet jedoch fehlen als Mittel, um Feedback von Benutzern und die Auffindbarkeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="75310-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="75310-303">Sound wird nicht wie erwartet, spatialized und/oder fehlende Sound bei der Benutzer in der UX.</span><span class="sxs-lookup"><span data-stu-id="75310-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="75310-304">Räumliche Audio wurde oder nicht berücksichtigt, die in den Entwurf des Szenarios verwendet.</span><span class="sxs-lookup"><span data-stu-id="75310-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-305">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-305">How to measure</span></span>

* <span data-ttu-id="75310-306">Im Allgemeinen sollte die relevanten Sounds von Ziel-Hologramme ausgeben (z. b., Rinde Sound holographic Hund stammen.)</span><span class="sxs-lookup"><span data-stu-id="75310-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="75310-307">Sound Hinweise sollten in der UX verwendet werden, um dem Benutzer Feedback oder Kenntnis der Aktionen außerhalb der holographic Frame zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="75310-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-308">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-308">Recommendations</span></span>

* <span data-ttu-id="75310-309">Verwenden Sie räumliche Audio, zur Unterstützung bei der Ermittlung und Benutzer-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="75310-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="75310-310">Echte Sounds besser funktionieren als synthetisier oder unnatürlichen Sound.</span><span class="sxs-lookup"><span data-stu-id="75310-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="75310-311">Die meisten Sounds sollten spatialized sein.</span><span class="sxs-lookup"><span data-stu-id="75310-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="75310-312">Vermeiden Sie unsichtbar korrekturemitter ab.</span><span class="sxs-lookup"><span data-stu-id="75310-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="75310-313">Vermeiden Sie räumliche Maskierung.</span><span class="sxs-lookup"><span data-stu-id="75310-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="75310-314">Alle Sounds zu normalisieren.</span><span class="sxs-lookup"><span data-stu-id="75310-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-315">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-316">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-316">Documentation</span></span>

* [<span data-ttu-id="75310-317">Raumklang</span><span class="sxs-lookup"><span data-stu-id="75310-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="75310-318">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="75310-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="75310-319">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="75310-320">Fallstudie für HoloTour sound räumlich</span><span class="sxs-lookup"><span data-stu-id="75310-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="75310-321">Verwenden von räumlichen Sound in RoboRaid Fallstudie</span><span class="sxs-lookup"><span data-stu-id="75310-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-322">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-322">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-323">MR räumlich 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="75310-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="75310-324">MRToolkit, Spatial Audio</span><span class="sxs-lookup"><span data-stu-id="75310-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="75310-325">Konzentrieren Sie sich an holographic Frame (Blickfeld) Grenzen</span><span class="sxs-lookup"><span data-stu-id="75310-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="75310-326">Gut gestaltete Benutzeroberflächen erstellen und Warten von nützlichen Kontext der virtuellen Umgebung, die über die Benutzer erweitert.</span><span class="sxs-lookup"><span data-stu-id="75310-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="75310-327">Einen durchdachten Entwurf Content skalierungs-und Kontext umfasst die Minderung der Auswirkungen der Blickfeld Grenzen, die räumliche Audio, Anleitungen, Systeme und Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="75310-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="75310-328">Wenn rechts durchgeführt wird, wird den Benutzer, dass weniger durch das Blickfeld Grenzen eingeschränkt, während Sie eine sich app-Erfahrung so aussehen.</span><span class="sxs-lookup"><span data-stu-id="75310-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-329">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-332">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-333">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-333">Quality criteria</span></span>

|  <span data-ttu-id="75310-334">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-334">Best</span></span>  |  <span data-ttu-id="75310-335">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-335">Meets</span></span> |  <span data-ttu-id="75310-336">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-337">Benutzer verliert nie Kontext und Anzeigen von vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="75310-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="75310-338">Unterstützung der Kontext wird für große Objekte bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="75310-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="75310-339">Auffindbarkeit und Anzeigen von Anweisungen für Objekte außerhalb des Rahmens bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="75310-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="75310-340">Im Allgemeinen sind die Motion-Entwurf und die Skalierung der Hologramme für eine vertraut Anzeigefunktionen geeignet.</span><span class="sxs-lookup"><span data-stu-id="75310-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="75310-341">Benutzer werden niemals Kontext verliert, aber in bestimmten Situationen möglicherweise zusätzliche trichterhalses während der Übertragung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="75310-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="75310-342">In bestimmten Situationen wird Skalierung Hologramme entweder vertikal oder horizontal Frames verursacht manche Bewegung trichterhalses Hologramme anzeigen zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="75310-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="75310-343">Wahrscheinlich Kontext und/oder konsistente trichterhalses Motion verlieren Benutzer ist erforderlich, um Hologramme anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="75310-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="75310-344">Kein Kontext für große Objekte holographic, Verschieben von Objekten außerhalb des Rahmens ohne Erkennbarkeit Anleitungen oder hohe Hologramme verliert einfach gefordert regulären trichterhalses während der Übertragung an.</span><span class="sxs-lookup"><span data-stu-id="75310-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-345">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-345">How to measure</span></span>

* <span data-ttu-id="75310-346">Kontext für eine (groß) – Hologramm verloren geht oder aufgrund der an den Grenzen freigestellt wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="75310-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="75310-347">Speicherort der Hologramme sind schwer zu finden, die aufgrund des Mangels an Aufmerksamkeit Directors oder Inhalte, die schnell in und aus der holografischen Frame verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="75310-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="75310-348">Szenario erfordert regelmäßige und sich wiederholende nach oben oder unten Head während der Übertragung ein Hologramm, wodurch trichterhalses Ermüdung vollständig angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75310-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-349">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-349">Recommendations</span></span>

* <span data-ttu-id="75310-350">Starten Sie die Benutzeroberfläche, mit kleine Objekte, die das Blickfeld anpassen, mit visuellen Hinweise auf größeren Versionen wechseln.</span><span class="sxs-lookup"><span data-stu-id="75310-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="75310-351">Verwenden Sie räumliche Audio- und Aufmerksamkeit Directors, um Benutzerinhalte suchen, die sich das Blickfeld.</span><span class="sxs-lookup"><span data-stu-id="75310-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="75310-352">Vermeiden Sie so weit wie möglich, Hologramme, die das Blickfeld vertikal zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="75310-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="75310-353">Geben Sie dem Benutzer mit in-app-Anleitung für die optimale Anzeige Speicherort ein.</span><span class="sxs-lookup"><span data-stu-id="75310-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-354">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-355">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-355">Documentation</span></span>

* [<span data-ttu-id="75310-356">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="75310-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="75310-357">Fallstudie, HoloStudio UI und Interaktion entwerfen Erkenntnisse</span><span class="sxs-lookup"><span data-stu-id="75310-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="75310-358">Skalieren von Objekten und Umgebungen</span><span class="sxs-lookup"><span data-stu-id="75310-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="75310-359">Cursor, visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="75310-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="75310-360">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="75310-360">External references</span></span>

* [<span data-ttu-id="75310-361">ActiveX Data Objects und das Blickfeld</span><span class="sxs-lookup"><span data-stu-id="75310-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="75310-362">Inhalte reagiert an Benutzerposition</span><span class="sxs-lookup"><span data-stu-id="75310-362">Content reacts to user position</span></span>

<span data-ttu-id="75310-363">Hologramme sollte auf die Benutzerposition auf ungefähr die gleiche Weise reagieren, die "echten" Objekte.</span><span class="sxs-lookup"><span data-stu-id="75310-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="75310-364">Eine wichtige Design-Herausforderungen ist UI-Elemente, die unbedingt eines Benutzers Position können nicht davon ausgehen nicht bewegt wird und sich Anpassen des Benutzers während der Übertragung.</span><span class="sxs-lookup"><span data-stu-id="75310-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="75310-365">Das Entwerfen einer app, die ordnungsgemäß an Benutzerposition anpasst erstellt eine mehr glaubwürdig Erfahrung und einfacher zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="75310-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-366">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-369">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-370">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-371">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="75310-372">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-372">Best</span></span> </td><td> <span data-ttu-id="75310-373">Inhalt und die Benutzeroberfläche anpassen an Benutzerpositionen, die Benutzer auf natürliche Weise mit Inhalt innerhalb des Bereichs der erwarteten Benutzer datenverschiebung kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="75310-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="75310-374">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-374">Meets</span></span> </td><td> <span data-ttu-id="75310-375">Benutzeroberfläche passt sich an die Benutzerposition an, aber Sie können die Ansicht der Aufforderung des Benutzers zum Anpassen ihrer Position schlüsselinhalt behindern.</span><span class="sxs-lookup"><span data-stu-id="75310-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="75310-376">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="75310-377">UI-Elemente sind verloren gegangen oder gesperrt, während der Verschiebung zu Benutzer Steuerelemente Nachklang zurück zu (oder suchen).</span><span class="sxs-lookup"><span data-stu-id="75310-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="75310-378">UI-Elemente begrenzen, die Ansicht der Hauptinhalt.</span><span class="sxs-lookup"><span data-stu-id="75310-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="75310-379">UI-Bewegung ist nicht optimiert, für die Anzeige von Abstand und Momentum, insbesondere bei <a href="billboarding-and-tag-along.md">Tag-along</a> UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="75310-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="75310-380">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-380">How to measure</span></span>

* <span data-ttu-id="75310-381">Alle Messungen sollte innerhalb eines angemessenen Bereichs des Szenarios ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="75310-382">Während der Verschiebung des Benutzers variieren kann, versuchen Sie nicht dazu bringen, die app mit extremer Benutzer verschieben.</span><span class="sxs-lookup"><span data-stu-id="75310-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="75310-383">Für Benutzeroberflächenelemente sollte relevante Steuerelemente zur Verfügung, unabhängig von der Benutzer verschieben.</span><span class="sxs-lookup"><span data-stu-id="75310-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="75310-384">Z. B., wenn der Benutzer wird durchlaufen, um eine 3D Karte mit Zoom und zum Anzeigen, sollte das Zoomsteuerelement für den Benutzer unabhängig vom Standort sofort verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="75310-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-385">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-385">Recommendations</span></span>

* <span data-ttu-id="75310-386">Der Benutzer die Kamera und steuern sie die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="75310-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="75310-387">Sie steuern können.</span><span class="sxs-lookup"><span data-stu-id="75310-387">Let them drive.</span></span>
* <span data-ttu-id="75310-388">Betrachten Sie billboarding für Text und Menüs-Systeme, die andernfalls Welt gesperrt oder verdeckt wird, wenn ein Benutzer verschoben wurden.</span><span class="sxs-lookup"><span data-stu-id="75310-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="75310-389">Verwenden Sie Tag-along für Inhalte, die folgen dem Benutzer während nach wie vor den Benutzer angezeigt, was vorangestellt ist.</span><span class="sxs-lookup"><span data-stu-id="75310-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-390">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-391">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-391">Documentation</span></span>

* [<span data-ttu-id="75310-392">Entwerfen für</span><span class="sxs-lookup"><span data-stu-id="75310-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="75310-393">Farbe, Material und Licht</span><span class="sxs-lookup"><span data-stu-id="75310-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="75310-394">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="75310-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="75310-395">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="75310-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="75310-396">Self-motion und Benutzer Locomotion</span><span class="sxs-lookup"><span data-stu-id="75310-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-397">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-397">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-398">MR-Eingabe 210: Anvisieren</span><span class="sxs-lookup"><span data-stu-id="75310-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="75310-399">Eingabe Interaktion Klarheit</span><span class="sxs-lookup"><span data-stu-id="75310-399">Input interaction clarity</span></span>

<span data-ttu-id="75310-400">Eingabe Interaktion Klarheit ist wichtig, zu der app-benutzerfreundlichkeit und umfassen Eingabe Konsistenz, Zugänglichkeit, Auffindbarkeit der Interaction-Methode.</span><span class="sxs-lookup"><span data-stu-id="75310-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="75310-401">Benutzer sollten plattformweiten allgemeine Aktivitäten ohne erlernen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="75310-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="75310-402">Wenn die app benutzerdefinierte Eingabe hat, muss klar kommuniziert und veranschaulicht werden.</span><span class="sxs-lookup"><span data-stu-id="75310-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-403">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-406">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-407">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-408">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-408">Quality criteria</span></span>

|  <span data-ttu-id="75310-409">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-409">Best</span></span>  |  <span data-ttu-id="75310-410">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-410">Meets</span></span> |  <span data-ttu-id="75310-411">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-412">Eingabe Interaction-Methode sind konsistent mit den Windows Mixed Reality bereitgestellten [Anleitungen](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="75310-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="75310-413">Eine benutzerdefinierte Eingabe muss sollte nicht in Hinblick auf die Standardeingabe (stattdessen Verwendung standard Interaktion) werden deutlich kommuniziert und gezeigt, um den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="75310-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="75310-414">Ähnlich wie bei der bewährten, aber benutzerdefinierte Eingaben, die mit standardmäßigen Eingabemethoden redundant sind.</span><span class="sxs-lookup"><span data-stu-id="75310-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="75310-415">Benutzer kann weiterhin die Ziel und den Fortschritt über die app-Funktionalität erreichen.</span><span class="sxs-lookup"><span data-stu-id="75310-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="75310-416">Schwierig, input Methode oder eine Schaltfläche-Zuordnung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="75310-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="75310-417">Eingabe stark angepasst wird, unterstützt nicht die Standardeingabe, keine Anweisungen oder Fatigue und Komfort Probleme verursachen.</span><span class="sxs-lookup"><span data-stu-id="75310-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-418">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-418">How to measure</span></span>

* <span data-ttu-id="75310-419">Die app verwendet einheitliche [Standard Eingabe Methoden.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="75310-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="75310-420">Wenn die app ist Eingabe hat, wird sie eindeutig über kommuniziert:</span><span class="sxs-lookup"><span data-stu-id="75310-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="75310-421">Eindrucks beim ersten Ausführen</span><span class="sxs-lookup"><span data-stu-id="75310-421">First-run experience</span></span>
* <span data-ttu-id="75310-422">Einführende Bildschirme</span><span class="sxs-lookup"><span data-stu-id="75310-422">Introductory screens</span></span>
* <span data-ttu-id="75310-423">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="75310-423">Tooltips</span></span>
* <span data-ttu-id="75310-424">Hand-coach</span><span class="sxs-lookup"><span data-stu-id="75310-424">Hand coach</span></span>
* <span data-ttu-id="75310-425">Hilfe</span><span class="sxs-lookup"><span data-stu-id="75310-425">Help section</span></span>
* <span data-ttu-id="75310-426">Voice-over</span><span class="sxs-lookup"><span data-stu-id="75310-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-427">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-427">Recommendations</span></span>

* <span data-ttu-id="75310-428">Verwenden Sie die standard-Eingabe-Methoden nach Möglichkeit.</span><span class="sxs-lookup"><span data-stu-id="75310-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="75310-429">Geben Sie Demos, Lernprogramme und QuickInfos für nicht standardmäßige Eingabemethoden an.</span><span class="sxs-lookup"><span data-stu-id="75310-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="75310-430">Verwenden Sie eine konsistente Interaktionsmodell in der gesamten app.</span><span class="sxs-lookup"><span data-stu-id="75310-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-431">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-432">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-432">Documentation</span></span>

* [<span data-ttu-id="75310-433">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="75310-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="75310-434">Es Objekte</span><span class="sxs-lookup"><span data-stu-id="75310-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="75310-435">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="75310-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="75310-436">Cursor</span><span class="sxs-lookup"><span data-stu-id="75310-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="75310-437">Komfort und Blicke</span><span class="sxs-lookup"><span data-stu-id="75310-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="75310-438">Gesten</span><span class="sxs-lookup"><span data-stu-id="75310-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="75310-439">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="75310-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="75310-440">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="75310-440">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="75310-441">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="75310-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="75310-442">Leitfaden für Eingabeportierung für Unity</span><span class="sxs-lookup"><span data-stu-id="75310-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="75310-443">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="75310-444">Anvisieren in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="75310-445">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="75310-446">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="75310-447">Tastatur-, Maus- und Controllereingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="75310-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="75310-448">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="75310-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="75310-449">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="75310-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="75310-450">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="75310-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-451">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-451">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-452">Fallstudie: Das Streben nach persönlichere Datenverarbeitung</span><span class="sxs-lookup"><span data-stu-id="75310-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="75310-453">CAST-Studie: Entwerfen von HoloStudio UI und Interaktion Erkenntnisse</span><span class="sxs-lookup"><span data-stu-id="75310-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="75310-454">Beispiel-app: Periodisch-Tabelle der Elemente</span><span class="sxs-lookup"><span data-stu-id="75310-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="75310-455">Beispiel-app: Mondkalender-Modul</span><span class="sxs-lookup"><span data-stu-id="75310-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="75310-456">MR-Eingabe 210: Anvisieren</span><span class="sxs-lookup"><span data-stu-id="75310-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="75310-457">MR-Eingabe 211: Gesten</span><span class="sxs-lookup"><span data-stu-id="75310-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="75310-458">MR-Eingabe 212: Sprache</span><span class="sxs-lookup"><span data-stu-id="75310-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="75310-459">Es Objekte</span><span class="sxs-lookup"><span data-stu-id="75310-459">Interactable objects</span></span>

<span data-ttu-id="75310-460">Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt.</span><span class="sxs-lookup"><span data-stu-id="75310-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="75310-461">In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="75310-462">Alles kann ein es Objekt sein, die ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="75310-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="75310-463">Ein Objekt es kann als etwas von einer Tasse Kaffee für die Tabelle, eine Gleitkommazahl in der Luft Sprechblase dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="75310-464">Unabhängig von der Art sollte es Objekte vom Benutzer über SEH- und Hinweise klar erkennbar sein.</span><span class="sxs-lookup"><span data-stu-id="75310-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-465">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-468">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-469">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-470">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-470">Quality criteria</span></span>

|  <span data-ttu-id="75310-471">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-471">Best</span></span>  |  <span data-ttu-id="75310-472">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-472">Meets</span></span> |  <span data-ttu-id="75310-473">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-474">Unabhängig von der Form, es Objekte sind über SEH- und Hinweise erkennbaren über drei Zustände: im Leerlauf, Ziel und ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="75310-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="75310-475">"Es noch einmal finden Sie unter" ist klarer und konsistent über die Umgebung verwendet.</span><span class="sxs-lookup"><span data-stu-id="75310-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="75310-476">Objekte werden skaliert und verteilt, um für fehlerfrei zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="75310-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="75310-477">Benutzer können erkennen Objekt als es durch Audio- oder visuelle Feedback, und als Ziel und aktivieren Sie das Objekt.</span><span class="sxs-lookup"><span data-stu-id="75310-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="75310-478">Wenn kein visual oder audio-Hinweise, kann Benutzer ein Objekt es nicht erkennen.</span><span class="sxs-lookup"><span data-stu-id="75310-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="75310-479">Interaktionen sind Fehler aufgrund von Objekt skalieren oder den Abstand zwischen den Objekten entstehen.</span><span class="sxs-lookup"><span data-stu-id="75310-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-480">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-480">How to measure</span></span>

* <span data-ttu-id="75310-481">Es stehen nebenbei gesagt, immer "es"; bestimmte Schaltflächen, Menüs und app-Inhalte, einschließlich.</span><span class="sxs-lookup"><span data-stu-id="75310-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="75310-482">Als Faustregel dürfte eine Orientierungshilfe SEH- und wenn es Objekte.</span><span class="sxs-lookup"><span data-stu-id="75310-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-483">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-483">Recommendations</span></span>

* <span data-ttu-id="75310-484">Verwenden Sie SEH- und Feedback für Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="75310-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="75310-485">Visuelles Feedback sollte unterschieden werden, für jede Zustand (im Leerlauf, gezielte, ausgewählte)</span><span class="sxs-lookup"><span data-stu-id="75310-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="75310-486">Es Objekte skaliert, und für die Zielgruppenadressierung fehlerfrei platziert.</span><span class="sxs-lookup"><span data-stu-id="75310-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="75310-487">Gruppierte es Objekte (z. B. eine Menüleiste oder Liste) sollte die richtigen Abstand für die Zielplattform verfügen.</span><span class="sxs-lookup"><span data-stu-id="75310-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="75310-488">Schaltflächen und Menüs, die Stimme-Befehl unterstützen sollten die Beschriftungen bereitstellen, für das Befehl-Schlüsselwort ("angezeigt, das so sagen")</span><span class="sxs-lookup"><span data-stu-id="75310-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="75310-489">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-490">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-490">Documentation</span></span>

* [<span data-ttu-id="75310-491">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="75310-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="75310-492">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="75310-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="75310-493">App-Leiste und Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="75310-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="75310-494">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="75310-494">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-495">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-495">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-496">Mixed Reality-Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="75310-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="75310-497">Raum Scannen</span><span class="sxs-lookup"><span data-stu-id="75310-497">Room scanning</span></span>

<span data-ttu-id="75310-498">Apps, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv.</span><span class="sxs-lookup"><span data-stu-id="75310-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="75310-499">Der Vollständigkeit und die Qualität der Daten hängt von einer Reihe von Faktoren wie der Menge der, die der Benutzer ausgeführt hat, wie viel Zeit verstrichen ist, da die Auswertung und gibt an, ob die Objekte, z. B. Möbel und Türen verschoben haben, da das Gerät über den Bereich überprüft.</span><span class="sxs-lookup"><span data-stu-id="75310-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="75310-500">Viele apps werden analysiert, die räumliche Zuordnungsdaten zu Beginn der Umgebung zu beurteilen, ob der Benutzer zusätzliche Schritte zur Verbesserung der Vollständigkeit und die Qualität der räumliche Zuordnung ausführen soll.</span><span class="sxs-lookup"><span data-stu-id="75310-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="75310-501">Wenn der Benutzer erforderlich ist, um die Überprüfung der Umgebung, klar, dass während der Überprüfung Oberfläche Anleitungen bereitgestellt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="75310-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-502">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-505">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-506">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-506">Quality criteria</span></span>

|  <span data-ttu-id="75310-507">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-507">Best</span></span>  |  <span data-ttu-id="75310-508">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-508">Meets</span></span> |  <span data-ttu-id="75310-509">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-510">Visualisierung der räumlichen Mesh erkennen Sie, dass Benutzer, die Überprüfung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="75310-511">Benutzer werden eindeutig weiß, was zu tun ist und wenn die Überprüfung wird gestartet und angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="75310-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="75310-512">Visualisierung der räumlichen Mesh angegeben ist, ist aber der Benutzer wissen möglicherweise nicht klar, was zu tun ist und keine Statusinformationen.</span><span class="sxs-lookup"><span data-stu-id="75310-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="75310-513">Keine Visualisierung des Mesh.</span><span class="sxs-lookup"><span data-stu-id="75310-513">No visualization of mesh.</span></span> <span data-ttu-id="75310-514">Keine Informationen bereitgestellt, um dem Benutzer, wo Sie suchen, oder wenn die Überprüfung startet/beendet wird.</span><span class="sxs-lookup"><span data-stu-id="75310-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="75310-515">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-515">How to measure</span></span>

* <span data-ttu-id="75310-516">SEH- und bei der Überprüfung erforderlichen Platz bietet es Anleitungen, der angibt, wo gesucht werden soll, und wann starten und beenden zu scannen.</span><span class="sxs-lookup"><span data-stu-id="75310-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-517">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-517">Recommendations</span></span>

* <span data-ttu-id="75310-518">Geben Sie an, welcher Anteil der Gesamtgröße des Datenträgers in der Nähe der Benutzer muss in der Umgebung sein.</span><span class="sxs-lookup"><span data-stu-id="75310-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="75310-519">Wenn die Überprüfung wird gestartet und beendet werden, z. B. eine Statusanzeige zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="75310-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="75310-520">Verwenden Sie eine Visualisierung des Netzes während der Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="75310-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="75310-521">Geben Sie SEH- und Hinweise, um den Benutzern suchen, und bewegen den Raum empfehlen.</span><span class="sxs-lookup"><span data-stu-id="75310-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="75310-522">Informieren Sie den Benutzer, wohin Sie wechseln, um die Daten zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="75310-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="75310-523">In vielen Fällen ist es möglicherweise am besten, die dem Benutzer mitzuteilen, was sie (z. B. die Obergrenze suchen hinter Möbel ansehen), um die Überprüfung der erforderlichen Qualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="75310-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-524">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="75310-525">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="75310-525">Documentation</span></span>

* [<span data-ttu-id="75310-526">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="75310-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="75310-527">Fallstudie: Erweitern die räumlichen Funktionen für die Zuordnung von HoloLens</span><span class="sxs-lookup"><span data-stu-id="75310-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="75310-528">Fallstudie: Räumliche Entwurf für HoloTour</span><span class="sxs-lookup"><span data-stu-id="75310-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="75310-529">Fallstudie: Erstellen ein Eintauchen in Fragmenten</span><span class="sxs-lookup"><span data-stu-id="75310-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="75310-530">Tools und tutorials</span><span class="sxs-lookup"><span data-stu-id="75310-530">Tools and tutorials</span></span>

* [<span data-ttu-id="75310-531">Mixed Reality-Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="75310-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="75310-532">Direktionale Indikatoren</span><span class="sxs-lookup"><span data-stu-id="75310-532">Directional indicators</span></span>

<span data-ttu-id="75310-533">In einer mixed Reality-app Inhalt möglicherweise außerhalb der Sichtfeld oder von realen Objekten okkludiert.</span><span class="sxs-lookup"><span data-stu-id="75310-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="75310-534">Eine wohlgeformte-app wird für den Benutzer nicht sichtbaren Inhalt erleichtern.</span><span class="sxs-lookup"><span data-stu-id="75310-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="75310-535">Direktionale Indikatoren warnen ein Benutzers auf wichtige Inhalte und bieten eine Anleitung, um den Inhalt relativ zur Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="75310-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="75310-536">Anleitungen, die nicht sichtbaren Inhalt kann es sich um die Form der sound korrekturemitter ab, mithilfe von Richtungspfeilen oder direkte visuelle Hinweise haben.</span><span class="sxs-lookup"><span data-stu-id="75310-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-537">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-540">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-541">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-542">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-542">Quality criteria</span></span>

|  <span data-ttu-id="75310-543">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-543">Best</span></span>  |  <span data-ttu-id="75310-544">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-544">Meets</span></span> |  <span data-ttu-id="75310-545">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-546">SEH- und Hinweise führen den Benutzer direkt zu den relevanten Inhalten außerhalb Blickfeld.</span><span class="sxs-lookup"><span data-stu-id="75310-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="75310-547">Ein Pfeil, oder einige Indikator, der der Benutzer in die allgemeine Richtung an, der den Inhalt verweist.</span><span class="sxs-lookup"><span data-stu-id="75310-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="75310-548">Relevante Inhalte außerhalb der Sichtfeld, und eine schlechte oder kein Speicherort enthält Anweisungen für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="75310-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="75310-549">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-549">How to measure</span></span>

* <span data-ttu-id="75310-550">Relevante Inhalte außerhalb der Sicht des Benutzers ist visual und/oder Hinweise ermittelt.</span><span class="sxs-lookup"><span data-stu-id="75310-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-551">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-551">Recommendations</span></span>

* <span data-ttu-id="75310-552">Verwenden Sie, wenn außerhalb des Benutzers Sichtfeld relevanten Inhalt ist ein direktionaler Indikatoren und Audiohinweise an den Benutzer auf den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="75310-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="75310-553">In vielen Fällen wird eine direkte visuelle Anleitung über Richtungspfeile bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="75310-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="75310-554">Direktionale Indikatoren sollten in den Cursor nicht erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="75310-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-555">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-555">Resources</span></span>

* [<span data-ttu-id="75310-556">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="75310-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="75310-557">Laden von Daten</span><span class="sxs-lookup"><span data-stu-id="75310-557">Data loading</span></span>

<span data-ttu-id="75310-558">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="75310-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="75310-559">Dies kann bedeuten, dass der Benutzer mit der app interagieren nicht möglich, wenn die Statusanzeige angezeigt wird und auch angeben kann, wie lange die Wartezeit möglicherweise.</span><span class="sxs-lookup"><span data-stu-id="75310-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="75310-560">Auswirkungen des Geräts</span><span class="sxs-lookup"><span data-stu-id="75310-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="75310-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="75310-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="75310-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="75310-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="75310-563">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75310-564">✔️</span><span class="sxs-lookup"><span data-stu-id="75310-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="75310-565">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="75310-565">Quality criteria</span></span>

|  <span data-ttu-id="75310-566">Am besten</span><span class="sxs-lookup"><span data-stu-id="75310-566">Best</span></span>  |  <span data-ttu-id="75310-567">Erfüllt</span><span class="sxs-lookup"><span data-stu-id="75310-567">Meets</span></span> |  <span data-ttu-id="75310-568">Fehler</span><span class="sxs-lookup"><span data-stu-id="75310-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="75310-569">Animierte visueller Indikator in Form einer Statusanzeige oder Ring, das Aufzeigen von Fortschritten bei der keine Daten laden oder zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="75310-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="75310-570">Der visuelle Indikator enthält Anleitungen, wie lange die Wartezeit werden konnte.</span><span class="sxs-lookup"><span data-stu-id="75310-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="75310-571">Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird, aber es gibt keinen Hinweis dafür, wie lange die Wartezeit sein kann.</span><span class="sxs-lookup"><span data-stu-id="75310-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="75310-572">Kein Laden von Daten oder die Prozess-Indikatoren für die Aufgabe, die länger als 5 Sekunden dauert.</span><span class="sxs-lookup"><span data-stu-id="75310-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="75310-573">Gewusst wie: messen</span><span class="sxs-lookup"><span data-stu-id="75310-573">How to measure</span></span>

* <span data-ttu-id="75310-574">Stellen Sie sicher, dass es mehr als 5 Sekunden ist kein leerer Zustand, beim Laden der Daten.</span><span class="sxs-lookup"><span data-stu-id="75310-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="75310-575">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="75310-575">Recommendations</span></span>

* <span data-ttu-id="75310-576">Geben Sie eine Data Loading Animator-aufzeigen von Fortschritten in allen Fällen, wenn der Benutzer diese app abgestürzt ist oder die Beantwortung wahrnehmen könnten.</span><span class="sxs-lookup"><span data-stu-id="75310-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="75310-577">Eine gute Faustregel ist, alle "laden"-Aktivität, die mehr als 5 Sekunden dauern.</span><span class="sxs-lookup"><span data-stu-id="75310-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="75310-578">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="75310-578">Resources</span></span>

* [<span data-ttu-id="75310-579">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="75310-579">Displaying progress</span></span>](progress.md)
