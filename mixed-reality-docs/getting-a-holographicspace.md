---
title: Erhalten eines holographicspace
description: Erläutert die holographicspace-API, ein Kernkonzept für das holografische Rendering und räumliche Eingaben.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographicspace, corewindow, räumliche Eingabe, Rendering, Austausch Kette, Holographic Frame, Update Schleife, Spiel Schleife, Frame der Referenz, loerability, Beispielcode, Exemplarische Vorgehensweise
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525444"
---
# <a name="getting-a-holographicspace"></a>Erhalten eines holographicspace

Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a> -Klasse ist Ihr Portal in der Holographic World. Es steuert das immersive Rendering, stellt Kameradaten bereit und ermöglicht den Zugriff auf APIs für räumliche Argumente. Sie erstellen einen für das <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">corewindow</a> ihrer UWP-APP oder das HWND ihrer Win32-app.

## <a name="set-up-the-holographic-space"></a>Einrichten des Holographic-Raums

Das Erstellen des Holographic Space-Objekts ist der erste Schritt beim Erstellen der Windows Mixed Reality-app. Herkömmliche Windows-apps werden in einer Direct3D-Swap-Kette gerenttet, die für das Kern Fenster ihrer Anwendungs Ansicht erstellt wurde. Diese austauschkette wird in der Holographic-Benutzeroberfläche als Slate angezeigt. Erstellen Sie einen holografischen Raum für das Kern Fenster anstelle einer Swapkette, um die Anwendungs Ansicht anstelle eines 2D-Slate zu verwenden. Durch das präsentieren von Holographic Frames, die von diesem holografischen Raum erstellt werden, wird Ihre APP in den Vollbild-Rendermodus versetzt.

Suchen Sie für eine **UWP-App** , [die mit der *Holographic DirectX 11-app (universelle Windows-Vorlage)* beginnt](creating-a-holographic-directx-project.md), in der **SetWindow** -Methode in appview. cpp nach diesem Code:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Sehen Sie sich für eine **Win32-App** , die mit [dem bsichologram Win32-Beispiel beginnt, den  ](creating-a-holographic-directx-project.md#creating-a-win32-project)Eintrag " **App:: Erstellungs windowandholographicspace** " an, um ein Beispiel dafür zu erhalten, wie ein HWND erstellt und anschließend in ein immersives HWND <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">konvertiert wird Holographicspace</a>:
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

Nachdem Sie nun einen holographicspace für das UWP-corewindow oder das Win32-HWND erhalten haben, verwenden Sie diesen holographicspace, um holografische Kameras zu verarbeiten, Koordinatensysteme zu erstellen und Holographic-Rendering durchzuführen. Der aktuelle holografische Raum wird an mehreren Stellen in der DirectX-Vorlage verwendet:
* Die **deviceresources** -Klasse muss Informationen aus dem holographicspace-Objekt erhalten, um das Direct3D-Gerät zu erstellen. Dies ist die DXGI-Adapter-ID, die der Holographic-Anzeige zugeordnet ist. Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a> -Klasse verwendet das Direct3D 11-Gerät Ihrer APP zum Erstellen und verwalten Geräte basierter Ressourcen, z. b. die Back Puffer für jede holografische Kamera. Wenn Sie wissen möchten, was diese Funktion im Hintergrund vornimmt, finden Sie Sie in deviceresources. cpp.
* Die Funktion **deviceresources:: initializeusingholographicspace** zeigt, wie Sie den Adapter abrufen, indem Sie die LUID – suchen und einen Standard Adapter auswählen, wenn kein bevorzugter Adapter angegeben wird.
* Die Hauptklasse der APP verwendet den Holographic-Speicherplatz aus **appview:: SetWindow** oder **App:: kreatewindowandholographicspace** für Updates und Rendering.

>[!NOTE]
>In den folgenden Abschnitten werden Funktionsnamen aus der Vorlage wie **appview:: SetWindow** erwähnt, die voraussetzen, dass Sie von der Holographic UWP-App-Vorlage aus begonnen haben. die Code Ausschnitte, die Sie sehen, gelten gleichermaßen für UWP-und Win32-apps.

Als nächstes betrachten wir den Setup Prozess, für den **setholographicspace** in der appmain-Klasse verantwortlich ist.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Kamera Ereignisse abonnieren, Kamera Ressourcen erstellen und entfernen

Der Holographic-Inhalt Ihrer APP befindet sich in seinem holografischen Raum und wird über eine oder mehrere Holographic-Kameras angezeigt, die verschiedene Perspektiven in der Szene darstellen. Nun, da Sie über den Holographic-Raum verfügen, können Sie Daten für Holographic-Kameras empfangen.

Ihre APP muss auf " **cameraadded** "-Ereignisse reagieren, indem Sie für diese kameraspezifische Ressourcen erstellt, wie z. b. die Ansicht "rückrenderziel". Sie können diesen Code in der **deviceresources:: setholographicspace** -Funktion sehen, die von **appview:: SetWindow** aufgerufen wird, bevor die APP Holographic Frames erstellt:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Ihre APP muss auch auf die **camerareverschoten** Ereignisse reagieren, indem Sie Ressourcen freigibt, die für diese Kamera erstellt wurden.

Aus **deviceresources:: CSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Die Ereignishandler müssen einige Aufgaben ausführen, um die reibungslose Ausführung des Holographic-Renderings zu gewährleisten, sodass Ihre APP überhaupt gerendert werden kann. Lesen Sie den Code und die Kommentare für die Details: Sie können in ihrer Hauptklasse nach **oncameraadded** und **oncamerareverschoden** Code suchen, um zu verstehen, wie die **m_cameraResources** Map von **deviceresources**verarbeitet wird.

Zurzeit konzentrieren wir uns auf appmain und das Setup, damit Ihre APP über Holographic-Kameras informiert werden kann. Vor diesem Hintergrund ist es wichtig, die folgenden beiden Anforderungen zu berücksichtigen:

1. Für den Ereignishandler " **cameraadded** " kann die APP asynchron ausgeführt werden, um das Erstellen von Ressourcen und das Laden von Assets für die neue Holographic-Kamera abzuschließen. Apps, die mehr als einen Frame zum Ausführen dieser Arbeit benötigen, sollten eine Verzögerung anfordern und die Verzögerung nach dem asynchronen Laden vervollständigen. eine [ppl-Aufgabe](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) kann verwendet werden, um asynchrone Aufgaben auszuführen. Ihre APP muss sicherstellen, dass Sie sofort an die Kamera gerehehbt, wenn Sie den Ereignishandler verlässt oder wenn Sie die Verzögerung abschließt. Das Beenden des Ereignis Handlers oder das Abschließen der Verzögerung weist das System darauf hin, dass Ihre APP nun bereit ist, Holographic Frames mit dieser Kamera zu empfangen.

2. Wenn die APP ein Ereignis  vom Typ "camerareverschobe" empfängt, muss Sie alle Verweise auf den Hintergrund Puffer freigeben und die Funktion sofort beenden. Dies schließt renderzielsichten und alle anderen Ressourcen ein, die möglicherweise einen Verweis auf die [idxgiresource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)enthalten. Außerdem muss die APP sicherstellen, dass der Hintergrund Puffer nicht als Renderziel angefügt wird, wie in **cameraresources:: releaseresourcesforbackbuffer**gezeigt. Um die Dinge zu beschleunigen, kann Ihre APP den Hintergrund Puffer freigeben und dann eine Aufgabe starten, um alle anderen Aufgaben, die zum Abfangen dieser Kamera erforderlich sind, asynchron abzuschließen. Die Vorlage für die Holographic-app enthält eine ppl-Aufgabe, die Sie zu diesem Zweck verwenden können.

>[!NOTE]
>Wenn Sie bestimmen möchten, wann eine hinzugefügte oder entfernte Kamera im Frame angezeigt wird, verwenden Sie die Eigenschaften **holographicframe** [addedkameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) und [removedkameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Erstellen eines Bezugsrahmens für den Holographic-Inhalt

Der Inhalt Ihrer APP muss in einem [räumlichen Koordinatensystem](coordinate-systems-in-directx.md) positioniert werden, das im holographicspace gerendert werden soll. Das System stellt zwei primäre Frame Frames bereit, mit denen Sie ein Koordinatensystem für Ihre Hologramme einrichten können.

Es gibt zwei Arten von Bezugs Frames in Windows Holographic: Verweis Rahmen, die an das Gerät angeschlossen sind, und Bezugsrahmen, die stationär bleiben, wenn das Gerät die Umgebung des Benutzers durchläuft. In der Holographic-App-Vorlage wird standardmäßig ein stationärer Verweis Rahmen verwendet. Dies ist eine der einfachsten Möglichkeiten zum Rendering von weltweit gesperrten holograms.

Stationäre Verweis Rahmen sind so konzipiert, dass Positionen in der Nähe des aktuellen Speicher Orts des Geräts stabilisiert werden. Dies bedeutet, dass Koordinaten, die sich weiter vom Gerät unterscheiden, in Bezug auf die Benutzerumgebung geringfügig abweichen dürfen, da das Gerät mehr über den Platz herum erfährt. Es gibt zwei Möglichkeiten, einen stationären Frame des Verweises zu erstellen: das Koordinatensystem aus der [räumlichen Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)abzurufen oder den standardspaticator zu verwenden. <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank"></a> Wenn Sie eine Windows Mixed Reality-App für immersive Headsets erstellen, wird als Ausgangspunkt die [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)empfohlen, in der auch Informationen über die Funktionen des immersiven Headsets, das vom Player getragen wird, bereitgestellt werden. Hier wird gezeigt, wie der standardzuordnerstandard verwendet wird. <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank"></a>

Der räumliche Serverlocatorpunkt stellt das Windows Mixed Reality-Gerät dar und verfolgt die Bewegung des Geräts und stellt Koordinatensysteme bereit, die relativ zum Speicherort verstanden werden können.

Aus **appmain:: onholographicdisplayisavailablechanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Erstellen Sie den stationären Verweis Rahmen einmal, wenn die APP gestartet wird. Dies ist analog zum Definieren eines Weltkoordinaten Systems, wobei der Ursprung an der Position des Geräts platziert wird, wenn die APP gestartet wird. Dieser Referenzrahmen bewegt sich nicht mit dem Gerät.

Aus **appmain:: abbildrfaden**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Alle Verweis Rahmen sind Schwerpunkte, was bedeutet, dass die y-Achse in Bezug auf die Umgebung des Benutzers "up" zeigt. Da Windows "rechtsseitige" Koordinatensysteme verwendet, stimmt die Richtung der – z-Achse mit der Vorwärtsrichtung überein, mit der das Gerät beim Erstellen des Verweis Rahmens konfrontiert wird.

>[!NOTE]
>Wenn Ihre APP eine exakte Platzierung einzelner holograms erfordert, verwenden Sie einen <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialanchor</a> , um das einzelne – Hologramm an eine Position in der realen Welt zu verankern. Verwenden Sie z. b. einen räumlichen Anker, wenn der Benutzer einen Punkt angibt, der ein besonderes Interesse sein soll. Anker Positionen werden nicht abweichen, Sie können jedoch angepasst werden. Wenn ein Anker angepasst wird, wird seine Position standardmäßig vor dem Abschluss der Korrektur in die nächsten Frames hineingebracht. Abhängig von Ihrer Anwendung können Sie in diesem Fall die Anpassung auf andere Weise verarbeiten (indem Sie Sie z. b. verzögern, bis das – Hologramm nicht mehr in der Ansicht ist). Die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">rawcoordinatesystem</a> -Eigenschaft und die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">rawcoordinatesystemadjusted</a> -Ereignisse ermöglichen diese Anpassungen.

## <a name="respond-to-locatability-changed-events"></a>Reagieren auf geänderte Ereignisse bei der Ereignis Änderung

Das Rendern von Welt gesperrten holograms erfordert, dass das Gerät sich selbst in der Welt finden kann. Dies ist möglicherweise aufgrund von Umgebungsbedingungen nicht immer möglich, und wenn dies der Fall ist, kann der Benutzer einen visuellen Hinweis auf die nach Verfolgungs Unterbrechung erwarten. Diese visuelle Anzeige muss mithilfe von Verweis Frames gerendert werden, die mit dem Gerät verbunden sind, anstatt auf der ganzen Welt.

Ihre APP kann anfordern, dass Sie benachrichtigt werden, wenn die Nachverfolgung aus irgendeinem Grund unterbrochen wird. Registrieren Sie sich für das loaufgeräterchanged-Ereignis, um zu erkennen, wann sich das Gerät in der Welt finden kann. Aus **appmain:: abbildrfaden:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Verwenden Sie dieses Ereignis dann, um zu bestimmen, wann holograms nicht auf der ganzen Welt gerendert werden können.

## <a name="see-also"></a>Siehe auch
* [Rendern in DirectX](rendering-in-directx.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
