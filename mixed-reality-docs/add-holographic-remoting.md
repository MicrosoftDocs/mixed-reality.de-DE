---
title: Hinzufügen von holographic remoting
description: Erläutert das Holographic Remoting zu verwenden, um Hologramme für eine HoloLens über das Netzwerk zu rendern.
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, holographic Remoting, remote-Rendering, rendering, HoloLens, remote-Hologramme Netzwerk
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829619"
---
# <a name="add-holographic-remoting"></a><span data-ttu-id="daf9d-104">Hinzufügen von holographic remoting</span><span class="sxs-lookup"><span data-stu-id="daf9d-104">Add holographic remoting</span></span>

## <a name="hololens-2"></a><span data-ttu-id="daf9d-105">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="daf9d-105">HoloLens 2</span></span>

> [!NOTE]
> <span data-ttu-id="daf9d-106">Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="daf9d-106">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="daf9d-107">HoloLens-Entwickler, die mit Holographic Remoting müssen ihre apps, damit sie kompatibel mit HoloLens 2 zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="daf9d-107">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span>  <span data-ttu-id="daf9d-108">Dies erfordert eine neue Version des Holographic Remoting-NuGet-Pakets, das nicht noch öffentlich verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="daf9d-108">This will require a new version of the Holographic Remoting NuGet package that is not publicly available yet.</span></span>  <span data-ttu-id="daf9d-109">Wenn eine Anwendung mit HoloLens-NuGet-Paket für die Verbindung für den Spieler Holographic Remoting HoloLens 2 versucht, schlägt die Verbindung fehl.</span><span class="sxs-lookup"><span data-stu-id="daf9d-109">If an application using the HoloLens NuGet package attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>  <span data-ttu-id="daf9d-110">Achten Sie auf dieser Seite für Updates, sobald die HoloLens-2-NuGet-Paket verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="daf9d-110">Watch this page for updates once the HoloLens 2 NuGet package is available.</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="daf9d-111">Hinzufügen von holographic Remoting auf dem Desktop oder dem UWP-app</span><span class="sxs-lookup"><span data-stu-id="daf9d-111">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="daf9d-112">Diese Seite beschreibt Holographic Remoting auf einem Desktop- oder UWP-app hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-112">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="daf9d-113">Holographic Remoting kann Ihre app eine HoloLens holographic Inhalt gehostet auf einem desktop-PC oder ein UWP-Gerät, z.B. der Xbox One, Zugriff auf mehr Systemressourcen und wodurch sie integrieren remote Ziel [immersive Ansichten](app-views.md) in vorhandene Desktop-PC-Software.</span><span class="sxs-lookup"><span data-stu-id="daf9d-113">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="daf9d-114">Eine Remoting-Host-app empfängt einen Eingabedatenstrom aus einer HoloLens, Inhalt in eine virtuelle immersive Ansicht rendert und Inhalts-Frames an HoloLens streamt.</span><span class="sxs-lookup"><span data-stu-id="daf9d-114">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="daf9d-115">Die Verbindung wird hergestellt mit WLAN-standard.</span><span class="sxs-lookup"><span data-stu-id="daf9d-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="daf9d-116">Um Remoting zu verwenden, werden Sie mithilfe von NuGet-Paket hinzu holographic Remoting auf dem Desktop oder dem UWP-app und Schreiben von Code, um die Verbindung zu verarbeiten und in eine immersive Ansicht gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="daf9d-116">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="daf9d-117">Bibliotheken befinden sich im Codebeispiel enthält, die die Aufgabe verarbeiten Sie die Verbindung zum Gerät zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-117">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="daf9d-118">Eine typische Remotingverbindung müssen so niedrig wie der Latenz 50 ms beträgt.</span><span class="sxs-lookup"><span data-stu-id="daf9d-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="daf9d-119">Die Player-app kann die Latenz in Echtzeit gemeldet.</span><span class="sxs-lookup"><span data-stu-id="daf9d-119">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="daf9d-120">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="daf9d-120">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="daf9d-121">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-121">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="daf9d-122">Die Remoting-NuGet-Pakete erhalten</span><span class="sxs-lookup"><span data-stu-id="daf9d-122">Get the remoting NuGet packages</span></span>

<span data-ttu-id="daf9d-123">Führen Sie diese Schritte, um das NuGet-Paket für holographic Remoting abzurufen, und fügen Sie aus Ihrem Projekt einen Verweis hinzu:</span><span class="sxs-lookup"><span data-stu-id="daf9d-123">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="daf9d-124">Wechseln Sie zu Ihrem Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="daf9d-124">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="daf9d-125">Mit der rechten Maustaste auf den Projektknoten, und wählen Sie **NuGet-Pakete verwalten...**</span><span class="sxs-lookup"><span data-stu-id="daf9d-125">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="daf9d-126">Klicken Sie im Bereich, der angezeigt wird, auf **Durchsuchen** und suchen Sie nach "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="daf9d-126">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="daf9d-127">Wählen Sie **Microsoft.Holographic.Remoting** , und klicken Sie auf **installieren**.</span><span class="sxs-lookup"><span data-stu-id="daf9d-127">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="daf9d-128">Wenn die **Vorschau** Dialogfeld erscheint, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="daf9d-128">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="daf9d-129">Im nächste Dialogfeld, das angezeigt wird, ist die Lizenzbedingungen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-129">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="daf9d-130">Klicken Sie auf **akzeptieren** , den Lizenzvertrag zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="daf9d-130">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="daf9d-131">Erstellen Sie die HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="daf9d-131">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="daf9d-132">Zunächst benötigen wir eine Instanz von HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="daf9d-132">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="daf9d-133">Fügen Sie diese auf die Klasse, die Remoting übernehmen wird.</span><span class="sxs-lookup"><span data-stu-id="daf9d-133">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="daf9d-134">Sie müssen auch zum Nachverfolgen des Status der Verbindung.</span><span class="sxs-lookup"><span data-stu-id="daf9d-134">You'll also need to track connection state.</span></span> <span data-ttu-id="daf9d-135">Wenn Sie die Vorschau zu rendern möchten, müssen Sie eine Textur, in die kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="daf9d-135">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="daf9d-136">Außerdem benötigen einige Dinge wie einen verbindungsstatussperre, eine Möglichkeit zum Speichern von HoloLens, die IP-Adresse und so weiter.</span><span class="sxs-lookup"><span data-stu-id="daf9d-136">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="daf9d-137">HolographicStreamerHelpers zu initialisieren und eine Verbindung mit HoloLens</span><span class="sxs-lookup"><span data-stu-id="daf9d-137">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="daf9d-138">Zum Verbinden mit einem HoloLens-Gerät erstellen Sie eine Instanz des HolographicStreamerHelpers und eine Verbindung mit der Ziel-IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="daf9d-138">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="daf9d-139">Sie müssen die video-Framegröße HoloLens Anzeigebreite und Höhe entsprechend festgelegt werden, da die Holographic Remoting-Bibliothek erwartet, dass die Encoder und Decoder Lösungen genau übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-139">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="daf9d-140">Verbindung mit dem Gerät ist asynchron.</span><span class="sxs-lookup"><span data-stu-id="daf9d-140">The device connection is asynchronous.</span></span> <span data-ttu-id="daf9d-141">Trennen Ihrer app benötigten Connect-Ereignishandler bereit und Frames Senden von Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-141">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="daf9d-142">Das OnConnected-Ereignis kann die Benutzeroberfläche aktualisiert, framerendering wird gestartet und so weiter.</span><span class="sxs-lookup"><span data-stu-id="daf9d-142">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="daf9d-143">In unserem Codebeispiel desktop aktualisieren wir den Fenstertitel, mit der Meldung "verbunden".</span><span class="sxs-lookup"><span data-stu-id="daf9d-143">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="daf9d-144">Das Ereignis OnDisconnected kann es sich um erneut eine Verbindung herzustellen, Aktualisierungen der Benutzeroberfläche usw. verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="daf9d-144">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="daf9d-145">In diesem Beispiel schließen wir wieder an, wenn ein vorübergehender Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="daf9d-145">In this example, we reconnect if there is a transient failure.</span></span>

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="daf9d-146">Wenn die Remoting-Komponenten bereit, um einen Frame zu senden ist, wird Ihre app Gelegenheit, stellen eine Kopie der Datei in die SendFrameEvent bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="daf9d-146">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="daf9d-147">Hier kopieren wir den Rahmen einer SwapChain, damit wir es in einem Vorschaufenster angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="daf9d-147">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="daf9d-148">Holographic Inhalt Rendern</span><span class="sxs-lookup"><span data-stu-id="daf9d-148">Render holographic content</span></span>

<span data-ttu-id="daf9d-149">Zum Rendern von Inhalt mithilfe von-Remoting, Sie richten Sie einen virtuellen "iframeworkview" in Ihrem Desktop oder UWP-app und holographic Frames von Remoting zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="daf9d-149">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="daf9d-150">Alle Windows Holographic-APIs werden verwendet, die die gleiche Weise wie durch diese anzeigen, aber es etwas anders eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="daf9d-150">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="daf9d-151">Statt sie selbst zu erstellen, stammen Ihre Klasse HolographicRemotingHelpers die holographic Speicherplatz und Spracherkennung-Komponenten:</span><span class="sxs-lookup"><span data-stu-id="daf9d-151">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="daf9d-152">Anstatt eine "Update"-Schleife in eine Run-Methode zu verwenden, geben Sie Tick-Updates von der Hauptschleife des Desktop oder UWP-app.</span><span class="sxs-lookup"><span data-stu-id="daf9d-152">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="daf9d-153">Dadurch kann Ihr Desktop oder die UWP-app in die Steuerung der Verarbeitung von Nachrichten bleiben.</span><span class="sxs-lookup"><span data-stu-id="daf9d-153">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="daf9d-154">Die Anzeige der holographic app Tick() Methode abgeschlossen wird, eine Iteration des Updates, zeichnen, vorhanden Schleife wird.</span><span class="sxs-lookup"><span data-stu-id="daf9d-154">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="daf9d-155">Holographic app Ansicht aktualisieren, rendern und vorhanden Schleife entspricht genau dem beim Ausführen für HoloLens - es ist, außer dass Sie Zugriff auf eine viel größere Menge an Systemressourcen auf Ihrem desktop-PC haben.</span><span class="sxs-lookup"><span data-stu-id="daf9d-155">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="daf9d-156">Sie können viele weitere Dreiecke zu rendern, haben weitere zeichnen übergibt, weitere Physik und Verwendung X64 Prozesse zum Laden von Inhalten, die erforderlich sind mehr als 2 GB RAM.</span><span class="sxs-lookup"><span data-stu-id="daf9d-156">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="daf9d-157">Trennen und die Remotesitzung zu beenden</span><span class="sxs-lookup"><span data-stu-id="daf9d-157">Disconnect and end the remote session</span></span>

<span data-ttu-id="daf9d-158">Um – z. B. trennen, klickt der Benutzer eine UI-Schaltfläche getrennt - 'Disconnect()' für die HolographicStreamerHelpers aufrufen, und klicken Sie dann das Objekt frei.</span><span class="sxs-lookup"><span data-stu-id="daf9d-158">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="daf9d-159">Abrufen des Remoting-Players</span><span class="sxs-lookup"><span data-stu-id="daf9d-159">Get the remoting player</span></span>

<span data-ttu-id="daf9d-160">Der Player für Windows Holographic-Remoting wird als Endpunkt für apps zum Hosten von Remoting für die Verbindung in den Windows appstore angeboten.</span><span class="sxs-lookup"><span data-stu-id="daf9d-160">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="daf9d-161">Rufen Sie die Windows Holographic-Remoting-Player finden Sie auf dem Windows appstore aus Ihrem HoloLens, suchen Sie nach Remoting, und herunterzuladen Sie die app.</span><span class="sxs-lookup"><span data-stu-id="daf9d-161">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="daf9d-162">Die Remoting-Player enthält ein Feature zum Anzeigen von Statistiken auf dem Bildschirm, dies hilfreich, beim Hosten von Remoting-apps zu debuggen sein kann.</span><span class="sxs-lookup"><span data-stu-id="daf9d-162">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="daf9d-163">Versionshinweise und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="daf9d-163">Notes and resources</span></span>

<span data-ttu-id="daf9d-164">Die holographic app-Ansicht benötigen eine Möglichkeit zum Bereitstellen von Ihrer app mit dem Direct3D-Gerät, die zum Initialisieren des holographic Speicherplatzes verwendet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-164">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="daf9d-165">Ihre app sollte das Direct3D-Gerät verwenden, zu kopieren und den Vorschauframe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-165">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="daf9d-166">**Codebeispiel:** Ein vollständiges Beispiel der Holographic Remoting-Code ist verfügbar, darunter eine holographic Anwendungsansicht, die mit Remoting und Remoting Hosten von Projekten für Win32-desktop, UWP DirectX und UWP mit XAML kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="daf9d-166">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="daf9d-167">Um es zu erhalten, finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="daf9d-167">To get it, go here:</span></span>
* [<span data-ttu-id="daf9d-168">Windows Holographic-Codebeispiel für das Remoting</span><span class="sxs-lookup"><span data-stu-id="daf9d-168">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="daf9d-169">**Beachten Sie zum Debuggen:** Die Bibliothek Holographic Remoting kann Ausnahmen auslösen.</span><span class="sxs-lookup"><span data-stu-id="daf9d-169">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="daf9d-170">Diese Ausnahmen möglicherweise sichtbar, in Debugsitzungen, abhängig von den Einstellungen der Visual Studio-Ausnahme, die zur Zeit aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="daf9d-170">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="daf9d-171">Diese Ausnahmen werden intern von der Bibliothek Holographic Remoting abgefangen und können ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="daf9d-171">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
