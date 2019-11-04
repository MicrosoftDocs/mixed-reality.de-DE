---
title: Native Reality-Objekte in Unity
description: Erhalten Sie Zugriff auf die zugrunde liegenden Holographic Native-Objekte in Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, Mixed Reality, Native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 975775f64a19fe5fff4bc395a3e954cbf529dfa9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437335"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="8da39-104">Native Reality-Objekte in Unity</span><span class="sxs-lookup"><span data-stu-id="8da39-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="8da39-105">Das [erhalten eines holographicspace](getting-a-holographicspace.md) ist das, was jede gemischte Reality-APP tut, bevor Sie mit dem Empfang von Kameradaten und renderingframes beginnt</span><span class="sxs-lookup"><span data-stu-id="8da39-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="8da39-106">In Unity übernimmt die Engine diese Schritte für Sie und verarbeitet holografische Objekte und Updates intern als Teil der Renderschleife.</span><span class="sxs-lookup"><span data-stu-id="8da39-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="8da39-107">In erweiterten Szenarien müssen Sie jedoch möglicherweise Zugriff auf die zugrunde liegenden systemeigenen Objekte erhalten, wie z. b. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">holographiccamera</a> und Current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a>.</span><span class="sxs-lookup"><span data-stu-id="8da39-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="8da39-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. xrdevice</a> ermöglicht den Zugriff auf diese systemeigenen Objekte.</span><span class="sxs-lookup"><span data-stu-id="8da39-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="8da39-109">Xrdevice</span><span class="sxs-lookup"><span data-stu-id="8da39-109">XRDevice</span></span> 

<span data-ttu-id="8da39-110">**Namespace:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="8da39-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="8da39-111">**Typ:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="8da39-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="8da39-112">Der *xrdevice* -Typ ermöglicht es Ihnen, mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">getnativeptr</a> -Methode Zugriff auf zugrunde liegende Native Objekte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8da39-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="8da39-113">Was getnativeptr zurückgibt, variiert zwischen verschiedenen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="8da39-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="8da39-114">Auf dem universelle Windows-Plattform gibt xrdevice. getnativeptr einen Zeiger (IntPtr) auf die folgende Struktur zurück, wenn das Windows Mixed Reality-SDK-SDK als Ziel verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="8da39-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="8da39-115">Sie können es mithilfe der Marshal. ptrumstructure-Methode in holographicframenativedata konvertieren:</span><span class="sxs-lookup"><span data-stu-id="8da39-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="8da39-116">***Iholographiccameraptr** ist ein Array von IntPtr, das als UnmanagedType. ByValArray gemarshallt wird, wobei eine Länge gleich maxnumofkameras ist.*</span><span class="sxs-lookup"><span data-stu-id="8da39-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="8da39-117">Nicht Marshalling nativer Zeiger</span><span class="sxs-lookup"><span data-stu-id="8da39-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="8da39-118">Wenn Sie [Microsoft. Windows. mixedreality. dotnetwinrt](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) verwenden, können Sie mithilfe der `FromNativePtr()`-Methode ein verwaltetes Objekt aus einem nativen Zeiger erstellen:</span><span class="sxs-lookup"><span data-stu-id="8da39-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="8da39-119">Verwenden Sie andernfalls `Marshal.GetObjectForIUnknown()` und in den gewünschten Typ umwandeln:</span><span class="sxs-lookup"><span data-stu-id="8da39-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the desired type:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="8da39-120">Zwischen Koordinatensystemen</span><span class="sxs-lookup"><span data-stu-id="8da39-120">Converting between coordinate systems</span></span>

<span data-ttu-id="8da39-121">Unity verwendet ein Links händiges Koordinatensystem, während die Windows-perception-APIs rechts gerichtete Koordinatensysteme verwenden.</span><span class="sxs-lookup"><span data-stu-id="8da39-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="8da39-122">Zum Konvertieren zwischen diesen beiden Konventionen können Sie die folgenden Hilfsprogramme verwenden:</span><span class="sxs-lookup"><span data-stu-id="8da39-122">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="8da39-123">Verwenden von systemeigenen holographicframe-Daten</span><span class="sxs-lookup"><span data-stu-id="8da39-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="8da39-124">Das Ändern des Zustands der systemeigenen Objekte, die über holographicframenativedata empfangen werden, kann zu unvorhersehbarem Verhalten und Rendern von Artefakten führen, insbesondere dann, wenn Unity auch für denselben Zustand verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="8da39-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="8da39-125">Sie sollten z. b. holographicframe. updatecurrentvorhersage nicht aufrufen, oder andernfalls ist die Pose-Vorhersage, die Unity mit diesem Frame rendert, nicht mit der von Windows erwarteten Pose synchron. Dadurch wird die [– Hologramm-Stabilität](hologram-stability.md)reduziert.</span><span class="sxs-lookup"><span data-stu-id="8da39-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="8da39-126">Sie können Daten von holographicframenativedata verwenden, wenn der Zugriff auf systemeigene Schnittstellen zum Rendern oder Debuggen in Ihren C# nativen Plug-ins oder Code erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="8da39-126">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="8da39-127">Im folgenden finden Sie ein Beispiel dafür, wie Sie holographicframenativedata verwenden können, um die Vorhersage des aktuellen Frames für die Photonen Zeit zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8da39-127">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="8da39-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8da39-128">See Also</span></span>
* [<span data-ttu-id="8da39-129">Verwenden des Windows-Namespace mit Unity-Apps für HoloLens</span><span class="sxs-lookup"><span data-stu-id="8da39-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="8da39-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">Spatialcoordinatesystem</a></span><span class="sxs-lookup"><span data-stu-id="8da39-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="8da39-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Holographicframe</a></span><span class="sxs-lookup"><span data-stu-id="8da39-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="8da39-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="8da39-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="8da39-133">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="8da39-133">Rendering in DirectX</span></span>](rendering-in-directx.md)
