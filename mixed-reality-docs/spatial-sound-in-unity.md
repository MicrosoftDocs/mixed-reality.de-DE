---
title: Räumlicher Sound in Unity
description: Wiedergabe von räumlichem Sound, der von einem bestimmten 3D-Punkt in der Unity-Szene stammt.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Ton, HRTF, Raum Größe
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641076"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="19112-104">Räumlicher Sound in Unity</span><span class="sxs-lookup"><span data-stu-id="19112-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="19112-105">Auf dieser Seite finden Sie Links zu Ressourcen, die Ihnen bei der Verwendung und dem Entwurf von Microsoft HRTF spatializer in ihren Unity Mixed Reality-Projekten helfen.</span><span class="sxs-lookup"><span data-stu-id="19112-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="19112-106">Spatialization aktivieren</span><span class="sxs-lookup"><span data-stu-id="19112-106">Enable spatialization</span></span>

<span data-ttu-id="19112-107">Aktivieren Sie den " **MS HRTF spatializer** " in den Audioeinstellungen Ihres Projekts.</span><span class="sxs-lookup"><span data-stu-id="19112-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="19112-108">Weitere Informationen finden Sie in [der Dokumentation zum spatializer von Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span><span class="sxs-lookup"><span data-stu-id="19112-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="19112-109">Fügen Sie eine **Audioquelle** an ein Objekt in der Hierarchie an, und aktivieren Sie die Verräumlichung, indem Sie das Kontrollkästchen **spatialization aktivieren aktivieren** und den Schieberegler **räumlicher Blend** auf ' 1 ' verschieben.</span><span class="sxs-lookup"><span data-stu-id="19112-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="19112-110">Weitere Informationen finden Sie in [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span><span class="sxs-lookup"><span data-stu-id="19112-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="19112-111">Entwerfen mit spatialization</span><span class="sxs-lookup"><span data-stu-id="19112-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="19112-112">Entfernungs basierte Dämpfung</span><span class="sxs-lookup"><span data-stu-id="19112-112">Distance-based attenuation</span></span>
<span data-ttu-id="19112-113">Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf.</span><span class="sxs-lookup"><span data-stu-id="19112-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="19112-114">Dies funktioniert möglicherweise für Ihr Szenario, oder Sie finden die Quellen zu schnell oder zu langsam.</span><span class="sxs-lookup"><span data-stu-id="19112-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="19112-115">Weitere Informationen zum Festlegen dieser Kurven in Unity finden Sie [unter Sound Design in gemischter Realität](spatial-sound-design.md) für empfohlene Einstellungen für Entfernungs [verlaufkurven](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) .</span><span class="sxs-lookup"><span data-stu-id="19112-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="19112-116">Umgebung</span><span class="sxs-lookup"><span data-stu-id="19112-116">Environment</span></span>
<span data-ttu-id="19112-117">Der **spatializer von MS HRTF** enthält eine Raum-Reverb-Komponente mit [vier Reverb-Einstellungen](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) und dem Standardwert "Small".</span><span class="sxs-lookup"><span data-stu-id="19112-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="19112-118">Die Raum Einstellung kann für jede Audioquelle Programm gesteuert geändert werden, indem das folgende C# Skript an jedes Objekt in Unity angehängt wird, das über eine räumliche Audioquelle verfügt:</span><span class="sxs-lookup"><span data-stu-id="19112-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="19112-119">Beispiele für räumliche Unity-Sounds</span><span class="sxs-lookup"><span data-stu-id="19112-119">Unity spatial sound examples</span></span>
<span data-ttu-id="19112-120">Das Mixed Reality Toolkit (mrtk) enthält Beispiele für Möglichkeiten zum Anwenden von Audioeffekten in gemischter Realität: [mrtk-Demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span><span class="sxs-lookup"><span data-stu-id="19112-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

