---
title: Schreiben einer Holographic Remoting-Remote-App
description: Durch das Erstellen einer auf einem Remote Computer gerenderten Remoting-Remote Anwendung für die Remote-app kann an hololens 2 gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 53f370dc32b4fe56eb610b6e5687022e0908f7a8
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866860"
---
# <a name="writing-a-holographic-remoting-remote-app"></a>Schreiben einer Holographic Remoting-Remote-App

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer Remote Anwendung für hololens 2 beschrieben. Für Remote Anwendungen für **hololens (1st Gen)** muss das nuget-Paketversion **1. x. x**verwendet werden. Dies bedeutet, dass für hololens 2 geschriebene Remote Anwendungen nicht mit hololens 1 und umgekehrt kompatibel sind. Die Dokumentation für hololens 1 finden Sie [hier](add-holographic-remoting.md).

Wenn Sie eine Holographic Remoting-Remote-app erstellen, können Remote Inhalte, die auf einem Remote Computer gerendert werden, an hololens 2 gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann. Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".

Holographic Remoting ermöglicht es einer APP, hololens 2 mit Holographic-Inhalten zu erreichen, die auf einem Desktop-PC oder auf einem UWP-Gerät (z. b. der Xbox One) gerendert werden, und ermöglicht so den Zugriff auf mehr Systemressourcen und ermöglicht die Integration [von in vorhandene](app-views.md) Desktop-PC-Software. Eine Remote-app empfängt einen Eingabedaten Strom von hololens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens 2. Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt. Holographic-Remoting wird mithilfe eines nuget-Pakets zu einer Desktop-oder UWP-app hinzugefügt. Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert.

Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit. Die Player-App kann die Latenzzeit in Echtzeit melden.

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte Desktop-oder UWP-APP, die auf die Windows Mixed Reality-API abzielt. Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung](directx-development-overview.md). Die [Projektvorlage C++ Holographic](creating-a-holographic-directx-project.md) ist ein guter Ausgangspunkt.

>[!IMPORTANT]
>Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)erstellt werden. Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer nicht optimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden. Bei Verwendung von C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment der Standard.



## <a name="get-the-holographic-remoting-nuget-package"></a>Holen Sie sich das Holographic Remoting-nuget-Paket.

Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**
3. Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".
4. Wählen Sie **Microsoft. Holographic. Remoting**aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.
6. Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung. Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.

>[!NOTE]
>Version **1. x. x** des nuget-Pakets ist weiterhin für Entwickler verfügbar, die auf hololens 1 abzielen möchten. Weitere Informationen finden [Sie unter Hinzufügen von Holographic Remoting (hololens (1st Gen))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Erstellen des Remote Kontexts

Als ersten Schritt sollte die Anwendung einen Remote Kontext erstellen.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>Holographic Remoting funktioniert durch das Ersetzen der Windows Mixed Reality-Laufzeit, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit. Dies erfolgt während der Erstellung des Remote Kontexts. Aus diesem Grund kann jeder beliebige Windows Mixed Reality-API-Aufrufe vor dem Erstellen des Remote Kontexts zu unerwartetem Verhalten führen. Die empfohlene Vorgehensweise besteht darin, den Remote Kontext so früh wie möglich zu erstellen, bevor Sie mit jeder gemischten Reality-API interagieren. Erstellen oder Abrufen von Objekten, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, vor dem Aufrufen von "" mit Objekten, die später erstellt oder abgerufen werden.

Als nächstes muss der holografische Speicherplatz erstellt werden. Das Angeben eines corewindow ist nicht erforderlich. Desktop-Apps, die nicht über ein corewindow verfügen, können nur einen übergeben ```nullptr``` .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Verbindung mit dem Gerät herstellen

Sobald die Remote-app zum Rendern von Inhalten bereit ist, kann eine Verbindung mit dem Gerät hergestellt werden.

Die Verbindung kann auf zwei Arten erreicht werden.
1) Die Remote-app stellt eine Verbindung zum Player her, der auf dem Gerät ausgeführt wird.
2) Der Player, der auf dem Gerät ausgeführt wird, stellt eine Verbindung zur Remote-app her

Zum Herstellen einer Verbindung zwischen der Remote-app und hololens 2 müssen Sie die- ```Connect``` Methode im Remote Kontext mit dem Hostnamen und dem Port angeben. Der von Holographic Remoting Player verwendete Port ist **8265**.

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Wie bei jeder C++/WinRT-API ```Connect``` könnte eine WinRT:: hresult_error ausgelöst werden, die behandelt werden muss.

>[!TIP]
>Um die Verwendung der [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) -sprach Projektion zu vermeiden, kann die Datei ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` im Holographic Remoting-nuget-Paket eingeschlossen werden. Sie enthält Deklarationen der zugrunde liegenden COM-Schnittstellen. Die Verwendung von C++/WinRT wird jedoch empfohlen.

Das Lauschen auf eingehende Verbindungen in der Remote-app kann durch Aufrufen der- ```Listen``` Methode erfolgen. Der Handshake-Port und der Transporttyp können während dieses Aufrufes angegeben werden. Der Handshake-Port wird für den ersten Handshake verwendet. Die Daten werden dann über den transportport gesendet. Standardmäßig werden **8265** und **8266** verwendet.

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.

## <a name="handling-remoting-specific-events"></a>Behandeln von Remoting-spezifischen Ereignissen

Der Remote Kontext macht drei Ereignisse verfügbar, die für die Überwachung des Zustands einer Verbindung wichtig sind.
1) Onconnected: wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) Ontrennt: wird ausgelöst, wenn eine etablierte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) Onlistening: beim lauschen auf eingehende Verbindungen wird gestartet.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Außerdem kann der Verbindungsstatus mithilfe der- ```ConnectionState``` Eigenschaft im Remote Kontext abgefragt werden.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Behandeln von sprach Ereignissen

Mithilfe der Remote Sprachschnittstelle ist es möglich, sprach Trigger bei hololens 2 zu registrieren und Sie Remote mit der Remote Anwendung zu verbinden.

Dieser zusätzliche Member ist erforderlich, um den Status der Remote Sprache zu verfolgen.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Zuerst muss die Remote Sprachschnittstelle abgerufen werden.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Mithilfe einer asynchronen Hilfsmethode können Sie dann die Remote Sprache initialisieren. Dies sollte asynchron erfolgen, da die Initialisierung eine beträchtliche Zeit in Anspruch nehmen kann. Parallelitäts [-und asynchrone Vorgänge mit C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) erläutert, wie asynchrone Funktionen mit C++ erstellt werden können/WinRT.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Es gibt zwei Möglichkeiten zum Angeben von Ausdrücken, die erkannt werden sollen.
1) Spezifikation in einer Sprachgrammatik-XML-Datei. Weitere Informationen finden [Sie unter Erstellen einer grundlegenden XML-Grammatik](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .
2) Geben Sie an, indem Sie Sie im Wörterbuch Vektor an übergeben ```ApplyParameters``` .

Innerhalb des onerkenzedspeech-Rückrufs können die sprach Ereignisse verarbeitet werden:

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Vorschau der lokal gestreuten Inhalte

Um denselben Inhalt in der Remote-app anzuzeigen, der an das Gerät gesendet wird, kann das- ```OnSendFrame``` Ereignis des Remote Kontexts verwendet werden. Das- ```OnSendFrame``` Ereignis wird jedes Mal ausgelöst, wenn die Holographic Remoting-Bibliothek den aktuellen Frame an das Remote Gerät sendet. Dies ist der ideale Zeitpunkt, um den Inhalt zu übernehmen und ihn im Desktop-oder UWP-Fenster zu blitten.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>Tiefen neuprojektion

Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)unterstützt Holographic Remoting die [tiefen neuprojektion](hologram-stability.md#reprojection). Dies erfordert zusätzlich zum Farb Puffer, dass auch der tiefen Puffer von der Remote Anwendung auf die hololens 2 gestreamt wird. Standardmäßig ist das tiefen Puffer Streaming aktiviert und so konfiguriert, dass die Hälfte der Auflösung des Farb Puffers verwendet wird. Dies kann wie folgt geändert werden:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Beachten Sie, dass, wenn Standardwerte nicht verwendet werden sollten, ```ConfigureDepthVideoStream``` vor dem Herstellen einer Verbindung mit den hololens 2 aufgerufen werden muss. Der beste Ort ist direkt, nachdem Sie den Remote Kontext erstellt haben. Mögliche Werte für depthbufferstreamresolution:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Deaktiviert (mit Version [2.1.3](holographic-remoting-version-history.md#v2.1.3) hinzugefügt und wird verwendet, wenn kein zusätzlicher ausführungsvideostream erstellt wird)

Beachten Sie, dass die Verwendung eines tiefen Puffers für die vollständige Auflösung auch die Bandbreitenanforderungen beeinflusst und in dem maximalen Bandbreitenwert berücksichtigt werden muss, der für bereitgestellt wird ```CreateRemoteContext``` .

Neben dem Konfigurieren der Auflösung müssen Sie auch einen tiefen Puffer über [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)übertragen.

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

Um zu überprüfen, ob die Tiefe Reprojektion auf hololens 2 korrigiert wird, können Sie über das Geräte Portal eine tiefen Schnellansicht aktivieren. Weitere Informationen finden Sie unter über [Prüfen der Tiefe festgelegt wurde](hologram-stability.md#verifying-depth-is-set-correctly) .

## <a name="optional-custom-data-channels"></a>Optional: benutzerdefinierte Datenkanäle

Benutzerdefinierte Datenkanäle können zum Senden von Benutzerdaten über die bereits festgelegte Remote Verbindung verwendet werden. Weitere Informationen finden Sie unter [benutzerdefinierte Datenkanäle](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Benutzerdefinierte Holographic Remoting-Datenkanäle](holographic-remoting-custom-data-channels.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
