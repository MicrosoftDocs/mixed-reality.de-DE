---
title: Spectator View
description: Visualisieren Sie Hologramme von einem externen Gerät als Mittel zur Darstellung eines Mixed Reality-Erlebnisses auf einem externen Display oder zur Aufzeichnung eines Mixed Reality-Erlebnisses.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Kamera, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, Demo, aufzeichnen
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491160"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="c2326-104">Spectator View für HoloLens und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c2326-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="c2326-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c2326-106">Overview</span></span>

<span data-ttu-id="c2326-107">Beim Tragen einer HoloLens vergessen wir oft, dass eine Person, die sie nicht trägt, all die Wunder, die wir erfahren, nicht erleben kann.</span><span class="sxs-lookup"><span data-stu-id="c2326-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="c2326-108">Mit Spectator View können andere auf einem zweidimensionalen Bildschirm sehen, was HoloLens-Benutzer in ihrer Welt sehen.</span><span class="sxs-lookup"><span data-stu-id="c2326-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="c2326-109">Spectator View bietet einen schnellen und bezahlbaren Ansatz zum Aufzeichnen von Hologrammen in HD mit mobilen Geräten.</span><span class="sxs-lookup"><span data-stu-id="c2326-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="c2326-110">Ferner bietet es die Möglichkeit zur Aufzeichnung von Hologrammen mit Videokameras in professioneller Qualität.</span><span class="sxs-lookup"><span data-stu-id="c2326-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="c2326-111">Wichtige Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c2326-111">Key Resources</span></span>

* [<span data-ttu-id="c2326-112">**Spectator View auf GitHub**</span><span class="sxs-lookup"><span data-stu-id="c2326-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="c2326-113">**Spectator View-Dokumentation**</span><span class="sxs-lookup"><span data-stu-id="c2326-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="c2326-114">**Spectator View-Beispiele**</span><span class="sxs-lookup"><span data-stu-id="c2326-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="c2326-115">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="c2326-115">Use Cases</span></span>
* <span data-ttu-id="c2326-116">Sie können ein Mixed Reality-Erlebnis mithilfe eines iPhone- oder Android-Geräts aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="c2326-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="c2326-117">Zeichnen Sie in Full HD auf, und wenden Sie Antialiasing auf Hologramme und sogar auf Schatten an.</span><span class="sxs-lookup"><span data-stu-id="c2326-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="c2326-118">Dies ist eine kostengünstige und schnelle Möglichkeit zum Erfassen von Videos von Hologrammen.</span><span class="sxs-lookup"><span data-stu-id="c2326-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="c2326-119">Streamen Sie von Ihrem iPhone oder iPad verzögerungsfrei Mixed Reality-Erlebnisse live auf ein Apple TV!</span><span class="sxs-lookup"><span data-stu-id="c2326-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="c2326-120">Teilen Sie das Erlebnis mit Gästen: Lassen Sie Benutzer ohne HoloLens Hologramme direkt auf Ihren Smartphones oder Tablets erleben.</span><span class="sxs-lookup"><span data-stu-id="c2326-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="c2326-121">Aktuelle Features</span><span class="sxs-lookup"><span data-stu-id="c2326-121">Current Features</span></span>

* <span data-ttu-id="c2326-122">Synchronisierung von Hologrammen im Raum, sodass alle die Hologramme an genau der gleichen Stelle sehen.</span><span class="sxs-lookup"><span data-stu-id="c2326-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="c2326-123">Unterstützung für iOS- (ARKit-fähige Geräte) und Android-Geräte (ARCore-fähige Geräte).</span><span class="sxs-lookup"><span data-stu-id="c2326-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="c2326-124">Mehrere iOS-Gäste.</span><span class="sxs-lookup"><span data-stu-id="c2326-124">Multiple iOS guests.</span></span>
<span data-ttu-id="c2326-125">Aufzeichnung von Video + Hologrammen + Raumklang + Hologrammklang.</span><span class="sxs-lookup"><span data-stu-id="c2326-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="c2326-126">Freigabeblatt, auf dem Sie Videos speichern, sie per E-Mail senden oder sie mit anderen unterstützten Apps teilen können.</span><span class="sxs-lookup"><span data-stu-id="c2326-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="c2326-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="c2326-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="c2326-128">In der folgenden Tabelle sind verschiedene Funktionen von Spectator View aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c2326-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="c2326-129">Wählen Sie die Option aus, die Ihren Anforderungen an Videoaufzeichnung am besten entspricht:</span><span class="sxs-lookup"><span data-stu-id="c2326-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="c2326-130">Mobile</span><span class="sxs-lookup"><span data-stu-id="c2326-130">Mobile</span></span>                  |                    <span data-ttu-id="c2326-131">Videokamera</span><span class="sxs-lookup"><span data-stu-id="c2326-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="c2326-132">HD-Qualität</span><span class="sxs-lookup"><span data-stu-id="c2326-132">HD quality</span></span>                           |         <span data-ttu-id="c2326-133">Full HD</span><span class="sxs-lookup"><span data-stu-id="c2326-133">Full HD</span></span>         |        <span data-ttu-id="c2326-134">Filmen in professioneller Qualität (durch die Videokamera bestimmt)</span><span class="sxs-lookup"><span data-stu-id="c2326-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="c2326-135">Einfache Kamerabewegung</span><span class="sxs-lookup"><span data-stu-id="c2326-135">Easy camera movement</span></span>                 |            <span data-ttu-id="c2326-136">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-136">✔</span></span>            |                      <span data-ttu-id="c2326-137">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-137">✔</span></span>                      |
| <span data-ttu-id="c2326-138">Third-Person-Ansicht</span><span class="sxs-lookup"><span data-stu-id="c2326-138">Third-person view</span></span>                    |            <span data-ttu-id="c2326-139">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-139">✔</span></span>            |                      <span data-ttu-id="c2326-140">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-140">✔</span></span>                      |
| <span data-ttu-id="c2326-141">Kann auf Bildschirme gestreamt werden</span><span class="sxs-lookup"><span data-stu-id="c2326-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="c2326-142">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-142">✔</span></span>            |                      <span data-ttu-id="c2326-143">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-143">✔</span></span>                      |
| <span data-ttu-id="c2326-144">Tragbar</span><span class="sxs-lookup"><span data-stu-id="c2326-144">Portable</span></span>                             |            <span data-ttu-id="c2326-145">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-145">✔</span></span>            |                                             |
| <span data-ttu-id="c2326-146">Drahtlos</span><span class="sxs-lookup"><span data-stu-id="c2326-146">Wireless</span></span>                             |            <span data-ttu-id="c2326-147">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-147">✔</span></span>            |                                             |
| <span data-ttu-id="c2326-148">Zusätzlich erforderliche Hardware</span><span class="sxs-lookup"><span data-stu-id="c2326-148">Additional required hardware</span></span>         |     <span data-ttu-id="c2326-149">Android-Smartphone, iPhone</span><span class="sxs-lookup"><span data-stu-id="c2326-149">Android phone, iPhone</span></span>    | <span data-ttu-id="c2326-150">HoloLens + Rig + Stativ + Videokamera + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="c2326-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="c2326-151">Hardwareinvestition</span><span class="sxs-lookup"><span data-stu-id="c2326-151">Hardware investment</span></span>                  |           <span data-ttu-id="c2326-152">Niedrig</span><span class="sxs-lookup"><span data-stu-id="c2326-152">Low</span></span>            |                     <span data-ttu-id="c2326-153">Hoch</span><span class="sxs-lookup"><span data-stu-id="c2326-153">High</span></span>                    |
| <span data-ttu-id="c2326-154">Plattformübergreifend</span><span class="sxs-lookup"><span data-stu-id="c2326-154">Cross-platform</span></span>                       |           <span data-ttu-id="c2326-155">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="c2326-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="c2326-156">Synchronisierte Inhalte</span><span class="sxs-lookup"><span data-stu-id="c2326-156">Synchronized content</span></span>                 |            <span data-ttu-id="c2326-157">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-157">✔</span></span>            |                      <span data-ttu-id="c2326-158">✔</span><span class="sxs-lookup"><span data-stu-id="c2326-158">✔</span></span>                      |
| <span data-ttu-id="c2326-159">Dauer des Runtime-Setups</span><span class="sxs-lookup"><span data-stu-id="c2326-159">Runtime setup duration</span></span>               |         <span data-ttu-id="c2326-160">Instant</span><span class="sxs-lookup"><span data-stu-id="c2326-160">Instant</span></span>          |                     <span data-ttu-id="c2326-161">Langsam</span><span class="sxs-lookup"><span data-stu-id="c2326-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="c2326-162">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c2326-162">See also</span></span>

* [<span data-ttu-id="c2326-163">Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="c2326-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="c2326-164">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="c2326-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="c2326-165">Gemeinsame Erlebnisse in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c2326-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
