---
title: Ersten Schritte mit mrtk Version 2
description: Für neue Entwickler, die an der Nutzung von mrtk interessiert sind
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, Test, Mixed Reality Toolkit, mrtk Version 2, mrtk, Tools, SDK, hololens, hololens 2
ms.openlocfilehash: 7eded2c766765a5ccebf741eed2f8b7fe8f65a93
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507928"
---
# <a name="getting-started-with-mrtk-v2"></a>Ersten Schritte mit mrtk v2

## <a name="mrtk-getting-started-guide"></a>Leitfaden zu den ersten Schritten mit mrtk
Informationen zu den ersten Schritten mit mrtk v2 finden Sie im Leitfaden zu den ersten Schritten mit [mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) .

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Was ist Mixed Reality Toolkit (mrtk)?
Das mrtk ist ein fantastisches Open Source-Toolkit, das seit der ersten Veröffentlichung der hololens verfügbar ist, und wäre nicht an der Stelle, an der es sich heute befindet, ohne die harte Arbeit unserer Entwickler Community, die dazu beigetragen hat. In den letzten drei Jahren haben wir uns mit dem Feedback unserer Entwickler Community beschäftigt und mrtk v2 erstellt, um die größten Bedenken zu berücksichtigen.  

Die mrtk v2 mit Unity ist ein plattformübergreifendes Open Source-Entwicklungs-Kit für gemischte Reality-Anwendungen.  Mrtk Version 2 soll die Entwicklung von Anwendungen beschleunigen, die auf Microsoft hololens-, Windows Mixed Reality-und openvr-Plattform abzielen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community zu leisten, während dieser Bereich weiter wächst. 


Weitere Informationen finden Sie im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .

## <a name="feature-areas"></a>Funktionsbereiche

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Eingabe System" width="105"> Eingabe System 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Hand Nachverfolgung (hololens 2)" width="105"> Hand Nachverfolgung (hololens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Eye Tracking (hololens 2)" width="105">
    Eye Tracking (hololens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Sprachbefehl" width="105"> Sprachbefehl
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Blick und Auswahl (hololens (1. Gen))" width="105">
    Blick und Auswahl (hololens (1. Gen))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportierung" width="105"> Teleportierung
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI-Steuerelemente" width="105"> UI-Steuerelemente
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver und Interaktionen" width="105"> Solver und Interaktionen
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Controller Visualisierung" width="105"> Controller Visualisierung
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Räumliche Kenntnisse" width="105"> Räumliche Kenntnisse
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Diagnose Tool" width="105"> Diagnose Tool
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Mrtk-Standard-Shader" width="105"> Mrtk-Standard-Shader
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Bausteine der Benutzeroberfläche und Interaktion

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Schaltfläche" width="250"><br>
    **Button** (Schaltfläche)<br>
    Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich der Bindestriche von hololens 2<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Begrenzungs Fenster" width="250"><br>
    **Begrenzungs Fenster**<br>
    Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulations Handler" width="250"><br>
    **Manipulations Handler**<br>
    Skript für die Bearbeitung von Objekten mit einem oder zwei Händen<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Tafel" width="250"><br>
    **Tafel** <br>
    2D-Stilebene, die den Bildlauf mit der Hand Eingabe unterstützt<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="System Tastatur" width="250"><br>
    **System Tastatur**<br>
    Beispielskript für die Verwendung der System Tastatur in Unity<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interaktionen" width="250"><br>
     **Interaktionen** <br>
     Ein Skript für die Interaktion von Objekten mit visuellen Zuständen und Designunterstützung<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    **Solver** <br>
    Verschiedene objektpositionierungsverhaltensweisen, z. b. Tag-entlang, Text Sperre, Konstante Ansichts Größe und Oberflächenstruktur<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Objektsammlung" width="250"><br>
    **Objektsammlung**<br>
    Skript für das Layout eines Arrays von Objekten in einer dreidimensionalen Form<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="QuickInfo" width="250">  <br>
    **QuickInfo**<br>
    Benutzeroberfläche der Anmerkung mit flexiblem Anker/pivotsystem, das zum bezeichnen von Bewegungs Controllern und Objekten verwendet werden kann<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="App-Leiste" width="250"><br>
    **App-Leiste**<br>
    Die Benutzeroberfläche für die manuelle Aktivierung des umgebenden Felds.<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Zeiger" width="250"><br>
    **Zeiger**<br>
    Weitere Informationen zu verschiedenen Zeiger Typen<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Fingertip-Visualisierung" width="250"><br>
     **Fingertip-Visualisierung**<br>
     Visuelles Element auf der fingerinfo, das das Vertrauen für die direkte Interaktion verbessert<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Schieberegler**<br>
    Schieberegler-Benutzeroberfläche zum Anpassen von Werten zur Unterstützung der direkt Hand<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Mrtk-Standard-Shader" width="250"><br>
    **Mrtk-Standard-Shader**<br>
    Der Standard-Shader von mrtk unterstützt verschiedene fließende Designelemente mit Leistung.<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Hand Gelenk" width="250"><br>
     **Hand Gelenk**<br>
     Veranschaulicht, wie Solver verwendet wird, um Objekte an die Handgelenke anzufügen.<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Augen Verfolgung: Zielauswahl" width="250"><br>
    **Augen Verfolgung: Zielauswahl**<br>
    Kombinieren Sie Augen, Stimme und Hand Eingaben, um schnell und einfach holograms in Ihrer Szene auszuwählen.<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Augen Verfolgung: Navigation" width="250"><br>
    **Augen Verfolgung: Navig**<br>
    Erfahren Sie, wie Sie den Text automatisch Scrollen oder basierend auf dem, was Sie sich ansehen, Inhalte mit Fokus vergrößern.<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Augen Verfolgung: Wärmebild" width="250"><br>
    **Augen Verfolgung: Wärmebild**<br>
    Beispiele für das Protokollieren, laden und visualisieren, was Benutzer in Ihrer APP betrachtet haben<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Mindestanforderung für mrtk v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 oder höher
* Windows SDK 18362 + 
* Windows 10 1803 oder höher

## <a name="new-with-mrtk-v2"></a>Neu mit mrtk v2
Wir möchten unsere Verpflichtung zu diesen Platt Form Tools betonen.  Tatsächlich haben wir mrtk Version 2 genutzt, um unsere Posteingangs Umgebung zu entwickeln, wie z. b. das Setup Erlebnis (OOBE) und unsere gemischte Reality Learning-Anwendung.  Sie können auch erwarten, dass neue hololens 2-Funktionen zuerst über mrtk verfügbar gemacht werden, da wir der Meinung sind, dass es sich um die beste Methode zum entwickeln auf unserer Plattform handelt. 

### <a name="modular"></a>Bau
Wir haben Sie auf modulare Weise erstellt, sodass Sie nicht jedes Bit des Toolkits in Ihr Projekt aufnehmen müssen.  Dies hat tatsächlich einige Vorteile.  Dadurch wird die Projektgröße kleiner, und die Verwaltung wird vereinfacht.  Darüber hinaus können Sie, da es mit Skript fähigen Objekten erstellt wurde und Schnittstellen gesteuert ist, auch die Komponenten ersetzen, die in Ihrem eigenen enthalten sind, um andere Dienste, Systeme und Plattformen zu unterstützen.


### <a name="cross-platform"></a>Plattformübergreifend
Bei anderen Plattformen wird eine plattformübergreifende Unterstützung unterstützt.  Obwohl dies nicht bedeutet, dass nicht jede einzelne Plattform standardmäßig unterstützt wird, haben wir sichergestellt, dass kein Toolkit-Code unterbricht, wenn Sie das Buildziel auf andere Plattformen umstellen.  Die Stabilität und Erweiterbarkeit des modularen Entwurfs richtet sich an einen guten Weg, um mehrere Plattformen zu unterstützen, wie z. b. Arcore, Arkit und openvr.


### <a name="performant"></a>Leistungsfähigen
Beim Arbeiten mit mobilen Plattformen wurde die Leistung mit der Leistung im Hinterkopf aufgebaut.  Dies ist äußerst wichtig, und wir wollten sicherstellen, dass die Tools nicht für Sie geeignet sind.


## <a name="see-also"></a>Siehe auch
* [Leitfaden zu den ersten Schritten mit mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Mrtk-Dokumentation Home](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Installieren der Tools](install-the-tools.md)
* [Portieren von HTK/mrtk zu mrtk Version 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
