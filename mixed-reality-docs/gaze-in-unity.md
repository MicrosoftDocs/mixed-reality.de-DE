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
# <a name="head-gaze-in-unity"></a>Kopf Blicke in Unity

Der Blick ist eine primäre Möglichkeit für Benutzer, die [Hologramme](hologram.md) , die Ihre APP in [gemischter Realität](mixed-reality.md)erstellt, als Ziel zu [betrachten](gaze.md) .


## <a name="implementing-head-gaze"></a>Implementieren des Head-Blicks

Konzeptionell wird der [Blick](gaze.md) durch die Projektion eines Strahls aus dem Head des Benutzers, an dem sich das Headset befindet, in der Vorwärtsrichtung implementiert, und es wird festgelegt, mit welchem Strahl dieses Ray kollidiert. In Unity werden die Head-Position und die Richtung des Benutzers über die Unity-Haupt [Kamera](camera-in-unity.md), insbesondere [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html), verfügbar gemacht. [Transform. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Der Aufruf von " [Physik. raycast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " führt zu einer [raycasthit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) -Struktur, die Informationen über den Konflikt enthält, einschließlich des 3D-Punkts, bei dem der Konflikt aufgetreten ist, und des anderen gameobject, mit dem der Blick

### <a name="example-implement-head-gaze"></a>Beispiel: Implementieren des Haupt Blicks

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

Obwohl das obige Beispiel zeigt, wie ein einzelnes raycast in einer Update-Schleife ausgeführt wird, um das Suchziel zu finden, empfiehlt es sich, dies in einem einzelnen Objekt zu tun, das den Blick verwaltet, anstatt dies in einem Objekt zu tun, das potenziell an dem Objekt interessiert ist, bei dem es sich befindet. Dadurch kann Ihre APP die Verarbeitung speichern, indem Sie nur einen Blick auf jeden Frame durchläuft.

## <a name="visualizing-gaze"></a>Visualisieren des Blicks

Ebenso wie auf dem Desktop, auf dem Sie mit einem Mauszeiger auf Inhalte abzielen und mit ihnen interagieren, sollten Sie einen [Cursor](cursors.md) implementieren, der den Blick des Benutzers darstellt. Dadurch erhält der Benutzer Vertrauen in das, was Sie im Begriff sind, mit zu interagieren.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Blick in Mixed Reality Toolkit v2
Sie können über den Eingabe- [Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk v2 auf den Blick zugreifen.

## <a name="see-also"></a>Siehe auch
* [Kamera](camera-in-unity.md)
* [Blick Eingabe](gaze.md)
* [Cursor](cursors.md)
* [Anvisieren](gaze-targeting.md)
