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
# <a name="mixed-reality-native-objects-in-unity"></a>Gemischte Realität, systemeigene Objekte in Unity

[Abrufen einer HolographicSpace](getting-a-holographicspace.md) ist, was jede Mixed Reality-app ist, bevor es gestartet wird, Empfangen von Kameradaten und das rendering von frames. In Unity das Modul übernimmt diese Schritte für Sie Holographic Objekte behandeln und intern als Teil seiner renderloop aktualisiert.

Allerdings in erweiterten Szenarien müssen Sie möglicherweise für den Zugriff auf die zugrunde liegende systemeigene Objekte, z. B. die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> und den aktuellen <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> ist, was den Zugriff auf diese systemeigene Objekte bietet.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Die *XRDevice* Typ ermöglicht Ihnen das Zugreifen auf zugrunde liegende systemeigene Objekte, die mit der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> Methode. Was GetNativePtr zurückgibt variiert zwischen verschiedenen Plattformen. XRDevice.GetNativePtr gibt einen Zeiger (IntPtr) für die universelle Windows-Plattform, bei Windows Mixed Reality XR SDK als Ziel die folgende Struktur zurück: 

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
Sie können in HolographicFrameNativeData mit Marshal.PtrToStructure-Methode konvertieren:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** ist ein Array von IntPtr als UnmanagedType.ByValArray gemarshallt werden, mit einer Länge gleich MaxNumberOfCameras* 


### <a name="using-holographicframenativedata"></a>Verwenden von HolographicFrameNativeData

> [!NOTE]
> Ändern des Status der nativen Objekte über HolographicFrameNativeData empfangen kann zu unvorhersehbaren Verhalten und Rendern von Artefakten, verursachen, besonders wenn Unity auch Informationen zu diesen gleichen Zustand Gründe.  Z. B. HolographicFrame.UpdateCurrentPrediction sollte nicht aufgerufen werden, da ansonsten die Haltung Vorhersage, die Unity mit diesen Frame gerendert wird, werden nicht mehr synchron mit der Haltung, die Windows erwartet wird, zu reduzieren, [– Hologramm Stabilität](hologram-stability.md).

Sie können Daten aus HolographicFrameNativeData verwenden, wenn der Zugriff auf systemeigene Schnittstellen für das Rendern oder das Debuggen verwendet werden, in Ihre native-Plug-Ins erforderlich ist oder C# Code. 

Hier ist ein Beispiel, wie Sie HolographicFrameNativeData verwenden können, um den aktuellen Frame Vorhersage Photon Zeit zu erhalten. 
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
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendern in DirectX](rendering-in-directx.md)
