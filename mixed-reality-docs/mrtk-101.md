---
title: 'MRTK-Einführung: Verwenden des Mixed Reality-Toolkits Unity für grundlegende Interaktionen (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)'
description: Verwenden des Mixed Reality-Toolkits Unity für grundlegende Interaktionen (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality-Toolkit, Windows Mixed Reality, Entwurf, Beispiel-App, Steuerelemente
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028313"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK-Einführung Verwenden des Mixed Reality-Toolkits Unity für grundlegende Interaktionen (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

Erfahren Sie, wie Sie das MRTK nutzen, um einige der am häufigsten verwendeten Interaktionsmuster in Mixed Reality umzusetzen.

- Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?
- Wie lässt sich ein Objekt greifen und bewegen?
- Wie wird die Größe eines Objekts geändert?
- Wie lässt sich ein Objekt präzise bewegen oder drehen?
- Wie lässt man ein Objekt auf Eingabeereignisse reagieren?
- Wie wird visuelles Feedback implementiert?
- Wie kann Audiofeedback hinzugefügt werden?
- Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?
- Wie lässt man sich von einem Objekt folgen?
- Wie erreicht man, dass ein Objekt sich einem zuwendet?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?
MRTK unterstützt die Simulation von Eingaben im Editor. Führen Sie die Szene einfach durch Klicken auf die Wiedergabe Schaltfläche in Unity aus. Verwenden der Tasten zum Simulieren von Eingaben.
Drücken Sie die Tasten W, A, S, D, um die Kamera zu bewegen.
Halten Sie die rechte Maustaste gedrückt, und bewegen Sie die Maus, um sich umzusehen.
Um die simulierten Hände anzuzeigen, drücken Sie die LEERTASTE (rechte Hand) oder die linke UMSCHALTTASTE (linke Hand). Um die simulierten Hände ständig anzuzeigen, drücken Sie die T- oder die Y-Taste. Um die simulierten Hände zu drehen, drücken Sie Q oder E (horizontal) bzw. R oder F (vertikal).

- [Weitere Informationen zur Eingabesimulation finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Wie lässt sich ein Objekt greifen und bewegen?
Um ein Objekt greifbar zu machen, weisen Sie diese beiden Skripts zu: „ManipulationHandler.cs“ und „NearInteractionGrabbable.cs“ (für direktes Greifen mit Eingabe durch artikuliertes Hand-Tracking). ManipulationHandler unterstützt sowohl Nah- als auch Fern-Interaktionen. Sie können ein Objekt durch die Eingabe mittels artikuliertem Hand-Tracking (nah), Handstrahl (fern), den Strahl des Motion Controllers (fern), den Anvisier-Cursor von HoloLens und Tippen in die Luft (fern) greifen und bewegen.

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>Wie wird die Größe eines Objekts geändert?
ManipulationHandler.cs unterstützt die beidhändige Skalierung/Drehung. Dies funktioniert mit verschiedenen Eingabetypen, wie z. B. der Handeingabe von HoloLens 2, der Eingabe durch Anvisieren und Gesten von HoloLens 1 und der Motion Controller-Eingabe des immersiven Headsets für Windows Mixed Reality.

- [Weitere Informationen zum Manipulation Handler finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Wie lässt sich ein Objekt präzise bewegen oder drehen?
Weisen Sie einem Objekt BoundingBox.cs zu, um Begrenzungsrahmen zu verwenden, die die Oberfläche zum Skalieren und Drehen von Objekten darstellen. Standardmäßig werden blaue Ziehpunkte und Drahtlinien im Stil von HoloLens 1 angezeigt. Um näherungsbasierte animierte Ziehpunkte im HoloLens 2-Stil zu verwenden, müssen Sie Prefabs und Materialien zuweisen. Informationen zu den Konfigurationsdetails finden Sie in der [Bounding Box-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) und der BoundingBoxExamples.unity-Szene.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Weitere Informationen zu Bounding Box finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Wie lässt man ein Objekt auf Eingabeereignisse reagieren?
Weisen Sie einem Objekt PointerHandler.cs zu. Im Inspektor können Sie die Ereignisse OnPointerDown (), OnPointerUp (), OnPointerClicked () und OnPointerDragged () verwenden. Um diese Ereignisse in einem Skript zu verwenden, implementieren Sie IMixedRealityPointerHandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Weitere Informationen zum Eingabesystem finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Wie wird visuelles Feedback implementiert?
Zuweisen von Interactable.cs zu einem Objekt. Erstellen Sie im Inspektor ein neues Design. Mithilfe der Designprofile von Interactable können Sie allen verfügbaren Interaktionszuständen auf einfache Weise visuelles Feedback hinzufügen.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable stellt verschiedene Arten von Designs zur Verfügung, einschließlich des Shader-Designs, mit dem Sie die Eigenschaften des Shaders pro Interaktionszustand steuern können.

- [Weitere Informationen zu Interactable finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Ein weiterer wichtiger Baustein für visuelles Feedback ist der MRTK-Standardshader. Mit dem MRTK-Standardshader können Sie auf einfache Weise visuelle Feedbackeffekte hinzufügen, wie das Licht beim Draufzeigen und Näherungslicht. Da der MRTK-Standardshader erheblich weniger Berechnungen als der Unity-Standardshader ausführt, können Sie ein leistungsstarkes Verhalten erreichen.

Erstellen Sie ein neues Material, und wählen Sie den Shader „Mixed Reality Toolkit > Standard“ aus. Alternativ können Sie eins der vorhandenen Materialien auswählen, die den MRTK-Standardshader verwenden.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Weitere Informationen zum MRTK-Standardshader finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Wie kann Audiofeedback hinzugefügt werden?
Fügen Sie einem Objekt AudioSource hinzu. Weisen Sie dann in den Skripts, die Eingabeereignisse verfügbar machen (z. B. Interactable.cs oder PointerHandler.cs) das Objekt dem Ereignis zu, und wählen Sie AudioSource.PlayOneShot() aus. Sie können eigene Audioclips verwenden oder einen aus den Audioressourcen des MRTK auswählen.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?
MRTK bietet verschiedene Typen von Schaltflächen im Stil der HoloLens 2-Shell (Betriebssystem). Es stehen raffinierte visuelle Feedbacks wie etwa Näherungslicht, ein gestauchtes Feld und ein Kräuseleffekt auf der Schaltflächenoberfläche zur Verfügung.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Legen Sie einfach eins der Prefabs für eine drückbare Schaltfläche im HoloLens 2-Stil per Drag & Drop in Ihrer Szene ab. Das Prefab verwendet Interactable.cs, die oben vorgestellt wurde. Sie können in Interactable verfügbar gemachte Ereignisse wie OnClick() verwenden, um Aktionen auszulösen.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Weitere Informationen zu Schaltflächen-Prefabs finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>Wie lässt man sich von einem Objekt folgen?
Weisen Sie einem Objekt das RadialView.cs-Skript zu. Es ist Teil der Solver-Reihe von Skripts, die Ihnen verschiedene Arten von Objektpositionierung im 3D-Raum ermöglichen. SolverHandler.cs wird automatisch hinzugefügt.
Unten finden Sie ein Beispiel der RadialView-Konfiguration, um ein „Hinterhertrotten“-Folgeverhalten zu erreichen, ähnlich wie das Startmenü in der HoloLens-Shell. Sie können die minimale/maximale Entfernung und den minimalen/maximalen Ansichtswinkel angeben. Im Beispiel unten ist die Positionierung des Objekts zwischen 0,4 m und 0,8 m in einem Bereich von 15 ° dargestellt. Passen Sie die Werte für die Lerp-Zeit an, um das Aktualisieren der Position schneller oder langsamer erfolgen zu lassen.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Weitere Informationen zu Solvern finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>Wie erreicht man, dass ein Objekt sich einem zuwendet?
Weisen Sie einem Objekt das Billboard.cs-Skript zu. Das Objekt wendet sich Ihnen dann immer zu, unabhängig von Ihrer Position. Sie können die Pivotachsenoption angeben.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Sind Sie bereit, beeindruckende Erlebnisse für Mixed Reality zu gestalten? Besuchen Sie die unten angegebenen Seiten, und erfahren Sie mehr über MRTK und Mixed Reality.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong-Yoon-Park</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Erste Schritte mit MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Portierungsrichtlinie HoloToolkit zu MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
