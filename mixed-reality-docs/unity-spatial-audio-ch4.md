---
title: 'Lernprogramme für räumliche Audiodaten: 4. Aktivieren und deaktivieren räumlicher Audiodaten zur Laufzeit'
description: Verwenden Sie eine Schaltfläche, um die Spatialisierung von Audiodaten zur Laufzeit zu aktivieren und zu deaktivieren.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182867"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="a3ef1-105">Aktivieren und Deaktivieren der Spatialisierung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="a3ef1-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="a3ef1-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="a3ef1-106">Objectives</span></span>
<span data-ttu-id="a3ef1-107">In diesem vierten Kapitel gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="a3ef1-108">Hinzufügen eines neuen Skripts zum Steuern der Spatialisierung eines Spiel Objekts</span><span class="sxs-lookup"><span data-stu-id="a3ef1-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="a3ef1-109">Das spatialization-Steuerelement Skript aus Schaltflächen Aktionen Steuern</span><span class="sxs-lookup"><span data-stu-id="a3ef1-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="a3ef1-110">Spatialization-Steuerelement Skript hinzufügen</span><span class="sxs-lookup"><span data-stu-id="a3ef1-110">Add spatialization control script</span></span>
<span data-ttu-id="a3ef1-111">Klicken Sie mit der rechten Maustaste in den Bereich **Projekt** , C# und erstellen Sie ein neues Skript, indem Sie  **C# > Skript erstellen**auswählen.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="a3ef1-112">Benennen Sie Ihr Skript mit dem Namen "spatializeonoff".</span><span class="sxs-lookup"><span data-stu-id="a3ef1-112">Name your script "SpatializeOnOff".</span></span>

![Erstellen des Skripts](images/spatial-audio/create-script.png)

<span data-ttu-id="a3ef1-114">Doppelklicken Sie im **Projekt** Bereich auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="a3ef1-115">Ersetzen Sie die Standardskript Inhalte durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="a3ef1-116">Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden in [Kapitel 5](unity-spatial-audio-ch5.md)auskommentiert.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="a3ef1-117">Zum Aktivieren oder Deaktivieren der Spatialisierung passt das Skript nur die **spatialblend** -Eigenschaft an, sodass die **spatialization** -Eigenschaft aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="a3ef1-118">In diesem Modus wendet Unity weiterhin die **volumekurve** an.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="a3ef1-119">Wenn der Benutzer die räumungszeit bei weitem von der Quelle deaktivieren würde, würde er das Volume plötzlich anwachsen.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="a3ef1-120">Wenn Sie die spatialization vollständig deaktivieren möchten, ändern Sie das Skript so, dass auch die Eigenschaft **spatialization** booleschen der **SourceObject** -Variablen angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="a3ef1-121">Fügen Sie das Skript an, und Steuern Sie es über die Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a3ef1-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="a3ef1-122">Klicken Sie im Bereich **Inspector** des **Quad**auf **Komponente hinzufügen** , und fügen Sie das Skript **spatialize on off** hinzu:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Skript zu Quad hinzufügen](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="a3ef1-124">Auf der Komponente **spatialize on off** des **Quad**:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="a3ef1-125">Suchen Sie das untergeordnete Element " **PressableButtonHoloLens2-> iconandtext-> textmeschpro** " in der **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="a3ef1-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subobject in the **Hierarchy**</span></span>
2. <span data-ttu-id="a3ef1-126">Ziehen Sie das **texttmeschpro** -suboject auf das Feld **buttontextobject** der Komponente **spatialize on off** .</span><span class="sxs-lookup"><span data-stu-id="a3ef1-126">Drag the **TextMeshPro** suboject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="a3ef1-127">Nachdem diese Änderungen vorgenommen wurden, sieht die **spatialize on off** -Komponente des **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Räumliche](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="a3ef1-129">Um die Schaltfläche so festzulegen, dass das Skript **spatialize on off** aufgerufen wird, wenn die Schaltfläche losgelassen wird, öffnen Sie den **Inspektor** -Bereich des **PressableButtonHoloLens2** -Objekts, suchen Sie die **interactable** -Komponente und:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="a3ef1-130">Suchen Sie den **OnClick ()** -Bereich des Unterabschnitts " **Ereignisse** ".</span><span class="sxs-lookup"><span data-stu-id="a3ef1-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="a3ef1-131">Ziehen Sie den **Quad** aus der- **Hierarchie** in den Zielobjekt Slot.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="a3ef1-132">Wählen Sie im Dropdown Feld Aktion die Option **spatializeonoff. tauapspatialization** aus.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="a3ef1-133">Nachdem diese Änderungen vorgenommen wurden, sieht die **interactable** -Komponente wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a3ef1-133">After these changes, the **Interactable** component will look like this:</span></span>

![Schaltflächen Aktions Einstellungen](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="a3ef1-135">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="a3ef1-135">Next steps</span></span>
<span data-ttu-id="a3ef1-136">Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="a3ef1-137">In der App können Sie nun auf die Schaltfläche klicken, um die Spatialisierung im Video zu aktivieren und zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="a3ef1-138">Wenn Sie im Unity-Editor testen, drücken Sie die Leertaste, und Scrollen Sie mit dem Mausrad, um die Hand Simulation zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

<span data-ttu-id="a3ef1-139">Fahren Sie mit [Kapitel 5](unity-spatial-audio-ch5.md) fort, um Soundquellen mithilfe von "Hall" den erkannten Abstand hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3ef1-139">Continue on to [Chapter 5](unity-spatial-audio-ch5.md) to add perceived distance to sound sources using reverb.</span></span>

