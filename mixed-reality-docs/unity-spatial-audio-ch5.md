---
title: Lernprogramme für räumliche Audiodaten-5. Verwenden von Reverb zum Hinzufügen von Abstand zu räumlichem Audio
description: Fügen Sie einen Hall Effekt hinzu, um den Sinn der Abstands Variation zu räumlichem Audiomaterial zu verbessern.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182737"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="5ea5f-105">Verwenden von Reverb zum Hinzufügen von Abstand zu räumlichem Audio</span><span class="sxs-lookup"><span data-stu-id="5ea5f-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="5ea5f-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="5ea5f-106">Objectives</span></span>
<span data-ttu-id="5ea5f-107">In den vorherigen Kapiteln haben wir den Sound spatialization hinzugefügt, um Ihnen einen Eindruck von der Richtung zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="5ea5f-108">In diesem fünften Kapitel fügen wir einen "Reverb"-Effekt hinzu, um Klänge einen Eindruck von der Entfernung zu geben.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="5ea5f-109">Unsere Ziele lauten:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-109">Our objectives are to:</span></span>
* <span data-ttu-id="5ea5f-110">Verbessern der erkannten Entfernung von Soundquellen durch Hinzufügen von Reverb</span><span class="sxs-lookup"><span data-stu-id="5ea5f-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="5ea5f-111">Den erkannten Abstand des Sounds mithilfe der Entfernung des Listener zum – Hologramm Steuern</span><span class="sxs-lookup"><span data-stu-id="5ea5f-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="5ea5f-112">Hinzufügen einer mischkeitsgruppe und eines einfügenden Effekts</span><span class="sxs-lookup"><span data-stu-id="5ea5f-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="5ea5f-113">In [Kapitel 2](unity-spatial-audio-ch2.md)haben wir einen Mixer hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="5ea5f-114">Der Mixer enthält standardmäßig eine **Gruppe** namens **Master**.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-114">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="5ea5f-115">Da wir nur einen "Hall"-Effekt auf einige Sounds anwenden möchten, fügen wir eine zweite **Gruppe** für diese Sounds hinzu.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="5ea5f-116">Um eine **Gruppe**hinzuzufügen, klicken Sie mit der rechten Maustaste auf die **Master** Gruppe im **Audiomixer** und wählen untergeordnete **Gruppe hinzufügen**aus:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-116">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![Untergeordnete Gruppe hinzufügen](images/spatial-audio/add-child-group.png)

<span data-ttu-id="5ea5f-118">In diesem Beispiel haben wir die neue Gruppe "Raumeffekt" benannt.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="5ea5f-119">Jede **Gruppe** hat einen eigenen Satz von Effekten.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="5ea5f-120">Fügen Sie der neuen Gruppe einen connectoreffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen** klicken, und wählen Sie **SFX-Hall**:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![SFX-Reverb hinzufügen](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="5ea5f-122">In der audioterminologie wird der ursprüngliche, nicht widerzuhallte _Audiopfad als trockener Pfad_bezeichnet, und die Audiodatei nach dem Filtern mit dem Hall Filter wird als _Nasser Pfad_bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-122">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="5ea5f-123">Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _nass/trocken Mischung_bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="5ea5f-124">Die nasse/trockene Mischung wirkt sich stark auf den Sinn der Entfernung aus.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="5ea5f-125">Der **SFX-Reverb umfasst Steuer** Elemente, mit denen die nasse/trockene Mischung innerhalb des Effekts angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="5ea5f-126">Da das **Microsoft spatializer** -Plug-in den trockenen Pfad behandelt, verwenden wir den **SFX-Reverb** nur für den nassen Pfad.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="5ea5f-127">Im **inspektorbereich** Ihres **SFX-einhall**:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-127">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="5ea5f-128">Legen Sie die Eigenschaft "Dry Level" auf die niedrigste Einstellung fest (-10000 MB).</span><span class="sxs-lookup"><span data-stu-id="5ea5f-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="5ea5f-129">Legen Sie die Eigenschaft "Room" auf die höchste Einstellung (0 MB) fest.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="5ea5f-130">Nachdem diese Änderungen vorgenommen wurden, sieht der **inspektorbereich** des **SFX-Reverb** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![SFX-Reverb-Eigenschaften](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="5ea5f-132">Mit den anderen Einstellungen wird das Gefühl des simulierten Raums gesteuert.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="5ea5f-133">Die **verwahrzeit** bezieht sich insbesondere auf die wahrgenommene Raum Größe.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="5ea5f-134">Aktivieren von "Reverb" für die Videowiedergabe</span><span class="sxs-lookup"><span data-stu-id="5ea5f-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="5ea5f-135">Zum Aktivieren von "Reverb" in einer Audioquelle müssen zwei Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="5ea5f-136">Leiten Sie die **Audioquelle** an die entsprechende **Gruppe** weiter.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="5ea5f-137">Festlegen des **Microsoft spatializer** -Plug-ins, um Audioinformationen zur Verarbeitung an die **Gruppe** zu übergeben</span><span class="sxs-lookup"><span data-stu-id="5ea5f-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="5ea5f-138">In den folgenden Schritten wird das Skript angepasst, um das Audiorouting zu steuern, und es wird ein mit dem **Microsoft spatializer** -Plug-in bereitgestelltes Steuerelement Skript zum Übertragen von Daten in den Reverb angehängt.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="5ea5f-139">Klicken Sie im Bereich **Inspector** für **das**Vierfache auf **Komponente hinzufügen** , und fügen Sie das Raumeffekt-Skript auf **Sende Ebene** hinzu:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-139">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![Skript für Sende Ebene hinzufügen](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="5ea5f-141">Es sei denn, Sie aktivieren das Feature " **Sende Ebene für raumeffekte** " des **Microsoft spatializer** -Plug-ins, es sendet keine Audiodaten an die Unity-Audioengine zur Auswirkung der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="5ea5f-142">Die Bereichs Effekt-Komponente der **Sende Ebene** enthält ein Graph-Steuerelement, mit dem die Audioebene festgelegt wird, die für die Verarbeitung von Reverb an die Unity-Audioengine</span><span class="sxs-lookup"><span data-stu-id="5ea5f-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="5ea5f-143">Klicken und ziehen Sie die Kurve nach unten, um die Ebene auf ungefähr-30dB festzulegen:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![Hall Kurve anpassen](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="5ea5f-145">Entfernen Sie dann die Auskommentierung der vier kommentierten Zeilen im **spatializeonoff** -Skript.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="5ea5f-146">Das Skript sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-146">The script will now look like this:</span></span>
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="5ea5f-147">Durch das Auskommentieren dieser Zeilen werden dem **inspektorbereich** für das Skript zwei Eigenschaften hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="5ea5f-148">Um diese festzulegen, legen Sie im Bereich **Inspector** der Komponente **spatialize on off** des **Quad**:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="5ea5f-149">Legen Sie die Eigenschaft " **Raumeffekt** " auf Ihre neue Platz Effekt-mischkeitsgruppe fest.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="5ea5f-150">Festlegen der **Master Group** -Eigenschaft auf die Master-Mixer-Gruppe</span><span class="sxs-lookup"><span data-stu-id="5ea5f-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="5ea5f-151">Nachdem diese Änderungen vorgenommen wurden, sieht die Eigenschaft **spatialize on off** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5ea5f-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatialize on off (erweitert)](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="5ea5f-153">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="5ea5f-153">Next steps</span></span>

<span data-ttu-id="5ea5f-154">Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="5ea5f-155">Wenn Sie nun die Schaltfläche in der APP zum Aktivieren der Spatialisierung berühren, leitet das Skript die Audiodatei an die Raumeffekt Gruppe weiter, um den Code hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="5ea5f-156">Beim Wechsel zu Stereo wird das Audiomaterial an die Master Gruppe weitergeleitet, und es wird vermieden, dass das Hinzufügen von Reverb erfolgt.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="5ea5f-157">Sie haben die Lernprogramme "hololens 2 Spatial audiotutorial" für Unity abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="5ea5f-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="5ea5f-158">Gratulation!</span><span class="sxs-lookup"><span data-stu-id="5ea5f-158">Congratulations!</span></span>


