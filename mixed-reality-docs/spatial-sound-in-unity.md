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
# <a name="spatial-sound-in-unity"></a>Räumlicher Sound in Unity

In diesem Thema wird beschrieben, wie räumlicher Sound in ihren Unity-Projekten verwendet wird. Dabei werden die erforderlichen Plug-in-Dateien sowie die Unity-Komponenten und-Eigenschaften behandelt, die räumliche Sounds ermöglichen.

## <a name="enabling-spatial-sound-in-unity"></a>Aktivieren von räumlichem Sound in Unity

Räumlicher Sound wird in Unity mithilfe eines audiospatializer-Plug-ins aktiviert. Die Plug-in-Dateien werden direkt in Unity gebündelt, sodass das Aktivieren von räumlichem Sound so einfach ist wie das **Bearbeiten > Projekteinstellungen > Audio** und das Ändern des **spatializer-Plug** -ins im Inspektor in den " **MS HRTF spatializer**". Da Microsoft spatializer derzeit nur 48000Hz unterstützt, sollten Sie die System Stichproben Rate auch auf 48000 festlegen, um einen HRTF-Fehler zu vermeiden, wenn das System Ausgabegerät nicht bereits auf 48000 festgelegt ist:

![Inspektor für Audiomanager](images/audio-250px.png)<br>
*Inspektor für Audiomanager*

Ihr Unity-Projekt ist nun so konfiguriert, dass räumliche Töne verwendet werden.

>[!NOTE]
>Wenn Sie keinen Windows 10-PC für die Entwicklung verwenden, erhalten Sie keinen räumlichen Ton im Editor und nicht auf dem Gerät (auch wenn Sie das Windows 10 SDK verwenden).

## <a name="using-spatial-sound-in-unity"></a>Verwenden von räumlichem Sound in Unity

Räumlicher Sound wird in Ihrem Unity-Projekt verwendet, indem drei Einstellungen in den audioquellkomponenten angepasst werden. Mit den folgenden Schritten werden die audioquellkomponenten für räumliche Audiodaten konfiguriert.
* Wählen Sie im Bereich **Hierarchie** das Spielobjekt aus, das über eine angefügte **Audioquelle**verfügt.
* Im **Inspektor** -Panel unter der Komponente **Audioquelle**
    * Aktivieren Sie die Option **spatialize** .
    * Legen Sie **räumliche Blend** auf **3D** (numerischer Wert 1) fest.
    * Um optimale Ergebnisse zu erzielen, erweitern Sie **3D Sound Settings** , und legen Sie **volumerrolloff** auf **benutzerdefiniertes Rolloff**fest

![Inspektor-Panel in Unity, das die Audioquelle anzeigt](images/audiosource.png)<br>
*Inspektor-Panel in Unity, das die Audioquelle anzeigt*

Ihre Sounds sind nun realistisch in der Umgebung des Projekts vorhanden!

Es wird dringend empfohlen, sich mit den [räumlichen Entwurfs Richtlinien](spatial-sound-design.md)vertraut zu machen. Diese Richtlinien tragen dazu bei, ihre Audioinhalte nahtlos in Ihr Projekt zu integrieren und Ihre Benutzer in die von Ihnen erstellte Benutzererlebnis zu vertiefen.

## <a name="setting-spatial-sound-settings"></a>Festlegen räumlicher Sound Einstellungen

Das Microsoft Spatial Sound Plugin bietet einen zusätzlichen Parameter, der pro Audioquelle festgelegt werden kann, um eine zusätzliche Steuerung der Audiosimulation zu ermöglichen. Dieser Parameter ist die Größe des simulierten Raums.

### <a name="room-size"></a>Raum Größe

Die Größe des Raums, der durch räumlichen Ton simuliert wird. Die ungefähren Größen der Räume sind: klein (ein Büro in einem kleinen Konferenzraum), Mittel (ein großer Konferenzraum) und groß (ein Auditorium). Sie können auch eine Raum Größe von keine angeben, um eine Umgebung im Außenbereich zu simulieren. Die Standard Raum Größe ist klein.

### <a name="example"></a>Beispiel

Das mixedrealitytoolkit für Unity stellt eine statische Klasse bereit, die das Festlegen der räumlichen Sound Einstellungen vereinfacht. Diese Klasse befindet sich im [Ordner mixedrealitytoolkit\spatialsound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) und kann von jedem Skript in Ihrem Projekt aufgerufen werden. Es wird empfohlen, diese Parameter für jede audioquellkomponente im Projekt festzulegen. Das folgende Beispiel zeigt, wie die mittlere Raum Größe für eine angefügte Audioquelle ausgewählt wird.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Direkter Zugriff auf Parameter aus Unity

Wenn Sie die ausgezeichneten Audiotools im mixedrealitytoolkit nicht verwenden möchten, finden Sie hier Informationen zum Ändern von HRTF-Parametern. Sie können diese Datei in ein Skript mit dem Namen *SetHRTF.cs* kopieren bzw. einfügen, das Sie an jede HRTF audiosource anfügen möchten. Damit können Sie die Parameter ändern, die für HRTF wichtig sind.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Räumlicher Sound im Mixed Reality Toolkit
- [HoloToolkit-examples/spatialsound/Szenen/uaudiomanagertest. unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Die folgenden Beispiele aus dem Mixed Reality Toolkit sind allgemeine Beispiele für Audioeffekte, die veranschaulichen, wie Sie Ihre Erfahrungen mit Sound rekursiv gestalten können.
- [HoloToolkit-examples/spatialsound/Szenen/audiolometest. unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-examples/spatialsound/Szenen/audiookoksiontest. unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Siehe auch
* [Raumklang](spatial-sound.md)
* [Raumklangentwurf](spatial-sound-design.md)
