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
# <a name="mixed-reality-native-objects-in-unity"></a>Native Reality-Objekte in Unity

Das [erhalten eines holographicspace](getting-a-holographicspace.md) ist das, was jede gemischte Reality-APP tut, bevor Sie mit dem Empfang von Kameradaten und renderingframes beginnt In Unity übernimmt die Engine diese Schritte für Sie und verarbeitet holografische Objekte und Updates intern als Teil der Renderschleife.

In erweiterten Szenarien müssen Sie jedoch möglicherweise Zugriff auf die zugrunde liegenden systemeigenen Objekte erhalten, wie z. b. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">holographiccamera</a> und Current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. xrdevice</a> ermöglicht den Zugriff auf diese systemeigenen Objekte.

## <a name="xrdevice"></a>Xrdevice 

**Namespace:** *Unityengine. XR*<br>
**Sorte** *Xrdevice*

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


### <a name="using-holographicframenativedata"></a>Verwenden von holographicframenativedata

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

## <a name="see-also"></a>Siehe auch
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">Spatialcoordinatesystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Holographicframe</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendern in DirectX](rendering-in-directx.md)
