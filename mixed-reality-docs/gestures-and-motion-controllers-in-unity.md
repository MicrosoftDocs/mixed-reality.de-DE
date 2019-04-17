---
title: Gesten und Motion-Controller in Unity
description: Es gibt zwei grundlegende Methoden für die Reaktion auf Ihre Blicke in Unity, gestensteuerung und Motion-Controller.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Bewegungen, während der Übertragung Controller, Unity, Blicke, Eingabe
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593288"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="8f056-104">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="8f056-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="8f056-105">Es gibt zwei grundlegende Methoden, Maßnahmen zu ergreifen, die auf Ihre [in Unity bestaunen](gaze-in-unity.md), [übergeben Gesten](gestures.md) und [motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="8f056-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="8f056-106">Die Daten für beide Quellen von räumlichen Eingabe greifen Sie über die gleichen APIs in Unity.</span><span class="sxs-lookup"><span data-stu-id="8f056-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="8f056-107">Unity bietet zwei bevorzugte Möglichkeiten auf räumlichen Daten für die Windows Mixed Reality, die allgemeine *Input.GetButton/Input.GetAxis* APIs, die über mehrere Unity-XR-SDKs, zusammenarbeiten und eine *InteractionManager / GestureRecognizer* API, die speziell für Windows Mixed Reality, die sämtliche räumliche Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="8f056-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="8f056-108">Unity-Schaltfläche/Achse-Zuordnungstabelle</span><span class="sxs-lookup"><span data-stu-id="8f056-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="8f056-109">Die Schaltfläche und die Achse-IDs in der folgenden Tabelle werden im Unity-Eingabe-Manager für Windows Mixed Reality-Motion-Controller durch den *Input.GetButton/GetAxis* -APIs, während die Spalte "MR für Windows-spezifische" auf Eigenschaften verweist verfügbar auf der *InteractionSourceState* Typ.</span><span class="sxs-lookup"><span data-stu-id="8f056-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="8f056-110">Jede dieser APIs werden in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8f056-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="8f056-111">Die Schaltfläche "/ Achse-ID-Zuordnungen für Windows Mixed Reality entsprechen im Allgemeinen die Oculus Schaltfläche/Achse-IDs.</span><span class="sxs-lookup"><span data-stu-id="8f056-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="8f056-112">Die Schaltfläche "/ Achse-ID-Zuordnungen für Windows Mixed Reality unterscheiden sich von OpenVRs Zuordnungen auf zwei Arten:</span><span class="sxs-lookup"><span data-stu-id="8f056-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="8f056-113">Die Zuordnung wird verwendet, Touchpad-IDs, die sich von Ministick, Controller mit Thumbsticks und Touchpad zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8f056-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="8f056-114">Die Zuordnung wird vermieden, überladen die Schaltfläche ein "und" X-IDs für die Menü-Schaltflächen, die für physische ABXY Schaltflächen verfügbar gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="8f056-115">Input</span><span class="sxs-lookup"><span data-stu-id="8f056-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="8f056-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="8f056-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="8f056-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="8f056-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="8f056-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows-MR-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="8f056-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="8f056-119">(XR.WSA.Input)</span><span class="sxs-lookup"><span data-stu-id="8f056-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="8f056-120">Links</span><span class="sxs-lookup"><span data-stu-id="8f056-120">Left hand</span></span> </th><th> <span data-ttu-id="8f056-121">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="8f056-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8f056-122">Select Trigger gedrückt</span><span class="sxs-lookup"><span data-stu-id="8f056-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="8f056-123">9 = 1.0-Achse</span><span class="sxs-lookup"><span data-stu-id="8f056-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="8f056-124">Axis 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="8f056-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="8f056-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="8f056-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-126">Wählen Sie analog Triggerwert</span><span class="sxs-lookup"><span data-stu-id="8f056-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="8f056-127">Achse 9</span><span class="sxs-lookup"><span data-stu-id="8f056-127">Axis 9</span></span> </td><td> <span data-ttu-id="8f056-128">Axis 10</span><span class="sxs-lookup"><span data-stu-id="8f056-128">Axis 10</span></span> </td><td> <span data-ttu-id="8f056-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="8f056-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-130">Select Trigger, die teilweise gedrückt.</span><span class="sxs-lookup"><span data-stu-id="8f056-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="8f056-131">Schaltfläche 14 <i>(Gamepad Compat)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8f056-132">Schaltfläche 15 <i>(Gamepad Compat)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8f056-133">SelectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="8f056-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-134">Menüschaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="8f056-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="8f056-135">Schaltfläche 6 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-135">Button 6\*</span></span> </td><td> <span data-ttu-id="8f056-136">Schaltfläche 7 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-136">Button 7\*</span></span> </td><td> <span data-ttu-id="8f056-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="8f056-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-138">Ziehpunkt ist gedrückt.</span><span class="sxs-lookup"><span data-stu-id="8f056-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="8f056-139">Achse 11 = 1.0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="8f056-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="8f056-140">Schaltfläche 4 <i>(Gamepad Compat)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8f056-141">Achse 12 = 1.0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="8f056-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="8f056-142">Schaltfläche 5 <i>(Gamepad Compat)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="8f056-143">Halten Sie</span><span class="sxs-lookup"><span data-stu-id="8f056-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-144">Ministick X <i>(linke: Bereich von -1,0, rechts: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="8f056-145">Axis 1</span><span class="sxs-lookup"><span data-stu-id="8f056-145">Axis 1</span></span> </td><td> <span data-ttu-id="8f056-146">Achse 4</span><span class="sxs-lookup"><span data-stu-id="8f056-146">Axis 4</span></span> </td><td> <span data-ttu-id="8f056-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="8f056-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-148">Ministick Y <i>(Top: Bereich von -1,0, unten: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="8f056-149">Achse 2</span><span class="sxs-lookup"><span data-stu-id="8f056-149">Axis 2</span></span> </td><td> <span data-ttu-id="8f056-150">Axis 5</span><span class="sxs-lookup"><span data-stu-id="8f056-150">Axis 5</span></span> </td><td> <span data-ttu-id="8f056-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="8f056-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-152">Ministick gedrückt</span><span class="sxs-lookup"><span data-stu-id="8f056-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="8f056-153">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="8f056-153">Button 8</span></span> </td><td> <span data-ttu-id="8f056-154">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="8f056-154">Button 9</span></span> </td><td> <span data-ttu-id="8f056-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="8f056-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-156">Touchpad X <i>(linke: Bereich von -1,0, rechts: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="8f056-157">Axis 17\*</span><span class="sxs-lookup"><span data-stu-id="8f056-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="8f056-158">Axis 19\*</span><span class="sxs-lookup"><span data-stu-id="8f056-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="8f056-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="8f056-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-160">Touchpad Y <i>(Top: Bereich von -1,0, unten: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="8f056-161">Axis 18\*</span><span class="sxs-lookup"><span data-stu-id="8f056-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="8f056-162">Achse 20 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="8f056-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="8f056-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-164">Touchpad berührt werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="8f056-165">Schaltfläche 18 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-165">Button 18\*</span></span> </td><td> <span data-ttu-id="8f056-166">Schaltfläche 19 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-166">Button 19\*</span></span> </td><td> <span data-ttu-id="8f056-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="8f056-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-168">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="8f056-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="8f056-169">Schaltfläche 16 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-169">Button 16\*</span></span> </td><td> <span data-ttu-id="8f056-170">Schaltfläche 17 \*</span><span class="sxs-lookup"><span data-stu-id="8f056-170">Button 17\*</span></span> </td><td> <span data-ttu-id="8f056-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="8f056-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-172">6DoF Ziehpunkt Haltung oder Zeiger Haltung</span><span class="sxs-lookup"><span data-stu-id="8f056-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="8f056-173"><i>Ziehpunkt</i> nur darstellen: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="8f056-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="8f056-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="8f056-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="8f056-175">Übergeben Sie <i>Ziehpunkt</i> oder <i>Zeiger</i> als Argument: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="8f056-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="8f056-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="8f056-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="8f056-177">Status der änderungsnachverfolgung</span><span class="sxs-lookup"><span data-stu-id="8f056-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="8f056-178"><i>Position Genauigkeit und Quelle Verlust Risiko nur MR-spezifische API erhältlich</i> </span><span class="sxs-lookup"><span data-stu-id="8f056-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="8f056-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="8f056-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="8f056-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="8f056-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="8f056-181">Diese Schaltfläche/Achse IDs unterscheiden sich von der IDs, die Unity für OpenVR aufgrund von Konflikten in den Zuordnungen von Gamepads, Oculus Touch und OpenVR verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8f056-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="8f056-182">Ziehpunkt Haltung im Vergleich zu zeigenden Haltung</span><span class="sxs-lookup"><span data-stu-id="8f056-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="8f056-183">Windows Mixed Reality unterstützt Controller, die während der Übertragung in einer Vielzahl von Formfaktoren, des Controllers Entwurf unterscheidet sich in der Beziehung zwischen Hand-Position des Benutzers und der natürliche "Weiterleiten" Richtung dieser apps sollten mit auf beim Rendern der Controller.</span><span class="sxs-lookup"><span data-stu-id="8f056-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="8f056-184">Um diese Controller besser darstellen zu können, es gibt zwei Arten von ist, können Sie für jede Datenquelle Interaktion untersuchen, der **Ziehpunkt Haltung** und **Zeiger Haltung**.</span><span class="sxs-lookup"><span data-stu-id="8f056-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="8f056-185">Sowohl der Ziehpunkt Haltung und Zeiger Haltung Koordinaten werden alle Unity-APIs in globalen Unity globalen Koordinaten angegeben.</span><span class="sxs-lookup"><span data-stu-id="8f056-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="8f056-186">Ziehpunkt Haltung</span><span class="sxs-lookup"><span data-stu-id="8f056-186">Grip pose</span></span>

<span data-ttu-id="8f056-187">Die **Ziehpunkt Haltung** stellt den Speicherort des dies im Handumdrehen einer Hand, die von einem HoloLens erkannt werden oder dies mit einem Controller während der Übertragung im Handumdrehen dar.</span><span class="sxs-lookup"><span data-stu-id="8f056-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="8f056-188">Für immersive Headsets, wird der Haltung Ziehpunkt am besten zum Rendern verwendet **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. eine "sword" oder dem damoklesschwert.</span><span class="sxs-lookup"><span data-stu-id="8f056-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="8f056-189">Der Ziehpunkt Haltung wird auch verwendet, bei der Visualisierung von eines Controllers während der Übertragung als die **zum Rendern Modell** bereitgestellten von Windows für eine Bewegung Controller als Ursprungs- und Mittelpunkt der Drehung der Ziehpunkt Haltung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f056-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="8f056-190">Der Ziehpunkt Haltung wird insbesondere wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="8f056-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="8f056-191">Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt.</span><span class="sxs-lookup"><span data-stu-id="8f056-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="8f056-192">Auf dem Windows Mixed Reality-Motion-Controller entspricht dieser Position in der Regel die Schaltfläche "verstehen".</span><span class="sxs-lookup"><span data-stu-id="8f056-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="8f056-193">Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)</span><span class="sxs-lookup"><span data-stu-id="8f056-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="8f056-194">Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.</span><span class="sxs-lookup"><span data-stu-id="8f056-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="8f056-195">Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.</span><span class="sxs-lookup"><span data-stu-id="8f056-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="8f056-196">Sie können auf den Ziehpunkt Haltung über anbieterübergreifende Eingabe für die entweder von Unity-API zugreifen (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) oder über die Windows-MR-spezifische API (*sourceState.sourcePose.TryGetPosition/Rotation*, Anfordern von Daten für darstellen der **Ziehpunkt** Knoten).</span><span class="sxs-lookup"><span data-stu-id="8f056-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="8f056-197">Zeiger Haltung</span><span class="sxs-lookup"><span data-stu-id="8f056-197">Pointer pose</span></span>

<span data-ttu-id="8f056-198">Die **Zeiger Haltung** stellt die Spitze des Controllers vorwärts verweist.</span><span class="sxs-lookup"><span data-stu-id="8f056-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="8f056-199">Die vom System bereitgestellte Zeiger Haltung ist am besten zum Raycast verwendet, wenn Sie können **das Controllermodell selbst rendern**.</span><span class="sxs-lookup"><span data-stu-id="8f056-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="8f056-200">Wenn Sie ein anderes virtuelles Objekt anstelle der Controller, z. B. eine virtuelle damoklesschwert, rendern sollten Sie mit einem Strahl verweisen, die für diese virtuellen Objekts, z. B. ein Strahl, die entlang der Lauf der app definierte damoklesschwert Modell geleitet.</span><span class="sxs-lookup"><span data-stu-id="8f056-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="8f056-201">Da Benutzer die virtuelles Objekt und nicht auf dem physischen Controller sehen können, werden zeigen mit dem virtuellen Objekt natürlichere für Benutzer, die Ihre app Sie wahrscheinlich.</span><span class="sxs-lookup"><span data-stu-id="8f056-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="8f056-202">Der Zeiger Haltung ist derzeit verfügbar in Unity nur über die Windows-MR-spezifische-API, *sourceState.sourcePose.TryGetPosition/Rotation*, und übergeben Sie *InteractionSourceNode.Pointer* wie die Argument.</span><span class="sxs-lookup"><span data-stu-id="8f056-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="8f056-203">Status der Controller-änderungsnachverfolgung</span><span class="sxs-lookup"><span data-stu-id="8f056-203">Controller tracking state</span></span>

<span data-ttu-id="8f056-204">Wie bei der Headsets muss die Windows Mixed Reality-Motion-Controller keine Einrichtung der externen Überwachung Sensoren.</span><span class="sxs-lookup"><span data-stu-id="8f056-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="8f056-205">Stattdessen werden die Controller von Sensoren in den Kopfhörer selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="8f056-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="8f056-206">Wenn der Benutzer aus den Kopfhörer des Sichtfelds Controller verschoben wird, wird in den meisten Fällen Windows weiterhin Positionen von Controller ableiten und Dokumente für die app bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8f056-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="8f056-207">Wenn der Controller verloren hat visual nachverfolgung für lange genug, des Controllers Positionen an ungefähren Genauigkeit Positionen gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="8f056-208">An diesem Punkt werden Body-Sperre den Controller für den Benutzer, die Position des Benutzers nachverfolgen, wie sie beim Verfügbarmachen immer noch auf "true" des Controllers-Ausrichtung mit der internen Ausrichtung Sensoren, verschieben.</span><span class="sxs-lookup"><span data-stu-id="8f056-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="8f056-209">Viele apps, die auf verweisen, und aktivieren die Elemente der Benutzeroberfläche mithilfe von verwaltungscontrollern können normalerweise ungefähre Genauigkeit im bemerken die Benutzer arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8f056-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="8f056-210">Die beste Möglichkeit, ein Gefühl dafür ist, um es selbst auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="8f056-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="8f056-211">Sehen Sie sich dieses Video mit Beispielen für die immersiven Inhalte, die während der Übertragung mit verschiedenen Status der Überwachung funktioniert:</span><span class="sxs-lookup"><span data-stu-id="8f056-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="8f056-212">Schlussfolgerungen über zustandsnachverfolgung explizit</span><span class="sxs-lookup"><span data-stu-id="8f056-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="8f056-213">Apps, die Positionen, die je nach der zustandsnachverfolgung unterschiedlich behandeln möchten möglicherweise weiter gehen und überprüfen Sie die Eigenschaften des controllerzustands, z. B. *SourceLossRisk* und *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="8f056-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="8f056-214">Status der änderungsnachverfolgung</span><span class="sxs-lookup"><span data-stu-id="8f056-214">Tracking state</span></span> </th><th> <span data-ttu-id="8f056-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="8f056-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="8f056-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="8f056-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="8f056-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="8f056-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8f056-218"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="8f056-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="8f056-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="8f056-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8f056-220">Hoch</span><span class="sxs-lookup"><span data-stu-id="8f056-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8f056-221">true</span><span class="sxs-lookup"><span data-stu-id="8f056-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-222"><b>Hohe Genauigkeit (Risiko der verlierenden)</b> </span><span class="sxs-lookup"><span data-stu-id="8f056-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="8f056-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="8f056-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8f056-224">Hoch</span><span class="sxs-lookup"><span data-stu-id="8f056-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8f056-225">true</span><span class="sxs-lookup"><span data-stu-id="8f056-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-226"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="8f056-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="8f056-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="8f056-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="8f056-228">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="8f056-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="8f056-229">true</span><span class="sxs-lookup"><span data-stu-id="8f056-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8f056-230"><b>Keine position</b> </span><span class="sxs-lookup"><span data-stu-id="8f056-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="8f056-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="8f056-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="8f056-232">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="8f056-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="8f056-233">false</span><span class="sxs-lookup"><span data-stu-id="8f056-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="8f056-234">Statusdefinitionen nachverfolgung während der Übertragung Controller sind wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="8f056-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="8f056-235">**Hoher Genauigkeit:** Während sich der Controller während der Übertragung in den Kopfhörer des Sichtfelds, erhalten sie in der Regel hohe Genauigkeit Positionen, basierend auf visuelle Verfolgung.</span><span class="sxs-lookup"><span data-stu-id="8f056-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="8f056-236">Beachten Sie, dass ein verschieben Controller, die vorübergehend das Sichtfeld verlässt oder vorübergehend von der Kopfhörer Sensoren verdeckt wird (z. B. durch der Benutzer der anderen Hand) wird weiterhin hoch-Genauigkeit ist für kurze Zeit, basierend auf Trägheit nachverfolgung des Controllers zurück sich selbst.</span><span class="sxs-lookup"><span data-stu-id="8f056-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="8f056-237">**Hohe Genauigkeit (Risiko der verlierenden):** Wenn der Benutzer den Controller während der Übertragung über den Rand der Kopfhörer des Sichtfelds bewegt, den Kopfhörer visuell des Controllers Position kann nicht in Kürze.</span><span class="sxs-lookup"><span data-stu-id="8f056-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="8f056-238">Die app erkennt, wenn der Controller diese Grenze Blickfeld von angezeigt erreicht hat die **SourceLossRisk** 1.0 zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="8f056-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="8f056-239">An diesem Punkt können die app Controller-Gesten anhalten, die einem stetigen Strom an sehr hoher Qualität ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8f056-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="8f056-240">**Ungefähre Genauigkeit:** Wenn der Controller verloren hat visual nachverfolgung für lange genug, des Controllers Positionen an ungefähren Genauigkeit Positionen gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="8f056-241">An diesem Punkt werden Body-Sperre den Controller für den Benutzer, die Position des Benutzers nachverfolgen, wie sie beim Verfügbarmachen immer noch auf "true" des Controllers-Ausrichtung mit der internen Ausrichtung Sensoren, verschieben.</span><span class="sxs-lookup"><span data-stu-id="8f056-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="8f056-242">Viele apps, die mithilfe von verwaltungscontrollern, zeigen Sie auf, und aktivieren die Elemente der Benutzeroberfläche können als normale Zeit mit einer Genauigkeit von ungefähren im bemerken die Benutzer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="8f056-243">Apps mit geringeres Routingaufkommen eingabeanforderungen können diese Verringerung von erkennen **hohe** Genauigkeit **ungefähr** Genauigkeit durch Überprüfen der **PositionAccuracy** -Eigenschaft für Beispiel: um dem Benutzer eine großzügigeren Hitbox auf außerhalb des Bildschirms Zielen während dieser Zeit geben.</span><span class="sxs-lookup"><span data-stu-id="8f056-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="8f056-244">**Keine Position:** Während der Controller auf ungefähre Genauigkeit für einen langen Zeitraum ausgeführt werden kann, weiß das System manchmal, dass auch eine Text-locked Position im Moment nicht aussagekräftig ist.</span><span class="sxs-lookup"><span data-stu-id="8f056-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="8f056-245">Z. B. ein Controller, der nur eingeschaltet wurde möglicherweise nie beobachtet wurde visuell, oder Sie einen Controller, der dann von einer anderen Person übernommen wird ein Benutzer festlegen kann.</span><span class="sxs-lookup"><span data-stu-id="8f056-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="8f056-246">Zu diesen Zeitpunkten, wird das System keine einer beliebigen Position, an die app bereitgestellt und *TryGetPosition* wird "false" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8f056-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="8f056-247">Allgemeine Unity-APIs (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="8f056-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="8f056-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="8f056-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="8f056-249">**Typen**: *Input*, *XR.InputTracking*</span><span class="sxs-lookup"><span data-stu-id="8f056-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="8f056-250">Unity verwendet derzeit der allgemeinen *Input.GetButton/Input.GetAxis* APIs, um die Eingabe für verfügbar zu machen [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich praktische und Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="8f056-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="8f056-251">Wenn Ihre app diese APIs für die Eingabe verwendet, kann es ganz einfach während der Übertragung Controller über mehrere XR-SDKs, darunter Windows Mixed Reality unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8f056-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="8f056-252">Abrufen einer logischen Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="8f056-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="8f056-253">Um die allgemeine Unity Eingabe-APIs verwenden zu können, Sie in der Regel beginnen verknüpfen Sie zuerst die Schaltflächen und verwendet, um den logischen Namen in der [Unity Input Managers](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binden eine Schaltfläche oder ein Achse IDs, die jedem Namen.</span><span class="sxs-lookup"><span data-stu-id="8f056-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="8f056-254">Anschließend können Sie Code schreiben, die auf diesem logischen Schaltfläche/Achse Namen verweist.</span><span class="sxs-lookup"><span data-stu-id="8f056-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="8f056-255">Wechseln Sie zum Beispiel zum Zuordnen des linken Motion-Controllers-Schaltfläche "Trigger" auf die Aktion senden zu **Bearbeiten > Projekteinstellungen > Eingabe** in Unity, und erweitern Sie die Eigenschaften der Abschnitt "übermitteln" unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="8f056-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="8f056-256">Ändern der **positive Schaltfläche** oder **Alt Positive Schaltfläche** -Eigenschaft in **Joystick Schaltfläche 14**, wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8f056-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="8f056-257">![Unity InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="8f056-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="8f056-258">*Unity InputManager*</span></span>

<span data-ttu-id="8f056-259">Ihr Skript kann dann das Kontrollkästchen für die senden-Aktion mit *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="8f056-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="8f056-260">Sie können mehr logische Schaltflächen hinzufügen, durch Ändern der **Größe** Eigenschaft **Achsen**.</span><span class="sxs-lookup"><span data-stu-id="8f056-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="8f056-261">Eine Taste gedrückt abrufen direkt</span><span class="sxs-lookup"><span data-stu-id="8f056-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="8f056-262">Sie können Schaltflächen auch manuell zugreifen, indem Sie ihre vollqualifizierten Namen *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="8f056-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="8f056-263">Abrufen einer Hand oder während der Übertragung des Controllers Haltung</span><span class="sxs-lookup"><span data-stu-id="8f056-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="8f056-264">Sie können Zugriff auf die Position und Drehung des Controllers, mithilfe von *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="8f056-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="8f056-265">Beachten Sie, dass dies des Controllers Ziehpunkt-Haltung (, in denen der Benutzer auf den Controller gespeichert), dies ist hilfreich stellt für das Rendern einer "sword" oder damoklesschwert des Benutzers manuell oder ein Modell für den Controller selbst.</span><span class="sxs-lookup"><span data-stu-id="8f056-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="8f056-266">Beachten Sie, dass die Beziehung zwischen dieser Ziehpunkt Haltung und der Zeiger Haltung (, auf die Spitze des Controllers verweist), die auf Controller abweichen kann.</span><span class="sxs-lookup"><span data-stu-id="8f056-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="8f056-267">Zu diesem Zeitpunkt ist nur den Zugriff auf die Zeiger Haltung des Controllers durch die Eingabe MR-spezifische API, die in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8f056-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="8f056-268">Windows-spezifische APIs (XR. WSA. Eingabe)</span><span class="sxs-lookup"><span data-stu-id="8f056-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="8f056-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="8f056-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="8f056-270">**Typen**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="8f056-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="8f056-271">Um weitere detaillierte Informationen zu Windows Mixed Reality-Hand-Eingabe (für HoloLens) und der Motion-Controller zu erhalten, können Sie die Windows-spezifische räumliche Eingabe-APIs unter dem *UnityEngine.XR.WSA.Input* Namespace.</span><span class="sxs-lookup"><span data-stu-id="8f056-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="8f056-272">Dadurch können Sie den Zugriff auf zusätzliche Informationen, z. B. Position Genauigkeit oder der datenquellenart, können Sie die praktische und Controller auseinander zu informieren.</span><span class="sxs-lookup"><span data-stu-id="8f056-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="8f056-273">Für den Status von Hand und Motion-Controllern abrufen</span><span class="sxs-lookup"><span data-stu-id="8f056-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="8f056-274">Sie können Abfragen für diesen Frame des Status der Quelle (manuell oder durch Motion-Controller) für jede Interaktion mithilfe der *GetCurrentReading* Methode.</span><span class="sxs-lookup"><span data-stu-id="8f056-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="8f056-275">Jede *InteractionSourceState* man Back stellt eine Quelle für die Interaktion zu den aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="8f056-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="8f056-276">Die *InteractionSourceState* Informationen wie z. B. macht:</span><span class="sxs-lookup"><span data-stu-id="8f056-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="8f056-277">Die [Arten von drückt](motion-controllers.md) auftreten (Select/Menü/verstehen/Touchpad/Ministick)</span><span class="sxs-lookup"><span data-stu-id="8f056-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="8f056-278">Andere Daten, die spezifisch für Motion-Controller, solche Touchpad und/oder des Ministick XY-Koordinaten und berührt Zustand</span><span class="sxs-lookup"><span data-stu-id="8f056-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="8f056-279">Die InteractionSourceKind wissen, ob die Quelle einer Hand oder einen Controller während der Übertragung ist</span><span class="sxs-lookup"><span data-stu-id="8f056-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="8f056-280">Abrufen der Forward-vorhergesagt Rendering ist</span><span class="sxs-lookup"><span data-stu-id="8f056-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="8f056-281">Bei der Interaktion von Quelldaten von Hand und Controller abrufen, sind die ist, erhalten Sie Forward-vorhergesagt ist für den Moment, in der Zeit des Frames Photonen des Benutzers Augen erreichen werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="8f056-282">Diese ist vorwärts-vorhergesagt werden am besten zum **Rendering** der Controller oder einem vorhandenen Objekt jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="8f056-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="8f056-283">Wenn Sie als Ziel das Drücken einer bestimmten oder mit dem Controller freizugeben, ist, die werden möglichst präzise, wenn Sie den historische Ereignis unten beschriebenen APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f056-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="8f056-284">Sie können auch die Forward-vorhergesagt Head Haltung für diesen aktuellen Frame abrufen.</span><span class="sxs-lookup"><span data-stu-id="8f056-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="8f056-285">Wie bei der Quelle Haltung, dies nützlich für **Rendering** einen Cursor, jedoch auf einem angegebenen drücken oder Release möglichst präzise, wenn Sie den historische Ereignis unten beschriebenen APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f056-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="8f056-286">Behandeln von Ereignissen der Interaktion-Quelle</span><span class="sxs-lookup"><span data-stu-id="8f056-286">Handling interaction source events</span></span>

<span data-ttu-id="8f056-287">Um Eingabeereignisse zu behandeln, wie sie mit ihren Daten genau historische Haltung auftreten, können Sie die Interaktion quellenereignisse anstelle einer Abruf behandeln.</span><span class="sxs-lookup"><span data-stu-id="8f056-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="8f056-288">Um die Interaktion quellenereignisse behandeln:</span><span class="sxs-lookup"><span data-stu-id="8f056-288">To handle interaction source events:</span></span>
* <span data-ttu-id="8f056-289">Registrieren Sie sich für eine *InteractionManager* Eingabeereignis.</span><span class="sxs-lookup"><span data-stu-id="8f056-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="8f056-290">Für jeden Typ von Interaktion-Ereignis, das Sie interessiert sind, müssen Sie abonnieren.</span><span class="sxs-lookup"><span data-stu-id="8f056-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="8f056-291">Behandeln des Ereignisses an.</span><span class="sxs-lookup"><span data-stu-id="8f056-291">Handle the event.</span></span> <span data-ttu-id="8f056-292">Nachdem Sie auf ein Ereignis für die Interaktion abonniert haben, erhalten Sie den Rückruf bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="8f056-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="8f056-293">In der *SourcePressed* beispielsweise diese werden nach die Quelle erkannt wurde und bevor sie veröffentlicht oder verloren gegangen ist.</span><span class="sxs-lookup"><span data-stu-id="8f056-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="8f056-294">Gewusst wie: Behandeln eines Ereignisses zu beenden</span><span class="sxs-lookup"><span data-stu-id="8f056-294">How to stop handling an event</span></span>

<span data-ttu-id="8f056-295">Sie müssen beenden Behandeln eines Ereignisses, wenn Sie nicht mehr Interesse am Ereignis sind aus, oder Sie werden zerstört, das Objekt, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="8f056-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="8f056-296">Um das Ereignis zu beenden, kündigen Sie das Ereignis ein.</span><span class="sxs-lookup"><span data-stu-id="8f056-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="8f056-297">Liste der Ereignisse der Benutzerinteraktion-Quelle</span><span class="sxs-lookup"><span data-stu-id="8f056-297">List of interaction source events</span></span>

<span data-ttu-id="8f056-298">Die mögliche Interaktion Quellereignisse sind:</span><span class="sxs-lookup"><span data-stu-id="8f056-298">The available interaction source events are:</span></span>
* <span data-ttu-id="8f056-299">*InteractionSourceDetected* (Quelle aktiv)</span><span class="sxs-lookup"><span data-stu-id="8f056-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="8f056-300">*InteractionSourceLost* (inaktiv)</span><span class="sxs-lookup"><span data-stu-id="8f056-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="8f056-301">*InteractionSourcePressed* (Tap, drücken Sie die Schaltfläche oder "Select", wenn)</span><span class="sxs-lookup"><span data-stu-id="8f056-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="8f056-302">*InteractionSourceReleased* (Ende einer Tap, losgelassen wurde, oder Ende von "Select", wenn)</span><span class="sxs-lookup"><span data-stu-id="8f056-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="8f056-303">*InteractionSourceUpdated* (verschiebt oder einen Zustand, der auf andere Weise ändert.)</span><span class="sxs-lookup"><span data-stu-id="8f056-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="8f056-304">Ereignisse für Verlaufsdaten für die Zielgruppenadressierung ist, die am genauesten ein drücken oder ein Release entsprechen</span><span class="sxs-lookup"><span data-stu-id="8f056-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="8f056-305">Die zuvor beschriebenen Abrufvorgänge-APIs Geben Sie Ihrer app ist vorwärts-vorhergesagt.</span><span class="sxs-lookup"><span data-stu-id="8f056-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="8f056-306">Während die vorhergesagten ist für das Rendern der Controller oder ein virtuelles handheld-Objekt am besten geeignet sind, sind zukünftige ist nicht optimal für die Zielplattform, für die zwei wichtigsten Gründe:</span><span class="sxs-lookup"><span data-stu-id="8f056-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="8f056-307">Bei der Benutzer auf einem Domänencontroller eine Schaltfläche klickt, kann es möglicherweise ungefähr 20 ms Latenz der drahtlose per Bluetooth, bevor das System, drücken Sie die empfängt.</span><span class="sxs-lookup"><span data-stu-id="8f056-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="8f056-308">Dann, wenn Sie eine Vorwärts-vorhergesagt Haltung, es verwenden eine andere 10-20-ms forward Vorhersage angewendet werden würde, wenn der aktuelle Frame Photonen des Benutzers Augen erreichen, wird, die Zeit als Ziel.</span><span class="sxs-lookup"><span data-stu-id="8f056-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="8f056-309">Dies bedeutet, dass der Abruf erhalten Sie eine Quelle Haltung oder Head darstellen, d. h. 30-40ms Weiterleiten von, Head und die Hände des Benutzers tatsächlich waren zurück, wenn Sie dem drücken oder Release ausgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="8f056-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="8f056-310">Für HoloLens Hand Eingabe-es gibt zwar keine Verzögerung drahtlosen Übertragung besteht ähnliche Verzögerungen bei der Verarbeitung, drücken Sie die zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="8f056-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="8f056-311">Zu genau Ziel basierend auf die ursprüngliche Absicht des Benutzers, für das Drücken einer Hand oder Controller, sollten Sie verwenden, die historische Quelle Haltung oder Head Haltung, *InteractionSourcePressed* oder *InteractionSourceReleased* Eingabeereignis.</span><span class="sxs-lookup"><span data-stu-id="8f056-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="8f056-312">Sie können Drücken einer als Ziel oder release mit historischen Haltung Daten des Benutzers Head oder ihre Controller:</span><span class="sxs-lookup"><span data-stu-id="8f056-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="8f056-313">Die Head Haltung zu dem Zeitpunkt eine Geste oder einen Controller beim Drücken aufgetreten ist, kann für verwendet werden **für** um zu bestimmen, was der Benutzer war [gazing](gaze.md) an:</span><span class="sxs-lookup"><span data-stu-id="8f056-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

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

* <span data-ttu-id="8f056-314">Die Quelle Haltung zu dem Zeitpunkt beim Drücken von eines Controllers während der Übertragung aufgetreten ist, kann für verwendet werden **für** um zu bestimmen, was der Benutzer den Controller in gezeigt wurde.</span><span class="sxs-lookup"><span data-stu-id="8f056-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="8f056-315">Dies ist der Zustand des Controllers wird, das Drücken das aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="8f056-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="8f056-316">Wenn Sie den Controller selbst rendern, können Sie anfordern, der Haltung Zeiger anstelle der Ziehpunkt Haltung, vorgesehen für die Zielgruppenadressierung Strahl von was der Benutzer die natürliche Tipps und Tricks, die Controller gerendert berücksichtigt wird:</span><span class="sxs-lookup"><span data-stu-id="8f056-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="8f056-317">Beispiel für Ereignis-Handler</span><span class="sxs-lookup"><span data-stu-id="8f056-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="8f056-318">Allgemeine zusammengesetzten Geste APIs (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="8f056-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="8f056-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="8f056-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="8f056-320">**Typen**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="8f056-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="8f056-321">Ihre app kann auch zusammengesetzte Gesten für räumliche Eingabequellen, tippen Sie auf, anhalten, Bearbeitung und Navigation Gesten erkennen.</span><span class="sxs-lookup"><span data-stu-id="8f056-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="8f056-322">Erkennen Sie diese zusammengesetzten Gesten in beiden [Hände](gestures.md) und [motion Controller](motion-controllers.md) mithilfe der GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="8f056-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="8f056-323">Jedes Ereignis Bewegung auf die GestureRecognizer bietet die SourceKind für die Eingabe als auch für die Zielgruppenadressierung anhand bestimmter Head Chow zum Zeitpunkt des Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="8f056-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="8f056-324">Einige Ereignisse bieten zusätzliche Kontextinformationen bestimmte.</span><span class="sxs-lookup"><span data-stu-id="8f056-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="8f056-325">Es gibt nur wenige Schritte erforderlich, um eine Stiftbewegungs-Erkennung mit Gesten erfasst:</span><span class="sxs-lookup"><span data-stu-id="8f056-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="8f056-326">Erstellen einer neuen Stiftbewegungs-Erkennung</span><span class="sxs-lookup"><span data-stu-id="8f056-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="8f056-327">Geben Sie die Gesten für die Überwachung</span><span class="sxs-lookup"><span data-stu-id="8f056-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="8f056-328">Abonnieren von Ereignissen für diese Gesten</span><span class="sxs-lookup"><span data-stu-id="8f056-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="8f056-329">Startet das Sammeln von Gesten</span><span class="sxs-lookup"><span data-stu-id="8f056-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="8f056-330">Erstellen einer neuen Stiftbewegungs-Erkennung</span><span class="sxs-lookup"><span data-stu-id="8f056-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="8f056-331">Verwenden der *GestureRecognizer*, müssen Sie erstellt haben eine *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="8f056-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="8f056-332">Geben Sie die Gesten für die Überwachung</span><span class="sxs-lookup"><span data-stu-id="8f056-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="8f056-333">Angeben, welche Aktionen, die Sie über interessiert sind *SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="8f056-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="8f056-334">Abonnieren von Ereignissen für diese Gesten</span><span class="sxs-lookup"><span data-stu-id="8f056-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="8f056-335">Abonnieren Sie Ereignisse für die Gesten, die, denen Sie interessieren.</span><span class="sxs-lookup"><span data-stu-id="8f056-335">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="8f056-336">Datennavigation und-Bearbeitung Gesten sind in einer Instanz von sich gegenseitig ausschließende eine *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="8f056-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="8f056-337">Startet das Sammeln von Gesten</span><span class="sxs-lookup"><span data-stu-id="8f056-337">Start capturing gestures</span></span>

<span data-ttu-id="8f056-338">Standardmäßig eine *GestureRecognizer* überwacht keine Eingabe bis *StartCapturingGestures()* aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8f056-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="8f056-339">Es ist möglich, dass eine Geste-Ereignis nach dem generiert möglicherweise *StopCapturingGestures()* wird aufgerufen, wenn die Eingabe vor dem Frame ausgeführt wurde, in denen *StopCapturingGestures()* verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="8f056-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="8f056-340">Die *GestureRecognizer* speichert, ob es aktiviert oder deaktiviert, während die vorherige-Frames in der die Aktion tatsächlich aufgetreten ist war, und daher sie zuverlässig ist, um zu starten und beenden Geste Überwachung basierend auf des Frames Blicke für.</span><span class="sxs-lookup"><span data-stu-id="8f056-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="8f056-341">Aufzeichnung der Aktionen wird beendet</span><span class="sxs-lookup"><span data-stu-id="8f056-341">Stop capturing gestures</span></span>

<span data-ttu-id="8f056-342">So beenden Sie die gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="8f056-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="8f056-343">Entfernen eine stiftbewegungs-Erkennung</span><span class="sxs-lookup"><span data-stu-id="8f056-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="8f056-344">Denken Sie daran, die abonnierten Ereignisse vor dem Zerstören abbestellen eine *GestureRecognizer* Objekt.</span><span class="sxs-lookup"><span data-stu-id="8f056-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="8f056-345">Rendern von der Motion-Controllermodell in Unity</span><span class="sxs-lookup"><span data-stu-id="8f056-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="8f056-346">![Während der Übertragung Controllermodell und teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="8f056-347">*Während der Übertragung Controllermodell und teleportation*</span><span class="sxs-lookup"><span data-stu-id="8f056-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="8f056-348">Um während der Übertragung von Domänencontrollern in Ihrer app zu rendern, die die physischen Controller entsprechen, Ihre Benutzer enthalten sind, und Erläutern Sie, wie verschiedene-Taste gedrückt werden, können Sie die **MotionController Prefab** in die [Mixed Reality-Toolkit ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="8f056-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="8f056-349">Diese Prefab lädt das richtige GlTF Modell zur Laufzeit dynamisch aus dem System installierten während der Übertragung Controllertreiber.</span><span class="sxs-lookup"><span data-stu-id="8f056-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="8f056-350">Es ist wichtig, diese Modelle dynamisch zu laden, statt Sie möglicherweise importieren manuell im Editor, damit Ihre app physisch genau-3D-Modelle für alle aktuellen und zukünftigen Controller Ihren Benutzern angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8f056-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="8f056-351">Führen Sie die [Einstieg](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Anweisungen zum Herunterladen von Mixed Reality Toolkit und Ihr Unity-Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8f056-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="8f056-352">Wenn Sie die Kamera mit ersetzt die *MixedRealityCameraParent* prefab als Teil der Schritte zum Einstieg können Sie schon fertig!</span><span class="sxs-lookup"><span data-stu-id="8f056-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="8f056-353">Diese Prefab enthält die Motion-Controller-Rendering.</span><span class="sxs-lookup"><span data-stu-id="8f056-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="8f056-354">Fügen Sie andernfalls *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* in die Szene im Projekt-Bereich.</span><span class="sxs-lookup"><span data-stu-id="8f056-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="8f056-355">Sie sollten hinzufügen, als untergeordnetes Element des beliebige übergeordneten Objekts prefab verwenden, um die Kamera um beim Verschieben der Teleports Benutzer innerhalb der Szene, so, dass die Controller zusammen mit der Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8f056-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="8f056-356">Wenn Ihre app keine Teleporting verbunden ist, müssen Sie einfach fügen Sie das Prefab im Stammverzeichnis Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="8f056-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="8f056-357">Auslösen von Objekten</span><span class="sxs-lookup"><span data-stu-id="8f056-357">Throwing objects</span></span>

<span data-ttu-id="8f056-358">Auslösen von Objekten in virtuelle Realität wird ein schwierigeres Problem, und klicken Sie dann Es mag zunächst.</span><span class="sxs-lookup"><span data-stu-id="8f056-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="8f056-359">Wie bei der am häufigsten physisch basierend Interaktionen, wenn im Spiel fungiert ein unerwartetes Verhalten auslösen, es ist sofort ersichtlich und Immersion unterbrochen.</span><span class="sxs-lookup"><span data-stu-id="8f056-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="8f056-360">Wir haben damit verbracht, einige nachgedacht tief zum Darstellen eines physisch richtigen auslösenden Verhaltens, und einige Richtlinien, die über Updates unserer Plattform, die wir für Sie freigeben möchten, die aktiviert werden, erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="8f056-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="8f056-361">Sie finden ein Beispiel, wie es wird, zum Auslösen von implementieren empfohlen [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="8f056-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="8f056-362">In diesem Beispiel folgt vier Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8f056-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="8f056-363">**Verwenden des Controllers *Geschwindigkeit* anstatt der Position**.</span><span class="sxs-lookup"><span data-stu-id="8f056-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="8f056-364">Im November-Update, Windows, wir eine Änderung im Verhalten eingeführt, in der ["Ermitteln" mit Feldern fester Breite Nachverfolgungsstatus](motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="8f056-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="8f056-365">In diesem Zustand weiterhin Geschwindigkeit Informationen zum Controller für gemeldet werden, solange wir, dass es hoher Genauigkeit, der was häufig bei länger glauben ist als die Position des hoher Genauigkeit bleibt.</span><span class="sxs-lookup"><span data-stu-id="8f056-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="8f056-366">**Integrieren der *Winkelgeschwindigkeit* des Controllers**.</span><span class="sxs-lookup"><span data-stu-id="8f056-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="8f056-367">Diese Logik ist enthalten die `throwing.cs` Datei die `GetThrownObjectVelAngVel` statische Methode, in dem Paket, das weiter oben Bezug genommen:</span><span class="sxs-lookup"><span data-stu-id="8f056-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="8f056-368">Wie die Winkelgeschwindigkeit konserviert ist, muss das ausgelöste Objekt die gleichen Winkelgeschwindigkeit, wie er zu dem Zeitpunkt ausgelöst hatte verwalten: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="8f056-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="8f056-369">Als Mittelpunkt der Masse des-Objekts ausgelöst wird, wahrscheinlich nicht auf den Ursprung des der Ziehpunkt Haltung, es wahrscheinlich eine andere Geschwindigkeit, des Controllers in der Verweisrahmen des Benutzers hat ist.</span><span class="sxs-lookup"><span data-stu-id="8f056-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="8f056-370">Der Teil des Objekts Geschwindigkeit beigetragen haben, auf diese Weise wird die sofortige tangential Geschwindigkeit der Mittelpunkt der Masse der das Objekt ausgelöst wird, um den Ursprung der Controller.</span><span class="sxs-lookup"><span data-stu-id="8f056-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="8f056-371">Diese tangential Geschwindigkeit ist das Kreuzprodukt die Winkelgeschwindigkeit des Controllers mit der Vektor, die den Abstand zwischen dem Controller-Ursprung und der Mittelpunkt der-Masse des-Objekts ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="8f056-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="8f056-372">Die gesamte Geschwindigkeit des das ausgelöste Objekt ist die Summe der Geschwindigkeit des Controllers und diese tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="8f056-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="8f056-373">**Achten Sie besonders auf die *Zeit* an dem wir die Geschwindigkeit anwenden**.</span><span class="sxs-lookup"><span data-stu-id="8f056-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="8f056-374">Wenn eine Schaltfläche geklickt wird, dauert es bis zu 20 ms für das Ereignis über Bluetooth an das Betriebssystem Bubbling.</span><span class="sxs-lookup"><span data-stu-id="8f056-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="8f056-375">Dies bedeutet, dass, wenn der Abruf für eine statusänderung der Controller aus aufgerufen wird, als nicht gedrückt bzw. umgekehrt, Controller Haltung Informationen, die mit ihm Sie erhalten tatsächlich werden vor dieser Änderung am Zustand.</span><span class="sxs-lookup"><span data-stu-id="8f056-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="8f056-376">Darüber hinaus wird der Controller Haltung angezeigt, die durch unsere API-Abruf vorwärts vorhergesagt, entsprechend einem wahrscheinlich Haltung zum Zeitpunkt der Rahmen angezeigt wird die weitere 20 ms. Klicken Sie dann in der Zukunft sein könnte.</span><span class="sxs-lookup"><span data-stu-id="8f056-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="8f056-377">Dies eignet sich gut für *Rendering* frei, die Objekte, aber auch unser Problem Zeit für *für* das Objekt wie wir die Kurve für den Moment berechnen veröffentlicht die Benutzer ihre auslösen.</span><span class="sxs-lookup"><span data-stu-id="8f056-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="8f056-378">Erfreulicherweise haben Sie mit der November-Update, wenn ein Unity-Ereignis wie *InteractionSourcePressed* oder *InteractionSourceReleased* gesendet wird, wird dieser Status umfasst die historischen Haltung Daten aus zurück, wenn die Schaltfläche " wurde tatsächlich gedrückt oder losgelassen.</span><span class="sxs-lookup"><span data-stu-id="8f056-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="8f056-379">Um möglichst genaue Controller-Rendering und Controller während der löst Zielgruppenadressierung zu erhalten, müssen Sie ordnungsgemäß Abruf- und Ereignisse, nach Bedarf verwenden:</span><span class="sxs-lookup"><span data-stu-id="8f056-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="8f056-380">Für **Controller Rendering** jeden Frame, positionieren Sie Ihre app sollte des Controllers *"gameobject"* auf Controllerebene Forward-vorhergesagt darstellen, für den aktuellen Frame Photon Zeit.</span><span class="sxs-lookup"><span data-stu-id="8f056-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="8f056-381">Sie erhalten diese Daten von Unity Abrufvorgänge APIs wie *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="8f056-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="8f056-382">Für **Controller als Ziel** anhand eines drücken oder die Version, Ihre app sollte Raycast und herabstürzendes basierend auf den historischen Controller Haltung für dieses Ereignis drücken oder Release zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="8f056-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="8f056-383">Sie erhalten diese Daten von der ereignisverwaltung der Unity-APIs, z. B.  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="8f056-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="8f056-384">**Verwenden Sie den Ziehpunkt Haltung**.</span><span class="sxs-lookup"><span data-stu-id="8f056-384">**Use the grip pose**.</span></span> <span data-ttu-id="8f056-385">Winkelgeschwindigkeit und Geschwindigkeit sind relativ zu den Ziehpunkt Haltung, kein Zeiger Haltung gemeldet.</span><span class="sxs-lookup"><span data-stu-id="8f056-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="8f056-386">Auslösen von weiterhin mit zukünftigen Windows-Updates zu verbessern, und Sie erwarten können, finden Sie weiterführende Informationen hier.</span><span class="sxs-lookup"><span data-stu-id="8f056-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="8f056-387">Schnellere Entwicklung mit Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="8f056-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="8f056-388">Es gibt zwei Beispiel-Szenen zu InputManager und MotionController in Unity.</span><span class="sxs-lookup"><span data-stu-id="8f056-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="8f056-389">Über diese Szenen erhalten Sie, wie MRTKs InputManager und Zugriff auf Daten behandeln Ereignisse aus der Motion-Controller-Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="8f056-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="8f056-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="8f056-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="8f056-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="8f056-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="8f056-392">Technische Details README-Datei</span><span class="sxs-lookup"><span data-stu-id="8f056-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="8f056-393">![Eingabebeispiel-Szenen in MRTK](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="8f056-394">*Eingabebeispiel-Szenen in MRTK*</span><span class="sxs-lookup"><span data-stu-id="8f056-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="8f056-395">Automatische Szene-setup</span><span class="sxs-lookup"><span data-stu-id="8f056-395">Automatic scene setup</span></span>

<span data-ttu-id="8f056-396">Beim Importieren von [MRTK releasepakete Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) oder Klonen Sie das Projekt aus der [GitHub-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), Sie sind dabei, ein neues Menü "Mixed Reality-Toolkit" in Unity finden.</span><span class="sxs-lookup"><span data-stu-id="8f056-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="8f056-397">Klicken Sie im Menü "Mixed Reality Szene-Einstellungen anwenden" wird unter "Konfigurieren" im Menü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8f056-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="8f056-398">Wenn Sie darauf klicken, wird er entfernt die Standardkamera und fügt grundlegende Komponenten - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), und [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="8f056-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="8f056-399">![MRTK-Menü für die Szene-setup](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="8f056-400">*MRTK-Menü für die Szene-setup*</span><span class="sxs-lookup"><span data-stu-id="8f056-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="8f056-401">![Automatische Szene Setup in MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="8f056-402">*Automatische Szene Setup in MRTK*</span><span class="sxs-lookup"><span data-stu-id="8f056-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="8f056-403">MixedRealityCamera prefabs</span><span class="sxs-lookup"><span data-stu-id="8f056-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="8f056-404">Sie können diese aus dem Projektfenster auch manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8f056-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="8f056-405">Sie finden diese Komponenten als prefabs (Vorlagen).</span><span class="sxs-lookup"><span data-stu-id="8f056-405">You can find these components as prefabs.</span></span> <span data-ttu-id="8f056-406">Bei der Suche **MixedRealityCamera**, Sie werden zwei verschiedene Kamera prefabs (Vorlagen) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8f056-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="8f056-407">Der Unterschied besteht darin, **MixedRealityCamera** ist die Kamera nur prefab dagegen **MixedRealityCameraParent** enthält zusätzliche Komponenten für die immersive Headsets wie z. B. Teleportation, während der Übertragung Controller und Grenze.</span><span class="sxs-lookup"><span data-stu-id="8f056-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="8f056-408">![Kamera-Prefabs im MRTK](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="8f056-409">*Kamera-Prefabs im MRTK*</span><span class="sxs-lookup"><span data-stu-id="8f056-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="8f056-410">**MixedRealtyCamera** HoloLens und immersive Kopfhörer unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8f056-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="8f056-411">Erkennt den Gerätetyp und die Eigenschaften wie z. B. deaktivieren Flags und Skybox optimiert.</span><span class="sxs-lookup"><span data-stu-id="8f056-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="8f056-412">Im folgenden können Sie einige nützliche Eigenschaften suchen, die können Sie z. B. benutzerdefinierte Cursor, während der Übertragung Controller-Modellen, anpassen und Floor.</span><span class="sxs-lookup"><span data-stu-id="8f056-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="8f056-413">![Eigenschaften für den Controller während der Übertragung, Cursor und Floor](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="8f056-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="8f056-414">*Eigenschaften für den Controller während der Übertragung, Cursor und Floor*</span><span class="sxs-lookup"><span data-stu-id="8f056-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="8f056-415">Nutzen Sie Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="8f056-415">Follow along with tutorials</span></span>

<span data-ttu-id="8f056-416">Schrittweiser Lernprogramme, mit der eine ausführlichere Beispiele für die Anpassung, sind in der Mixed Reality Academy verfügbar:</span><span class="sxs-lookup"><span data-stu-id="8f056-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="8f056-417">MR Eingabe 211: Aktion</span><span class="sxs-lookup"><span data-stu-id="8f056-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="8f056-418">MR Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="8f056-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="8f056-419">[![MR Eingabe 213 - Motion-controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="8f056-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="8f056-420">*MR Eingabe 213 - Motion-controller*</span><span class="sxs-lookup"><span data-stu-id="8f056-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="8f056-421">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8f056-421">See also</span></span>

* [<span data-ttu-id="8f056-422">Gesten</span><span class="sxs-lookup"><span data-stu-id="8f056-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="8f056-423">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="8f056-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="8f056-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="8f056-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="8f056-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="8f056-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="8f056-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="8f056-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
