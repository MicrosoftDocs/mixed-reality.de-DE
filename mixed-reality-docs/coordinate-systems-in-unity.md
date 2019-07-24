---
title: Koordinatensysteme in Unity
description: Erfahren Sie, wie Sie in Unity sitzender, stehender, Raum-und Welt weite Umgebungen mit gemischter Realität erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, geografischer Koordinatensystem, nur Ausrichtung, sitzender Skalierung, aneinandergreifende Skala, Raum Skala, Welt weite, 360 Grad, sitzend, stehend, Raum, Welt, Skala, Position, Ausrichtung, Unity, Anker, räumlicher Anker, Welt Anker, weltweit gesperrt, Welt Sperre, gesperrter Text, Body-Lock, nach Verfolgungs Verlust, loerbarkeit, Grenzen, wiedergeben
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525962"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="93a80-104">Koordinatensysteme in Unity</span><span class="sxs-lookup"><span data-stu-id="93a80-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="93a80-105">Windows Mixed Reality unterstützt Apps über eine Vielzahl von [Skalierungs](coordinate-systems.md)Möglichkeiten hinweg, von ausgerichteten und skalierbaren apps bis hin zu hochskalierbaren apps.</span><span class="sxs-lookup"><span data-stu-id="93a80-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="93a80-106">Auf hololens können Sie weitere apps erstellen und Apps erstellen, mit denen Benutzer mehr als 5 Meter durchlaufen können, indem Sie eine ganze Etage eines Builds und darüber hinaus untersuchen.</span><span class="sxs-lookup"><span data-stu-id="93a80-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="93a80-107">Der erste Schritt beim Aufbau einer gemischten Realität in Unity besteht darin, zu bestimmen [, welche Benutzer](coordinate-systems.md) Oberfläche Ihre APP als Ziel hat.</span><span class="sxs-lookup"><span data-stu-id="93a80-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="93a80-108">Aufbauen einer reinen Orientierung oder einer Skalierungs Funktion</span><span class="sxs-lookup"><span data-stu-id="93a80-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="93a80-109">**Namespace:** *Unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="93a80-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="93a80-110">**Sorte** *Xrdevice*</span><span class="sxs-lookup"><span data-stu-id="93a80-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="93a80-111">Sie müssen Unity auf den Typ "stationärer nach verfolgungsbereich" festlegen, um eine **Orientierung** oder eine **Skalierung**zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="93a80-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="93a80-112">Dadurch wird das World-Koordinatensystem von Unity festgelegt, um den [stationären Frame des Verweises](coordinate-systems.md#spatial-coordinate-systems)zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="93a80-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="93a80-113">Im Modus der stationären Nachverfolgung wird der Inhalt, der direkt vor dem Standard Speicherort der Kamera (vorwärts ist-Z) im Editor eingefügt wird, vor dem Benutzer angezeigt, wenn die APP gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="93a80-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="93a80-114">**Namespace:** *Unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="93a80-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="93a80-115">**Sorte** *Inputtracking*</span><span class="sxs-lookup"><span data-stu-id="93a80-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="93a80-116">Bei einer reinen **Orientierung** , z. b. bei einem Video Viewer mit einem 360-Grad (bei dem Positions Aktualisierungen die Illusion zerstören würden), können Sie "XR" festlegen [. Inputtracking. disablepositionaltracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf true:</span><span class="sxs-lookup"><span data-stu-id="93a80-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="93a80-117">Um dem Benutzer die Möglichkeit zu geben, den sitzenden Ursprung zu einem späteren Zeitpunkt wieder einzugeben, können Sie den XR-Vorgang für eine Benutzer **freundliche Skalierung**durchführen [. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) -Methode:</span><span class="sxs-lookup"><span data-stu-id="93a80-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="93a80-118">Aufbauen einer Dauer-oder Raum Skalierung</span><span class="sxs-lookup"><span data-stu-id="93a80-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="93a80-119">**Namespace:** *Unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="93a80-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="93a80-120">**Sorte** *Xrdevice*</span><span class="sxs-lookup"><span data-stu-id="93a80-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="93a80-121">Für eine **Dauer-** oder **Raum Skalierung**müssen Sie Inhalte in Relation zum Boden platzieren.</span><span class="sxs-lookup"><span data-stu-id="93a80-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="93a80-122">Sie haben eine Begründung für den Benutzer, der die **[räumliche Phase](coordinate-systems.md#spatial-coordinate-systems)** verwendet, die den definierten Ursprung und die optionale Raumgrenze des Benutzers darstellt, die während der ersten Durchführung eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="93a80-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="93a80-123">Um sicherzustellen, dass Unity mit dem globalen Koordinatensystem auf Grundebene betrieben wird, können Sie Unity auf den Typ des roomscale-nach Verfolgungs Raums festlegen und sicherstellen, dass der Satz erfolgreich ist:</span><span class="sxs-lookup"><span data-stu-id="93a80-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="93a80-124">Wenn settrackingspacetype true zurückgibt, hat Unity das World-Koordinatensystem erfolgreich umgestellt, um den stagingframe [des Verweises](coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="93a80-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="93a80-125">Wenn settrackingspacetype false zurückgibt, konnte Unity nicht in den stagingframe des Verweises wechseln. Dies liegt wahrscheinlich daran, dass der Benutzer noch keine Etage in der Umgebung eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="93a80-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="93a80-126">Dies ist nicht üblich, kann jedoch vorkommen, wenn die Stufe in einem anderen Raum eingerichtet wurde und das Gerät in den aktuellen Raum verschoben wurde, ohne dass der Benutzer eine neue Stufe einrichten muss.</span><span class="sxs-lookup"><span data-stu-id="93a80-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="93a80-127">Nachdem Ihre APP den Typ für die Nachverfolgung von roomscale festgelegt hat, wird der Inhalt auf der Ebene "y = 0" auf der Etage angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93a80-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="93a80-128">Der Ursprung bei (0,0) ist die spezifische Stelle auf dem Boden, an der der Benutzer während des Raum Setups Stand, wobei-Z die Vorwärtsrichtung darstellt, die während des Setups aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="93a80-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="93a80-129">**Namespace:** *Unityengine. experimental. XR*</span><span class="sxs-lookup"><span data-stu-id="93a80-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="93a80-130">**Sorte** *Begrenzungs*</span><span class="sxs-lookup"><span data-stu-id="93a80-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="93a80-131">In Skriptcode können Sie dann die trygetgeometry-Methode aufrufen, indem Sie den Typ "unityengine. experimental. XR. Boundary" verwenden, um ein Begrenzungs Polygon abzurufen und dabei den Grenztyp "trackedarea" anzugeben.</span><span class="sxs-lookup"><span data-stu-id="93a80-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="93a80-132">Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste mit Scheitel Punkten), ist es sicher, dass er für den Benutzer eine **Raum** Umgebung bereitstellt, in der er die von Ihnen erstellte Szene durchlaufen kann.</span><span class="sxs-lookup"><span data-stu-id="93a80-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="93a80-133">Beachten Sie, dass das System die Grenze automatisch durchführt, wenn sich der Benutzer nähert.</span><span class="sxs-lookup"><span data-stu-id="93a80-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="93a80-134">Ihre APP muss dieses Polygon nicht verwenden, um die Grenze selbst zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="93a80-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="93a80-135">Allerdings können Sie Ihre Szenen Objekte mithilfe dieses Begrenzungs Polygons anordnen, um sicherzustellen, dass der Benutzer diese Objekte physisch ohne teleportierung erreichen kann:</span><span class="sxs-lookup"><span data-stu-id="93a80-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="93a80-136">Entwickeln eines weltweiten Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="93a80-136">Building a world-scale experience</span></span>

<span data-ttu-id="93a80-137">**Namespace:** *Unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="93a80-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="93a80-138">**Sorte** *Worldanchor*</span><span class="sxs-lookup"><span data-stu-id="93a80-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="93a80-139">Für echte **Welt weite** Oberflächen in hololens, mit denen Benutzer mehr als 5 Meter bewegen können, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raum Skalierungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="93a80-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="93a80-140">Ein wichtiges Verfahren, das Sie verwenden, besteht darin, einen [räumlichen Anker](coordinate-systems.md#spatial-anchors) zu erstellen, mit dem ein Cluster von holograms genau in der physischen Welt gesperrt wird, unabhängig davon, wie weit der Benutzer gewechselt hat, und [diese Hologramme in späteren Sitzungen erneut finden](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="93a80-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="93a80-141">In Unity erstellen Sie einen räumlichen Anker durch Hinzufügen der Unity-Komponente **worldanchor** zu einem gameobject-Objekt.</span><span class="sxs-lookup"><span data-stu-id="93a80-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="93a80-142">Hinzufügen eines Welt Ankers</span><span class="sxs-lookup"><span data-stu-id="93a80-142">Adding a World Anchor</span></span>

<span data-ttu-id="93a80-143">Um einen Welt Anker hinzuzufügen, nennen Sie addComponent<WorldAnchor>() für das Game-Objekt mit der Transformation, die Sie in der realen Welt verankern möchten.</span><span class="sxs-lookup"><span data-stu-id="93a80-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="93a80-144">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="93a80-144">That's it!</span></span> <span data-ttu-id="93a80-145">Dieses Spielobjekt wird nun an seinem aktuellen Speicherort in der physischen Welt verankert. möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="93a80-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="93a80-146">Verwenden Sie [Persistenz](persistence-in-unity.md) , um diesen verankerten Standort in einer zukünftigen App-Sitzung wieder zu suchen.</span><span class="sxs-lookup"><span data-stu-id="93a80-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="93a80-147">Entfernen eines Welt Ankers</span><span class="sxs-lookup"><span data-stu-id="93a80-147">Removing a World Anchor</span></span>

<span data-ttu-id="93a80-148">Wenn Sie nicht mehr möchten, dass das gameobject-Objekt an eine physische Welt Stelle gesperrt ist, und Sie dieses Frame nicht verschieben möchten, können Sie einfach "zerstören" für die "World Anchor"-Komponente aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="93a80-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="93a80-149">Wenn Sie das gameobject-Objekt in diesen Frame verschieben möchten, müssen Sie stattdessen destroyimmediate aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="93a80-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="93a80-150">Verschieben eines weltweit verankerten gameobject</span><span class="sxs-lookup"><span data-stu-id="93a80-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="93a80-151">Gameobject kann nicht verschoben werden, wenn ein Welt Anker darauf liegt.</span><span class="sxs-lookup"><span data-stu-id="93a80-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="93a80-152">Wenn Sie das gameobject für diesen Frame verschieben müssen, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="93a80-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="93a80-153">Destroyimmediate der Welt Anker Komponente</span><span class="sxs-lookup"><span data-stu-id="93a80-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="93a80-154">Verschieben des gameobject</span><span class="sxs-lookup"><span data-stu-id="93a80-154">Move the GameObject</span></span>
3. <span data-ttu-id="93a80-155">Fügen Sie dem gameobject eine neue Welt Anker Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="93a80-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="93a80-156">Behandeln von Änderungen an der Anwendungs Freundlichkeit</span><span class="sxs-lookup"><span data-stu-id="93a80-156">Handling Locatability Changes</span></span>

<span data-ttu-id="93a80-157">Ein worldanchor kann nicht in der physischen Welt zu einem bestimmten Zeitpunkt einstellbar sein.</span><span class="sxs-lookup"><span data-stu-id="93a80-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="93a80-158">Wenn dies der Fall ist, wird die Transformation des verankerten Objekts von Unity nicht aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="93a80-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="93a80-159">Dies kann sich auch ändern, während eine app ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="93a80-159">This also can change while an app is running.</span></span> <span data-ttu-id="93a80-160">Wenn Sie die Änderung der loerability nicht bewältigen, wird das Objekt nicht am richtigen physischen Speicherort der Welt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93a80-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="93a80-161">So erhalten Sie eine Benachrichtigung über die Änderungen der Änderungen:</span><span class="sxs-lookup"><span data-stu-id="93a80-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="93a80-162">Ontrackingchanged-Ereignis abonnieren</span><span class="sxs-lookup"><span data-stu-id="93a80-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="93a80-163">Behandeln des Ereignisses</span><span class="sxs-lookup"><span data-stu-id="93a80-163">Handle the event</span></span>

<span data-ttu-id="93a80-164">Das **ontrackingchanged** -Ereignis wird immer dann aufgerufen, wenn sich der zugrunde liegende räumliche Anker zwischen dem Zustand "verwendbar" und "nicht zu verwendbar" ändert.</span><span class="sxs-lookup"><span data-stu-id="93a80-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="93a80-165">Behandeln Sie dann das-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="93a80-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="93a80-166">Manchmal werden Anker sofort gefunden.</span><span class="sxs-lookup"><span data-stu-id="93a80-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="93a80-167">In diesem Fall wird diese islocated-Eigenschaft des Ankers auf true festgelegt, wenn addComponent<WorldAnchor>() zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="93a80-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="93a80-168">Folglich wird das ontrackingchanged-Ereignis nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="93a80-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="93a80-169">Ein sauberes Muster besteht darin, den ontrackingchanged-Handler mit dem ursprünglichen ISSE-Zustand nach dem Anfügen eines Ankers aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="93a80-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="93a80-170">Gemeinsame Nutzung von Ankern Geräten</span><span class="sxs-lookup"><span data-stu-id="93a80-170">Sharing anchors across devices</span></span>

<span data-ttu-id="93a80-171">Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.</span><span class="sxs-lookup"><span data-stu-id="93a80-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="93a80-172">Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.</span><span class="sxs-lookup"><span data-stu-id="93a80-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="93a80-173">Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="93a80-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="93a80-174">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="93a80-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="93a80-175">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="93a80-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="93a80-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="93a80-176">See Also</span></span>
* [<span data-ttu-id="93a80-177">Skalierungsmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="93a80-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="93a80-178">Räumliche Phase</span><span class="sxs-lookup"><span data-stu-id="93a80-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="93a80-179">Verfolgbarkeitsverlust in Unity</span><span class="sxs-lookup"><span data-stu-id="93a80-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="93a80-180">Raumanker</span><span class="sxs-lookup"><span data-stu-id="93a80-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="93a80-181">Persistenz in Unity</span><span class="sxs-lookup"><span data-stu-id="93a80-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="93a80-182">Gemeinsame Erlebnisse in Unity</span><span class="sxs-lookup"><span data-stu-id="93a80-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="93a80-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="93a80-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="93a80-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="93a80-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>