---
title: Audioinhalte in gemischter Realität
description: Audioinhalte in gemischter Realität können das Vertrauen von Benutzeroberflächen Interaktionen erhöhen und Benutzer in der Benutzeroberfläche eintauchen.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: räumlicher Sound, Umschließungs Sound, 3D--Audio, 3D--Ton, räumliche Audiodaten
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641108"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="95cb4-104">Audioinhalte in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="95cb4-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="95cb4-105">Audiodaten sind ein wesentlicher Bestandteil des Entwurfs und der Produktivität in gemischter Realität und können folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="95cb4-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="95cb4-106">Verbessern der Benutzer Zuverlässigkeit in Gesten-und sprachbasierten Interaktionen</span><span class="sxs-lookup"><span data-stu-id="95cb4-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="95cb4-107">Benutzer zu den nächsten Schritten führen</span><span class="sxs-lookup"><span data-stu-id="95cb4-107">Guide users to next steps</span></span>
* <span data-ttu-id="95cb4-108">Effektives kombinieren virtueller Objekte mit der realen Welt</span><span class="sxs-lookup"><span data-stu-id="95cb4-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="95cb4-109">Die Head-Nachverfolgung mit niedriger Latenz von Mixed Reality-Headsets, einschließlich hololens, ermöglicht die Verwendung der auf der HRTF basierenden Spatialisierung mit hoher Qualität.</span><span class="sxs-lookup"><span data-stu-id="95cb4-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="95cb4-110">Das spatialisieren von Audiodaten in der Anwendung kann:</span><span class="sxs-lookup"><span data-stu-id="95cb4-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="95cb4-111">Aufmerksamkeit von visuellen Elementen auf Aufrufe</span><span class="sxs-lookup"><span data-stu-id="95cb4-111">Call attention to visual elements</span></span>
* <span data-ttu-id="95cb4-112">Helfen Sie Benutzern dabei, das Bewusstsein für ihre reale Umgebung zu wahren.</span><span class="sxs-lookup"><span data-stu-id="95cb4-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="95cb4-113">Durch das Hinzufügen von Akustik werden Hologramme tiefer mit der gemischten Welt verbunden, und es können Hinweise zur Umgebung und zum Objektzustand bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="95cb4-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="95cb4-114">Ausführlichere Beispiele für den Entwurf mithilfe von Audio finden Sie unter [Sound Design](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="95cb4-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="95cb4-115">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="95cb4-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="95cb4-116"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="95cb4-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="95cb4-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="95cb4-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="95cb4-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="95cb4-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="95cb4-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="95cb4-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="95cb4-120">Spatialisierung</span><span class="sxs-lookup"><span data-stu-id="95cb4-120">Spatialization</span></span></td>
        <td><span data-ttu-id="95cb4-121">✔️</span><span class="sxs-lookup"><span data-stu-id="95cb4-121">✔️</span></span></td>
        <td><span data-ttu-id="95cb4-122">✔️</span><span class="sxs-lookup"><span data-stu-id="95cb4-122">✔️</span></span></td>
        <td><span data-ttu-id="95cb4-123">✔️</span><span class="sxs-lookup"><span data-stu-id="95cb4-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="95cb4-124">Beschleunigung der spatialisierungs Hardware</span><span class="sxs-lookup"><span data-stu-id="95cb4-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="95cb4-125">✔️</span><span class="sxs-lookup"><span data-stu-id="95cb4-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="95cb4-126">Verwenden von Sounds in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="95cb4-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="95cb4-127">Die [Verwendung von Sounds in gemischter Realität](spatial-sound-design.md) kann einen anderen Ansatz als in Anwendungen mit Finger Eingaben und Tastatur und Maus erfordern.</span><span class="sxs-lookup"><span data-stu-id="95cb4-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="95cb4-128">Wichtige Entscheidungen zum Entwurf von Entscheidungen umfassen, welche Sounds räumlich und welche Interaktionen mit sonify zu tun haben.</span><span class="sxs-lookup"><span data-stu-id="95cb4-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="95cb4-129">Diese Entscheidungen können starke Auswirkungen auf die Benutzer Zuverlässigkeit, Produktivität und Lernkurve haben.</span><span class="sxs-lookup"><span data-stu-id="95cb4-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="95cb4-130">Fallstudien</span><span class="sxs-lookup"><span data-stu-id="95cb4-130">Case studies</span></span>
<span data-ttu-id="95cb4-131">Mit holotour werden Benutzer praktisch zu touristischen und historischen Websites auf der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="95cb4-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="95cb4-132">Die folgende Fallstudie beschreibt den Sound Entwurf für holotour: [Sound Design für holotour](case-study-spatial-sound-design-for-holotour.md).</span><span class="sxs-lookup"><span data-stu-id="95cb4-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="95cb4-133">Ein spezielles Mikrofon und renderingsetup wurden zum Erfassen der Themenbereiche verwendet.</span><span class="sxs-lookup"><span data-stu-id="95cb4-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="95cb4-134">Roboraid ist ein Hochenergie geschütztes Gerät für hololens.</span><span class="sxs-lookup"><span data-stu-id="95cb4-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="95cb4-135">In der folgenden Fallstudie werden die Entwurfsentscheidungen beschrieben, mit denen sichergestellt wird, dass räumliche Audiodaten in vollem Umfang dramatisch umgesetzt werden: [Sound Design für roboraid](case-study-using-spatial-sound-in-roboraid.md).</span><span class="sxs-lookup"><span data-stu-id="95cb4-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="95cb4-136">Spatialisierung</span><span class="sxs-lookup"><span data-stu-id="95cb4-136">Spatialization</span></span>
<span data-ttu-id="95cb4-137">Spatialization ist die direktionale Komponente räumlicher Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="95cb4-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="95cb4-138">Bei Verwendung eines 7,1-Home-Theater Setups ist die Spatialisierung so einfach wie das Schwenken zwischen Lautsprecher.</span><span class="sxs-lookup"><span data-stu-id="95cb4-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="95cb4-139">Mit den Kopfhörern in gemischter Realität ist es jedoch von entscheidender Bedeutung, eine auf HRTF basierende Technologie für Genauigkeit und Komfort zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="95cb4-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="95cb4-140">Windows bietet eine auf HRTF basierende Spatialisierung. diese Unterstützung ist auf hololens 2 Hardware beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="95cb4-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="95cb4-141">Sollte ich räumlich spatialisieren?</span><span class="sxs-lookup"><span data-stu-id="95cb4-141">Should I spatialize?</span></span>
<span data-ttu-id="95cb4-142">Viele Sounds in Mixed Reality-Anwendungen profitieren von der Spatialisierung, bei der ein Sound aus dem Kopf des Listener hervorgeht und auf der ganzen Welt platziert wird.</span><span class="sxs-lookup"><span data-stu-id="95cb4-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="95cb4-143">Unter " [räumlicher Sound Entwurf](spatial-sound-design.md) " finden Sie Vorschläge zu den effektivsten Verwendungsmöglichkeiten der Spatialisierung in Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="95cb4-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="95cb4-144">Spatializer-Personalisierung</span><span class="sxs-lookup"><span data-stu-id="95cb4-144">Spatializer personalization</span></span>
<span data-ttu-id="95cb4-145">HRTFs bearbeitet die Ebenen-und Phasenunterschiede zwischen den Ohren im Frequenzspektrum.</span><span class="sxs-lookup"><span data-stu-id="95cb4-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="95cb4-146">Sie basieren auf physischen Modellen und Messungen von Menschen Kopf-, Rumpf-und Ohrformen (pinnae).</span><span class="sxs-lookup"><span data-stu-id="95cb4-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="95cb4-147">Unsere Gehirne reagieren auf diese Unterschiede, um einen Eindruck von der Richtung in Sound zu machen.</span><span class="sxs-lookup"><span data-stu-id="95cb4-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="95cb4-148">Jede Person verfügt über eine eindeutige Ohrform, Kopfgröße und Position, sodass Sie die besten HRTFs-Funktionen sind, die Ihnen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="95cb4-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="95cb4-149">Hololens erhöht die räumungsgenauigkeit, indem der IPD (Inter-pupilary Distance) aus den Headset-anzeigen verwendet wird, um den HRTFs für die Kopfgröße anzupassen.</span><span class="sxs-lookup"><span data-stu-id="95cb4-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="95cb4-150">Unterstützung für spatializer-Plattform</span><span class="sxs-lookup"><span data-stu-id="95cb4-150">Spatializer platform support</span></span>
<span data-ttu-id="95cb4-151">Windows bietet mithilfe der [ispatialaudioclient-API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)eine spatialization, einschließlich HRTFs.</span><span class="sxs-lookup"><span data-stu-id="95cb4-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="95cb4-152">Diese API macht die Hardwarebeschleunigung von hololens 2 HRTF für Anwendungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="95cb4-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="95cb4-153">Unterstützung für spatializer-Middleware</span><span class="sxs-lookup"><span data-stu-id="95cb4-153">Spatializer middleware support</span></span>
<span data-ttu-id="95cb4-154">Die Unterstützung für Windows ' HRTFs ist für einige Drittanbieter-AUDIOMODULE verfügbar:</span><span class="sxs-lookup"><span data-stu-id="95cb4-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="95cb4-155">Ein Plug-in für die [Unity-Audioengine](spatial-sound-in-unity.md) Ruft den HRTF xapo</span><span class="sxs-lookup"><span data-stu-id="95cb4-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="95cb4-156">Ein [wwise Audio Engine-Plug-](https://www.audiokinetic.com/products/plug-ins/msspatial/) in Ruft die ispatialaudioclient-API auf.</span><span class="sxs-lookup"><span data-stu-id="95cb4-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="95cb4-157">Akustische</span><span class="sxs-lookup"><span data-stu-id="95cb4-157">Acoustics</span></span>
<span data-ttu-id="95cb4-158">Räumliche Audiodaten können mehr als die Richtung aufweisen.</span><span class="sxs-lookup"><span data-stu-id="95cb4-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="95cb4-159">Andere Dimensionen, einschließlich Okklusion, Behinderung, Reverb, portalling und Quell Modellierung, werden kollektiv als "Akustik" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="95cb4-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="95cb4-160">Ohne Akustik fehlt bei spatialisierten Sounds eine nicht wahrgenommene Entfernung.</span><span class="sxs-lookup"><span data-stu-id="95cb4-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="95cb4-161">Die Akustik-Behandlung kann von einfach bis sehr komplex reichen.</span><span class="sxs-lookup"><span data-stu-id="95cb4-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="95cb4-162">Wenn Sie einen einfachen Reverb verwenden, wie z. b., der von einer beliebigen Audioengine unterstützt wird, können Sie spatialisierte Sounds in die Umgebung verschieben, die den Listener umgibt.</span><span class="sxs-lookup"><span data-stu-id="95cb4-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="95cb4-163">Umfangreichere und überzeugendere Reinigungsmöglichkeiten sind über Akustiksysteme verfügbar, wie z. b. die [Projekt Akustik](https://aka.ms/acoustics).</span><span class="sxs-lookup"><span data-stu-id="95cb4-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="95cb4-164">Die Projekt Akustik kann die Auswirkung von Wänden, Türen und anderen Szenen Geometrie in einem Sound modellieren und ist eine effektive Option für Fälle, in denen die relevante Szene Geometrie zur Entwicklungszeit bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="95cb4-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

