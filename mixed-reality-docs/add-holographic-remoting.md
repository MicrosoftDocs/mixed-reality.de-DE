---
title: Holographic-Remoting hinzufügen
description: Erläutert die Verwendung von Holographic Remoting zum Rendering von holograms in einem hololens über das Netzwerk.
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277708"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a>Holographic-Remoting hinzufügen (hololens (1. Gen))

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer Host Anwendung für hololens 1 beschrieben. Die Host Anwendung für **hololens (1st Gen)** muss das nuget-Paketversion **1. x. x**verwenden. Dies bedeutet, dass für hololens 1 geschriebene Host Anwendungen nicht mit hololens 2 und umgekehrt kompatibel sind.

## <a name="hololens-2"></a>HoloLens 2

Hololens-Entwickler, die Holographic Remoting verwenden, müssen Ihre apps aktualisieren, damit Sie mit hololens 2 kompatibel sind. Hierfür ist eine neue Version des nuget-Pakets "Holographic Remoting" erforderlich. Wenn eine Anwendung, die das Holographic Remoting-nuget-Paket mit einer Versionsnummer kleiner als 2.0.0.0 verwendet, versucht, eine Verbindung mit dem Holographic Remoting Player auf hololens 2 herzustellen, schlägt die Verbindung fehl.

>[!NOTE]
>Anleitungen für hololens 2 finden Sie [hier](holographic-remoting-create-host.md).


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Hinzufügen von Holographic Remoting zu Ihrer Desktop-oder UWP-App

Auf dieser Seite wird beschrieben, wie Sie Holographic Remoting zu einer Desktop-oder UWP-app hinzufügen.

Holographic Remoting ermöglicht der APP das Ausrichten von hololens mit Holographic-Inhalten, die auf einem Desktop-PC oder auf einem UWP-Gerät (z. b. der Xbox One) gehostet werden, und ermöglicht so den Zugriff auf mehr Systemressourcen und ermöglicht die Integration von [immersiven Remote Ansichten](app-views.md) in vorhandene Desktop-PC-Software. Eine Remoting-Host-App empfängt einen Eingabedaten Strom von einem hololens, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens. Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt. Um Remoting zu verwenden, verwenden Sie ein nuget-Paket zum Hinzufügen von Holographic Remoting zu Ihrer Desktop-oder UWP-APP und zum Schreiben von Code zum Verarbeiten der Verbindung und zum Rendering in einer immersiven Ansicht. Hilfsbibliotheken sind im Codebeispiel enthalten, das die Aufgabe der Verarbeitung der Geräte Verbindung vereinfacht.

Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit. Die Player-App kann die Latenzzeit in Echtzeit melden.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

### <a name="get-the-remoting-nuget-packages"></a>Remoting-nuget-Pakete

Führen Sie die folgenden Schritte aus, um das nuget-Paket für Holographic Remoting zu erhalten und einen Verweis aus dem Projekt hinzuzufügen:
1. Wechseln Sie zu Ihrem Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**
3. Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".
4. Wählen Sie **Microsoft. Holographic. Remoting** aus, und klicken Sie auf **Installieren**.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.
6. Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung. Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.

### <a name="create-the-holographicstreamerhelpers"></a>Erstellen der holographicstreamerhilfsprogramme

Zuerst benötigen wir eine Instanz von holographicstreamerhilfsprogramme. Fügen Sie der Klasse, die Remoting verarbeitet, dieses hinzu.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Außerdem müssen Sie den Verbindungsstatus nachverfolgen. Wenn Sie die Vorschau darstellen möchten, benötigen Sie eine Textur, in die Sie kopiert werden können. Außerdem benötigen Sie einige Dinge, wie z. b. eine Verbindungs Zustands Sperre, eine Möglichkeit, die IP-Adresse von hololens zu speichern, usw.

```cpp
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Initialisieren von holographicstreamerhilfsprogramme und verbinden mit hololens

Zum Herstellen einer Verbindung mit einem hololens-Gerät erstellen Sie eine Instanz von holographicstreamerhilfsprogramme, und stellen Sie eine Verbindung mit der Ziel-IP-Adresse her Sie müssen die Video Frame Größe so festlegen, dass Sie mit der hololens-Anzeigebreite und-Höhe übereinstimmt, da die Holographic Remoting-Bibliothek erwartet, dass die Encoder-und decoderauflösungen genau übereinstimmen.

```cpp
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

Die Geräte Verbindung ist asynchron. Ihre APP muss Ereignishandler für Connect-, Disconnect-und Frame Send-Ereignisse bereitstellen.

Das onconnected-Ereignis kann die Benutzeroberfläche aktualisieren, das Rendering starten usw. In unserem Desktop Codebeispiel aktualisieren wir den Fenstertitel mit der Meldung "Connected" (verbunden).

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Das ongetrennte-Ereignis kann die erneute Verbindung, Aktualisierungen der Benutzeroberfläche usw. verarbeiten. In diesem Beispiel wird die Verbindung wieder hergestellt, wenn ein vorübergehender Fehler vorliegt.

```cpp
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

Wenn die Remoting-Komponente bereit ist, einen Frame zu senden, bietet Ihre APP die Möglichkeit, eine Kopie davon im sendframeevent zu erstellen. Hier kopieren wir den Frame in eine Austausch Kette, damit wir ihn in einem Vorschaufenster anzeigen können.

```cpp
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

### <a name="render-holographic-content"></a>Holographic-Inhalt Wiedergabe

Zum Rendering von Inhalten mithilfe von Remoting richten Sie eine virtuelle iframeworkview innerhalb Ihrer Desktop-oder UWP-App ein und verarbeiten holografische Frames aus Remoting. Alle Windows Holographic-APIs werden in dieser Ansicht auf dieselbe Weise verwendet, Sie werden aber etwas anders eingerichtet.

Anstatt Sie selbst zu erstellen, stammen die Holographic Space-und Speech-Komponenten von ihrer holographikremumughelpers-Klasse:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Anstatt eine Update-Schleife innerhalb einer Run-Methode zu verwenden, stellen Sie Tick-Updates aus der Hauptschleife ihrer Desktop-oder UWP-App bereit. Dies ermöglicht es Ihrer Desktop-oder UWP-APP, die Kontrolle über die Nachrichtenverarbeitung zu behalten.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Die Tick ()-Methode der Holographic-App-Ansicht schließt eine Iterationen der Update-, Draw-, Present-Schleife ab.

```cpp
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

Die Holographic App View Update-, Rendering-und Present-Schleife ist identisch mit der Ausführung auf hololens, mit der Ausnahme, dass Sie Zugriff auf eine viel größere Menge an Systemressourcen auf Ihrem Desktop-PC haben. Sie können viele weitere Dreiecke darstellen, mehr Zeichnungs Pässe haben, mehr Physik durchführen und x64-Prozesse zum Laden von Inhalten verwenden, die mehr als 2 GB RAM erfordern.

### <a name="disconnect-and-end-the-remote-session"></a>Trennen und Beenden der Remote Sitzung

So trennen Sie die Verbindung, z. b. wenn der Benutzer auf eine UI-Schaltfläche klickt, um die Verbindung zu trennen (), für die holographicstreamerhilfsprogramme.

```cpp
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

## <a name="get-the-remoting-player"></a>Remoting Player

Der Windows Holographic Remoting Player wird im Windows App Store als Endpunkt für Remoting-Host-apps angeboten, mit denen eine Verbindung hergestellt werden kann. Um den Windows Holographic Remoting Player zu erhalten, besuchen Sie den Windows App Store aus ihren hololens, suchen Sie nach Remoting, und laden Sie die APP herunter. Der Remoting Player enthält ein Feature zum Anzeigen von Statistiken auf dem Bildschirm, was beim Debuggen von Remoting-Host-apps hilfreich sein kann.

## <a name="notes-and-resources"></a>Hinweise und Ressourcen

In der Ansicht der Holographic-app muss die APP über das Direct3D-Gerät bereitgestellt werden, das zum Initialisieren des Holographic-Raums verwendet werden muss. Ihre APP sollte dieses Direct3D-Gerät verwenden, um den Vorschau Rahmen zu kopieren und anzuzeigen.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Code Beispiel:** Ein vollständiges Holographic Remoting-Codebeispiel ist verfügbar, das eine Holographic-Anwendungs Ansicht enthält, die mit Remoting-und Remoting-Host Projekten für Desktop Win32, UWP DirectX und UWP mit XAML kompatibel ist. Weitere Informationen finden Sie hier:
* [Windows Holographic-Code Beispiel für Remoting](https://github.com/Microsoft/HoloLensCompanionKit/)

**Debughinweis:** Die Holographic Remoting-Bibliothek kann Ausnahmen der ersten Chance auslösen. Diese Ausnahmen sind möglicherweise in Debugsitzungen sichtbar, abhängig von den Visual Studio-Ausnahme Einstellungen, die zu diesem Zeitpunkt aktiv sind. Diese Ausnahmen werden intern von der Holographic Remoting-Bibliothek abgefangen und können ignoriert werden.
