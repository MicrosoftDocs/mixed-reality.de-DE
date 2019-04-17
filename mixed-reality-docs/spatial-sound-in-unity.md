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
# <a name="spatial-sound-in-unity"></a>Räumliche Sound in Unity

Dieses Thema beschreibt, wie Sie räumliche Sound in Ihre Unity-Projekte zu verwenden. Hierin sind die erforderlichen-Plug-in-Dateien als auch die Unity-Komponenten und die Eigenschaften, die räumliche Sound zu aktivieren.

## <a name="enabling-spatial-sound-in-unity"></a>Aktivieren von räumlichen Sound in Unity

Räumliche Sound, in Unity ist eine audio Spatializer Plug-in aktiviert. Die Plug-in-Dateien werden direkt in Unity gebündelt, also aktivieren räumliche Sound so einfach wie das möchte **Bearbeiten > Projekteinstellungen > Audio** und Ändern der **Spatializer-Plug-Ins** im Inspektor auf den  **MS HRTF Spatializer**. Da der Microsoft-Spatializer nur 48000 Hz derzeit unterstützt, sollten Sie auch Ihr System Samplingrate festlegen, um 48000, um Fehler HRTF, in dem seltenen Fall zu verhindern, dass Ihr Systemgerät nicht bereits auf 48000 festgelegt ist:

![Inspektor für AudioManager](images/audio-250px.png)<br>
*Inspektor für AudioManager*

Ihr Unity-Projekt ist jetzt konfiguriert, um räumliche Sound zu verwenden.

>[!NOTE]
>Wenn Sie ein Windows 10-PCs für die Entwicklung nicht verwenden, wird nicht räumlich Sound im Editor noch auf dem Gerät erhalten Sie (selbst wenn Sie das Windows 10-SDK verwenden).

## <a name="using-spatial-sound-in-unity"></a>Verwenden von räumlichen Sound in Unity

Räumliche Sound wird in Ihrem Unity-Projekt verwendet, durch Anpassen der drei Einstellungen für die Audio Source-Komponenten. Die folgenden Schritte aus, werden Ihre Audio Source-Komponenten für räumliche Sound konfiguriert.
* In der **Hierarchie** wählen das spielobjekt, die eine angefügte **Audio Source**.
* In der **Inspektor** Bereich unter der **Audio Source** Komponente
    * Überprüfen Sie die **Spatialize** Option.
    * Legen Sie **räumliche Blend** zu **3D** (numerischen Wert 1).
    * Erweitern Sie für optimale Ergebnisse **3D Sound Einstellungen** und legen Sie **Volume Rolloff** zu **benutzerdefinierte Rolloff**.

![Inspector-Bereich, in die Audio-Quelle mit Unity](images/audiosource.png)<br>
*Inspector-Bereich, in die Audio-Quelle mit Unity*

Ihre Sounds werden jetzt innerhalb der Umgebung des Projekts realistisch betrachtet sind!

Es wird dringend empfohlen, dass Sie sich mit vertraut der [räumlich Sound-Entwurfsrichtlinien](spatial-sound-design.md). Diese Richtlinien unterstützen, Ihre Audio-nahtlos in Ihr Projekt integrieren und weiteren Benutzern in der Umgebung tauchen, die Sie erstellt haben.

## <a name="setting-spatial-sound-settings"></a>Einrichtung von räumlichen Sound

Der Microsoft Spatial Sound-Plug-in bietet einen zusätzlichen Parameter, die auf festlegen werden kann, eine pro-Audio Source-Basis, um zusätzliche Kontrolle über die audio Simulation zu ermöglichen. Dieser Parameter ist die Größe des simulierten Raums.

### <a name="room-size"></a>Der Größe

Die Größe der Raum, der durch räumliche Sound simuliert werden wird. Die ungefähre Größe der Räume sind. klein (einem Büro auf einem kleinen Konferenzraum), Mittel (einen großen Konferenzraum) "und" large (ein Hörsaal). Sie können auch eine Größe ' None ' zum Simulieren einer outdoor-Umgebung angeben. Die Standardgröße des Raums ist klein.

### <a name="example"></a>Beispiel

Die MixedRealityToolkit für Unity bietet es sich um eine statische Klasse, mit der Einrichtung der räumlich Sound einfach. Diese Klasse finden Sie in der [MixedRealityToolkit\SpatialSound Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) und von einem Skript in Ihrem Projekt aufgerufen werden kann. Es wird empfohlen, dass Sie diese Parameter für jede Audio Source-Komponente in Ihr Projekt festlegen. Das folgende Beispiel zeigt die mittlere Größe für eine angefügte Audio-Datenquelle auswählen.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Direktes Zugreifen auf Parameter von Unity

Wenn Sie nicht die ausgezeichnete Audio-Tools in der MixedRealityToolkit verwenden möchten, sieht aus wie Sie HRTF-Parameter ändern würde. Sie können kopieren und Einfügen dieser in ein Skript namens *SetHRTF.cs* , die Sie an jedem HRTF AudioSource anfügen möchten. Sie können Parameter, die wichtige zum HRTF zu ändern.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Räumliche Sound in Mixed Reality-Toolkit
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Die folgenden Beispiele aus dem Mixed Reality-Toolkit sind allgemeine Audioeffekt-Beispiele, die Möglichkeiten, um Ihre Erfahrungen seine machen, indem Sie mit der Sound zu veranschaulichen.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Siehe auch
* [Räumliche sound](spatial-sound.md)
* [Räumliche Entwurf](spatial-sound-design.md)
