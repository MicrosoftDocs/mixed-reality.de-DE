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
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028313"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="af0b6-104">MRTK-Einführung Verwenden des Mixed Reality-Toolkits Unity für grundlegende Interaktionen (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span><span class="sxs-lookup"><span data-stu-id="af0b6-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="af0b6-106">Erfahren Sie, wie Sie das MRTK nutzen, um einige der am häufigsten verwendeten Interaktionsmuster in Mixed Reality umzusetzen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="af0b6-107">Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?</span><span class="sxs-lookup"><span data-stu-id="af0b6-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="af0b6-108">Wie lässt sich ein Objekt greifen und bewegen?</span><span class="sxs-lookup"><span data-stu-id="af0b6-108">How to grab and move an object?</span></span>
- <span data-ttu-id="af0b6-109">Wie wird die Größe eines Objekts geändert?</span><span class="sxs-lookup"><span data-stu-id="af0b6-109">How to resize an object?</span></span>
- <span data-ttu-id="af0b6-110">Wie lässt sich ein Objekt präzise bewegen oder drehen?</span><span class="sxs-lookup"><span data-stu-id="af0b6-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="af0b6-111">Wie lässt man ein Objekt auf Eingabeereignisse reagieren?</span><span class="sxs-lookup"><span data-stu-id="af0b6-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="af0b6-112">Wie wird visuelles Feedback implementiert?</span><span class="sxs-lookup"><span data-stu-id="af0b6-112">How to add visual feedback?</span></span>
- <span data-ttu-id="af0b6-113">Wie kann Audiofeedback hinzugefügt werden?</span><span class="sxs-lookup"><span data-stu-id="af0b6-113">How to add audio feedback?</span></span>
- <span data-ttu-id="af0b6-114">Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?</span><span class="sxs-lookup"><span data-stu-id="af0b6-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="af0b6-115">Wie lässt man sich von einem Objekt folgen?</span><span class="sxs-lookup"><span data-stu-id="af0b6-115">How to make an object follow you?</span></span>
- <span data-ttu-id="af0b6-116">Wie erreicht man, dass ein Objekt sich einem zuwendet?</span><span class="sxs-lookup"><span data-stu-id="af0b6-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="af0b6-117">Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?</span><span class="sxs-lookup"><span data-stu-id="af0b6-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="af0b6-118">MRTK unterstützt die Simulation von Eingaben im Editor.</span><span class="sxs-lookup"><span data-stu-id="af0b6-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="af0b6-119">Führen Sie die Szene einfach durch Klicken auf die Wiedergabe Schaltfläche in Unity aus.</span><span class="sxs-lookup"><span data-stu-id="af0b6-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="af0b6-120">Verwenden der Tasten zum Simulieren von Eingaben.</span><span class="sxs-lookup"><span data-stu-id="af0b6-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="af0b6-121">Drücken Sie die Tasten W, A, S, D, um die Kamera zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="af0b6-122">Halten Sie die rechte Maustaste gedrückt, und bewegen Sie die Maus, um sich umzusehen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="af0b6-123">Um die simulierten Hände anzuzeigen, drücken Sie die LEERTASTE (rechte Hand) oder die linke UMSCHALTTASTE (linke Hand). Um die simulierten Hände ständig anzuzeigen, drücken Sie die T- oder die Y-Taste. Um die simulierten Hände zu drehen, drücken Sie Q oder E (horizontal) bzw. R oder F (vertikal).</span><span class="sxs-lookup"><span data-stu-id="af0b6-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="af0b6-124">Weitere Informationen zur Eingabesimulation finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="af0b6-125">Wie lässt sich ein Objekt greifen und bewegen?</span><span class="sxs-lookup"><span data-stu-id="af0b6-125">How to grab and move an object?</span></span>
<span data-ttu-id="af0b6-126">Um ein Objekt greifbar zu machen, weisen Sie diese beiden Skripts zu: „ManipulationHandler.cs“ und „NearInteractionGrabbable.cs“ (für direktes Greifen mit Eingabe durch artikuliertes Hand-Tracking). ManipulationHandler unterstützt sowohl Nah- als auch Fern-Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="af0b6-127">Sie können ein Objekt durch die Eingabe mittels artikuliertem Hand-Tracking (nah), Handstrahl (fern), den Strahl des Motion Controllers (fern), den Anvisier-Cursor von HoloLens und Tippen in die Luft (fern) greifen und bewegen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="af0b6-128">Wie wird die Größe eines Objekts geändert?</span><span class="sxs-lookup"><span data-stu-id="af0b6-128">How to resize an object?</span></span>
<span data-ttu-id="af0b6-129">ManipulationHandler.cs unterstützt die beidhändige Skalierung/Drehung.</span><span class="sxs-lookup"><span data-stu-id="af0b6-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="af0b6-130">Dies funktioniert mit verschiedenen Eingabetypen, wie z. B. der Handeingabe von HoloLens 2, der Eingabe durch Anvisieren und Gesten von HoloLens 1 und der Motion Controller-Eingabe des immersiven Headsets für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="af0b6-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="af0b6-131">Weitere Informationen zum Manipulation Handler finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="af0b6-132">Wie lässt sich ein Objekt präzise bewegen oder drehen?</span><span class="sxs-lookup"><span data-stu-id="af0b6-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="af0b6-133">Weisen Sie einem Objekt BoundingBox.cs zu, um Begrenzungsrahmen zu verwenden, die die Oberfläche zum Skalieren und Drehen von Objekten darstellen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="af0b6-134">Standardmäßig werden blaue Ziehpunkte und Drahtlinien im Stil von HoloLens 1 angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af0b6-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="af0b6-135">Um näherungsbasierte animierte Ziehpunkte im HoloLens 2-Stil zu verwenden, müssen Sie Prefabs und Materialien zuweisen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="af0b6-136">Informationen zu den Konfigurationsdetails finden Sie in der [Bounding Box-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) und der BoundingBoxExamples.unity-Szene.</span><span class="sxs-lookup"><span data-stu-id="af0b6-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="af0b6-137">Weitere Informationen zu Bounding Box finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="af0b6-138">Wie lässt man ein Objekt auf Eingabeereignisse reagieren?</span><span class="sxs-lookup"><span data-stu-id="af0b6-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="af0b6-139">Weisen Sie einem Objekt PointerHandler.cs zu.</span><span class="sxs-lookup"><span data-stu-id="af0b6-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="af0b6-140">Im Inspektor können Sie die Ereignisse OnPointerDown (), OnPointerUp (), OnPointerClicked () und OnPointerDragged () verwenden. Um diese Ereignisse in einem Skript zu verwenden, implementieren Sie IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="af0b6-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="af0b6-141">Weitere Informationen zum Eingabesystem finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="af0b6-142">Wie wird visuelles Feedback implementiert?</span><span class="sxs-lookup"><span data-stu-id="af0b6-142">How to add visual feedback?</span></span>
<span data-ttu-id="af0b6-143">Zuweisen von Interactable.cs zu einem Objekt.</span><span class="sxs-lookup"><span data-stu-id="af0b6-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="af0b6-144">Erstellen Sie im Inspektor ein neues Design.</span><span class="sxs-lookup"><span data-stu-id="af0b6-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="af0b6-145">Mithilfe der Designprofile von Interactable können Sie allen verfügbaren Interaktionszuständen auf einfache Weise visuelles Feedback hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="af0b6-146">Interactable stellt verschiedene Arten von Designs zur Verfügung, einschließlich des Shader-Designs, mit dem Sie die Eigenschaften des Shaders pro Interaktionszustand steuern können.</span><span class="sxs-lookup"><span data-stu-id="af0b6-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="af0b6-147">Weitere Informationen zu Interactable finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="af0b6-148">Ein weiterer wichtiger Baustein für visuelles Feedback ist der MRTK-Standardshader.</span><span class="sxs-lookup"><span data-stu-id="af0b6-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="af0b6-149">Mit dem MRTK-Standardshader können Sie auf einfache Weise visuelle Feedbackeffekte hinzufügen, wie das Licht beim Draufzeigen und Näherungslicht.</span><span class="sxs-lookup"><span data-stu-id="af0b6-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="af0b6-150">Da der MRTK-Standardshader erheblich weniger Berechnungen als der Unity-Standardshader ausführt, können Sie ein leistungsstarkes Verhalten erreichen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="af0b6-151">Erstellen Sie ein neues Material, und wählen Sie den Shader „Mixed Reality Toolkit > Standard“ aus.</span><span class="sxs-lookup"><span data-stu-id="af0b6-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="af0b6-152">Alternativ können Sie eins der vorhandenen Materialien auswählen, die den MRTK-Standardshader verwenden.</span><span class="sxs-lookup"><span data-stu-id="af0b6-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="af0b6-153">Weitere Informationen zum MRTK-Standardshader finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="af0b6-154">Wie kann Audiofeedback hinzugefügt werden?</span><span class="sxs-lookup"><span data-stu-id="af0b6-154">How to add audio feedback?</span></span>
<span data-ttu-id="af0b6-155">Fügen Sie einem Objekt AudioSource hinzu.</span><span class="sxs-lookup"><span data-stu-id="af0b6-155">Add AudioSource to an object.</span></span> <span data-ttu-id="af0b6-156">Weisen Sie dann in den Skripts, die Eingabeereignisse verfügbar machen (z. B. Interactable.cs oder PointerHandler.cs) das Objekt dem Ereignis zu, und wählen Sie AudioSource.PlayOneShot() aus.</span><span class="sxs-lookup"><span data-stu-id="af0b6-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="af0b6-157">Sie können eigene Audioclips verwenden oder einen aus den Audioressourcen des MRTK auswählen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="af0b6-158">Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?</span><span class="sxs-lookup"><span data-stu-id="af0b6-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="af0b6-159">MRTK bietet verschiedene Typen von Schaltflächen im Stil der HoloLens 2-Shell (Betriebssystem).</span><span class="sxs-lookup"><span data-stu-id="af0b6-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="af0b6-160">Es stehen raffinierte visuelle Feedbacks wie etwa Näherungslicht, ein gestauchtes Feld und ein Kräuseleffekt auf der Schaltflächenoberfläche zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="af0b6-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="af0b6-161">Legen Sie einfach eins der Prefabs für eine drückbare Schaltfläche im HoloLens 2-Stil per Drag & Drop in Ihrer Szene ab.</span><span class="sxs-lookup"><span data-stu-id="af0b6-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="af0b6-162">Das Prefab verwendet Interactable.cs, die oben vorgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="af0b6-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="af0b6-163">Sie können in Interactable verfügbar gemachte Ereignisse wie OnClick() verwenden, um Aktionen auszulösen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="af0b6-164">Weitere Informationen zu Schaltflächen-Prefabs finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="af0b6-165">Wie lässt man sich von einem Objekt folgen?</span><span class="sxs-lookup"><span data-stu-id="af0b6-165">How to make an object follow you?</span></span>
<span data-ttu-id="af0b6-166">Weisen Sie einem Objekt das RadialView.cs-Skript zu.</span><span class="sxs-lookup"><span data-stu-id="af0b6-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="af0b6-167">Es ist Teil der Solver-Reihe von Skripts, die Ihnen verschiedene Arten von Objektpositionierung im 3D-Raum ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="af0b6-168">SolverHandler.cs wird automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="af0b6-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="af0b6-169">Unten finden Sie ein Beispiel der RadialView-Konfiguration, um ein „Hinterhertrotten“-Folgeverhalten zu erreichen, ähnlich wie das Startmenü in der HoloLens-Shell.</span><span class="sxs-lookup"><span data-stu-id="af0b6-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="af0b6-170">Sie können die minimale/maximale Entfernung und den minimalen/maximalen Ansichtswinkel angeben.</span><span class="sxs-lookup"><span data-stu-id="af0b6-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="af0b6-171">Im Beispiel unten ist die Positionierung des Objekts zwischen 0,4 m und 0,8 m in einem Bereich von 15 ° dargestellt.</span><span class="sxs-lookup"><span data-stu-id="af0b6-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="af0b6-172">Passen Sie die Werte für die Lerp-Zeit an, um das Aktualisieren der Position schneller oder langsamer erfolgen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="af0b6-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="af0b6-173">Weitere Informationen zu Solvern finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="af0b6-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="af0b6-174">Wie erreicht man, dass ein Objekt sich einem zuwendet?</span><span class="sxs-lookup"><span data-stu-id="af0b6-174">How to make an object face you?</span></span>
<span data-ttu-id="af0b6-175">Weisen Sie einem Objekt das Billboard.cs-Skript zu.</span><span class="sxs-lookup"><span data-stu-id="af0b6-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="af0b6-176">Das Objekt wendet sich Ihnen dann immer zu, unabhängig von Ihrer Position.</span><span class="sxs-lookup"><span data-stu-id="af0b6-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="af0b6-177">Sie können die Pivotachsenoption angeben.</span><span class="sxs-lookup"><span data-stu-id="af0b6-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="af0b6-178">Sind Sie bereit, beeindruckende Erlebnisse für Mixed Reality zu gestalten?</span><span class="sxs-lookup"><span data-stu-id="af0b6-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="af0b6-179">Besuchen Sie die unten angegebenen Seiten, und erfahren Sie mehr über MRTK und Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="af0b6-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="af0b6-180">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="af0b6-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="af0b6-181"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="af0b6-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="af0b6-182">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="af0b6-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="af0b6-183">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="af0b6-183">See also</span></span>

* [<span data-ttu-id="af0b6-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="af0b6-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="af0b6-185">MRTK-Dokumentationsportal</span><span class="sxs-lookup"><span data-stu-id="af0b6-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="af0b6-186">Erste Schritte mit MRTK</span><span class="sxs-lookup"><span data-stu-id="af0b6-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="af0b6-187">Portierungsrichtlinie HoloToolkit zu MRTK</span><span class="sxs-lookup"><span data-stu-id="af0b6-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
