---
title: Gemischte Realität, systemeigene Objekte in Unity
description: Erhalten Sie Zugriff auf die zugrunde liegenden Holographic systemeigene Objekte in Unity ein.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, mixed Reality, systemeigen, Xrdevice, Spatialcoordinatesystem, Holographicframe, Holographiccamera, Ispatialcoordinatesystem, Iholographicframe, Iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942096"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="9a286-104">Gemischte Realität, systemeigene Objekte in Unity</span><span class="sxs-lookup"><span data-stu-id="9a286-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="9a286-105">[Abrufen einer HolographicSpace](getting-a-holographicspace.md) ist, was jede Mixed Reality-app ist, bevor es gestartet wird, Empfangen von Kameradaten und das rendering von frames.</span><span class="sxs-lookup"><span data-stu-id="9a286-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="9a286-106">In Unity das Modul übernimmt diese Schritte für Sie Holographic Objekte behandeln und intern als Teil seiner renderloop aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="9a286-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="9a286-107">Allerdings in erweiterten Szenarien müssen Sie möglicherweise für den Zugriff auf die zugrunde liegende systemeigene Objekte, z. B. die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> und den aktuellen <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span><span class="sxs-lookup"><span data-stu-id="9a286-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="9a286-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> ist, was den Zugriff auf diese systemeigene Objekte bietet.</span><span class="sxs-lookup"><span data-stu-id="9a286-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="9a286-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="9a286-109">XRDevice</span></span> 

<span data-ttu-id="9a286-110">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="9a286-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9a286-111">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="9a286-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="9a286-112">Die *XRDevice* Typ ermöglicht Ihnen das Zugreifen auf zugrunde liegende systemeigene Objekte, die mit der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> Methode.</span><span class="sxs-lookup"><span data-stu-id="9a286-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="9a286-113">Was GetNativePtr zurückgibt variiert zwischen verschiedenen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="9a286-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="9a286-114">XRDevice.GetNativePtr gibt einen Zeiger (IntPtr) für die universelle Windows-Plattform, bei Windows Mixed Reality XR SDK als Ziel die folgende Struktur zurück:</span><span class="sxs-lookup"><span data-stu-id="9a286-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="9a286-115">Sie können in HolographicFrameNativeData mit Marshal.PtrToStructure-Methode konvertieren:</span><span class="sxs-lookup"><span data-stu-id="9a286-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="9a286-116">***IHolographicCameraPtr** ist ein Array von IntPtr als UnmanagedType.ByValArray gemarshallt werden, mit einer Länge gleich MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="9a286-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="9a286-117">Verwenden von HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="9a286-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="9a286-118">Ändern des Status der nativen Objekte über HolographicFrameNativeData empfangen kann zu unvorhersehbaren Verhalten und Rendern von Artefakten, verursachen, besonders wenn Unity auch Informationen zu diesen gleichen Zustand Gründe.</span><span class="sxs-lookup"><span data-stu-id="9a286-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="9a286-119">Z. B. HolographicFrame.UpdateCurrentPrediction sollte nicht aufgerufen werden, da ansonsten die Haltung Vorhersage, die Unity mit diesen Frame gerendert wird, werden nicht mehr synchron mit der Haltung, die Windows erwartet wird, zu reduzieren, [– Hologramm Stabilität](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="9a286-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="9a286-120">Sie können Daten aus HolographicFrameNativeData verwenden, wenn der Zugriff auf systemeigene Schnittstellen für das Rendern oder das Debuggen verwendet werden, in Ihre native-Plug-Ins erforderlich ist oder C# Code.</span><span class="sxs-lookup"><span data-stu-id="9a286-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="9a286-121">Hier ist ein Beispiel, wie Sie HolographicFrameNativeData verwenden können, um den aktuellen Frame Vorhersage Photon Zeit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9a286-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="9a286-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9a286-122">See Also</span></span>
* <span data-ttu-id="9a286-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="9a286-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="9a286-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="9a286-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="9a286-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="9a286-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="9a286-126">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="9a286-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
