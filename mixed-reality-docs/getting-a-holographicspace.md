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
# <a name="getting-a-holographicspace"></a><span data-ttu-id="d7c56-104">Abrufen einer HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="d7c56-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="d7c56-105">Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> Klasse ist das Portal in die Welt der holographic.</span><span class="sxs-lookup"><span data-stu-id="d7c56-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="d7c56-106">Immersive Rendering steuert, stellt Kameradaten und ermöglicht den Zugriff auf den spatial Argumentation APIs.</span><span class="sxs-lookup"><span data-stu-id="d7c56-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="d7c56-107">Erstellen Sie eine für Ihre UWP-app <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">"corewindow"</a> oder Ihre Win32-app-HWND.</span><span class="sxs-lookup"><span data-stu-id="d7c56-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="d7c56-108">Einrichten des holographic Speicherplatzes</span><span class="sxs-lookup"><span data-stu-id="d7c56-108">Set up the holographic space</span></span>

<span data-ttu-id="d7c56-109">Erstellen des Objekts holographic Speicherplatz ist der erste Schritt bei der Erstellung Ihrer Windows Mixed Reality-app.</span><span class="sxs-lookup"><span data-stu-id="d7c56-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="d7c56-110">Herkömmliche Windows-apps, die in einer Direct3D-SwapChain erstellt, die für das Fenster "Core" ihrer Anwendung Ansicht gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="d7c56-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="d7c56-111">Dieser SwapChain wird ein Slate-Objekt in der holografischen Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d7c56-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="d7c56-112">Ihre Anwendungsansicht statt 2D Slate holographic können, erstellen Sie ein holographic Speicherplatz für das Fenster "Core" anstatt einer Swapkette erläutert.</span><span class="sxs-lookup"><span data-stu-id="d7c56-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="d7c56-113">Darstellen von holographic Frames, die von diesem holographic Bereich erstellt werden, stellt Ihre app in Full-Screen-Rendering-Modus.</span><span class="sxs-lookup"><span data-stu-id="d7c56-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="d7c56-114">Für eine **UWP-app** [beginnend mit der *Holographic DirectX 11-App (Universelles Windows) Vorlage*](creating-a-holographic-directx-project.md), suchen Sie nach diesen Code in die **"SetWindow"** die Methode in der AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="d7c56-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="d7c56-115">Für eine **Win32-app** [beginnend mit der *BasicHologram* Win32-Beispiel](creating-a-holographic-directx-project.md#creating-a-win32-project), sehen Sie sich **App::CreateWindowAndHolographicSpace** für ein Beispiel für das Erstellen von einem HWND, und konvertieren Sie sie in eine immersive HWND durch das Erstellen eines zugeordneten <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="d7c56-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="d7c56-116">Nun, da Sie eine HolographicSpace für Ihre UWP "corewindow" oder Win32-HWND erhalten haben, verwenden Sie diese HolographicSpace behandeln holographic Kameras, Koordinatensysteme erstellen und holographic rendern.</span><span class="sxs-lookup"><span data-stu-id="d7c56-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="d7c56-117">Der aktuelle holographic Speicherplatz wird an mehreren Stellen in der DirectX-Vorlage verwendet:</span><span class="sxs-lookup"><span data-stu-id="d7c56-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="d7c56-118">Die **DeviceResources** Klasse benötigt, um Informationen aus dem HolographicSpace-Objekt zu erhalten, um das Direct3D-Gerät zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d7c56-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="d7c56-119">Dies ist die DXGI-Adapter-ID, die die holographic Anzeige zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="d7c56-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="d7c56-120">Die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> Klasse verwendet die Geräte von Ihrer app Direct3D 11 zum Erstellen und Verwalten von gerätebasierten Ressourcen, z. B. die Hintergrundpuffer für jede holographic Kamera.</span><span class="sxs-lookup"><span data-stu-id="d7c56-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="d7c56-121">Wenn Sie möchten sehen, was diese Funktion im Hintergrund ist, finden Sie es in "deviceresources.cpp".</span><span class="sxs-lookup"><span data-stu-id="d7c56-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="d7c56-122">Die Funktion **DeviceResources::InitializeUsingHolographicSpace** wird veranschaulicht, wie zum Abrufen des Adapters durch Aufrufen der LUID – und so ein Standardadapter ausgewählt, wenn keine bevorzugten Adapters angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d7c56-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="d7c56-123">Die Hauptklasse der Anwendung verwendet die holographic Speicherplatz von **AppView::SetWindow** oder **App::CreateWindowAndHolographicSpace** für Updates und -Rendering.</span><span class="sxs-lookup"><span data-stu-id="d7c56-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="d7c56-124">Während in den folgenden Abschnitten ganz zu Funktionsnamen aus der Vorlage schweigen wie **AppView::SetWindow** , die wird davon ausgegangen, dass Sie aus der holografischen UWP-app-Vorlage gestartet, die Codeausschnitte, die Sie sehen, gelten gleichermaßen für UWP und Win32-apps.</span><span class="sxs-lookup"><span data-stu-id="d7c56-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="d7c56-125">Als Nächstes, wir analysieren dabei das Setup zu verarbeiten, die **SetHolographicSpace** ist verantwortlich für die in der AppMain-Klasse.</span><span class="sxs-lookup"><span data-stu-id="d7c56-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="d7c56-126">Kameraereignisse abonnieren Sie, erstellen Sie und entfernen Sie die Kamera-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d7c56-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="d7c56-127">Den Inhalt Ihrer app holographic befindet sich in der holografischen Speicherplatz und wird über eine oder mehrere holographic Kameras, die verschiedene Perspektiven in der Szene darstellen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d7c56-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="d7c56-128">Nun, da Sie die holographic Speicherplatz verfügen, können Sie Daten für holographic Kameras erhalten.</span><span class="sxs-lookup"><span data-stu-id="d7c56-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="d7c56-129">Ihre app muss auf reagieren **CameraAdded** Ereignisse nach Ressourcen zu erstellen, sind spezifisch für, Kamera, wie Ihre Hintergrundpuffer Ansicht des Renderziels.</span><span class="sxs-lookup"><span data-stu-id="d7c56-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="d7c56-130">Sehen Sie diesen Code in die **DeviceResources::SetHolographicSpace** Funktion von **AppView::SetWindow** , bevor die app keine holographic Frames erstellt:</span><span class="sxs-lookup"><span data-stu-id="d7c56-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="d7c56-131">Ihre app muss außerdem auf reagieren **CameraRemoved** Ereignisse durch die Freigabe von Ressourcen, die für diese Kamera erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="d7c56-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="d7c56-132">Von **DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="d7c56-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="d7c56-133">Die Ereignishandler müssen einige Aufgaben ausführen, um holographic reibungslos, fließt Rendering zu halten, damit Ihre app überhaupt rendern kann.</span><span class="sxs-lookup"><span data-stu-id="d7c56-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="d7c56-134">Lesen Sie den Code und Kommentare für die Details: sehen Sie für **OnCameraAdded** und **OnCameraRemoved** in Ihrer main-Klasse, zu verstehen wie das **M_cameraResources** Zuordnung ist behandelt, indem **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="d7c56-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="d7c56-135">Moment, wir konzentrieren uns AppMain und der Einrichtung, die sie zum Aktivieren Ihrer app holographic Kameras kennen.</span><span class="sxs-lookup"><span data-stu-id="d7c56-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="d7c56-136">In diesem Sinn ist es wichtig, sich die beiden folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="d7c56-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="d7c56-137">Für die **CameraAdded** -Ereignishandler die app kann asynchron Arbeit zum Erstellen von Ressourcen, und Laden von Medienobjekten, die für die neue holographic Kamera abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="d7c56-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="d7c56-138">Apps, die mehr als einem Frame zum Abschließen dieser Arbeit annehmen sollte eine Verzögerung anfordern und die Verzögerung abgeschlossen, nachdem asynchron geladen; eine [PPL-Aufgabe](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) kann verwendet werden, um asynchrone Arbeit zu erledigen.</span><span class="sxs-lookup"><span data-stu-id="d7c56-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="d7c56-139">Ihre app muss sicherstellen, dass es kann zu dieser Kamera direkt rendern, wenn den Ereignishandler vorhanden, oder bei Abschluss die Verzögerung.</span><span class="sxs-lookup"><span data-stu-id="d7c56-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="d7c56-140">Beenden den Ereignishandler oder Abschluss der Verzögerung weist das System an, dass Ihre app jetzt für holographic Frames mit, Kamera, enthalten den Empfang bereit ist.</span><span class="sxs-lookup"><span data-stu-id="d7c56-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="d7c56-141">Wenn die app empfängt eine **CameraRemoved** Ereignis müssen sie alle Verweise auf die Hintergrundpuffer, und beenden die Funktion rechts sofort freigeben.</span><span class="sxs-lookup"><span data-stu-id="d7c56-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="d7c56-142">Dies schließt renderzielansichten und alle anderen Ressourcen, die einen Verweis auf enthalten möglicherweise die [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="d7c56-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="d7c56-143">Die app muss auch sicherstellen, dass der Hintergrundpuffer nicht als ein Renderziel angefügt wird Siehe **CameraResources::ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="d7c56-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="d7c56-144">Um die Geschwindigkeit von Dingen vorgehen können, kann Ihre app den Hintergrundpuffer freizugeben und starten Sie eine Aufgabe, um asynchron auf beliebige andere Arbeiten ausführen, die erforderlich ist, entfernen Sie diese Kamera.</span><span class="sxs-lookup"><span data-stu-id="d7c56-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="d7c56-145">Die holographic app-Vorlage enthält PPL-Aufgabe, die Sie zu diesem Zweck verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d7c56-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="d7c56-146">Wenn Sie möchten, um zu bestimmen, wenn eine Kamera hinzugefügte oder entfernte des Frames verwenden angezeigt werden die **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) und [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="d7c56-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="d7c56-147">Erstellen Sie einen Bezugsrahmen für Ihre holographic Inhalte</span><span class="sxs-lookup"><span data-stu-id="d7c56-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="d7c56-148">Den Inhalt Ihrer app muss in positioniert werden eine [räumliche Koordinatensystem](coordinate-systems-in-directx.md) in die HolographicSpace gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="d7c56-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="d7c56-149">Das System bietet zwei primäre Frames als Referenz für die Sie verwenden können, um Koordinatensysteme für Ihre Hologramme herzustellen.</span><span class="sxs-lookup"><span data-stu-id="d7c56-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="d7c56-150">Es gibt zwei Arten von referenzbildern in Windows Holographic: Verweisen auf Frames, die an das Gerät angeschlossen und Referenz-Frames, die feststehend bleiben soll, wenn das Gerät über die Umgebung des Benutzers verschoben.</span><span class="sxs-lookup"><span data-stu-id="d7c56-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="d7c56-151">Die holographic app-Vorlage einen Frame stationär Verweis wird standardmäßig verwendet; Dies ist eine der einfachsten Möglichkeiten zum Rendern von Hologramme Welt gesperrt.</span><span class="sxs-lookup"><span data-stu-id="d7c56-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="d7c56-152">Stationär referenzbildern dienen zur Stabilisierung Positionen in der Nähe des Geräts die aktuelle Position.</span><span class="sxs-lookup"><span data-stu-id="d7c56-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="d7c56-153">Dies bedeutet, dass Koordinaten das. des Geräts zulässig sind, um etwas in Bezug auf die Umgebung des Benutzers abweichen, wie das Gerät, die Weitere Informationen zu den Platz um es herum lernt.</span><span class="sxs-lookup"><span data-stu-id="d7c56-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="d7c56-154">Es gibt zwei Möglichkeiten, erstellen eine feststehende Verweisrahmen: das Koordinatensystem vom Abrufen der [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), oder verwenden Sie die Standardeinstellung <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="d7c56-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="d7c56-155">Bei der Erstellung einer Windows Mixed Reality-app für immersive Headsets, ist der empfohlene Ausgangspunkt der [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), Informationen zu den Funktionen von der durch den Player abgenutzt immersive Kopfhörer bereit.</span><span class="sxs-lookup"><span data-stu-id="d7c56-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="d7c56-156">Hier erfahren, wie die Standardeinstellung verwenden <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="d7c56-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="d7c56-157">Der räumliche Locator stellt das Gerät Windows Mixed Reality und verfolgt die Bewegung des Geräts und stellt die Koordinatensysteme, die relativ zu seinem Speicherort verstanden werden können.</span><span class="sxs-lookup"><span data-stu-id="d7c56-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="d7c56-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="d7c56-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="d7c56-159">Erstellen Sie den Rahmen eines stationären Zustands Verweis einmal aus, wenn die app gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="d7c56-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="d7c56-160">Dies ist vergleichbar mit einem Koordinatensystem der Welt definieren, mit dem Ursprung des Geräts Position platziert werden, wenn die app gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="d7c56-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="d7c56-161">Dieser Verweis Frame wird nicht mit dem Gerät verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="d7c56-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="d7c56-162">Von **AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="d7c56-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="d7c56-163">Alle referenzbildern sind Schwerkraft ausgerichtet, was bedeutet, dass die y-Achse zeigt, "up", um in Bezug auf die Umgebung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="d7c56-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="d7c56-164">Da Windows "rechtshändige" Koordinatensysteme verwendet wird, stimmt die Richtung der Z-Achse, mit der "forward" Richtung an, die das Gerät mit Internetzugriff wird, wenn der Verweis Frame erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="d7c56-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="d7c56-165">Wenn Ihre app die präzise Platzierung von einzelnen Hologramme erfordert, verwenden Sie eine <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> der einzelnen Hologramm an eine Position in der realen Welt verankert.</span><span class="sxs-lookup"><span data-stu-id="d7c56-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="d7c56-166">Verwenden Sie z. B. einen räumlichen Anker auf, wenn der Benutzer gibt an, ein Punkt, besonders interessant sein.</span><span class="sxs-lookup"><span data-stu-id="d7c56-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="d7c56-167">Anker Positionen werden nicht abweichen, aber sie angepasst werden können.</span><span class="sxs-lookup"><span data-stu-id="d7c56-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="d7c56-168">In der Standardeinstellung, wenn ein Anker angepasst wird, erleichtert es seine Position an Ort über die nächsten mehrere Frames nachdem die Korrektur erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="d7c56-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="d7c56-169">Je nach Anwendung in diesem Fall empfiehlt, behandeln die Anpassung auf andere Weise (z. B. durch Sie verzögern, bis die Hologramm aus der Ansicht ist).</span><span class="sxs-lookup"><span data-stu-id="d7c56-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="d7c56-170">Die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> Eigenschaft und <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> Ereignisse ermöglichen diese Anpassungen.</span><span class="sxs-lookup"><span data-stu-id="d7c56-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="d7c56-171">Reagieren Sie auf Ereignisse der Locatability geändert</span><span class="sxs-lookup"><span data-stu-id="d7c56-171">Respond to locatability changed events</span></span>

<span data-ttu-id="d7c56-172">World-locked-Hologramme rendern, muss das Gerät selbst in der ganzen Welt zu finden sein.</span><span class="sxs-lookup"><span data-stu-id="d7c56-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="d7c56-173">Dies sind nicht immer unbedingt möglich, da umgebungsbedingungen, und wenn dies der Fall ist, kann der Benutzer einen visuellen Hinweis für die nachverfolgung Unterbrechung erwarten.</span><span class="sxs-lookup"><span data-stu-id="d7c56-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="d7c56-174">Dieser visuelle indikatore muss mithilfe des Geräts, anstatt stationär auf der ganzen Welt referenzbildern gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="d7c56-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="d7c56-175">Ihre app kann anfordern, benachrichtigt werden, wenn die nachverfolgung aus irgendeinem Grund unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="d7c56-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="d7c56-176">Registrieren Sie für das Ereignis LocatabilityChanged erkennen, wann die Fähigkeit des Geräts auf sich selbst in die Welt Änderungen gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="d7c56-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="d7c56-177">Von **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="d7c56-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="d7c56-178">Klicken Sie dann verwenden Sie dieses Ereignis, um zu ermitteln, wann Hologramme nicht stationär auf der ganzen Welt gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="d7c56-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7c56-179">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d7c56-179">See also</span></span>
* [<span data-ttu-id="d7c56-180">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="d7c56-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="d7c56-181">Koordinatensysteme im DirectX</span><span class="sxs-lookup"><span data-stu-id="d7c56-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
