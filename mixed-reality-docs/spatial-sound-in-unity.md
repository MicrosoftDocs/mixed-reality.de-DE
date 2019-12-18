---
title: Räumlicher Sound in Unity
description: Wiedergabe von räumlichem Sound von einem bestimmten 3D-Punkt in der Unity-Szene.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Ton, HRTF, Raum Größe
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181990"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="4a00a-104">Räumlicher Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="4a00a-104">Spatial sound in Unity</span></span>

<span data-ttu-id="4a00a-105">Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.</span><span class="sxs-lookup"><span data-stu-id="4a00a-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="4a00a-106">Spatializer-Optionen</span><span class="sxs-lookup"><span data-stu-id="4a00a-106">Spatializer options</span></span>
<span data-ttu-id="4a00a-107">Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="4a00a-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="4a00a-108">*MS HRTF spatializer*.</span><span class="sxs-lookup"><span data-stu-id="4a00a-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="4a00a-109">Unity stellt dies als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.</span><span class="sxs-lookup"><span data-stu-id="4a00a-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="4a00a-110">Dies erfolgt auf CPU in einer kostengünstigeren "Single Source"-Architektur.</span><span class="sxs-lookup"><span data-stu-id="4a00a-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="4a00a-111">Dies wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4a00a-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="4a00a-112">Der *Microsoft spatializer*.</span><span class="sxs-lookup"><span data-stu-id="4a00a-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="4a00a-113">Dies ist im [GitHub-Repository von Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4a00a-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="4a00a-114">Hierfür wird eine kostengünstigere Architektur mit mehreren Quellen verwendet.</span><span class="sxs-lookup"><span data-stu-id="4a00a-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="4a00a-115">Auf hololens 2 wird dies in einen Hardwarebeschleuniger verlagert.</span><span class="sxs-lookup"><span data-stu-id="4a00a-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="4a00a-116">Für neue Anwendungen wird *Microsoft spatializer*empfohlen.</span><span class="sxs-lookup"><span data-stu-id="4a00a-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="4a00a-117">Spatialization aktivieren</span><span class="sxs-lookup"><span data-stu-id="4a00a-117">Enable spatialization</span></span>

<span data-ttu-id="4a00a-118">Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus.</span><span class="sxs-lookup"><span data-stu-id="4a00a-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="4a00a-119">Anschließend:</span><span class="sxs-lookup"><span data-stu-id="4a00a-119">Then:</span></span>
* <span data-ttu-id="4a00a-120">Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="4a00a-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="4a00a-121">Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .</span><span class="sxs-lookup"><span data-stu-id="4a00a-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="4a00a-122">Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".</span><span class="sxs-lookup"><span data-stu-id="4a00a-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="4a00a-123">Weitere Details findest du unter:</span><span class="sxs-lookup"><span data-stu-id="4a00a-123">For more details, see:</span></span>
* [<span data-ttu-id="4a00a-124">Microsoft spatializer-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="4a00a-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="4a00a-125">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="4a00a-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="4a00a-126">Dokumentation zur Audioquelle von Unity</span><span class="sxs-lookup"><span data-stu-id="4a00a-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="4a00a-127">Dokumentation zu spatializer von Unity</span><span class="sxs-lookup"><span data-stu-id="4a00a-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="4a00a-128">Distanzabhängige Dämpfung</span><span class="sxs-lookup"><span data-stu-id="4a00a-128">Distance-based attenuation</span></span>
<span data-ttu-id="4a00a-129">Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf.</span><span class="sxs-lookup"><span data-stu-id="4a00a-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="4a00a-130">Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden.</span><span class="sxs-lookup"><span data-stu-id="4a00a-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="4a00a-131">Weitere Details findest du unter:</span><span class="sxs-lookup"><span data-stu-id="4a00a-131">For more details, see:</span></span>
* <span data-ttu-id="4a00a-132">[Sound Design in gemischter Realität](spatial-sound-design.md) für empfohlene Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="4a00a-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="4a00a-133">In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.</span><span class="sxs-lookup"><span data-stu-id="4a00a-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="4a00a-134">Hall</span><span class="sxs-lookup"><span data-stu-id="4a00a-134">Reverb</span></span>
<span data-ttu-id="4a00a-135">Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="4a00a-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="4a00a-136">So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:</span><span class="sxs-lookup"><span data-stu-id="4a00a-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="4a00a-137">Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.</span><span class="sxs-lookup"><span data-stu-id="4a00a-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="4a00a-138">Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.</span><span class="sxs-lookup"><span data-stu-id="4a00a-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="4a00a-139">Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="4a00a-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="4a00a-140">Beispiele für räumliche Unity-Sounds</span><span class="sxs-lookup"><span data-stu-id="4a00a-140">Unity spatial sound examples</span></span>
<span data-ttu-id="4a00a-141">Beispiele für räumliche Sounds in Unity finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="4a00a-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="4a00a-142">Mrtk-Demos</span><span class="sxs-lookup"><span data-stu-id="4a00a-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="4a00a-143">Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="4a00a-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a00a-144">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="4a00a-144">Next steps</span></span>
* [<span data-ttu-id="4a00a-145">Sound Design in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="4a00a-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="4a00a-146">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="4a00a-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

