---
title: Rendern in DirectX
description: Erläutert, holographic Rendering für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, der Rendering, der 3D-Grafiken HolographicFrame, rendern, Schleife, "Update"-Schleife, exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: fd35f971af4c3c9dfd7f21ee396c92216b3246e9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605164"
---
# <a name="rendering-in-directx"></a>Rendern in DirectX

Windows Mixed Reality basiert auf DirectX, um umfassende zu erzeugen, 3D grafische Umgebungen für Benutzer. Die Rendering-Abstraktion befindet sich direkt über DirectX und können eine app befassen Position und Ausrichtung von ein oder mehrere Beobachter über einer Szene holographic als vorhergesagten vom System. Entwickler kann ermitteln, deren Hologramme Bezug auf jede Kamera, lassen die app diese Hologramme in verschiedenen räumliche Koordinatensysteme zu rendern, wie der Benutzer, um wechselt.

## <a name="update-for-the-current-frame"></a>Update für den aktuellen frame

Zum Aktualisieren des Anwendungsstatus Hologramme einmal pro Bild der app führt Folgendes aus:
* Abrufen einer <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> aus dem Verwaltungssystem anzeigen.
* Aktualisieren Sie die Szene, mit der aktuellen Vorhersage, wo die Kameraansicht werden sollen, wenn Rendern abgeschlossen ist. Beachten Sie, dass mehr als einer Kamera für die Szene holographic möglich.

Um mit holographic Kameraansichten zu rendern, einmal pro Bild der app führt Folgendes aus:
* Rendern Sie für jede Kamera der Szene für den aktuellen Frame, mit der Kamera Ansichts- und Projektionstransformation Matrizen aus dem System ein.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Erstellen Sie einen neuen holographic Frame, und rufen Sie die Vorhersage

Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> enthält Informationen, die die app benötigt werden, um zu aktualisieren und den aktuellen Frame zu rendern. Die app beginnt jede neuen Frame mit dem Aufruf der **CreateNextFrame** Methode. Wenn diese Methode aufgerufen wird, erfolgen Vorhersagen unter Verwendung der neuesten Sensordaten verfügbar, und im gekapselten **CurrentPrediction** Objekt.

Ein neues Frameobjekt muss für jeden gerenderten Frame verwendet werden, wie es nur gültig für einen Zeitpunkt in der Zeit ist. Die **CurrentPrediction** Eigenschaft enthält Informationen wie z. B. die Position (Kamera). Die Informationen wird auf den genauen Zeitpunkt extrapoliert, wenn der Frame erwartet wird, für den Benutzer angezeigt werden.

Der folgende Code ist ein Auszug aus **AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Prozess-Kamera-updates

Hintergrundpuffer können von einem Frame zu Frame ändern. Ihre app muss die Sicherung überprüfen Puffern für jede Kamera, freigeben und Ressourcenansichten und Tiefenpuffern nach Bedarf neu erstellen. Beachten Sie, dass der Satz von ist in die Vorhersage der autoritative Liste der Kameras, die in den aktuellen Frame verwendet wird. In der Regel verwenden Sie diese Liste auf den Satz von Kameras zu durchlaufen.

Von **AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Von **DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Erhalten Sie das Koordinatensystem, die als Grundlage für das Rendering verwendet werden.

Windows Mixed Reality ermöglicht Ihrer app, die Erstellung verschiedener [Koordinatensysteme](coordinate-systems-in-directx.md) nach Bedarf, z. B. den angefügten Verweisdaten und der Frame stationär Verweis zur nachverfolgung von Standorten in der realen Welt. Ihre app können Sie dann diese Koordinatensysteme Grund dazu, wo Sie Hologramme jeder Frame zu rendern. Beim Anfordern von Koordinaten aus einer API, Sie werden immer übergeben die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> in dem diese Koordinaten ausgedrückt werden soll.

Von **AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Diese Koordinatensysteme kann dann verwendet werden, um Stereo Ansicht Matrizen zu generieren, wenn den Inhalt in der Szene zu rendern.

Von **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Prozess Blicke und Gestenhandler, die Eingabe

[Bestaunen](gaze.md) und [Geste](gestures.md) Eingabe sind nicht zeitbasierte und daher keine haben, aktualisieren Sie in der **StepTimer** Funktion. Jedoch [diese Eingabe](gaze,-gestures,-and-motion-controllers-in-directx.md) ist etwas, das die app bei jedem Bild aussehen muss.

### <a name="process-time-based-updates"></a>Verarbeiten eines zeitbasierten updates

Alle Echtzeit-Rendering-Apps benötigen eine Möglichkeit zum Verarbeiten von zeitbasierten Updates; Wir bieten eine Möglichkeit dazu in der Vorlage für Windows Holographic app über eine **StepTimer** Implementierung. Dies ähnelt der StepTimer, angegeben in die DirectX 11-UWP-app-Vorlage, also wenn Sie diese Vorlage bereits besprochen haben Sie auf vertraute Boden sein sollten. Diese Hilfsklasse für StepTimer Beispiel kann fester Zeitschritt Updates sowie Variablen Zeitschritt Updates bereitstellen, und der Standardmodus ist Variablen Zeitschritten.

Im Fall von holographic Rendering, haben wir uns speziell entschieden, nicht zu viel in der Timer-Funktion zu übertragen. Dies ist, da Sie können konfigurieren, um einen festen Schritt, in diesem Fall es möglicherweise mehr als einmal pro Frame – oder überhaupt nicht für einige Frames aufgerufen – und unsere holographic datenaktualisierungen einmal pro Frame auftreten sollte.


Von **AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Position und drehen Hologramme in Ihre Koordinatensystem

Wenn Sie in einem einzelnen Koordinatensystem, arbeiten, wie die Vorlage mit der **SpatialStationaryReferenceFrame**, dieser Vorgang unterscheidet sich nicht von was Sie andernfalls werden verwendet, die bei 3D-Grafiken. Hier, wir drehen Sie den Cube, und legen Sie die modellmatrix relativ zur Position im Koordinatensystem eines stationären Zustands.

Von **SpinningCubeRenderer::Update**:

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

**Beachten Sie Informationen zu erweiterten Szenarien:** Der sich drehenden Würfels ist ein sehr einfaches Beispiel zum Positionieren Sie ggf. ein Hologramm innerhalb eines einzelnen Verweises. Es ist auch möglich, [verwenden mehrere SpatialCoordinateSystems](coordinate-systems-in-directx.md) im gleichen gerenderte Frame, zur gleichen Zeit.

### <a name="update-constant-buffer-data"></a>Konstantenpuffer Aktualisierungsdaten

Modell-Transformationen für Inhalte werden wie gewohnt aktualisiert. Nun werden Sie gültige Transformationen für das Koordinatensystem berechnet wurde, die, denen Sie bei der, Rendern werden müssen.

Von **SpinningCubeRenderer::Update**:

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

Was ist mit der Ansichts- und Projektionstransformation Transformationen? Für optimale Ergebnisse sollten warten, bis wir fast fertig für unsere zeichnen, sind bevor wir diese eingehen.

## <a name="render-the-current-frame"></a>Den aktuellen Frame zu rendern

Rendern in Windows Mixed Reality unterscheidet sich nicht wesentlich vom Rendering in einer 2D-mono-Anzeige, aber es gibt einige Unterschiede, die, denen Sie berücksichtigen müssen:
* Holographic Frame Vorhersagen sind wichtig. Je näher die Vorhersage besteht darin, wenn Ihr Frame dargestellt wird, desto besser Ihre Hologramme sieht.
* Windows Mixed Reality steuert die Kameraansichten. Sie müssen in jeder gerendert werden soll, da der holographic Rahmen diese für Sie später noch Mal vorführen.
* Stereo-Rendern wird empfohlen, mithilfe von instanziierten Zeichnung auf ein Array der Render-Ziel erreicht werden. Die holographic app-Vorlage verwendet, die empfohlene Vorgehensweise instanziierten Zeichnung in ein Array der Render-Ziel, die eine renderzielansicht auf verwendet eine **Texture2DArray**.
* Wenn Sie ohne Verwendung von Stereo Instanziierung rendern möchten, müssen Sie zwei RenderTargetViews für nicht-Array (eine für jedes Auge) zu erstellen, die jeden Verweis eine der beiden in slices der **Texture2DArray** an die app aus dem System bereitgestellt. Dies wird nicht empfohlen, wie es in der Regel wesentlich langsamer als die Verwendung von Instanziierung ist.

### <a name="get-an-updated-holographicframe-prediction"></a>Erhalten Sie eine aktualisierte HolographicFrame-Vorhersage

Aktualisieren die Frame-Vorhersage verbessert die Effektivität der Stabilisierung des Image, und ermöglicht genauere Positionierung von Hologramme aufgrund der kürzeren Zeit zwischen der Vorhersage und wenn der Frame für den Benutzer sichtbar ist. Im Idealfall aktualisieren Sie Ihre Frame Vorhersage nur vor dem Rendern.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Für jede Kamera Rendern

Eine Schleife für den Satz von Kamera ist in die Vorhersage, und in jede Kamera in dieser Gruppe gerendert.

**Richten Sie Ihren Pass-rendering**

Windows Mixed Reality verwendet stereoskopische Rendering, um die Illusion von Tiefe zu verbessern und Gläsern, rendern, damit der linken und rechten Anzeige aktiv sind. Bei stereoskopische Rendering besteht eine Abweichung zwischen den zwei angezeigt, die vom Gehirn als tatsächliche Tiefe abstimmen kann. Dieser Abschnitt behandelt stereoskopische Rendern über Instanziierung ist die Verwendung eines Codes über die Windows Holographic-app-Vorlage.

Jede Kamera hat einen eigenen Render Ziel (Hintergrundpuffer), und die Ansichts- und Projektionstransformation Matrizen in der holografischen Speicherplatz. Ihre app benötigt andere Kamera-basierte Ressourcen – z. B. Tiefenpuffer - auf einer pro-Kamera-Basis zu erstellen. In der Windows Holographic-app-Vorlage bieten wir eine Hilfsklasse, um diese Ressourcen im DX::CameraResources bündeln. Starten Sie, indem die renderzielansichten einrichten:

Von **AppMain::Render**:

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

**Verwenden Sie die Vorhersage, um die Ansichts- und Projektionstransformation Matrizen für die Kamera zu erhalten.**

Die Ansichts- und Projektionstransformation Matrizen für jede holographic Kamera werden mit jedem Frame ändern. Aktualisieren Sie die Daten in den Konstantenpuffer für jede holographic Kamera. Dies tun, nachdem Sie die Vorhersage aktualisiert, und vor jedem Zeichnen für diese Kamera.

Von **AppMain::Render**:

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

Hier wird erläutert, wie die Matrizen von der Kamera Haltung erworben werden. Während dieses Vorgangs erhalten wir auch die aktuellen Viewport für die Kamera. Beachten Sie, wie wir einem Koordinatensystem bereitstellen: Dies ist das gleiche Koordinatensystem, die wir verwendet, um die Blicke zu verstehen, und es ist die gleiche wir verwendet, um den sich drehenden Würfels zu positionieren.


Von **CameraResources::UpdateViewProjectionBuffer**:

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

Der Viewport muss jeder Frame festgelegt werden. Der Vertex-Shader benötigen (mindestens) in der Regel Zugriff auf die Daten für die Ansichts-und Projektionsmatrix.


Von **CameraResources::AttachViewProjectionBuffer**:

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

**In den Hintergrundpuffer der Kamera gerendert, und committen Sie Tiefenpuffer**:

Es ist eine gute Idee, die überprüft, ob **TryGetViewTransform** erfolgreich war, bevor Sie versuchen, die die Ansichts-und Projektionsmatrix-Daten verwenden, da ist das Koordinatensystem nicht gefunden werden (z. B. nachverfolgung wurde unterbrochen) Ihre app kann nicht mit gerendert werden, Frame. Die Vorlage nur ruft **Rendern** auf den sich drehenden Würfels Wenn die **CameraResources** -Ereignisklasse zeigt an, ein erfolgreiches Update.

Um Hologramme zu halten, in denen schreibt ein Entwickler oder Benutzer sie in der ganzen Welt, bietet Windows Mixed Reality Features für [image Stabilisierung](hologram-stability.md). Image Stabilisierung ist hilfreich, die Wartezeit, die sich eine Rendering-Pipeline, um sicherzustellen, dass die am besten holographic Benutzeroberflächen für Benutzer auszublenden. ein Fokuspunkt kann angegeben werden, um Image Stabilisierung noch weiter zu verbessern, oder ein Tiefenpuffer kann angegeben werden, um berechnen Image Stabilisierung in Echtzeit optimiert.

Für optimale Ergebnisse sollten Ihre app bereitstellen, eine Tiefe Puffer mithilfe der <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API. Windows Mixed Reality Geometrieinformationen können Sie dann aus der Tiefenpuffer Image Stabilisierung in Echtzeit zu optimieren. Die Windows Holographic-app-Vorlage führt einen Commit für die app Tiefenpuffer standardmäßig unterstützen – Hologramm Stabilität zu optimieren.

Von **AppMain::Render**:

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
>Windows verarbeitet Ihre Tiefe Textur auf der GPU, sodass es möglich, Ihre Tiefenpuffer als Shaderressource zu verwenden sein muss. Die ID3D11Texture2D, die Sie erstellen sollte in einem Format typenlos und es als Shaderressource gebunden werden soll. Hier ist ein Beispiel dafür, wie eine Textur Tiefe zu erstellen, die für die Stabilisierung des Image ausgeführt werden kann.

Code für **Tiefe Puffer ressourcenerstellung für CommitDirect3D11DepthBuffer**:

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

**Zeichnen Sie holographic Inhalt**

Die Windows Holographic-app-Vorlage rendert Inhalt in Stereo mit das empfohlene Verfahren ein Texture2DArray von der Größe 2 instanziierten Geometrie gezeichnet. Sehen wir uns auf die Instanziierung Teil dies und deren Funktionsweise in Windows Mixed Reality.

Von **SpinningCubeRenderer::Render**:

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

Jede Instanz greift auf eine andere Ansicht/Projektionsmatrix aus den Konstantenpuffer zu. Hier ist die Konstantenpuffer-Struktur, die nur ein Array von 2-Matrizen ist.

Von **VertexShaderShared.hlsl**, eingeschlossen durch **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Der Arrayindex der Render-Ziel muss für jedes Pixel festgelegt werden. Im folgenden Codeausschnitt output.viewId zugeordnet ist die **SV_RenderTargetArrayIndex** semantische. Beachten Sie, dass diese Unterstützung für eine optionale Direct3D 11.3-Funktion, dem den Arrayindex der Render-Ziel semantische aus shaderstufe festgelegt werden können.

From **VPRTVertexShader.hlsl**:

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

Von **VertexShaderShared.hlsl**, eingeschlossen durch **VPRTVertexShader.hlsl**:

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

Wenn Sie Ihre vorhandene Instanz verwenden möchten zeichnen Techniken mit dieser Methode der Zeichnung auf ein Stereo Rendern Zielarrays begonnen wird alles, was man dazu Unternehmen muss zweimal die Anzahl der Instanzen, die in der Regel keine zeichnen. In den Shader, teilen **input.instId** durch 2, um die ursprüngliche Instanz-ID zu erhalten, die in (z. B.) auf einen Puffer von pro-Objekt Daten indiziert werden kann: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Wichtiger Hinweis zum Rendern von Stereo Inhalt für HoloLens

Windows Mixed Reality unterstützt die Möglichkeit, die den Arrayindex der Render-Ziel über shaderstufe festgelegt. Normalerweise ist dies eine Aufgabe, die nur in der Geometrie-Shader-Stufe aufgrund der Art, durchgeführt werden konnte, die die Semantik für Direct3D 11 definiert ist. Hier zeigen wir ein vollständiges Beispiel dafür, wie eine renderingpipeline mit den Scheitelpunkt und den Pixel-Shader Phasen Satz einrichten. Der Shader-Code wird wie oben beschrieben.

Von **SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Wichtiger Hinweis zum Rendern auf nicht-HoloLens-Geräte

Zum Festlegen des Arrayindex der Render-Ziel in der Vertex-Shader muss der Grafiktreiber eine optionale Direct3D 11.3-Funktion unterstützt die HoloLens unterstützen. Ihre app möglicherweise nur diese Methode für das Rendering sicher zu implementieren, und für die Ausführung auf der Microsoft HoloLens werden alle Anforderungen erfüllt werden.

Es kann der Fall sein, den Sie ebenfalls die HoloLens-Emulator verwenden möchten die kann eine leistungsstarke Entwicklungstool für Ihre holographic-app - und unterstützen Windows Mixed Reality immersive Kopfhörer-Geräte, die mit Windows 10-PCs verbunden sind. Unterstützung für den nicht-HoloLens-Rendering-Pfad - und daher für alle Windows Mixed Reality - ist auch in die Windows Holographic-app-Vorlage integriert. Im Vorlagencode finden Sie Code für Ihre Anwendung holographic auf der GPU in Ihrem Entwicklungs-PC ausgeführt werden kann. Hier ist die **DeviceResources** -Klasse sucht diese optionales Feature-Unterstützung.

Von **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Um rendern, ohne diese optionale Funktion zu unterstützen, muss Ihre app einen Geometrie-Shader verwenden, den Arrayindex der Render-Ziel festlegen. Dieser Codeausschnitt hinzugefügt *nach* **VSSetConstantBuffers**, und *vor* **PSSetShader** im Codebeispiel wird gezeigt, in der vorherigen Abschnitt für das Rendern von Stereo für HoloLens erläutert wird.

Von **SpinningCubeRenderer::Render**:

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

**BEACHTEN SIE HLSL**: In diesem Fall müssen Sie auch einen leicht abgeänderte Vertex-Shader laden, der den Arrayindex der Render-Ziel an die Geometrie-Shader verwenden eine semantische, z. B. TEXCOORD0 immer zulässig Shaders übergibt. Geometrie-Shader keine Schritte erforderlich; die Vorlage Geometrie-Shader durchläuft alle Daten, mit Ausnahme von Render Zielindex des Arrays, die verwendet wird, die SV_RenderTargetArrayIndex semantische festlegen ab.

App-Vorlagencode für **GeometryShader.hlsl**:

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

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Aktivieren Sie den holographic Frame die SwapChain vorhanden

Mit Windows Mixed Reality steuert das System die SwapChain. Das System verwaltet dann in jede Kamera holographic, um sicherzustellen, dass eine qualitativ hochwertige benutzererfahrung Präsentation vorführen Frames. Darüber hinaus ein Update des Viewports jeden Frame für jede Kamera, um Aspekte des Systems wie z. B. Image Stabilisierung oder Mixed Reality erfassen zu optimieren. Also eine holographic-app mit DirectX Aufrufen nicht **vorhanden** auf eine DXGI Kette austauschen. Verwenden Sie stattdessen die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> Klasse, um alle Sie swapchains hervor für einen Frame vorhanden, wenn Sie fertig sind gezeichnet wird.

Von **DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Standardmäßig wartet diese API für den Rahmen um den Vorgang abzuschließen, bevor sie zurückkehrt. Holographic apps sollten warten, für den vorherigen Frame abgeschlossen ist, bevor Sie mit der Arbeit beginnen auf einen neuen Frame, da dies verringert die Latenz und eine bessere Ergebnisse holographic Frame Vorhersagen ermöglicht. Dies ist eine feste Regel nicht, und wenn man Frames, die länger als einen Bildschirm Aktualisierung durch dauern, um Sie rendern deaktivieren, diese Wartezeit durch Übergeben des Parameters HolographicFramePresentWaitBehavior zu <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. Sie würden in diesem Fall wahrscheinlich einen asynchrones Rendering-Thread verwenden, um einer fortlaufenden Last auf dem GPU zu gewährleisten. Beachten Sie, dass die Häufigkeit der Aktualisierung des Geräts HoloLens 60 hz ist, in dem Frame eine Dauer von ca. 16 ms. Immersive Kopfhörer Geräten reichen von 60 hz bis 90 hz; Wenn Sie die Anzeige bei 90 hz aktualisieren zu können, müssen alle Frames eine Dauer von etwa 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>In Zusammenarbeit mit der HolographicFrame DeviceLost Szenarien

DirectX 11-apps sollten in der Regel überprüfen Sie der DXGI-SwapChain zurückgegebene HRESULT **vorhanden** Funktion, um herauszufinden, ob es wurde eine **DeviceLost** Fehler. Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> Klasse übernimmt dies für Sie. Überprüfen Sie die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> wird zurückgegeben, um herauszufinden, ob müssen Sie Version und der Direct3D-Gerät und mithilfe von gerätebasierten Ressourcen neu zu erstellen.

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

Beachten Sie, dass wenn das Direct3D-Gerät unterbrochen wurde, und Sie es neu erstellen, Sie müssen die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> beim Einstieg in das neue Gerät. Die SwapChain wird für dieses Gerät neu erstellt werden.

Von **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Wenn Ihr Frame dargestellt wird, können Sie an die Schleife Hauptprogramm zurückgegeben und erlauben, dass bis zum nächsten Frame zu.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Hybrid-Grafik-PCs und mixed Reality-Anwendungen

Windows 10 Creators Update PCs können so konfiguriert werden, mit **sowohl** diskreter als auch integrierten GPUs. Mit diesen Typen von Computern wählt Windows den Adapter, die, dem an den Kopfhörer angeschlossen ist. Anwendungen müssen stellen Sie sicher, dass das DirectX-Gerät erstellten den gleichen Adapter verwendet.

Die meisten allgemeinen Direct3D-Beispielcode veranschaulicht das Erstellen einer DirectX-Gerät mit den Standardadapter für die Hardware, der auf einem hybridsystem nicht identisch mit der für den Kopfhörer verwendet werden kann.

Verwenden Sie zur Umgehung Probleme dadurch möglicherweise die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> entweder <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() oder <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId(). Diese "AdapterId" kann dann verwendet werden, Auswahl der richtigen DXGIAdapter IDXGIFactory4.EnumAdapterByLuid verwenden.

Von **DeviceResources::InitializeUsingHolographicSpace**:

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

Um den Code **DeviceResources::CreateDeviceResources Verwendung IDXGIAdapter aktualisieren**

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

**Hybrid-Grafiken und Media Foundation**

Mit Media Foundation in Hybriden Systemen kann verursachen, in dem Video wird nicht gerendert oder video-Textur ist beschädigt. Dies kann auftreten, da Media Foundation, um ein Systemverhalten Standardwert ist wie oben erwähnt. In einigen Szenarien ist es erforderlich, Unterstützung von Multithreading und das richtige erstellen, die Flags festgelegt sind, erstellen eine separate ID3D11Device.

Wenn die ID3D11Device initialisiert wird, muss D3D11_CREATE_DEVICE_VIDEO_SUPPORT-Flag im Rahmen der D3D11_CREATE_DEVICE_FLAG definiert werden. Rufen Sie nach dem Gerät und dem Kontext erstellt wird, <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> zu multithreading. Zuordnen des Geräts mit der <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, verwenden Sie die <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> Funktion.

Um den Code **ordnen Sie einem ID3D11Device IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme im DirectX](coordinate-systems-in-directx.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
