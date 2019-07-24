---
title: Erstellen eines Holographic DirectX-Projekts
description: Erläutert das Erstellen einer neuen Holographic-App basierend auf der Windows Mixed Reality-App-Vorlage.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Holographic APP, New APP, UWP APP, Template APP, holograms, neues Projekt, Exemplarische Vorgehensweise, Download, Beispielcode
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387615"
---
# <a name="creating-a-holographic-directx-project"></a>Erstellen eines Holographic DirectX-Projekts

Eine Holographic-APP, die Sie für ein hololens erstellen, ist eine <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">universelle Windows-Plattform-app (UWP)</a>.  Wenn Sie auf Desktop-Windows Mixed Reality-Headsets abzielen, können Sie eine UWP-APP oder eine Win32-app erstellen.

Die Vorlage DirectX 11 Holographic UWP App ähnelt der APP-Vorlage DirectX 11 UWP. Sie enthält eine Programm Schleife (oder "Spiel Schleife"), eine **deviceresources** -Klasse zum Verwalten des Direct3D-Geräts und-Kontexts und eine vereinfachte inhaltsrendererklasse. Es verfügt auch über eine <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">iframeworkview</a>, wie jede andere UWP-app.

Die Mixed Reality-App bietet jedoch einige zusätzliche Funktionen, die in einer typischen Direct3D 11 UWP-APP nicht vorhanden sind. Die Vorlage für die Windows Holographic-App kann folgende Aktionen ausführen:
* Handle Direct3D Geräte Ressourcen, die mit Holographic Kameras verknüpft sind.
* Rückruf Puffer aus dem System abrufen.
* Behandeln Sie die über [Blicks](gaze.md) Eingaben, und erkennen Sie eine einfache [Geste](gestures.md).
* Wechseln Sie in den Vollbild-Stereo Renderingmodus.

## <a name="how-do-i-get-started"></a>Gewusst wie starten?

Installieren Sie zunächst [die Tools](install-the-tools.md), und befolgen Sie dabei die Anweisungen zum Herunterladen von Visual Studio 2019 und dem Microsoft hololens-Emulator. Die Holographic-App-Vorlagen sind im gleichen Installer enthalten wie der Microsoft hololens-Emulator. Stellen Sie außerdem sicher, dass die Option zum Installieren der Vorlagen vor der Installation von ausgewählt ist.

Nun können Sie Ihre DirectX 11 Windows Mixed Reality-app erstellen! Wenn Sie den Beispiel Inhalt entfernen möchten, kommentieren Sie die **DRAW_SAMPLE_CONTENT** -Präprozessordirektive in " *PCH. h*" aus.

## <a name="creating-a-uwp-project"></a>Erstellen eines UWP-Projekts

Nachdem Sie die [Tools installiert haben](install-the-tools.md) , können Sie ein Holographic DirectX-UWP-Projekt erstellen.

So erstellen Sie ein neues Projekt:
1. Starten Sie **Visual Studio**.
2. Zeigen Sie im Menü **Datei** auf **neu** , und wählen Sie im Kontextmenü **Projekt** aus. Das Dialogfeld " **Neues Projekt** " wird geöffnet.
3. Erweitern Sie auf der linken Seite die Option **installiert** , und erweitern Sie den Knoten **visuelle C++**  Sprache.
4. Navigieren Sie zum Knoten **universelle Windows-> Holographic** , und wählen Sie **Holographic DirectX 11-APPC++(universelle Windows-APP) (/WinRT)** aus.
   ![Screenshot der Holographic DirectX 11 C++/WinRT UWP-App-Projektvorlage in Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holographic DirectX 11 C++/WinRT UWP-App-Projektvorlage in Visual Studio*
   >[!IMPORTANT]
   >Stellen Sie sicher, dass der Name der Projektvorlage "C++(/WinRT)" enthält.  Andernfalls ist eine ältere Version der Holographic-Projektvorlagen installiert.  Um die neuesten Projektvorlagen zu erhalten, [Installieren Sie den neuesten hololens-Emulator](using-the-hololens-emulator.md).
5. Füllen Sie die Textfelder **Name** und **Speicherort** aus, und klicken oder tippen Sie auf **OK**. Das Projekt für die Holographic-APP wird erstellt.
6. Stellen Sie sicher, dass die **Zielversion** und die **Mindestversion** für die Entwicklung auf hololens 2 auf **Windows 10, Version 1903,** festgelegt sind.  Wenn Sie auch hololens (1st Gen) oder Desktop-Windows Mixed Reality-Headsets als Ziel verwenden, können Sie die **Mindestversion** auf **Windows 10, Version 1809** , festlegen, obwohl dies einige <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">Adaptive Überprüfungen der Version</a> in Ihrem Code erfordert, wenn Sie New verwenden. Features von hololens 2.
   ![Screenshot der Festlegung von Windows 10, Version 1903, als Ziel-und Mindestversion](images/new-uwp-project.png)<br>
   *Festlegen von **Windows 10, Version 1903** als Ziel-und Mindestversion*
   >[!IMPORTANT]
   >Wenn **Windows 10, Version 1903** , nicht als Option angezeigt wird, ist das neueste Windows 10 SDK nicht installiert.  Um diese Option anzuzeigen, installieren Sie <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">die Version 10.0.18362.0 oder höher des Windows 10 SDK</a>.

Die Vorlage generiert ein Projekt mit <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, einer c++ 17-sprach Projektion der Windows-Runtime-APIs, die jeden Standard kompatiblen c++ 17-Compiler unterstützen.  Das Projekt zeigt, wie ein weltweit gesperrter Cube erstellt wird, der zwei Meter vom Benutzer platziert wird. Der Benutzer kann auf dem Controller auf eine Schaltfläche [tippen](gestures.md#air-tap) oder auf eine Schaltfläche klicken, um den Cube an einer anderen Position zu platzieren, die durch den Benutzer angezeigt [wird.](gaze.md) Sie können dieses Projekt ändern, um eine beliebige gemischte Reality-APP zu erstellen.

Alternativ können Sie ein neues Projekt erstellen, indem Sie **die C# Visual** Holographic-Projektvorlage verwenden, die auf sharpdx basiert.  Wenn Ihr Holographic C# -Projekt nicht mit der Windows Holographic-App-Vorlage gestartet wurde, müssen Sie die Datei "MS. fxcompile. targets" aus einem Windows C# Mixed Reality-Vorlagen Projekt kopieren und in die CSPROJ-Datei importieren, um HLSL zu kompilieren. Dateien, die Sie dem Projekt hinzufügen.

Lesen Sie die Informationen unter [Verwenden von Visual Studio zum Bereitstellen und Debuggen](using-visual-studio.md) , um Informationen zum Erstellen und Bereitstellen des Beispiels für Ihre hololens, PCs mit immersives Gerät oder einen Emulator zu erhalten.

In den restlichen Anweisungen wird davon ausgegangen, dass Sie verwenden C++ , um Ihre APP zu erstellen.

### <a name="uwp-app-entry-point"></a>UWP-App-Einstiegspunkt

Ihre Holographic UWP-App beginnt in der **wWinMain** -Funktion in appview. cpp. Die **wWinMain** -Funktion erstellt die <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">iframeworkview</a> der APP und startet die <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">coreapplication-Anwendung</a> .

Aus **appview. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Ab diesem Zeitpunkt behandelt die appview-Klasse die Interaktion mit Windows Basic-Eingabe Ereignissen, corewindow-Ereignissen und-Messaging usw. Außerdem wird der von Ihrer APP verwendete holographicspace-Wert erstellt.

## <a name="creating-a-win32-project"></a>Erstellen eines Win32-Projekts

Die einfachste Möglichkeit, um mit dem Aufbau eines Win32 Holographic-Projekts zu beginnen, besteht darin, das <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">Win32-Beispiel *basichologram* </a>anzupassen.

Dieses Win32-Beispiel verwendet <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, eine c++ 17-sprach Projektion der Windows-Runtime-APIs, die jeden Standard kompatiblen c++ 17-Compiler unterstützen.  Das Projekt zeigt, wie ein weltweit gesperrter Cube erstellt wird, der zwei Meter vom Benutzer platziert wird. Der Benutzer kann auf dem Controller auf eine Schaltfläche klicken, um den Cube an einer anderen Position zu platzieren, die durch den Benutzer [Blick](gaze.md)angegeben wird. Sie können dieses Projekt ändern, um eine beliebige gemischte Reality-APP zu erstellen.

### <a name="win32-app-entry-point"></a>Win32-App-Einstiegspunkt

Ihre Holographic-Win32-App beginnt in der **wWinMain** -Funktion in appmain. cpp. Die **wWinMain** -Funktion erstellt das HWND der APP und startet die Nachrichten Schleife.

Aus **appmain. cpp**:

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

Ab diesem Punkt verarbeitet die appmain-Klasse die Interaktion mit grundlegenden Fenster Meldungen usw. Außerdem wird der von Ihrer APP verwendete holographicspace-Wert erstellt.

## <a name="render-holographic-content"></a>Holographic-Inhalt Wiedergabe

Der **Inhalts** Ordner des Projekts enthält Klassen zum Rendern von holograms im [Holographic-Raum](getting-a-holographicspace.md). Das standardmäßige – Hologramm in der Vorlage ist ein drehende Cube, der zwei Meter entfernt ist als der Benutzer. Das zeichnen dieses Cubes ist in der Datei " **spinningcuberenderer. cpp**" implementiert, die über die folgenden Schlüsselmethoden verfügt:

|  Methode  |  Erläuterung | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Lädt Shader und erstellt das Cube-Mesh. | 
|  `PositionHologram` |  Platziert das Hologramm an der Position, die durch die bereitgestellte <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">spatialpointerpose</a>angegeben wird. | 
|  `Update` |  Dreht den Cube und legt die Modell Matrix fest. | 
|  `Render` |  Rendert einen Frame mit dem Scheitelpunkt und den Pixel-Shadern. | 

Der Unterordner **Shaders** enthält vier standardshaderimplementierungen:

|  Shader  |  Erläuterung | 
|----------|----------|
|  `GeometryShader.hlsl` |  Ein Pass-Through, bei dem die Geometrie unverändert bleibt. | 
|  `PixelShader.hlsl` |  Durchläuft die Farbdaten. Die Farbdaten werden interpoliert und einem Pixel im rasterisierungsschritt zugewiesen. | 
|  `VertexShader.hlsl` |  Einfacher Shader für die Verarbeitung von Scheitel Punkten auf der GPU. | 
|  `VPRTVertexShader.hlsl` |  Einfacher Shader für die Verarbeitung von Scheitel Punkten auf der GPU, die für Windows Mixed Reality-Stereo Rendering optimiert ist. | 

`VertexShaderShared.hlsl`enthält gemeinsamen Code, `VertexShader.hlsl` der `VPRTVertexShader.hlsl`von und gemeinsam verwendet wird.

Die Shader werden kompiliert, wenn das Projekt erstellt wird, und Sie werden in die Methode " **spinningcuberenderer:: createdevicedependentresources** " geladen.

## <a name="interact-with-your-holograms"></a>Interagieren mit ihren holograms

Benutzereingaben werden in der **spatialinputhandler** -Klasse verarbeitet, die eine <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">spatialinteraktionmanager</a> -Instanz abruft und das <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a> -Ereignis abonniert. Dies ermöglicht das Erkennen der Luft tippen Bewegung und anderer räumlicher Eingabeereignisse.

## <a name="update-holographic-content"></a>Holographic-Inhalt aktualisieren

Ihre Mixed Reality-APP wird in einer Spiel Schleife aktualisiert, die standardmäßig in der **Update** -Methode `AppMain.cpp`in implementiert wird. Die **Update** -Methode aktualisiert Szenen Objekte, wie z. b. den drehenden Cube, und gibt ein <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> -Objekt zurück, das verwendet wird, um aktuelle Ansichts-und Projektions Matrizen zu erhalten und die Austausch Kette darzustellen.

Die  Rendermethode `AppMain.cpp` in nimmt den <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a> an und rendert den aktuellen Frame entsprechend der aktuellen APP und dem räumlichen Positions Zustand für jede Holographic-Kamera.

## <a name="see-also"></a>Siehe auch
* [Abrufen eines HolographicSpace-Objekts](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">Holographicspace</a>
* [Rendern in DirectX](rendering-in-directx.md)
* [Verwenden von Visual Studio zum Bereitstellen und Debuggen](using-visual-studio.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Verwenden von XAML mit holographischen DirectX-Apps](using-xaml-with-holographic-directx-apps.md)
