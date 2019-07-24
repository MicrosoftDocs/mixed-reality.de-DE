---
title: Einsetzbare Kamera in DirectX
description: Erläutert die Verwendung der Point-of-View-Kamera (POV) in einer hololens-app.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, einsetzbare Kamera, Point of View, POV, unporoject, Media Foundation, MF, Custom Sink, Exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516865"
---
# <a name="locatable-camera-in-directx"></a>Einsetzbare Kamera in DirectX

In diesem Thema wird beschrieben, wie Sie eine [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) Pipeline für den Zugriff auf die [Kamera](locatable-camera.md) in einer DirectX-App einrichten, einschließlich der Frame-Metadaten, mit denen Sie die in der realen Welt erzeugten Bilder suchen können.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media Capture und Media Foundation Entwicklung: Imfattributes

Jeder Bild Rahmen [enthält ein Koordinatensystem](locatable-camera.md#images-with-coordinate-systems) sowie zwei wichtige Transformationen. Die Transformation "Ansicht" wird vom bereitgestellten Koordinatensystem zur Kamera zugeordnet, und die Projektion "Projektion" wird von der Kamera zu Pixel im Bild zugeordnet. Das Koordinatensystem und die 2 Transformationen werden als Metadaten in jedem Bild Rahmen über Media Foundation [imfattributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)eingebettet.

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Beispiel Verwendung für das Lesen von Attributen mit benutzerdefinierter MF-Senke und-Projektion

In Ihrem benutzerdefinierten MF-senkenstream ([IMF streamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) erhalten Sie [IMF Sample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) mit Beispiel Attributen:

Die folgenden mediaextensions müssen für WinRT-basierten Code definiert werden:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

Sie können nicht von WinRT-APIs aus auf diese Attribute zugreifen, erfordern jedoch die Implementierung der medienerweiterung von [imftransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (für Effekt) oder [imfmediasink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) und [imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (für benutzerdefinierte Senke). Wenn Sie das Beispiel in dieser Erweiterung entweder in [IMF Transform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMF Transform::P rocess Output ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) oder [IMF streamsink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)verarbeiten, können Sie Attribute wie dieses Beispielabfragen.

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

Um auf die Textur von der Kamera zuzugreifen, benötigen Sie dasselbe D3D-Gerät, das eine Kamera Rahmen Textur erstellt. Dieses D3D-Gerät befindet sich in der Aufzeichnungs Pipeline in [IMF dxgidebug Manager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) . Um den DXGI-Geräte-Manager von der Medien Erfassung zu erhalten, können Sie [iadvancedmediacapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) -und [iadvancedmediacapturesettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) -Schnittstellen verwenden.

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

Sie können die Maus-und Tastatureingabe auch als optionale Eingabemethoden für Ihre Windows Mixed Reality-App aktivieren. Dies kann auch eine hervorragend Debuggingfunktion für Geräte wie hololens sein und ist möglicherweise für Benutzereingaben in Mixed Reality-apps wünschenswert, die in immersiven, mit PCs verbundenen Headsets ausgeführt werden.
