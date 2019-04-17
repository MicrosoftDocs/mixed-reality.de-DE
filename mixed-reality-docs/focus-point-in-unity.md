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
# <a name="focus-point-in-unity"></a><span data-ttu-id="029ba-104">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="029ba-104">Focus point in Unity</span></span>

<span data-ttu-id="029ba-105">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="029ba-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="029ba-106">**Typ**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="029ba-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="029ba-107">Die [konzentrieren Punkt](hologram-stability.md#stabilization-plane) kann angezeigt werden, auf HoloLens Geben Sie einen Hinweis dazu, wie Sie am besten Stabilisierung auf die Hologramme Grundsatzes festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="029ba-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="029ba-108">Wenn der Fokuspunkt in Unity festgelegt werden sollen, muss jeder Frame mit festgelegt werden *HolographicSettings.SetFocusPointForFrame()*.</span><span class="sxs-lookup"><span data-stu-id="029ba-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="029ba-109">Wenn der Fokus Punkt für einen Frame nicht festgelegt ist, wird die standardmäßige Stabilisierung-Ebene verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="029ba-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="029ba-110">Standardmäßig können neue Unity-Projekte "Tiefe Puffer Freigabe aktivieren" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="029ba-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="029ba-111">Mit dieser Option eine Unity-app auf eine immersive desktop Kopfhörer oder eine HoloLens, mit der Windows 10 April 2018 Update (RS4) oder höher wird Ihre Tiefenpuffer zu Windows – Hologramm Stabilität automatisch, ohne Ihrer app optimieren Übermitteln einer Fokuspunkt:</span><span class="sxs-lookup"><span data-stu-id="029ba-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="029ba-112">Für eine immersive desktop Kopfhörer wird diese pro-Pixel-Depth-basierte Reprojection aktivieren.</span><span class="sxs-lookup"><span data-stu-id="029ba-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="029ba-113">Klicken Sie auf eine HoloLens Ausführen der Windows 10 April 2018 aktualisieren oder diese später analysiert den Tiefenpuffer, um eine optimale Stabilisierung Ebene automatisch ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="029ba-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="029ba-114">Beide Ansätze sollten noch bessere Bildqualität ohne explizite von Ihrer app auf einen Zeitpunkt fokusmodus auszuwählen jeden Frame bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="029ba-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="029ba-115">Beachten Sie, dass wenn Sie einen Fokuspunkt manuell bereitstellen, wird das oben beschriebene automatische Verhalten überschreiben, und – Hologramm Stabilität in der Regel reduziert.</span><span class="sxs-lookup"><span data-stu-id="029ba-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="029ba-116">Im Allgemeinen sollten Sie nur einen manuelle Fokuspunkt beim Angeben Ihrer app auf einem HoloLens ausgeführt wird, die noch nicht auf dem Windows aktualisiert wurde 10 April 2018 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="029ba-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="029ba-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="029ba-117">Example</span></span>

<span data-ttu-id="029ba-118">Es gibt viele Möglichkeiten, legen Sie den Fokuspunkt gemäß dem Vorschlag von Überladungen verfügbar, auf die *SetFocusPointForFrame* statische Funktion.</span><span class="sxs-lookup"><span data-stu-id="029ba-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="029ba-119">Unten ist ein einfaches Beispiel für der Ebene der Fokus auf das angegebene Objekt jeden Frame festgelegt:</span><span class="sxs-lookup"><span data-stu-id="029ba-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

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

<span data-ttu-id="029ba-120">Beachten Sie, dass es sich bei der oben angegebenen einfachen Code – Hologramm Stabilität reduzieren, wenn das fokussierte Objekt hinter der Benutzer am Ende aufweisen kann.</span><span class="sxs-lookup"><span data-stu-id="029ba-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="029ba-121">Daher ist Sie in der Regel "Tiefe Puffer Freigabe aktivieren" festlegen sollten anstatt manuell einem Zeitpunkt fokusmodus.</span><span class="sxs-lookup"><span data-stu-id="029ba-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="029ba-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="029ba-122">See also</span></span>
* [<span data-ttu-id="029ba-123">Stabilisierung-Ebene</span><span class="sxs-lookup"><span data-stu-id="029ba-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
