---
title: Räumlicher Sound in Unity
description: Wiedergabe von räumlichem Sound von einem bestimmten 3D-Punkt in der Unity-Szene.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Ton, HRTF, Raum Größe
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082043"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="60eec-104">Räumlicher Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="60eec-104">Spatial sound in Unity</span></span>

<span data-ttu-id="60eec-105">Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.</span><span class="sxs-lookup"><span data-stu-id="60eec-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="60eec-106">Spatializer-Optionen</span><span class="sxs-lookup"><span data-stu-id="60eec-106">Spatializer options</span></span>
<span data-ttu-id="60eec-107">Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="60eec-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="60eec-108">*MS HRTF spatializer*.</span><span class="sxs-lookup"><span data-stu-id="60eec-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="60eec-109">Unity stellt dies als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.</span><span class="sxs-lookup"><span data-stu-id="60eec-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="60eec-110">Dies erfolgt auf CPU in einer kostengünstigeren "Single Source"-Architektur.</span><span class="sxs-lookup"><span data-stu-id="60eec-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="60eec-111">Dies wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="60eec-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="60eec-112">Der *Microsoft spatializer*.</span><span class="sxs-lookup"><span data-stu-id="60eec-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="60eec-113">Dies ist im [GitHub-Repository von Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="60eec-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="60eec-114">Hierfür wird eine kostengünstigere Architektur mit mehreren Quellen verwendet.</span><span class="sxs-lookup"><span data-stu-id="60eec-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="60eec-115">Auf hololens 2 wird dies in einen Hardwarebeschleuniger verlagert.</span><span class="sxs-lookup"><span data-stu-id="60eec-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="60eec-116">Für neue Anwendungen wird *Microsoft spatializer*empfohlen.</span><span class="sxs-lookup"><span data-stu-id="60eec-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="60eec-117">Spatialization aktivieren</span><span class="sxs-lookup"><span data-stu-id="60eec-117">Enable spatialization</span></span>

<span data-ttu-id="60eec-118">Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus.</span><span class="sxs-lookup"><span data-stu-id="60eec-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="60eec-119">Dann:</span><span class="sxs-lookup"><span data-stu-id="60eec-119">Then:</span></span>
* <span data-ttu-id="60eec-120">Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="60eec-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="60eec-121">Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .</span><span class="sxs-lookup"><span data-stu-id="60eec-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="60eec-122">Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".</span><span class="sxs-lookup"><span data-stu-id="60eec-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="60eec-123">Stellen Sie sicher, dass auf Ihrer Entwickler Arbeitsstation räumliche Audiodaten aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="60eec-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="60eec-124">Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volumesymbol klicken und sicherstellen, dass räumlicher Sound auf einen anderen Wert als "Off" gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="60eec-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="60eec-125">Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **Windows Sonic für Kopfhörer aus**.</span><span class="sxs-lookup"><span data-stu-id="60eec-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="60eec-126">Wenn Sie in Unity eine Fehlermeldung erhalten, dass das Plug-in "Microsoft. spatialaudio. spatializer. unity" nicht geladen werden kann, weil eine ihrer Abhängigkeiten fehlt, überprüfen Sie, ob die neueste Version von [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) auf dem PC installiert ist.</span><span class="sxs-lookup"><span data-stu-id="60eec-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="60eec-127">Weitere Details findest du unter:</span><span class="sxs-lookup"><span data-stu-id="60eec-127">For more details, see:</span></span>
* [<span data-ttu-id="60eec-128">Microsoft spatializer-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="60eec-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="60eec-129">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="60eec-129">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="60eec-130">Dokumentation zur Audioquelle von Unity</span><span class="sxs-lookup"><span data-stu-id="60eec-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="60eec-131">Dokumentation zu spatializer von Unity</span><span class="sxs-lookup"><span data-stu-id="60eec-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="60eec-132">Entfernungs basierte Dämpfung</span><span class="sxs-lookup"><span data-stu-id="60eec-132">Distance-based attenuation</span></span>
<span data-ttu-id="60eec-133">Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf.</span><span class="sxs-lookup"><span data-stu-id="60eec-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="60eec-134">Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden.</span><span class="sxs-lookup"><span data-stu-id="60eec-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="60eec-135">Weitere Details findest du unter:</span><span class="sxs-lookup"><span data-stu-id="60eec-135">For more details, see:</span></span>
* <span data-ttu-id="60eec-136">[Sound Design in gemischter Realität](spatial-sound-design.md) für empfohlene Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="60eec-136">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="60eec-137">In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.</span><span class="sxs-lookup"><span data-stu-id="60eec-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="60eec-138">Hall</span><span class="sxs-lookup"><span data-stu-id="60eec-138">Reverb</span></span>
<span data-ttu-id="60eec-139">Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="60eec-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="60eec-140">So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:</span><span class="sxs-lookup"><span data-stu-id="60eec-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="60eec-141">Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.</span><span class="sxs-lookup"><span data-stu-id="60eec-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="60eec-142">Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.</span><span class="sxs-lookup"><span data-stu-id="60eec-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="60eec-143">Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="60eec-143">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="60eec-144">Beispiele für räumliche Unity-Sounds</span><span class="sxs-lookup"><span data-stu-id="60eec-144">Unity spatial sound examples</span></span>
<span data-ttu-id="60eec-145">Beispiele für räumliche Sounds in Unity finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="60eec-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="60eec-146">Mrtk-Demos</span><span class="sxs-lookup"><span data-stu-id="60eec-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="60eec-147">Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="60eec-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="60eec-148">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="60eec-148">Next steps</span></span>
* [<span data-ttu-id="60eec-149">Sound Design in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="60eec-149">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="60eec-150">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="60eec-150">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

