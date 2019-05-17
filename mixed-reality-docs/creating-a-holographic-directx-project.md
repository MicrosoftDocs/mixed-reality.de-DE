---
title: Erstellen eines holographic DirectX-Projekts
description: Erläutert, wie Sie eine neue holographic app basierend auf der Windows Mixed Reality-app-Vorlage erstellen.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic-app, neue app, UWP-app, Vorlagen-app, Hologramme, neues Projekt, exemplarische Vorgehensweise, Herunterladen von Beispielcode
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828133"
---
# <a name="creating-a-holographic-directx-project"></a>Erstellen eines holographic DirectX-Projekts

Eine holographic-app erstellen Sie bei einem HoloLens eine <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">universelle Windows-Plattform (UWP) app</a>.  Wenn desktop Windows Mixed Reality-Headsets verwenden zu können, können Sie eine UWP-app oder eine Win32-app erstellen.

Die DirectX 11 holographic UWP-app-Vorlage ähnelt die DirectX 11-UWP-app-Vorlage; Es enthält eine Programm-Schleife (oder "spielschleife") eine **DeviceResources** zum Verwalten der Direct3D-Gerät und der Kontext, und einer vereinfachten inhaltsrenderer-Klasse. Es verfügt auch über eine <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">"iframeworkview"</a>genau wie jede andere UWP-app.

Mixed Reality-app, hat jedoch einige zusätzlichen Funktionen, die nicht in einer typischen Direct3D 11-UWP-app vorhanden sind. Die Windows Holographic-app-Vorlage kann:
* Behandeln Sie Direct3D-Geräteressourcen holographic Kameras zugeordnet.
* Abgerufen Sie Kamera-Hintergrundpuffer vom System werden.
* Behandeln [bestaunen](gaze.md) geben an, und erkennen Sie eine einfache [Geste](gestures.md).
* Wechseln Sie in den Vollbild-Stereo Renderingmodus.

## <a name="how-do-i-get-started"></a>Wie fange ich an?

Erste [Installieren der Tools](install-the-tools.md), gemäß den Anweisungen zum Herunterladen von Visual Studio 2017 und dem Microsoft HoloLens-Emulator. Die holographic app-Vorlagen sind in der gleiche Installer als Microsoft HoloLens-Emulator enthalten. Stellen Sie außerdem sicher, dass die Option zum Installieren der Vorlagen vor der Installation ausgewählt ist.

Nun können Sie die DirectX 11 Windows Mixed Reality-app erstellt. Beachten Sie, dass die Beispielinhalte zu entfernen, kommentieren Sie die **DRAW_SAMPLE_CONTENT** -präprozessoranweisung in *"PCH.h"*.

## <a name="creating-a-uwp-project"></a>Erstellen eines UWP-Projekts

Sobald die [-Tools sind installiert](install-the-tools.md) anschließend können Sie ein holographic DirectX-UWP-Projekt erstellen.

So erstellen Sie ein neues Projekt:
1. Starten Sie **Visual Studio**.
2. Von der **Datei** Startmenü **neu** , und wählen Sie **Projekt** aus dem Kontextmenü. Die **neues Projekt** Dialogfeld wird geöffnet.
3. Erweitern Sie **installiert** auf der linken Seite, und erweitern Sie die **Visual C++**  Sprachknoten.
4. Navigieren Sie zu der **Windows Universal > Holographic** Knoten, und wählen **Holographic DirectX 11-App (Universelles Windows) (C++"/ WinRT")**.
   ![Screenshot des Holographic DirectX 11 C++WinRT UWP-app-Projektvorlage in Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holographic DirectX 11 C++WinRT UWP-app-Projektvorlage in Visual Studio*
   >[!IMPORTANT]
   >Achten Sie darauf, dass die Projektvorlage enthält "(C++" / WinRT ")".  Wenn dies nicht der Fall ist, Sie haben eine ältere Version der installierten holographic Projektvorlagen.  Zum Abrufen der neuesten Projektvorlagen [installieren Sie den neuesten Emulator für HoloLens](using-the-hololens-emulator.md).
5. Geben Sie die **Namen** und **Speicherort** Textfelder, und klicken oder tippen Sie **OK**. Das holographic app-Projekt wird erstellt.
6. Für die Entwicklung als Ziel nur HoloLens 2, sicher, dass die **Zielversion** und **Mindestversion** festgelegt **Windows 10, Version 1903**.  Wenn Sie auch die HoloLens verwenden möchten (der 1. Generation) oder desktop Windows Mixed Reality-Headsets, Sie können festlegen, **mindestens erforderliche Version** zu **Windows 10, Version 1809** stattdessen, obwohl dies einige erfordert <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> adaptive versionsprüfungen</a> in Ihrem Code bei Verwendung der neuen Features von HoloLens 2.
   ![Screenshot der Windows 10, Version 1903 sein, wie die Ziel- und mindestplattformversionen Versionen festlegen](images/new-uwp-project.png)<br>
   *Festlegen von **Windows 10, Version 1903** wie die Ziel- und mindestplattformversionen-Versionen*
   >[!IMPORTANT]
   >Wenn Sie nicht sehen **Windows 10, Version 1903** als Option können Sie keine der neuesten Windows 10-SDK installiert.  Um diese Option aus, die angezeigt werden, erhalten <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">installieren Sie Version 10.0.18362.0 oder höher von Windows 10 SDK</a>.

Die Vorlage generiert ein Projekt mit <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++"/ WinRT"</a>, eine C ++ 17 sprachprojektion für die Windows-Runtime-APIs, die von einem beliebigen standardkonformen C ++ 17-Compiler unterstützt.  Das Projekt veranschaulicht, wie einen Welt gesperrt Cube zu erstellen, der zwei Werte aus der Benutzer platziert wurde. Der Benutzer kann [tippbewegung](gestures.md#air-tap) oder auf eine Schaltfläche klicken, auf dem Controller auf den Cube in einer anderen Position zu platzieren, das durch des Benutzers angegeben wird [bestaunen](gaze.md). Sie können dieses Projekt aus, um alle mixed Reality-app erstellen, ändern.

Alternativ können Sie ein neues Projekt mit erstellen die **Visual C#**  holographic-Projektvorlage, die auf "sharpdx" basiert.  Wenn Ihre holographic C# Projekt konnte nicht aus der Vorlage für Windows Holographic-app gestartet werden, müssen Sie zum Kopieren der ms.fxcompile.targets-Datei aus einer Windows Mixed Reality C# -Vorlagenprojekt und importieren es in Ihrer CSPROJ-Datei Datei zum Kompilieren von "HLSL" Dateien, die Sie Ihrem Projekt hinzu.

Überprüfen Sie [mit Visual Studio bereitstellen und Debuggen](using-visual-studio.md) Informationen zum Erstellen und Bereitstellen der App in Ihrem HoloLens, PC mit immersive angeschlossenen Gerät oder einem Emulator.

Der Rest der unten stehenden Anweisungen aus der Annahme, dass die Verwendung von C++ zum Erstellen der app.

### <a name="uwp-app-entry-point"></a>Einstiegspunkt für UWP-app

Die holographic UWP-app startet, in der **wWinMain** -Funktion in AppView.cpp. Die **wWinMain** -Funktion erstellt, der app <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">"iframeworkview"</a> und startet die <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">"coreapplication"</a> mit.

Von **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Von diesem Zeitpunkt an behandelt die AppView-Klasse Interaktion mit grundlegenden Windows-Eingabeereignisse, CoreWindow-Ereignisse und messaging und So weiter. Es wird auch die von Ihrer app verwendeten HolographicSpace erstellt.

## <a name="creating-a-win32-project"></a>Erstellen ein Win32-Projekt

Die einfachste Möglichkeit zum Entwickeln einer Win32 holographic Projekt angepasst ist die <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32-Beispiel</a>.

Dieses Beispiel Win32 verwendet <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++"/ WinRT"</a>, eine C ++ 17 sprachprojektion für die Windows-Runtime-APIs, die von einem beliebigen standardkonformen C ++ 17-Compiler unterstützt.  Das Projekt veranschaulicht, wie einen Welt gesperrt Cube zu erstellen, der zwei Werte aus der Benutzer platziert wurde. Der Benutzer kann eine Schaltfläche drücken, auf dem Controller auf den Cube in einer anderen Position zu platzieren, das durch des Benutzers angegeben wird [bestaunen](gaze.md). Sie können dieses Projekt aus, um alle mixed Reality-app erstellen, ändern.

### <a name="win32-app-entry-point"></a>Einstiegspunkt für Win32-app

Ihre holographic Win32-app gestartet wird, der **wWinMain** -Funktion in AppMain.cpp. Die **wWinMain** Funktion der app-HWND erstellt und die Meldungsschleife beginnt.

Von **AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Von diesem Zeitpunkt an behandelt die AppMain Klasse Interaktion mit grundlegenden Windows-Meldungen und So weiter. Es wird auch die von Ihrer app verwendeten HolographicSpace erstellt.

## <a name="render-holographic-content"></a>Holographic Inhalt Rendern

Des Projekts **Content** Ordner enthält die Klassen für die Rendering-Hologramme in die [holographic Speicherplatz](getting-a-holographicspace.md). Der Standardwert – Hologramm, in der Vorlage ist eine sich drehenden Würfels, die zwei Verbrauchseinheiten Weg von der Benutzer platziert wurde. Zeichnen diesen Cube ist in implementiert **SpinningCubeRenderer.cpp**, die über diese wichtigsten Methoden verfügt:

|  Methode  |  Erläuterung | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Shader geladen und erstellt das Netz Cube. | 
|  `PositionHologram` |  Der – Hologramm platziert, an der Position angegeben wird, vom bereitgestellten <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>. | 
|  `Update` |  Dreht den Cube und setzt die modellmatrix. | 
|  `Render` |  Rendert einen Frame mit dem Scheitelpunkt und Pixel-Shader. | 

Die **Shader** Unterordner enthält vier standardimplementierungen-Shader:

|  Shader  |  Erläuterung | 
|----------|----------|
|  `GeometryShader.hlsl` |  Ein Passthrough-Vorgang, die die Geometrie bleibt unverändert. | 
|  `PixelShader.hlsl` |  Durchläuft die Farbdaten. Die Farbdaten werden interpoliert und ein Pixel auf den Schritt Rasterization zugewiesen. | 
|  `VertexShader.hlsl` |  Einfacher Shader für Vertex-Bearbeitung auf der GPU führen zu erhalten. | 
|  `VPRTVertexShader.hlsl` |  Einfacher Shader für Vertex-Bearbeitung in der GPU, die für das Windows Mixed Reality-Stereo-Rendering optimiert ist, führen zu erhalten. | 

`VertexShaderShared.hlsl` enthält die gemeinsamen Code gemeinsam `VertexShader.hlsl` und `VPRTVertexShader.hlsl`.

Shader werden kompiliert, wenn das Projekt erstellt wird, und sie im geladen sind der **SpinningCubeRenderer::CreateDeviceDependentResources** Methode.

## <a name="interact-with-your-holograms"></a>Interagieren mit Ihrem Hologramme

Benutzereingabe wird verarbeitet, der **SpatialInputHandler** Klasse, welche Ruft eine <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> -Instanz und abonniert die <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> Ereignis. Dies ermöglicht die tippbewegung Aktion und andere räumliche Eingabeereignisse erkannt.

## <a name="update-holographic-content"></a>Holographic Inhalt aktualisieren

Ihrer mixed Reality-app-Updates in einer Spiele-Schleife, die standardmäßig in implementiert ist die **Update** -Methode in der `AppMain.cpp`. Die **Update** Methode szeneobjekte, z. B. den sich drehenden Würfels, aktualisiert und gibt eine <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> -Objekt, das verwendet wird, um auf dem neuesten Stand Ansichts- und Projektionstransformation Matrizen abzurufen und die SwapChain zu präsentieren.

Die **Rendern** -Methode in der `AppMain.cpp` nimmt die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> und rendert den aktuellen Frame jede holographic Kamera, entsprechend der aktuellen app und die räumliche Positionierung Zustand.

## <a name="see-also"></a>Siehe auch
* [Abrufen eines HolographicSpace-Objekts](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Rendern in DirectX](rendering-in-directx.md)
* [Verwenden von Visual Studio zum Bereitstellen und Debuggen](using-visual-studio.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Verwenden von XAML mit holographischen DirectX-Apps](using-xaml-with-holographic-directx-apps.md)
