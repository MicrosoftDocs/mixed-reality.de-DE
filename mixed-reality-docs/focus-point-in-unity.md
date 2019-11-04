---
title: Fokuspunkt in Unity
description: Manuelles Optimieren der – Hologramm-Stabilität in Unity durch Festlegen des Fokus Punkts
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Fokuspunkt, Fokusebene, Stabilisierungs Ebene, Stabilisierungs Punkt, neuprojektion, LSR, tiefen Puffer
ms.openlocfilehash: d48f6f1878a68a17be263f10b809229dc2705c58
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435412"
---
# <a name="focus-point-in-unity"></a>Fokuspunkt in Unity

**Namespace:** *unityengine. XR. WSA*<br>
**Typ**: *holographicsettings*

Der [Fokuspunkt](hologram-stability.md#reprojection) kann so festgelegt werden, dass hololens einen Hinweis zur optimalen Durchführung der Stabilisierung auf den derzeit angezeigten holograms bereitstellt.

Wenn Sie den Fokuspunkt in Unity festlegen möchten, muss er jedes Frame mithilfe von *holographicsettings. setfocuspointforframe ()* festgelegt werden. Wenn der Fokuspunkt nicht für einen Frame festgelegt ist, wird die Standard Stabilisierungs Ebene verwendet.

> [!NOTE]
> In neuen Unity-Projekten ist die Option "Tiefe Puffer Freigabe aktivieren" standardmäßig festgelegt.  Mit dieser Option übermittelt eine Unity-APP, die auf einem immersiven Desktop-Headset oder einem hololens ausgeführt wird, auf dem das Windows 10 April 2018 Update (RS4) oder höher ausgeführt wird, ihren tiefen Puffer an Windows, um die – Hologramm-Stabilität automatisch zu optimieren, ohne dass Ihre APP eine Fokuspunkt:
> * Auf einem immersiven Desktop-Headset wird dadurch eine auf pro Pixel basierende Reprojektion ermöglicht.
> * Auf einem hololens, auf dem das Windows 10-Update vom April 2018 oder höher ausgeführt wird, wird der tiefen Puffer analysiert, um automatisch eine optimale Stabilisierungs Ebene auszuwählen.
>
> Beide Ansätze sollten eine noch bessere Bildqualität bieten, ohne dass Sie von Ihrer APP explizit arbeiten müssen, um einen Fokuspunkt für jeden Frame auszuwählen.  Beachten Sie Folgendes: Wenn Sie einen Schwerpunkt Punkt manuell angeben, wird das oben beschriebene automatische Verhalten überschrieben, und die Stabilität des Hologramms wird normalerweise verringert.  Im Allgemeinen sollten Sie nur dann einen manuellen Fokuspunkt angeben, wenn die APP auf einem hololens ausgeführt wird, der noch nicht auf das Windows 10-Update vom April 2018 aktualisiert wurde.

### <a name="example"></a>Beispiel

Es gibt viele Möglichkeiten, den Schwerpunkt Punkt festzulegen, wie von den über Ladungen für die statische Funktion *setfocuspointforframe* vorgeschlagen. Im folgenden finden Sie ein einfaches Beispiel für die Festlegung der Fokusebene auf das bereitgestellte Objekt jedes Frames:

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

Beachten Sie, dass der obige einfache Code möglicherweise zu einer Verringerung der – Hologramm-Stabilität wird, wenn das fokussierte Objekt hinter dem Benutzer endet.  Daher sollten Sie in der Regel "Tiefe Puffer Freigabe aktivieren" festlegen, anstatt manuell einen Fokuspunkt anzugeben.

### <a name="see-also"></a>Weitere Informationen:
* [Stabilisierungs Ebene](hologram-stability.md#reprojection)
