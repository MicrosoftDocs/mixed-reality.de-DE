---
title: Gesten und Bewegungs Controller in Unity
description: Es gibt zwei wichtige Möglichkeiten, um ihre Blicke in Unity, Handgesten und Bewegungs Controllern zu übernehmen.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe
ms.openlocfilehash: f0d2835a08ef534af1310db35ccb81888e49aeb8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525760"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="8d925-104">Gesten und Bewegungs Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="8d925-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="8d925-105">Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](gestures.md) und [Bewegungs Controllern](motion-controllers.md) in hololens und immersiven HMD zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="8d925-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="8d925-106">Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.</span><span class="sxs-lookup"><span data-stu-id="8d925-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="8d925-107">Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality, die gängigen *Input. getbutton/Input. getaxis-* APIs, die über mehrere Unity-XR-sdker hinweg verwendet werden können, sowie eine API für *interaktionmanager/GestureRecognizer* . Windows Mixed Reality, das den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="8d925-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="8d925-108">Unity-Schaltfläche/Achsen Zuordnung (Tabelle)</span><span class="sxs-lookup"><span data-stu-id="8d925-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="8d925-109">Die Schaltflächen-und Achsen-IDs in der folgenden Tabelle werden im Unity-Eingabe-Manager für Windows Mixed Reality Motion Controller über die *Eingabe. getbutton/getaxis* -APIs unterstützt, während die Spalte "Windows Mr-spezifisch" auf Eigenschaften verweist, die aus dem *Interaktionsourcestate* -Typ.</span><span class="sxs-lookup"><span data-stu-id="8d925-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="8d925-110">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8d925-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="8d925-111">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs</span><span class="sxs-lookup"><span data-stu-id="8d925-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="8d925-112">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:</span><span class="sxs-lookup"><span data-stu-id="8d925-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="8d925-113">Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8d925-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="8d925-114">Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für physische abxy-Schaltflächen verfügbar</span><span class="sxs-lookup"><span data-stu-id="8d925-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="8d925-115">Eingabe</span><span class="sxs-lookup"><span data-stu-id="8d925-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="8d925-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="8d925-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="8d925-117">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="8d925-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="8d925-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="8d925-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="8d925-119">XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="8d925-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="8d925-120">Links</span><span class="sxs-lookup"><span data-stu-id="8d925-120">Left hand</span></span> </th><th> <span data-ttu-id="8d925-121">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="8d925-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8d925-122">Select-Taste gedrückt</span><span class="sxs-lookup"><span data-stu-id="8d925-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="8d925-123">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="8d925-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="8d925-124">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="8d925-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="8d925-125">selectpressed</span><span class="sxs-lookup"><span data-stu-id="8d925-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-126">Auswählen des analogen Auslöse Werts</span><span class="sxs-lookup"><span data-stu-id="8d925-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="8d925-127">Achse 9</span><span class="sxs-lookup"><span data-stu-id="8d925-127">Axis 9</span></span> </td><td> <span data-ttu-id="8d925-128">Achse 10</span><span class="sxs-lookup"><span data-stu-id="8d925-128">Axis 10</span></span> </td><td> <span data-ttu-id="8d925-129">selectpressedamount</span><span class="sxs-lookup"><span data-stu-id="8d925-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-130">Select-Taste teilweise gedrückt</span><span class="sxs-lookup"><span data-stu-id="8d925-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="8d925-131">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8d925-132">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8d925-133">selectpressedamount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="8d925-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-134">Menü Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="8d925-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="8d925-135">Schaltfläche 6 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-135">Button 6\*</span></span> </td><td> <span data-ttu-id="8d925-136">Schaltfläche 7 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-136">Button 7\*</span></span> </td><td> <span data-ttu-id="8d925-137">menupressed</span><span class="sxs-lookup"><span data-stu-id="8d925-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-138">Zieh Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="8d925-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="8d925-139">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="8d925-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="8d925-140">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8d925-141">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="8d925-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="8d925-142">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8d925-143">Schna</span><span class="sxs-lookup"><span data-stu-id="8d925-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-144">Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="8d925-145">Achse 1</span><span class="sxs-lookup"><span data-stu-id="8d925-145">Axis 1</span></span> </td><td> <span data-ttu-id="8d925-146">Achse 4</span><span class="sxs-lookup"><span data-stu-id="8d925-146">Axis 4</span></span> </td><td> <span data-ttu-id="8d925-147">thumbstickposition. x</span><span class="sxs-lookup"><span data-stu-id="8d925-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-148">Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="8d925-149">Achse 2</span><span class="sxs-lookup"><span data-stu-id="8d925-149">Axis 2</span></span> </td><td> <span data-ttu-id="8d925-150">Achse 5</span><span class="sxs-lookup"><span data-stu-id="8d925-150">Axis 5</span></span> </td><td> <span data-ttu-id="8d925-151">thumbstickposition. y</span><span class="sxs-lookup"><span data-stu-id="8d925-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-152">Thumbstick gedrückt</span><span class="sxs-lookup"><span data-stu-id="8d925-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="8d925-153">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="8d925-153">Button 8</span></span> </td><td> <span data-ttu-id="8d925-154">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="8d925-154">Button 9</span></span> </td><td> <span data-ttu-id="8d925-155">thumbstickpressed</span><span class="sxs-lookup"><span data-stu-id="8d925-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-156">Touchpad X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="8d925-157">Achse 17 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="8d925-158">Achse 19 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="8d925-159">touchpadposition. x</span><span class="sxs-lookup"><span data-stu-id="8d925-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-160">Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="8d925-161">Achse 18 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="8d925-162">Achse 20 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="8d925-163">touchpadposition. y</span><span class="sxs-lookup"><span data-stu-id="8d925-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-164">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="8d925-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="8d925-165">Schaltfläche 18 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-165">Button 18\*</span></span> </td><td> <span data-ttu-id="8d925-166">Schaltfläche 19 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-166">Button 19\*</span></span> </td><td> <span data-ttu-id="8d925-167">touchpadtouched</span><span class="sxs-lookup"><span data-stu-id="8d925-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-168">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="8d925-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="8d925-169">Schaltfläche 16 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-169">Button 16\*</span></span> </td><td> <span data-ttu-id="8d925-170">Schaltfläche 17 \*</span><span class="sxs-lookup"><span data-stu-id="8d925-170">Button 17\*</span></span> </td><td> <span data-ttu-id="8d925-171">touchpadpressed</span><span class="sxs-lookup"><span data-stu-id="8d925-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-172">6DOF-Zieh Punkt Pose oder Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="8d925-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="8d925-173">Nur Ziehpunkt <i>darstellen:</i> <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a></span><span class="sxs-lookup"><span data-stu-id="8d925-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="8d925-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></span><span class="sxs-lookup"><span data-stu-id="8d925-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="8d925-175">Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition</span><span class="sxs-lookup"><span data-stu-id="8d925-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="8d925-176">SourceState. sourcepose. trygetrotation</span><span class="sxs-lookup"><span data-stu-id="8d925-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="8d925-177">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="8d925-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="8d925-178"><i>Die Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über die Mr-spezifische API verfügbar.</i> </span><span class="sxs-lookup"><span data-stu-id="8d925-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="8d925-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a></span><span class="sxs-lookup"><span data-stu-id="8d925-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="8d925-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></span><span class="sxs-lookup"><span data-stu-id="8d925-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="8d925-181">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="8d925-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="8d925-182">Ziehpunkt im Vergleich zu Zeige darstellen</span><span class="sxs-lookup"><span data-stu-id="8d925-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="8d925-183">Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die apps beim Rendern der ern.</span><span class="sxs-lookup"><span data-stu-id="8d925-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="8d925-184">Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können **, die** Ziehpunkt-und die **Zeiger**Darstellung.</span><span class="sxs-lookup"><span data-stu-id="8d925-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="8d925-185">Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="8d925-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="8d925-186">Ziehpunkt darstellen</span><span class="sxs-lookup"><span data-stu-id="8d925-186">Grip pose</span></span>

<span data-ttu-id="8d925-187">Die Ziehpunkt- **Pose** stellt die Position der Palme einer Hand dar, die von einem hololens erkannt wird, oder die Palme, die einen Bewegungs Controller enthält.</span><span class="sxs-lookup"><span data-stu-id="8d925-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="8d925-188">Bei immersiven Headsets eignet sich die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten**wird, z. b. ein Schwert oder eine Waffe.</span><span class="sxs-lookup"><span data-stu-id="8d925-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="8d925-189">Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet, da das **renderbare Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, die Zieh Punkt Darstellung als Ursprung und Mittelpunkt der Drehung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d925-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="8d925-190">Die Ziehpunkt-Pose wird wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="8d925-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="8d925-191">Die Zieh **Punktposition**: Der Palmen Schwerpunkt, wenn der Controller auf natürliche Weise nach links oder rechts angepasst wird, um die Position im Ziehpunkt zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="8d925-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="8d925-192">Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".</span><span class="sxs-lookup"><span data-stu-id="8d925-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="8d925-193">Die **Rechte Achse**der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist der Strahl, der normal ist, für das Palmen (vorwärts von der linken Palme, rückwärts von der rechten Palme)</span><span class="sxs-lookup"><span data-stu-id="8d925-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="8d925-194">Die **Vorwärts Achse**der Zieh Richtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das von Ihnen nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.</span><span class="sxs-lookup"><span data-stu-id="8d925-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="8d925-195">Die **aufwärts-Achse**der Zieh Richtung: Die aufwärts-Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="8d925-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="8d925-196">Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation*) oder über die Windows-spezifische API (*SourceState. sourcepose. trygetposition/Rotation*), die die Daten für den **Zieh Knoten** anfordert.</span><span class="sxs-lookup"><span data-stu-id="8d925-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="8d925-197">Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="8d925-197">Pointer pose</span></span>

<span data-ttu-id="8d925-198">Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.</span><span class="sxs-lookup"><span data-stu-id="8d925-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="8d925-199">Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**.</span><span class="sxs-lookup"><span data-stu-id="8d925-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="8d925-200">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der entlang des fassers des App-defined Gun-Modells verläuft.</span><span class="sxs-lookup"><span data-stu-id="8d925-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="8d925-201">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.</span><span class="sxs-lookup"><span data-stu-id="8d925-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="8d925-202">Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation*verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="8d925-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="8d925-203">Controller nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="8d925-203">Controller tracking state</span></span>

<span data-ttu-id="8d925-204">Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8d925-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="8d925-205">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="8d925-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="8d925-206">Wenn der Benutzer die Controller aus dem Feld des endfelds der Ansicht verschiebt, werden in den meisten Fällen die Controller Positionen von Windows weiter abgeleitet und der APP bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8d925-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="8d925-207">Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="8d925-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="8d925-208">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="8d925-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="8d925-209">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.</span><span class="sxs-lookup"><span data-stu-id="8d925-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="8d925-210">Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="8d925-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="8d925-211">Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:</span><span class="sxs-lookup"><span data-stu-id="8d925-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="8d925-212">Grund für die explizite Nachverfolgung des Zustands</span><span class="sxs-lookup"><span data-stu-id="8d925-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="8d925-213">Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy*:</span><span class="sxs-lookup"><span data-stu-id="8d925-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="8d925-214">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="8d925-214">Tracking state</span></span> </th><th> <span data-ttu-id="8d925-215">Sourcelossrisk</span><span class="sxs-lookup"><span data-stu-id="8d925-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="8d925-216">Positionsgenauigkeit</span><span class="sxs-lookup"><span data-stu-id="8d925-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="8d925-217">Trygetposition</span><span class="sxs-lookup"><span data-stu-id="8d925-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8d925-218"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="8d925-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="8d925-219">&lt;1,0</span><span class="sxs-lookup"><span data-stu-id="8d925-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8d925-220">Hoch</span><span class="sxs-lookup"><span data-stu-id="8d925-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8d925-221">true</span><span class="sxs-lookup"><span data-stu-id="8d925-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-222"><b>Hohe Genauigkeit (Risiko eines Verlusts)</b> </span><span class="sxs-lookup"><span data-stu-id="8d925-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="8d925-223">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="8d925-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8d925-224">Hoch</span><span class="sxs-lookup"><span data-stu-id="8d925-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8d925-225">true</span><span class="sxs-lookup"><span data-stu-id="8d925-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-226"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="8d925-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="8d925-227">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="8d925-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="8d925-228">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="8d925-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8d925-229">true</span><span class="sxs-lookup"><span data-stu-id="8d925-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8d925-230"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="8d925-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="8d925-231">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="8d925-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="8d925-232">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="8d925-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="8d925-233">false</span><span class="sxs-lookup"><span data-stu-id="8d925-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="8d925-234">Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="8d925-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="8d925-235">**Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit.</span><span class="sxs-lookup"><span data-stu-id="8d925-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="8d925-236">Beachten Sie, dass ein beweglicher Controller, der das Sichtfeld vorübergehend verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, weiterhin hohe Genauigkeit für kurze Zeit zurückgibt, basierend auf der Trägheits Verfolgung des Controllers. etabliert.</span><span class="sxs-lookup"><span data-stu-id="8d925-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="8d925-237">**Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="8d925-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="8d925-238">Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht.</span><span class="sxs-lookup"><span data-stu-id="8d925-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="8d925-239">An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von sehr hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="8d925-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="8d925-240">**Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="8d925-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="8d925-241">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="8d925-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="8d925-242">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden</span><span class="sxs-lookup"><span data-stu-id="8d925-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="8d925-243">Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird Während dieser Zeit.</span><span class="sxs-lookup"><span data-stu-id="8d925-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="8d925-244">**Keine Position:** Obwohl der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine vom Text gesperrte Position im Moment nicht aussagekräftig ist.</span><span class="sxs-lookup"><span data-stu-id="8d925-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="8d925-245">Beispielsweise kann ein Controller, der gerade eingeschaltet war, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der von einer anderen Person abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8d925-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="8d925-246">Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.</span><span class="sxs-lookup"><span data-stu-id="8d925-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="8d925-247">Allgemeine Unity-APIs (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="8d925-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="8d925-248">**Namespace:** *Unityengine*, *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="8d925-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="8d925-249">**Typen**: *Eingabe*, *XR. Inputtracking*</span><span class="sxs-lookup"><span data-stu-id="8d925-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="8d925-250">Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="8d925-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="8d925-251">Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8d925-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="8d925-252">Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="8d925-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="8d925-253">Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen</span><span class="sxs-lookup"><span data-stu-id="8d925-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="8d925-254">Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.</span><span class="sxs-lookup"><span data-stu-id="8d925-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="8d925-255">Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="8d925-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="8d925-256">Ändern **Sie die**Schaltfläche "pokschaltfläche" oder die positiv Schaltfläche "alt", um die **Schalt** Fläche "</span><span class="sxs-lookup"><span data-stu-id="8d925-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="8d925-257">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="8d925-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="8d925-258">*Unity-InputManager*</span><span class="sxs-lookup"><span data-stu-id="8d925-258">*Unity InputManager*</span></span>

<span data-ttu-id="8d925-259">Das Skript kann dann mithilfe von " *Input. getbutton*" die Aktion "Senden" überprüfen:</span><span class="sxs-lookup"><span data-stu-id="8d925-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="8d925-260">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen**ändern.</span><span class="sxs-lookup"><span data-stu-id="8d925-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="8d925-261">Direktes drücken des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="8d925-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="8d925-262">Sie können mithilfe von *Input. GetKey*auch manuell über den voll qualifizierten Namen auf Schaltflächen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="8d925-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="8d925-263">Die Pose eines Hand-oder Bewegungs Controllers</span><span class="sxs-lookup"><span data-stu-id="8d925-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="8d925-264">Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking*:</span><span class="sxs-lookup"><span data-stu-id="8d925-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="8d925-265">Beachten Sie, dass dies die Zieh Punktposition des Controllers darstellt (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="8d925-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="8d925-266">Beachten Sie, dass die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) sich zwischen Controllern unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="8d925-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="8d925-267">Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.</span><span class="sxs-lookup"><span data-stu-id="8d925-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="8d925-268">Windows-spezifische APIs (XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="8d925-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="8d925-269">**Namespace:** *Unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="8d925-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="8d925-270">**Typen**: *Interaktionsmanager*, *interaktionsourcestate*, *interaktionsource*, *interaktionsourceproperties*, *interaktionsourcekind*, *interaktionsourcelokation*</span><span class="sxs-lookup"><span data-stu-id="8d925-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="8d925-271">Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d925-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="8d925-272">Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.</span><span class="sxs-lookup"><span data-stu-id="8d925-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="8d925-273">Abrufen des Zustands von Händen und Bewegungs Controllern</span><span class="sxs-lookup"><span data-stu-id="8d925-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="8d925-274">Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="8d925-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="8d925-275">Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="8d925-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="8d925-276">Das *interaktionsourcestate* macht Informationen wie z. b.:</span><span class="sxs-lookup"><span data-stu-id="8d925-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="8d925-277">Welche [Arten von Druck](motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="8d925-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="8d925-278">Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status</span><span class="sxs-lookup"><span data-stu-id="8d925-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="8d925-279">Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt</span><span class="sxs-lookup"><span data-stu-id="8d925-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="8d925-280">Abrufen von vorwärts vorhergesagten Renderingvorgängen</span><span class="sxs-lookup"><span data-stu-id="8d925-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="8d925-281">Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="8d925-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="8d925-282">Diese vorwärts Gesagten Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d925-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="8d925-283">Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die nachstehend beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d925-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="8d925-284">Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.</span><span class="sxs-lookup"><span data-stu-id="8d925-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="8d925-285">Wie bei der Quell **Darstellung** ist dies für das Rendern eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d925-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="8d925-286">Behandeln von Interaktions Quell Ereignissen</span><span class="sxs-lookup"><span data-stu-id="8d925-286">Handling interaction source events</span></span>

<span data-ttu-id="8d925-287">Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.</span><span class="sxs-lookup"><span data-stu-id="8d925-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="8d925-288">So behandeln Sie Interaktions Quell Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="8d925-288">To handle interaction source events:</span></span>
* <span data-ttu-id="8d925-289">Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis.</span><span class="sxs-lookup"><span data-stu-id="8d925-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="8d925-290">Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="8d925-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="8d925-291">Behandeln Sie das-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="8d925-291">Handle the event.</span></span> <span data-ttu-id="8d925-292">Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="8d925-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="8d925-293">Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="8d925-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="8d925-294">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="8d925-294">How to stop handling an event</span></span>

<span data-ttu-id="8d925-295">Sie müssen die Verarbeitung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="8d925-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="8d925-296">Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.</span><span class="sxs-lookup"><span data-stu-id="8d925-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="8d925-297">Liste der Interaktions Quell Ereignisse</span><span class="sxs-lookup"><span data-stu-id="8d925-297">List of interaction source events</span></span>

<span data-ttu-id="8d925-298">Die folgenden Interaktions Quell Ereignisse sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="8d925-298">The available interaction source events are:</span></span>
* <span data-ttu-id="8d925-299">*Interaktionsourceerkannt* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="8d925-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="8d925-300">*Interaktionsourcelost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="8d925-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="8d925-301">*Interaktionsourcepressed* (tippen, Schaltfläche "drücken" oder "auswählen")</span><span class="sxs-lookup"><span data-stu-id="8d925-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="8d925-302">*Interaktionsourcereleasing* (Ende einer Tap-Taste, Schaltfläche freigegeben oder Ende der "Select"-Taste)</span><span class="sxs-lookup"><span data-stu-id="8d925-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="8d925-303">*Interaktionsourceupdatiert* (verschiebt oder ändert einen anderen Zustand.)</span><span class="sxs-lookup"><span data-stu-id="8d925-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="8d925-304">Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind</span><span class="sxs-lookup"><span data-stu-id="8d925-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="8d925-305">Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.</span><span class="sxs-lookup"><span data-stu-id="8d925-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="8d925-306">Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Posen nicht optimal für das Ziel, aus zwei Hauptgründen:</span><span class="sxs-lookup"><span data-stu-id="8d925-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="8d925-307">Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.</span><span class="sxs-lookup"><span data-stu-id="8d925-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="8d925-308">Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Zeit angewendet wird, in der die Daten des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="8d925-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="8d925-309">Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30 bis 40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Presse oder das Release aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="8d925-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="8d925-310">Bei der Eingabe von hololens-Hand Eingaben kommt es zu einer ähnlichen Verarbeitungs Verzögerung, um den Press zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="8d925-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="8d925-311">Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d925-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="8d925-312">Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:</span><span class="sxs-lookup"><span data-stu-id="8d925-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="8d925-313">Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht](gaze.md) hat:</span><span class="sxs-lookup"><span data-stu-id="8d925-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="8d925-314">Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.</span><span class="sxs-lookup"><span data-stu-id="8d925-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="8d925-315">Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="8d925-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="8d925-316">Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:</span><span class="sxs-lookup"><span data-stu-id="8d925-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="8d925-317">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="8d925-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="8d925-318">APIs für zusammengesetzte Gesten auf hoher Ebene (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="8d925-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="8d925-319">**Namespace:** *Unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="8d925-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="8d925-320">**Typen**: *GestureRecognizer*, *gesturesettings*, *interaktionsourcekind*</span><span class="sxs-lookup"><span data-stu-id="8d925-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="8d925-321">Ihre APP kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabe Quellen, Tap-, Halt-, Manipulations-und Navigations Gesten erkennen.</span><span class="sxs-lookup"><span data-stu-id="8d925-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="8d925-322">Mit dem GestureRecognizer können Sie diese zusammengesetzten Gesten sowohl in [Hand](gestures.md) -als auch in [Bewegungs Controllern](motion-controllers.md) erkennen.</span><span class="sxs-lookup"><span data-stu-id="8d925-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="8d925-323">Jedes Gesten Ereignis für den GestureRecognizer stellt sowohl sourcekind für die Eingabe als auch den Ziel-Head-Strahl zum Zeitpunkt des Ereignisses bereit.</span><span class="sxs-lookup"><span data-stu-id="8d925-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="8d925-324">Einige Ereignisse bieten zusätzliche kontextspezifische Informationen.</span><span class="sxs-lookup"><span data-stu-id="8d925-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="8d925-325">Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:</span><span class="sxs-lookup"><span data-stu-id="8d925-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="8d925-326">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="8d925-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="8d925-327">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8d925-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="8d925-328">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="8d925-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="8d925-329">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="8d925-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="8d925-330">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="8d925-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="8d925-331">Wenn Sie den *GestureRecognizer*verwenden möchten, müssen Sie einen *GestureRecognizer*erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="8d925-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="8d925-332">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8d925-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="8d925-333">Geben Sie an, welche Gesten Sie über "" mit "" auf "" festgelegt haben *()* :</span><span class="sxs-lookup"><span data-stu-id="8d925-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="8d925-334">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="8d925-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="8d925-335">Abonnieren Sie Ereignisse für die Gesten, an denen Sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="8d925-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="8d925-336">Navigations-und Manipulations Gesten schließen sich gegenseitig für eine Instanz eines *GestureRecognizer*aus.</span><span class="sxs-lookup"><span data-stu-id="8d925-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="8d925-337">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="8d925-337">Start capturing gestures</span></span>

<span data-ttu-id="8d925-338">Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *startcapturinggesten ()* aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8d925-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="8d925-339">Möglicherweise wird ein Gesten Ereignis generiert, nachdem *stopcapturinggesten ()* aufgerufen wurde, wenn Eingaben vor dem Frame durchgeführt wurden, in dem *stopcapturinggesten ()* verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="8d925-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="8d925-340">Der *GestureRecognizer* weiß, ob er während des previou-Frames, in dem die Geste tatsächlich aufgetreten ist, ein-oder ausgeschaltet war, und daher ist es zuverlässig, die Gesten Überwachung auf der Grundlage der Anzeige Ziele dieses Frames zu starten und zu beenden.</span><span class="sxs-lookup"><span data-stu-id="8d925-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="8d925-341">Erfassungs Gesten nicht mehr</span><span class="sxs-lookup"><span data-stu-id="8d925-341">Stop capturing gestures</span></span>

<span data-ttu-id="8d925-342">So verhindern Sie die Gestenerkennung:</span><span class="sxs-lookup"><span data-stu-id="8d925-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="8d925-343">Entfernen einer Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="8d925-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="8d925-344">Denken Sie daran, abonnierte Ereignisse abzubestellen, bevor Sie ein *GestureRecognizer* -Objekt zerstören.</span><span class="sxs-lookup"><span data-stu-id="8d925-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="8d925-345">Rendern des Motion Controller-Modells in Unity</span><span class="sxs-lookup"><span data-stu-id="8d925-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="8d925-346">![Motion Controller-Modell und-teleportierung](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="8d925-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="8d925-347">*Motion Controller-Modell und-teleportierung*</span><span class="sxs-lookup"><span data-stu-id="8d925-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="8d925-348">Zum Rendering von Bewegungs Controllern in Ihrer APP, die den physischen Controllern entsprechen, die die Benutzer als verschiedene Schaltflächen verwenden, die Sie verwenden, können Sie die **vorfab von "mutioncontroller** " im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d925-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="8d925-349">Dieser Prefab lädt das korrekte gltf-Modell zur Laufzeit dynamisch aus dem installierten Motion Controller-Treiber des Systems.</span><span class="sxs-lookup"><span data-stu-id="8d925-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="8d925-350">Es ist wichtig, dass diese Modelle dynamisch geladen werden, anstatt Sie manuell in den Editor zu importieren, damit Ihre APP physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller anzeigt, die Ihre Benutzer möglicherweise haben.</span><span class="sxs-lookup"><span data-stu-id="8d925-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="8d925-351">Befolgen Sie [die Anweisungen für](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) die ersten Schritte, um das Mixed Reality Toolkit herunterzuladen und es Ihrem Unity-Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d925-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="8d925-352">Wenn Sie Ihre Kamera durch das *mixedrealitycameraparent* -präfab im Rahmen der Schritte für die ersten Schritte ersetzt haben, können Sie es tun!</span><span class="sxs-lookup"><span data-stu-id="8d925-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="8d925-353">Dieses präfab umfasst das Rendern von Bewegungs Controllern.</span><span class="sxs-lookup"><span data-stu-id="8d925-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="8d925-354">Andernfalls fügen Sie *Assets/holotoolkit/Input/Prefabs/mutioncontrollers. Prefab* aus dem Projektbereich in die Szene ein.</span><span class="sxs-lookup"><span data-stu-id="8d925-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="8d925-355">Sie sollten diese Prefab als untergeordnetes Element eines beliebigen übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in der Szene Teleports verwendet, sodass die Controller mit dem Benutzer zusammenkommen.</span><span class="sxs-lookup"><span data-stu-id="8d925-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="8d925-356">Wenn Ihre APP keine teleportierung umfasst, fügen Sie einfach die vorfab im Stammverzeichnis Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d925-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="8d925-357">Auslösen von Objekten</span><span class="sxs-lookup"><span data-stu-id="8d925-357">Throwing objects</span></span>

<span data-ttu-id="8d925-358">Das Auslösen von Objekten in Virtual Reality ist ein schwierigeres Problem, das möglicherweise zuerst erscheint.</span><span class="sxs-lookup"><span data-stu-id="8d925-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="8d925-359">Wie bei den meisten physisch basierenden Interaktionen verhält es sich beim Auslösen im Spiel auf unerwartete Weise, es ist sofort offensichtlich und unterbricht das eintauchen.</span><span class="sxs-lookup"><span data-stu-id="8d925-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="8d925-360">Wir haben einige Zeit damit verbracht, ein physisch korrektes auslösverhalten darzustellen, und haben einige Richtlinien, die über Updates auf unserer Plattform aktiviert wurden, für Sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="8d925-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="8d925-361">Ein Beispiel für die Implementierung von "throw" finden Sie [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="8d925-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="8d925-362">Dieses Beispiel befolgt diese vier Richtlinien:</span><span class="sxs-lookup"><span data-stu-id="8d925-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="8d925-363">**Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position**.</span><span class="sxs-lookup"><span data-stu-id="8d925-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="8d925-364">Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn der [ungefähre Status der Positionsüberwachung ("ungefähre"](motion-controllers.md#controller-tracking-state)) ist.</span><span class="sxs-lookup"><span data-stu-id="8d925-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="8d925-365">In diesem Zustand werden Velocity-Informationen über den Controller weiterhin angezeigt, solange wir glauben, dass es sich um eine hohe Genauigkeit handelt, die häufig länger ist als die Position mit hoher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="8d925-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="8d925-366">**Integrieren Sie die *Winkelgeschwindigkeit* des Controllers**.</span><span class="sxs-lookup"><span data-stu-id="8d925-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="8d925-367">Diese Logik ist in der- `throwing.cs` Datei `GetThrownObjectVelAngVel` in der statischen-Methode innerhalb des oben verknüpften Pakets enthalten:</span><span class="sxs-lookup"><span data-stu-id="8d925-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="8d925-368">Wenn die Angular-Geschwindigkeit beibehalten wird, muss das ausgelöste Objekt dieselbe Angular-Geschwindigkeit wie in der Zeit der throw-Ausnahme beibehalten:`objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="8d925-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="8d925-369">Da sich der Mittelpunkt der Masse des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Ziehpunkt-Pose befindet, weist er wahrscheinlich eine andere Geschwindigkeit auf als der Controller im Verweis auf den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8d925-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="8d925-370">Der Teil der auf diese Weise beigetragenen Geschwindigkeit des Objekts ist die sofortige tangential Geschwindigkeit des Mittelpunkts der Masse des ausgelösten Objekts um den Controller Ursprung.</span><span class="sxs-lookup"><span data-stu-id="8d925-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="8d925-371">Diese tangential-Geschwindigkeit ist das Kreuz Produkt der Angular-Geschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controller Ursprung und dem Mittelpunkt der Masse des ausgelösten Objekts darstellt.</span><span class="sxs-lookup"><span data-stu-id="8d925-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="8d925-372">Die Gesamtgeschwindigkeit des ausgelösten Objekts entspricht daher der Summe der Geschwindigkeit des Controllers und der tangential Geschwindigkeit:`objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="8d925-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="8d925-373">Achten **Sie genau auf die *Zeit* , zu der wir die Geschwindigkeit anwenden**.</span><span class="sxs-lookup"><span data-stu-id="8d925-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="8d925-374">Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann.</span><span class="sxs-lookup"><span data-stu-id="8d925-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="8d925-375">Dies bedeutet Folgendes: Wenn Sie eine Änderung des Controller Zustands von "gedrückt" in "nicht gedrückt" oder umgekehrt abrufen, werden die Informationen, die Sie mit dem Controller erhalten, tatsächlich vor dieser Zustandsänderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d925-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="8d925-376">Außerdem wird die von unserer Abruf-API dargestellte Controller Darstellung vorhergesagt, um eine wahrscheinliche Darstellung zum Zeitpunkt der Anzeige des Frames widerzuspiegeln, der in der Zukunft mehr als 20 ms betragen kann.</span><span class="sxs-lookup"><span data-stu-id="8d925-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="8d925-377">Dies eignet sich gut  für das Rendern von gehaltenen Objekten, stellt jedoch unser Zeitproblem für das *Ziel des Objekts* dar</span><span class="sxs-lookup"><span data-stu-id="8d925-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="8d925-378">Wenn beim November-Update ein Unity-Ereignis wie *interaktionsourcepressed* oder *interaktionsourcereleasing* gesendet wird, enthält der Zustand die Vergangenheits Daten von hinten, wenn die Schaltfläche tatsächlich gedrückt oder freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="8d925-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="8d925-379">Um das präzisere Controller Rendering und die Zielplattform für das Ausführen von Triggeroptionen zu erhalten, müssen Sie nach Bedarf Abruf-und Ereignis Ereignisse ordnungsgemäß verwenden:</span><span class="sxs-lookup"><span data-stu-id="8d925-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="8d925-380">Für den Controller, der die einzelnen Frames rendert, sollte Ihre APP das *gameobject* des Controllers an der vorwärts Gesagten Controller **Darstellung** für die Photon-Zeit des aktuellen Frames positionieren.</span><span class="sxs-lookup"><span data-stu-id="8d925-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="8d925-381">Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. Inputtracking. getlocalposition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input. interaktionmanager. getcurrentreading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span><span class="sxs-lookup"><span data-stu-id="8d925-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="8d925-382">Für den Controller, der auf eine Presse oder ein Release **abzielt** , sollte Ihre APP auf der Grundlage der Verlaufs Controller-Pose für das Press-oder releaseereignis auf der Grundlage der Verlaufs Controller-</span><span class="sxs-lookup"><span data-stu-id="8d925-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="8d925-383">Sie erhalten diese Daten aus den Unity-Ereignis-APIs, wie z. b. *[interaktionmanager. interaktionsourcepressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span><span class="sxs-lookup"><span data-stu-id="8d925-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="8d925-384">**Verwenden Sie die**Ziehpunkt-Pose.</span><span class="sxs-lookup"><span data-stu-id="8d925-384">**Use the grip pose**.</span></span> <span data-ttu-id="8d925-385">Winkelgeschwindigkeit und-Geschwindigkeit werden relativ zur Zieh Punkt Pose, nicht zum Darstellen von Zeigern, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d925-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="8d925-386">Das auslösen wird mit zukünftigen Windows-Updates weiter verbessern, und Sie können davon ausgehen, dass Sie hier weitere Informationen finden.</span><span class="sxs-lookup"><span data-stu-id="8d925-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="8d925-387">Gesten-und Bewegungs Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="8d925-387">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="8d925-388">Sie können über den Eingabe-Manager auf Gesten-und Bewegungs Controller zugreifen.</span><span class="sxs-lookup"><span data-stu-id="8d925-388">You can access gesture and motion controller from the input Manager.</span></span> 
* [<span data-ttu-id="8d925-389">Geste in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="8d925-389">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="8d925-390">Motion Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="8d925-390">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="8d925-391">Befolgen Sie die Tutorials</span><span class="sxs-lookup"><span data-stu-id="8d925-391">Follow along with tutorials</span></span>

<span data-ttu-id="8d925-392">Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:</span><span class="sxs-lookup"><span data-stu-id="8d925-392">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="8d925-393">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="8d925-393">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="8d925-394">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="8d925-394">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="8d925-395">[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="8d925-395">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="8d925-396">*Mr-Eingabe 213-Motion Controller*</span><span class="sxs-lookup"><span data-stu-id="8d925-396">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="8d925-397">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8d925-397">See also</span></span>

* [<span data-ttu-id="8d925-398">Gesten</span><span class="sxs-lookup"><span data-stu-id="8d925-398">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="8d925-399">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="8d925-399">Motion controllers</span></span>](motion-controllers.md)


