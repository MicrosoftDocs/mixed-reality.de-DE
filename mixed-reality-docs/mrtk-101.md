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
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="17b5f-104">Mrtk 101: Verwenden von Mixed Reality Toolkit Unity für grundlegende Interaktionen (hololens 2, hololens, Windows Mixed Reality, Open VR)</span><span class="sxs-lookup"><span data-stu-id="17b5f-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![Mrtk](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="17b5f-106">Erfahren Sie, wie Sie mrtk verwenden können, um einige der am häufigsten verwendeten Interaktionsmuster in gemischter Realität zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="17b5f-107">Simulieren von Eingabe Interaktionen im Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="17b5f-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="17b5f-108">Wie kann man ein Objekt erfassen und verschieben?</span><span class="sxs-lookup"><span data-stu-id="17b5f-108">How to grab and move an object?</span></span>
- <span data-ttu-id="17b5f-109">Wie wird die Größe eines Objekts geändert?</span><span class="sxs-lookup"><span data-stu-id="17b5f-109">How to resize an object?</span></span>
- <span data-ttu-id="17b5f-110">Verschieben oder Drehen eines Objekts mit präziser Genauigkeit</span><span class="sxs-lookup"><span data-stu-id="17b5f-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="17b5f-111">Wie wird ein Objekt auf Eingabeereignisse reagieren?</span><span class="sxs-lookup"><span data-stu-id="17b5f-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="17b5f-112">Vorgehensweise beim Hinzufügen von visuellem Feedback</span><span class="sxs-lookup"><span data-stu-id="17b5f-112">How to add visual feedback?</span></span>
- <span data-ttu-id="17b5f-113">Vorgehensweise beim Hinzufügen von Audiofeedback</span><span class="sxs-lookup"><span data-stu-id="17b5f-113">How to add audio feedback?</span></span>
- <span data-ttu-id="17b5f-114">Verwendung von hololens 2-Schaltflächen für Stilvorlagen</span><span class="sxs-lookup"><span data-stu-id="17b5f-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="17b5f-115">Wie wird ein Objekt befolgt?</span><span class="sxs-lookup"><span data-stu-id="17b5f-115">How to make an object follow you?</span></span>
- <span data-ttu-id="17b5f-116">Wie wird ein Objekt Ihnen angezeigt?</span><span class="sxs-lookup"><span data-stu-id="17b5f-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="17b5f-117">Simulieren von Eingabe Interaktionen im Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="17b5f-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="17b5f-118">Mrtk unterstützt die Eingabe Simulation im Editor.</span><span class="sxs-lookup"><span data-stu-id="17b5f-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="17b5f-119">Führen Sie einfach die Szene durch Klicken auf die Wiedergabe Schaltfläche Unity aus.</span><span class="sxs-lookup"><span data-stu-id="17b5f-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="17b5f-120">Verwenden Sie diese Schlüssel, um Eingaben zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="17b5f-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="17b5f-121">Drücken Sie die Taste W, A, S, D, um die Kamera zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="17b5f-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="17b5f-122">Halten Sie die Rechte Maustaste gedrückt, und bewegen Sie die Maus, um sich umzusehen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="17b5f-123">Um die simulierten Hände anzuzeigen, drücken Sie die Leertaste (Rechte Seite) oder die linke Umschalttaste (linke Seite), um simulierte Hände in der Ansicht beizubehalten, drücken Sie die Taste T oder Y, um simulierte Hände zu drehen, und drücken Sie Q oder E (horizontal)/R oder F (vertikal).</span><span class="sxs-lookup"><span data-stu-id="17b5f-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="17b5f-124">Weitere Informationen zur Eingabe Simulation finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="17b5f-125">Wie kann man ein Objekt erfassen und verschieben?</span><span class="sxs-lookup"><span data-stu-id="17b5f-125">How to grab and move an object?</span></span>
<span data-ttu-id="17b5f-126">Wenn Sie ein Objekt abgleichen möchten, weisen Sie diese beiden Skripts zu: ManipulationHandler.cs und nearinteraktiongrabbable. cs (für Direct Send mit der Eingabe von Handgelenk Nachverfolgung), unterstützt manipulationhandler sowohl near-als auch weite Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="17b5f-127">Sie können ein Objekt mit der Hand nach Verfolgungs Eingabe (in der Nähe), dem Hand Strahl (weit), dem Strahl des Bewegungs Controllers (weit), dem Blick & Cursor des hololens 2 (in der Nähe), dem Hand Strahl (Far</span><span class="sxs-lookup"><span data-stu-id="17b5f-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="17b5f-128">Wie wird die Größe eines Objekts geändert?</span><span class="sxs-lookup"><span data-stu-id="17b5f-128">How to resize an object?</span></span>
<span data-ttu-id="17b5f-129">ManipulationHandler.cs unterstützt zweistufige Skalierung/Drehung.</span><span class="sxs-lookup"><span data-stu-id="17b5f-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="17b5f-130">Dies funktioniert mit verschiedenen Eingabetypen, wie z. b. der Hand Eingabe von hololens 2, der Eingabe von hololens 1 und der EINGABETASTE und der Eingabe des Bewegungs Controllers von Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="17b5f-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="17b5f-131">Weitere Informationen zum Manipulations Handler finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="17b5f-132">Verschieben oder Drehen eines Objekts mit präziser Genauigkeit</span><span class="sxs-lookup"><span data-stu-id="17b5f-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="17b5f-133">Weisen Sie einem Objekt BoundingBox.cs zu, um das umgebende Feld zu verwenden, das die Schnittstelle zum Skalieren und Drehen eines Objekts ist.</span><span class="sxs-lookup"><span data-stu-id="17b5f-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="17b5f-134">In der Standardeinstellung werden hololens 1 Style Blue Handles und Drähte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="17b5f-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="17b5f-135">Zum Verwenden von hololens 2-Stil-near-basierten animierten Handles müssen Sie Prefabs und Material zuweisen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="17b5f-136">Ausführliche Informationen zur Konfiguration finden Sie in der Dokumentation zum umgebenden [Feld](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) und in der boundingboxexamples. unity-Szene.</span><span class="sxs-lookup"><span data-stu-id="17b5f-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="17b5f-137">Weitere Informationen zum umgebenden Feld finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="17b5f-138">Wie wird ein Objekt auf Eingabeereignisse reagieren?</span><span class="sxs-lookup"><span data-stu-id="17b5f-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="17b5f-139">Weisen Sie einem Objekt PointerHandler.cs zu.</span><span class="sxs-lookup"><span data-stu-id="17b5f-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="17b5f-140">Im Inspektor können Sie die Ereignisse onpointerdown (), onpointerup (), onpointergeklickt () und onpointerdrag () verwenden, um diese Ereignisse in einem Skript zu verwenden, implementieren Sie imixedrealitypointerhandler.</span><span class="sxs-lookup"><span data-stu-id="17b5f-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="17b5f-141">Weitere Informationen zum Eingabe System finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="17b5f-142">Vorgehensweise beim Hinzufügen von visuellem Feedback</span><span class="sxs-lookup"><span data-stu-id="17b5f-142">How to add visual feedback?</span></span>
<span data-ttu-id="17b5f-143">Weisen Sie einem Objekt Interactable.cs zu.</span><span class="sxs-lookup"><span data-stu-id="17b5f-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="17b5f-144">Erstellen Sie im Inspektor ein neues Design.</span><span class="sxs-lookup"><span data-stu-id="17b5f-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="17b5f-145">Mithilfe der designprofile von interactable können Sie allen verfügbaren Eingabe Interaktions Zuständen problemlos visuelles Feedback hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="17b5f-146">Interactable bietet verschiedene Arten von Themen, einschließlich des Shader-Designs, mit dem Sie die Eigenschaften des Shaders pro Interaktions Zustand steuern können.</span><span class="sxs-lookup"><span data-stu-id="17b5f-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="17b5f-147">Weitere Informationen zu interactable finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="17b5f-148">Ein weiterer wichtiger Baustein für visuelles Feedback ist der mrtk-Standard-Shader.</span><span class="sxs-lookup"><span data-stu-id="17b5f-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="17b5f-149">Mit dem mrtk-Standard-Shader können Sie problemlos visuelle Feedback Effekte hinzufügen, wie z. b. Hover Light und Near Light.</span><span class="sxs-lookup"><span data-stu-id="17b5f-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="17b5f-150">Da der mrtk-Standard-Shader eine deutlich geringere Berechnung als der Unity-standardshader durchführt, können Sie ein leistungsfähiges Verhalten erzielen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="17b5f-151">Erstellen Sie ein neues Material, und wählen Sie den Shader ' Mixed Reality Toolkit > Standard ' aus.</span><span class="sxs-lookup"><span data-stu-id="17b5f-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="17b5f-152">Oder Sie können eines der vorhandenen Materialien auswählen, das den mrtk-Standard-Shader verwendet.</span><span class="sxs-lookup"><span data-stu-id="17b5f-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="17b5f-153">Weitere Informationen zum mrtk-Standard-Shader finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="17b5f-154">Vorgehensweise beim Hinzufügen von Audiofeedback</span><span class="sxs-lookup"><span data-stu-id="17b5f-154">How to add audio feedback?</span></span>
<span data-ttu-id="17b5f-155">Fügen Sie audiosource einem Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="17b5f-155">Add AudioSource to an object.</span></span> <span data-ttu-id="17b5f-156">Weisen Sie dann in den Skripts, die Eingabeereignisse verfügbar machen (z. b. Interactable.cs oder PointerHandler.cs) das Objekt dem-Ereignis zu, und wählen Sie audiosource. playoneshot () aus.</span><span class="sxs-lookup"><span data-stu-id="17b5f-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="17b5f-157">Sie können Ihre Audioclips verwenden oder eines aus den audioassets von mrtk auswählen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="17b5f-158">Verwendung von hololens 2-Schaltflächen für Stilvorlagen</span><span class="sxs-lookup"><span data-stu-id="17b5f-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="17b5f-159">Mrtk bietet verschiedene Typen von hololens 2-shellschaltflächen (OS).</span><span class="sxs-lookup"><span data-stu-id="17b5f-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="17b5f-160">Es bietet anspruchsvolle visuelle Feedback, wie z. b. near Light, Compress Box und einen Ripple-Effekt auf der Schaltflächen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="17b5f-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="17b5f-161">Per Drag & Drop können Sie einfach eine der vorfab auf der Schaltfläche hololens 2-Stil in ihre Szene ziehen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="17b5f-162">Die vorfab verwendet Interactable.cs, das oben vorgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="17b5f-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="17b5f-163">Sie können verfügbar gemachte Ereignisse wie z. b. "OnClick ()" in der interactable verwenden, um Aktionen auszumachen.</span><span class="sxs-lookup"><span data-stu-id="17b5f-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="17b5f-164">Weitere Informationen zu Schaltflächen-Prefabs finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="17b5f-165">Wie wird ein Objekt befolgt?</span><span class="sxs-lookup"><span data-stu-id="17b5f-165">How to make an object follow you?</span></span>
<span data-ttu-id="17b5f-166">Zuweisen eines RadialView.cs-Skripts zu einem Objekt.</span><span class="sxs-lookup"><span data-stu-id="17b5f-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="17b5f-167">Er ist Teil der Solver-Skript Reihe, mit der Sie verschiedene Arten der Objekt Positionierung in 3D-Raum erreichen können.</span><span class="sxs-lookup"><span data-stu-id="17b5f-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="17b5f-168">SolverHandler.cs wird automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="17b5f-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="17b5f-169">Im folgenden finden Sie ein Beispiel für eine radialview-Konfiguration, um das "Lazy follow"-tagparallel Verhalten zu erreichen, wie das Startmenü in der hololens-Shell.</span><span class="sxs-lookup"><span data-stu-id="17b5f-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="17b5f-170">Sie können die minimale/maximale Entfernung und die minimale/maximale Anzeige Grad angeben.</span><span class="sxs-lookup"><span data-stu-id="17b5f-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="17b5f-171">Im folgenden Beispiel wird gezeigt, wie das Objekt zwischen 0,4 m und 0,8 m Bereich in 15 ° positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="17b5f-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="17b5f-172">Passen Sie Lerp-Zeit Werte an, um das Positions Update schneller oder langsamer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="17b5f-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="17b5f-173">Weitere Informationen zu Solvers finden Sie in der mrtk-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="17b5f-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="17b5f-174">Wie wird ein Objekt Ihnen angezeigt?</span><span class="sxs-lookup"><span data-stu-id="17b5f-174">How to make an object face you?</span></span>
<span data-ttu-id="17b5f-175">Zuweisen eines Billboard.cs-Skripts zu einem Objekt.</span><span class="sxs-lookup"><span data-stu-id="17b5f-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="17b5f-176">Sie wird unabhängig von ihrer Position immer mit Ihnen konfrontiert.</span><span class="sxs-lookup"><span data-stu-id="17b5f-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="17b5f-177">Sie können die Option Pivot-Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="17b5f-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="17b5f-178">Sind Sie bereit, beeindruckende Umgebungen für gemischte Realität zu schaffen?</span><span class="sxs-lookup"><span data-stu-id="17b5f-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="17b5f-179">Besuchen Sie die nachfolgenden Seiten, und erfahren Sie mehr über mrtk und gemischte Realität.</span><span class="sxs-lookup"><span data-stu-id="17b5f-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="17b5f-180">Über die Autorin</span><span class="sxs-lookup"><span data-stu-id="17b5f-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="17b5f-181"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="17b5f-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="17b5f-182">UX-Designer-@Microsoft</span><span class="sxs-lookup"><span data-stu-id="17b5f-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="17b5f-183">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="17b5f-183">See also</span></span>

* [<span data-ttu-id="17b5f-184">Mixed Reality Toolkit-Unity (mrtk) GitHub</span><span class="sxs-lookup"><span data-stu-id="17b5f-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="17b5f-185">Mrtk-Dokumentations Portal</span><span class="sxs-lookup"><span data-stu-id="17b5f-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="17b5f-186">Ersten Schritte mit mrtk</span><span class="sxs-lookup"><span data-stu-id="17b5f-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="17b5f-187">Holotoolkit zu mrtk Porting-Richtlinie</span><span class="sxs-lookup"><span data-stu-id="17b5f-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
