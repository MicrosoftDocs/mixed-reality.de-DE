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
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="6aa07-104">Einsetzbare Kamera in DirectX</span><span class="sxs-lookup"><span data-stu-id="6aa07-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="6aa07-105">In diesem Thema wird beschrieben, wie Sie eine [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) Pipeline für den Zugriff auf die [Kamera](locatable-camera.md) in einer DirectX-App einrichten, einschließlich der Frame-Metadaten, mit denen Sie die in der realen Welt erzeugten Bilder suchen können.</span><span class="sxs-lookup"><span data-stu-id="6aa07-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="6aa07-106">Windows Media Capture und Media Foundation Entwicklung: Imfattributes</span><span class="sxs-lookup"><span data-stu-id="6aa07-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="6aa07-107">Jeder Bild Rahmen [enthält ein Koordinatensystem](locatable-camera.md#images-with-coordinate-systems) sowie zwei wichtige Transformationen.</span><span class="sxs-lookup"><span data-stu-id="6aa07-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="6aa07-108">Die Transformation "Ansicht" wird vom bereitgestellten Koordinatensystem zur Kamera zugeordnet, und die Projektion "Projektion" wird von der Kamera zu Pixel im Bild zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="6aa07-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="6aa07-109">Das Koordinatensystem und die 2 Transformationen werden als Metadaten in jedem Bild Rahmen über Media Foundation [imfattributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)eingebettet.</span><span class="sxs-lookup"><span data-stu-id="6aa07-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="6aa07-110">Beispiel Verwendung für das Lesen von Attributen mit benutzerdefinierter MF-Senke und-Projektion</span><span class="sxs-lookup"><span data-stu-id="6aa07-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="6aa07-111">In Ihrem benutzerdefinierten MF-senkenstream ([IMF streamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) erhalten Sie [IMF Sample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) mit Beispiel Attributen:</span><span class="sxs-lookup"><span data-stu-id="6aa07-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="6aa07-112">Die folgenden mediaextensions müssen für WinRT-basierten Code definiert werden:</span><span class="sxs-lookup"><span data-stu-id="6aa07-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="6aa07-113">Sie können nicht von WinRT-APIs aus auf diese Attribute zugreifen, erfordern jedoch die Implementierung der medienerweiterung von [imftransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (für Effekt) oder [imfmediasink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) und [imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (für benutzerdefinierte Senke).</span><span class="sxs-lookup"><span data-stu-id="6aa07-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="6aa07-114">Wenn Sie das Beispiel in dieser Erweiterung entweder in [IMF Transform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMF Transform::P rocess Output ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) oder [IMF streamsink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)verarbeiten, können Sie Attribute wie dieses Beispielabfragen.</span><span class="sxs-lookup"><span data-stu-id="6aa07-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

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

<span data-ttu-id="6aa07-115">Um auf die Textur von der Kamera zuzugreifen, benötigen Sie dasselbe D3D-Gerät, das eine Kamera Rahmen Textur erstellt.</span><span class="sxs-lookup"><span data-stu-id="6aa07-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="6aa07-116">Dieses D3D-Gerät befindet sich in der Aufzeichnungs Pipeline in [IMF dxgidebug Manager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) .</span><span class="sxs-lookup"><span data-stu-id="6aa07-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="6aa07-117">Um den DXGI-Geräte-Manager von der Medien Erfassung zu erhalten, können Sie [iadvancedmediacapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) -und [iadvancedmediacapturesettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) -Schnittstellen verwenden.</span><span class="sxs-lookup"><span data-stu-id="6aa07-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

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

<span data-ttu-id="6aa07-118">Sie können die Maus-und Tastatureingabe auch als optionale Eingabemethoden für Ihre Windows Mixed Reality-App aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6aa07-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="6aa07-119">Dies kann auch eine hervorragend Debuggingfunktion für Geräte wie hololens sein und ist möglicherweise für Benutzereingaben in Mixed Reality-apps wünschenswert, die in immersiven, mit PCs verbundenen Headsets ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6aa07-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
