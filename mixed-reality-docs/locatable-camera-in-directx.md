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
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="4ab5d-104">Gebietsschemabezogene Kamera in DirectX</span><span class="sxs-lookup"><span data-stu-id="4ab5d-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="4ab5d-105">In diesem Thema wird beschrieben, wie zum Einrichten einer [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline für den Zugriff auf die [Kamera](locatable-camera.md) in einer DirectX-app, einschließlich der Frame-Metadaten, die Sie suchen Sie die Images kann in der realen Welt erstellt.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="4ab5d-106">Windows Media-Erfassung und Media Foundation-Entwicklung: IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="4ab5d-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="4ab5d-107">Jedes Bild-Frame [enthält einem Koordinatensystem](locatable-camera.md#images-with-coordinate-systems) , sowie zwei wichtige Transformationen.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="4ab5d-108">Die "View" wandeln Sie Zuordnungen aus der angegebenen Koordinatensystem bis zur Kamera und der "Projection" wird von der Kamera Pixel im Bild.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="4ab5d-109">Das Koordinatensystem und 2 Transformationen werden als Metadaten in jedem Bild-Frame über Media Foundation eingebettet [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="4ab5d-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="4ab5d-110">Beispiel für die Verwendung der Attribute mit benutzerdefinierten MF-Senke lesen und Ausführen der Projektion</span><span class="sxs-lookup"><span data-stu-id="4ab5d-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="4ab5d-111">In Ihren benutzerdefinierten MF Senke-Datenstrom ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), erhalten Sie [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) mit Beispiel-Attributen:</span><span class="sxs-lookup"><span data-stu-id="4ab5d-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="4ab5d-112">Die folgenden MediaExtensions müssen für WinRT-basierten Code definiert werden:</span><span class="sxs-lookup"><span data-stu-id="4ab5d-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="4ab5d-113">Sie können nicht auf diese Attribute von WinRT-APIs zugreifen, aber erfordert die Implementierung Medienerweiterung [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (für Auswirkung) oder [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) und [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) () für die benutzerdefinierte Senke).</span><span class="sxs-lookup"><span data-stu-id="4ab5d-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="4ab5d-114">Wenn Sie das Beispiel in dieser Erweiterung entweder verarbeiten in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) oder [IMFStreamSink::ProcessSample() ](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), Sie können Attribute wie in diesem Beispiel Abfragen.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

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

<span data-ttu-id="4ab5d-115">Um die Textur mit der Kamera zuzugreifen, benötigen Sie die gleichen D3D-Gerät, das Kamera-Frame-Textur erstellt.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="4ab5d-116">Diese D3D-Gerät befindet sich im [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in der Pipeline erfassen.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="4ab5d-117">Um die DXGI-Geräte-Manager aus Medienaufzeichnung zu erhalten, Sie können [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) und [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

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

<span data-ttu-id="4ab5d-118">Sie können auch die Maus- und Tastatureingaben als optionale Eingabe Methoden für die Windows Mixed Reality-app aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="4ab5d-119">Dies kann auch sein, eine großartige Debugfunktion für Geräte wie HoloLens und möglicherweise wünschenswert, dass Benutzereingaben in mixed Reality-apps, die, die im immersive Headsets an PCs angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="4ab5d-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
