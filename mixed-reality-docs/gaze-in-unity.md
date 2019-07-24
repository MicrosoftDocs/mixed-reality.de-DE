---
title: Blick in Unity
description: Der Blick ist eine primäre Möglichkeit für Benutzer, die Hologramme, die Ihre APP in gemischter Realität erstellt, als Ziel zu betrachten.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: Blick, Unity, Hologram, gemischte Realität
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453718"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="77d65-104">Kopf Blicke in Unity</span><span class="sxs-lookup"><span data-stu-id="77d65-104">Head gaze in Unity</span></span>

<span data-ttu-id="77d65-105">Der Blick ist eine primäre Möglichkeit für Benutzer, die [Hologramme](hologram.md) , die Ihre APP in [gemischter Realität](mixed-reality.md)erstellt, als Ziel zu [betrachten](gaze.md) .</span><span class="sxs-lookup"><span data-stu-id="77d65-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="77d65-106">Implementieren des Head-Blicks</span><span class="sxs-lookup"><span data-stu-id="77d65-106">Implementing head gaze</span></span>

<span data-ttu-id="77d65-107">Konzeptionell wird der [Blick](gaze.md) durch die Projektion eines Strahls aus dem Head des Benutzers, an dem sich das Headset befindet, in der Vorwärtsrichtung implementiert, und es wird festgelegt, mit welchem Strahl dieses Ray kollidiert.</span><span class="sxs-lookup"><span data-stu-id="77d65-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="77d65-108">In Unity werden die Head-Position und die Richtung des Benutzers über die Unity-Haupt [Kamera](camera-in-unity.md), insbesondere [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html), verfügbar gemacht. [Transform. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="77d65-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="77d65-109">Der Aufruf von " [Physik. raycast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " führt zu einer [raycasthit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) -Struktur, die Informationen über den Konflikt enthält, einschließlich des 3D-Punkts, bei dem der Konflikt aufgetreten ist, und des anderen gameobject, mit dem der Blick</span><span class="sxs-lookup"><span data-stu-id="77d65-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="77d65-110">Beispiel: Implementieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="77d65-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="77d65-111">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="77d65-111">Best Practices</span></span>

<span data-ttu-id="77d65-112">Obwohl das obige Beispiel zeigt, wie ein einzelnes raycast in einer Update-Schleife ausgeführt wird, um das Suchziel zu finden, empfiehlt es sich, dies in einem einzelnen Objekt zu tun, das den Blick verwaltet, anstatt dies in einem Objekt zu tun, das potenziell an dem Objekt interessiert ist, bei dem es sich befindet.</span><span class="sxs-lookup"><span data-stu-id="77d65-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="77d65-113">Dadurch kann Ihre APP die Verarbeitung speichern, indem Sie nur einen Blick auf jeden Frame durchläuft.</span><span class="sxs-lookup"><span data-stu-id="77d65-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="77d65-114">Visualisieren des Blicks</span><span class="sxs-lookup"><span data-stu-id="77d65-114">Visualizing Gaze</span></span>

<span data-ttu-id="77d65-115">Ebenso wie auf dem Desktop, auf dem Sie mit einem Mauszeiger auf Inhalte abzielen und mit ihnen interagieren, sollten Sie einen [Cursor](cursors.md) implementieren, der den Blick des Benutzers darstellt.</span><span class="sxs-lookup"><span data-stu-id="77d65-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="77d65-116">Dadurch erhält der Benutzer Vertrauen in das, was Sie im Begriff sind, mit zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="77d65-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="77d65-117">Blick in Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="77d65-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="77d65-118">Sie können über den Eingabe- [Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk v2 auf den Blick zugreifen.</span><span class="sxs-lookup"><span data-stu-id="77d65-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="77d65-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="77d65-119">See also</span></span>
* [<span data-ttu-id="77d65-120">Kamera</span><span class="sxs-lookup"><span data-stu-id="77d65-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="77d65-121">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="77d65-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="77d65-122">Cursor</span><span class="sxs-lookup"><span data-stu-id="77d65-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="77d65-123">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="77d65-123">Gaze targeting</span></span>](gaze-targeting.md)
