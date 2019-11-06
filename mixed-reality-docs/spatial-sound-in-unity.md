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
# <a name="spatial-sound-in-unity"></a>Räumlicher Sound in Unity

Auf dieser Seite finden Sie Links zu Ressourcen, die Ihnen bei der Verwendung und dem Entwurf von Microsoft HRTF spatializer in ihren Unity Mixed Reality-Projekten helfen.

## <a name="enable-spatialization"></a>Spatialization aktivieren

Aktivieren Sie den " **MS HRTF spatializer** " in den Audioeinstellungen Ihres Projekts. Weitere Informationen finden Sie in [der Dokumentation zum spatializer von Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html). 

Fügen Sie eine **Audioquelle** an ein Objekt in der Hierarchie an, und aktivieren Sie die Verräumlichung, indem Sie das Kontrollkästchen **spatialization aktivieren aktivieren** und den Schieberegler **räumlicher Blend** auf ' 1 ' verschieben. Weitere Informationen finden Sie in [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html). 

## <a name="design-with-spatialization"></a>Entwerfen mit spatialization

### <a name="distance-based-attenuation"></a>Entfernungs basierte Dämpfung
Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf. Dies funktioniert möglicherweise für Ihr Szenario, oder Sie finden die Quellen zu schnell oder zu langsam. Weitere Informationen zum Festlegen dieser Kurven in Unity finden Sie [unter Sound Design in gemischter Realität](spatial-sound-design.md) für empfohlene Einstellungen für Entfernungs [verlaufkurven](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) .

### <a name="environment"></a>Umgebung
Der **spatializer von MS HRTF** enthält eine Raum-Reverb-Komponente mit [vier Reverb-Einstellungen](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) und dem Standardwert "Small". Die Raum Einstellung kann für jede Audioquelle Programm gesteuert geändert werden, indem das folgende C# Skript an jedes Objekt in Unity angehängt wird, das über eine räumliche Audioquelle verfügt:

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

## <a name="unity-spatial-sound-examples"></a>Beispiele für räumliche Unity-Sounds
Das Mixed Reality Toolkit (mrtk) enthält Beispiele für Möglichkeiten zum Anwenden von Audioeffekten in gemischter Realität: [mrtk-Demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).

