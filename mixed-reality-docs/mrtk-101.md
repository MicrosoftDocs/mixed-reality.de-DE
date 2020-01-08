---
title: 'Mrtk 101-Gewusst wie: Verwenden von Mixed Reality Toolkit Unity für grundlegende Interaktionen (hololens 2, hololens, Windows Mixed Reality, Open VR)'
description: Verwenden von Mixed Reality Toolkit Unity für grundlegende Interaktionen (hololens 2, hololens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: Hololens, mrtk, Mixed Reality Toolkit, Windows Mixed Reality, Design, Beispiel-APP, Steuerelemente
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623500"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>Mrtk 101: Verwenden von Mixed Reality Toolkit Unity für grundlegende Interaktionen (hololens 2, hololens, Windows Mixed Reality, Open VR)

![Mrtk](images/MRTK101/MRTK101Cover.png)

Erfahren Sie, wie Sie mrtk verwenden können, um einige der am häufigsten verwendeten Interaktionsmuster in gemischter Realität zu erzielen.

- Simulieren von Eingabe Interaktionen im Unity-Editor
- Wie kann man ein Objekt erfassen und verschieben?
- Wie wird die Größe eines Objekts geändert?
- Verschieben oder Drehen eines Objekts mit präziser Genauigkeit
- Wie wird ein Objekt auf Eingabeereignisse reagieren?
- Vorgehensweise beim Hinzufügen von visuellem Feedback
- Vorgehensweise beim Hinzufügen von Audiofeedback
- Verwendung von hololens 2-Schaltflächen für Stilvorlagen
- Wie wird ein Objekt befolgt?
- Wie wird ein Objekt Ihnen angezeigt?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Simulieren von Eingabe Interaktionen im Unity-Editor
Mrtk unterstützt die Eingabe Simulation im Editor. Führen Sie einfach die Szene durch Klicken auf die Wiedergabe Schaltfläche Unity aus. Verwenden Sie diese Schlüssel, um Eingaben zu simulieren.
Drücken Sie die Taste W, A, S, D, um die Kamera zu verschieben.
Halten Sie die Rechte Maustaste gedrückt, und bewegen Sie die Maus, um sich umzusehen.
Um die simulierten Hände anzuzeigen, drücken Sie die Leertaste (Rechte Seite) oder die linke Umschalttaste (linke Seite), um simulierte Hände in der Ansicht beizubehalten, drücken Sie die Taste T oder Y, um simulierte Hände zu drehen, und drücken Sie Q oder E (horizontal)/R oder F (vertikal).

- [Weitere Informationen zur Eingabe Simulation finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Wie kann man ein Objekt erfassen und verschieben?
Wenn Sie ein Objekt abgleichen möchten, weisen Sie diese beiden Skripts zu: ManipulationHandler.cs und nearinteraktiongrabbable. cs (für Direct Send mit der Eingabe von Handgelenk Nachverfolgung), unterstützt manipulationhandler sowohl near-als auch weite Interaktionen. Sie können ein Objekt mit der Hand nach Verfolgungs Eingabe (in der Nähe), dem Hand Strahl (weit), dem Strahl des Bewegungs Controllers (weit), dem Blick & Cursor des hololens 2 (in der Nähe), dem Hand Strahl (Far

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>Wie wird die Größe eines Objekts geändert?
ManipulationHandler.cs unterstützt zweistufige Skalierung/Drehung. Dies funktioniert mit verschiedenen Eingabetypen, wie z. b. der Hand Eingabe von hololens 2, der Eingabe von hololens 1 und der EINGABETASTE und der Eingabe des Bewegungs Controllers von Windows Mixed Reality.

- [Weitere Informationen zum Manipulations Handler finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Verschieben oder Drehen eines Objekts mit präziser Genauigkeit
Weisen Sie einem Objekt BoundingBox.cs zu, um das umgebende Feld zu verwenden, das die Schnittstelle zum Skalieren und Drehen eines Objekts ist. In der Standardeinstellung werden hololens 1 Style Blue Handles und Drähte angezeigt. Zum Verwenden von hololens 2-Stil-near-basierten animierten Handles müssen Sie Prefabs und Material zuweisen. Ausführliche Informationen zur Konfiguration finden Sie in der Dokumentation zum umgebenden [Feld](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) und in der boundingboxexamples. unity-Szene.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Weitere Informationen zum umgebenden Feld finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Wie wird ein Objekt auf Eingabeereignisse reagieren?
Weisen Sie einem Objekt PointerHandler.cs zu. Im Inspektor können Sie die Ereignisse onpointerdown (), onpointerup (), onpointergeklickt () und onpointerdrag () verwenden, um diese Ereignisse in einem Skript zu verwenden, implementieren Sie imixedrealitypointerhandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Weitere Informationen zum Eingabe System finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Vorgehensweise beim Hinzufügen von visuellem Feedback
Weisen Sie einem Objekt Interactable.cs zu. Erstellen Sie im Inspektor ein neues Design. Mithilfe der designprofile von interactable können Sie allen verfügbaren Eingabe Interaktions Zuständen problemlos visuelles Feedback hinzufügen.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable bietet verschiedene Arten von Themen, einschließlich des Shader-Designs, mit dem Sie die Eigenschaften des Shaders pro Interaktions Zustand steuern können.

- [Weitere Informationen zu interactable finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Ein weiterer wichtiger Baustein für visuelles Feedback ist der mrtk-Standard-Shader. Mit dem mrtk-Standard-Shader können Sie problemlos visuelle Feedback Effekte hinzufügen, wie z. b. Hover Light und Near Light. Da der mrtk-Standard-Shader eine deutlich geringere Berechnung als der Unity-standardshader durchführt, können Sie ein leistungsfähiges Verhalten erzielen.

Erstellen Sie ein neues Material, und wählen Sie den Shader ' Mixed Reality Toolkit > Standard ' aus. Oder Sie können eines der vorhandenen Materialien auswählen, das den mrtk-Standard-Shader verwendet.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Weitere Informationen zum mrtk-Standard-Shader finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Vorgehensweise beim Hinzufügen von Audiofeedback
Fügen Sie audiosource einem Objekt hinzu. Weisen Sie dann in den Skripts, die Eingabeereignisse verfügbar machen (z. b. Interactable.cs oder PointerHandler.cs) das Objekt dem-Ereignis zu, und wählen Sie audiosource. playoneshot () aus. Sie können Ihre Audioclips verwenden oder eines aus den audioassets von mrtk auswählen.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>Verwendung von hololens 2-Schaltflächen für Stilvorlagen
Mrtk bietet verschiedene Typen von hololens 2-shellschaltflächen (OS). Es bietet anspruchsvolle visuelle Feedback, wie z. b. near Light, Compress Box und einen Ripple-Effekt auf der Schaltflächen Oberfläche.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Per Drag & Drop können Sie einfach eine der vorfab auf der Schaltfläche hololens 2-Stil in ihre Szene ziehen. Die vorfab verwendet Interactable.cs, das oben vorgestellt wurde. Sie können verfügbar gemachte Ereignisse wie z. b. "OnClick ()" in der interactable verwenden, um Aktionen auszumachen.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Weitere Informationen zu Schaltflächen-Prefabs finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>Wie wird ein Objekt befolgt?
Zuweisen eines RadialView.cs-Skripts zu einem Objekt. Er ist Teil der Solver-Skript Reihe, mit der Sie verschiedene Arten der Objekt Positionierung in 3D-Raum erreichen können. SolverHandler.cs wird automatisch hinzugefügt.
Im folgenden finden Sie ein Beispiel für eine radialview-Konfiguration, um das "Lazy follow"-tagparallel Verhalten zu erreichen, wie das Startmenü in der hololens-Shell. Sie können die minimale/maximale Entfernung und die minimale/maximale Anzeige Grad angeben. Im folgenden Beispiel wird gezeigt, wie das Objekt zwischen 0,4 m und 0,8 m Bereich in 15 ° positioniert wird. Passen Sie Lerp-Zeit Werte an, um das Positions Update schneller oder langsamer zu gestalten.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Weitere Informationen zu Solvers finden Sie in der mrtk-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>Wie wird ein Objekt Ihnen angezeigt?
Zuweisen eines Billboard.cs-Skripts zu einem Objekt. Sie wird unabhängig von ihrer Position immer mit Ihnen konfrontiert. Sie können die Option Pivot-Achse angeben.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Sind Sie bereit, beeindruckende Umgebungen für gemischte Realität zu schaffen? Besuchen Sie die nachfolgenden Seiten, und erfahren Sie mehr über mrtk und gemischte Realität.

## <a name="about-the-author"></a>Über die Autorin

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong-Yoon-Park</b><br>UX-Designer-@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Weitere Informationen:

* [Mixed Reality Toolkit-Unity (mrtk) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Ersten Schritte mit mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Holotoolkit zu mrtk Porting-Richtlinie](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
