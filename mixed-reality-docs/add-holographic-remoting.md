---
title: Hinzufügen von holographic remoting
description: Erläutert das Holographic Remoting zu verwenden, um Hologramme für eine HoloLens über das Netzwerk zu rendern.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, holographic Remoting, remote-Rendering, rendering, HoloLens, remote-Hologramme Netzwerk
ms.openlocfilehash: 1e9567976bad1e2b72e95feca292bf3475893230
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270356"
---
# <a name="add-holographic-remoting"></a>Hinzufügen von holographic remoting

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

HoloLens-Entwickler, die mit Holographic Remoting müssen ihre apps, damit sie kompatibel mit HoloLens 2 zu aktualisieren.  Dies erfordert eine neue Version des Holographic Remoting-NuGet-Pakets, das nicht noch öffentlich verfügbar ist.  Wenn eine Anwendung mit HoloLens-NuGet-Paket für die Verbindung für den Spieler Holographic Remoting HoloLens 2 versucht, schlägt die Verbindung fehl.  Achten Sie auf dieser Seite für Updates, sobald die HoloLens-2-NuGet-Paket verfügbar ist.

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Hinzufügen von holographic Remoting auf dem Desktop oder dem UWP-app

Diese Seite beschreibt Holographic Remoting auf einem Desktop- oder UWP-app hinzufügen.

Holographic Remoting kann Ihre app eine HoloLens holographic Inhalt gehostet auf einem desktop-PC oder ein UWP-Gerät, z.B. der Xbox One, Zugriff auf mehr Systemressourcen und wodurch sie integrieren remote Ziel [immersive Ansichten](app-views.md) in vorhandene Desktop-PC-Software. Eine Remoting-Host-app empfängt einen Eingabedatenstrom aus einer HoloLens, Inhalt in eine virtuelle immersive Ansicht rendert und Inhalts-Frames an HoloLens streamt. Die Verbindung wird hergestellt mit WLAN-standard. Um Remoting zu verwenden, werden Sie mithilfe von NuGet-Paket hinzu holographic Remoting auf dem Desktop oder dem UWP-app und Schreiben von Code, um die Verbindung zu verarbeiten und in eine immersive Ansicht gerendert werden soll. Bibliotheken befinden sich im Codebeispiel enthält, die die Aufgabe verarbeiten Sie die Verbindung zum Gerät zu vereinfachen.

Eine typische Remotingverbindung müssen so niedrig wie der Latenz 50 ms beträgt. Die Player-app kann die Latenz in Echtzeit gemeldet.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

### <a name="get-the-remoting-nuget-packages"></a>Die Remoting-NuGet-Pakete erhalten

Führen Sie diese Schritte, um das NuGet-Paket für holographic Remoting abzurufen, und fügen Sie aus Ihrem Projekt einen Verweis hinzu:
1. Wechseln Sie zu Ihrem Projekt in Visual Studio.
2. Mit der rechten Maustaste auf den Projektknoten, und wählen Sie **NuGet-Pakete verwalten...**
3. Klicken Sie im Bereich, der angezeigt wird, auf **Durchsuchen** und suchen Sie nach "Holographic Remoting".
4. Wählen Sie **Microsoft.Holographic.Remoting** , und klicken Sie auf **installieren**.
5. Wenn die **Vorschau** Dialogfeld erscheint, klicken Sie auf **OK**.
6. Im nächste Dialogfeld, das angezeigt wird, ist die Lizenzbedingungen. Klicken Sie auf **akzeptieren** , den Lizenzvertrag zu akzeptieren.

### <a name="create-the-holographicstreamerhelpers"></a>Erstellen Sie die HolographicStreamerHelpers

Zunächst benötigen wir eine Instanz von HolographicStreamerHelpers. Fügen Sie diese auf die Klasse, die Remoting übernehmen wird.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Sie müssen auch zum Nachverfolgen des Status der Verbindung. Wenn Sie die Vorschau zu rendern möchten, müssen Sie eine Textur, in die kopiert haben. Außerdem benötigen einige Dinge wie einen verbindungsstatussperre, eine Möglichkeit zum Speichern von HoloLens, die IP-Adresse und so weiter.

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>HolographicStreamerHelpers zu initialisieren und eine Verbindung mit HoloLens

Zum Verbinden mit einem HoloLens-Gerät erstellen Sie eine Instanz des HolographicStreamerHelpers und eine Verbindung mit der Ziel-IP-Adresse. Sie müssen die video-Framegröße HoloLens Anzeigebreite und Höhe entsprechend festgelegt werden, da die Holographic Remoting-Bibliothek erwartet, dass die Encoder und Decoder Lösungen genau übereinstimmen.

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

Verbindung mit dem Gerät ist asynchron. Trennen Ihrer app benötigten Connect-Ereignishandler bereit und Frames Senden von Ereignissen.

Das OnConnected-Ereignis kann die Benutzeroberfläche aktualisiert, framerendering wird gestartet und so weiter. In unserem Codebeispiel desktop aktualisieren wir den Fenstertitel, mit der Meldung "verbunden".

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Das Ereignis OnDisconnected kann es sich um erneut eine Verbindung herzustellen, Aktualisierungen der Benutzeroberfläche usw. verarbeiten. In diesem Beispiel schließen wir wieder an, wenn ein vorübergehender Fehler vorliegt.

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

Wenn die Remoting-Komponenten bereit, um einen Frame zu senden ist, wird Ihre app Gelegenheit, stellen eine Kopie der Datei in die SendFrameEvent bereitgestellt. Hier kopieren wir den Rahmen einer SwapChain, damit wir es in einem Vorschaufenster angezeigt werden können.

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

### <a name="render-holographic-content"></a>Holographic Inhalt Rendern

Zum Rendern von Inhalt mithilfe von-Remoting, Sie richten Sie einen virtuellen "iframeworkview" in Ihrem Desktop oder UWP-app und holographic Frames von Remoting zu verarbeiten. Alle Windows Holographic-APIs werden verwendet, die die gleiche Weise wie durch diese anzeigen, aber es etwas anders eingerichtet ist.

Statt sie selbst zu erstellen, stammen Ihre Klasse HolographicRemotingHelpers die holographic Speicherplatz und Spracherkennung-Komponenten:

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Anstatt eine "Update"-Schleife in eine Run-Methode zu verwenden, geben Sie Tick-Updates von der Hauptschleife des Desktop oder UWP-app. Dadurch kann Ihr Desktop oder die UWP-app in die Steuerung der Verarbeitung von Nachrichten bleiben.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Die Anzeige der holographic app Tick() Methode abgeschlossen wird, eine Iteration des Updates, zeichnen, vorhanden Schleife wird.

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

Holographic app Ansicht aktualisieren, rendern und vorhanden Schleife entspricht genau dem beim Ausführen für HoloLens - es ist, außer dass Sie Zugriff auf eine viel größere Menge an Systemressourcen auf Ihrem desktop-PC haben. Sie können viele weitere Dreiecke zu rendern, haben weitere zeichnen übergibt, weitere Physik und Verwendung X64 Prozesse zum Laden von Inhalten, die erforderlich sind mehr als 2 GB RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Trennen und die Remotesitzung zu beenden

Um – z. B. trennen, klickt der Benutzer eine UI-Schaltfläche getrennt - 'Disconnect()' für die HolographicStreamerHelpers aufrufen, und klicken Sie dann das Objekt frei.

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

## <a name="get-the-remoting-player"></a>Abrufen des Remoting-Players

Der Player für Windows Holographic-Remoting wird als Endpunkt für apps zum Hosten von Remoting für die Verbindung in den Windows appstore angeboten. Rufen Sie die Windows Holographic-Remoting-Player finden Sie auf dem Windows appstore aus Ihrem HoloLens, suchen Sie nach Remoting, und herunterzuladen Sie die app. Die Remoting-Player enthält ein Feature zum Anzeigen von Statistiken auf dem Bildschirm, dies hilfreich, beim Hosten von Remoting-apps zu debuggen sein kann.

## <a name="notes-and-resources"></a>Versionshinweise und Ressourcen

Die holographic app-Ansicht benötigen eine Möglichkeit zum Bereitstellen von Ihrer app mit dem Direct3D-Gerät, die zum Initialisieren des holographic Speicherplatzes verwendet werden müssen. Ihre app sollte das Direct3D-Gerät verwenden, zu kopieren und den Vorschauframe anzuzeigen.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Codebeispiel:** Ein vollständiges Beispiel der Holographic Remoting-Code ist verfügbar, darunter eine holographic Anwendungsansicht, die mit Remoting und Remoting Hosten von Projekten für Win32-desktop, UWP DirectX und UWP mit XAML kompatibel ist. Um es zu erhalten, finden Sie hier:
* [Windows Holographic-Codebeispiel für das Remoting](https://github.com/Microsoft/HoloLensCompanionKit/)

**Beachten Sie zum Debuggen:** Die Bibliothek Holographic Remoting kann Ausnahmen auslösen. Diese Ausnahmen möglicherweise sichtbar, in Debugsitzungen, abhängig von den Einstellungen der Visual Studio-Ausnahme, die zur Zeit aktiv sind. Diese Ausnahmen werden intern von der Bibliothek Holographic Remoting abgefangen und können ignoriert werden.
