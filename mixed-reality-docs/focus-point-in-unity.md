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
# <a name="focus-point-in-unity"></a><span data-ttu-id="f2264-104">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="f2264-104">Focus point in Unity</span></span>

<span data-ttu-id="f2264-105">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="f2264-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="f2264-106">**Typ**: *holographicsettings*</span><span class="sxs-lookup"><span data-stu-id="f2264-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="f2264-107">Der [Fokuspunkt](hologram-stability.md#reprojection) kann so festgelegt werden, dass hololens einen Hinweis zur optimalen Durchführung der Stabilisierung auf den derzeit angezeigten holograms bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="f2264-107">The [focus point](hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="f2264-108">Wenn Sie den Fokuspunkt in Unity festlegen möchten, muss er jedes Frame mithilfe von *holographicsettings. setfocuspointforframe ()* festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f2264-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="f2264-109">Wenn der Fokuspunkt nicht für einen Frame festgelegt ist, wird die Standard Stabilisierungs Ebene verwendet.</span><span class="sxs-lookup"><span data-stu-id="f2264-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="f2264-110">In neuen Unity-Projekten ist die Option "Tiefe Puffer Freigabe aktivieren" standardmäßig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2264-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="f2264-111">Mit dieser Option übermittelt eine Unity-APP, die auf einem immersiven Desktop-Headset oder einem hololens ausgeführt wird, auf dem das Windows 10 April 2018 Update (RS4) oder höher ausgeführt wird, ihren tiefen Puffer an Windows, um die – Hologramm-Stabilität automatisch zu optimieren, ohne dass Ihre APP eine Fokuspunkt:</span><span class="sxs-lookup"><span data-stu-id="f2264-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="f2264-112">Auf einem immersiven Desktop-Headset wird dadurch eine auf pro Pixel basierende Reprojektion ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f2264-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="f2264-113">Auf einem hololens, auf dem das Windows 10-Update vom April 2018 oder höher ausgeführt wird, wird der tiefen Puffer analysiert, um automatisch eine optimale Stabilisierungs Ebene auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f2264-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="f2264-114">Beide Ansätze sollten eine noch bessere Bildqualität bieten, ohne dass Sie von Ihrer APP explizit arbeiten müssen, um einen Fokuspunkt für jeden Frame auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f2264-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="f2264-115">Beachten Sie Folgendes: Wenn Sie einen Schwerpunkt Punkt manuell angeben, wird das oben beschriebene automatische Verhalten überschrieben, und die Stabilität des Hologramms wird normalerweise verringert.</span><span class="sxs-lookup"><span data-stu-id="f2264-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="f2264-116">Im Allgemeinen sollten Sie nur dann einen manuellen Fokuspunkt angeben, wenn die APP auf einem hololens ausgeführt wird, der noch nicht auf das Windows 10-Update vom April 2018 aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f2264-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="f2264-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f2264-117">Example</span></span>

<span data-ttu-id="f2264-118">Es gibt viele Möglichkeiten, den Schwerpunkt Punkt festzulegen, wie von den über Ladungen für die statische Funktion *setfocuspointforframe* vorgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="f2264-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="f2264-119">Im folgenden finden Sie ein einfaches Beispiel für die Festlegung der Fokusebene auf das bereitgestellte Objekt jedes Frames:</span><span class="sxs-lookup"><span data-stu-id="f2264-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

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

<span data-ttu-id="f2264-120">Beachten Sie, dass der obige einfache Code möglicherweise zu einer Verringerung der – Hologramm-Stabilität wird, wenn das fokussierte Objekt hinter dem Benutzer endet.</span><span class="sxs-lookup"><span data-stu-id="f2264-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="f2264-121">Daher sollten Sie in der Regel "Tiefe Puffer Freigabe aktivieren" festlegen, anstatt manuell einen Fokuspunkt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="f2264-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="f2264-122">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f2264-122">See also</span></span>
* [<span data-ttu-id="f2264-123">Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="f2264-123">Stabilization plane</span></span>](hologram-stability.md#reprojection)
