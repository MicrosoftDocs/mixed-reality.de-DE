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
# <a name="mixed-reality-native-objects-in-unity"></a>Native Reality-Objekte in Unity

Das [erhalten eines holographicspace](getting-a-holographicspace.md) ist das, was jede gemischte Reality-APP tut, bevor Sie mit dem Empfang von Kameradaten und renderingframes beginnt In Unity übernimmt die Engine diese Schritte für Sie und verarbeitet holografische Objekte und Updates intern als Teil der Renderschleife.

In erweiterten Szenarien müssen Sie jedoch möglicherweise Zugriff auf die zugrunde liegenden systemeigenen Objekte erhalten, wie z. b. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">holographiccamera</a> und Current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. xrdevice</a> ermöglicht den Zugriff auf diese systemeigenen Objekte.

## <a name="xrdevice"></a>Xrdevice 

**Namespace:** *unityengine. XR*<br>
**Typ:** *xrdevice*

Der *xrdevice* -Typ ermöglicht es Ihnen, mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">getnativeptr</a> -Methode Zugriff auf zugrunde liegende Native Objekte zu erhalten. Was getnativeptr zurückgibt, variiert zwischen verschiedenen Plattformen. Auf dem universelle Windows-Plattform gibt xrdevice. getnativeptr einen Zeiger (IntPtr) auf die folgende Struktur zurück, wenn das Windows Mixed Reality-SDK-SDK als Ziel verwendet wird: 

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
Sie können es mithilfe der Marshal. ptrumstructure-Methode in holographicframenativedata konvertieren:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***Iholographiccameraptr** ist ein Array von IntPtr, das als UnmanagedType. ByValArray gemarshallt wird, wobei eine Länge gleich maxnumofkameras ist.* 

### <a name="unmarshaling-native-pointers"></a>Nicht Marshalling nativer Zeiger

Wenn Sie [Microsoft. Windows. mixedreality. dotnetwinrt](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) verwenden, können Sie mithilfe der `FromNativePtr()`-Methode ein verwaltetes Objekt aus einem nativen Zeiger erstellen:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

Verwenden Sie andernfalls `Marshal.GetObjectForIUnknown()` und in den gewünschten Typ umwandeln:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>Zwischen Koordinatensystemen

Unity verwendet ein Links händiges Koordinatensystem, während die Windows-perception-APIs rechts gerichtete Koordinatensysteme verwenden. Zum Konvertieren zwischen diesen beiden Konventionen können Sie die folgenden Hilfsprogramme verwenden:

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

### <a name="using-holographicframe-native-data"></a>Verwenden von systemeigenen holographicframe-Daten

> [!NOTE]
> Das Ändern des Zustands der systemeigenen Objekte, die über holographicframenativedata empfangen werden, kann zu unvorhersehbarem Verhalten und Rendern von Artefakten führen, insbesondere dann, wenn Unity auch für denselben Zustand verantwortlich ist.  Sie sollten z. b. holographicframe. updatecurrentvorhersage nicht aufrufen, oder andernfalls ist die Pose-Vorhersage, die Unity mit diesem Frame rendert, nicht mit der von Windows erwarteten Pose synchron. Dadurch wird die [– Hologramm-Stabilität](hologram-stability.md)reduziert.

Sie können Daten von holographicframenativedata verwenden, wenn der Zugriff auf systemeigene Schnittstellen zum Rendern oder Debuggen in Ihren C# nativen Plug-ins oder Code erforderlich ist. 

Im folgenden finden Sie ein Beispiel dafür, wie Sie holographicframenativedata verwenden können, um die Vorhersage des aktuellen Frames für die Photonen Zeit zu erhalten. 
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

## <a name="see-also"></a>Weitere Informationen
* [Verwenden des Windows-Namespace mit Unity-Apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">Spatialcoordinatesystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Holographicframe</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendern in DirectX](rendering-in-directx.md)
