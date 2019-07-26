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
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="84ff5-104">Ersten Schritte mit mrtk v2</span><span class="sxs-lookup"><span data-stu-id="84ff5-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="84ff5-105">Leitfaden zu den ersten Schritten mit mrtk</span><span class="sxs-lookup"><span data-stu-id="84ff5-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="84ff5-106">Informationen zu den ersten Schritten mit mrtk v2 finden Sie im Leitfaden zu den ersten Schritten mit [mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) .</span><span class="sxs-lookup"><span data-stu-id="84ff5-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="84ff5-107">Was ist Mixed Reality Toolkit (mrtk)?</span><span class="sxs-lookup"><span data-stu-id="84ff5-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="84ff5-108">Das mrtk ist ein fantastisches Open Source-Toolkit, das seit der ersten Veröffentlichung der hololens verfügbar ist, und wäre nicht an der Stelle, an der es sich heute befindet, ohne die harte Arbeit unserer Entwickler Community, die dazu beigetragen hat.</span><span class="sxs-lookup"><span data-stu-id="84ff5-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="84ff5-109">In den letzten drei Jahren haben wir uns mit dem Feedback unserer Entwickler Community beschäftigt und mrtk v2 erstellt, um die größten Bedenken zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="84ff5-110">Die mrtk v2 mit Unity ist ein plattformübergreifendes Open Source-Entwicklungs-Kit für gemischte Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="84ff5-111">Mrtk Version 2 soll die Entwicklung von Anwendungen beschleunigen, die auf Microsoft hololens-, Windows Mixed Reality-und openvr-Plattform abzielen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="84ff5-112">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community zu leisten, während dieser Bereich weiter wächst.</span><span class="sxs-lookup"><span data-stu-id="84ff5-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="84ff5-113">Weitere Informationen finden Sie im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .</span><span class="sxs-lookup"><span data-stu-id="84ff5-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="84ff5-114">Funktionsbereiche</span><span class="sxs-lookup"><span data-stu-id="84ff5-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Eingabe System" width="105"> <span data-ttu-id="84ff5-116">Eingabe System</span><span class="sxs-lookup"><span data-stu-id="84ff5-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Hand Nachverfolgung (hololens 2)" width="105"> <span data-ttu-id="84ff5-118">Hand Nachverfolgung (hololens 2)</span><span class="sxs-lookup"><span data-stu-id="84ff5-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Eye Tracking (hololens 2)" width="105">
    <span data-ttu-id="84ff5-120">Eye Tracking (hololens 2)</span><span class="sxs-lookup"><span data-stu-id="84ff5-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Sprachbefehl" width="105"> <span data-ttu-id="84ff5-122">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="84ff5-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Blick und Auswahl (hololens (1. Gen))" width="105">
    <span data-ttu-id="84ff5-124">Blick und Auswahl (hololens (1. Gen))</span><span class="sxs-lookup"><span data-stu-id="84ff5-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportierung" width="105"> <span data-ttu-id="84ff5-126">Teleportierung</span><span class="sxs-lookup"><span data-stu-id="84ff5-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI-Steuerelemente" width="105"> <span data-ttu-id="84ff5-128">UI-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="84ff5-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver und Interaktionen" width="105"> <span data-ttu-id="84ff5-130">Solver und Interaktionen</span><span class="sxs-lookup"><span data-stu-id="84ff5-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Controller Visualisierung" width="105"> <span data-ttu-id="84ff5-132">Controller Visualisierung</span><span class="sxs-lookup"><span data-stu-id="84ff5-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Räumliche Kenntnisse" width="105"> <span data-ttu-id="84ff5-134">Räumliche Kenntnisse</span><span class="sxs-lookup"><span data-stu-id="84ff5-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Diagnose Tool" width="105"> <span data-ttu-id="84ff5-136">Diagnose Tool</span><span class="sxs-lookup"><span data-stu-id="84ff5-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Mrtk-Standard-Shader" width="105"> <span data-ttu-id="84ff5-138">Mrtk-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="84ff5-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="84ff5-139">Bausteine der Benutzeroberfläche und Interaktion</span><span class="sxs-lookup"><span data-stu-id="84ff5-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Schaltfläche" width="250"><br>
    <span data-ttu-id="84ff5-141">**Button** (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="84ff5-141">**Button**</span></span><br>
    <span data-ttu-id="84ff5-142">Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich der Bindestriche von hololens 2<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Begrenzungs Fenster" width="250"><br>
    <span data-ttu-id="84ff5-144">**Begrenzungs Fenster**</span><span class="sxs-lookup"><span data-stu-id="84ff5-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="84ff5-145">Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulations Handler" width="250"><br>
    <span data-ttu-id="84ff5-147">**Manipulations Handler**</span><span class="sxs-lookup"><span data-stu-id="84ff5-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="84ff5-148">Skript für die Bearbeitung von Objekten mit einem oder zwei Händen<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Tafel" width="250"><br>
    <span data-ttu-id="84ff5-150">**Tafel**</span><span class="sxs-lookup"><span data-stu-id="84ff5-150">**Slate**</span></span> <br>
    <span data-ttu-id="84ff5-151">2D-Stilebene, die den Bildlauf mit der Hand Eingabe unterstützt<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="System Tastatur" width="250"><br>
    <span data-ttu-id="84ff5-153">**System Tastatur**</span><span class="sxs-lookup"><span data-stu-id="84ff5-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="84ff5-154">Beispielskript für die Verwendung der System Tastatur in Unity<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interaktionen" width="250"><br>
     <span data-ttu-id="84ff5-156">**Interaktionen**</span><span class="sxs-lookup"><span data-stu-id="84ff5-156">**Interactable**</span></span> <br>
     <span data-ttu-id="84ff5-157">Ein Skript für die Interaktion von Objekten mit visuellen Zuständen und Designunterstützung<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    <span data-ttu-id="84ff5-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="84ff5-159">**Solver**</span></span> <br>
    <span data-ttu-id="84ff5-160">Verschiedene objektpositionierungsverhaltensweisen, z. b. Tag-entlang, Text Sperre, Konstante Ansichts Größe und Oberflächenstruktur<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Objektsammlung" width="250"><br>
    <span data-ttu-id="84ff5-162">**Objektsammlung**</span><span class="sxs-lookup"><span data-stu-id="84ff5-162">**Object Collection**</span></span><br>
    <span data-ttu-id="84ff5-163">Skript für das Layout eines Arrays von Objekten in einer dreidimensionalen Form<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="QuickInfo" width="250">  <br>
    <span data-ttu-id="84ff5-165">**QuickInfo**</span><span class="sxs-lookup"><span data-stu-id="84ff5-165">**Tooltip**</span></span><br>
    <span data-ttu-id="84ff5-166">Benutzeroberfläche der Anmerkung mit flexiblem Anker/pivotsystem, das zum bezeichnen von Bewegungs Controllern und Objekten verwendet werden kann<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="App-Leiste" width="250"><br>
    <span data-ttu-id="84ff5-168">**App-Leiste**</span><span class="sxs-lookup"><span data-stu-id="84ff5-168">**App Bar**</span></span><br>
    <span data-ttu-id="84ff5-169">Die Benutzeroberfläche für die manuelle Aktivierung des umgebenden Felds.<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Zeiger" width="250"><br>
    <span data-ttu-id="84ff5-171">**Zeiger**</span><span class="sxs-lookup"><span data-stu-id="84ff5-171">**Pointers**</span></span><br>
    <span data-ttu-id="84ff5-172">Weitere Informationen zu verschiedenen Zeiger Typen<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Fingertip-Visualisierung" width="250"><br>
     <span data-ttu-id="84ff5-174">**Fingertip-Visualisierung**</span><span class="sxs-lookup"><span data-stu-id="84ff5-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="84ff5-175">Visuelles Element auf der fingerinfo, das das Vertrauen für die direkte Interaktion verbessert<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="84ff5-177">**Schieberegler**</span><span class="sxs-lookup"><span data-stu-id="84ff5-177">**Slider**</span></span><br>
    <span data-ttu-id="84ff5-178">Schieberegler-Benutzeroberfläche zum Anpassen von Werten zur Unterstützung der direkt Hand<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Mrtk-Standard-Shader" width="250"><br>
    <span data-ttu-id="84ff5-180">**Mrtk-Standard-Shader**</span><span class="sxs-lookup"><span data-stu-id="84ff5-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="84ff5-181">Der Standard-Shader von mrtk unterstützt verschiedene fließende Designelemente mit Leistung.<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Hand Gelenk" width="250"><br>
     <span data-ttu-id="84ff5-183">**Hand Gelenk**</span><span class="sxs-lookup"><span data-stu-id="84ff5-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="84ff5-184">Veranschaulicht, wie Solver verwendet wird, um Objekte an die Handgelenke anzufügen.<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Augen Verfolgung: Zielauswahl" width="250"><br>
    <span data-ttu-id="84ff5-186">**Augen Verfolgung: Zielauswahl**</span><span class="sxs-lookup"><span data-stu-id="84ff5-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="84ff5-187">Kombinieren Sie Augen, Stimme und Hand Eingaben, um schnell und einfach holograms in Ihrer Szene auszuwählen.<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Augen Verfolgung: Navigation" width="250"><br>
    <span data-ttu-id="84ff5-189">**Augen Verfolgung: Navig**</span><span class="sxs-lookup"><span data-stu-id="84ff5-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="84ff5-190">Erfahren Sie, wie Sie den Text automatisch Scrollen oder basierend auf dem, was Sie sich ansehen, Inhalte mit Fokus vergrößern.<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Augen Verfolgung: Wärmebild" width="250"><br>
    <span data-ttu-id="84ff5-192">**Augen Verfolgung: Wärmebild**</span><span class="sxs-lookup"><span data-stu-id="84ff5-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="84ff5-193">Beispiele für das Protokollieren, laden und visualisieren, was Benutzer in Ihrer APP betrachtet haben<a/></span><span class="sxs-lookup"><span data-stu-id="84ff5-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="84ff5-194">Mindestanforderung für mrtk v2</span><span class="sxs-lookup"><span data-stu-id="84ff5-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="84ff5-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="84ff5-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="84ff5-196">Microsoft Visual Studio 2017 oder höher</span><span class="sxs-lookup"><span data-stu-id="84ff5-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="84ff5-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="84ff5-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="84ff5-198">Windows 10 1803 oder höher</span><span class="sxs-lookup"><span data-stu-id="84ff5-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="84ff5-199">Neu mit mrtk v2</span><span class="sxs-lookup"><span data-stu-id="84ff5-199">New with MRTK v2</span></span>
<span data-ttu-id="84ff5-200">Wir möchten unsere Verpflichtung zu diesen Platt Form Tools betonen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="84ff5-201">Tatsächlich haben wir mrtk Version 2 genutzt, um unsere Posteingangs Umgebung zu entwickeln, wie z. b. das Setup Erlebnis (OOBE) und unsere gemischte Reality Learning-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="84ff5-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="84ff5-202">Sie können auch erwarten, dass neue hololens 2-Funktionen zuerst über mrtk verfügbar gemacht werden, da wir der Meinung sind, dass es sich um die beste Methode zum entwickeln auf unserer Plattform handelt.</span><span class="sxs-lookup"><span data-stu-id="84ff5-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="84ff5-203">Bau</span><span class="sxs-lookup"><span data-stu-id="84ff5-203">Modular</span></span>
<span data-ttu-id="84ff5-204">Wir haben Sie auf modulare Weise erstellt, sodass Sie nicht jedes Bit des Toolkits in Ihr Projekt aufnehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="84ff5-205">Dies hat tatsächlich einige Vorteile.</span><span class="sxs-lookup"><span data-stu-id="84ff5-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="84ff5-206">Dadurch wird die Projektgröße kleiner, und die Verwaltung wird vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="84ff5-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="84ff5-207">Darüber hinaus können Sie, da es mit Skript fähigen Objekten erstellt wurde und Schnittstellen gesteuert ist, auch die Komponenten ersetzen, die in Ihrem eigenen enthalten sind, um andere Dienste, Systeme und Plattformen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="84ff5-208">Plattformübergreifend</span><span class="sxs-lookup"><span data-stu-id="84ff5-208">Cross-platform</span></span>
<span data-ttu-id="84ff5-209">Bei anderen Plattformen wird eine plattformübergreifende Unterstützung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84ff5-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="84ff5-210">Obwohl dies nicht bedeutet, dass nicht jede einzelne Plattform standardmäßig unterstützt wird, haben wir sichergestellt, dass kein Toolkit-Code unterbricht, wenn Sie das Buildziel auf andere Plattformen umstellen.</span><span class="sxs-lookup"><span data-stu-id="84ff5-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="84ff5-211">Die Stabilität und Erweiterbarkeit des modularen Entwurfs richtet sich an einen guten Weg, um mehrere Plattformen zu unterstützen, wie z. b. Arcore, Arkit und openvr.</span><span class="sxs-lookup"><span data-stu-id="84ff5-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="84ff5-212">Leistungsfähigen</span><span class="sxs-lookup"><span data-stu-id="84ff5-212">Performant</span></span>
<span data-ttu-id="84ff5-213">Beim Arbeiten mit mobilen Plattformen wurde die Leistung mit der Leistung im Hinterkopf aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="84ff5-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="84ff5-214">Dies ist äußerst wichtig, und wir wollten sicherstellen, dass die Tools nicht für Sie geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="84ff5-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="84ff5-215">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="84ff5-215">See also</span></span>
* [<span data-ttu-id="84ff5-216">Leitfaden zu den ersten Schritten mit mrtk</span><span class="sxs-lookup"><span data-stu-id="84ff5-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="84ff5-217">Mrtk-Dokumentation Home</span><span class="sxs-lookup"><span data-stu-id="84ff5-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="84ff5-218">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="84ff5-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="84ff5-219">Portieren von HTK/mrtk zu mrtk Version 2</span><span class="sxs-lookup"><span data-stu-id="84ff5-219">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
