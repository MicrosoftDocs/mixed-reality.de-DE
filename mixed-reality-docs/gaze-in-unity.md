---
title: In Unity bestaunen
description: Blicke ist ein primärer Weg für Benutzer der Hologramme als Ziel, die Ihre app in mixed Reality erstellt.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Blicke, Unity, Hologramm, mixed reality
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604804"
---
# <a name="gaze-in-unity"></a><span data-ttu-id="b76a1-104">In Unity bestaunen</span><span class="sxs-lookup"><span data-stu-id="b76a1-104">Gaze in Unity</span></span>

<span data-ttu-id="b76a1-105">[Bestaunen](gaze.md) ist ein primärer Weg für Benutzer als Ziel der [Hologramme](hologram.md) Ihrer app erstellt in [mixed Reality](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="b76a1-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="b76a1-106">Implementieren von Blicke</span><span class="sxs-lookup"><span data-stu-id="b76a1-106">Implementing Gaze</span></span>

<span data-ttu-id="b76a1-107">Im Prinzip [bestaunen](gaze.md) wird durch Projizieren ein Strahl aus, in denen die Kopfhörer ist, vorwärts sie konfrontiert sind, und bestimmen, des Benutzers-Head implementiert das Chow verursacht einen Konflikt mit.</span><span class="sxs-lookup"><span data-stu-id="b76a1-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="b76a1-108">In Unity Head-Position des Benutzers und die Richtung sind verfügbar gemacht werden über der Unity-Hauptseite [Kamera](camera-in-unity.md), insbesondere [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ "Transform.Position"](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="b76a1-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="b76a1-109">Aufrufen von [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) führt zu einem [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) Struktur enthält Informationen zu den Konflikt, einschließlich der 3D-Punkts, in dem Konflikt aufgetreten ist, und die anderen "gameobject" Blicke Strahl widersprachen.</span><span class="sxs-lookup"><span data-stu-id="b76a1-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="b76a1-110">Beispiel: Implementieren Blicke</span><span class="sxs-lookup"><span data-stu-id="b76a1-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="b76a1-111">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="b76a1-111">Best Practices</span></span>

<span data-ttu-id="b76a1-112">Während im obigen Beispiel wird veranschaulicht, wie Sie eine einzelne Raycast in einer Update-Schleife, um die Blicke-Ziel zu finden, wird empfohlen, führen Sie dies in ein einzelnes Objekt, das Verwalten von Blicke, anstatt dies in ein Objekt, das das Objekt wird an gazed möglicherweise interessiert ist.</span><span class="sxs-lookup"><span data-stu-id="b76a1-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="b76a1-113">Dadurch wird Ihre app, die Verarbeitung zu speichern, indem Sie nur eine Blicke Raycast jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="b76a1-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="b76a1-114">Visualisieren von Blicke</span><span class="sxs-lookup"><span data-stu-id="b76a1-114">Visualizing Gaze</span></span>

<span data-ttu-id="b76a1-115">Genau wie auf dem Desktop, in dem Sie mit dem Mauszeiger auf Ziel und interagieren mit Inhalt, die Sie implementieren sollten eine [Cursor](cursors.md) , des Benutzers Blicke darstellt.</span><span class="sxs-lookup"><span data-stu-id="b76a1-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="b76a1-116">Dadurch wird das Vertrauen in Was sind zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="b76a1-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="b76a1-117">Bestaunen Sie in Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="b76a1-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="b76a1-118">Beim Importieren von [MRTK releasepakete Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) oder Klonen Sie das Projekt aus der [GitHub-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), Sie sind dabei, ein neues Menü "Mixed Reality-Toolkit" in Unity finden.</span><span class="sxs-lookup"><span data-stu-id="b76a1-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="b76a1-119">Klicken Sie im Menü "Mixed Reality Szene-Einstellungen anwenden" wird unter "Konfigurieren" im Menü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b76a1-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="b76a1-120">Wenn Sie darauf klicken, wird er entfernt die Standardkamera und fügt grundlegende Komponenten - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), und [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="b76a1-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="b76a1-121">![MRTK-Menü für die Szene-setup](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="b76a1-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="b76a1-122">*MRTK-Menü für die Szene-setup*</span><span class="sxs-lookup"><span data-stu-id="b76a1-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="b76a1-123">![Automatische Szene Setup in MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="b76a1-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="b76a1-124">*Automatische Szene Setup in MRTK*</span><span class="sxs-lookup"><span data-stu-id="b76a1-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="b76a1-125">Bestaunen Sie zusammengehörigen Skripts zu Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="b76a1-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="b76a1-126">Mixed Reality-Toolkit InputManager prefab enthält [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) und [bestaunen Stabilisierung](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span><span class="sxs-lookup"><span data-stu-id="b76a1-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="b76a1-127">Klicken Sie unter [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), Sie können Ihre benutzerdefinierten Cursor zuweisen.</span><span class="sxs-lookup"><span data-stu-id="b76a1-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="b76a1-128">Im standardmäßigen, animiert [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="b76a1-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="b76a1-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) und [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) erfahren Sie, wie Sie Ihre Blicke Verwenden von Cursorn zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="b76a1-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="b76a1-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b76a1-130">See also</span></span>
* [<span data-ttu-id="b76a1-131">Kamera</span><span class="sxs-lookup"><span data-stu-id="b76a1-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="b76a1-132">Blicke</span><span class="sxs-lookup"><span data-stu-id="b76a1-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="b76a1-133">Cursor</span><span class="sxs-lookup"><span data-stu-id="b76a1-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b76a1-134">Blicke für</span><span class="sxs-lookup"><span data-stu-id="b76a1-134">Gaze targeting</span></span>](gaze-targeting.md)
