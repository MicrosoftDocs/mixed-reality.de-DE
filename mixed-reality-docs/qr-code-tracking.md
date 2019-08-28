---
title: QR-Code Nachverfolgung
description: Erfahren Sie, wie Sie QR-Codes auf hololens 2 erkennen.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, Location based Entertainment, VR-Arkade, Arcade, immersive, QR, QR-Code, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047160"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="e4926-104">QR-Code Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="e4926-104">QR code tracking</span></span>

<span data-ttu-id="e4926-105">Hololens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der realen Position jedes Codes einrichten.</span><span class="sxs-lookup"><span data-stu-id="e4926-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="e4926-106">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="e4926-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e4926-107">Feature</span><span class="sxs-lookup"><span data-stu-id="e4926-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e4926-108"><a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></span><span class="sxs-lookup"><span data-stu-id="e4926-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e4926-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e4926-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="e4926-110"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="e4926-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e4926-111">QR-Code Erkennung</span><span class="sxs-lookup"><span data-stu-id="e4926-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="e4926-112">️</span><span class="sxs-lookup"><span data-stu-id="e4926-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e4926-113">✔️</span><span class="sxs-lookup"><span data-stu-id="e4926-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="e4926-114">Siehe Hinweis</span><span class="sxs-lookup"><span data-stu-id="e4926-114">See note</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="e4926-115">Die Unterstützung von immersiven Windows Mixed Reality-Headsets auf Desktop-PCs wird derzeit nicht mit dem unten aufgeführten nuget-Paket unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4926-115">Support for immersive Windows Mixed Reality headsets on desktop PCs is not currently supported with the NuGet package below.</span></span>  <span data-ttu-id="e4926-116">Bleiben Sie auf dem neuesten Stand der Desktop Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="e4926-116">Stay tuned for further updates on desktop support.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="e4926-117">Erhalten des QR-Pakets</span><span class="sxs-lookup"><span data-stu-id="e4926-117">Getting the QR package</span></span>
<span data-ttu-id="e4926-118">[Hier](https://github.com/dorreneb/mixed-reality/releases)können Sie ein nuget-Paket für die QR-Code Erkennung herunterladen.</span><span class="sxs-lookup"><span data-stu-id="e4926-118">You can download a NuGet package for QR code detection [here](https://github.com/dorreneb/mixed-reality/releases).</span></span>

<span data-ttu-id="e4926-119">Zukünftige Versionen dieses Pakets sind über das öffentliche nuget-Paketrepository verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e4926-119">Future versions of this package will be available through the public NuGet package repository.</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="e4926-120">Erkennen von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="e4926-120">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="e4926-121">Hinzufügen der Webcam-Funktion</span><span class="sxs-lookup"><span data-stu-id="e4926-121">Adding the webcam capability</span></span>
<span data-ttu-id="e4926-122">Sie müssen die Funktion `webcam` ihrem Manifest hinzufügen, um QR-Codes zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="e4926-122">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="e4926-123">Diese Funktion ist erforderlich, da die Daten in erkannten Codes in der Benutzerumgebung möglicherweise vertrauliche Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4926-123">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="e4926-124">Die Berechtigung kann durch Aufrufen `QRCodeWatcher.RequestAccessAsync()`von angefordert werden:</span><span class="sxs-lookup"><span data-stu-id="e4926-124">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="e4926-125">_C#:_</span><span class="sxs-lookup"><span data-stu-id="e4926-125">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="e4926-126">_C++:_</span><span class="sxs-lookup"><span data-stu-id="e4926-126">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="e4926-127">Vor dem Erstellen eines qrcodewatcher-Objekts muss eine Berechtigung angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="e4926-127">Permission should be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="e4926-128">Obwohl die Erkennung von QR- `webcam` Code die Funktion erfordert, erfolgt die Erkennung mithilfe der Überwachungskameras des Geräts.</span><span class="sxs-lookup"><span data-stu-id="e4926-128">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="e4926-129">Dies bietet einen umfassenderen Erkennungs FOV und eine bessere Akku Lebensdauer im Vergleich zur Erkennung mit der Photo/Video (PV)-Kamera des Geräts.</span><span class="sxs-lookup"><span data-stu-id="e4926-129">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="e4926-130">Erkennen von QR-Codes in Unity</span><span class="sxs-lookup"><span data-stu-id="e4926-130">Detecting QR codes in Unity</span></span>

<span data-ttu-id="e4926-131">Sie können die QR-Code Erkennungs-API in Unity verwenden, ohne eine Abhängigkeit von mrtk zu treffen.</span><span class="sxs-lookup"><span data-stu-id="e4926-131">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="e4926-132">Zu diesem Zweck müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="e4926-132">To do so, you must:</span></span>

1. <span data-ttu-id="e4926-133">Erstellen Sie einen neuen Ordner im Ordner "Assets" Ihres Unity-Projekts mitden Namen-Plug-ins.</span><span class="sxs-lookup"><span data-stu-id="e4926-133">Create a new folder in the assets folder of your unity project with the name *Plugins*.</span></span>
2. <span data-ttu-id="e4926-134">Kopieren Sie alle erforderlichen Dateien aus diesem Ordner in den lokalen Ordner "Plug-ins", den Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e4926-134">Copy all the required files from this folder into the local "Plugins" folder you just created.</span></span>

<span data-ttu-id="e4926-135">Es gibt eine Beispiel-Unity-APP, die ein Holographic-Quadrat über QR-Codes anzeigt, zusammen mit den zugehörigen Daten wie GUID, physischer Größe, timestamp und decodierten Daten.</span><span class="sxs-lookup"><span data-stu-id="e4926-135">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="e4926-136">Diese APP befindet sich unter https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span><span class="sxs-lookup"><span data-stu-id="e4926-136">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="e4926-137">Erkennen von QR-Codes inC++</span><span class="sxs-lookup"><span data-stu-id="e4926-137">Detecting QR codes in C++</span></span>

>[!NOTE]
><span data-ttu-id="e4926-138">Die C++ Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C + +17-kompatibler C++/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e4926-138">The C++ code snippets in this article currently demonstrate the use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="e4926-139">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="e4926-139">The concepts are equivalent for a C++/WinRT project, though you need to translate the code.</span></span>

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="e4926-140">Erhalten des Koordinatensystems für einen QR-Code</span><span class="sxs-lookup"><span data-stu-id="e4926-140">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="e4926-141">Jeder erkannte QR-Code macht ein [räumliches Koordinatensystem](coordinate-systems.md) verfügbar, das mit dem QR-Code in der oberen linken Ecke des oberen linken Rands des schnell Erkennungs Quadrats ausgerichtet ist, wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4926-141">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="e4926-142">Wenn Sie das QR SDK direkt verwenden, zeigt die z-Achse auf das Papier (nicht angezeigt): bei der Konvertierung in Unity-Koordinaten verweist die z-Achse auf das Papier und wird von Links entfernt.</span><span class="sxs-lookup"><span data-stu-id="e4926-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="e4926-143">Das spatialcoordinatesystem eines QR-Codes wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4926-143">A QR code's SpatialCoordinateSystem aligns shown.</span></span> <span data-ttu-id="e4926-144">Dieses Koordinatensystem kann von der Plattform abgerufen werden, indem Sie <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">spatialgraphinteroppreview:: createcoordinatesystemfornode</a> aufrufen und die spatialgraphnodeid des Codes übergeben.</span><span class="sxs-lookup"><span data-stu-id="e4926-144">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![QR-Code Koordinatensystem](images/Qr-coordinatesystem.png) 

<span data-ttu-id="e4926-146">Für ein QRCode-Objekt zeigt der C++folgende/CX-Code, wie ein Rechteck erstellt und mithilfe des Koordinatensystems des QR-Codes platziert wird:</span><span class="sxs-lookup"><span data-stu-id="e4926-146">For a QRCode object, the following C++/CX code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="e4926-147">Sie können die physische Größe zum Erstellen des QR-Rechtecks verwenden:</span><span class="sxs-lookup"><span data-stu-id="e4926-147">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="e4926-148">Das Koordinatensystem kann zum Zeichnen des QR-Codes oder zum Anfügen von holograms an den Speicherort verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="e4926-148">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

<span data-ttu-id="e4926-149">Der *qrcodewatcher:: qrcodeaddedhandler* könnte etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="e4926-149">Altogether, your *QRCodeWatcher::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="e4926-150">Bewährte Methoden für die Erkennung von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="e4926-150">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="e4926-151">Stille Zonen um QR-Codes</span><span class="sxs-lookup"><span data-stu-id="e4926-151">Quiet zones around QR Codes</span></span>

<span data-ttu-id="e4926-152">Um ordnungsgemäß gelesen zu werden, erfordern QR-Codes einen Rand um alle Seiten des Codes.</span><span class="sxs-lookup"><span data-stu-id="e4926-152">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="e4926-153">Dieser Rand darf keine gedruckten Inhalte enthalten und sollte vier Module (ein einzelnes schwarzes Quadrat im Code) enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4926-153">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="e4926-154">Die [QR-Spezifikation](https://www.qrcode.com/en/howto/code.html) enthält weitere Informationen zu stillen Zonen.</span><span class="sxs-lookup"><span data-stu-id="e4926-154">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="e4926-155">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="e4926-155">Lighting and backdrop</span></span>
<span data-ttu-id="e4926-156">Die Qualität der QR-Code Erkennung ist anfällig für die unterschiedliche Beleuchtung und den Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="e4926-156">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="e4926-157">Drucken Sie in einer Szene mit besonders heller Beleuchtung einen Code, der in einem grauen Hintergrund schwarz ist.</span><span class="sxs-lookup"><span data-stu-id="e4926-157">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="e4926-158">Andernfalls drucken Sie einen schwarzen QR-Code in einem weißen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="e4926-158">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="e4926-159">Wenn der Hintergrund des Codes besonders dunkel ist, versuchen Sie es mit einem grauen Code, wenn die Erkennungsrate niedrig ist.</span><span class="sxs-lookup"><span data-stu-id="e4926-159">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="e4926-160">Wenn die Kulisse relativ hell ist, sollte ein regulärer Code einwandfrei funktionieren.</span><span class="sxs-lookup"><span data-stu-id="e4926-160">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="e4926-161">Größe der QR-Codes</span><span class="sxs-lookup"><span data-stu-id="e4926-161">Size of QR codes</span></span>
<span data-ttu-id="e4926-162">Windows Mixed Reality-Geräte funktionieren nicht mit QR-Codes mit Seiten, die kleiner als 5 cm sind.</span><span class="sxs-lookup"><span data-stu-id="e4926-162">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="e4926-163">Bei QR-Codes zwischen 5 und 10 cm-Längen Seiten müssen Sie den Code relativ nah sehen.</span><span class="sxs-lookup"><span data-stu-id="e4926-163">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="e4926-164">Außerdem dauert es länger, bis Codes mit dieser Größe erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="e4926-164">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="e4926-165">Die genaue Zeit zum Erkennen von Codes hängt nicht nur von der Größe der QR-Codes ab, sondern von der Entfernung des Codes.</span><span class="sxs-lookup"><span data-stu-id="e4926-165">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="e4926-166">Wenn Sie sich näher an den Code bewegen, können Probleme mit der Größe abgeglichen werden.</span><span class="sxs-lookup"><span data-stu-id="e4926-166">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="e4926-167">Entfernung und Winkelposition aus dem QR-Code</span><span class="sxs-lookup"><span data-stu-id="e4926-167">Distance and angular position from the QR code</span></span>
<span data-ttu-id="e4926-168">Die Überwachungskameras können nur eine bestimmte Detailebene erkennen.</span><span class="sxs-lookup"><span data-stu-id="e4926-168">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="e4926-169">Bei wirklich kleinen Codes-< 10cm auf den Seiten müssen Sie ziemlich nah sein.</span><span class="sxs-lookup"><span data-stu-id="e4926-169">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="e4926-170">Bei einem QR-Code der Version 1, der zwischen 10 und 25 cm breit ist, reicht der minimale Erkennungsabstand zwischen 0,15 und 0,5 Meter.</span><span class="sxs-lookup"><span data-stu-id="e4926-170">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="e4926-171">Der Erkennungsabstand für die Größe erhöht sich linear.</span><span class="sxs-lookup"><span data-stu-id="e4926-171">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="e4926-172">Die QR-Erkennung funktioniert mit einem Bereich von Winkeln + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="e4926-172">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="e4926-173">Dadurch wird sichergestellt, dass die richtige Lösung für die Erkennung des Codes vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e4926-173">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="e4926-174">QR-Codes mit Logos</span><span class="sxs-lookup"><span data-stu-id="e4926-174">QR codes with logos</span></span>
<span data-ttu-id="e4926-175">QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4926-175">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="e4926-176">Verwalten von QR-Codedaten</span><span class="sxs-lookup"><span data-stu-id="e4926-176">Managing QR code data</span></span>
<span data-ttu-id="e4926-177">Windows Mixed Reality-Geräte erkennen QR-Codes auf der Systemebene des Treibers.</span><span class="sxs-lookup"><span data-stu-id="e4926-177">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="e4926-178">Wenn das Gerät neu gestartet wird, sind die erkannten QR-Codes verschwunden und werden als neue Objekte das nächste Mal wiedererkannt.</span><span class="sxs-lookup"><span data-stu-id="e4926-178">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="e4926-179">Es wird empfohlen, die APP so zu konfigurieren, dass Sie QR-Codes ignoriert, die älter sind als ein bestimmter Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="e4926-179">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="e4926-180">Derzeit unterstützt die API das Löschen von QR-Code Verläufen nicht.</span><span class="sxs-lookup"><span data-stu-id="e4926-180">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="e4926-181">QR-Code Platzierung in einem Leerzeichen</span><span class="sxs-lookup"><span data-stu-id="e4926-181">QR code placement in a space</span></span>
<span data-ttu-id="e4926-182">Empfehlungen dazu, wo und wie QR-Codes platziert werden, finden Sie unter [Überlegungen zur Umgebung für hololens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="e4926-182">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="e4926-183">QR-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="e4926-183">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e4926-184">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e4926-184">See also</span></span>
* [<span data-ttu-id="e4926-185">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="e4926-185">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="e4926-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="e4926-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>