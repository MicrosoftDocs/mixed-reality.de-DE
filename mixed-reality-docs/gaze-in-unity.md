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
# <a name="head-gaze-in-unity"></a>Kopf schauen in Unity

Der Blick ist eine primäre Möglichkeit für Benutzer, die [Hologramme](hologram.md) , die Ihre APP in [gemischter Realität](mixed-reality.md)erstellt, als Ziel zu [betrachten](gaze.md) .


## <a name="implementing-head-gaze"></a>Implementieren von Head-Gaze

Konzeptionell wird die [Kopfzeile](gaze.md) implementiert, indem ein Strahl von der Kopfzeile des Benutzers projiziert wird, an der sich das Headset befindet, und in der Vorwärtsrichtung, mit der der Strahl in Konflikt steht. In Unity werden die Head-Position und die Richtung des Benutzers über die Unity-Haupt [Kamera](camera-in-unity.md), insbesondere [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html), verfügbar gemacht. [Transform. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Das Aufrufen von " [Physik. raycast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " führt zu einer [raycasthit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) -Struktur, die Informationen über den Konflikt enthält, einschließlich des 3D-Punkts, bei dem der Konflikt aufgetreten ist, und des anderen gameobject, mit dem der Kopf-und

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

### <a name="best-practices"></a>Empfohlene Methoden

Obwohl das obige Beispiel zeigt, wie ein einzelnes raycast in einer Update-Schleife ausgeführt wird, um das Ziel der Hauptbenutzer des Benutzers zu finden, empfiehlt es sich, dies in einem einzelnen Objekt zu tun, das die Kopfzeile verwaltet, anstatt dies in einem Objekt zu tun, das potenziell an dem Agentsoftware interessiert ist. t wird bei der Eingabe von. Dadurch kann Ihre APP die Verarbeitung speichern, indem Sie für jeden Frame nur einen Head-Gaze-raycast durchgeführt wird.

## <a name="visualizing-head-gaze"></a>Visualisieren des Haupt Blicks

Ebenso wie auf dem Desktop, auf dem Sie mit einem Mauszeiger auf Inhalte abzielen und mit ihnen interagieren, sollten Sie einen [Cursor](cursors.md) implementieren, der die Kopfzeile des Benutzers darstellt. Dadurch erhält der Benutzer Vertrauen in das, was Sie im Begriff sind, mit zu interagieren.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Der Haupt Blick im Mixed Reality Toolkit v2
Sie können über den [Eingabe-Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk v2 auf den Haupt Blick zugreifen.

## <a name="see-also"></a>Siehe auch
* [Kamera](camera-in-unity.md)
* [Cursor](cursors.md)
* [Blick Eingabe](gaze.md)
* [Anvisieren](gaze-targeting.md)
