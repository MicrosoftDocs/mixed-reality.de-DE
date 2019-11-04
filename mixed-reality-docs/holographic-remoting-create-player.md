---
title: Schreiben eines benutzerdefinierten Holographic Remoting-Players
description: Indem Sie eine benutzerdefinierte Holographic Remoting Player-App erstellen, können Sie eine benutzerdefinierte Anwendung erstellen, mit der auf einem Remote Computer gerenderte Inhalte in den hololens 2 angezeigt werden können. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 982a3f42014d8f5eb9ba181247fee9825fb78371
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434318"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Schreiben einer benutzerdefinierten Holographic Remoting Player-App

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer benutzerdefinierten Player Anwendung für hololens 2 beschrieben. Für hololens 2 geschriebene benutzerdefinierte Player sind nicht kompatibel mit Host Anwendungen, die für hololens 1 geschrieben wurden. Dies bedeutet, dass beide Anwendungen das nuget-Paketversion **2. x. x**verwenden müssen.

Indem Sie eine benutzerdefinierte Holographic Remoting Player-App erstellen, können Sie eine benutzerdefinierte Anwendung erstellen, die auf einem Remote Computer auf den hololens 2 [immersive Ansichten](app-views.md) anzeigen kann. In diesem Artikel wird beschrieben, wie dies erreicht werden kann. Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".

Ein Holographic Remoting Player ermöglicht Ihrer APP das Anzeigen von Holographic-Inhalten, die auf einem Desktop-PC oder auf einem UWP-Gerät (z. b. der Xbox One) [gerendert](rendering.md) werden Eine Holographic Remoting Player-App streamt Eingabedaten an eine Holographic Remoting-Host Anwendung und empfängt eine immersive Ansicht als Video-und Audiodatenstrom. Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt. Um eine Player-App zu erstellen, verwenden Sie ein nuget-Paket zum Hinzufügen von Holographic Remoting zu ihrer UWP-APP und zum Schreiben von Code, um die Verbindung zu verarbeiten und eine immersive Ansicht anzuzeigen. 

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte UWP-APP, die bereits auf die Windows Mixed Reality-API abzielt. Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung](directx-development-overview.md). Wenn Sie keine vorhandene APP haben und von Grund auf neu beginnen möchten, ist die [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md) ein guter Ausgangspunkt.

>[!IMPORTANT]
>Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)erstellt werden. Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer suboptimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden. Bei Verwendung C++von/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment der Standard.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holen Sie sich das Holographic Remoting-nuget-Paket.

Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**
3. Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".
4. Wählen Sie **Microsoft. Holographic. Remoting**aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.
6. Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung. Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.

>[!IMPORTANT]
><a name="idl"></a>Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Ändern Sie die Datei "Package. appxmanifest" der Anwendung.

Die folgenden Schritte müssen für das Projekt ausgeführt werden, damit die Anwendung die vom nuget-Paket hinzugefügte Microsoft. Holographic. appremoting. dll erkennt:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datei " **Package. appxmanifest** ", und wählen Sie **Öffnen mit...**
2. **XML (Text)-Editor** auswählen und auf OK klicken
3. Fügen Sie der Datei die folgenden Zeilen hinzu, und speichern Sie Sie.
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Erstellen des Player Kontexts

Als ersten Schritt sollte die Anwendung einen Player Kontext erstellen.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic Remoting funktioniert durch das Ersetzen der Windows Mixed Reality-Laufzeit, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit. Dies erfolgt während der Erstellung des Player Kontexts. Aus diesem Grund kann jeder beliebige Windows Mixed Reality-API-Aufrufe vor dem Erstellen des Player Kontexts zu unerwartetem Verhalten führen. Die empfohlene Vorgehensweise besteht darin, den Player Kontext so früh wie möglich zu erstellen, bevor Sie mit jeder gemischten Reality-API interagieren. Mischen Sie niemals Objekte, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, bevor Sie ```PlayerContext::Create()``` mit Objekten erstellen, die später erstellt oder abgerufen werden.

Als nächstes kann der holographicspace durch Aufrufen von [holographicspace. createforcorewindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)erstellt werden.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>Verbindung mit dem Host herstellen

Sobald die Player-App zum Rendern von Inhalten bereit ist, kann eine Verbindung mit dem Host hergestellt werden.

Die Verbindung kann auf eine der folgenden Arten hergestellt werden:
1) Die Player-App auf hololens 2 stellt eine Verbindung mit der Host-App her.
2) Die Host-App stellt eine Verbindung mit der Player-App her, die auf hololens 2 ausgeführt wird

Zum Herstellen einer Verbindung zwischen der Player-App und dem Host wird die ```Connect```-Methode im Player Kontext aufgerufen, um den Hostnamen und den Port anzugeben. Der Standardport ist **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Wie bei jeder C++/WinRT-API könnte ```Connect``` eine WinRT:: hresult_error auslösen, die behandelt werden muss.

Um eingehende Verbindungen für die Player-App zu überwachen, können Sie die ```Listen```-Methode aufrufen. Der Handshake-Port und der Transporttyp können während dieses Aufrufes angegeben werden. Der Handshake-Port wird für den ersten Handshake verwendet. Die Daten werden dann über den transportport gesendet. Standardmäßig werden Portnummer **8265** und **8266** verwendet.

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Behandeln von Verbindungs bezogenen Ereignissen

Der ```PlayerContext``` macht drei Ereignisse verfügbar, um den Status der Verbindung zu überwachen.
1) Onconnected: wird ausgelöst, wenn eine Verbindung mit dem Host erfolgreich hergestellt wurde.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) Ongetrennte: wird ausgelöst, wenn eine etablierte Verbindung beendet oder eine Verbindung nicht hergestellt werden konnte.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>Mögliche ```ConnectionFailureReason``` Werte werden in der ```Microsoft.Holographic.AppRemoting.idl```- [Datei](#idl)dokumentiert.

3) Onlistening: beim lauschen auf eingehende Verbindungen wird gestartet.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Außerdem kann der Verbindungsstatus mithilfe der ```ConnectionState```-Eigenschaft im Player Kontext abgefragt werden.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Remote gerenderten Frame anzeigen

Um den Remote gerenderten Inhalt anzuzeigen, müssen Sie ```PlayerContext::BlitRemoteFrame()``` aufrufen, während Sie einen [holographicframe](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)rendern. 

```BlitRemoteFrame()``` erfordert, dass der Hintergrund Puffer für den aktuellen holographicframe als Renderziel gebunden ist. Der Hintergrund Puffer kann von [holographiccamer-deringparameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) über die [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) -Eigenschaft empfangen werden.

Beim Aufrufen von kopiert ```BlitRemoteFrame()``` den letzten empfangenen Frame aus der Host Anwendung in den BackBuffer von holographicframe. Außerdem wird der Fokus Punktsatz festgelegt, wenn die Remote Anwendung während des Renderings des Remote Frames einen Fokuspunkt angegeben hat.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()``` potenziell den Fokuspunkt für den aktuellen Frame überschreiben. 
>- Um einen Fall Back Fokuspunkt festzustellen, nennen Sie [holographiccamer-deringparameters:: setfocuspoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) vor der ```PlayerContext::BlitRemoteFrame()```. 
>- Um den Remote Fokuspunkt zu überschreiben, wenden Sie [holographiccamer-deringparameters:: setfocuspoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) nach ```PlayerContext::BlitRemoteFrame()```an.

Bei Erfolg gibt ```BlitRemoteFrame()``` ```BlitResult::Success_Color```zurück. Andernfalls wird die Fehlerursache zurückgegeben:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: fehlgeschlagen, da kein Remote Rahmen verfügbar ist.
- ```BlitResult::Failed_NoCamera```: fehlgeschlagen, da keine Kamera vorhanden ist.
- ```BlitResult::Failed_RemoteFrameTooOld```: fehlgeschlagen, da der Remote Rahmen zu alt ist (siehe playercontext:: blitremoteframetimeout-Eigenschaft).

## Optional: Set blitremoteframetimeout<a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimout``` wird ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9)unterstützt. 

Die ```PlayerContext::BlitRemoteFrameTimeout```-Eigenschaft gibt die Zeitspanne an, für die ein Remote Rahmen wieder verwendet wird, wenn kein neuer Remote Rahmen empfangen wird. 

Ein gängiger Anwendungsfall besteht darin, das blitremoteframe-Timeout zu aktivieren, um einen leeren Bildschirm anzuzeigen, wenn für einen bestimmten Zeitraum keine neuen Frames empfangen werden. Wenn diese Option aktiviert ist, kann der Rückgabetyp der ```BlitRemoteFrame``` Methode auch verwendet werden, um zu einem lokal gerenderten Fall Back Inhalt zu wechseln. 

Um das Timeout zu aktivieren, legen Sie den-Eigenschafts Wert auf eine Dauer gleich oder größer als 100 MS fest. Um das Timeout zu deaktivieren, legen Sie die-Eigenschaft auf die Dauer NULL fest. Wenn das Timeout aktiviert ist und für die festgelegte Dauer kein Remote Rahmen empfangen wird, schlägt blitremoteframe fehl und gibt ```Failed_RemoteFrameTooOld``` zurück, bis ein neuer Remote Rahmen empfangen wird.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Optional: Statistiken zum letzten Remote Rahmen erhalten

Zum Diagnostizieren von Leistungs-oder Netzwerkproblemen können Statistiken über den letzten Remote Rahmen über die ```PlayerContext::LastFrameStatistics```-Eigenschaft abgerufen werden. Statistiken werden während des Aufrufes [holographicframe aktualisiert::P "Ressentiments usingcurrentvorhersage](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)".

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Weitere Informationen finden Sie in der ```PlayerFrameStatistics```-Dokumentation in der ```Microsoft.Holographic.AppRemoting.idl```- [Datei](#idl).

## <a name="optional-custom-data-channels"></a>Optional: benutzerdefinierte Datenkanäle

Benutzerdefinierte Datenkanäle können zum Senden von Benutzerdaten über die bereits festgelegte Remote Verbindung verwendet werden. Weitere Informationen finden Sie unter [benutzerdefinierte Datenkanäle](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Benutzerdefinierte Holographic Remoting-Datenkanäle](holographic-remoting-custom-data-channels.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
