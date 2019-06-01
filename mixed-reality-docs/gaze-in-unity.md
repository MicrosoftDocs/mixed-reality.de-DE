---
title: In Unity bestaunen
description: Blicke ist ein primärer Weg für Benutzer der Hologramme als Ziel, die Ihre app in mixed Reality erstellt.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: Blicke, Unity, Hologramm, mixed reality
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453718"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="fef19-104">Head Blicke in Unity</span><span class="sxs-lookup"><span data-stu-id="fef19-104">Head gaze in Unity</span></span>

<span data-ttu-id="fef19-105">[Bestaunen](gaze.md) ist ein primärer Weg für Benutzer als Ziel der [Hologramme](hologram.md) Ihrer app erstellt in [Mixed Reality](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="fef19-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="fef19-106">Implementierende Head Blicke</span><span class="sxs-lookup"><span data-stu-id="fef19-106">Implementing head gaze</span></span>

<span data-ttu-id="fef19-107">Im Prinzip [bestaunen](gaze.md) wird durch Projizieren ein Strahl aus, in denen die Kopfhörer ist, vorwärts sie konfrontiert sind, und bestimmen, des Benutzers-Head implementiert das Chow verursacht einen Konflikt mit.</span><span class="sxs-lookup"><span data-stu-id="fef19-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="fef19-108">In Unity Head-Position des Benutzers und die Richtung sind verfügbar gemacht werden über der Unity-Hauptseite [Kamera](camera-in-unity.md), insbesondere [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ "Transform.Position"](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="fef19-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="fef19-109">Aufrufen von [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) führt zu einem [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) Struktur enthält Informationen zu den Konflikt, einschließlich der 3D-Punkts, in dem Konflikt aufgetreten ist, und die anderen "gameobject" Blicke Strahl widersprachen.</span><span class="sxs-lookup"><span data-stu-id="fef19-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="fef19-110">Beispiel: Head Blicke implementieren</span><span class="sxs-lookup"><span data-stu-id="fef19-110">Example: Implement head gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="fef19-111">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="fef19-111">Best Practices</span></span>

<span data-ttu-id="fef19-112">Während im obigen Beispiel wird veranschaulicht, wie Sie eine einzelne Raycast in einer Update-Schleife, um die Blicke-Ziel zu finden, wird empfohlen, führen Sie dies in ein einzelnes Objekt, das Verwalten von Blicke, anstatt dies in ein Objekt, das das Objekt wird an gazed möglicherweise interessiert ist.</span><span class="sxs-lookup"><span data-stu-id="fef19-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="fef19-113">Dadurch wird Ihre app, die Verarbeitung zu speichern, indem Sie nur eine Blicke Raycast jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="fef19-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="fef19-114">Visualisieren von Blicke</span><span class="sxs-lookup"><span data-stu-id="fef19-114">Visualizing Gaze</span></span>

<span data-ttu-id="fef19-115">Genau wie auf dem Desktop, in dem Sie mit dem Mauszeiger auf Ziel und interagieren mit Inhalt, die Sie implementieren sollten eine [Cursor](cursors.md) , des Benutzers Blicke darstellt.</span><span class="sxs-lookup"><span data-stu-id="fef19-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="fef19-116">Dadurch wird das Vertrauen in Was sind zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="fef19-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="fef19-117">In Mixed Reality bestaunen Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="fef19-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="fef19-118">Sie erreichen die Blicke, aus der [Eingabe Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="fef19-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="fef19-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fef19-119">See also</span></span>
* [<span data-ttu-id="fef19-120">Kamera</span><span class="sxs-lookup"><span data-stu-id="fef19-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="fef19-121">Blickverlaufseingabe</span><span class="sxs-lookup"><span data-stu-id="fef19-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="fef19-122">Cursor</span><span class="sxs-lookup"><span data-stu-id="fef19-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="fef19-123">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="fef19-123">Gaze targeting</span></span>](gaze-targeting.md)
