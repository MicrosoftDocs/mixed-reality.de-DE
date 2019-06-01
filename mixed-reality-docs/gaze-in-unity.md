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
# <a name="head-gaze-in-unity"></a>Head Blicke in Unity

[Bestaunen](gaze.md) ist ein primärer Weg für Benutzer als Ziel der [Hologramme](hologram.md) Ihrer app erstellt in [Mixed Reality](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementierende Head Blicke

Im Prinzip [bestaunen](gaze.md) wird durch Projizieren ein Strahl aus, in denen die Kopfhörer ist, vorwärts sie konfrontiert sind, und bestimmen, des Benutzers-Head implementiert das Chow verursacht einen Konflikt mit. In Unity Head-Position des Benutzers und die Richtung sind verfügbar gemacht werden über der Unity-Hauptseite [Kamera](camera-in-unity.md), insbesondere [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ "Transform.Position"](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Aufrufen von [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) führt zu einem [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) Struktur enthält Informationen zu den Konflikt, einschließlich der 3D-Punkts, in dem Konflikt aufgetreten ist, und die anderen "gameobject" Blicke Strahl widersprachen.

### <a name="example-implement-head-gaze"></a>Beispiel: Head Blicke implementieren

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

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>In Mixed Reality bestaunen Toolkit v2
Sie erreichen die Blicke, aus der [Eingabe Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.

## <a name="see-also"></a>Siehe auch
* [Kamera](camera-in-unity.md)
* [Blickverlaufseingabe](gaze.md)
* [Cursor](cursors.md)
* [Anvisieren](gaze-targeting.md)
