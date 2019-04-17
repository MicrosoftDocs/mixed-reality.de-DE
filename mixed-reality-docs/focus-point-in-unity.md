---
title: Fokuspunkt in Unity
description: Manuell – Hologramm Stabilität in Unity durch Festlegen der Fokuspunkt optimieren
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Fokuspunkt, den Fokus Ebene, Stabilisierung-Ebene, Stabilisierung Point, Reprojection, LSR, Tiefenpuffer
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604884"
---
# <a name="focus-point-in-unity"></a>Fokuspunkt in Unity

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ**: *HolographicSettings*

Die [konzentrieren Punkt](hologram-stability.md#stabilization-plane) kann angezeigt werden, auf HoloLens Geben Sie einen Hinweis dazu, wie Sie am besten Stabilisierung auf die Hologramme Grundsatzes festgelegt wird.

Wenn der Fokuspunkt in Unity festgelegt werden sollen, muss jeder Frame mit festgelegt werden *HolographicSettings.SetFocusPointForFrame()*. Wenn der Fokus Punkt für einen Frame nicht festgelegt ist, wird die standardmäßige Stabilisierung-Ebene verwendet werden.

> [!NOTE]
> Standardmäßig können neue Unity-Projekte "Tiefe Puffer Freigabe aktivieren" festgelegt.  Mit dieser Option eine Unity-app auf eine immersive desktop Kopfhörer oder eine HoloLens, mit der Windows 10 April 2018 Update (RS4) oder höher wird Ihre Tiefenpuffer zu Windows – Hologramm Stabilität automatisch, ohne Ihrer app optimieren Übermitteln einer Fokuspunkt:
> * Für eine immersive desktop Kopfhörer wird diese pro-Pixel-Depth-basierte Reprojection aktivieren.
> * Klicken Sie auf eine HoloLens Ausführen der Windows 10 April 2018 aktualisieren oder diese später analysiert den Tiefenpuffer, um eine optimale Stabilisierung Ebene automatisch ausgewählt.
>
> Beide Ansätze sollten noch bessere Bildqualität ohne explizite von Ihrer app auf einen Zeitpunkt fokusmodus auszuwählen jeden Frame bereitstellen.  Beachten Sie, dass wenn Sie einen Fokuspunkt manuell bereitstellen, wird das oben beschriebene automatische Verhalten überschreiben, und – Hologramm Stabilität in der Regel reduziert.  Im Allgemeinen sollten Sie nur einen manuelle Fokuspunkt beim Angeben Ihrer app auf einem HoloLens ausgeführt wird, die noch nicht auf dem Windows aktualisiert wurde 10 April 2018 aktualisieren.

### <a name="example"></a>Beispiel

Es gibt viele Möglichkeiten, legen Sie den Fokuspunkt gemäß dem Vorschlag von Überladungen verfügbar, auf die *SetFocusPointForFrame* statische Funktion. Unten ist ein einfaches Beispiel für der Ebene der Fokus auf das angegebene Objekt jeden Frame festgelegt:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

Beachten Sie, dass es sich bei der oben angegebenen einfachen Code – Hologramm Stabilität reduzieren, wenn das fokussierte Objekt hinter der Benutzer am Ende aufweisen kann.  Daher ist Sie in der Regel "Tiefe Puffer Freigabe aktivieren" festlegen sollten anstatt manuell einem Zeitpunkt fokusmodus.

### <a name="see-also"></a>Siehe auch
* [Stabilisierung-Ebene](hologram-stability.md#stabilization-plane)
