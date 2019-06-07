---
title: Erste Schritte mit MRTK Version 2
description: Für angehende Entwickler interessieren, die bei der Nutzung von MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, zu testen, Mixed Reality-Toolkit, MRTK Version 2, MRTK, Tools, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750365"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="4ad4b-104">Erste Schritte mit MRTK v2</span><span class="sxs-lookup"><span data-stu-id="4ad4b-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="4ad4b-105">MRTK – erste Schritte</span><span class="sxs-lookup"><span data-stu-id="4ad4b-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="4ad4b-106">Finden Sie unter den [MRTK – erste Schritte](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) Informationen zu den ersten Schritten mit MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="4ad4b-107">Was ist Mixed Reality-Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="4ad4b-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="4ad4b-108">Die MRTK ist eine tolle open-Source-Toolkit, das schon seit den HoloLens zuerst veröffentlicht wurde und nicht, wo es heute ist ohne den Aufwand für unsere Entwickler-Community, die darauf beigetragen haben.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="4ad4b-109">Über den letzten drei Jahren haben wir datenkanalports, auf das Feedback auf unsere Entwickler-Community und erstellt MRTK v2, um die wichtigsten Aspekte zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="4ad4b-110">Der MRTK v2 mit Unity ist ein open-Source-Cross-Platform Development-Kit für mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="4ad4b-111">MRTK Version 2 beschleunigen der Entwicklung von Anwendungen für Microsoft HoloLens, Faszinierende Windows Mixed Reality (VR)-Headsets und OpenVR-Plattform dient.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="4ad4b-112">Das Projekt zielt auf die Reduzierung von Sperren auf einen Eintrag in mixed Reality-Anwendungen zu erstellen und an der Community beitragen, wenn wir alle wachsen.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="4ad4b-113">Finden Sie unter den [MRTK dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) um mehr zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="4ad4b-114">Funktionsbereiche</span><span class="sxs-lookup"><span data-stu-id="4ad4b-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Eingabesystem" width="105"> <span data-ttu-id="4ad4b-116">Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="4ad4b-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Übergeben von nachverfolgung (HoloLens 2)" width="105"> <span data-ttu-id="4ad4b-118">Übergeben von nachverfolgung (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4ad4b-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Eye-Tracking (HoloLens 2)" width="105">
    <span data-ttu-id="4ad4b-120">Eye-Tracking (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4ad4b-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Voice-Befehle" width="105"> <span data-ttu-id="4ad4b-122">Voice-Befehle</span><span class="sxs-lookup"><span data-stu-id="4ad4b-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Bestaunen + auswählen (HoloLens (1. Generation))" width="105">
    <span data-ttu-id="4ad4b-124">Bestaunen + auswählen (HoloLens (1. Generation))</span><span class="sxs-lookup"><span data-stu-id="4ad4b-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="4ad4b-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="4ad4b-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI-Steuerelemente" width="105"> <span data-ttu-id="4ad4b-128">UI-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="4ad4b-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver und Interaktionen" width="105"> <span data-ttu-id="4ad4b-130">Solver und Interaktionen</span><span class="sxs-lookup"><span data-stu-id="4ad4b-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Controller-Visualisierung" width="105"> <span data-ttu-id="4ad4b-132">Controller-Visualisierung</span><span class="sxs-lookup"><span data-stu-id="4ad4b-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Räumliche verstehen" width="105"> <span data-ttu-id="4ad4b-134">Räumliche verstehen</span><span class="sxs-lookup"><span data-stu-id="4ad4b-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Diagnosetools" width="105"> <span data-ttu-id="4ad4b-136">Diagnosetools</span><span class="sxs-lookup"><span data-stu-id="4ad4b-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK Standard-Shader" width="105"> <span data-ttu-id="4ad4b-138">MRTK Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="4ad4b-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="4ad4b-139">Benutzeroberfläche und Interaktion Erstellen von Blöcken</span><span class="sxs-lookup"><span data-stu-id="4ad4b-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Schaltfläche" width="250"><br>
    <span data-ttu-id="4ad4b-141">**Button** (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="4ad4b-141">**Button**</span></span><br>
    <span data-ttu-id="4ad4b-142">Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden, einschließlich HoloLens 2 angezeigte Seite unterstützt <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Umgebendes Feld" width="250"><br>
    <span data-ttu-id="4ad4b-144">**Umgebendes Feld**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="4ad4b-145">Standard-Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulation-Handler" width="250"><br>
    <span data-ttu-id="4ad4b-147">**Manipulation-Handler**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="4ad4b-148">Skript zum Bearbeiten von Objekten mit einem oder zwei Hand <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate-Objekt" width="250"><br>
    <span data-ttu-id="4ad4b-150">**Slate-Objekt**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-150">**Slate**</span></span> <br>
    <span data-ttu-id="4ad4b-151">2D Style-Ebene unterstützt, Durchführen eines Bildlaufs mit angezeigte Seite Eingabe <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Systemtastatur" width="250"><br>
    <span data-ttu-id="4ad4b-153">**Systemtastatur**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="4ad4b-154">Beispiel:-Skript, der über die Systemtastatur in Unity <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Es" width="250"><br>
     <span data-ttu-id="4ad4b-156">**Es**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-156">**Interactable**</span></span> <br>
     <span data-ttu-id="4ad4b-157">Ein Skript für die Objekte stellen, die es mit visuellen Zuständen und Unterstützung von Designs <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    <span data-ttu-id="4ad4b-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-159">**Solver**</span></span> <br>
    <span data-ttu-id="4ad4b-160">Verschiedene Objekt Positionierung Verhaltensweisen wie Tag-along "," Text-Lock "," Größe der Konstanten Ansicht "und" Surface Magnetismus <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Eine Objektauflistung" width="250"><br>
    <span data-ttu-id="4ad4b-162">**Eine Objektauflistung**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-162">**Object Collection**</span></span><br>
    <span data-ttu-id="4ad4b-163">Skript für Lay out ein Array von Objekten in einer dreidimensionalen Form <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="QuickInfo" width="250">  <br>
    <span data-ttu-id="4ad4b-165">**Tooltip**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-165">**Tooltip**</span></span><br>
    <span data-ttu-id="4ad4b-166">UI-Anmerkung mit flexiblen Anker/Pivot-System, das verwendet werden kann, für die Bezeichnung der Motion-Controllern und Objekt <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="App-Leiste" width="250"><br>
    <span data-ttu-id="4ad4b-168">**App-Leiste**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-168">**App Bar**</span></span><br>
    <span data-ttu-id="4ad4b-169">Benutzeroberfläche für die manuelle Aktivierung umgebende Feld <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Zeiger" width="250"><br>
    <span data-ttu-id="4ad4b-171">**Zeiger**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-171">**Pointers**</span></span><br>
    <span data-ttu-id="4ad4b-172">Erfahren Sie mehr über die verschiedenen Typen von Zeigern <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Fingertippen-Visualisierung" width="250"><br>
     <span data-ttu-id="4ad4b-174">**Fingertippen-Visualisierung**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="4ad4b-175">Visuelle Unterstützung für die fingertippen die verbessert die Zuverlässigkeit für die direkte Interaktion <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="4ad4b-177">**Schieberegler**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-177">**Slider**</span></span><br>
    <span data-ttu-id="4ad4b-178">Schieberegler-Benutzeroberfläche für die Anpassung Werte unterstützen direkte manuell Nachverfolgen der Aktivität <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK Standard-Shader" width="250"><br>
    <span data-ttu-id="4ad4b-180">**MRTK Standard-Shader**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="4ad4b-181">MRTK des Standard-Shader unterstützt verschiedene Fluent Designelemente mit der Leistung <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Gemeinsame Chaser manuell" width="250"><br>
     <span data-ttu-id="4ad4b-183">**Gemeinsame Chaser manuell**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="4ad4b-184">Veranschaulicht, wie Solver zum Anfügen von Objekten auf der Hand joints <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Eye-Tracking: Ziel-Auswahl" width="250"><br>
    <span data-ttu-id="4ad4b-186">**Eye-Tracking: Ziel-Auswahl**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="4ad4b-187">Kombinieren von Augen, Sprach- und manuell eingeben, schnell und mühelos in Ihre Szene Hologramme auswählen <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Eye-Tracking: Navigation" width="250"><br>
    <span data-ttu-id="4ad4b-189">**Eye-Tracking: Navigation**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="4ad4b-190">Erfahren Sie, wie automatisch eines Bildlaufs im Text "oder" nahtlos in gezielter Inhalte basierend auf der dabei am zoom <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Eye-Tracking: Wärmebild" width="250"><br>
    <span data-ttu-id="4ad4b-192">**Eye-Tracking: Wärmebild**</span><span class="sxs-lookup"><span data-stu-id="4ad4b-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="4ad4b-193">Beispiele für die Protokollierung haben laden und Visualisieren von welchen Benutzern in Ihrer app ansehen <a/></span><span class="sxs-lookup"><span data-stu-id="4ad4b-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="4ad4b-194">Die Mindestanforderung für MRTK v2</span><span class="sxs-lookup"><span data-stu-id="4ad4b-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="4ad4b-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="4ad4b-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="4ad4b-196">Microsoft Visual Studio 2017 oder höher</span><span class="sxs-lookup"><span data-stu-id="4ad4b-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="4ad4b-197">Windows SDK 18362+</span><span class="sxs-lookup"><span data-stu-id="4ad4b-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="4ad4b-198">Windows 10-Version 1803 oder höher</span><span class="sxs-lookup"><span data-stu-id="4ad4b-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="4ad4b-199">Neues in MRTK v2</span><span class="sxs-lookup"><span data-stu-id="4ad4b-199">New with MRTK v2</span></span>
<span data-ttu-id="4ad4b-200">Wir unserer Verpflichtung, diese plattformtools belastet werden soll.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="4ad4b-201">In der Tat nutzten wir MRTK Version 2 zum Entwickeln von unserer Erfahrungen bei der Posteingang, z. B. der Setup-Experience (OOBE) und unser Mixed Reality-Learning-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="4ad4b-202">Sie können auch erwarten neue HoloLens-2-Funktionen, die zuerst offen gelegten MRTK da wir davon, dass es sich um die beste Möglichkeit ausgehen, die auf unserer Plattform zu entwickeln ist.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="4ad4b-203">Modular</span><span class="sxs-lookup"><span data-stu-id="4ad4b-203">Modular</span></span>
<span data-ttu-id="4ad4b-204">Wir haben es auf modulare Weise erstellt, so, dass Sie nicht benötigen, und jedes Bit des Toolkits Ihr Projekt angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="4ad4b-205">Es gibt tatsächlich einige Vorteile dieser.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="4ad4b-206">Er hält Ihre Projektgröße kleiner als auch ist es einfacher zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="4ad4b-207">Da skriptfähige Objekte zusammengesetzt ist, und Schnittstelle basiert, ist es, auch möglich, ersetzen die Komponenten, die durch Ihre eigenen, um andere Dienste, Systeme und Plattformen zu unterstützen, enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="4ad4b-208">Plattformübergreifend</span><span class="sxs-lookup"><span data-stu-id="4ad4b-208">Cross-platform</span></span>
<span data-ttu-id="4ad4b-209">Apropos auf anderen Plattformen, hat es die plattformübergreifende Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="4ad4b-210">Und obwohl dies nicht bedeutet, dass jede einzelne Plattform standardmäßig unterstützt wird, wir haben dafür gesorgt, dass kein Teil des Codes Toolkit unterbrochen wird, wenn Sie Ihre Build-Ziel für andere Plattformen wechseln.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="4ad4b-211">Die Stabilität und Erweiterbarkeit mit der modularen Aufbaus richtet auf der beste Weg, um die Unterstützung mehrerer Plattformen, wie z. B. ARCore ARKit und OpenVR zu können.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="4ad4b-212">Leistungsstarke</span><span class="sxs-lookup"><span data-stu-id="4ad4b-212">Performant</span></span>
<span data-ttu-id="4ad4b-213">Arbeiten mit mobilen Plattformen, erstellt es diese Leistungsfähigkeit berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="4ad4b-214">Dies ist sehr wichtig, und wir stellen Sie sicher, dass die Tools nicht das für Sie arbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="4ad4b-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="4ad4b-215">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4ad4b-215">See also</span></span>
* [<span data-ttu-id="4ad4b-216">MRTK Leitfaden für erste Schritte</span><span class="sxs-lookup"><span data-stu-id="4ad4b-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="4ad4b-217">MRTK Documentation Home (.NET-Dokumentation: Startseite</span><span class="sxs-lookup"><span data-stu-id="4ad4b-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="4ad4b-218">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="4ad4b-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="4ad4b-219">Portieren von HTK/MRTK auf MRTK Version 2</span><span class="sxs-lookup"><span data-stu-id="4ad4b-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
