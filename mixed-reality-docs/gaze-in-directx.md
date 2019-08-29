---
title: Kopf-und Augenblick in DirectX
description: Entwicklerhandbuch zur Verwendung von Head-Blick und Eye-Nachverfolgung in nativen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: Augenblick, Haupt Blick, Head-Tracking, Eye Tracking, DirectX, Input, holograms
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122060"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="677d1-104">Eingaben in den Kopf-und Augenblick in DirectX</span><span class="sxs-lookup"><span data-stu-id="677d1-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="677d1-105">In Windows Mixed Reality werden die Eingaben für Eye und Head-Blick verwendet, um zu bestimmen, was der Benutzer sieht.</span><span class="sxs-lookup"><span data-stu-id="677d1-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="677d1-106">Dies kann verwendet werden, um primäre Eingabe Modelle, wie z. b. [Kopf-und Commit](gaze-and-commit.md), zu steuern und um Kontext für Interaktions Typen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="677d1-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="677d1-107">Es gibt zwei Arten von Blick Vektoren, die über die API bereitgestellt werden: Kopf-und Augenblick.</span><span class="sxs-lookup"><span data-stu-id="677d1-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="677d1-108">Beide werden als dreidimensionale Ray mit einem Ursprung und einer Richtung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="677d1-109">Anwendungen können dann in Ihre Szenen oder in der realen Welt integriert werden und bestimmen, was der Benutzer als Ziel verwendet.</span><span class="sxs-lookup"><span data-stu-id="677d1-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="677d1-110">Der **Kopf** zeilig stellt die Richtung dar, in der die Kopfzeile des Benutzers gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="677d1-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="677d1-111">Stellen Sie sich dies als Position und Vorwärtsrichtung des Geräts selbst vor, wobei die Position den Mittelpunkt zwischen den beiden anzeigen darstellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="677d1-112">Der Haupt Blick ist auf allen Geräten mit gemischter Realität verfügbar.</span><span class="sxs-lookup"><span data-stu-id="677d1-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="677d1-113">Der Augen **Blick** stellt die Richtung dar, in der die Augen des Benutzers suchen.</span><span class="sxs-lookup"><span data-stu-id="677d1-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="677d1-114">Der Ursprung befindet sich zwischen den Augen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="677d1-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="677d1-115">Es ist auf Geräten mit gemischter Realität verfügbar, die ein Augen Verfolgungssystem enthalten.</span><span class="sxs-lookup"><span data-stu-id="677d1-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="677d1-116">Mit der [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API ist sowohl der Kopf-als auch der Augenblick-Strahlen zugänglich.</span><span class="sxs-lookup"><span data-stu-id="677d1-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="677d1-117">Sie können einfach [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) aufrufen, um ein neues spatialpointerpose-Objekt am angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md)zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="677d1-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="677d1-118">Diese spatialpointerpose enthält den Ursprung und die Richtung des Haupt Blicks.</span><span class="sxs-lookup"><span data-stu-id="677d1-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="677d1-119">Sie enthält außerdem einen Blick auf den Ursprung und die Richtung des Augenblicks, wenn die Augen Verfolgung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="677d1-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="677d1-120">Verwenden des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="677d1-120">Using head-gaze</span></span>

<span data-ttu-id="677d1-121">Um auf den Kopf Blick zuzugreifen, rufen Sie zunächst [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) auf, um ein neues spatialpointerpose-Objekt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="677d1-121">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="677d1-122">Sie müssen die folgenden Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="677d1-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="677d1-123">Ein [spatialcoordinatesystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , das das gewünschte Koordinatensystem für den Haupt Blick darstellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="677d1-124">Dies wird von der *CoordinateSystem* -Variablen im folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="677d1-125">Weitere Informationen finden Sie im Entwicklerhandbuch zu [Koordinatensystemen](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="677d1-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="677d1-126">Ein [Zeitstempel](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , der die genaue Uhrzeit der angeforderten Kopfzeile darstellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="677d1-127">In der Regel verwenden Sie einen Zeitstempel, der der Uhrzeit entspricht, zu der der aktuelle Frame angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="677d1-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="677d1-128">Sie können diesen vorhergesagten Anzeigezeit Stempel von einem [holographicframevorhersage](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt erhalten, das über den aktuellen [holographicframe](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="677d1-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="677d1-129">Dieses holographicframevorhersage-Objekt wird durch die *Vorhersage* Variable im folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="677d1-130">Sobald Sie über eine gültige spatialpointerpose verfügen, sind die Kopf-und Vorwärtsrichtung als Eigenschaften zugänglich.</span><span class="sxs-lookup"><span data-stu-id="677d1-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="677d1-131">Der folgende Code zeigt, wie Sie darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="677d1-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="677d1-132">Verwenden des Augenblicks</span><span class="sxs-lookup"><span data-stu-id="677d1-132">Using eye-gaze</span></span>

<span data-ttu-id="677d1-133">Die Eye-Eye-API ähnelt der Kopfzeile.</span><span class="sxs-lookup"><span data-stu-id="677d1-133">The eye-gaze API is very similar to head-gaze.</span></span>  <span data-ttu-id="677d1-134">Dabei wird dieselbe [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API verwendet, die einen Strahl Ursprung und eine Richtung bereitstellt, die Sie für Ihre Szene bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="677d1-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="677d1-135">Der einzige Unterschied besteht darin, dass Sie die Eye-Nachverfolgung vor der Verwendung explizit aktivieren müssen.</span><span class="sxs-lookup"><span data-stu-id="677d1-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="677d1-136">Hierfür müssen Sie zwei Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="677d1-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="677d1-137">Fordern Sie die Benutzer Berechtigung zum Verwenden der Augen Verfolgung in Ihrer APP an.</span><span class="sxs-lookup"><span data-stu-id="677d1-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="677d1-138">Aktivieren Sie die Funktion "Blick auf Eingaben" in Ihrem Paket Manifest.</span><span class="sxs-lookup"><span data-stu-id="677d1-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="677d1-139">Anfordern des Zugriffs auf die Eingabe des Augenblicks</span><span class="sxs-lookup"><span data-stu-id="677d1-139">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="677d1-140">Wenn Ihre APP gestartet wird, können Sie [eyespose:: requestaccessasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) aufrufen, um den Zugriff auf die Eye-Nachverfolgung anzufordern.</span><span class="sxs-lookup"><span data-stu-id="677d1-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="677d1-141">Das System fordert den Benutzer bei Bedarf auf und gibt " [gazeinputaccessstatus:: Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) " zurück, nachdem der Zugriff gewährt wurde.</span><span class="sxs-lookup"><span data-stu-id="677d1-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="677d1-142">Dabei handelt es sich um einen asynchronen-Befehl, der eine gewisse zusätzliche Verwaltung erfordert.</span><span class="sxs-lookup"><span data-stu-id="677d1-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="677d1-143">Im folgenden Beispiel wird ein getrennter Std:: Thread aufgerufen, um auf das Ergebnis zu warten, das in einer Member-Variable mit dem Namen *m_isEyeTrackingEnabled*gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="677d1-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="677d1-144">Das Starten eines getrennten Threads ist nur eine Option für die Behandlung von asynchronen Aufrufen.</span><span class="sxs-lookup"><span data-stu-id="677d1-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="677d1-145">Alternativ könnten Sie die neue [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) -Funktionalität verwenden, die C++von/WinRT. unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="677d1-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="677d1-146">Im folgenden finden Sie ein weiteres Beispiel für das Anfordern von Benutzerberechtigungen:</span><span class="sxs-lookup"><span data-stu-id="677d1-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="677d1-147">Mit eyespose:: IsSupported () kann die Anwendung das Berechtigungs Dialogfeld nur aufrufen, wenn ein Eye Tracker vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="677d1-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="677d1-148">Gazinput Access Status m_gazeInputAccessStatus; Dadurch wird verhindert, dass die Berechtigungs Aufforderung immer wieder nach oben und wiederholt wird.</span><span class="sxs-lookup"><span data-stu-id="677d1-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="677d1-149">Deklarieren der *Blick Eingabe* Funktion</span><span class="sxs-lookup"><span data-stu-id="677d1-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="677d1-150">Doppelklicken Sie in *Projektmappen-Explorer*auf die Datei appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="677d1-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="677d1-151">Navigieren Sie dann zum Abschnitt " *Funktionen* ", und überprüfen Sie die Funktion " *Blick Eingaben* "</span><span class="sxs-lookup"><span data-stu-id="677d1-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Blick Eingabe Funktion](images/gaze-input-capability.png)

<span data-ttu-id="677d1-153">Dadurch werden dem *Paket* Abschnitt in der appxmanifest-Datei die folgenden Zeilen hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="677d1-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="677d1-154">Der Augenblick Strahl</span><span class="sxs-lookup"><span data-stu-id="677d1-154">Getting the eye-gaze ray</span></span>
<span data-ttu-id="677d1-155">Nachdem Sie den Zugriff auf das et erhalten haben, können Sie den Augenblick Strahl jedes Frame abrufen.</span><span class="sxs-lookup"><span data-stu-id="677d1-155">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="677d1-156">Rufen Sie das [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -Attribut wie bei der Kopfzeile durch Aufrufen von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und Koordinatensystem ab.</span><span class="sxs-lookup"><span data-stu-id="677d1-156">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="677d1-157">Spatialpointerpose enthält ein [eyespose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) -Objekt über die [Augen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="677d1-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="677d1-158">Dieser Wert ist nur ungleich NULL, wenn die Eye-Nachverfolgung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="677d1-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="677d1-159">Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät über eine Eye Tracking-Kalibrierung verfügt, indem Sie [eyespose:: iscalibrationvalid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)aufrufen.</span><span class="sxs-lookup"><span data-stu-id="677d1-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="677d1-160">Verwenden Sie als nächstes die Eigenschaft " [Blick](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) ", um ein [spatialray](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) zu erhalten, das die Position und Richtung des Augenblicks zusammen hängelt.</span><span class="sxs-lookup"><span data-stu-id="677d1-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="677d1-161">Die Eigenschaft "Blick" kann in manchen Fällen NULL sein. Achten Sie daher darauf, dies zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="677d1-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="677d1-162">Dies kann vorkommen, wenn ein Benutzer mit einem kalibrierten Benutzer die Augen vorübergehend schließt.</span><span class="sxs-lookup"><span data-stu-id="677d1-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="677d1-163">Der folgende Code zeigt, wie Sie auf den Augenblick-Strahl zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="677d1-163">The following code shows how to access the eye-gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="677d1-164">Korrelieren von Blick mit anderen Eingaben</span><span class="sxs-lookup"><span data-stu-id="677d1-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="677d1-165">Manchmal stellen Sie möglicherweise fest, dass Sie eine [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) benötigen, die einem Ereignis in der Vergangenheit entspricht.</span><span class="sxs-lookup"><span data-stu-id="677d1-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="677d1-166">Wenn der Benutzer beispielsweise eine Klimaanlage durchführt, möchte Ihre APP möglicherweise wissen, was Sie sich angeschaut haben.</span><span class="sxs-lookup"><span data-stu-id="677d1-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="677d1-167">Zu diesem Zweck wäre die einfache Verwendung von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit der vorhergesagten Frame Zeit aufgrund der Latenz zwischen der System Eingabe Verarbeitung und der Anzeigezeit ungenau.</span><span class="sxs-lookup"><span data-stu-id="677d1-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="677d1-168">Wenn Sie den Augenblick für das anvisieren verwenden, werden die Augen darüber hinaus weiter bewegt, bevor eine Commit-Aktion abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="677d1-168">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="677d1-169">Dabei handelt es sich weniger um ein Problem bei einer einfachen Luft tippen, aber es wird wichtiger, wenn Sie lange Sprachbefehle mit fast-Eye-Bewegungen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="677d1-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="677d1-170">Eine Möglichkeit zur Behandlung dieses Szenarios besteht darin, einen zusätzlichen aufzurufenden [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)mithilfe eines historischen Zeitstempels zu erstellen, der dem Eingabe Ereignis entspricht.</span><span class="sxs-lookup"><span data-stu-id="677d1-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="677d1-171">Bei Eingaben, die den spatialinteraktionmanager weiterleiten, gibt es jedoch eine einfachere Methode.</span><span class="sxs-lookup"><span data-stu-id="677d1-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="677d1-172">Der [spatialinteraktionsourcestate](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) verfügt über seine eigene [trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="677d1-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="677d1-173">Der Aufruf von, der eine perfekt korrelierte [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne den "Guess work" bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="677d1-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="677d1-174">Weitere Informationen zum Arbeiten mit spatialinteraktionsourcestates finden Sie [in den Hand-und Bewegungs Controllern in der DirectX-](hands-and-motion-controllers-in-directx.md) Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="677d1-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="677d1-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="677d1-175">See also</span></span>
* [<span data-ttu-id="677d1-176">Kopf-und Commit-Eingabe Modell</span><span class="sxs-lookup"><span data-stu-id="677d1-176">Head-gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="677d1-177">Blick auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="677d1-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="677d1-178">Kalibrierung</span><span class="sxs-lookup"><span data-stu-id="677d1-178">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="677d1-179">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="677d1-179">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="677d1-180">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="677d1-180">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="677d1-181">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="677d1-181">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
