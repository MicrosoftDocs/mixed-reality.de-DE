---
title: Rendern in DirectX
description: Erläutert, holographic Rendering für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, der Rendering, der 3D-Grafiken HolographicFrame, rendern, Schleife, "Update"-Schleife, exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629036"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="87bb3-104">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="87bb3-104">Rendering in DirectX</span></span>

<span data-ttu-id="87bb3-105">Windows Mixed Reality basiert auf DirectX, um umfassende zu erzeugen, 3D grafische Umgebungen für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="87bb3-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="87bb3-106">Die Rendering-Abstraktion befindet sich direkt über DirectX und können eine app befassen Position und Ausrichtung von ein oder mehrere Beobachter über einer Szene holographic als vorhergesagten vom System.</span><span class="sxs-lookup"><span data-stu-id="87bb3-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="87bb3-107">Entwickler kann ermitteln, deren Hologramme Bezug auf jede Kamera, lassen die app diese Hologramme in verschiedenen räumliche Koordinatensysteme zu rendern, wie der Benutzer, um wechselt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="87bb3-108">Update für den aktuellen frame</span><span class="sxs-lookup"><span data-stu-id="87bb3-108">Update for the current frame</span></span>

<span data-ttu-id="87bb3-109">Zum Aktualisieren des Anwendungsstatus Hologramme einmal pro Bild der app führt Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="87bb3-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="87bb3-110">Abrufen einer <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> aus dem Verwaltungssystem anzeigen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="87bb3-111">Aktualisieren Sie die Szene, mit der aktuellen Vorhersage, wo die Kameraansicht werden sollen, wenn Rendern abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="87bb3-112">Beachten Sie, dass mehr als einer Kamera für die Szene holographic möglich.</span><span class="sxs-lookup"><span data-stu-id="87bb3-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="87bb3-113">Um mit holographic Kameraansichten zu rendern, einmal pro Bild der app führt Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="87bb3-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="87bb3-114">Rendern Sie für jede Kamera der Szene für den aktuellen Frame, mit der Kamera Ansichts- und Projektionstransformation Matrizen aus dem System ein.</span><span class="sxs-lookup"><span data-stu-id="87bb3-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="87bb3-115">Erstellen Sie einen neuen holographic Frame, und rufen Sie die Vorhersage</span><span class="sxs-lookup"><span data-stu-id="87bb3-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="87bb3-116">Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> enthält Informationen, die die app benötigt werden, um zu aktualisieren und den aktuellen Frame zu rendern.</span><span class="sxs-lookup"><span data-stu-id="87bb3-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="87bb3-117">Die app beginnt jede neuen Frame mit dem Aufruf der **CreateNextFrame** Methode.</span><span class="sxs-lookup"><span data-stu-id="87bb3-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="87bb3-118">Wenn diese Methode aufgerufen wird, erfolgen Vorhersagen unter Verwendung der neuesten Sensordaten verfügbar, und im gekapselten **CurrentPrediction** Objekt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="87bb3-119">Ein neues Frameobjekt muss für jeden gerenderten Frame verwendet werden, wie es nur gültig für einen Zeitpunkt in der Zeit ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="87bb3-120">Die **CurrentPrediction** Eigenschaft enthält Informationen wie z. B. die Position (Kamera).</span><span class="sxs-lookup"><span data-stu-id="87bb3-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="87bb3-121">Die Informationen wird auf den genauen Zeitpunkt extrapoliert, wenn der Frame erwartet wird, für den Benutzer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="87bb3-122">Der folgende Code ist ein Auszug aus **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="87bb3-123">Prozess-Kamera-updates</span><span class="sxs-lookup"><span data-stu-id="87bb3-123">Process camera updates</span></span>

<span data-ttu-id="87bb3-124">Hintergrundpuffer können von einem Frame zu Frame ändern.</span><span class="sxs-lookup"><span data-stu-id="87bb3-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="87bb3-125">Ihre app muss die Sicherung überprüfen Puffern für jede Kamera, freigeben und Ressourcenansichten und Tiefenpuffern nach Bedarf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="87bb3-126">Beachten Sie, dass der Satz von ist in die Vorhersage der autoritative Liste der Kameras, die in den aktuellen Frame verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="87bb3-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="87bb3-127">In der Regel verwenden Sie diese Liste auf den Satz von Kameras zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="87bb3-128">Von **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="87bb3-129">Von **DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="87bb3-130">Erhalten Sie das Koordinatensystem, die als Grundlage für das Rendering verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="87bb3-131">Windows Mixed Reality ermöglicht Ihrer app, die Erstellung verschiedener [Koordinatensysteme](coordinate-systems-in-directx.md) nach Bedarf, z. B. den angefügten Verweisdaten und der Frame stationär Verweis zur nachverfolgung von Standorten in der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="87bb3-132">Ihre app können Sie dann diese Koordinatensysteme Grund dazu, wo Sie Hologramme jeder Frame zu rendern.</span><span class="sxs-lookup"><span data-stu-id="87bb3-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="87bb3-133">Beim Anfordern von Koordinaten aus einer API, Sie werden immer übergeben die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> in dem diese Koordinaten ausgedrückt werden soll.</span><span class="sxs-lookup"><span data-stu-id="87bb3-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="87bb3-134">Von **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="87bb3-135">Diese Koordinatensysteme kann dann verwendet werden, um Stereo Ansicht Matrizen zu generieren, wenn den Inhalt in der Szene zu rendern.</span><span class="sxs-lookup"><span data-stu-id="87bb3-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="87bb3-136">Von **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="87bb3-137">Prozess Blicke und Gestenhandler, die Eingabe</span><span class="sxs-lookup"><span data-stu-id="87bb3-137">Process gaze and gesture input</span></span>

<span data-ttu-id="87bb3-138">[Bestaunen](gaze-in-directx.md) und [Hand](hands-and-motion-controllers-in-directx.md) Eingabe sind nicht zeitbasierte und daher keine haben, aktualisieren Sie in der **StepTimer** Funktion.</span><span class="sxs-lookup"><span data-stu-id="87bb3-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="87bb3-139">Diese Eingabe ist jedoch etwas, das die app bei jedem Bild aussehen muss.</span><span class="sxs-lookup"><span data-stu-id="87bb3-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="87bb3-140">Verarbeiten eines zeitbasierten updates</span><span class="sxs-lookup"><span data-stu-id="87bb3-140">Process time-based updates</span></span>

<span data-ttu-id="87bb3-141">Alle Echtzeit-Rendering-Apps benötigen eine Möglichkeit zum Verarbeiten von zeitbasierten Updates; Wir bieten eine Möglichkeit dazu in der Vorlage für Windows Holographic app über eine **StepTimer** Implementierung.</span><span class="sxs-lookup"><span data-stu-id="87bb3-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="87bb3-142">Dies ähnelt der StepTimer, angegeben in die DirectX 11-UWP-app-Vorlage, also wenn Sie diese Vorlage bereits besprochen haben Sie auf vertraute Boden sein sollten.</span><span class="sxs-lookup"><span data-stu-id="87bb3-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="87bb3-143">Diese Hilfsklasse für StepTimer Beispiel kann fester Zeitschritt Updates sowie Variablen Zeitschritt Updates bereitstellen, und der Standardmodus ist Variablen Zeitschritten.</span><span class="sxs-lookup"><span data-stu-id="87bb3-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="87bb3-144">Im Fall von holographic Rendering, haben wir uns speziell entschieden, nicht zu viel in der Timer-Funktion zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="87bb3-145">Dies ist, da Sie können konfigurieren, um einen festen Schritt, in diesem Fall es möglicherweise mehr als einmal pro Frame – oder überhaupt nicht für einige Frames aufgerufen – und unsere holographic datenaktualisierungen einmal pro Frame auftreten sollte.</span><span class="sxs-lookup"><span data-stu-id="87bb3-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="87bb3-146">Von **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="87bb3-147">Position und drehen Hologramme in Ihre Koordinatensystem</span><span class="sxs-lookup"><span data-stu-id="87bb3-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="87bb3-148">Wenn Sie in einem einzelnen Koordinatensystem, arbeiten, wie die Vorlage mit der **SpatialStationaryReferenceFrame**, dieser Vorgang unterscheidet sich nicht von was Sie andernfalls werden verwendet, die bei 3D-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="87bb3-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="87bb3-149">Hier, wir drehen Sie den Cube, und legen Sie die modellmatrix relativ zur Position im Koordinatensystem eines stationären Zustands.</span><span class="sxs-lookup"><span data-stu-id="87bb3-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="87bb3-150">Von **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-150">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="87bb3-151">**Beachten Sie Informationen zu erweiterten Szenarien:** Der sich drehenden Würfels ist ein sehr einfaches Beispiel zum Positionieren Sie ggf. ein Hologramm innerhalb eines einzelnen Verweises.</span><span class="sxs-lookup"><span data-stu-id="87bb3-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="87bb3-152">Es ist auch möglich, [verwenden mehrere SpatialCoordinateSystems](coordinate-systems-in-directx.md) im gleichen gerenderte Frame, zur gleichen Zeit.</span><span class="sxs-lookup"><span data-stu-id="87bb3-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="87bb3-153">Konstantenpuffer Aktualisierungsdaten</span><span class="sxs-lookup"><span data-stu-id="87bb3-153">Update constant buffer data</span></span>

<span data-ttu-id="87bb3-154">Modell-Transformationen für Inhalte werden wie gewohnt aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="87bb3-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="87bb3-155">Nun werden Sie gültige Transformationen für das Koordinatensystem berechnet wurde, die, denen Sie bei der, Rendern werden müssen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="87bb3-156">Von **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-156">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="87bb3-157">Was ist mit der Ansichts- und Projektionstransformation Transformationen?</span><span class="sxs-lookup"><span data-stu-id="87bb3-157">What about view and projection transforms?</span></span> <span data-ttu-id="87bb3-158">Für optimale Ergebnisse sollten warten, bis wir fast fertig für unsere zeichnen, sind bevor wir diese eingehen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="87bb3-159">Den aktuellen Frame zu rendern</span><span class="sxs-lookup"><span data-stu-id="87bb3-159">Render the current frame</span></span>

<span data-ttu-id="87bb3-160">Rendern in Windows Mixed Reality unterscheidet sich nicht wesentlich vom Rendering in einer 2D-mono-Anzeige, aber es gibt einige Unterschiede, die, denen Sie berücksichtigen müssen:</span><span class="sxs-lookup"><span data-stu-id="87bb3-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="87bb3-161">Holographic Frame Vorhersagen sind wichtig.</span><span class="sxs-lookup"><span data-stu-id="87bb3-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="87bb3-162">Je näher die Vorhersage besteht darin, wenn Ihr Frame dargestellt wird, desto besser Ihre Hologramme sieht.</span><span class="sxs-lookup"><span data-stu-id="87bb3-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="87bb3-163">Windows Mixed Reality steuert die Kameraansichten.</span><span class="sxs-lookup"><span data-stu-id="87bb3-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="87bb3-164">Sie müssen in jeder gerendert werden soll, da der holographic Rahmen diese für Sie später noch Mal vorführen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="87bb3-165">Stereo-Rendern wird empfohlen, mithilfe von instanziierten Zeichnung auf ein Array der Render-Ziel erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="87bb3-166">Die holographic app-Vorlage verwendet, die empfohlene Vorgehensweise instanziierten Zeichnung in ein Array der Render-Ziel, die eine renderzielansicht auf verwendet eine **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="87bb3-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="87bb3-167">Wenn Sie ohne Verwendung von Stereo Instanziierung rendern möchten, müssen Sie zwei RenderTargetViews für nicht-Array (eine für jedes Auge) zu erstellen, die jeden Verweis eine der beiden in slices der **Texture2DArray** an die app aus dem System bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="87bb3-168">Dies wird nicht empfohlen, wie es in der Regel wesentlich langsamer als die Verwendung von Instanziierung ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="87bb3-169">Erhalten Sie eine aktualisierte HolographicFrame-Vorhersage</span><span class="sxs-lookup"><span data-stu-id="87bb3-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="87bb3-170">Aktualisieren die Frame-Vorhersage verbessert die Effektivität der Stabilisierung des Image, und ermöglicht genauere Positionierung von Hologramme aufgrund der kürzeren Zeit zwischen der Vorhersage und wenn der Frame für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="87bb3-171">Im Idealfall aktualisieren Sie Ihre Frame Vorhersage nur vor dem Rendern.</span><span class="sxs-lookup"><span data-stu-id="87bb3-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="87bb3-172">Für jede Kamera Rendern</span><span class="sxs-lookup"><span data-stu-id="87bb3-172">Render to each camera</span></span>

<span data-ttu-id="87bb3-173">Eine Schleife für den Satz von Kamera ist in die Vorhersage, und in jede Kamera in dieser Gruppe gerendert.</span><span class="sxs-lookup"><span data-stu-id="87bb3-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="87bb3-174">**Richten Sie Ihren Pass-rendering**</span><span class="sxs-lookup"><span data-stu-id="87bb3-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="87bb3-175">Windows Mixed Reality verwendet stereoskopische Rendering, um die Illusion von Tiefe zu verbessern und Gläsern, rendern, damit der linken und rechten Anzeige aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="87bb3-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="87bb3-176">Bei stereoskopische Rendering besteht eine Abweichung zwischen den zwei angezeigt, die vom Gehirn als tatsächliche Tiefe abstimmen kann.</span><span class="sxs-lookup"><span data-stu-id="87bb3-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="87bb3-177">Dieser Abschnitt behandelt stereoskopische Rendern über Instanziierung ist die Verwendung eines Codes über die Windows Holographic-app-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="87bb3-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="87bb3-178">Jede Kamera hat einen eigenen Render Ziel (Hintergrundpuffer), und die Ansichts- und Projektionstransformation Matrizen in der holografischen Speicherplatz.</span><span class="sxs-lookup"><span data-stu-id="87bb3-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="87bb3-179">Ihre app benötigt andere Kamera-basierte Ressourcen – z. B. Tiefenpuffer - auf einer pro-Kamera-Basis zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="87bb3-180">In der Windows Holographic-app-Vorlage bieten wir eine Hilfsklasse, um diese Ressourcen im DX::CameraResources bündeln.</span><span class="sxs-lookup"><span data-stu-id="87bb3-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="87bb3-181">Starten Sie, indem die renderzielansichten einrichten:</span><span class="sxs-lookup"><span data-stu-id="87bb3-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="87bb3-182">Von **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-182">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="87bb3-183">**Verwenden Sie die Vorhersage, um die Ansichts- und Projektionstransformation Matrizen für die Kamera zu erhalten.**</span><span class="sxs-lookup"><span data-stu-id="87bb3-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="87bb3-184">Die Ansichts- und Projektionstransformation Matrizen für jede holographic Kamera werden mit jedem Frame ändern.</span><span class="sxs-lookup"><span data-stu-id="87bb3-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="87bb3-185">Aktualisieren Sie die Daten in den Konstantenpuffer für jede holographic Kamera.</span><span class="sxs-lookup"><span data-stu-id="87bb3-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="87bb3-186">Dies tun, nachdem Sie die Vorhersage aktualisiert, und vor jedem Zeichnen für diese Kamera.</span><span class="sxs-lookup"><span data-stu-id="87bb3-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="87bb3-187">Von **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="87bb3-188">Hier wird erläutert, wie die Matrizen von der Kamera Haltung erworben werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="87bb3-189">Während dieses Vorgangs erhalten wir auch die aktuellen Viewport für die Kamera.</span><span class="sxs-lookup"><span data-stu-id="87bb3-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="87bb3-190">Beachten Sie, wie wir einem Koordinatensystem bereitstellen: Dies ist das gleiche Koordinatensystem, die wir verwendet, um die Blicke zu verstehen, und es ist die gleiche wir verwendet, um den sich drehenden Würfels zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="87bb3-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="87bb3-191">Von **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="87bb3-192">Der Viewport muss jeder Frame festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-192">The viewport should be set each frame.</span></span> <span data-ttu-id="87bb3-193">Der Vertex-Shader benötigen (mindestens) in der Regel Zugriff auf die Daten für die Ansichts-und Projektionsmatrix.</span><span class="sxs-lookup"><span data-stu-id="87bb3-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="87bb3-194">Von **CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="87bb3-195">**In den Hintergrundpuffer der Kamera gerendert, und committen Sie Tiefenpuffer**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="87bb3-196">Es ist eine gute Idee, die überprüft, ob **TryGetViewTransform** erfolgreich war, bevor Sie versuchen, die die Ansichts-und Projektionsmatrix-Daten verwenden, da ist das Koordinatensystem nicht gefunden werden (z. B. nachverfolgung wurde unterbrochen) Ihre app kann nicht mit gerendert werden, Frame.</span><span class="sxs-lookup"><span data-stu-id="87bb3-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="87bb3-197">Die Vorlage nur ruft **Rendern** auf den sich drehenden Würfels Wenn die **CameraResources** -Ereignisklasse zeigt an, ein erfolgreiches Update.</span><span class="sxs-lookup"><span data-stu-id="87bb3-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="87bb3-198">Um Hologramme zu halten, in denen schreibt ein Entwickler oder Benutzer sie in der ganzen Welt, bietet Windows Mixed Reality Features für [image Stabilisierung](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="87bb3-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="87bb3-199">Image Stabilisierung ist hilfreich, die Wartezeit, die sich eine Rendering-Pipeline, um sicherzustellen, dass die am besten holographic Benutzeroberflächen für Benutzer auszublenden. ein Fokuspunkt kann angegeben werden, um Image Stabilisierung noch weiter zu verbessern, oder ein Tiefenpuffer kann angegeben werden, um berechnen Image Stabilisierung in Echtzeit optimiert.</span><span class="sxs-lookup"><span data-stu-id="87bb3-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="87bb3-200">Für optimale Ergebnisse sollten Ihre app bereitstellen, eine Tiefe Puffer mithilfe der <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span><span class="sxs-lookup"><span data-stu-id="87bb3-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="87bb3-201">Windows Mixed Reality Geometrieinformationen können Sie dann aus der Tiefenpuffer Image Stabilisierung in Echtzeit zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="87bb3-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="87bb3-202">Die Windows Holographic-app-Vorlage führt einen Commit für die app Tiefenpuffer standardmäßig unterstützen – Hologramm Stabilität zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="87bb3-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="87bb3-203">Von **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-203">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="87bb3-204">Windows verarbeitet Ihre Tiefe Textur auf der GPU, sodass es möglich, Ihre Tiefenpuffer als Shaderressource zu verwenden sein muss.</span><span class="sxs-lookup"><span data-stu-id="87bb3-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="87bb3-205">Die ID3D11Texture2D, die Sie erstellen sollte in einem Format typenlos und es als Shaderressource gebunden werden soll.</span><span class="sxs-lookup"><span data-stu-id="87bb3-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="87bb3-206">Hier ist ein Beispiel dafür, wie eine Textur Tiefe zu erstellen, die für die Stabilisierung des Image ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="87bb3-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="87bb3-207">Code für **Tiefe Puffer ressourcenerstellung für CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="87bb3-208">**Zeichnen Sie holographic Inhalt**</span><span class="sxs-lookup"><span data-stu-id="87bb3-208">**Draw holographic content**</span></span>

<span data-ttu-id="87bb3-209">Die Windows Holographic-app-Vorlage rendert Inhalt in Stereo mit das empfohlene Verfahren ein Texture2DArray von der Größe 2 instanziierten Geometrie gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="87bb3-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="87bb3-210">Sehen wir uns auf die Instanziierung Teil dies und deren Funktionsweise in Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="87bb3-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="87bb3-211">Von **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-211">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="87bb3-212">Jede Instanz greift auf eine andere Ansicht/Projektionsmatrix aus den Konstantenpuffer zu.</span><span class="sxs-lookup"><span data-stu-id="87bb3-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="87bb3-213">Hier ist die Konstantenpuffer-Struktur, die nur ein Array von 2-Matrizen ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="87bb3-214">Von **VertexShaderShared.hlsl**, eingeschlossen durch **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="87bb3-215">Der Arrayindex der Render-Ziel muss für jedes Pixel festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="87bb3-216">Im folgenden Codeausschnitt output.viewId zugeordnet ist die **SV_RenderTargetArrayIndex** semantische.</span><span class="sxs-lookup"><span data-stu-id="87bb3-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="87bb3-217">Beachten Sie, dass diese Unterstützung für eine optionale Direct3D 11.3-Funktion, dem den Arrayindex der Render-Ziel semantische aus shaderstufe festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="87bb3-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="87bb3-218">From **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-218">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="87bb3-219">Von **VertexShaderShared.hlsl**, eingeschlossen durch **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="87bb3-220">Wenn Sie Ihre vorhandene Instanz verwenden möchten zeichnen Techniken mit dieser Methode der Zeichnung auf ein Stereo Rendern Zielarrays begonnen wird alles, was man dazu Unternehmen muss zweimal die Anzahl der Instanzen, die in der Regel keine zeichnen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="87bb3-221">In den Shader, teilen **input.instId** durch 2, um die ursprüngliche Instanz-ID zu erhalten, die in (z. B.) auf einen Puffer von pro-Objekt Daten indiziert werden kann: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="87bb3-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="87bb3-222">Wichtiger Hinweis zum Rendern von Stereo Inhalt für HoloLens</span><span class="sxs-lookup"><span data-stu-id="87bb3-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="87bb3-223">Windows Mixed Reality unterstützt die Möglichkeit, die den Arrayindex der Render-Ziel über shaderstufe festgelegt. Normalerweise ist dies eine Aufgabe, die nur in der Geometrie-Shader-Stufe aufgrund der Art, durchgeführt werden konnte, die die Semantik für Direct3D 11 definiert ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="87bb3-224">Hier zeigen wir ein vollständiges Beispiel dafür, wie eine renderingpipeline mit den Scheitelpunkt und den Pixel-Shader Phasen Satz einrichten.</span><span class="sxs-lookup"><span data-stu-id="87bb3-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="87bb3-225">Der Shader-Code wird wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="87bb3-225">The shader code is as described above.</span></span>

<span data-ttu-id="87bb3-226">Von **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-226">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="87bb3-227">Wichtiger Hinweis zum Rendern auf nicht-HoloLens-Geräte</span><span class="sxs-lookup"><span data-stu-id="87bb3-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="87bb3-228">Zum Festlegen des Arrayindex der Render-Ziel in der Vertex-Shader muss der Grafiktreiber eine optionale Direct3D 11.3-Funktion unterstützt die HoloLens unterstützen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="87bb3-229">Ihre app möglicherweise nur diese Methode für das Rendering sicher zu implementieren, und für die Ausführung auf der Microsoft HoloLens werden alle Anforderungen erfüllt werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="87bb3-230">Es kann der Fall sein, den Sie ebenfalls die HoloLens-Emulator verwenden möchten die kann eine leistungsstarke Entwicklungstool für Ihre holographic-app - und unterstützen Windows Mixed Reality immersive Kopfhörer-Geräte, die mit Windows 10-PCs verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="87bb3-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="87bb3-231">Unterstützung für den nicht-HoloLens-Rendering-Pfad - und daher für alle Windows Mixed Reality - ist auch in die Windows Holographic-app-Vorlage integriert.</span><span class="sxs-lookup"><span data-stu-id="87bb3-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="87bb3-232">Im Vorlagencode finden Sie Code für Ihre Anwendung holographic auf der GPU in Ihrem Entwicklungs-PC ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="87bb3-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="87bb3-233">Hier ist die **DeviceResources** -Klasse sucht diese optionales Feature-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="87bb3-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="87bb3-234">Von **DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="87bb3-235">Um rendern, ohne diese optionale Funktion zu unterstützen, muss Ihre app einen Geometrie-Shader verwenden, den Arrayindex der Render-Ziel festlegen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="87bb3-236">Dieser Codeausschnitt hinzugefügt *nach* **VSSetConstantBuffers**, und *vor* **PSSetShader** im Codebeispiel wird gezeigt, in der vorherigen Abschnitt für das Rendern von Stereo für HoloLens erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="87bb3-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="87bb3-237">Von **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-237">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="87bb3-238">**BEACHTEN SIE HLSL**: In diesem Fall müssen Sie auch einen leicht abgeänderte Vertex-Shader laden, der den Arrayindex der Render-Ziel an die Geometrie-Shader verwenden eine semantische, z. B. TEXCOORD0 immer zulässig Shaders übergibt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="87bb3-239">Geometrie-Shader keine Schritte erforderlich; die Vorlage Geometrie-Shader durchläuft alle Daten, mit Ausnahme von Render Zielindex des Arrays, die verwendet wird, die SV_RenderTargetArrayIndex semantische festlegen ab.</span><span class="sxs-lookup"><span data-stu-id="87bb3-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="87bb3-240">App-Vorlagencode für **GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-240">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="87bb3-241">Darstellen</span><span class="sxs-lookup"><span data-stu-id="87bb3-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="87bb3-242">Aktivieren Sie den holographic Frame die SwapChain vorhanden</span><span class="sxs-lookup"><span data-stu-id="87bb3-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="87bb3-243">Mit Windows Mixed Reality steuert das System die SwapChain.</span><span class="sxs-lookup"><span data-stu-id="87bb3-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="87bb3-244">Das System verwaltet dann in jede Kamera holographic, um sicherzustellen, dass eine qualitativ hochwertige benutzererfahrung Präsentation vorführen Frames.</span><span class="sxs-lookup"><span data-stu-id="87bb3-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="87bb3-245">Darüber hinaus ein Update des Viewports jeden Frame für jede Kamera, um Aspekte des Systems wie z. B. Image Stabilisierung oder Mixed Reality erfassen zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="87bb3-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="87bb3-246">Also eine holographic-app mit DirectX Aufrufen nicht **vorhanden** auf eine DXGI Kette austauschen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="87bb3-247">Verwenden Sie stattdessen die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> Klasse, um alle Sie swapchains hervor für einen Frame vorhanden, wenn Sie fertig sind gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="87bb3-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="87bb3-248">Von **DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="87bb3-249">Standardmäßig wartet diese API für den Rahmen um den Vorgang abzuschließen, bevor sie zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="87bb3-250">Holographic apps sollten warten, für den vorherigen Frame abgeschlossen ist, bevor Sie mit der Arbeit beginnen auf einen neuen Frame, da dies verringert die Latenz und eine bessere Ergebnisse holographic Frame Vorhersagen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="87bb3-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="87bb3-251">Dies ist eine feste Regel nicht, und wenn man Frames, die länger als einen Bildschirm Aktualisierung durch dauern, um Sie rendern deaktivieren, diese Wartezeit durch Übergeben des Parameters HolographicFramePresentWaitBehavior zu <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="87bb3-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="87bb3-252">Sie würden in diesem Fall wahrscheinlich einen asynchrones Rendering-Thread verwenden, um einer fortlaufenden Last auf dem GPU zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="87bb3-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="87bb3-253">Beachten Sie, dass die Häufigkeit der Aktualisierung des Geräts HoloLens 60 hz ist, in dem Frame eine Dauer von ca. 16 ms.</span><span class="sxs-lookup"><span data-stu-id="87bb3-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="87bb3-254">Immersive Kopfhörer Geräten reichen von 60 hz bis 90 hz; Wenn Sie die Anzeige bei 90 hz aktualisieren zu können, müssen alle Frames eine Dauer von etwa 11 ms.</span><span class="sxs-lookup"><span data-stu-id="87bb3-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="87bb3-255">In Zusammenarbeit mit der HolographicFrame DeviceLost Szenarien</span><span class="sxs-lookup"><span data-stu-id="87bb3-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="87bb3-256">DirectX 11-apps sollten in der Regel überprüfen Sie der DXGI-SwapChain zurückgegebene HRESULT **vorhanden** Funktion, um herauszufinden, ob es wurde eine **DeviceLost** Fehler.</span><span class="sxs-lookup"><span data-stu-id="87bb3-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="87bb3-257">Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> Klasse übernimmt dies für Sie.</span><span class="sxs-lookup"><span data-stu-id="87bb3-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="87bb3-258">Überprüfen Sie die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> wird zurückgegeben, um herauszufinden, ob müssen Sie Version und der Direct3D-Gerät und mithilfe von gerätebasierten Ressourcen neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="87bb3-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="87bb3-259">Beachten Sie, dass wenn das Direct3D-Gerät unterbrochen wurde, und Sie es neu erstellen, Sie müssen die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> beim Einstieg in das neue Gerät.</span><span class="sxs-lookup"><span data-stu-id="87bb3-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="87bb3-260">Die SwapChain wird für dieses Gerät neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="87bb3-261">Von **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="87bb3-262">Wenn Ihr Frame dargestellt wird, können Sie an die Schleife Hauptprogramm zurückgegeben und erlauben, dass bis zum nächsten Frame zu.</span><span class="sxs-lookup"><span data-stu-id="87bb3-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="87bb3-263">Hybrid-Grafik-PCs und mixed Reality-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="87bb3-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="87bb3-264">Windows 10 Creators Update PCs können so konfiguriert werden, mit **sowohl** diskreter als auch integrierten GPUs.</span><span class="sxs-lookup"><span data-stu-id="87bb3-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="87bb3-265">Mit diesen Typen von Computern wählt Windows den Adapter, die, dem an den Kopfhörer angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="87bb3-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="87bb3-266">Anwendungen müssen stellen Sie sicher, dass das DirectX-Gerät erstellten den gleichen Adapter verwendet.</span><span class="sxs-lookup"><span data-stu-id="87bb3-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="87bb3-267">Die meisten allgemeinen Direct3D-Beispielcode veranschaulicht das Erstellen einer DirectX-Gerät mit den Standardadapter für die Hardware, der auf einem hybridsystem nicht identisch mit der für den Kopfhörer verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="87bb3-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="87bb3-268">Verwenden Sie zur Umgehung Probleme dadurch möglicherweise die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> entweder <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() oder <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId().</span><span class="sxs-lookup"><span data-stu-id="87bb3-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="87bb3-269">Diese "AdapterId" kann dann verwendet werden, Auswahl der richtigen DXGIAdapter IDXGIFactory4.EnumAdapterByLuid verwenden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="87bb3-270">Von **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="87bb3-271">Um den Code **DeviceResources::CreateDeviceResources Verwendung IDXGIAdapter aktualisieren**</span><span class="sxs-lookup"><span data-stu-id="87bb3-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="87bb3-272">**Hybrid-Grafiken und Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="87bb3-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="87bb3-273">Mit Media Foundation in Hybriden Systemen kann verursachen, in dem Video wird nicht gerendert oder video-Textur ist beschädigt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="87bb3-274">Dies kann auftreten, da Media Foundation, um ein Systemverhalten Standardwert ist wie oben erwähnt.</span><span class="sxs-lookup"><span data-stu-id="87bb3-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="87bb3-275">In einigen Szenarien ist es erforderlich, Unterstützung von Multithreading und das richtige erstellen, die Flags festgelegt sind, erstellen eine separate ID3D11Device.</span><span class="sxs-lookup"><span data-stu-id="87bb3-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="87bb3-276">Wenn die ID3D11Device initialisiert wird, muss D3D11_CREATE_DEVICE_VIDEO_SUPPORT-Flag im Rahmen der D3D11_CREATE_DEVICE_FLAG definiert werden.</span><span class="sxs-lookup"><span data-stu-id="87bb3-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="87bb3-277">Rufen Sie nach dem Gerät und dem Kontext erstellt wird, <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> zu multithreading.</span><span class="sxs-lookup"><span data-stu-id="87bb3-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="87bb3-278">Zuordnen des Geräts mit der <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, verwenden Sie die <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> Funktion.</span><span class="sxs-lookup"><span data-stu-id="87bb3-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="87bb3-279">Um den Code **ordnen Sie einem ID3D11Device IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="87bb3-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="87bb3-280">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="87bb3-280">See also</span></span>
* [<span data-ttu-id="87bb3-281">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="87bb3-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="87bb3-282">Verwendung des HoloLens Emulators</span><span class="sxs-lookup"><span data-stu-id="87bb3-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
