---
title: Räumlicher Sound in Unity
description: Wiedergabe von räumlichem Sound von einem bestimmten 3D-Punkt in der Unity-Szene.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Ton, HRTF, Raum Größe
ms.openlocfilehash: 6720eac30c69ebfcd0f003cf131f60295818d676
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553698"
---
# <a name="spatial-sound-in-unity"></a>Räumlicher Sound in Unity

Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.

## <a name="spatializer-options"></a>Spatializer-Optionen
Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:
* *MS HRTF spatializer*. Unity stellt dies als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.
  * Dies erfolgt auf CPU in einer kostengünstigeren "Single Source"-Architektur.
  * Dies wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.
* Der *Microsoft spatializer*. Dies ist im [GitHub-Repository von Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)verfügbar.
  * Hierfür wird eine kostengünstigere Architektur mit mehreren Quellen verwendet.
  * Auf hololens 2 wird dies in einen Hardwarebeschleuniger verlagert.

Für neue Anwendungen wird *Microsoft spatializer*empfohlen.

## <a name="enable-spatialization"></a>Spatialization aktivieren

Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus. Dann:
* Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie
* Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .
* Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".
* Stellen Sie sicher, dass auf Ihrer Entwickler Arbeitsstation räumliche Audiodaten aktiviert sind Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volumesymbol klicken und sicherstellen, dass räumlicher Sound auf einen anderen Wert als "Off" gesetzt ist. Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **Windows Sonic für Kopfhörer aus**.

Weitere Details findest du unter:
* [Microsoft spatializer-GitHub-Repository](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft-Tutorial zu spatializer](unity-spatial-audio-ch1.md)
* [Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Dokumentation zu spatializer von Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Entfernungs basierte Dämpfung
Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf. Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden. Weitere Details findest du unter:
* [Sound Design in gemischter Realität](spatial-sound-design.md) für empfohlene Einstellungen.
* In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.

## <a name="reverb"></a>Hall
Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig. So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:
* Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.
* Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.

Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](unity-spatial-audio-ch5.md) .

## <a name="unity-spatial-sound-examples"></a>Beispiele für räumliche Unity-Sounds
Beispiele für räumliche Sounds in Unity finden Sie unter:
* [Mrtk-Demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>Nächste Schritte
* [Sound Design in gemischter Realität](spatial-sound-design.md)
* [Microsoft-Tutorial zu spatializer](unity-spatial-audio-ch1.md)

