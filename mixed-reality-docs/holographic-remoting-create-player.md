---
title: Schreiben eines benutzerdefinierten Holographic Remoting-Players
description: Indem Sie eine benutzerdefinierte Holographic Remoting Player-App erstellen, können Sie eine benutzerdefinierte Anwendung erstellen, mit der auf einem Remote Computer gerenderte Inhalte in den hololens 2 angezeigt werden können. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 1f8a0cbe0f6da88c0c5e5a695737d8694020635c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926653"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="2d656-105">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="2d656-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="2d656-106">In diesem Dokument wird die Erstellung einer benutzerdefinierten Player Anwendung für hololens 2 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2d656-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="2d656-107">Für hololens 2 geschriebene benutzerdefinierte Player sind nicht kompatibel mit Host Anwendungen, die für hololens 1 geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="2d656-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="2d656-108">Dies bedeutet, dass beide Anwendungen das nuget-Paketversion **2. x. x**verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="2d656-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="2d656-109">Indem Sie eine benutzerdefinierte Holographic Remoting Player-App erstellen, können Sie eine benutzerdefinierte Anwendung erstellen, die auf einem Remote Computer auf den hololens 2 [immersive Ansichten](app-views.md) anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="2d656-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="2d656-110">In diesem Artikel wird beschrieben, wie dies erreicht werden kann.</span><span class="sxs-lookup"><span data-stu-id="2d656-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="2d656-111">Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".</span><span class="sxs-lookup"><span data-stu-id="2d656-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="2d656-112">Ein Holographic Remoting Player ermöglicht Ihrer APP das Anzeigen von Holographic-Inhalten, die auf einem Desktop-PC oder auf einem UWP-Gerät (z. b. der Xbox One) [gerendert](rendering.md) werden</span><span class="sxs-lookup"><span data-stu-id="2d656-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="2d656-113">Eine Holographic Remoting Player-App streamt Eingabedaten an eine Holographic Remoting-Host Anwendung und empfängt eine immersive Ansicht als Video-und Audiodatenstrom.</span><span class="sxs-lookup"><span data-stu-id="2d656-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="2d656-114">Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt.</span><span class="sxs-lookup"><span data-stu-id="2d656-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="2d656-115">Um eine Player-App zu erstellen, verwenden Sie ein nuget-Paket zum Hinzufügen von Holographic Remoting zu ihrer UWP-APP und zum Schreiben von Code, um die Verbindung zu verarbeiten und eine immersive Ansicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2d656-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="2d656-116">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2d656-116">Prerequisites</span></span>

<span data-ttu-id="2d656-117">Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte UWP-APP, die bereits auf die Windows Mixed Reality-API abzielt.</span><span class="sxs-lookup"><span data-stu-id="2d656-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="2d656-118">Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d656-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="2d656-119">Wenn Sie keine vorhandene APP haben und von Grund auf neu beginnen möchten, ist die [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md) ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="2d656-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="2d656-120">Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="2d656-121">Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer suboptimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="2d656-122">Wenn Sie C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) verwenden, ist ein Multithread-Apartment der Standard.</span><span class="sxs-lookup"><span data-stu-id="2d656-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="2d656-123">Holen Sie sich das Holographic Remoting-nuget-Paket.</span><span class="sxs-lookup"><span data-stu-id="2d656-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="2d656-124">Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d656-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="2d656-125">Öffnen Sie das Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d656-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="2d656-126">Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="2d656-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="2d656-127">Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="2d656-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="2d656-128">Wählen Sie **Microsoft. Holographic. Remoting**aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="2d656-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="2d656-129">Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d656-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="2d656-130">Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung.</span><span class="sxs-lookup"><span data-stu-id="2d656-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="2d656-131">Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="2d656-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="2d656-132">Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="2d656-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="2d656-133">Ändern Sie die Datei "Package. appxmanifest" der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="2d656-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="2d656-134">Die folgenden Schritte müssen für das Projekt ausgeführt werden, damit die Anwendung die vom nuget-Paket hinzugefügte Microsoft. Holographic. appremoting. dll erkennt:</span><span class="sxs-lookup"><span data-stu-id="2d656-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="2d656-135">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datei " **Package. appxmanifest** ", und wählen Sie **Öffnen mit...**</span><span class="sxs-lookup"><span data-stu-id="2d656-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="2d656-136">**XML (Text)-Editor** auswählen und auf OK klicken</span><span class="sxs-lookup"><span data-stu-id="2d656-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="2d656-137">Fügen Sie der Datei die folgenden Zeilen hinzu, und speichern Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="2d656-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="2d656-138">Erstellen des Player Kontexts</span><span class="sxs-lookup"><span data-stu-id="2d656-138">Create the player context</span></span>

<span data-ttu-id="2d656-139">Als ersten Schritt sollte die Anwendung einen Player Kontext erstellen.</span><span class="sxs-lookup"><span data-stu-id="2d656-139">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="2d656-140">Holographic Remoting funktioniert durch das Ersetzen der Windows Mixed Reality-Laufzeit, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="2d656-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="2d656-141">Dies erfolgt während der Erstellung des Player Kontexts.</span><span class="sxs-lookup"><span data-stu-id="2d656-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="2d656-142">Aus diesem Grund kann jeder beliebige Windows Mixed Reality-API-Aufrufe vor dem Erstellen des Player Kontexts zu unerwartetem Verhalten führen.</span><span class="sxs-lookup"><span data-stu-id="2d656-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="2d656-143">Die empfohlene Vorgehensweise besteht darin, den Player Kontext so früh wie möglich zu erstellen, bevor Sie mit jeder gemischten Reality-API interagieren.</span><span class="sxs-lookup"><span data-stu-id="2d656-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="2d656-144">Mischen Sie niemals Objekte, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, bevor Sie ```PlayerContext::Create()``` mit Objekten erstellen, die später erstellt oder abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="2d656-145">Als nächstes kann der holographicspace durch Aufrufen von [holographicspace. createforcorewindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="2d656-146">Verbindung mit dem Host herstellen</span><span class="sxs-lookup"><span data-stu-id="2d656-146">Connect to the host</span></span>

<span data-ttu-id="2d656-147">Sobald die Player-App zum Rendern von Inhalten bereit ist, kann eine Verbindung mit dem Host hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="2d656-148">Die Verbindung kann auf eine der folgenden Arten hergestellt werden:</span><span class="sxs-lookup"><span data-stu-id="2d656-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="2d656-149">Die Player-App auf hololens 2 stellt eine Verbindung mit der Host-App her.</span><span class="sxs-lookup"><span data-stu-id="2d656-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="2d656-150">Die Host-App stellt eine Verbindung mit der Player-App her, die auf hololens 2 ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="2d656-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="2d656-151">Zum Herstellen einer Verbindung zwischen der Player-App und dem Host wird die ```Connect```-Methode im Player Kontext aufgerufen, um den Hostnamen und den Port anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2d656-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="2d656-152">Der Standardport ist **8265**.</span><span class="sxs-lookup"><span data-stu-id="2d656-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="2d656-153">Wie bei jeder C++/WinRT-API könnte ```Connect``` einen WinRT:: hresult_error auslösen, der behandelt werden muss.</span><span class="sxs-lookup"><span data-stu-id="2d656-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="2d656-154">Um eingehende Verbindungen für die Player-App zu überwachen, können Sie die ```Listen```-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2d656-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="2d656-155">Der Handshake-Port und der Transporttyp können während dieses Aufrufes angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="2d656-156">Der Handshake-Port wird für den ersten Handshake verwendet.</span><span class="sxs-lookup"><span data-stu-id="2d656-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="2d656-157">Die Daten werden dann über den transportport gesendet.</span><span class="sxs-lookup"><span data-stu-id="2d656-157">The data is then send over the transport port.</span></span> <span data-ttu-id="2d656-158">Standardmäßig werden Portnummer **8265** und **8266** verwendet.</span><span class="sxs-lookup"><span data-stu-id="2d656-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="2d656-159">Behandeln von Verbindungs bezogenen Ereignissen</span><span class="sxs-lookup"><span data-stu-id="2d656-159">Handling connection related events</span></span>

<span data-ttu-id="2d656-160">Der ```PlayerContext``` macht drei Ereignisse verfügbar, um den Status der Verbindung zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="2d656-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="2d656-161">Onconnected: wird ausgelöst, wenn eine Verbindung mit dem Host erfolgreich hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="2d656-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="2d656-162">Ongetrennte: wird ausgelöst, wenn eine etablierte Verbindung beendet oder eine Verbindung nicht hergestellt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="2d656-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="2d656-163">Mögliche ```ConnectionFailureReason``` Werte werden in der ```Microsoft.Holographic.AppRemoting.idl```- [Datei](#idl)dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="2d656-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="2d656-164">Onlistening: beim lauschen auf eingehende Verbindungen wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="2d656-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="2d656-165">Außerdem kann der Verbindungsstatus mithilfe der ```ConnectionState```-Eigenschaft im Player Kontext abgefragt werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="2d656-166">Remote gerenderten Frame anzeigen</span><span class="sxs-lookup"><span data-stu-id="2d656-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="2d656-167">Um den Remote gerenderten Inhalt anzuzeigen, müssen Sie ```PlayerContext::BlitRemoteFrame()``` aufrufen, während Sie einen [holographicframe](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)rendern.</span><span class="sxs-lookup"><span data-stu-id="2d656-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="2d656-168">```BlitRemoteFrame()``` erfordert, dass der Hintergrund Puffer für den aktuellen holographicframe als Renderziel gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="2d656-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="2d656-169">Der Hintergrund Puffer kann von [holographiccamer-deringparameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) über die [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) -Eigenschaft empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="2d656-170">Beim Aufrufen von kopiert ```BlitRemoteFrame()``` den letzten empfangenen Frame aus der Host Anwendung in den BackBuffer von holographicframe.</span><span class="sxs-lookup"><span data-stu-id="2d656-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="2d656-171">Außerdem wird der Fokus Punktsatz festgelegt, wenn die Remote Anwendung während des Renderings des Remote Frames einen Fokuspunkt angegeben hat.</span><span class="sxs-lookup"><span data-stu-id="2d656-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="2d656-172">```PlayerContext::BlitRemoteFrame()``` potenziell den Fokuspunkt für den aktuellen Frame überschreiben.</span><span class="sxs-lookup"><span data-stu-id="2d656-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="2d656-173">Um einen Fall Back Fokuspunkt anzugeben, nennen Sie [holographiccamerarenderingparameters:: setfocuspoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) vor der ```PlayerContext::BlitRemoteFrame()```.</span><span class="sxs-lookup"><span data-stu-id="2d656-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="2d656-174">Um den Remote Fokuspunkt zu überschreiben, wenden Sie [holographiccamer-deringparameters:: setfocuspoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) nach ```PlayerContext::BlitRemoteFrame()```an.</span><span class="sxs-lookup"><span data-stu-id="2d656-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="2d656-175">Bei Erfolg gibt ```BlitRemoteFrame()``` ```BlitResult::Success_Color```zurück.</span><span class="sxs-lookup"><span data-stu-id="2d656-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="2d656-176">Andernfalls wird die Fehlerursache zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="2d656-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="2d656-177">```BlitResult::Failed_NoRemoteFrameAvailable```: fehlgeschlagen, da kein Remote Rahmen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2d656-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="2d656-178">```BlitResult::Failed_NoCamera```: fehlgeschlagen, da keine Kamera vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2d656-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="2d656-179">```BlitResult::Failed_RemoteFrameTooOld```: fehlgeschlagen, da der Remote Rahmen zu alt ist (siehe playercontext:: blitremoteframetimeout-Eigenschaft).</span><span class="sxs-lookup"><span data-stu-id="2d656-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

## <span data-ttu-id="2d656-180">Optional: Set blitremoteframetimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="2d656-180">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="2d656-181">```PlayerContext::BlitRemoteFrameTimeout``` wird ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9)unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2d656-181">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="2d656-182">Die ```PlayerContext::BlitRemoteFrameTimeout```-Eigenschaft gibt die Zeitspanne an, für die ein Remote Rahmen wieder verwendet wird, wenn kein neuer Remote Rahmen empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="2d656-182">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="2d656-183">Ein gängiger Anwendungsfall besteht darin, das blitremoteframe-Timeout zu aktivieren, um einen leeren Bildschirm anzuzeigen, wenn für einen bestimmten Zeitraum keine neuen Frames empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-183">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="2d656-184">Wenn diese Option aktiviert ist, kann der Rückgabetyp der ```BlitRemoteFrame``` Methode auch verwendet werden, um zu einem lokal gerenderten Fall Back Inhalt zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="2d656-184">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="2d656-185">Um das Timeout zu aktivieren, legen Sie den-Eigenschafts Wert auf eine Dauer gleich oder größer als 100 MS fest.</span><span class="sxs-lookup"><span data-stu-id="2d656-185">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="2d656-186">Um das Timeout zu deaktivieren, legen Sie die-Eigenschaft auf die Dauer NULL fest.</span><span class="sxs-lookup"><span data-stu-id="2d656-186">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="2d656-187">Wenn das Timeout aktiviert ist und für die festgelegte Dauer kein Remote Rahmen empfangen wird, schlägt blitremoteframe fehl und gibt ```Failed_RemoteFrameTooOld``` zurück, bis ein neuer Remote Rahmen empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="2d656-187">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="2d656-188">Optional: Statistiken zum letzten Remote Rahmen erhalten</span><span class="sxs-lookup"><span data-stu-id="2d656-188">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="2d656-189">Zum Diagnostizieren von Leistungs-oder Netzwerkproblemen können Statistiken über den letzten Remote Rahmen über die ```PlayerContext::LastFrameStatistics```-Eigenschaft abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-189">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="2d656-190">Statistiken werden während des Aufrufes [holographicframe aktualisiert::P "Ressentiments usingcurrentvorhersage](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)".</span><span class="sxs-lookup"><span data-stu-id="2d656-190">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="2d656-191">Weitere Informationen finden Sie in der ```PlayerFrameStatistics```-Dokumentation in der ```Microsoft.Holographic.AppRemoting.idl```- [Datei](#idl).</span><span class="sxs-lookup"><span data-stu-id="2d656-191">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="2d656-192">Optional: benutzerdefinierte Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="2d656-192">Optional: Custom data channels</span></span>

<span data-ttu-id="2d656-193">Benutzerdefinierte Datenkanäle können zum Senden von Benutzerdaten über die bereits festgelegte Remote Verbindung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2d656-193">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="2d656-194">Weitere Informationen finden Sie unter [benutzerdefinierte Datenkanäle](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="2d656-194">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d656-195">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2d656-195">See Also</span></span>
* [<span data-ttu-id="2d656-196">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="2d656-196">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="2d656-197">Benutzerdefinierte Holographic Remoting-Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="2d656-197">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="2d656-198">Einrichten einer sicheren Verbindung mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="2d656-198">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="2d656-199">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="2d656-199">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="2d656-200">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="2d656-200">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="2d656-201">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="2d656-201">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
