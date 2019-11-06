---
title: Kopf-und Augenblick in DirectX
description: Entwicklerhandbuch zur Verwendung von Head-Blick und Eye-Nachverfolgung in nativen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: Augenblick, Haupt Blick, Head-Tracking, Eye Tracking, DirectX, Input, holograms
ms.openlocfilehash: 48188cc8c886b371847357701b42249f486bceac
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641118"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="54e07-104">Eingaben in den Kopf-und Augenblick in DirectX</span><span class="sxs-lookup"><span data-stu-id="54e07-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="54e07-105">In Windows Mixed Reality werden die Eingaben für Eye und Head-Blick verwendet, um zu bestimmen, was der Benutzer sieht.</span><span class="sxs-lookup"><span data-stu-id="54e07-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="54e07-106">Dies kann verwendet werden, um primäre Eingabe Modelle, wie z. b. [Kopf-und Commit](gaze-and-commit.md), zu steuern und um Kontext für Interaktions Typen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="54e07-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="54e07-107">Es gibt zwei Arten von Blick Vektoren, die über die API bereitgestellt werden: Kopf-und Augenblick.</span><span class="sxs-lookup"><span data-stu-id="54e07-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="54e07-108">Beide werden als dreidimensionale Ray mit einem Ursprung und einer Richtung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="54e07-109">Anwendungen können dann in Ihre Szenen oder in der realen Welt integriert werden und bestimmen, was der Benutzer als Ziel verwendet.</span><span class="sxs-lookup"><span data-stu-id="54e07-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="54e07-110">Der **Kopf** zeilig stellt die Richtung dar, in der die Kopfzeile des Benutzers gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="54e07-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="54e07-111">Stellen Sie sich dies als Position und Vorwärtsrichtung des Geräts selbst vor, wobei die Position den Mittelpunkt zwischen den beiden anzeigen darstellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="54e07-112">Der Haupt Blick ist auf allen Geräten mit gemischter Realität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="54e07-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="54e07-113">Der Augen **Blick** stellt die Richtung dar, in der die Augen des Benutzers suchen.</span><span class="sxs-lookup"><span data-stu-id="54e07-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="54e07-114">Der Ursprung befindet sich zwischen den Augen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="54e07-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="54e07-115">Es ist auf Geräten mit gemischter Realität verfügbar, die ein Augen Verfolgungssystem enthalten.</span><span class="sxs-lookup"><span data-stu-id="54e07-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="54e07-116">Mit der [spatialpointerpose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API ist sowohl der Kopf-als auch der Augenblick-Strahlen zugänglich.</span><span class="sxs-lookup"><span data-stu-id="54e07-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="54e07-117">Sie können einfach [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) aufrufen, um ein neues spatialpointerpose-Objekt am angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md)zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="54e07-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="54e07-118">Diese spatialpointerpose enthält den Ursprung und die Richtung des Haupt Blicks.</span><span class="sxs-lookup"><span data-stu-id="54e07-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="54e07-119">Sie enthält außerdem einen Blick auf den Ursprung und die Richtung des Augenblicks, wenn die Augen Verfolgung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="54e07-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="54e07-120">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="54e07-120">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="54e07-121"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="54e07-121"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="54e07-122"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="54e07-122"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="54e07-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="54e07-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="54e07-124"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="54e07-124"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="54e07-125">Anvisieren mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="54e07-125">Head-gaze</span></span></td>
     <td><span data-ttu-id="54e07-126">✔️</span><span class="sxs-lookup"><span data-stu-id="54e07-126">✔️</span></span></td>
     <td><span data-ttu-id="54e07-127">✔️</span><span class="sxs-lookup"><span data-stu-id="54e07-127">✔️</span></span></td>
     <td><span data-ttu-id="54e07-128">✔️</span><span class="sxs-lookup"><span data-stu-id="54e07-128">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="54e07-129">Augenblick</span><span class="sxs-lookup"><span data-stu-id="54e07-129">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="54e07-130">✔️</span><span class="sxs-lookup"><span data-stu-id="54e07-130">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="54e07-131">Verwenden des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="54e07-131">Using head-gaze</span></span>

<span data-ttu-id="54e07-132">Um auf den Kopf Blick zuzugreifen, rufen Sie zunächst [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) auf, um ein neues spatialpointerpose-Objekt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="54e07-132">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="54e07-133">Sie müssen die folgenden Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="54e07-133">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="54e07-134">Ein [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) , das das gewünschte Koordinatensystem für den Haupt Blick darstellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-134">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="54e07-135">Dies wird von der *CoordinateSystem* -Variablen im folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-135">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="54e07-136">Weitere Informationen finden Sie im Entwicklerhandbuch zu [Koordinatensystemen](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="54e07-136">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="54e07-137">Ein [Zeitstempel](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , der die genaue Uhrzeit der angeforderten Kopfzeile darstellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-137">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="54e07-138">In der Regel verwenden Sie einen Zeitstempel, der der Uhrzeit entspricht, zu der der aktuelle Frame angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="54e07-138">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="54e07-139">Sie können diesen vorhergesagten Anzeigezeit Stempel von einem [holographicframevorhersage](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt erhalten, das über den aktuellen [holographicframe](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="54e07-139">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="54e07-140">Dieses holographicframevorhersage-Objekt wird durch die *Vorhersage* Variable im folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-140">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="54e07-141">Sobald Sie über eine gültige spatialpointerpose verfügen, sind die Kopf-und Vorwärtsrichtung als Eigenschaften zugänglich.</span><span class="sxs-lookup"><span data-stu-id="54e07-141">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="54e07-142">Der folgende Code zeigt, wie Sie darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="54e07-142">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="54e07-143">Verwenden des Augenblicks</span><span class="sxs-lookup"><span data-stu-id="54e07-143">Using eye-gaze</span></span>

<span data-ttu-id="54e07-144">Beachten Sie, dass die Benutzer bei der erstmaligen Verwendung des Geräts über eine [Eye-Tracking-benutzerkalibrierung](calibration.md) verfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="54e07-144">Please note that for your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](calibration.md) the first time they use the device.</span></span> <span data-ttu-id="54e07-145">Die Eye-Eye-API ähnelt der Kopfzeile.</span><span class="sxs-lookup"><span data-stu-id="54e07-145">The eye-gaze API is very similar to head-gaze.</span></span>
<span data-ttu-id="54e07-146">Dabei wird dieselbe [spatialpointerpose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API verwendet, die einen Strahl Ursprung und eine Richtung bereitstellt, die Sie für Ihre Szene bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="54e07-146">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="54e07-147">Der einzige Unterschied besteht darin, dass Sie die Eye-Nachverfolgung vor der Verwendung explizit aktivieren müssen.</span><span class="sxs-lookup"><span data-stu-id="54e07-147">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="54e07-148">Hierfür müssen Sie zwei Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="54e07-148">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="54e07-149">Fordern Sie die Benutzer Berechtigung zum Verwenden der Augen Verfolgung in Ihrer APP an.</span><span class="sxs-lookup"><span data-stu-id="54e07-149">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="54e07-150">Aktivieren Sie die Funktion "Blick auf Eingaben" in Ihrem Paket Manifest.</span><span class="sxs-lookup"><span data-stu-id="54e07-150">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="54e07-151">Anfordern des Zugriffs auf die Eingabe des Augenblicks</span><span class="sxs-lookup"><span data-stu-id="54e07-151">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="54e07-152">Wenn Ihre APP gestartet wird, können Sie [eyespose:: requestaccessasync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) aufrufen, um den Zugriff auf die Eye-Nachverfolgung anzufordern.</span><span class="sxs-lookup"><span data-stu-id="54e07-152">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="54e07-153">Das System fordert den Benutzer bei Bedarf auf und gibt " [gazeinputaccessstatus:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) " zurück, nachdem der Zugriff gewährt wurde.</span><span class="sxs-lookup"><span data-stu-id="54e07-153">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="54e07-154">Dabei handelt es sich um einen asynchronen-Befehl, der eine gewisse zusätzliche Verwaltung erfordert.</span><span class="sxs-lookup"><span data-stu-id="54e07-154">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="54e07-155">Im folgenden Beispiel wird ein getrennter Std:: Thread aufgerufen, um auf das Ergebnis zu warten, das in einer Member-Variable mit dem Namen *m_isEyeTrackingEnabled*gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="54e07-155">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="54e07-156">Das Starten eines getrennten Threads ist nur eine Option für die Behandlung von asynchronen Aufrufen.</span><span class="sxs-lookup"><span data-stu-id="54e07-156">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="54e07-157">Alternativ könnten Sie die neue [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) -Funktionalität verwenden, die C++von/WinRT. unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="54e07-157">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="54e07-158">Im folgenden finden Sie ein weiteres Beispiel für das Anfordern von Benutzerberechtigungen:</span><span class="sxs-lookup"><span data-stu-id="54e07-158">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="54e07-159">Mit eyespose:: IsSupported () kann die Anwendung das Berechtigungs Dialogfeld nur aufrufen, wenn ein Eye Tracker vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="54e07-159">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="54e07-160">Gazinput Access Status m_gazeInputAccessStatus; Dadurch wird verhindert, dass die Berechtigungs Aufforderung immer wieder nach oben und wiederholt wird.</span><span class="sxs-lookup"><span data-stu-id="54e07-160">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="54e07-161">Deklarieren der *Blick Eingabe* Funktion</span><span class="sxs-lookup"><span data-stu-id="54e07-161">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="54e07-162">Doppelklicken Sie in *Projektmappen-Explorer*auf die Datei appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="54e07-162">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="54e07-163">Navigieren Sie dann zum Abschnitt " *Funktionen* ", und überprüfen Sie die Funktion " *Blick Eingaben* "</span><span class="sxs-lookup"><span data-stu-id="54e07-163">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Blick Eingabe Funktion](images/gaze-input-capability.png)

<span data-ttu-id="54e07-165">Dadurch werden dem *Paket* Abschnitt in der appxmanifest-Datei die folgenden Zeilen hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="54e07-165">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="54e07-166">Der Augenblick Strahl</span><span class="sxs-lookup"><span data-stu-id="54e07-166">Getting the eye-gaze ray</span></span>
<span data-ttu-id="54e07-167">Nachdem Sie den Zugriff auf das et erhalten haben, können Sie den Augenblick Strahl jedes Frame abrufen.</span><span class="sxs-lookup"><span data-stu-id="54e07-167">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="54e07-168">Rufen Sie das [spatialpointerpose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -Attribut wie bei der Kopfzeile durch Aufrufen von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und Koordinatensystem ab.</span><span class="sxs-lookup"><span data-stu-id="54e07-168">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="54e07-169">Spatialpointerpose enthält ein [eyespose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) -Objekt über die [Augen](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="54e07-169">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="54e07-170">Dieser Wert ist nur ungleich NULL, wenn die Eye-Nachverfolgung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="54e07-170">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="54e07-171">Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät über eine Eye Tracking-Kalibrierung verfügt, indem Sie [eyespose:: iscalibrationvalid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="54e07-171">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="54e07-172">Verwenden Sie als nächstes die Eigenschaft " [Blick](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) ", um ein [spatialray](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) zu erhalten, das die Position und Richtung des Augenblicks zusammen hängelt.</span><span class="sxs-lookup"><span data-stu-id="54e07-172">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="54e07-173">Die Eigenschaft "Blick" kann in manchen Fällen NULL sein. Achten Sie daher darauf, dies zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="54e07-173">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="54e07-174">Dies kann vorkommen, wenn ein Benutzer mit einem kalibrierten Benutzer die Augen vorübergehend schließt.</span><span class="sxs-lookup"><span data-stu-id="54e07-174">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="54e07-175">Der folgende Code zeigt, wie Sie auf den Augenblick-Strahl zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="54e07-175">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-is-not-available"></a><span data-ttu-id="54e07-176">Fallback, wenn die Augen Verfolgung nicht verfügbar ist</span><span class="sxs-lookup"><span data-stu-id="54e07-176">Fallback when eye tracking is not available</span></span>
<span data-ttu-id="54e07-177">Wie in unserer Design Dokumentation für die [Augen Verfolgung](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)erwähnt, sollten sowohl Designer als auch Entwickler wissen, dass es Instanzen geben kann, in denen Überwachungsdaten für Ihre APP möglicherweise nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="54e07-177">As mentioned in our [eye tracking design docs](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers as well as developers should be aware that there may be instances in which eye tracking data may not be available to your app.</span></span>
<span data-ttu-id="54e07-178">Es gibt verschiedene Gründe dafür, dass ein Benutzer, der nicht gerade nicht gerade nicht gerade ist, den Zugriff der APP auf seine Überwachungsdaten oder einfach auf temporäre Störungen (wie z. b. smudges auf den hololens-Hypervisor oder das Haar Ausblenden der Augen des Benutzers) verweigert.</span><span class="sxs-lookup"><span data-stu-id="54e07-178">There are various reasons for this ranging from a user not being calibrated, the user having denied the app access to his/her eye tracking data or simply temporary interferences (such as smudges on the HoloLens visor or hair occluding the user's eyes).</span></span> <span data-ttu-id="54e07-179">Einige der APIs wurden bereits in diesem Dokument erwähnt. im folgenden finden Sie eine Übersicht darüber, wie Sie erkennen können, dass die Augen Verfolgung als Kurzübersicht verfügbar ist:</span><span class="sxs-lookup"><span data-stu-id="54e07-179">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="54e07-180">Überprüfen Sie, ob das System die Augen Verfolgung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="54e07-180">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="54e07-181">Wenden Sie die folgende *Methode*an: [Windows. perception. People. eyespose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="54e07-181">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="54e07-182">Überprüfen Sie, ob der Benutzer auf eine Kalibrierung fest.</span><span class="sxs-lookup"><span data-stu-id="54e07-182">Check that the user is calibrated.</span></span> <span data-ttu-id="54e07-183">Folgende *Eigenschaft*aufzurufen: [Windows. perception. People. eyespose. iscalibrationvalid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="54e07-183">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="54e07-184">Überprüfen Sie, ob der Benutzer Ihre APP berechtigt hat, ihre Überwachungsdaten zu verwenden: Rufen Sie den aktuellen _"gazeinputaccessstatus"_ ab.</span><span class="sxs-lookup"><span data-stu-id="54e07-184">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="54e07-185">Ein Beispiel hierfür finden Sie unter [anfordern des Zugriffs auf die Eingabe](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="54e07-185">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="54e07-186">Darüber hinaus können Sie überprüfen, ob Ihre Augen Verfolgungs Daten nicht veraltet sind, indem Sie ein Timeout zwischen empfangenen Datenaktualisierungen für die Augen Verfolgung hinzufügen und andernfalls auf den Haupt Blick zurückgreifen, wie unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="54e07-186">In addition, you may want to check that your eye tracking data is not stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>  
<span data-ttu-id="54e07-187">Weitere Informationen finden Sie in unseren [Fall Back Entwurfs Überlegungen](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .</span><span class="sxs-lookup"><span data-stu-id="54e07-187">Please visit our [fallback design considerations](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="54e07-188">Korrelieren von Blick mit anderen Eingaben</span><span class="sxs-lookup"><span data-stu-id="54e07-188">Correlating gaze with other inputs</span></span>
<span data-ttu-id="54e07-189">Manchmal stellen Sie möglicherweise fest, dass Sie eine [spatialpointerpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) benötigen, die einem Ereignis in der Vergangenheit entspricht.</span><span class="sxs-lookup"><span data-stu-id="54e07-189">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="54e07-190">Wenn der Benutzer beispielsweise eine Klimaanlage durchführt, möchte Ihre APP möglicherweise wissen, was Sie sich angeschaut haben.</span><span class="sxs-lookup"><span data-stu-id="54e07-190">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="54e07-191">Zu diesem Zweck wäre die einfache Verwendung von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit der vorhergesagten Frame Zeit aufgrund der Latenz zwischen der System Eingabe Verarbeitung und der Anzeigezeit ungenau.</span><span class="sxs-lookup"><span data-stu-id="54e07-191">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="54e07-192">Wenn Sie den Augenblick für das anvisieren verwenden, werden die Augen darüber hinaus weiter bewegt, bevor eine Commit-Aktion abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="54e07-192">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="54e07-193">Dabei handelt es sich weniger um ein Problem bei einer einfachen Luft tippen, aber es wird wichtiger, wenn Sie lange Sprachbefehle mit fast-Eye-Bewegungen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="54e07-193">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="54e07-194">Eine Möglichkeit zur Behandlung dieses Szenarios besteht darin, einen zusätzlichen aufzurufenden [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)mithilfe eines historischen Zeitstempels zu erstellen, der dem Eingabe Ereignis entspricht.</span><span class="sxs-lookup"><span data-stu-id="54e07-194">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="54e07-195">Bei Eingaben, die den spatialinteraktionmanager weiterleiten, gibt es jedoch eine einfachere Methode.</span><span class="sxs-lookup"><span data-stu-id="54e07-195">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="54e07-196">Der [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) verfügt über seine eigene [trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="54e07-196">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="54e07-197">Der Aufruf von, der eine perfekt korrelierte [spatialpointerpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne den "Guess work" bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="54e07-197">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="54e07-198">Weitere Informationen zum Arbeiten mit spatialinteraktionsourcestates finden Sie [in den Hand-und Bewegungs Controllern in der DirectX-](hands-and-motion-controllers-in-directx.md) Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="54e07-198">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="54e07-199">Energie</span><span class="sxs-lookup"><span data-stu-id="54e07-199">Calibration</span></span>
<span data-ttu-id="54e07-200">Damit die Eye-Nachverfolgung ordnungsgemäß funktioniert, muss jeder Benutzer über eine [Eye Tracking-benutzerkalibrierung](calibration.md)verfügen.</span><span class="sxs-lookup"><span data-stu-id="54e07-200">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](calibration.md).</span></span> <span data-ttu-id="54e07-201">Dies ermöglicht es dem Gerät, das System für eine komfortablere und qualitativ hochwertige Anzeige für den Benutzer anzupassen und gleichzeitig eine genaue Eye-Nachverfolgung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="54e07-201">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="54e07-202">Entwickler müssen nichts auf Ihrem Ende durchführen, um die benutzerkalibrierung zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="54e07-202">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="54e07-203">Das System stellt sicher, dass der Benutzer in den folgenden Situationen aufgefordert wird, das Gerät zu kalibrieren: \* der Benutzer verwendet das Gerät zum ersten Mal \* der Benutzer hat sich zuvor am Kalibrierungsprozess entschieden \* der Kalibrierungsprozess war nicht erfolgreich. Zeitpunkt, zu dem der Benutzer das Gerät verwendet hat</span><span class="sxs-lookup"><span data-stu-id="54e07-203">The system will ensure that the user gets prompted to calibrate the device under the following circumstances: \*The user is using the device for the first time \*The user previously opted out of the calibration process \*The calibration process did not succeed the last time the user used the device</span></span>

<span data-ttu-id="54e07-204">Entwickler sollten sicherstellen, dass Sie angemessene Unterstützung für Benutzer bereitstellen, für die die Augen Verfolgungs Daten möglicherweise nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="54e07-204">Developers should make sure to provide adequate support for users for whom eye tracking data may not be available.</span></span> <span data-ttu-id="54e07-205">Erfahren Sie mehr über Überlegungen zu Fall Back-Lösungen bei der [Überwachung von hololens 2](eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="54e07-205">Learn more about considerations for fallback solutions at [Eye tracking on Hololens 2](eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="54e07-206">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="54e07-206">See also</span></span>
* [<span data-ttu-id="54e07-207">Kalibrierung</span><span class="sxs-lookup"><span data-stu-id="54e07-207">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="54e07-208">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="54e07-208">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="54e07-209">Blick auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="54e07-209">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="54e07-210">Überblicks-und Commit-Eingabe Modell</span><span class="sxs-lookup"><span data-stu-id="54e07-210">Gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="54e07-211">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="54e07-211">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="54e07-212">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="54e07-212">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
