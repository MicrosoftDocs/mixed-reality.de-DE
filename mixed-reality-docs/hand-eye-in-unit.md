---
title: Hand-und Augen Nachverfolgung in Unity
description: Es gibt zwei wichtige Möglichkeiten, um ihre Blicke in Unity, Handgesten und Bewegungs Controllern zu übernehmen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe
ms.openlocfilehash: b60c5567714893f2d1f2cc929e832bb851dd9e34
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203323"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Hand-und Augen Nachverfolgung in Unity

Hololens 2 hat einige neue interessante Funktionen eingeführt: die Hand-und die Augen Nachverfolgung.

Die einfachste Möglichkeit, die neue Funktion in Unity zu nutzen, ist die Verwendung von mrtk v2. Es gibt auch einige Beispiel Szenen, die Ihnen den Einstieg erleichtern. 

* [Einstieg in die Hand in mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Einstieg in die Eye-Nachverfolgung in mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Bausteine, die Hände, Augen und andere in mrtk v2 unterstützen

Mrtk v2 bietet eine Reihe von UI-Steuerelementen und-Blöcken, die Ihnen helfen, ihre Entwicklung zu beschleunigen. 

|  [![Schaltfläche](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [Schaltfläche](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [![Begrenzungsrahmen](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [Begrenzungsrahmen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [![Bearbeitungshandler](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [Bearbeitungshandler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich HoloLens2's-Hand | Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum | Skript für die Bearbeitung von Objekten mit einem oder zwei Händen |
|  [![Slate](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) - [Slate](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | Tastatur des [System Tastatur](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [Systems](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html)![ | [![](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) interactable- [Tabelle](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| 2D-Stilebene, die den Bildlauf mit der Hand Eingabe unterstützt | Beispielskript für die Verwendung der System Tastatur in Unity  | Ein Skript für die Interaktion von Objekten mit visuellen Zuständen und Designunterstützung |
|  [![Solver](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) - [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [![Objektsammlung](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [Objektsammlung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [![QuickInfo](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [QuickInfo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Verschiedene objektpositionierungsverhaltensweisen, z. b. Tag-entlang, Text Sperre, Konstante Ansichts Größe und Oberflächenstruktur | Skript für das Layout eines Arrays von Objekten in einer dreidimensionalen Form | Benutzeroberfläche der Anmerkung mit flexiblem Anker/pivotsystem, das zum bezeichnen von Bewegungs Controllern und Objekten verwendet werden kann. |
|  [![App-Leiste](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [App-Leiste](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![Zeiger](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) [Zeiger](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | [![Fingertip-Visualisierung](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [Fingertip-Visualisierung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Die Benutzeroberfläche für die manuelle Aktivierung des umgebenden Felds. | Weitere Informationen zu verschiedenen Zeiger Typen | Visuelles Element auf der fingerinfo, das das Vertrauen für die direkte Interaktion verbessert |
|  [![Eye-Nachverfolgung: Ziel](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) Auswahl Eye-nach [Verfolgung: Zielauswahl](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![Eye Tracking:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) Navigation im Navigationsbereich [: Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![Eye Tracking: Heat Map](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [Eye Tracking: Heat Map](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Kombinieren Sie Augen, Stimme und Hand Eingaben, um schnell und einfach holograms in Ihrer Szene auszuwählen. | Erfahren Sie, wie Sie den Text automatisch Scrollen oder basierend auf dem, was Sie sich ansehen, Inhalte mit Fokus vergrößern.| Beispiele für das Protokollieren, laden und visualisieren, was Benutzer in Ihrer APP betrachtet haben |

## <a name="example-scenes"></a>Beispiel Szenen
Erkunden Sie die verschiedenen Arten von Interaktionen und UI-Steuerelementen von mrtk in [dieser Beispiel Szene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Weitere Beispiel Szenen finden Sie im [Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) unter **Assets/mixedrealitytoolkit. examples/Demos**Folder.

[![Beispiel Szene](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>Weitere Informationen

* [Augenbasierte Interaktion] (eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2] (eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Motion-Controller](motion-controllers.md)
* [Unityengine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [Unityengine. XR. inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
