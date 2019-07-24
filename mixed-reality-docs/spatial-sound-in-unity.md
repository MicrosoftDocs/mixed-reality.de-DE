---
title: Räumlicher Sound in Unity
description: Wiedergabe von räumlichem Sound, der von einem bestimmten 3D-Punkt in der Unity-Szene stammt.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumlicher Ton, HRTF, Raum Größe
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549083"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="334af-104">Räumlicher Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="334af-104">Spatial sound in Unity</span></span>

<span data-ttu-id="334af-105">In diesem Thema wird beschrieben, wie räumlicher Sound in ihren Unity-Projekten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="334af-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="334af-106">Dabei werden die erforderlichen Plug-in-Dateien sowie die Unity-Komponenten und-Eigenschaften behandelt, die räumliche Sounds ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="334af-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="334af-107">Aktivieren von räumlichem Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="334af-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="334af-108">Räumlicher Sound wird in Unity mithilfe eines audiospatializer-Plug-ins aktiviert.</span><span class="sxs-lookup"><span data-stu-id="334af-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="334af-109">Die Plug-in-Dateien werden direkt in Unity gebündelt, sodass das Aktivieren von räumlichem Sound so einfach ist wie das **Bearbeiten > Projekteinstellungen > Audio** und das Ändern des **spatializer-Plug** -ins im Inspektor in den " **MS HRTF spatializer**".</span><span class="sxs-lookup"><span data-stu-id="334af-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="334af-110">Da Microsoft spatializer derzeit nur 48000Hz unterstützt, sollten Sie die System Stichproben Rate auch auf 48000 festlegen, um einen HRTF-Fehler zu vermeiden, wenn das System Ausgabegerät nicht bereits auf 48000 festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="334af-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="334af-111">![Inspektor für Audiomanager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="334af-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="334af-112">*Inspektor für Audiomanager*</span><span class="sxs-lookup"><span data-stu-id="334af-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="334af-113">Ihr Unity-Projekt ist nun so konfiguriert, dass räumliche Töne verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="334af-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="334af-114">Wenn Sie keinen Windows 10-PC für die Entwicklung verwenden, erhalten Sie keinen räumlichen Ton im Editor und nicht auf dem Gerät (auch wenn Sie das Windows 10 SDK verwenden).</span><span class="sxs-lookup"><span data-stu-id="334af-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="334af-115">Verwenden von räumlichem Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="334af-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="334af-116">Räumlicher Sound wird in Ihrem Unity-Projekt verwendet, indem drei Einstellungen in den audioquellkomponenten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="334af-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="334af-117">Mit den folgenden Schritten werden die audioquellkomponenten für räumliche Audiodaten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="334af-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="334af-118">Wählen Sie im Bereich **Hierarchie** das Spielobjekt aus, das über eine angefügte **Audioquelle**verfügt.</span><span class="sxs-lookup"><span data-stu-id="334af-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="334af-119">Im **Inspektor** -Panel unter der Komponente **Audioquelle**</span><span class="sxs-lookup"><span data-stu-id="334af-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="334af-120">Aktivieren Sie die Option **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="334af-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="334af-121">Legen Sie **räumliche Blend** auf **3D** (numerischer Wert 1) fest.</span><span class="sxs-lookup"><span data-stu-id="334af-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="334af-122">Um optimale Ergebnisse zu erzielen, erweitern Sie **3D Sound Settings** , und legen Sie **volumerrolloff** auf **benutzerdefiniertes Rolloff**fest</span><span class="sxs-lookup"><span data-stu-id="334af-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="334af-123">![Inspektor-Panel in Unity, das die Audioquelle anzeigt](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="334af-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="334af-124">*Inspektor-Panel in Unity, das die Audioquelle anzeigt*</span><span class="sxs-lookup"><span data-stu-id="334af-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="334af-125">Ihre Sounds sind nun realistisch in der Umgebung des Projekts vorhanden!</span><span class="sxs-lookup"><span data-stu-id="334af-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="334af-126">Es wird dringend empfohlen, sich mit den [räumlichen Entwurfs Richtlinien](spatial-sound-design.md)vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="334af-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="334af-127">Diese Richtlinien tragen dazu bei, ihre Audioinhalte nahtlos in Ihr Projekt zu integrieren und Ihre Benutzer in die von Ihnen erstellte Benutzererlebnis zu vertiefen.</span><span class="sxs-lookup"><span data-stu-id="334af-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="334af-128">Festlegen räumlicher Sound Einstellungen</span><span class="sxs-lookup"><span data-stu-id="334af-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="334af-129">Das Microsoft Spatial Sound Plugin bietet einen zusätzlichen Parameter, der pro Audioquelle festgelegt werden kann, um eine zusätzliche Steuerung der Audiosimulation zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="334af-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="334af-130">Dieser Parameter ist die Größe des simulierten Raums.</span><span class="sxs-lookup"><span data-stu-id="334af-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="334af-131">Raum Größe</span><span class="sxs-lookup"><span data-stu-id="334af-131">Room Size</span></span>

<span data-ttu-id="334af-132">Die Größe des Raums, der durch räumlichen Ton simuliert wird.</span><span class="sxs-lookup"><span data-stu-id="334af-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="334af-133">Die ungefähren Größen der Räume sind: klein (ein Büro in einem kleinen Konferenzraum), Mittel (ein großer Konferenzraum) und groß (ein Auditorium).</span><span class="sxs-lookup"><span data-stu-id="334af-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="334af-134">Sie können auch eine Raum Größe von keine angeben, um eine Umgebung im Außenbereich zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="334af-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="334af-135">Die Standard Raum Größe ist klein.</span><span class="sxs-lookup"><span data-stu-id="334af-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="334af-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="334af-136">Example</span></span>

<span data-ttu-id="334af-137">Das mixedrealitytoolkit für Unity stellt eine statische Klasse bereit, die das Festlegen der räumlichen Sound Einstellungen vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="334af-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="334af-138">Diese Klasse befindet sich im [Ordner mixedrealitytoolkit\spatialsound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) und kann von jedem Skript in Ihrem Projekt aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="334af-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="334af-139">Es wird empfohlen, diese Parameter für jede audioquellkomponente im Projekt festzulegen.</span><span class="sxs-lookup"><span data-stu-id="334af-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="334af-140">Das folgende Beispiel zeigt, wie die mittlere Raum Größe für eine angefügte Audioquelle ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="334af-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="334af-141">Direkter Zugriff auf Parameter aus Unity</span><span class="sxs-lookup"><span data-stu-id="334af-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="334af-142">Wenn Sie die ausgezeichneten Audiotools im mixedrealitytoolkit nicht verwenden möchten, finden Sie hier Informationen zum Ändern von HRTF-Parametern.</span><span class="sxs-lookup"><span data-stu-id="334af-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="334af-143">Sie können diese Datei in ein Skript mit dem Namen *SetHRTF.cs* kopieren bzw. einfügen, das Sie an jede HRTF audiosource anfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="334af-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="334af-144">Damit können Sie die Parameter ändern, die für HRTF wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="334af-144">It lets you change parameters important to HRTF.</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="334af-145">Räumlicher Sound im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="334af-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="334af-146">HoloToolkit-examples/spatialsound/Szenen/uaudiomanagertest. unity</span><span class="sxs-lookup"><span data-stu-id="334af-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="334af-147">Die folgenden Beispiele aus dem Mixed Reality Toolkit sind allgemeine Beispiele für Audioeffekte, die veranschaulichen, wie Sie Ihre Erfahrungen mit Sound rekursiv gestalten können.</span><span class="sxs-lookup"><span data-stu-id="334af-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="334af-148">HoloToolkit-examples/spatialsound/Szenen/audiolometest. unity</span><span class="sxs-lookup"><span data-stu-id="334af-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="334af-149">HoloToolkit-examples/spatialsound/Szenen/audiookoksiontest. unity</span><span class="sxs-lookup"><span data-stu-id="334af-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="334af-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="334af-150">See also</span></span>
* [<span data-ttu-id="334af-151">Raumklang</span><span class="sxs-lookup"><span data-stu-id="334af-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="334af-152">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="334af-152">Spatial sound design</span></span>](spatial-sound-design.md)
