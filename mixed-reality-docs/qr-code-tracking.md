---
title: QR-Code Nachverfolgung
description: Erfahren Sie, wie Sie QR-Codes auf hololens 2 erkennen.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, Location based Entertainment, VR-Arkade, Arcade, immersive, QR, QR-Code, hololens2
ms.openlocfilehash: e14fe14fd76bceaf506dd7b85a57825c3f18d223
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438120"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="39e62-104">QR-Code Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="39e62-104">QR code tracking</span></span>

<span data-ttu-id="39e62-105">Hololens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der realen Position jedes Codes einrichten.</span><span class="sxs-lookup"><span data-stu-id="39e62-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="39e62-106">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="39e62-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="39e62-107">Feature</span><span class="sxs-lookup"><span data-stu-id="39e62-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="39e62-108"><a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></span><span class="sxs-lookup"><span data-stu-id="39e62-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="39e62-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="39e62-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="39e62-110"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="39e62-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="39e62-111">QR-Code Erkennung</span><span class="sxs-lookup"><span data-stu-id="39e62-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="39e62-112">️</span><span class="sxs-lookup"><span data-stu-id="39e62-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="39e62-113">✔️</span><span class="sxs-lookup"><span data-stu-id="39e62-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="39e62-114">Siehe Hinweis</span><span class="sxs-lookup"><span data-stu-id="39e62-114">See note</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="39e62-115">Die Unterstützung von immersiven Windows Mixed Reality-Headsets auf Desktop-PCs wird derzeit nicht mit dem unten aufgeführten nuget-Paket unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39e62-115">Support for immersive Windows Mixed Reality headsets on desktop PCs is not currently supported with the NuGet package below.</span></span>  <span data-ttu-id="39e62-116">Bleiben Sie auf dem neuesten Stand der Desktop Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="39e62-116">Stay tuned for further updates on desktop support.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="39e62-117">Erhalten des QR-Pakets</span><span class="sxs-lookup"><span data-stu-id="39e62-117">Getting the QR package</span></span>
<span data-ttu-id="39e62-118">Sie können das nuget-Paket für die QR-Code Erkennung [hier](https://nuget.org/Packages/Microsoft.MixedReality.QR)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="39e62-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="39e62-119">Erkennen von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="39e62-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="39e62-120">Hinzufügen der Webcam-Funktion</span><span class="sxs-lookup"><span data-stu-id="39e62-120">Adding the webcam capability</span></span>
<span data-ttu-id="39e62-121">Sie müssen den Funktions `webcam` dem Manifest hinzufügen, um QR-Codes zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="39e62-121">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="39e62-122">Diese Funktion ist erforderlich, da die Daten in erkannten Codes in der Benutzerumgebung möglicherweise vertrauliche Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="39e62-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="39e62-123">Die Berechtigung kann durch Aufrufen von `QRCodeWatcher.RequestAccessAsync()`angefordert werden:</span><span class="sxs-lookup"><span data-stu-id="39e62-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="39e62-124">_C#:_</span><span class="sxs-lookup"><span data-stu-id="39e62-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="39e62-125">_C++:_</span><span class="sxs-lookup"><span data-stu-id="39e62-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="39e62-126">Vor dem Erstellen eines qrcodewatcher-Objekts muss eine Berechtigung angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="39e62-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="39e62-127">Obwohl die Erkennung von QR-Code die `webcam` Funktion erfordert, erfolgt die Erkennung mithilfe der Überwachungskameras des Geräts.</span><span class="sxs-lookup"><span data-stu-id="39e62-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="39e62-128">Dies bietet einen umfassenderen Erkennungs FOV und eine bessere Akku Lebensdauer im Vergleich zur Erkennung mit der Photo/Video (PV)-Kamera des Geräts.</span><span class="sxs-lookup"><span data-stu-id="39e62-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="39e62-129">Erkennen von QR-Codes in Unity</span><span class="sxs-lookup"><span data-stu-id="39e62-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="39e62-130">Sie können die QR-Code Erkennungs-API in Unity verwenden, ohne eine Abhängigkeit von mrtk zu treffen.</span><span class="sxs-lookup"><span data-stu-id="39e62-130">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="39e62-131">Hierzu müssen Sie das nuget-Paket mithilfe [von nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity)installieren.</span><span class="sxs-lookup"><span data-stu-id="39e62-131">To do so, you must install the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>

<span data-ttu-id="39e62-132">Es gibt eine Beispiel-Unity-APP, die ein Holographic-Quadrat über QR-Codes anzeigt, zusammen mit den zugehörigen Daten wie GUID, physischer Größe, timestamp und decodierten Daten.</span><span class="sxs-lookup"><span data-stu-id="39e62-132">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="39e62-133">Diese APP kann sich unter https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes befinden.</span><span class="sxs-lookup"><span data-stu-id="39e62-133">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="39e62-134">Erkennen von QR-Codes inC++</span><span class="sxs-lookup"><span data-stu-id="39e62-134">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="39e62-135">Erhalten des Koordinatensystems für einen QR-Code</span><span class="sxs-lookup"><span data-stu-id="39e62-135">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="39e62-136">Jeder erkannte QR-Code macht ein [räumliches Koordinatensystem](coordinate-systems.md) verfügbar, das mit dem QR-Code in der oberen linken Ecke des oberen linken Rands des schnell Erkennungs Quadrats ausgerichtet ist, wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="39e62-136">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="39e62-137">Wenn Sie das QR SDK direkt verwenden, zeigt die z-Achse auf das Papier (nicht angezeigt): bei der Konvertierung in Unity-Koordinaten verweist die z-Achse auf das Papier und wird von Links entfernt.</span><span class="sxs-lookup"><span data-stu-id="39e62-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="39e62-138">Das spatialcoordinatesystem eines QR-Codes richtet sich wie gezeigt aus.</span><span class="sxs-lookup"><span data-stu-id="39e62-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="39e62-139">Dieses Koordinatensystem kann von der Plattform abgerufen werden, indem Sie <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">spatialgraphinteroppreview:: createcoordinatesystemfornode</a> aufrufen und die spatialgraphnodeid des Codes übergeben.</span><span class="sxs-lookup"><span data-stu-id="39e62-139">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![QR-Code Koordinatensystem](images/Qr-coordinatesystem.png) 

<span data-ttu-id="39e62-141">Für ein QRCode-Objekt zeigt der C++ folgende Code, wie ein Rechteck erstellt und mit dem Koordinatensystem des QR-Codes platziert wird:</span><span class="sxs-lookup"><span data-stu-id="39e62-141">For a QRCode object, the following C++ code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="39e62-142">Sie können die physische Größe zum Erstellen des QR-Rechtecks verwenden:</span><span class="sxs-lookup"><span data-stu-id="39e62-142">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="39e62-143">Das Koordinatensystem kann zum Zeichnen des QR-Codes oder zum Anfügen von holograms an den Speicherort verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="39e62-143">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="39e62-144">Ihr *qrcodeaddedhandler* könnte etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="39e62-144">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="39e62-145">Bewährte Methoden für die Erkennung von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="39e62-145">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="39e62-146">Stille Zonen um QR-Codes</span><span class="sxs-lookup"><span data-stu-id="39e62-146">Quiet zones around QR Codes</span></span>

<span data-ttu-id="39e62-147">Um ordnungsgemäß gelesen zu werden, erfordern QR-Codes einen Rand um alle Seiten des Codes.</span><span class="sxs-lookup"><span data-stu-id="39e62-147">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="39e62-148">Dieser Rand darf keine gedruckten Inhalte enthalten und sollte vier Module (ein einzelnes schwarzes Quadrat im Code) enthalten.</span><span class="sxs-lookup"><span data-stu-id="39e62-148">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="39e62-149">Die [QR-Spezifikation](https://www.qrcode.com/en/howto/code.html) enthält weitere Informationen zu stillen Zonen.</span><span class="sxs-lookup"><span data-stu-id="39e62-149">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="39e62-150">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="39e62-150">Lighting and backdrop</span></span>
<span data-ttu-id="39e62-151">Die Qualität der QR-Code Erkennung ist anfällig für die unterschiedliche Beleuchtung und den Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="39e62-151">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="39e62-152">Drucken Sie in einer Szene mit besonders heller Beleuchtung einen Code, der in einem grauen Hintergrund schwarz ist.</span><span class="sxs-lookup"><span data-stu-id="39e62-152">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="39e62-153">Andernfalls drucken Sie einen schwarzen QR-Code in einem weißen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="39e62-153">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="39e62-154">Wenn der Hintergrund des Codes besonders dunkel ist, versuchen Sie es mit einem grauen Code, wenn die Erkennungsrate niedrig ist.</span><span class="sxs-lookup"><span data-stu-id="39e62-154">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="39e62-155">Wenn die Kulisse relativ hell ist, sollte ein regulärer Code einwandfrei funktionieren.</span><span class="sxs-lookup"><span data-stu-id="39e62-155">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="39e62-156">Größe der QR-Codes</span><span class="sxs-lookup"><span data-stu-id="39e62-156">Size of QR codes</span></span>
<span data-ttu-id="39e62-157">Windows Mixed Reality-Geräte funktionieren nicht mit QR-Codes mit Seiten, die kleiner als 5 cm sind.</span><span class="sxs-lookup"><span data-stu-id="39e62-157">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="39e62-158">Bei QR-Codes zwischen 5 und 10 cm-Längen Seiten müssen Sie den Code relativ nah sehen.</span><span class="sxs-lookup"><span data-stu-id="39e62-158">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="39e62-159">Außerdem dauert es länger, bis Codes mit dieser Größe erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="39e62-159">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="39e62-160">Die genaue Zeit zum Erkennen von Codes hängt nicht nur von der Größe der QR-Codes ab, sondern von der Entfernung des Codes.</span><span class="sxs-lookup"><span data-stu-id="39e62-160">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="39e62-161">Wenn Sie sich näher an den Code bewegen, können Probleme mit der Größe abgeglichen werden.</span><span class="sxs-lookup"><span data-stu-id="39e62-161">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="39e62-162">Entfernung und Winkelposition aus dem QR-Code</span><span class="sxs-lookup"><span data-stu-id="39e62-162">Distance and angular position from the QR code</span></span>
<span data-ttu-id="39e62-163">Die Überwachungskameras können nur eine bestimmte Detailebene erkennen.</span><span class="sxs-lookup"><span data-stu-id="39e62-163">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="39e62-164">Bei wirklich kleinen Codes-< 10cm auf den Seiten müssen Sie ziemlich nah sein.</span><span class="sxs-lookup"><span data-stu-id="39e62-164">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="39e62-165">Bei einem QR-Code der Version 1, der zwischen 10 und 25 cm breit ist, reicht der minimale Erkennungsabstand zwischen 0,15 und 0,5 Meter.</span><span class="sxs-lookup"><span data-stu-id="39e62-165">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="39e62-166">Der Erkennungsabstand für die Größe erhöht sich linear.</span><span class="sxs-lookup"><span data-stu-id="39e62-166">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="39e62-167">Die QR-Erkennung funktioniert mit einem Bereich von Winkeln + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="39e62-167">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="39e62-168">Dadurch wird sichergestellt, dass die richtige Lösung für die Erkennung des Codes vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="39e62-168">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="39e62-169">QR-Codes mit Logos</span><span class="sxs-lookup"><span data-stu-id="39e62-169">QR codes with logos</span></span>
<span data-ttu-id="39e62-170">QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39e62-170">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="39e62-171">Verwalten von QR-Codedaten</span><span class="sxs-lookup"><span data-stu-id="39e62-171">Managing QR code data</span></span>
<span data-ttu-id="39e62-172">Windows Mixed Reality-Geräte erkennen QR-Codes auf der Systemebene des Treibers.</span><span class="sxs-lookup"><span data-stu-id="39e62-172">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="39e62-173">Wenn das Gerät neu gestartet wird, sind die erkannten QR-Codes verschwunden und werden als neue Objekte das nächste Mal wiedererkannt.</span><span class="sxs-lookup"><span data-stu-id="39e62-173">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="39e62-174">Es wird empfohlen, die APP so zu konfigurieren, dass Sie QR-Codes ignoriert, die älter sind als ein bestimmter Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="39e62-174">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="39e62-175">Derzeit unterstützt die API das Löschen von QR-Code Verläufen nicht.</span><span class="sxs-lookup"><span data-stu-id="39e62-175">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="39e62-176">QR-Code Platzierung in einem Leerzeichen</span><span class="sxs-lookup"><span data-stu-id="39e62-176">QR code placement in a space</span></span>
<span data-ttu-id="39e62-177">Empfehlungen dazu, wo und wie QR-Codes platziert werden, finden Sie unter [Überlegungen zur Umgebung für hololens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="39e62-177">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="39e62-178">QR-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="39e62-178">QR API reference</span></span>

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
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

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
    public enum QRVersion
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

## <a name="see-also"></a><span data-ttu-id="39e62-179">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="39e62-179">See also</span></span>
* [<span data-ttu-id="39e62-180">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="39e62-180">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="39e62-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="39e62-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>
