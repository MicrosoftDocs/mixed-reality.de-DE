---
title: Rendering in DirectX
description: Erläutert das Holographic-Rendering für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holograms, Rendering, 3D-Grafiken, holographicframe, Renderschleife, Update Schleife, Exemplarische Vorgehensweise, Beispielcode, Direct3D
ms.openlocfilehash: 6b2e2dca9115d7093e94019d5ed91201f6ee3424
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940868"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="231bf-104">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="231bf-104">Rendering in DirectX</span></span>

<span data-ttu-id="231bf-105">Windows Mixed Reality basiert auf DirectX, um für Benutzer eine umfassende, grafische Darstellung von 3D-Funktionen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="231bf-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="231bf-106">Die renderingabstraktion befindet sich direkt oberhalb von DirectX und ermöglicht einer APP einen Grund zur Position und Ausrichtung von einem oder mehreren Beobachtern einer Holographic-Szene, die vom System vorhergesagt wurde.</span><span class="sxs-lookup"><span data-stu-id="231bf-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="231bf-107">Der Entwickler kann dann seine Hologramme in Relation zu den einzelnen Kameras finden, sodass die APP diese Hologramme in verschiedenen räumlichen Koordinatensystemen gereinigen kann, wenn der Benutzer sich bewegt.</span><span class="sxs-lookup"><span data-stu-id="231bf-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="231bf-108">Hinweis: in dieser exemplarischen Vorgehensweise wird das Holographic-Rendering in Direct3D 11 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="231bf-108">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="231bf-109">Eine Direct3D 12-Windows Mixed Reality-App-Vorlage wird auch mit der Erweiterung "Mixed Reality App Templates" bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="231bf-109">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="231bf-110">Update für den aktuellen Frame</span><span class="sxs-lookup"><span data-stu-id="231bf-110">Update for the current frame</span></span>

<span data-ttu-id="231bf-111">Um den Anwendungs Zustand für holograms zu aktualisieren, führt die APP einmal pro Frame folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="231bf-111">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="231bf-112">Verschaffen Sie sich einen <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> aus dem Anzeige Verwaltungssystem.</span><span class="sxs-lookup"><span data-stu-id="231bf-112">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="231bf-113">Aktualisieren Sie die Szene mit der aktuellen Vorhersage, bei der die Kameraansicht angezeigt wird, wenn das Rendering abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-113">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="231bf-114">Beachten Sie, dass für die Holographic-Szene mehr als eine Kamera vorhanden sein kann.</span><span class="sxs-lookup"><span data-stu-id="231bf-114">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="231bf-115">Zum Rendering in Holographic Camera-Ansichten führt die APP einmal pro Frame folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="231bf-115">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="231bf-116">Rendering Sie für jede Kamera die Szene für den aktuellen Frame, indem Sie die Kameraansicht und Projektions Matrizen aus dem System verwenden.</span><span class="sxs-lookup"><span data-stu-id="231bf-116">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="231bf-117">Erstellen Sie einen neuen Holographic Frame, und rufen Sie seine Vorhersage ab</span><span class="sxs-lookup"><span data-stu-id="231bf-117">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="231bf-118">Der <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> enthält Informationen, die die APP benötigt, um den aktuellen Frame zu aktualisieren und zu Rendering.</span><span class="sxs-lookup"><span data-stu-id="231bf-118">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="231bf-119">Die APP startet jeden neuen Frame durch Aufrufen der **createnextframe** -Methode.</span><span class="sxs-lookup"><span data-stu-id="231bf-119">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="231bf-120">Wenn diese Methode aufgerufen wird, werden Vorhersagen mit den neuesten verfügbaren Sensordaten erstellt und im **currentvorhersage** -Objekt gekapselt.</span><span class="sxs-lookup"><span data-stu-id="231bf-120">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="231bf-121">Für jeden gerenderten Frame muss ein neues Frame Objekt verwendet werden, da es nur für einen Zeitpunkt gültig ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-121">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="231bf-122">Die **currentvorhersage** -Eigenschaft enthält Informationen, wie z. b. die Kameraposition.</span><span class="sxs-lookup"><span data-stu-id="231bf-122">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="231bf-123">Die Informationen werden auf den genauen Zeitpunkt hochgerechnet, zu dem der Frame erwartungsgemäß für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-123">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="231bf-124">Der folgende Code wird aus **appmain:: Update**entnommen:</span><span class="sxs-lookup"><span data-stu-id="231bf-124">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="231bf-125">Verarbeiten von Kamera Updates</span><span class="sxs-lookup"><span data-stu-id="231bf-125">Process camera updates</span></span>

<span data-ttu-id="231bf-126">Backpuffer können von Frame zu Frame geändert werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-126">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="231bf-127">Ihre APP muss den Hintergrund Puffer für jede Kamera validieren und Ressourcen Sichten und tiefen Puffer nach Bedarf freigeben und neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="231bf-127">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="231bf-128">Beachten Sie, dass der Satz von Posen in der Vorhersage die autoritative Liste der Kameras ist, die im aktuellen Frame verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-128">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="231bf-129">Normalerweise verwenden Sie diese Liste, um den Satz von Kameras zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="231bf-129">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="231bf-130">Aus **appmain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="231bf-130">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="231bf-131">Aus **deviceresources:: ensurecameraresources**:</span><span class="sxs-lookup"><span data-stu-id="231bf-131">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="231bf-132">Das Koordinatensystem zur Verwendung als Grundlage für das Rendering erhalten</span><span class="sxs-lookup"><span data-stu-id="231bf-132">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="231bf-133">Windows Mixed Reality ermöglicht der APP, bei Bedarf verschiedene [Koordinatensysteme](coordinate-systems-in-directx.md) zu erstellen, wie z. b. den angefügten Verweis Rahmen und den stationären Referenzrahmen, der Standorte in der physischen Welt nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="231bf-133">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="231bf-134">Diese Koordinatensysteme können von Ihrer APP dann verwendet werden, um zu verdeutlichen, wo die einzelnen Frames von holograms dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-134">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="231bf-135">Wenn Sie Koordinaten über eine API anfordern, übergeben Sie immer das <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">spatialcoordinatesystem</a> , in dem Sie die Koordinaten ausdrücken möchten.</span><span class="sxs-lookup"><span data-stu-id="231bf-135">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="231bf-136">Aus **appmain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="231bf-136">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="231bf-137">Diese Koordinatensysteme können dann zum Generieren von Stereo Ansichts Matrizen verwendet werden, wenn der Inhalt in der Szene gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="231bf-137">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="231bf-138">Aus **cameraresources:: updateviewprojectionbuffer**:</span><span class="sxs-lookup"><span data-stu-id="231bf-138">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="231bf-139">Verarbeiten von Blick und Gesten Eingaben</span><span class="sxs-lookup"><span data-stu-id="231bf-139">Process gaze and gesture input</span></span>

<span data-ttu-id="231bf-140">Die Zeiger-und [Hand](hands-and-motion-controllers-in-directx.md) Eingaben sind nicht Zeit basiert und müssen daher nicht in der **Steptimer** [-Funktion](gaze-in-directx.md) aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-140">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="231bf-141">Diese Eingabe muss jedoch in den einzelnen Frames angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-141">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="231bf-142">Zeitbasierte Updates verarbeiten</span><span class="sxs-lookup"><span data-stu-id="231bf-142">Process time-based updates</span></span>

<span data-ttu-id="231bf-143">Jede Echtzeit-renderinganwendung benötigt eine Möglichkeit zum Verarbeiten zeitbasierter Updates. Wir bieten eine Möglichkeit, dies in der Windows Holographic-App-Vorlage über eine **Step Timer** -Implementierung umzusetzen.</span><span class="sxs-lookup"><span data-stu-id="231bf-143">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="231bf-144">Dies ähnelt dem in der APP-Vorlage DirectX 11-UWP bereitgestellten Steptimer. Wenn Sie sich also bereits diese Vorlage angesehen haben, sollten Sie sich auf dem Weg zu einem vertrauten Grund befinden.</span><span class="sxs-lookup"><span data-stu-id="231bf-144">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="231bf-145">Diese Beispiel-Hilfsklasse von Steptimer kann festgelegte Zeit Schritt Updates sowie Variable Zeit Schritt Updates bereitstellen, und der Standardmodus ist Variable Zeit Schritte.</span><span class="sxs-lookup"><span data-stu-id="231bf-145">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="231bf-146">Im Fall von Holographic Rendering haben wir ausdrücklich entschieden, nicht zu viel in die Timer-Funktion zu versetzen.</span><span class="sxs-lookup"><span data-stu-id="231bf-146">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="231bf-147">Dies liegt daran, dass Sie ihn als einen festgelegten Zeit Schritt konfigurieren können. in diesem Fall wird er möglicherweise mehrmals pro Frame – oder gar nicht bei manchen Frames aufgerufen – und unsere Holographic-Datenaktualisierungen sollten einmal pro Frame erfolgen.</span><span class="sxs-lookup"><span data-stu-id="231bf-147">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="231bf-148">Aus **appmain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="231bf-148">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="231bf-149">Positionieren und Drehen von holograms im Koordinatensystem</span><span class="sxs-lookup"><span data-stu-id="231bf-149">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="231bf-150">Wenn Sie in einem einzelnen Koordinatensystem arbeiten, wie die Vorlage mit **spatialstationaryreferenceframe**funktioniert, unterscheidet sich dieser Vorgang nicht von dem, was Sie anderweitig in 3D-Grafiken verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="231bf-150">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="231bf-151">Hier drehen wir den Cube und legen die Modell Matrix relativ zur Position im stationären Koordinatensystem fest.</span><span class="sxs-lookup"><span data-stu-id="231bf-151">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="231bf-152">Von **spinningcuberenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="231bf-152">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="231bf-153">**Hinweis zu erweiterten Szenarien:** Der spincube ist ein sehr einfaches Beispiel dafür, wie ein – Hologramm innerhalb eines einzelnen Referenzrahmens positioniert werden kann.</span><span class="sxs-lookup"><span data-stu-id="231bf-153">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="231bf-154">Es ist auch möglich, [mehrere spatialcoordinatesystems](coordinate-systems-in-directx.md) gleichzeitig im gleichen gerenderten Frame zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="231bf-154">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="231bf-155">Aktualisieren konstanter Puffer Daten</span><span class="sxs-lookup"><span data-stu-id="231bf-155">Update constant buffer data</span></span>

<span data-ttu-id="231bf-156">Modell Transformationen für Inhalt werden wie gewohnt aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="231bf-156">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="231bf-157">Jetzt verfügen Sie über die gültigen Transformationen für das Koordinatensystem, in dem Sie das Rendering durchführt.</span><span class="sxs-lookup"><span data-stu-id="231bf-157">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="231bf-158">Von **spinningcuberenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="231bf-158">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="231bf-159">Wie sieht es mit Ansichts-und Projektions Transformationen aus?</span><span class="sxs-lookup"><span data-stu-id="231bf-159">What about view and projection transforms?</span></span> <span data-ttu-id="231bf-160">Um optimale Ergebnisse zu erzielen, möchten wir warten, bis wir fast bereit für unsere Draw-Aufrufe sind, bevor wir diese erhalten.</span><span class="sxs-lookup"><span data-stu-id="231bf-160">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="231bf-161">Aktuellen Frame Rendering</span><span class="sxs-lookup"><span data-stu-id="231bf-161">Render the current frame</span></span>

<span data-ttu-id="231bf-162">Das Rendering in Windows Mixed Reality unterscheidet sich nicht wesentlich vom Rendering in einer 2D-Mono-Anzeige, es gibt jedoch einige Unterschiede, die Sie kennen müssen:</span><span class="sxs-lookup"><span data-stu-id="231bf-162">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="231bf-163">Holographic-Frame Vorhersagen sind wichtig.</span><span class="sxs-lookup"><span data-stu-id="231bf-163">Holographic frame predictions are important.</span></span> <span data-ttu-id="231bf-164">Je näher die Vorhersage ist, wenn Ihr Frame dargestellt wird, desto besser werden die Hologramme aussehen.</span><span class="sxs-lookup"><span data-stu-id="231bf-164">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="231bf-165">Windows Mixed Reality steuert die Kameraansichten.</span><span class="sxs-lookup"><span data-stu-id="231bf-165">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="231bf-166">Sie müssen jedes Rendering durchzuführen, da der Holographic-Frame Sie später für Sie darstellt.</span><span class="sxs-lookup"><span data-stu-id="231bf-166">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="231bf-167">Es wird empfohlen, das Stereo Rendering mithilfe der instanzierten Zeichnung in ein renderzielarray zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="231bf-167">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="231bf-168">In der Holographic-App-Vorlage wird die empfohlene Vorgehensweise für das Zeichnen in ein renderzielarray verwendet, das eine renderzielansicht in einem **Texture2DArray**verwendet.</span><span class="sxs-lookup"><span data-stu-id="231bf-168">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="231bf-169">Wenn Sie ohne Stereo-Instanziierung Renderingvorgang durchführen möchten, müssen Sie zwei nicht-Array-rendertargetviews (einen für jedes Auge) erstellen, die jeweils auf einen der beiden Slices in der **Texture2DArray** verweisen, die für die APP aus dem System bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-169">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="231bf-170">Dies wird nicht empfohlen, da es in der Regel deutlich langsamer als die Verwendung der Instanziierung ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-170">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="231bf-171">Holen Sie sich eine aktualisierte holographicframe-Vorhersage</span><span class="sxs-lookup"><span data-stu-id="231bf-171">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="231bf-172">Durch das Aktualisieren der Frame Vorhersage wird die Effektivität der Bildstabilisierung erhöht und eine genauere Positionierung von holograms aufgrund der kürzeren Zeit zwischen der Vorhersage und der Sichtbarkeit des Frames für den Benutzer ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="231bf-172">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="231bf-173">Aktualisieren Sie Ihre Frame Vorhersage idealerweise direkt vor dem Rendering.</span><span class="sxs-lookup"><span data-stu-id="231bf-173">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="231bf-174">An jede Kamera Rendering</span><span class="sxs-lookup"><span data-stu-id="231bf-174">Render to each camera</span></span>

<span data-ttu-id="231bf-175">Schleife für den Satz von Kamera stellt in der Vorhersage dar und renderauf jeder Kamera in diesem Satz.</span><span class="sxs-lookup"><span data-stu-id="231bf-175">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="231bf-176">**Einrichten Ihres Renderings**</span><span class="sxs-lookup"><span data-stu-id="231bf-176">**Set up your rendering pass**</span></span>

<span data-ttu-id="231bf-177">Windows Mixed Reality verwendet das stereorenderingrendering, um die Illusion von Tiefe zu verbessern und die stereoscopiisch zu rendern, sodass sowohl die linke als auch die Rechte Anzeige aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-177">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="231bf-178">Beim stereorenderingrendering gibt es einen Offset zwischen den beiden anzeigen, der vom Gehirn als tatsächliche Tiefe abgeglichen werden kann.</span><span class="sxs-lookup"><span data-stu-id="231bf-178">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="231bf-179">In diesem Abschnitt wird das stereoserienrendering mithilfe der Instanziierung mithilfe von Code aus der Windows Holographic App-Vorlage behandelt.</span><span class="sxs-lookup"><span data-stu-id="231bf-179">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="231bf-180">Jede Kamera verfügt über ein eigenes Renderziel (BackBuffer) und Ansichts-und Projektions Matrizen in den Holographic-Raum.</span><span class="sxs-lookup"><span data-stu-id="231bf-180">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="231bf-181">Ihre APP muss alle anderen kamerabasierten Ressourcen erstellen, z. b. den tiefen Puffer pro Kamera.</span><span class="sxs-lookup"><span data-stu-id="231bf-181">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="231bf-182">In der Windows Holographic-App-Vorlage stellen wir eine Hilfsklasse bereit, um diese Ressourcen zusammen in DX:: cameraresources zu bündeln.</span><span class="sxs-lookup"><span data-stu-id="231bf-182">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="231bf-183">Beginnen Sie, indem Sie die renderzielsichten einrichten:</span><span class="sxs-lookup"><span data-stu-id="231bf-183">Start by setting up the render target views:</span></span>

<span data-ttu-id="231bf-184">Aus **appmain:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="231bf-184">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="231bf-185">**Verwenden der Vorhersage, um die Ansichts-und Projektions Matrizen für die Kamera zu erhalten**</span><span class="sxs-lookup"><span data-stu-id="231bf-185">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="231bf-186">Die Ansichts-und Projektions Matrizen für jede holografische Kamera werden bei jedem Frame geändert.</span><span class="sxs-lookup"><span data-stu-id="231bf-186">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="231bf-187">Aktualisieren Sie die Daten im Konstanten Puffer für jede holografische Kamera.</span><span class="sxs-lookup"><span data-stu-id="231bf-187">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="231bf-188">Führen Sie diese Schritte aus, nachdem Sie die Vorhersage aktualisiert haben und bevor Sie für diese Kamera Draw-Aufrufe durchführen.</span><span class="sxs-lookup"><span data-stu-id="231bf-188">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="231bf-189">Aus **appmain:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="231bf-189">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="231bf-190">Hier wird gezeigt, wie die Matrizen von der Kamera bezogen werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-190">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="231bf-191">Während dieses Vorgangs wird auch der aktuelle Viewport für die Kamera abgerufen.</span><span class="sxs-lookup"><span data-stu-id="231bf-191">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="231bf-192">Beachten Sie, wie wir ein Koordinatensystem bereitstellen: Dies ist das gleiche Koordinatensystem, das wir zum Verständnis des Blicks verwendet haben. es ist dasselbe Koordinatensystem, das wir zum Positionieren des drehenden Cubes verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="231bf-192">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="231bf-193">Aus **cameraresources:: updateviewprojectionbuffer**:</span><span class="sxs-lookup"><span data-stu-id="231bf-193">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="231bf-194">Der Viewport sollte jeden Frame festlegen.</span><span class="sxs-lookup"><span data-stu-id="231bf-194">The viewport should be set each frame.</span></span> <span data-ttu-id="231bf-195">Der Vertex-Shader (zumindest) benötigt in der Regel Zugriff auf die Ansichts-/Projektionsdaten.</span><span class="sxs-lookup"><span data-stu-id="231bf-195">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="231bf-196">Aus **cameraresources:: attachviewprojectionbuffer**:</span><span class="sxs-lookup"><span data-stu-id="231bf-196">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="231bf-197">**Renderer in den Kamera-Hintergrund Puffer und Commit für den tiefen Puffer**aus:</span><span class="sxs-lookup"><span data-stu-id="231bf-197">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="231bf-198">Es empfiehlt sich, zu überprüfen, ob **trygetviewtransform** erfolgreich war, bevor versucht wird, die Ansichts-/Projektionsdaten zu verwenden, denn wenn das Koordinatensystem nicht erstellbar ist (z. b. wenn die Überwachung unterbrochen wurde), kann Ihre APP nicht mit ihr für diesen Frame bieten</span><span class="sxs-lookup"><span data-stu-id="231bf-198">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="231bf-199">Die Vorlage ruft " **Rendering** " nur für den drehenden Cube auf, wenn die **cameraresources** -Klasse ein erfolgreiches Update angibt.</span><span class="sxs-lookup"><span data-stu-id="231bf-199">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="231bf-200">Um holograms beizubehalten, in denen ein Entwickler oder Benutzer Sie in der Welt platziert, umfasst Windows Mixed Reality Features für die [Bildstabilisierung](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="231bf-200">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="231bf-201">Die Bildstabilisierung hilft dabei, die in einer Renderingpipeline enthaltene Latenz zu verbergen, um den Benutzern die beste holografische Umgebung zu bieten. Es kann ein Fokuspunkt angegeben werden, um die Bildstabilisierung noch weiter zu verbessern, oder es kann ein tiefen Puffer bereitgestellt werden, um die optimierte Bildstabilisierung in Echtzeit zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="231bf-201">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="231bf-202">Um optimale Ergebnisse zu erzielen, sollte Ihre APP einen tiefen Puffer mithilfe der <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> -API bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="231bf-202">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="231bf-203">Die gemischte Realität von Windows kann dann Geometrie Informationen aus dem tiefen Puffer verwenden, um die Bildstabilisierung in Echtzeit zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="231bf-203">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="231bf-204">Die Vorlage für die Windows Holographic-App führt standardmäßig einen Commit für den tiefen Puffer der app durch</span><span class="sxs-lookup"><span data-stu-id="231bf-204">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="231bf-205">Aus **appmain:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="231bf-205">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="231bf-206">Windows verarbeitet Ihre tiefe Textur auf der GPU, daher muss es möglich sein, den tiefen Puffer als Shaderressource zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="231bf-206">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="231bf-207">Der ID3D11Texture2D, den Sie erstellen, sollte ein typloses Format aufweisen und als Shader-Ressourcen Ansicht gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-207">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="231bf-208">Im folgenden finden Sie ein Beispiel für das Erstellen einer tiefen Textur, die für die Bildstabilisierung committet werden kann.</span><span class="sxs-lookup"><span data-stu-id="231bf-208">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="231bf-209">Code für die **Erstellung von tiefen Puffer Ressourcen für CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="231bf-209">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="231bf-210">**Holographic-Inhalt zeichnen**</span><span class="sxs-lookup"><span data-stu-id="231bf-210">**Draw holographic content**</span></span>

<span data-ttu-id="231bf-211">Die Vorlage für die Windows Holographic-App rendert Inhalte in Stereo mithilfe der empfohlenen Vorgehensweise zum Zeichnen der instanziierten Geometrie in eine Texture2DArray der Größe 2.</span><span class="sxs-lookup"><span data-stu-id="231bf-211">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="231bf-212">Sehen wir uns den Teil der Instanziierung an und erläutert, wie er in Windows Mixed Reality funktioniert.</span><span class="sxs-lookup"><span data-stu-id="231bf-212">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="231bf-213">Von **spinningcuberenderer:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="231bf-213">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="231bf-214">Jede Instanz greift auf eine andere Ansicht/Projektions Matrix aus dem Konstanten Puffer zu.</span><span class="sxs-lookup"><span data-stu-id="231bf-214">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="231bf-215">Hier ist die Konstante Puffer Struktur, bei der es sich lediglich um ein Array von 2 Matrizen handelt.</span><span class="sxs-lookup"><span data-stu-id="231bf-215">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="231bf-216">Aus " **vertexshadershared. HLSL**", enthalten in " **vprtvertexshader. HLSL**":</span><span class="sxs-lookup"><span data-stu-id="231bf-216">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="231bf-217">Der Array Index des Renderziels muss für jedes Pixel festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-217">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="231bf-218">Im folgenden Code Ausschnitt wird "Output. viewId" der **SV_RenderTargetArrayIndex** Semantik zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="231bf-218">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="231bf-219">Beachten Sie, dass hierfür eine optionale Direct3D 11,3-Funktion unterstützt wird, mit der die Semantik des Renderziel-Array Indexes aus jeder Shader-Stufe festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="231bf-219">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="231bf-220">Aus **vprtvertexshader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="231bf-220">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="231bf-221">Aus " **vertexshadershared. HLSL**", enthalten in " **vprtvertexshader. HLSL**":</span><span class="sxs-lookup"><span data-stu-id="231bf-221">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="231bf-222">Wenn Sie Ihre vorhandenen instanziierten Zeichentechniken mit dieser Methode zum Zeichnen in ein Array von Stereo Renderziel verwenden möchten, müssen Sie lediglich die doppelte Anzahl von Instanzen zeichnen, die Sie normalerweise haben.</span><span class="sxs-lookup"><span data-stu-id="231bf-222">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="231bf-223">Dividieren Sie im Shader **Input. instId** durch 2, um die ursprüngliche Instanz-ID zu erhalten, die in (z. b.) einen Puffer von objektbezogenen Daten indiziert werden kann: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="231bf-223">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="231bf-224">Wichtiger Hinweis zum Rendern von Stereo Inhalten in hololens</span><span class="sxs-lookup"><span data-stu-id="231bf-224">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="231bf-225">Windows Mixed Reality unterstützt die Möglichkeit, den Renderziel-Array Index aus beliebigen Shader-Stufen festzulegen. Normalerweise handelt es sich hierbei um eine Aufgabe, die nur in der Geometry-Shader-Phase durchgeführt werden kann, weil die Semantik für Direct3D 11 definiert ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-225">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="231bf-226">Hier finden Sie ein umfassendes Beispiel für das Einrichten einer Renderingpipeline, in der nur die Vertex-und Pixel-Shader-Stufen festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="231bf-226">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="231bf-227">Der Shader-Code ist wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="231bf-227">The shader code is as described above.</span></span>

<span data-ttu-id="231bf-228">Von **spinningcuberenderer:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="231bf-228">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="231bf-229">Wichtiger Hinweis zum Rendern auf nicht hololens-Geräten</span><span class="sxs-lookup"><span data-stu-id="231bf-229">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="231bf-230">Wenn Sie den renderzielarray-Index im Vertexshader festlegen, muss der Grafiktreiber ein optionales Direct3D 11,3-Feature unterstützen, das hololens unterstützt.</span><span class="sxs-lookup"><span data-stu-id="231bf-230">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="231bf-231">Ihre APP ist möglicherweise in der Lage, nur diese Methode für das Rendering sicher zu implementieren, und alle Anforderungen werden für die Ausführung auf den Microsoft hololens erfüllt.</span><span class="sxs-lookup"><span data-stu-id="231bf-231">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="231bf-232">Möglicherweise möchten Sie auch den hololens-Emulator verwenden, der ein leistungsfähiges Entwicklungs Tool für Ihre Holographic APP sein kann und Windows Mixed Reality-immersive Headset-Geräte unterstützen, die an Windows 10-PCs angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="231bf-232">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="231bf-233">Unterstützung für den nicht hololens-Renderingpfad (und somit für alle Windows Mixed Reality) ist auch in der Windows Holographic-App-Vorlage integriert.</span><span class="sxs-lookup"><span data-stu-id="231bf-233">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="231bf-234">Im Vorlagen Code finden Sie Code, mit dem Ihre Holographic-App auf der GPU auf dem Entwicklungs-PC ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="231bf-234">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="231bf-235">Im folgenden wird erläutert, wie die **deviceresources** -Klasse diese optionale Funktions Unterstützung prüft.</span><span class="sxs-lookup"><span data-stu-id="231bf-235">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="231bf-236">Aus **deviceresources:: kreatedeviceresources**:</span><span class="sxs-lookup"><span data-stu-id="231bf-236">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="231bf-237">Um das Rendering ohne diese optionale Funktion zu unterstützen, muss Ihre APP einen Geometry-Shader verwenden, um den Renderziel-Array Index festzulegen.</span><span class="sxs-lookup"><span data-stu-id="231bf-237">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="231bf-238">Dieser Code Ausschnitt wird *nach* **vssetconstantbuffers**und *vor* **pssetshader** im Codebeispiel im vorherigen Abschnitt hinzugefügt, in dem erläutert wird, wie Stereo in hololens dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="231bf-238">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="231bf-239">Von **spinningcuberenderer:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="231bf-239">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="231bf-240">**HLSL-Hinweis**: in diesem Fall müssen Sie auch einen leicht geänderten Vertexshader laden, der den renderzielarray-Index an den Geometry-Shader übergibt, indem er eine immer zulässige Shader-Semantik verwendet, z. b. TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="231bf-240">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="231bf-241">Der Geometry-Shader muss keine Arbeit erledigen. der Vorlagen Geometrie-Shader durchläuft alle Daten, mit Ausnahme des Renderziel-Array Indexes, der zum Festlegen der SV_RenderTargetArrayIndex Semantik verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="231bf-241">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="231bf-242">App-Vorlagen Code für **geometryshader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="231bf-242">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="231bf-243">Darstellen</span><span class="sxs-lookup"><span data-stu-id="231bf-243">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="231bf-244">Aktivieren des Holographic Frame zum Darstellen der SwapChain</span><span class="sxs-lookup"><span data-stu-id="231bf-244">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="231bf-245">Mit Windows Mixed Reality steuert das System die Swapkette.</span><span class="sxs-lookup"><span data-stu-id="231bf-245">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="231bf-246">Das System verwaltet dann Frames für jede holografische Kamera, um eine hohe Qualität zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="231bf-246">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="231bf-247">Außerdem bietet es eine Viewport-Aktualisierung jedes Frames für jede Kamera, um die Aspekte des Systems zu optimieren, wie z. b. die Bildstabilisierung oder die Transformation für gemischte Realität.</span><span class="sxs-lookup"><span data-stu-id="231bf-247">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="231bf-248">Eine Holographic-APP, die DirectX verwendet, **ruft daher** nicht in einer DXGI-SwapChain auf.</span><span class="sxs-lookup"><span data-stu-id="231bf-248">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="231bf-249">Stattdessen verwenden Sie die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> -Klasse, um alle SwapChain für einen Frame darzustellen, sobald Sie das Zeichnen abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="231bf-249">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="231bf-250">Aus **deviceresources::P erneut gesendet**:</span><span class="sxs-lookup"><span data-stu-id="231bf-250">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="231bf-251">Standardmäßig wartet diese API, bis der Frame abgeschlossen ist, bevor Sie zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="231bf-251">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="231bf-252">Holographic apps sollten warten, bis der vorherige Frame abgeschlossen ist, bevor die Arbeit an einem neuen Frame gestartet wird, da dadurch die Latenzzeit reduziert wird und bessere Ergebnisse aus Holographic Frame-Vorhersagen erzielt werden können.</span><span class="sxs-lookup"><span data-stu-id="231bf-252">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="231bf-253">Dies ist keine harte Regel, und wenn Sie über Frames verfügen, die mehr als eine Bildschirm Aktualisierung zum Renderingvorgang benötigen, können Sie diesen warte Vorgang deaktivieren, indem Sie den holographicframepresentwaitbehavior-Parameter an <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">presentusingcurrentvorhersage</a>übergeben.</span><span class="sxs-lookup"><span data-stu-id="231bf-253">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="231bf-254">In diesem Fall würden Sie wahrscheinlich einen asynchronen Renderingthread verwenden, um eine fortlaufende Last auf der GPU aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="231bf-254">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="231bf-255">Beachten Sie, dass die Aktualisierungsrate des hololens-Geräts 60Hz beträgt, wobei ein Frame eine Dauer von ungefähr 16 MS hat.</span><span class="sxs-lookup"><span data-stu-id="231bf-255">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="231bf-256">Immersive Headset-Geräte können zwischen 60Hz und 90Hz reichen. beim Aktualisieren der Anzeige bei 90 Hz erhält jeder Frame eine Dauer von ungefähr 11 ms.</span><span class="sxs-lookup"><span data-stu-id="231bf-256">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="231bf-257">Behandeln von DeviceLost-Szenarien in Zusammenarbeit mit holographicframe</span><span class="sxs-lookup"><span data-stu-id="231bf-257">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="231bf-258">DirectX 11-apps müssten in der Regel das von der **Present** -Funktion der DXGI-SwapChain zurückgegebene HRESULT überprüfen, um herauszufinden, ob ein **DeviceLost** -Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-258">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="231bf-259">Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> -Klasse übernimmt diese für Sie.</span><span class="sxs-lookup"><span data-stu-id="231bf-259">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="231bf-260">Überprüfen Sie das <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">holographicframepresentresult</a> , das zurückgegeben wird, um herauszufinden, ob Sie das Direct3D-Gerät und Geräte basierte Ressourcen freigeben und neu erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="231bf-260">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="231bf-261">Beachten Sie Folgendes: Wenn das Direct3D-Gerät verloren gegangen ist und Sie es neu erstellt haben, müssen Sie den <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a> anweisen, das neue Gerät zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="231bf-261">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="231bf-262">Die Swapkette wird für dieses Gerät neu erstellt.</span><span class="sxs-lookup"><span data-stu-id="231bf-262">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="231bf-263">Aus **deviceresources:: initializeusingholographicspace**:</span><span class="sxs-lookup"><span data-stu-id="231bf-263">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="231bf-264">Sobald Ihr Frame angezeigt wird, können Sie zur Hauptprogramm Schleife zurückkehren und zulassen, dass Sie mit dem nächsten Frame fortfahren.</span><span class="sxs-lookup"><span data-stu-id="231bf-264">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="231bf-265">Hybrid Grafik-PCs und Mixed Reality-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="231bf-265">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="231bf-266">Windows 10 Creators Update-PCs **können mit diskreten** und integrierten GPUs konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-266">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="231bf-267">Mit diesen Computertypen wählt Windows den Adapter aus, mit dem das Headset verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-267">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="231bf-268">Anwendungen müssen sicherstellen, dass das von Ihnen erstellte DirectX-Gerät denselben Adapter verwendet.</span><span class="sxs-lookup"><span data-stu-id="231bf-268">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="231bf-269">Allgemeiner Direct3D Beispielcode veranschaulicht das Erstellen eines DirectX-Geräts mithilfe des Standard Hardware Adapters, der auf einem Hybridsystem möglicherweise nicht identisch mit dem für das Headset verwendeten ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-269">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="231bf-270">Um Probleme zu umgehen, kann dies dazu führen, dass <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">holographicadapterid</a> entweder von <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a>verwendet wird. Primaryadapterid () oder <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">holographicdisplay</a>. Adapterid ().</span><span class="sxs-lookup"><span data-stu-id="231bf-270">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="231bf-271">Diese Adapter-ID kann dann verwendet werden, um den richtigen dxgiadapter mithilfe von "IDXGIFactory4. endumadapterbyluid" auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="231bf-271">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="231bf-272">Aus **deviceresources:: initializeusingholographicspace**:</span><span class="sxs-lookup"><span data-stu-id="231bf-272">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="231bf-273">Code zum **Aktualisieren von deviceresources:: kreatedeviceresources zur Verwendung von idxgiadapter**</span><span class="sxs-lookup"><span data-stu-id="231bf-273">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="231bf-274">**Hybrid Grafiken und Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="231bf-274">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="231bf-275">Die Verwendung von Media Foundation auf Hybridsystemen kann zu Problemen führen, bei denen das Video nicht angezeigt wird oder die Video Textur beschädigt ist.</span><span class="sxs-lookup"><span data-stu-id="231bf-275">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="231bf-276">Dies kann der Fall sein, wenn Media Foundation ein Systemverhalten standardmäßig wie oben erwähnt absetzt.</span><span class="sxs-lookup"><span data-stu-id="231bf-276">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="231bf-277">In einigen Szenarien ist das Erstellen eines separaten ID3D11Device erforderlich, um Multithreading zu unterstützen, und die richtigen erstellungsflags werden festgelegt.</span><span class="sxs-lookup"><span data-stu-id="231bf-277">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="231bf-278">Beim Initialisieren des ID3D11Device muss D3D11_CREATE_DEVICE_VIDEO_SUPPORT Flag als Teil des D3D11_CREATE_DEVICE_FLAG definiert werden.</span><span class="sxs-lookup"><span data-stu-id="231bf-278">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="231bf-279">Nachdem das Gerät und der Kontext erstellt wurden, müssen Sie <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">setmultithreadprotected</a> aufrufen, um Multithreading zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="231bf-279">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="231bf-280">Um das Gerät dem <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">imfdxgidebug</a>Manager zuzuordnen, verwenden Sie die <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">imfdxgide vicemanager:: ResetDevice</a> -Funktion.</span><span class="sxs-lookup"><span data-stu-id="231bf-280">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="231bf-281">Code zum **Zuordnen eines ID3D11Device zu imfdxgidevicemanager**:</span><span class="sxs-lookup"><span data-stu-id="231bf-281">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="231bf-282">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="231bf-282">See also</span></span>
* [<span data-ttu-id="231bf-283">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="231bf-283">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="231bf-284">Verwendung des HoloLens Emulators</span><span class="sxs-lookup"><span data-stu-id="231bf-284">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
