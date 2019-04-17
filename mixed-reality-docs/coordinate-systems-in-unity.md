---
title: Koordinatensysteme in Unity
description: Erfahren Sie, wie Sie sitzen, ständigen erstellen, die Platz Skalierung und weltweit einsetzbaren mixed Reality-Erfahrungen in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, räumliche Koordinatensystem, Ausrichtung, sitzen Skalierung, ständigen Maß Platz skalierbare, weltweit skalierbare, 360-Grad-sitzen, ständigen, Raum, Welt, skalieren, Position, Ausrichtung, Unity, Anker, räumliche Anker, Welt Anker, die World-gesperrt, World-sperren "," Text-gesperrt, Text-sperren, Nachverfolgen von Verlust, Locatability, den angegebenen Begrenzungen, verschoben
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605054"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="68b7f-104">Koordinatensysteme in Unity</span><span class="sxs-lookup"><span data-stu-id="68b7f-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="68b7f-105">Windows Mixed Reality unterstützt apps für eine Vielzahl von [auftreten Skalen](coordinate-systems.md), aus nur Ausrichtung und sitzen Skalierung apps sich über den Raum einsetzbaren apps.</span><span class="sxs-lookup"><span data-stu-id="68b7f-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="68b7f-106">Für HoloLens können Sie weiter gehen und Erstellen von weltweit einsetzbaren apps, mit denen Benutzer über 5 Meter Schritt für Schritt ein ganzes Stockwerk eines Gebäudes und darüber hinaus untersuchen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="68b7f-107">Der erste Schritt bei der Erstellung einer mixed Reality-Erfahrung in Unity wird bestimmt, welche [auftreten Skalierung](coordinate-systems.md) Ihrer app ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="68b7f-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="68b7f-108">Erstellen eine reine Ausrichtung oder sitzen Skalierung-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="68b7f-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="68b7f-109">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="68b7f-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="68b7f-110">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="68b7f-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="68b7f-111">Zum Erstellen einer **Ausrichtung nur** oder **sitzen Skalierung Erfahrung**, müssen Sie Unity auf Festlegen der stationär Speicherplatz Überwachungstyp.</span><span class="sxs-lookup"><span data-stu-id="68b7f-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="68b7f-112">Hiermit wird von Unity globales Koordinatensystem zum Nachverfolgen der [feststehende Verweisrahmen](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="68b7f-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="68b7f-113">In den Modus zum Nachverfolgen von nicht bewegt, wird Inhalt im Editor einfach vor der Kamera-Standardspeicherort platziert (forward ist – Z) wird vor dem Benutzer angezeigt, wenn die app gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="68b7f-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="68b7f-114">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="68b7f-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="68b7f-115">**Typ:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="68b7f-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="68b7f-116">Für ein reines **Ausrichtung ausschließlich Erfahrung** wie z. B. eine 360-Grad-video-Viewer (wobei mit Feldern fester Breite Head Updates würde auflöst, die Illusion), Sie können dann festlegen [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf "true":</span><span class="sxs-lookup"><span data-stu-id="68b7f-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="68b7f-117">Für eine **sitzen Skalierung Erfahrung**, damit der Benutzer später verschoben sitzen Ursprung rufen Sie die [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) Methode:</span><span class="sxs-lookup"><span data-stu-id="68b7f-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="68b7f-118">Erstellen eine Umgebung ständigen Skalierung oder Platz Skalierung</span><span class="sxs-lookup"><span data-stu-id="68b7f-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="68b7f-119">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="68b7f-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="68b7f-120">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="68b7f-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="68b7f-121">Für eine **ständigen Skalierung** oder **Platz Skalierung Erfahrung**, müssen Sie den Inhalt relativ zu dem Boden platziere.</span><span class="sxs-lookup"><span data-stu-id="68b7f-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="68b7f-122">Sie des Benutzers verständlich floor, mit der  **[räumliche Phase](coordinate-systems.md#spatial-coordinate-systems)**, Etage Ursprung und optional Platz Grenze definiert die des Benutzers darstellt, richten Sie während der ersten ausführen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="68b7f-123">Um sicherzustellen, dass Unity mit der ganzen Welt Koordinatensystem Floor-Ebene ausgeführt wird, können Sie Unity auf den Speicherplatz Überwachungstyp RoomScale festgelegt, und stellen Sie sicher, dass die Gruppe erfolgreich ist:</span><span class="sxs-lookup"><span data-stu-id="68b7f-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="68b7f-124">Wenn SetTrackingSpaceType "true" zurückgibt, Unity der Wechsel der globales Koordinatensystem zum Nachverfolgen der [Phase Verweisrahmen](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="68b7f-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="68b7f-125">Wenn SetTrackingSpaceType "false" zurückgegeben wird, konnte sich Unity, wechseln auf der Bühne Verweisrahmen, wahrscheinlich weil der Benutzer nicht selbst eine Etage in ihrer Umgebung eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="68b7f-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="68b7f-126">Dies ist nicht üblich, aber es kann vorkommen, wenn die Stufe in einem anderen Raum eingerichtet wurde und das Gerät wurde in der aktuellen Raum ohne die Benutzer-Einstellung, um eine neue Stufe verschoben.</span><span class="sxs-lookup"><span data-stu-id="68b7f-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="68b7f-127">Sobald Ihre app erfolgreich der Überwachungstyp Speicherplatz, Inhalte auf der y-platziert RoomScale festgelegt = 0, die auf dem Boden Ebene angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="68b7f-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="68b7f-128">Der Ursprung an (0, 0, 0) werden die bestimmten Stelle auf dem Boden, in denen der Benutzer vor während des Setups Platz mit -Z, die sie während des Setups konfrontiert wurden vorwärts darstellt.</span><span class="sxs-lookup"><span data-stu-id="68b7f-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="68b7f-129">**Namespace:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="68b7f-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="68b7f-130">**Typ:** *Begrenzungsgruppen*</span><span class="sxs-lookup"><span data-stu-id="68b7f-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="68b7f-131">In Skriptcode können Sie rufen Sie die TryGetGeometry-Methode für Sie sind der UnityEngine.Experimental.XR.Boundary-Typ, um eine Begrenzung Vieleck, erhalten ein Grenze TrackedArea angeben werden.</span><span class="sxs-lookup"><span data-stu-id="68b7f-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="68b7f-132">Wenn der Benutzer eine Grenze definiert (erhalten Sie wieder eine Liste der Scheitelpunkte), wissen Sie, es ist sicher bereitstellen eine **Platz Skalierung Erfahrung** für den Benutzer, in dem sie eine in der Szene Anleitung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="68b7f-133">Beachten Sie, dass das System automatisch die Grenze gerendert wird, wenn der Benutzer es erreicht.</span><span class="sxs-lookup"><span data-stu-id="68b7f-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="68b7f-134">Ihre app muss nicht auf dieses Polygon zu verwenden, um die Begrenzung selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="68b7f-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="68b7f-135">Allerdings können Sie auswählen, um das Layout der szeneobjekte, die über diese Begrenzung Vieleck, um sicherzustellen, dass der Benutzer diese Objekte ohne Teleporting physisch erreichen kann:</span><span class="sxs-lookup"><span data-stu-id="68b7f-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="68b7f-136">Erstellen einer weltweit einsetzbaren-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="68b7f-136">Building a world-scale experience</span></span>

<span data-ttu-id="68b7f-137">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="68b7f-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="68b7f-138">**Typ:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="68b7f-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="68b7f-139">Für "true" **weltweit einsetzbaren Erfahrungen** für HoloLens, mit denen Benutzer über 5 Meter erkundungs können, benötigen Sie neue Techniken hinausgehen für Platz Skalierung Oberflächen verwendet.</span><span class="sxs-lookup"><span data-stu-id="68b7f-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="68b7f-140">Ist eine wichtige Technik, die Sie verwenden die Erstellung einer [räumliche Anker](coordinate-systems.md#spatial-anchors) , Sperren einen Cluster mit Hologramme genau an die Stelle in der realen Welt, unabhängig davon, wie weit der Benutzer gewechselt hat, und klicken Sie dann [finden Sie diese Hologramme erneut in einem späteren Zeitpunkt Sitzungen](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="68b7f-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="68b7f-141">In Unity, erstellen Sie einen räumlichen Anker durch Hinzufügen der **WorldAnchor** Unity-Komponente zu einem "gameobject".</span><span class="sxs-lookup"><span data-stu-id="68b7f-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="68b7f-142">Einen Anker Welt hinzufügen</span><span class="sxs-lookup"><span data-stu-id="68b7f-142">Adding a World Anchor</span></span>

<span data-ttu-id="68b7f-143">Rufen Sie zum Hinzufügen eines Welt Ankers AddComponent<WorldAnchor>(-) für das spielobjekt mit der Transformation, die Sie in der realen Welt verankert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="68b7f-144">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="68b7f-144">That's it!</span></span> <span data-ttu-id="68b7f-145">Dieses spielobjekt wird jetzt an ihrem aktuellen Speicherort in der realen Welt verankert werden – möglicherweise angezeigt, die Unity globale Koordinaten, die im Laufe der Zeit, um sicherzustellen, dass diese physische Ausrichtung leicht anpassen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="68b7f-146">Verwendung [Persistenz](persistence-in-unity.md) Ermittlung verankert Speicherort in einem künftigen app-Sitzung erneut.</span><span class="sxs-lookup"><span data-stu-id="68b7f-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="68b7f-147">Entfernen einen Anker World</span><span class="sxs-lookup"><span data-stu-id="68b7f-147">Removing a World Anchor</span></span>

<span data-ttu-id="68b7f-148">Wenn Sie nicht mehr, dass das "gameobject" an einen Speicherort für die physische Welt gesperrt werden soll und nicht auf diesen Frame verschieben möchten, können Sie einfach löschen auf der Welt Anchor-Komponente aufrufen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="68b7f-149">Wenn Sie das "gameobject" diesen Frame verschieben möchten, müssen Sie DestroyImmediate stattdessen aufrufen.</span><span class="sxs-lookup"><span data-stu-id="68b7f-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="68b7f-150">Verschieben einer Welt verankert "gameobject"</span><span class="sxs-lookup"><span data-stu-id="68b7f-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="68b7f-151">Des "gameobject" kann nicht verschoben werden, während ein Anker Welt darauf ist.</span><span class="sxs-lookup"><span data-stu-id="68b7f-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="68b7f-152">Wenn Sie das "gameobject" diesen Frame verschieben müssen, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="68b7f-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="68b7f-153">DestroyImmediate der Welt Anchor-Komponente</span><span class="sxs-lookup"><span data-stu-id="68b7f-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="68b7f-154">Verschieben Sie das "gameobject"</span><span class="sxs-lookup"><span data-stu-id="68b7f-154">Move the GameObject</span></span>
3. <span data-ttu-id="68b7f-155">Fügen Sie eine neue Welt Anker-Komponente, auf das "gameobject".</span><span class="sxs-lookup"><span data-stu-id="68b7f-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="68b7f-156">Locatability Änderungen</span><span class="sxs-lookup"><span data-stu-id="68b7f-156">Handling Locatability Changes</span></span>

<span data-ttu-id="68b7f-157">Eine WorldAnchor auffindbaren in der realen Welt zu einem bestimmten Zeitpunkt möglicherweise nicht.</span><span class="sxs-lookup"><span data-stu-id="68b7f-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="68b7f-158">Wenn in diesem Fall ist Unity nicht die Transformation das verankerten Objekt aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="68b7f-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="68b7f-159">Dies kann auch ändern, während eine app ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="68b7f-159">This also can change while an app is running.</span></span> <span data-ttu-id="68b7f-160">Fehler bei die Änderung in Locatability verarbeiten bewirkt das Objekt, das nicht in den richtigen physischen Speicherort in der ganzen Welt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="68b7f-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="68b7f-161">Um zu Locatability Änderungen benachrichtigt zu werden:</span><span class="sxs-lookup"><span data-stu-id="68b7f-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="68b7f-162">Abonnieren des Ereignisses OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="68b7f-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="68b7f-163">Behandeln des Ereignisses</span><span class="sxs-lookup"><span data-stu-id="68b7f-163">Handle the event</span></span>

<span data-ttu-id="68b7f-164">Die **OnTrackingChanged** Ereignis wird aufgerufen, wenn der zugrunde liegenden räumliche Anker zwischen den Zuständen, im Vergleich zu nicht auffindbaren werden gebietsschemabezogene ändert.</span><span class="sxs-lookup"><span data-stu-id="68b7f-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="68b7f-165">Klicken Sie dann das Ereignis zu behandeln:</span><span class="sxs-lookup"><span data-stu-id="68b7f-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="68b7f-166">Manchmal sind sofort Anker befindet.</span><span class="sxs-lookup"><span data-stu-id="68b7f-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="68b7f-167">In diesem Fall wird diese IsLocated-Eigenschaft von der Anker auf bei "true" festgelegt werden AddComponent<WorldAnchor>() gibt.</span><span class="sxs-lookup"><span data-stu-id="68b7f-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="68b7f-168">Daher wird die OnTrackingChanged-Ereignis nicht ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="68b7f-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="68b7f-169">Ein clean Muster wäre Ihr OnTrackingChanged Handler mit dem Anfangszustand IsLocated rufen Sie nach dem Anfügen eines Ankers.</span><span class="sxs-lookup"><span data-stu-id="68b7f-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="68b7f-170">Freigeben von Anker auf Geräten</span><span class="sxs-lookup"><span data-stu-id="68b7f-170">Sharing anchors across devices</span></span>

<span data-ttu-id="68b7f-171">Können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> einen dauerhafte Anker aus einer lokalen WorldAnchor, zu erstellen, die Ihrer app über mehrere HoloLens, iOS und Android-Geräte suchen kann.</span><span class="sxs-lookup"><span data-stu-id="68b7f-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="68b7f-172">Anhand der einen allgemeine räumlichen Anker auf mehreren Geräten, kann jeder Benutzer Inhalt gerendert wird, relativ zu diesem-Anker wird in demselben physischen Standort finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="68b7f-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="68b7f-173">Dadurch können freigegebene ein Nutzererlebnis in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="68b7f-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="68b7f-174">Informationen zum Einstieg gemeinsame Erfahrungen in Unity erstellen, Testen der 5-Minuten- <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure räumliche Anker Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="68b7f-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="68b7f-175">Sobald Sie mit Azure räumliche Anker die betriebsbereit sind, können Sie dann <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">erstellen, und suchen Sie in Unity Anker</a>.</span><span class="sxs-lookup"><span data-stu-id="68b7f-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="68b7f-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="68b7f-176">See Also</span></span>
* [<span data-ttu-id="68b7f-177">Erleben Sie Skalierungen</span><span class="sxs-lookup"><span data-stu-id="68b7f-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="68b7f-178">Räumliche Phase</span><span class="sxs-lookup"><span data-stu-id="68b7f-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="68b7f-179">Verlust der Überwachung in Unity</span><span class="sxs-lookup"><span data-stu-id="68b7f-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="68b7f-180">Räumliche Anker</span><span class="sxs-lookup"><span data-stu-id="68b7f-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="68b7f-181">Dauerhaftigkeit in Unity</span><span class="sxs-lookup"><span data-stu-id="68b7f-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="68b7f-182">Freigegebene Funktionen in Unity</span><span class="sxs-lookup"><span data-stu-id="68b7f-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="68b7f-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a></span><span class="sxs-lookup"><span data-stu-id="68b7f-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="68b7f-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure räumliche Anker SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="68b7f-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>