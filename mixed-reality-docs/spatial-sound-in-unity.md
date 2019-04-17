---
title: Räumliche Sound in Unity
description: Räumliche Sound wiedergeben, die stammt von einem bestimmten 3D Punkt innerhalb der Unity-Szene.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Sound, HRTF, Größe
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593232"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="a0a8b-104">Räumliche Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-104">Spatial sound in Unity</span></span>

<span data-ttu-id="a0a8b-105">Dieses Thema beschreibt, wie Sie räumliche Sound in Ihre Unity-Projekte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="a0a8b-106">Hierin sind die erforderlichen-Plug-in-Dateien als auch die Unity-Komponenten und die Eigenschaften, die räumliche Sound zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="a0a8b-107">Aktivieren von räumlichen Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="a0a8b-108">Räumliche Sound, in Unity ist eine audio Spatializer Plug-in aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="a0a8b-109">Die Plug-in-Dateien werden direkt in Unity gebündelt, also aktivieren räumliche Sound so einfach wie das möchte **Bearbeiten > Projekteinstellungen > Audio** und Ändern der **Spatializer-Plug-Ins** im Inspektor auf den  **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="a0a8b-110">Da der Microsoft-Spatializer nur 48000 Hz derzeit unterstützt, sollten Sie auch Ihr System Samplingrate festlegen, um 48000, um Fehler HRTF, in dem seltenen Fall zu verhindern, dass Ihr Systemgerät nicht bereits auf 48000 festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="a0a8b-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="a0a8b-111">![Inspektor für AudioManager](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="a0a8b-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="a0a8b-112">*Inspektor für AudioManager*</span><span class="sxs-lookup"><span data-stu-id="a0a8b-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="a0a8b-113">Ihr Unity-Projekt ist jetzt konfiguriert, um räumliche Sound zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="a0a8b-114">Wenn Sie ein Windows 10-PCs für die Entwicklung nicht verwenden, wird nicht räumlich Sound im Editor noch auf dem Gerät erhalten Sie (selbst wenn Sie das Windows 10-SDK verwenden).</span><span class="sxs-lookup"><span data-stu-id="a0a8b-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="a0a8b-115">Verwenden von räumlichen Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="a0a8b-116">Räumliche Sound wird in Ihrem Unity-Projekt verwendet, durch Anpassen der drei Einstellungen für die Audio Source-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="a0a8b-117">Die folgenden Schritte aus, werden Ihre Audio Source-Komponenten für räumliche Sound konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="a0a8b-118">In der **Hierarchie** wählen das spielobjekt, die eine angefügte **Audio Source**.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="a0a8b-119">In der **Inspektor** Bereich unter der **Audio Source** Komponente</span><span class="sxs-lookup"><span data-stu-id="a0a8b-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="a0a8b-120">Überprüfen Sie die **Spatialize** Option.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="a0a8b-121">Legen Sie **räumliche Blend** zu **3D** (numerischen Wert 1).</span><span class="sxs-lookup"><span data-stu-id="a0a8b-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="a0a8b-122">Erweitern Sie für optimale Ergebnisse **3D Sound Einstellungen** und legen Sie **Volume Rolloff** zu **benutzerdefinierte Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="a0a8b-123">![Inspector-Bereich, in die Audio-Quelle mit Unity](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="a0a8b-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="a0a8b-124">*Inspector-Bereich, in die Audio-Quelle mit Unity*</span><span class="sxs-lookup"><span data-stu-id="a0a8b-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="a0a8b-125">Ihre Sounds werden jetzt innerhalb der Umgebung des Projekts realistisch betrachtet sind!</span><span class="sxs-lookup"><span data-stu-id="a0a8b-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="a0a8b-126">Es wird dringend empfohlen, dass Sie sich mit vertraut der [räumlich Sound-Entwurfsrichtlinien](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="a0a8b-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="a0a8b-127">Diese Richtlinien unterstützen, Ihre Audio-nahtlos in Ihr Projekt integrieren und weiteren Benutzern in der Umgebung tauchen, die Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="a0a8b-128">Einrichtung von räumlichen Sound</span><span class="sxs-lookup"><span data-stu-id="a0a8b-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="a0a8b-129">Der Microsoft Spatial Sound-Plug-in bietet einen zusätzlichen Parameter, die auf festlegen werden kann, eine pro-Audio Source-Basis, um zusätzliche Kontrolle über die audio Simulation zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="a0a8b-130">Dieser Parameter ist die Größe des simulierten Raums.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="a0a8b-131">Der Größe</span><span class="sxs-lookup"><span data-stu-id="a0a8b-131">Room Size</span></span>

<span data-ttu-id="a0a8b-132">Die Größe der Raum, der durch räumliche Sound simuliert werden wird.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="a0a8b-133">Die ungefähre Größe der Räume sind. klein (einem Büro auf einem kleinen Konferenzraum), Mittel (einen großen Konferenzraum) "und" large (ein Hörsaal).</span><span class="sxs-lookup"><span data-stu-id="a0a8b-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="a0a8b-134">Sie können auch eine Größe ' None ' zum Simulieren einer outdoor-Umgebung angeben.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="a0a8b-135">Die Standardgröße des Raums ist klein.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="a0a8b-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a0a8b-136">Example</span></span>

<span data-ttu-id="a0a8b-137">Die MixedRealityToolkit für Unity bietet es sich um eine statische Klasse, mit der Einrichtung der räumlich Sound einfach.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="a0a8b-138">Diese Klasse finden Sie in der [MixedRealityToolkit\SpatialSound Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) und von einem Skript in Ihrem Projekt aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="a0a8b-139">Es wird empfohlen, dass Sie diese Parameter für jede Audio Source-Komponente in Ihr Projekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="a0a8b-140">Das folgende Beispiel zeigt die mittlere Größe für eine angefügte Audio-Datenquelle auswählen.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="a0a8b-141">Direktes Zugreifen auf Parameter von Unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="a0a8b-142">Wenn Sie nicht die ausgezeichnete Audio-Tools in der MixedRealityToolkit verwenden möchten, sieht aus wie Sie HRTF-Parameter ändern würde.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="a0a8b-143">Sie können kopieren und Einfügen dieser in ein Skript namens *SetHRTF.cs* , die Sie an jedem HRTF AudioSource anfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="a0a8b-144">Sie können Parameter, die wichtige zum HRTF zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="a0a8b-145">Räumliche Sound in Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="a0a8b-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="a0a8b-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="a0a8b-147">Die folgenden Beispiele aus dem Mixed Reality-Toolkit sind allgemeine Audioeffekt-Beispiele, die Möglichkeiten, um Ihre Erfahrungen seine machen, indem Sie mit der Sound zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="a0a8b-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="a0a8b-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="a0a8b-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="a0a8b-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="a0a8b-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a0a8b-150">See also</span></span>
* [<span data-ttu-id="a0a8b-151">Räumliche sound</span><span class="sxs-lookup"><span data-stu-id="a0a8b-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="a0a8b-152">Räumliche Entwurf</span><span class="sxs-lookup"><span data-stu-id="a0a8b-152">Spatial sound design</span></span>](spatial-sound-design.md)
