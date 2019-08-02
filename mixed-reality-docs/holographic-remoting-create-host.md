---
title: Schreiben einer Holographic Remoting-Host-App
description: Durch das Erstellen einer Holographic Remoting Host-APP, die auf einem Remote Computer gerendert wird, kann an hololens 2 gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 95cf98504f26e2362b3c4fd38e7d9228350798f3
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718064"
---
# <a name="writing-a-holographic-remoting-host-app"></a><span data-ttu-id="f1f0b-105">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="f1f0b-105">Writing a Holographic Remoting host app</span></span>

>[!IMPORTANT]
><span data-ttu-id="f1f0b-106">In diesem Dokument wird die Erstellung einer Host Anwendung für hololens 2 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-106">This document describes the creation of a host application for HoloLens 2.</span></span> <span data-ttu-id="f1f0b-107">Die Host Anwendung für **hololens 1** muss das nuget-Paketversion **1. x. x**verwenden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-107">Host application for **HoloLens 1** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="f1f0b-108">Dies bedeutet, dass für hololens 2 geschriebene Host Anwendungen nicht mit hololens 1 und umgekehrt kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-108">This implies that host applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="f1f0b-109">Die Dokumentation für hololens 1 finden Sie [hier](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="f1f0b-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="f1f0b-110">Durch das Erstellen einer Holographic Remoting Host-App können Remote Inhalte, die auf einem Remote Computer gerendert werden, an hololens 2 gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-110">By creating a Holographic Remoting host app remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="f1f0b-111">In diesem Artikel wird beschrieben, wie dies erreicht werden kann.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="f1f0b-112">Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".</span><span class="sxs-lookup"><span data-stu-id="f1f0b-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="f1f0b-113">Holographic Remoting ermöglicht es einer APP, hololens 2 mit Holographic-Inhalten zu erreichen, die auf einem Desktop-PC oder auf einem UWP-Gerät (z. b. der Xbox One) gehostet werden, und ermöglicht so den Zugriff auf mehr Systemressourcen und ermöglicht die Integration von [immersiven Remote Sichten](app-views.md) in vorhandene Desktop-PC-Software.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-113">Holographic remoting allows an app to target HoloLens 2 with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="f1f0b-114">Eine Remoting-Host-App empfängt einen Eingabedaten Strom von hololens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens 2.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-114">A remoting host app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="f1f0b-115">Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="f1f0b-116">Holographic-Remoting wird mithilfe eines nuget-Pakets zu einer Desktop-oder UWP-app hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="f1f0b-117">Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="f1f0b-118">Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="f1f0b-119">Die Player-App kann die Latenzzeit in Echtzeit melden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1f0b-120">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f1f0b-120">Prerequisites</span></span>

<span data-ttu-id="f1f0b-121">Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte Desktop-oder UWP-APP, die auf die Windows Mixed Reality-API abzielt.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="f1f0b-122">Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1f0b-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="f1f0b-123">Die [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md) ist ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f1f0b-124">Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="f1f0b-125">Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer nicht optimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-125">The use of a [single-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="f1f0b-126">Bei Verwendung C++von/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment der Standard.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="f1f0b-127">Holen Sie sich das Holographic Remoting-nuget-Paket.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="f1f0b-128">Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="f1f0b-129">Öffnen Sie das Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="f1f0b-130">Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="f1f0b-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="f1f0b-131">Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="f1f0b-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="f1f0b-132">Wählen Sie **Microsoft. Holographic. Remoting**aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="f1f0b-133">Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="f1f0b-134">Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="f1f0b-135">Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="f1f0b-136">Version **1. x. x** des nuget-Pakets ist weiterhin für Entwickler verfügbar, die auf hololens 1 abzielen möchten.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="f1f0b-137">Weitere Informationen finden [Sie unter Hinzufügen von Holographic Remoting (hololens 1)](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="f1f0b-137">For details see [Add Holographic Remoting (HoloLens 1)](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="f1f0b-138">Erstellen des Remote Kontexts</span><span class="sxs-lookup"><span data-stu-id="f1f0b-138">Create the remote context</span></span>

<span data-ttu-id="f1f0b-139">Als ersten Schritt sollte die Anwendung einen Remote Kontext erstellen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-139">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="f1f0b-140">Holographic Remoting funktioniert durch das Ersetzen der Windows Mixed Reality-Laufzeit, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="f1f0b-141">Dies erfolgt während der Erstellung des Remote Kontexts.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="f1f0b-142">Aus diesem Grund kann jeder beliebige Windows Mixed Reality-API-Aufrufe vor dem Erstellen des Remote Kontexts zu unerwartetem Verhalten führen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="f1f0b-143">Die empfohlene Vorgehensweise besteht darin, den Remote Kontext so früh wie möglich zu erstellen, bevor Sie mit jeder gemischten Reality-API interagieren.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="f1f0b-144">Erstellen oder Abrufen von Objekten, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, vor dem Aufrufen von "" mit Objekten, die später erstellt oder abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="f1f0b-145">Als nächstes muss der holografische Speicherplatz erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="f1f0b-146">Das Angeben eines corewindow ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="f1f0b-147">Desktop-Apps, die nicht über ein corewindow verfügen, können ```nullptr```nur einen übergeben.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="f1f0b-148">Verbindung mit dem Gerät herstellen</span><span class="sxs-lookup"><span data-stu-id="f1f0b-148">Connect to the device</span></span>

<span data-ttu-id="f1f0b-149">Sobald die Host-App zum Rendern von Inhalten bereit ist, kann eine Verbindung mit dem Gerät hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-149">Once the host app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="f1f0b-150">Die Verbindung kann auf zwei Arten erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="f1f0b-151">Die Host-App stellt eine Verbindung zum Player her, der auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-151">The host app connects to the player running on the device.</span></span>
2) <span data-ttu-id="f1f0b-152">Der auf dem Gerät ausgeführt wird, stellt eine Verbindung mit der Host-App her.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-152">The player running on the device connects to the host app.</span></span>

<span data-ttu-id="f1f0b-153">Zum Herstellen einer Verbindung zwischen der Host-APP und hololens 2 müssen ```Connect``` Sie die-Methode im Remote Kontext mit dem Hostnamen und dem Port angeben.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-153">To establish a connection from the host app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="f1f0b-154">Der von Holographic Remoting Player verwendete Port ist **8265**.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="f1f0b-155">Wie bei jeder C++/WinRT- ```Connect``` API könnte eine WinRT:: hresult_error-Ausnahme ausgelöst werden, die behandelt werden muss.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="f1f0b-156">Um die Verwendung [ C++der/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) -sprach Projektion ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` zu vermeiden, kann die Datei im Holographic Remoting-nuget-Paket eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-156">To avoid using [C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="f1f0b-157">Sie enthält Deklarationen der zugrunde liegenden COM-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="f1f0b-158">Die Verwendung von C++/WinRT wird jedoch empfohlen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="f1f0b-159">Das Lauschen auf eingehende Verbindungen auf der Host-App kann durch Aufrufen ```Listen``` der-Methode erfolgen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-159">Listening for incoming connections on the host app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="f1f0b-160">Der Handshake-Port und der Transporttyp können während dieses Aufrufes angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="f1f0b-161">Der Handshake-Port wird für den ersten Handshake verwendet.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="f1f0b-162">Die Daten werden dann über den transportport gesendet.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-162">The data is then send over the transport port.</span></span> <span data-ttu-id="f1f0b-163">Standardmäßig werden **8265** und **8266** verwendet.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-163">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="f1f0b-164">Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="f1f0b-165">Behandeln von Remoting-spezifischen Ereignissen</span><span class="sxs-lookup"><span data-stu-id="f1f0b-165">Handling Remoting specific events</span></span>

<span data-ttu-id="f1f0b-166">Der Remote Kontext macht drei Ereignisse verfügbar, die für die Überwachung des Zustands einer Verbindung wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="f1f0b-167">Onconnected: Wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="f1f0b-168">Ongetrennte: Wird ausgelöst, wenn eine etablierte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
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
3) <span data-ttu-id="f1f0b-169">Onlistening: Beim lauschen auf eingehende Verbindungen wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="f1f0b-170">Außerdem kann der Verbindungsstatus mithilfe der ```ConnectionState``` -Eigenschaft im Remote Kontext abgefragt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="f1f0b-171">Behandeln von sprach Ereignissen</span><span class="sxs-lookup"><span data-stu-id="f1f0b-171">Handling speech events</span></span>

<span data-ttu-id="f1f0b-172">Mithilfe der Remote Sprachschnittstelle ist es möglich, sprach Trigger bei hololens 2 zu registrieren und Sie Remote zur Host Anwendung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the host application.</span></span>

<span data-ttu-id="f1f0b-173">Dieser zusätzliche Member ist erforderlich, um den Status der Remote Sprache zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="f1f0b-174">Zuerst muss die Remote Sprachschnittstelle abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="f1f0b-175">Mithilfe einer asynchronen Hilfsmethode können Sie dann die Remote Sprache initialisieren.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="f1f0b-176">Dies sollte asynchron erfolgen, da die Initialisierung eine beträchtliche Zeit in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="f1f0b-177">[Parallelitäts-und asynchrone Vorgänge C++mit/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) erläutert, wie asynchrone Funktionen mit C++/WinRT. erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"en-US", grammarFile, dictionary);
}
```

<span data-ttu-id="f1f0b-178">Es gibt zwei Möglichkeiten zum Angeben von Ausdrücken, die erkannt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="f1f0b-179">Spezifikation in einer Sprachgrammatik-XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="f1f0b-180">Weitere Informationen finden [Sie unter Erstellen einer grundlegenden XML-Grammatik](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="f1f0b-180">See [How to create a basic XML Grammar](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="f1f0b-181">Geben Sie an, indem Sie Sie im Wörter ```ApplyParameters```Buch Vektor an übergeben.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="f1f0b-182">Innerhalb des onerkenzedspeech-Rückrufs können die sprach Ereignisse verarbeitet werden:</span><span class="sxs-lookup"><span data-stu-id="f1f0b-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="f1f0b-183">Vorschau der lokal gestreuten Inhalte</span><span class="sxs-lookup"><span data-stu-id="f1f0b-183">Preview streamed content locally</span></span>

<span data-ttu-id="f1f0b-184">Zum Anzeigen desselben Inhalts in der Host-APP, die an das Gerät gesendet wird ```OnSendFrame``` , kann das-Ereignis des Remote Kontexts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-184">To display the same content in the host app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="f1f0b-185">Das ```OnSendFrame``` -Ereignis wird jedes Mal ausgelöst, wenn die Holographic Remoting-Bibliothek den aktuellen Frame an das Remote Gerät sendet.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="f1f0b-186">Dies ist der ideale Zeitpunkt, um den Inhalt zu übernehmen und ihn im Desktop-oder UWP-Fenster zu blitten.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="optional-custom-data-channels"></a><span data-ttu-id="f1f0b-187">Optional: Benutzerdefinierte Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="f1f0b-187">Optional: Custom data channels</span></span>

<span data-ttu-id="f1f0b-188">Benutzerdefinierte Datenkanäle können zum Senden von Benutzerdaten über die bereits festgelegte Remote Verbindung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-188">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="f1f0b-189">Weitere Informationen finden Sie unter [benutzerdefinierte Datenkanäle](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="f1f0b-189">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1f0b-190">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f1f0b-190">See Also</span></span>
* [<span data-ttu-id="f1f0b-191">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="f1f0b-191">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f1f0b-192">Benutzerdefinierte Holographic-Remoting-Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="f1f0b-192">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="f1f0b-193">Einrichten einer sicheren Verbindung mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f1f0b-193">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="f1f0b-194">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f1f0b-194">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f1f0b-195">Software Lizenzbedingungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f1f0b-195">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f1f0b-196">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="f1f0b-196">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)