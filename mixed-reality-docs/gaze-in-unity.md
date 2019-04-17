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
# <a name="gaze-in-unity"></a>In Unity bestaunen

[Bestaunen](gaze.md) ist ein primärer Weg für Benutzer als Ziel der [Hologramme](hologram.md) Ihrer app erstellt in [mixed Reality](mixed-reality.md).

## <a name="implementing-gaze"></a>Implementieren von Blicke

Im Prinzip [bestaunen](gaze.md) wird durch Projizieren ein Strahl aus, in denen die Kopfhörer ist, vorwärts sie konfrontiert sind, und bestimmen, des Benutzers-Head implementiert das Chow verursacht einen Konflikt mit. In Unity Head-Position des Benutzers und die Richtung sind verfügbar gemacht werden über der Unity-Hauptseite [Kamera](camera-in-unity.md), insbesondere [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ "Transform.Position"](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Aufrufen von [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) führt zu einem [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) Struktur enthält Informationen zu den Konflikt, einschließlich der 3D-Punkts, in dem Konflikt aufgetreten ist, und die anderen "gameobject" Blicke Strahl widersprachen.

### <a name="example-implement-gaze"></a>Beispiel: Implementieren Blicke

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

### <a name="best-practices"></a>Empfehlungen

Während im obigen Beispiel wird veranschaulicht, wie Sie eine einzelne Raycast in einer Update-Schleife, um die Blicke-Ziel zu finden, wird empfohlen, führen Sie dies in ein einzelnes Objekt, das Verwalten von Blicke, anstatt dies in ein Objekt, das das Objekt wird an gazed möglicherweise interessiert ist. Dadurch wird Ihre app, die Verarbeitung zu speichern, indem Sie nur eine Blicke Raycast jeden Frame.

## <a name="visualizing-gaze"></a>Visualisieren von Blicke

Genau wie auf dem Desktop, in dem Sie mit dem Mauszeiger auf Ziel und interagieren mit Inhalt, die Sie implementieren sollten eine [Cursor](cursors.md) , des Benutzers Blicke darstellt. Dadurch wird das Vertrauen in Was sind zu interagieren.

## <a name="gaze-in-mixed-reality-toolkit"></a>Bestaunen Sie in Mixed Reality-Toolkit
Beim Importieren von [MRTK releasepakete Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) oder Klonen Sie das Projekt aus der [GitHub-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), Sie sind dabei, ein neues Menü "Mixed Reality-Toolkit" in Unity finden. Klicken Sie im Menü "Mixed Reality Szene-Einstellungen anwenden" wird unter "Konfigurieren" im Menü angezeigt. Wenn Sie darauf klicken, wird er entfernt die Standardkamera und fügt grundlegende Komponenten - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), und [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![MRTK-Menü für die Szene-setup](images/MRTK_Input_Menu.png)<br>
*MRTK-Menü für die Szene-setup*

![Automatische Szene Setup in MRTK](images/MRTK_HowTo_Input1.png)<br>
*Automatische Szene Setup in MRTK*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>Bestaunen Sie zusammengehörigen Skripts zu Mixed Reality-Toolkit
Mixed Reality-Toolkit InputManager prefab enthält [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) und [bestaunen Stabilisierung](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs). Klicken Sie unter [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), Sie können Ihre benutzerdefinierten Cursor zuweisen. Im standardmäßigen, animiert [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) zugewiesen wird.

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) und [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) erfahren Sie, wie Sie Ihre Blicke Verwenden von Cursorn zu visualisieren.

## <a name="see-also"></a>Siehe auch
* [Kamera](camera-in-unity.md)
* [Blicke](gaze.md)
* [Cursor](cursors.md)
* [Blicke für](gaze-targeting.md)
