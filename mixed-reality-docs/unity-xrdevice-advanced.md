---
title: Native Reality-Objekte in Unity
description: Erhalten Sie Zugriff auf die zugrunde liegenden Holographic Native-Objekte in Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, Mixed Reality, Native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942096"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="9911b-104">Native Reality-Objekte in Unity</span><span class="sxs-lookup"><span data-stu-id="9911b-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="9911b-105">Das [erhalten eines holographicspace](getting-a-holographicspace.md) ist das, was jede gemischte Reality-APP tut, bevor Sie mit dem Empfang von Kameradaten und renderingframes beginnt</span><span class="sxs-lookup"><span data-stu-id="9911b-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="9911b-106">In Unity übernimmt die Engine diese Schritte für Sie und verarbeitet holografische Objekte und Updates intern als Teil der Renderschleife.</span><span class="sxs-lookup"><span data-stu-id="9911b-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="9911b-107">In erweiterten Szenarien müssen Sie jedoch möglicherweise Zugriff auf die zugrunde liegenden systemeigenen Objekte erhalten, wie z. b. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">holographiccamera</a> und Current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a>.</span><span class="sxs-lookup"><span data-stu-id="9911b-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="9911b-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. xrdevice</a> ermöglicht den Zugriff auf diese systemeigenen Objekte.</span><span class="sxs-lookup"><span data-stu-id="9911b-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="9911b-109">Xrdevice</span><span class="sxs-lookup"><span data-stu-id="9911b-109">XRDevice</span></span> 

<span data-ttu-id="9911b-110">**Namespace:** *Unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="9911b-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9911b-111">**Sorte** *Xrdevice*</span><span class="sxs-lookup"><span data-stu-id="9911b-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="9911b-112">Der *xrdevice* -Typ ermöglicht es Ihnen, mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">getnativeptr</a> -Methode Zugriff auf zugrunde liegende Native Objekte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9911b-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="9911b-113">Was getnativeptr zurückgibt, variiert zwischen verschiedenen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="9911b-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="9911b-114">Auf dem universelle Windows-Plattform gibt xrdevice. getnativeptr einen Zeiger (IntPtr) auf die folgende Struktur zurück, wenn das Windows Mixed Reality-SDK-SDK als Ziel verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="9911b-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="9911b-115">Sie können es mithilfe der Marshal. ptrumstructure-Methode in holographicframenativedata konvertieren:</span><span class="sxs-lookup"><span data-stu-id="9911b-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="9911b-116">***Iholographiccameraptr** ist ein Array von IntPtr, das als UnmanagedType. ByValArray gemarshallt wird, wobei eine Länge gleich maxnumofkameras ist.*</span><span class="sxs-lookup"><span data-stu-id="9911b-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="9911b-117">Verwenden von holographicframenativedata</span><span class="sxs-lookup"><span data-stu-id="9911b-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="9911b-118">Das Ändern des Zustands der systemeigenen Objekte, die über holographicframenativedata empfangen werden, kann zu unvorhersehbarem Verhalten und Rendern von Artefakten führen, insbesondere dann, wenn Unity auch für denselben Zustand verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="9911b-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="9911b-119">Sie sollten z. b. holographicframe. updatecurrentvorhersage nicht aufrufen, oder andernfalls ist die Pose-Vorhersage, die Unity mit diesem Frame rendert, nicht mit der von Windows erwarteten Pose synchron. Dadurch wird die [– Hologramm-Stabilität](hologram-stability.md)reduziert.</span><span class="sxs-lookup"><span data-stu-id="9911b-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="9911b-120">Sie können Daten von holographicframenativedata verwenden, wenn der Zugriff auf systemeigene Schnittstellen zum Rendern oder Debuggen in Ihren C# nativen Plug-ins oder Code erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9911b-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="9911b-121">Im folgenden finden Sie ein Beispiel dafür, wie Sie holographicframenativedata verwenden können, um die Vorhersage des aktuellen Frames für die Photonen Zeit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9911b-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="9911b-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9911b-122">See Also</span></span>
* <span data-ttu-id="9911b-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">Spatialcoordinatesystem</a></span><span class="sxs-lookup"><span data-stu-id="9911b-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="9911b-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Holographicframe</a></span><span class="sxs-lookup"><span data-stu-id="9911b-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="9911b-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="9911b-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="9911b-126">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="9911b-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
