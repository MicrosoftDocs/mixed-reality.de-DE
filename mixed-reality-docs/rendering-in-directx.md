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
# <a name="rendering-in-directx"></a>Rendering in DirectX

Windows Mixed Reality basiert auf DirectX, um für Benutzer eine umfassende, grafische Darstellung von 3D-Funktionen zu erstellen. Die renderingabstraktion befindet sich direkt oberhalb von DirectX und ermöglicht einer APP einen Grund zur Position und Ausrichtung von einem oder mehreren Beobachtern einer Holographic-Szene, die vom System vorhergesagt wurde. Der Entwickler kann dann seine Hologramme in Relation zu den einzelnen Kameras finden, sodass die APP diese Hologramme in verschiedenen räumlichen Koordinatensystemen gereinigen kann, wenn der Benutzer sich bewegt.

Hinweis: in dieser exemplarischen Vorgehensweise wird das Holographic-Rendering in Direct3D 11 beschrieben. Eine Direct3D 12-Windows Mixed Reality-App-Vorlage wird auch mit der Erweiterung "Mixed Reality App Templates" bereitgestellt.

## <a name="update-for-the-current-frame"></a>Update für den aktuellen Frame

Um den Anwendungs Zustand für holograms zu aktualisieren, führt die APP einmal pro Frame folgende Aktionen aus:
* Verschaffen Sie sich einen <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> aus dem Anzeige Verwaltungssystem.
* Aktualisieren Sie die Szene mit der aktuellen Vorhersage, bei der die Kameraansicht angezeigt wird, wenn das Rendering abgeschlossen ist. Beachten Sie, dass für die Holographic-Szene mehr als eine Kamera vorhanden sein kann.

Zum Rendering in Holographic Camera-Ansichten führt die APP einmal pro Frame folgende Aktionen aus:
* Rendering Sie für jede Kamera die Szene für den aktuellen Frame, indem Sie die Kameraansicht und Projektions Matrizen aus dem System verwenden.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Erstellen Sie einen neuen Holographic Frame, und rufen Sie seine Vorhersage ab

Der <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> enthält Informationen, die die APP benötigt, um den aktuellen Frame zu aktualisieren und zu Rendering. Die APP startet jeden neuen Frame durch Aufrufen der **createnextframe** -Methode. Wenn diese Methode aufgerufen wird, werden Vorhersagen mit den neuesten verfügbaren Sensordaten erstellt und im **currentvorhersage** -Objekt gekapselt.

Für jeden gerenderten Frame muss ein neues Frame Objekt verwendet werden, da es nur für einen Zeitpunkt gültig ist. Die **currentvorhersage** -Eigenschaft enthält Informationen, wie z. b. die Kameraposition. Die Informationen werden auf den genauen Zeitpunkt hochgerechnet, zu dem der Frame erwartungsgemäß für den Benutzer sichtbar ist.

Der folgende Code wird aus **appmain:: Update**entnommen:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Verarbeiten von Kamera Updates

Backpuffer können von Frame zu Frame geändert werden. Ihre APP muss den Hintergrund Puffer für jede Kamera validieren und Ressourcen Sichten und tiefen Puffer nach Bedarf freigeben und neu erstellen. Beachten Sie, dass der Satz von Posen in der Vorhersage die autoritative Liste der Kameras ist, die im aktuellen Frame verwendet werden. Normalerweise verwenden Sie diese Liste, um den Satz von Kameras zu durchlaufen.

Aus **appmain:: Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Aus **deviceresources:: ensurecameraresources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Das Koordinatensystem zur Verwendung als Grundlage für das Rendering erhalten

Windows Mixed Reality ermöglicht der APP, bei Bedarf verschiedene [Koordinatensysteme](coordinate-systems-in-directx.md) zu erstellen, wie z. b. den angefügten Verweis Rahmen und den stationären Referenzrahmen, der Standorte in der physischen Welt nachverfolgt. Diese Koordinatensysteme können von Ihrer APP dann verwendet werden, um zu verdeutlichen, wo die einzelnen Frames von holograms dargestellt werden. Wenn Sie Koordinaten über eine API anfordern, übergeben Sie immer das <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">spatialcoordinatesystem</a> , in dem Sie die Koordinaten ausdrücken möchten.

Aus **appmain:: Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Diese Koordinatensysteme können dann zum Generieren von Stereo Ansichts Matrizen verwendet werden, wenn der Inhalt in der Szene gerendert wird.

Aus **cameraresources:: updateviewprojectionbuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Verarbeiten von Blick und Gesten Eingaben

Die Zeiger-und [Hand](hands-and-motion-controllers-in-directx.md) Eingaben sind nicht Zeit basiert und müssen daher nicht in der **Steptimer** [-Funktion](gaze-in-directx.md) aktualisiert werden. Diese Eingabe muss jedoch in den einzelnen Frames angezeigt werden.

### <a name="process-time-based-updates"></a>Zeitbasierte Updates verarbeiten

Jede Echtzeit-renderinganwendung benötigt eine Möglichkeit zum Verarbeiten zeitbasierter Updates. Wir bieten eine Möglichkeit, dies in der Windows Holographic-App-Vorlage über eine **Step Timer** -Implementierung umzusetzen. Dies ähnelt dem in der APP-Vorlage DirectX 11-UWP bereitgestellten Steptimer. Wenn Sie sich also bereits diese Vorlage angesehen haben, sollten Sie sich auf dem Weg zu einem vertrauten Grund befinden. Diese Beispiel-Hilfsklasse von Steptimer kann festgelegte Zeit Schritt Updates sowie Variable Zeit Schritt Updates bereitstellen, und der Standardmodus ist Variable Zeit Schritte.

Im Fall von Holographic Rendering haben wir ausdrücklich entschieden, nicht zu viel in die Timer-Funktion zu versetzen. Dies liegt daran, dass Sie ihn als einen festgelegten Zeit Schritt konfigurieren können. in diesem Fall wird er möglicherweise mehrmals pro Frame – oder gar nicht bei manchen Frames aufgerufen – und unsere Holographic-Datenaktualisierungen sollten einmal pro Frame erfolgen.


Aus **appmain:: Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Positionieren und Drehen von holograms im Koordinatensystem

Wenn Sie in einem einzelnen Koordinatensystem arbeiten, wie die Vorlage mit **spatialstationaryreferenceframe**funktioniert, unterscheidet sich dieser Vorgang nicht von dem, was Sie anderweitig in 3D-Grafiken verwendet haben. Hier drehen wir den Cube und legen die Modell Matrix relativ zur Position im stationären Koordinatensystem fest.

Von **spinningcuberenderer:: Update**:

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

**Hinweis zu erweiterten Szenarien:** Der spincube ist ein sehr einfaches Beispiel dafür, wie ein – Hologramm innerhalb eines einzelnen Referenzrahmens positioniert werden kann. Es ist auch möglich, [mehrere spatialcoordinatesystems](coordinate-systems-in-directx.md) gleichzeitig im gleichen gerenderten Frame zu verwenden.

### <a name="update-constant-buffer-data"></a>Aktualisieren konstanter Puffer Daten

Modell Transformationen für Inhalt werden wie gewohnt aktualisiert. Jetzt verfügen Sie über die gültigen Transformationen für das Koordinatensystem, in dem Sie das Rendering durchführt.

Von **spinningcuberenderer:: Update**:

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

Wie sieht es mit Ansichts-und Projektions Transformationen aus? Um optimale Ergebnisse zu erzielen, möchten wir warten, bis wir fast bereit für unsere Draw-Aufrufe sind, bevor wir diese erhalten.

## <a name="render-the-current-frame"></a>Aktuellen Frame Rendering

Das Rendering in Windows Mixed Reality unterscheidet sich nicht wesentlich vom Rendering in einer 2D-Mono-Anzeige, es gibt jedoch einige Unterschiede, die Sie kennen müssen:
* Holographic-Frame Vorhersagen sind wichtig. Je näher die Vorhersage ist, wenn Ihr Frame dargestellt wird, desto besser werden die Hologramme aussehen.
* Windows Mixed Reality steuert die Kameraansichten. Sie müssen jedes Rendering durchzuführen, da der Holographic-Frame Sie später für Sie darstellt.
* Es wird empfohlen, das Stereo Rendering mithilfe der instanzierten Zeichnung in ein renderzielarray zu erreichen. In der Holographic-App-Vorlage wird die empfohlene Vorgehensweise für das Zeichnen in ein renderzielarray verwendet, das eine renderzielansicht in einem **Texture2DArray**verwendet.
* Wenn Sie ohne Stereo-Instanziierung Renderingvorgang durchführen möchten, müssen Sie zwei nicht-Array-rendertargetviews (einen für jedes Auge) erstellen, die jeweils auf einen der beiden Slices in der **Texture2DArray** verweisen, die für die APP aus dem System bereitgestellt werden. Dies wird nicht empfohlen, da es in der Regel deutlich langsamer als die Verwendung der Instanziierung ist.

### <a name="get-an-updated-holographicframe-prediction"></a>Holen Sie sich eine aktualisierte holographicframe-Vorhersage

Durch das Aktualisieren der Frame Vorhersage wird die Effektivität der Bildstabilisierung erhöht und eine genauere Positionierung von holograms aufgrund der kürzeren Zeit zwischen der Vorhersage und der Sichtbarkeit des Frames für den Benutzer ermöglicht. Aktualisieren Sie Ihre Frame Vorhersage idealerweise direkt vor dem Rendering.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>An jede Kamera Rendering

Schleife für den Satz von Kamera stellt in der Vorhersage dar und renderauf jeder Kamera in diesem Satz.

**Einrichten Ihres Renderings**

Windows Mixed Reality verwendet das stereorenderingrendering, um die Illusion von Tiefe zu verbessern und die stereoscopiisch zu rendern, sodass sowohl die linke als auch die Rechte Anzeige aktiv ist. Beim stereorenderingrendering gibt es einen Offset zwischen den beiden anzeigen, der vom Gehirn als tatsächliche Tiefe abgeglichen werden kann. In diesem Abschnitt wird das stereoserienrendering mithilfe der Instanziierung mithilfe von Code aus der Windows Holographic App-Vorlage behandelt.

Jede Kamera verfügt über ein eigenes Renderziel (BackBuffer) und Ansichts-und Projektions Matrizen in den Holographic-Raum. Ihre APP muss alle anderen kamerabasierten Ressourcen erstellen, z. b. den tiefen Puffer pro Kamera. In der Windows Holographic-App-Vorlage stellen wir eine Hilfsklasse bereit, um diese Ressourcen zusammen in DX:: cameraresources zu bündeln. Beginnen Sie, indem Sie die renderzielsichten einrichten:

Aus **appmain:: Rendering**:

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

**Verwenden der Vorhersage, um die Ansichts-und Projektions Matrizen für die Kamera zu erhalten**

Die Ansichts-und Projektions Matrizen für jede holografische Kamera werden bei jedem Frame geändert. Aktualisieren Sie die Daten im Konstanten Puffer für jede holografische Kamera. Führen Sie diese Schritte aus, nachdem Sie die Vorhersage aktualisiert haben und bevor Sie für diese Kamera Draw-Aufrufe durchführen.

Aus **appmain:: Rendering**:

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

Hier wird gezeigt, wie die Matrizen von der Kamera bezogen werden. Während dieses Vorgangs wird auch der aktuelle Viewport für die Kamera abgerufen. Beachten Sie, wie wir ein Koordinatensystem bereitstellen: Dies ist das gleiche Koordinatensystem, das wir zum Verständnis des Blicks verwendet haben. es ist dasselbe Koordinatensystem, das wir zum Positionieren des drehenden Cubes verwendet haben.


Aus **cameraresources:: updateviewprojectionbuffer**:

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

Der Viewport sollte jeden Frame festlegen. Der Vertex-Shader (zumindest) benötigt in der Regel Zugriff auf die Ansichts-/Projektionsdaten.


Aus **cameraresources:: attachviewprojectionbuffer**:

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

**Renderer in den Kamera-Hintergrund Puffer und Commit für den tiefen Puffer**aus:

Es empfiehlt sich, zu überprüfen, ob **trygetviewtransform** erfolgreich war, bevor versucht wird, die Ansichts-/Projektionsdaten zu verwenden, denn wenn das Koordinatensystem nicht erstellbar ist (z. b. wenn die Überwachung unterbrochen wurde), kann Ihre APP nicht mit ihr für diesen Frame bieten Die Vorlage ruft " **Rendering** " nur für den drehenden Cube auf, wenn die **cameraresources** -Klasse ein erfolgreiches Update angibt.

Um holograms beizubehalten, in denen ein Entwickler oder Benutzer Sie in der Welt platziert, umfasst Windows Mixed Reality Features für die [Bildstabilisierung](hologram-stability.md). Die Bildstabilisierung hilft dabei, die in einer Renderingpipeline enthaltene Latenz zu verbergen, um den Benutzern die beste holografische Umgebung zu bieten. Es kann ein Fokuspunkt angegeben werden, um die Bildstabilisierung noch weiter zu verbessern, oder es kann ein tiefen Puffer bereitgestellt werden, um die optimierte Bildstabilisierung in Echtzeit zu berechnen.

Um optimale Ergebnisse zu erzielen, sollte Ihre APP einen tiefen Puffer mithilfe der <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> -API bereitstellen. Die gemischte Realität von Windows kann dann Geometrie Informationen aus dem tiefen Puffer verwenden, um die Bildstabilisierung in Echtzeit zu optimieren. Die Vorlage für die Windows Holographic-App führt standardmäßig einen Commit für den tiefen Puffer der app durch

Aus **appmain:: Rendering**:

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
>Windows verarbeitet Ihre tiefe Textur auf der GPU, daher muss es möglich sein, den tiefen Puffer als Shaderressource zu verwenden. Der ID3D11Texture2D, den Sie erstellen, sollte ein typloses Format aufweisen und als Shader-Ressourcen Ansicht gebunden werden. Im folgenden finden Sie ein Beispiel für das Erstellen einer tiefen Textur, die für die Bildstabilisierung committet werden kann.

Code für die **Erstellung von tiefen Puffer Ressourcen für CommitDirect3D11DepthBuffer**:

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

**Holographic-Inhalt zeichnen**

Die Vorlage für die Windows Holographic-App rendert Inhalte in Stereo mithilfe der empfohlenen Vorgehensweise zum Zeichnen der instanziierten Geometrie in eine Texture2DArray der Größe 2. Sehen wir uns den Teil der Instanziierung an und erläutert, wie er in Windows Mixed Reality funktioniert.

Von **spinningcuberenderer:: Rendering**:

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

Jede Instanz greift auf eine andere Ansicht/Projektions Matrix aus dem Konstanten Puffer zu. Hier ist die Konstante Puffer Struktur, bei der es sich lediglich um ein Array von 2 Matrizen handelt.

Aus " **vertexshadershared. HLSL**", enthalten in " **vprtvertexshader. HLSL**":

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Der Array Index des Renderziels muss für jedes Pixel festgelegt werden. Im folgenden Code Ausschnitt wird "Output. viewId" der **SV_RenderTargetArrayIndex** Semantik zugeordnet. Beachten Sie, dass hierfür eine optionale Direct3D 11,3-Funktion unterstützt wird, mit der die Semantik des Renderziel-Array Indexes aus jeder Shader-Stufe festgelegt werden kann.

Aus **vprtvertexshader. HLSL**:

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

Aus " **vertexshadershared. HLSL**", enthalten in " **vprtvertexshader. HLSL**":

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

Wenn Sie Ihre vorhandenen instanziierten Zeichentechniken mit dieser Methode zum Zeichnen in ein Array von Stereo Renderziel verwenden möchten, müssen Sie lediglich die doppelte Anzahl von Instanzen zeichnen, die Sie normalerweise haben. Dividieren Sie im Shader **Input. instId** durch 2, um die ursprüngliche Instanz-ID zu erhalten, die in (z. b.) einen Puffer von objektbezogenen Daten indiziert werden kann: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Wichtiger Hinweis zum Rendern von Stereo Inhalten in hololens

Windows Mixed Reality unterstützt die Möglichkeit, den Renderziel-Array Index aus beliebigen Shader-Stufen festzulegen. Normalerweise handelt es sich hierbei um eine Aufgabe, die nur in der Geometry-Shader-Phase durchgeführt werden kann, weil die Semantik für Direct3D 11 definiert ist. Hier finden Sie ein umfassendes Beispiel für das Einrichten einer Renderingpipeline, in der nur die Vertex-und Pixel-Shader-Stufen festgelegt sind. Der Shader-Code ist wie oben beschrieben.

Von **spinningcuberenderer:: Rendering**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Wichtiger Hinweis zum Rendern auf nicht hololens-Geräten

Wenn Sie den renderzielarray-Index im Vertexshader festlegen, muss der Grafiktreiber ein optionales Direct3D 11,3-Feature unterstützen, das hololens unterstützt. Ihre APP ist möglicherweise in der Lage, nur diese Methode für das Rendering sicher zu implementieren, und alle Anforderungen werden für die Ausführung auf den Microsoft hololens erfüllt.

Möglicherweise möchten Sie auch den hololens-Emulator verwenden, der ein leistungsfähiges Entwicklungs Tool für Ihre Holographic APP sein kann und Windows Mixed Reality-immersive Headset-Geräte unterstützen, die an Windows 10-PCs angeschlossen sind. Unterstützung für den nicht hololens-Renderingpfad (und somit für alle Windows Mixed Reality) ist auch in der Windows Holographic-App-Vorlage integriert. Im Vorlagen Code finden Sie Code, mit dem Ihre Holographic-App auf der GPU auf dem Entwicklungs-PC ausgeführt werden kann. Im folgenden wird erläutert, wie die **deviceresources** -Klasse diese optionale Funktions Unterstützung prüft.

Aus **deviceresources:: kreatedeviceresources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Um das Rendering ohne diese optionale Funktion zu unterstützen, muss Ihre APP einen Geometry-Shader verwenden, um den Renderziel-Array Index festzulegen. Dieser Code Ausschnitt wird *nach* **vssetconstantbuffers**und *vor* **pssetshader** im Codebeispiel im vorherigen Abschnitt hinzugefügt, in dem erläutert wird, wie Stereo in hololens dargestellt wird.

Von **spinningcuberenderer:: Rendering**:

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

**HLSL-Hinweis**: in diesem Fall müssen Sie auch einen leicht geänderten Vertexshader laden, der den renderzielarray-Index an den Geometry-Shader übergibt, indem er eine immer zulässige Shader-Semantik verwendet, z. b. TEXCOORD0. Der Geometry-Shader muss keine Arbeit erledigen. der Vorlagen Geometrie-Shader durchläuft alle Daten, mit Ausnahme des Renderziel-Array Indexes, der zum Festlegen der SV_RenderTargetArrayIndex Semantik verwendet wird.

App-Vorlagen Code für **geometryshader. HLSL**:

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

## <a name="present"></a>Darstellen

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Aktivieren des Holographic Frame zum Darstellen der SwapChain

Mit Windows Mixed Reality steuert das System die Swapkette. Das System verwaltet dann Frames für jede holografische Kamera, um eine hohe Qualität zu gewährleisten. Außerdem bietet es eine Viewport-Aktualisierung jedes Frames für jede Kamera, um die Aspekte des Systems zu optimieren, wie z. b. die Bildstabilisierung oder die Transformation für gemischte Realität. Eine Holographic-APP, die DirectX verwendet, **ruft daher** nicht in einer DXGI-SwapChain auf. Stattdessen verwenden Sie die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> -Klasse, um alle SwapChain für einen Frame darzustellen, sobald Sie das Zeichnen abgeschlossen haben.

Aus **deviceresources::P erneut gesendet**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Standardmäßig wartet diese API, bis der Frame abgeschlossen ist, bevor Sie zurückkehrt. Holographic apps sollten warten, bis der vorherige Frame abgeschlossen ist, bevor die Arbeit an einem neuen Frame gestartet wird, da dadurch die Latenzzeit reduziert wird und bessere Ergebnisse aus Holographic Frame-Vorhersagen erzielt werden können. Dies ist keine harte Regel, und wenn Sie über Frames verfügen, die mehr als eine Bildschirm Aktualisierung zum Renderingvorgang benötigen, können Sie diesen warte Vorgang deaktivieren, indem Sie den holographicframepresentwaitbehavior-Parameter an <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">presentusingcurrentvorhersage</a>übergeben. In diesem Fall würden Sie wahrscheinlich einen asynchronen Renderingthread verwenden, um eine fortlaufende Last auf der GPU aufrechtzuerhalten. Beachten Sie, dass die Aktualisierungsrate des hololens-Geräts 60Hz beträgt, wobei ein Frame eine Dauer von ungefähr 16 MS hat. Immersive Headset-Geräte können zwischen 60Hz und 90Hz reichen. beim Aktualisieren der Anzeige bei 90 Hz erhält jeder Frame eine Dauer von ungefähr 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Behandeln von DeviceLost-Szenarien in Zusammenarbeit mit holographicframe

DirectX 11-apps müssten in der Regel das von der **Present** -Funktion der DXGI-SwapChain zurückgegebene HRESULT überprüfen, um herauszufinden, ob ein **DeviceLost** -Fehler aufgetreten ist. Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> -Klasse übernimmt diese für Sie. Überprüfen Sie das <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">holographicframepresentresult</a> , das zurückgegeben wird, um herauszufinden, ob Sie das Direct3D-Gerät und Geräte basierte Ressourcen freigeben und neu erstellen müssen.

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

Beachten Sie Folgendes: Wenn das Direct3D-Gerät verloren gegangen ist und Sie es neu erstellt haben, müssen Sie den <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a> anweisen, das neue Gerät zu verwenden. Die Swapkette wird für dieses Gerät neu erstellt.

Aus **deviceresources:: initializeusingholographicspace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Sobald Ihr Frame angezeigt wird, können Sie zur Hauptprogramm Schleife zurückkehren und zulassen, dass Sie mit dem nächsten Frame fortfahren.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Hybrid Grafik-PCs und Mixed Reality-Anwendungen

Windows 10 Creators Update-PCs **können mit diskreten** und integrierten GPUs konfiguriert werden. Mit diesen Computertypen wählt Windows den Adapter aus, mit dem das Headset verbunden ist. Anwendungen müssen sicherstellen, dass das von Ihnen erstellte DirectX-Gerät denselben Adapter verwendet.

Allgemeiner Direct3D Beispielcode veranschaulicht das Erstellen eines DirectX-Geräts mithilfe des Standard Hardware Adapters, der auf einem Hybridsystem möglicherweise nicht identisch mit dem für das Headset verwendeten ist.

Um Probleme zu umgehen, kann dies dazu führen, dass <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">holographicadapterid</a> entweder von <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a>verwendet wird. Primaryadapterid () oder <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">holographicdisplay</a>. Adapterid (). Diese Adapter-ID kann dann verwendet werden, um den richtigen dxgiadapter mithilfe von "IDXGIFactory4. endumadapterbyluid" auszuwählen.

Aus **deviceresources:: initializeusingholographicspace**:

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

Code zum **Aktualisieren von deviceresources:: kreatedeviceresources zur Verwendung von idxgiadapter**

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

**Hybrid Grafiken und Media Foundation**

Die Verwendung von Media Foundation auf Hybridsystemen kann zu Problemen führen, bei denen das Video nicht angezeigt wird oder die Video Textur beschädigt ist. Dies kann der Fall sein, wenn Media Foundation ein Systemverhalten standardmäßig wie oben erwähnt absetzt. In einigen Szenarien ist das Erstellen eines separaten ID3D11Device erforderlich, um Multithreading zu unterstützen, und die richtigen erstellungsflags werden festgelegt.

Beim Initialisieren des ID3D11Device muss D3D11_CREATE_DEVICE_VIDEO_SUPPORT Flag als Teil des D3D11_CREATE_DEVICE_FLAG definiert werden. Nachdem das Gerät und der Kontext erstellt wurden, müssen Sie <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">setmultithreadprotected</a> aufrufen, um Multithreading zu aktivieren. Um das Gerät dem <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">imfdxgidebug</a>Manager zuzuordnen, verwenden Sie die <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">imfdxgide vicemanager:: ResetDevice</a> -Funktion.

Code zum **Zuordnen eines ID3D11Device zu imfdxgidevicemanager**:

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

## <a name="see-also"></a>Weitere Informationen:
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
