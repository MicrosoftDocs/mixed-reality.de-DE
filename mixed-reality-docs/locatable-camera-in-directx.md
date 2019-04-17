---
title: Gebietsschemabezogene Kamera in DirectX
description: Erläutert, wie die Kamera des Punkt-der-Ansicht (COOLIE) in einer app HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, auffindbaren Kamera, der Sicht, COOLIE, Unporoject, Media Foundation, MF, benutzerdefinierte Senke, exemplarische Vorgehensweise mit Beispielcode
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595304"
---
# <a name="locatable-camera-in-directx"></a>Gebietsschemabezogene Kamera in DirectX

In diesem Thema wird beschrieben, wie zum Einrichten einer [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline für den Zugriff auf die [Kamera](locatable-camera.md) in einer DirectX-app, einschließlich der Frame-Metadaten, die Sie suchen Sie die Images kann in der realen Welt erstellt.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media-Erfassung und Media Foundation-Entwicklung: IMFAttributes

Jedes Bild-Frame [enthält einem Koordinatensystem](locatable-camera.md#images-with-coordinate-systems) , sowie zwei wichtige Transformationen. Die "View" wandeln Sie Zuordnungen aus der angegebenen Koordinatensystem bis zur Kamera und der "Projection" wird von der Kamera Pixel im Bild. Das Koordinatensystem und 2 Transformationen werden als Metadaten in jedem Bild-Frame über Media Foundation eingebettet [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Beispiel für die Verwendung der Attribute mit benutzerdefinierten MF-Senke lesen und Ausführen der Projektion

In Ihren benutzerdefinierten MF Senke-Datenstrom ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), erhalten Sie [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) mit Beispiel-Attributen:

Die folgenden MediaExtensions müssen für WinRT-basierten Code definiert werden:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

Sie können nicht auf diese Attribute von WinRT-APIs zugreifen, aber erfordert die Implementierung Medienerweiterung [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (für Auswirkung) oder [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) und [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) () für die benutzerdefinierte Senke). Wenn Sie das Beispiel in dieser Erweiterung entweder verarbeiten in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) oder [IMFStreamSink::ProcessSample() ](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), Sie können Attribute wie in diesem Beispiel Abfragen.

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

Um die Textur mit der Kamera zuzugreifen, benötigen Sie die gleichen D3D-Gerät, das Kamera-Frame-Textur erstellt. Diese D3D-Gerät befindet sich im [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in der Pipeline erfassen. Um die DXGI-Geräte-Manager aus Medienaufzeichnung zu erhalten, Sie können [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) und [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) Schnittstellen.

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

Sie können auch die Maus- und Tastatureingaben als optionale Eingabe Methoden für die Windows Mixed Reality-app aktivieren. Dies kann auch sein, eine großartige Debugfunktion für Geräte wie HoloLens und möglicherweise wünschenswert, dass Benutzereingaben in mixed Reality-apps, die, die im immersive Headsets an PCs angeschlossen.
