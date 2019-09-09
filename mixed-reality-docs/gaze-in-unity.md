---
title: Blick in Unity
description: Der Blick ist eine primäre Möglichkeit für Benutzer, die Hologramme, die Ihre APP in gemischter Realität erstellt, als Ziel zu betrachten.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: Eye-Do, Head-Blick, Unity, Hologram, gemischte Realität
ms.openlocfilehash: 43e643bac00e3c889b14000331d2ed95014fdcc5
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122038"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="32ac9-104">Kopf schauen in Unity</span><span class="sxs-lookup"><span data-stu-id="32ac9-104">Head-gaze in Unity</span></span>

<span data-ttu-id="32ac9-105">Der Blick ist eine primäre Möglichkeit für Benutzer, die [Hologramme](hologram.md) , die Ihre APP in [gemischter Realität](mixed-reality.md)erstellt, als Ziel zu [betrachten](gaze.md) .</span><span class="sxs-lookup"><span data-stu-id="32ac9-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="32ac9-106">Implementieren von Head-Gaze</span><span class="sxs-lookup"><span data-stu-id="32ac9-106">Implementing head-gaze</span></span>

<span data-ttu-id="32ac9-107">Konzeptionell wird die [Kopfzeile](gaze.md) implementiert, indem ein Strahl von der Kopfzeile des Benutzers projiziert wird, an der sich das Headset befindet, und in der Vorwärtsrichtung, mit der der Strahl in Konflikt steht.</span><span class="sxs-lookup"><span data-stu-id="32ac9-107">Conceptually, [head-gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="32ac9-108">In Unity werden die Head-Position und die Richtung des Benutzers über die Unity-Haupt [Kamera](camera-in-unity.md), insbesondere [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html), verfügbar gemacht. [Transform. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="32ac9-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="32ac9-109">Das Aufrufen von " [Physik. raycast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " führt zu einer [raycasthit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) -Struktur, die Informationen über den Konflikt enthält, einschließlich des 3D-Punkts, bei dem der Konflikt aufgetreten ist, und des anderen gameobject, mit dem der Kopf-und</span><span class="sxs-lookup"><span data-stu-id="32ac9-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="32ac9-110">Beispiel: Implementieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="32ac9-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="32ac9-111">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="32ac9-111">Best practices</span></span>

<span data-ttu-id="32ac9-112">Obwohl das obige Beispiel zeigt, wie ein einzelnes raycast in einer Update-Schleife ausgeführt wird, um das Ziel der Hauptbenutzer des Benutzers zu finden, empfiehlt es sich, dies in einem einzelnen Objekt zu tun, das die Kopfzeile verwaltet, anstatt dies in einem Objekt zu tun, das potenziell an dem Agentsoftware interessiert ist. t wird bei der Eingabe von.</span><span class="sxs-lookup"><span data-stu-id="32ac9-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="32ac9-113">Dadurch kann Ihre APP die Verarbeitung speichern, indem Sie für jeden Frame nur einen Head-Gaze-raycast durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="32ac9-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="32ac9-114">Visualisieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="32ac9-114">Visualizing head-gaze</span></span>

<span data-ttu-id="32ac9-115">Ebenso wie auf dem Desktop, auf dem Sie mit einem Mauszeiger auf Inhalte abzielen und mit ihnen interagieren, sollten Sie einen [Cursor](cursors.md) implementieren, der die Kopfzeile des Benutzers darstellt.</span><span class="sxs-lookup"><span data-stu-id="32ac9-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="32ac9-116">Dadurch erhält der Benutzer Vertrauen in das, was Sie im Begriff sind, mit zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="32ac9-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="32ac9-117">Der Haupt Blick im Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="32ac9-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="32ac9-118">Sie können über den [Eingabe-Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk v2 auf den Haupt Blick zugreifen.</span><span class="sxs-lookup"><span data-stu-id="32ac9-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="32ac9-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="32ac9-119">See also</span></span>
* [<span data-ttu-id="32ac9-120">Kamera</span><span class="sxs-lookup"><span data-stu-id="32ac9-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="32ac9-121">Cursor</span><span class="sxs-lookup"><span data-stu-id="32ac9-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="32ac9-122">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="32ac9-122">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="32ac9-123">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="32ac9-123">Gaze targeting</span></span>](gaze-targeting.md)
