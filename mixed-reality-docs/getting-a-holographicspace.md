---
title: Abrufen einer HolographicSpace
description: Erläutert die HolographicSpace-API, ein Kernkonzept für holographic Rendering und räumliche Eingabe.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, "corewindow", räumliche Eingabe, rendering und swap-Kette, holographic Frame, "Update"-Schleife, spielschleife, Verweisrahmen, Locatability, Beispielcode, exemplarische Vorgehensweise
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605084"
---
# <a name="getting-a-holographicspace"></a>Abrufen einer HolographicSpace

Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> Klasse ist das Portal in die Welt der holographic. Immersive Rendering steuert, stellt Kameradaten und ermöglicht den Zugriff auf den spatial Argumentation APIs. Erstellen Sie eine für Ihre UWP-app <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">"corewindow"</a> oder Ihre Win32-app-HWND.

## <a name="set-up-the-holographic-space"></a>Einrichten des holographic Speicherplatzes

Erstellen des Objekts holographic Speicherplatz ist der erste Schritt bei der Erstellung Ihrer Windows Mixed Reality-app. Herkömmliche Windows-apps, die in einer Direct3D-SwapChain erstellt, die für das Fenster "Core" ihrer Anwendung Ansicht gerendert werden. Dieser SwapChain wird ein Slate-Objekt in der holografischen Benutzeroberfläche angezeigt. Ihre Anwendungsansicht statt 2D Slate holographic können, erstellen Sie ein holographic Speicherplatz für das Fenster "Core" anstatt einer Swapkette erläutert. Darstellen von holographic Frames, die von diesem holographic Bereich erstellt werden, stellt Ihre app in Full-Screen-Rendering-Modus.

Für eine **UWP-app** [beginnend mit der *Holographic DirectX 11-App (Universelles Windows) Vorlage*](creating-a-holographic-directx-project.md), suchen Sie nach diesen Code in die **"SetWindow"** die Methode in der AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Für eine **Win32-app** [beginnend mit der *BasicHologram* Win32-Beispiel](creating-a-holographic-directx-project.md#creating-a-win32-project), sehen Sie sich **App::CreateWindowAndHolographicSpace** für ein Beispiel für das Erstellen von einem HWND, und konvertieren Sie sie in eine immersive HWND durch das Erstellen eines zugeordneten <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

Nun, da Sie eine HolographicSpace für Ihre UWP "corewindow" oder Win32-HWND erhalten haben, verwenden Sie diese HolographicSpace behandeln holographic Kameras, Koordinatensysteme erstellen und holographic rendern. Der aktuelle holographic Speicherplatz wird an mehreren Stellen in der DirectX-Vorlage verwendet:
* Die **DeviceResources** Klasse benötigt, um Informationen aus dem HolographicSpace-Objekt zu erhalten, um das Direct3D-Gerät zu erstellen. Dies ist die DXGI-Adapter-ID, die die holographic Anzeige zugeordnet. Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> Klasse verwendet die Geräte von Ihrer app Direct3D 11 zum Erstellen und Verwalten von gerätebasierten Ressourcen, z. B. die Hintergrundpuffer für jede holographic Kamera. Wenn Sie möchten sehen, was diese Funktion im Hintergrund ist, finden Sie es in "deviceresources.cpp".
* Die Funktion **DeviceResources::InitializeUsingHolographicSpace** wird veranschaulicht, wie zum Abrufen des Adapters durch Aufrufen der LUID – und so ein Standardadapter ausgewählt, wenn keine bevorzugten Adapters angegeben wird.
* Die Hauptklasse der Anwendung verwendet die holographic Speicherplatz von **AppView::SetWindow** oder **App::CreateWindowAndHolographicSpace** für Updates und -Rendering.

>[!NOTE]
>Während in den folgenden Abschnitten ganz zu Funktionsnamen aus der Vorlage schweigen wie **AppView::SetWindow** , die wird davon ausgegangen, dass Sie aus der holografischen UWP-app-Vorlage gestartet, die Codeausschnitte, die Sie sehen, gelten gleichermaßen für UWP und Win32-apps.

Als Nächstes, wir analysieren dabei das Setup zu verarbeiten, die **SetHolographicSpace** ist verantwortlich für die in der AppMain-Klasse.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Kameraereignisse abonnieren Sie, erstellen Sie und entfernen Sie die Kamera-Ressourcen

Den Inhalt Ihrer app holographic befindet sich in der holografischen Speicherplatz und wird über eine oder mehrere holographic Kameras, die verschiedene Perspektiven in der Szene darstellen angezeigt. Nun, da Sie die holographic Speicherplatz verfügen, können Sie Daten für holographic Kameras erhalten.

Ihre app muss auf reagieren **CameraAdded** Ereignisse nach Ressourcen zu erstellen, sind spezifisch für, Kamera, wie Ihre Hintergrundpuffer Ansicht des Renderziels. Sehen Sie diesen Code in die **DeviceResources::SetHolographicSpace** Funktion von **AppView::SetWindow** , bevor die app keine holographic Frames erstellt:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Ihre app muss außerdem auf reagieren **CameraRemoved** Ereignisse durch die Freigabe von Ressourcen, die für diese Kamera erstellt wurden.

Von **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Die Ereignishandler müssen einige Aufgaben ausführen, um holographic reibungslos, fließt Rendering zu halten, damit Ihre app überhaupt rendern kann. Lesen Sie den Code und Kommentare für die Details: sehen Sie für **OnCameraAdded** und **OnCameraRemoved** in Ihrer main-Klasse, zu verstehen wie das **M_cameraResources** Zuordnung ist behandelt, indem **DeviceResources**.

Moment, wir konzentrieren uns AppMain und der Einrichtung, die sie zum Aktivieren Ihrer app holographic Kameras kennen. In diesem Sinn ist es wichtig, sich die beiden folgenden Anforderungen:

1. Für die **CameraAdded** -Ereignishandler die app kann asynchron Arbeit zum Erstellen von Ressourcen, und Laden von Medienobjekten, die für die neue holographic Kamera abgeschlossen. Apps, die mehr als einem Frame zum Abschließen dieser Arbeit annehmen sollte eine Verzögerung anfordern und die Verzögerung abgeschlossen, nachdem asynchron geladen; eine [PPL-Aufgabe](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) kann verwendet werden, um asynchrone Arbeit zu erledigen. Ihre app muss sicherstellen, dass es kann zu dieser Kamera direkt rendern, wenn den Ereignishandler vorhanden, oder bei Abschluss die Verzögerung. Beenden den Ereignishandler oder Abschluss der Verzögerung weist das System an, dass Ihre app jetzt für holographic Frames mit, Kamera, enthalten den Empfang bereit ist.

2. Wenn die app empfängt eine **CameraRemoved** Ereignis müssen sie alle Verweise auf die Hintergrundpuffer, und beenden die Funktion rechts sofort freigeben. Dies schließt renderzielansichten und alle anderen Ressourcen, die einen Verweis auf enthalten möglicherweise die [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). Die app muss auch sicherstellen, dass der Hintergrundpuffer nicht als ein Renderziel angefügt wird Siehe **CameraResources::ReleaseResourcesForBackBuffer**. Um die Geschwindigkeit von Dingen vorgehen können, kann Ihre app den Hintergrundpuffer freizugeben und starten Sie eine Aufgabe, um asynchron auf beliebige andere Arbeiten ausführen, die erforderlich ist, entfernen Sie diese Kamera. Die holographic app-Vorlage enthält PPL-Aufgabe, die Sie zu diesem Zweck verwenden können.

>[!NOTE]
>Wenn Sie möchten, um zu bestimmen, wenn eine Kamera hinzugefügte oder entfernte des Frames verwenden angezeigt werden die **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) und [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) Eigenschaften.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Erstellen Sie einen Bezugsrahmen für Ihre holographic Inhalte

Den Inhalt Ihrer app muss in positioniert werden eine [räumliche Koordinatensystem](coordinate-systems-in-directx.md) in die HolographicSpace gerendert werden soll. Das System bietet zwei primäre Frames als Referenz für die Sie verwenden können, um Koordinatensysteme für Ihre Hologramme herzustellen.

Es gibt zwei Arten von referenzbildern in Windows Holographic: Verweisen auf Frames, die an das Gerät angeschlossen und Referenz-Frames, die feststehend bleiben soll, wenn das Gerät über die Umgebung des Benutzers verschoben. Die holographic app-Vorlage einen Frame stationär Verweis wird standardmäßig verwendet; Dies ist eine der einfachsten Möglichkeiten zum Rendern von Hologramme Welt gesperrt.

Stationär referenzbildern dienen zur Stabilisierung Positionen in der Nähe des Geräts die aktuelle Position. Dies bedeutet, dass Koordinaten das. des Geräts zulässig sind, um etwas in Bezug auf die Umgebung des Benutzers abweichen, wie das Gerät, die Weitere Informationen zu den Platz um es herum lernt. Es gibt zwei Möglichkeiten, erstellen eine feststehende Verweisrahmen: das Koordinatensystem vom Abrufen der [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), oder verwenden Sie die Standardeinstellung <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Bei der Erstellung einer Windows Mixed Reality-app für immersive Headsets, ist der empfohlene Ausgangspunkt der [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), Informationen zu den Funktionen von der durch den Player abgenutzt immersive Kopfhörer bereit. Hier erfahren, wie die Standardeinstellung verwenden <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

Der räumliche Locator stellt das Gerät Windows Mixed Reality und verfolgt die Bewegung des Geräts und stellt die Koordinatensysteme, die relativ zu seinem Speicherort verstanden werden können.

From **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Erstellen Sie den Rahmen eines stationären Zustands Verweis einmal aus, wenn die app gestartet wird. Dies ist vergleichbar mit einem Koordinatensystem der Welt definieren, mit dem Ursprung des Geräts Position platziert werden, wenn die app gestartet wird. Dieser Verweis Frame wird nicht mit dem Gerät verschoben werden.

Von **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Alle referenzbildern sind Schwerkraft ausgerichtet, was bedeutet, dass die y-Achse zeigt, "up", um in Bezug auf die Umgebung des Benutzers. Da Windows "rechtshändige" Koordinatensysteme verwendet wird, stimmt die Richtung der Z-Achse, mit der "forward" Richtung an, die das Gerät mit Internetzugriff wird, wenn der Verweis Frame erstellt wird.

>[!NOTE]
>Wenn Ihre app die präzise Platzierung von einzelnen Hologramme erfordert, verwenden Sie eine <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> der einzelnen Hologramm an eine Position in der realen Welt verankert. Verwenden Sie z. B. einen räumlichen Anker auf, wenn der Benutzer gibt an, ein Punkt, besonders interessant sein. Anker Positionen werden nicht abweichen, aber sie angepasst werden können. In der Standardeinstellung, wenn ein Anker angepasst wird, erleichtert es seine Position an Ort über die nächsten mehrere Frames nachdem die Korrektur erfolgt ist. Je nach Anwendung in diesem Fall empfiehlt, behandeln die Anpassung auf andere Weise (z. B. durch Sie verzögern, bis die Hologramm aus der Ansicht ist). Die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> Eigenschaft und <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> Ereignisse ermöglichen diese Anpassungen.

## <a name="respond-to-locatability-changed-events"></a>Reagieren Sie auf Ereignisse der Locatability geändert

World-locked-Hologramme rendern, muss das Gerät selbst in der ganzen Welt zu finden sein. Dies sind nicht immer unbedingt möglich, da umgebungsbedingungen, und wenn dies der Fall ist, kann der Benutzer einen visuellen Hinweis für die nachverfolgung Unterbrechung erwarten. Dieser visuelle indikatore muss mithilfe des Geräts, anstatt stationär auf der ganzen Welt referenzbildern gerendert werden.

Ihre app kann anfordern, benachrichtigt werden, wenn die nachverfolgung aus irgendeinem Grund unterbrochen wird. Registrieren Sie für das Ereignis LocatabilityChanged erkennen, wann die Fähigkeit des Geräts auf sich selbst in die Welt Änderungen gesucht werden soll. Von **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Klicken Sie dann verwenden Sie dieses Ereignis, um zu ermitteln, wann Hologramme nicht stationär auf der ganzen Welt gerendert werden können.

## <a name="see-also"></a>Siehe auch
* [Rendern in DirectX](rendering-in-directx.md)
* [Koordinatensysteme im DirectX](coordinate-systems-in-directx.md)
