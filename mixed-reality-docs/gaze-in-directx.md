---
title: Haupt- und Eye Blicke in DirectX
description: Entwicklerhandbuch für die Verwendung von Head Blicke und Eye-tracking in systemeigenen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: Blicke, Head Blicke, Head, die nachverfolgung, Eye-tracking, Directx, Eingabe, Hologramme
ms.openlocfilehash: ac72c5305527ed2d68945aeb32051cf2246a736e
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453743"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="2e15c-104">Haupt- und Eye bestaunen Eingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="2e15c-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="2e15c-105">In Windows Mixed Reality, Augen und Head Blicke Eingabe verwendet, um zu bestimmen, was der Benutzer ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="2e15c-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="2e15c-106">Dies kann verwendet werden, um die primäre Eingabe-Modelle, wie z. B. Laufwerk [head Blicke und Commit](gaze-and-commit.md), und auch um den Kontext für die Arten von Aktivitäten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2e15c-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="2e15c-107">Es gibt zwei Arten von Blicke Vektoren, die über die API zur Verfügung: head Blicke und Eye Blicke.</span><span class="sxs-lookup"><span data-stu-id="2e15c-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="2e15c-108">Beide dienen als eine drei dimensionalen Chow mit einem Ursprung und Richtung.</span><span class="sxs-lookup"><span data-stu-id="2e15c-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="2e15c-109">Anwendungen können dann Raycast in ihre Szenen oder der realen Welt und zu ermitteln, was der Benutzer abzielt.</span><span class="sxs-lookup"><span data-stu-id="2e15c-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="2e15c-110">**Head bestaunen** stellt die Richtung, die des Benutzers Head in gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2e15c-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="2e15c-111">Stellen Sie sich die Position und Vorwärts, von dem Gerät selbst, und zeigen Sie mit der Position die Mitte darstellt zwischen den zwei angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2e15c-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="2e15c-112">Head Blicke steht auf allen Mixed Reality-Geräten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="2e15c-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="2e15c-113">**Eye Blicke** stellt die Richtung, die der Benutzer die Augen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="2e15c-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="2e15c-114">Der Ursprung befindet sich zwischen dem Benutzer die Augen.</span><span class="sxs-lookup"><span data-stu-id="2e15c-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="2e15c-115">Es steht in Mixed Reality-Geräte, die eine Eye-tracking System enthalten.</span><span class="sxs-lookup"><span data-stu-id="2e15c-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="2e15c-116">Sowohl die Hauptknoten als auch die Augen Blicke Strahlung können Sie über die [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span><span class="sxs-lookup"><span data-stu-id="2e15c-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="2e15c-117">Rufen Sie ganz einfach [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) erhalten Sie ein neues SpatialPointerPose-Objekt, auf dem angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="2e15c-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="2e15c-118">Diese SpatialPointerPose enthält eine Head Blicke Ursprung und eine Richtung.</span><span class="sxs-lookup"><span data-stu-id="2e15c-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="2e15c-119">Es enthält auch ein Auge Blicke Ursprung und die Richtung, wenn Eye-tracking verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2e15c-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="2e15c-120">Head Blicke verwenden</span><span class="sxs-lookup"><span data-stu-id="2e15c-120">Using head gaze</span></span>

<span data-ttu-id="2e15c-121">Starten Sie den Zugriff auf die Head Blicke durch Aufrufen von [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) um ein neues SpatialPointerPose-Objekt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2e15c-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="2e15c-122">Sie müssen die folgenden Parameter zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="2e15c-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="2e15c-123">Ein [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , die das gewünschte Koordinatensystem für den Hauptknoten Blicke darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e15c-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="2e15c-124">Wird dies durch die *Koordinatensystem* Variablen in den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="2e15c-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="2e15c-125">Weitere Informationen finden Sie auf unserer [Koordinatensysteme](coordinate-systems-in-directx.md) -Entwicklerhandbuch.</span><span class="sxs-lookup"><span data-stu-id="2e15c-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="2e15c-126">Ein [Zeitstempel](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , die die genaue Zeit von der angeforderten Head Haltung darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e15c-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="2e15c-127">In der Regel verwenden Sie einen Zeitstempel, der bis zum Zeitpunkt entspricht, wenn der aktuelle Frame angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2e15c-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="2e15c-128">Erhalten Sie diesem Zeitstempel vorhergesagten Anzeige von einem [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt, das über den aktuellen zugänglich ist [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="2e15c-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="2e15c-129">Dieses Objekt HolographicFramePrediction wird dargestellt, durch die *Vorhersage* Variablen in den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="2e15c-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="2e15c-130">Nachdem Sie eine gültige SpatialPointerPose haben, sind die Head-Position und eine vorwärts gerichtete als Eigenschaften zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="2e15c-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="2e15c-131">Der folgende Code zeigt, wie darauf zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="2e15c-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="2e15c-132">Verwenden die Augen Blicke</span><span class="sxs-lookup"><span data-stu-id="2e15c-132">Using eye gaze</span></span>

<span data-ttu-id="2e15c-133">Die Augen Blicke-API ist Head Blicke sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="2e15c-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="2e15c-134">Dabei wird derselbe [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API, die ein Strahl bereitstellt, Ursprung und die Richtung, die Sie für Ihre Szene Raycast können.</span><span class="sxs-lookup"><span data-stu-id="2e15c-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="2e15c-135">Der einzige Unterschied ist, dass Sie Eye-Tracking vor der Verwendung explizit aktiviert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2e15c-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="2e15c-136">Hierzu müssen Sie zwei Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="2e15c-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="2e15c-137">Fordern Sie die Berechtigung zum Eye-tracking in Ihrer app verwenden.</span><span class="sxs-lookup"><span data-stu-id="2e15c-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="2e15c-138">Aktivieren Sie die Funktion "Bestaunen Input" im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="2e15c-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="2e15c-139">Anfordern des Zugriffs auf die Eingabe bestaunen</span><span class="sxs-lookup"><span data-stu-id="2e15c-139">Requesting access to gaze input</span></span>
<span data-ttu-id="2e15c-140">Wenn Ihre app gestartet wird, rufen Sie [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) zum Anfordern des Zugriffs auf Eye-Überwachung.</span><span class="sxs-lookup"><span data-stu-id="2e15c-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="2e15c-141">Das System fordert den Benutzer bei Bedarf, und zurückgeben [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) nach Zugriff gewährt wurde.</span><span class="sxs-lookup"><span data-stu-id="2e15c-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="2e15c-142">Dies ist ein asynchroner Aufruf, damit es ein wenig zusätzliche Verwaltung erfordert.</span><span class="sxs-lookup"><span data-stu-id="2e15c-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="2e15c-143">Im folgende Beispiel startet einen getrennten Std:: Thread warten, das Ergebnis, die auf eine Membervariable namens gespeichert *M_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="2e15c-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="2e15c-144">Starten eines getrennten Threads ist nur eine Option für die Verarbeitung von asynchronen Aufrufe.</span><span class="sxs-lookup"><span data-stu-id="2e15c-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="2e15c-145">Alternativ können Sie die neue verwenden [Co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) von unterstützten Funktionen C++"/ WinRT".</span><span class="sxs-lookup"><span data-stu-id="2e15c-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="2e15c-146">Hier ist ein weiteres Beispiel für die Berechtigung des Benutzers aufgefordert:</span><span class="sxs-lookup"><span data-stu-id="2e15c-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="2e15c-147">EyesPose::IsSupported() kann es sich um die Anwendung aus, um das Dialogfeld "Berechtigung" auszulösen, nur dann, wenn ein Auge-Tracker.</span><span class="sxs-lookup"><span data-stu-id="2e15c-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="2e15c-148">GazeInputAccessStatus M_gazeInputAccessStatus; Dies werden zu verhindern, dass der berechtigungseingabeaufforderung immer wieder eingeblendet.</span><span class="sxs-lookup"><span data-stu-id="2e15c-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="2e15c-149">Deklarieren der *bestaunen Eingabe* Funktion</span><span class="sxs-lookup"><span data-stu-id="2e15c-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="2e15c-150">Klicken Sie mit der Doppelklicken auf die Appxmanifest-Datei im *Projektmappen-Explorer*.</span><span class="sxs-lookup"><span data-stu-id="2e15c-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="2e15c-151">Navigieren Sie dann auf die *Funktionen* Abschnitt, und überprüfen Sie die *bestaunen Eingabe* Funktion.</span><span class="sxs-lookup"><span data-stu-id="2e15c-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Eingabe Blicke-Funktion](images/gaze-input-capability.png)

<span data-ttu-id="2e15c-153">Dadurch werden die folgenden Zeilen auf die *Paket* Abschnitt in der Appxmanifest-Datei:</span><span class="sxs-lookup"><span data-stu-id="2e15c-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="2e15c-154">Die Augen Blicke Chow abrufen</span><span class="sxs-lookup"><span data-stu-id="2e15c-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="2e15c-155">Nachdem Sie den Zugriff auf ET erhalten haben, können Sie dem Auge Blicke Strahl jeder Frame erfasst.</span><span class="sxs-lookup"><span data-stu-id="2e15c-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="2e15c-156">Genau wie bei Head Blicke, erhalten die [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) durch Aufrufen von [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und der Koordinatensystem.</span><span class="sxs-lookup"><span data-stu-id="2e15c-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="2e15c-157">Die SpatialPointerPose enthält ein [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) -Objekt über die [Augen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="2e15c-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="2e15c-158">Dies ist nicht Null nur, wenn Eye-tracking aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2e15c-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="2e15c-159">Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät ein blickbewegungsregistrierung Kalibrierung durch den Aufruf hat [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="2e15c-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="2e15c-160">Verwenden Sie als Nächstes die [bestaunen](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) -Eigenschaft zum Abrufen der eine [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) Contianing Auge bestaunen, Position und die Richtung.</span><span class="sxs-lookup"><span data-stu-id="2e15c-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="2e15c-161">Die Blicke-Eigenschaft kann auch null sein, daher sollten Sie unbedingt dafür.</span><span class="sxs-lookup"><span data-stu-id="2e15c-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="2e15c-162">Dies kann ist treten auf, wenn ein kalibrierten Benutzer vorübergehend ihren Augen Wirklichkeit schließt.</span><span class="sxs-lookup"><span data-stu-id="2e15c-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="2e15c-163">Der folgende Code zeigt, wie auf den Auge Blicke Strahl zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="2e15c-163">The following code shows how to access the eye gaze ray.</span></span>

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
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="2e15c-164">Korrelieren von Blicke mit anderen Eingaben</span><span class="sxs-lookup"><span data-stu-id="2e15c-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="2e15c-165">Manchmal können möglicherweise müssen Sie eine [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , die mit einem Ereignis in der Vergangenheit entspricht.</span><span class="sxs-lookup"><span data-stu-id="2e15c-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="2e15c-166">Z. B. wenn ein Air Tippen Sie auf der Benutzer ausführt, möchten Ihre app wissen, wonach sie gesucht haben, an.</span><span class="sxs-lookup"><span data-stu-id="2e15c-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="2e15c-167">Zu diesem Zweck verwenden Sie einfach [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit den vorhergesagten Frame Zeit wäre ungenaue aufgrund der Latenz zwischen System Eingabeverarbeitung und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2e15c-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="2e15c-168">Darüber hinaus neigen dazu, wenn für die Zielgruppenadressierung Eye Blicke verwenden möchten, im Auge sogar vor dem Abschluss einer Commit-Aktion fortfahren.</span><span class="sxs-lookup"><span data-stu-id="2e15c-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="2e15c-169">Dies liegt ein Problem für eine einfache per Funk tippen, aber wichtiger wird, wenn lange Sprachbefehle mit schnellen Eye kombinieren.</span><span class="sxs-lookup"><span data-stu-id="2e15c-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="2e15c-170">Eine Möglichkeit zum Behandeln dieses Szenarios ist, stellen einen zusätzlichen Aufruf [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mit einem historischen Zeitstempel, der das Eingabeereignis entspricht.</span><span class="sxs-lookup"><span data-stu-id="2e15c-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="2e15c-171">Für die Eingabe, die über die SpatialInteractionManager weiterleitet, ist jedoch eine einfachere Methode.</span><span class="sxs-lookup"><span data-stu-id="2e15c-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="2e15c-172">Die [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) hat seine eigenen [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) Funktion.</span><span class="sxs-lookup"><span data-stu-id="2e15c-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="2e15c-173">Aufrufen, die perfekt korrelierte bereitstellen [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne Frage.</span><span class="sxs-lookup"><span data-stu-id="2e15c-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="2e15c-174">Weitere Informationen zum Arbeiten mit SpatialInteractionSourceStates sehen Sie sich die [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md) Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="2e15c-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e15c-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2e15c-175">See also</span></span>
* [<span data-ttu-id="2e15c-176">Head-Eingabemodell Blicke und commit</span><span class="sxs-lookup"><span data-stu-id="2e15c-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2e15c-177">Eye-tracking für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2e15c-177">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2e15c-178">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="2e15c-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="2e15c-179">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="2e15c-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="2e15c-180">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="2e15c-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
