---
title: Schreiben einer Holographic Remoting-Remote-app
description: Durch das Erstellen einer auf einem Remote Computer gerenderten Remoting-Remote Anwendung für die Remote-app kann an hololens 2 gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 76e37499fd32a82e6846c6c7cac1a292ef6b553a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092322"
---
# <a name="writing-a-holographic-remoting-remote-app"></a><span data-ttu-id="80db4-105">Schreiben einer Holographic Remoting-Remote-app</span><span class="sxs-lookup"><span data-stu-id="80db4-105">Writing a Holographic Remoting remote app</span></span>

>[!IMPORTANT]
><span data-ttu-id="80db4-106">In diesem Dokument wird die Erstellung einer Remote Anwendung für hololens 2 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="80db4-106">This document describes the creation of a remote application for HoloLens 2.</span></span> <span data-ttu-id="80db4-107">Für Remote Anwendungen für **hololens (1st Gen)** muss das nuget-Paketversion **1. x. x**verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="80db4-108">Dies bedeutet, dass für hololens 2 geschriebene Remote Anwendungen nicht mit hololens 1 und umgekehrt kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="80db4-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="80db4-109">Die Dokumentation für hololens 1 finden Sie [hier](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="80db4-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="80db4-110">Wenn Sie eine Holographic Remoting-Remote-app erstellen, können Remote Inhalte, die auf einem Remote Computer gerendert werden, an hololens 2 gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="80db4-111">In diesem Artikel wird beschrieben, wie dies erreicht werden kann.</span><span class="sxs-lookup"><span data-stu-id="80db4-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="80db4-112">Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".</span><span class="sxs-lookup"><span data-stu-id="80db4-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="80db4-113">Holographic Remoting ermöglicht es einer APP, hololens 2 mit Holographic-Inhalten zu erreichen, die auf einem Desktop-PC oder auf einem UWP-Gerät (z. b. der Xbox One) gerendert werden, und ermöglicht so den Zugriff auf mehr Systemressourcen und ermöglicht die Integration [von in vorhandene](app-views.md) Desktop-PC-Software.</span><span class="sxs-lookup"><span data-stu-id="80db4-113">Holographic remoting allows an app to target HoloLens 2 with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="80db4-114">Eine Remote-app empfängt einen Eingabedaten Strom von hololens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens 2.</span><span class="sxs-lookup"><span data-stu-id="80db4-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="80db4-115">Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt.</span><span class="sxs-lookup"><span data-stu-id="80db4-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="80db4-116">Holographic-Remoting wird mithilfe eines nuget-Pakets zu einer Desktop-oder UWP-app hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="80db4-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="80db4-117">Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert.</span><span class="sxs-lookup"><span data-stu-id="80db4-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="80db4-118">Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit.</span><span class="sxs-lookup"><span data-stu-id="80db4-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="80db4-119">Die Player-App kann die Latenzzeit in Echtzeit melden.</span><span class="sxs-lookup"><span data-stu-id="80db4-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80db4-120">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="80db4-120">Prerequisites</span></span>

<span data-ttu-id="80db4-121">Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte Desktop-oder UWP-APP, die auf die Windows Mixed Reality-API abzielt.</span><span class="sxs-lookup"><span data-stu-id="80db4-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="80db4-122">Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="80db4-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="80db4-123">Die [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md) ist ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="80db4-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="80db4-124">Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="80db4-125">Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer nicht optimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="80db4-126">Wenn Sie C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) verwenden, ist ein Multithread-Apartment der Standard.</span><span class="sxs-lookup"><span data-stu-id="80db4-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="80db4-127">Holen Sie sich das Holographic Remoting-nuget-Paket.</span><span class="sxs-lookup"><span data-stu-id="80db4-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="80db4-128">Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="80db4-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="80db4-129">Öffnen Sie das Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80db4-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="80db4-130">Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="80db4-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="80db4-131">Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="80db4-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="80db4-132">Wählen Sie **Microsoft. Holographic. Remoting**aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="80db4-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="80db4-133">Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="80db4-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="80db4-134">Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung.</span><span class="sxs-lookup"><span data-stu-id="80db4-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="80db4-135">Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="80db4-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="80db4-136">Version **1. x. x** des nuget-Pakets ist weiterhin für Entwickler verfügbar, die auf hololens 1 abzielen möchten.</span><span class="sxs-lookup"><span data-stu-id="80db4-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="80db4-137">Weitere Informationen finden [Sie unter Hinzufügen von Holographic Remoting (hololens (1st Gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="80db4-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="80db4-138">Erstellen des Remote Kontexts</span><span class="sxs-lookup"><span data-stu-id="80db4-138">Create the remote context</span></span>

<span data-ttu-id="80db4-139">Als ersten Schritt sollte die Anwendung einen Remote Kontext erstellen.</span><span class="sxs-lookup"><span data-stu-id="80db4-139">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="80db4-140">Holographic Remoting funktioniert durch das Ersetzen der Windows Mixed Reality-Laufzeit, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="80db4-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="80db4-141">Dies erfolgt während der Erstellung des Remote Kontexts.</span><span class="sxs-lookup"><span data-stu-id="80db4-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="80db4-142">Aus diesem Grund kann jeder beliebige Windows Mixed Reality-API-Aufrufe vor dem Erstellen des Remote Kontexts zu unerwartetem Verhalten führen.</span><span class="sxs-lookup"><span data-stu-id="80db4-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="80db4-143">Die empfohlene Vorgehensweise besteht darin, den Remote Kontext so früh wie möglich zu erstellen, bevor Sie mit jeder gemischten Reality-API interagieren.</span><span class="sxs-lookup"><span data-stu-id="80db4-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="80db4-144">Erstellen oder Abrufen von Objekten, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, vor dem Aufrufen von "" mit Objekten, die später erstellt oder abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="80db4-145">Als nächstes muss der holografische Speicherplatz erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="80db4-146">Das Angeben eines corewindow ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="80db4-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="80db4-147">Desktop-Apps, die nicht über ein corewindow verfügen, können nur eine ```nullptr```übergeben.</span><span class="sxs-lookup"><span data-stu-id="80db4-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="80db4-148">Verbindung mit dem Gerät herstellen</span><span class="sxs-lookup"><span data-stu-id="80db4-148">Connect to the device</span></span>

<span data-ttu-id="80db4-149">Sobald die Remote-app zum Rendern von Inhalten bereit ist, kann eine Verbindung mit dem Gerät hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-149">Once the remote app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="80db4-150">Die Verbindung kann auf zwei Arten erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="80db4-151">Die Remote-app stellt eine Verbindung zum Player her, der auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80db4-151">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="80db4-152">Der Player, der auf dem Gerät ausgeführt wird, stellt eine Verbindung zur Remote-app her</span><span class="sxs-lookup"><span data-stu-id="80db4-152">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="80db4-153">Zum Herstellen einer Verbindung zwischen der Remote-app und hololens 2 müssen Sie die ```Connect```-Methode im Remote Kontext mit dem Hostnamen und dem Port angeben.</span><span class="sxs-lookup"><span data-stu-id="80db4-153">To establish a connection from the remote app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="80db4-154">Der von Holographic Remoting Player verwendete Port ist **8265**.</span><span class="sxs-lookup"><span data-stu-id="80db4-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="80db4-155">Wie bei jeder C++/WinRT-API könnte ```Connect``` einen WinRT:: hresult_error auslösen, der behandelt werden muss.</span><span class="sxs-lookup"><span data-stu-id="80db4-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="80db4-156">Um die Verwendung der [ C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) -sprach Projektion zu vermeiden, können Sie die Datei ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` im Holographic Remoting-nuget-Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="80db4-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="80db4-157">Sie enthält Deklarationen der zugrunde liegenden COM-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="80db4-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="80db4-158">Die Verwendung von C++/WinRT wird jedoch empfohlen.</span><span class="sxs-lookup"><span data-stu-id="80db4-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="80db4-159">Zum lauschen auf eingehende Verbindungen in der Remote-app können Sie die ```Listen```-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="80db4-159">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="80db4-160">Der Handshake-Port und der Transporttyp können während dieses Aufrufes angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="80db4-161">Der Handshake-Port wird für den ersten Handshake verwendet.</span><span class="sxs-lookup"><span data-stu-id="80db4-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="80db4-162">Die Daten werden dann über den transportport gesendet.</span><span class="sxs-lookup"><span data-stu-id="80db4-162">The data is then send over the transport port.</span></span> <span data-ttu-id="80db4-163">Standardmäßig werden **8265** und **8266** verwendet.</span><span class="sxs-lookup"><span data-stu-id="80db4-163">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="80db4-164">Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="80db4-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="80db4-165">Behandeln von Remoting-spezifischen Ereignissen</span><span class="sxs-lookup"><span data-stu-id="80db4-165">Handling Remoting specific events</span></span>

<span data-ttu-id="80db4-166">Der Remote Kontext macht drei Ereignisse verfügbar, die für die Überwachung des Zustands einer Verbindung wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="80db4-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="80db4-167">Onconnected: wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="80db4-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="80db4-168">Ontrennt: wird ausgelöst, wenn eine etablierte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="80db4-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
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
3) <span data-ttu-id="80db4-169">Onlistening: beim lauschen auf eingehende Verbindungen wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="80db4-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="80db4-170">Außerdem kann der Verbindungsstatus mithilfe der ```ConnectionState```-Eigenschaft im Remote Kontext abgefragt werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="80db4-171">Behandeln von sprach Ereignissen</span><span class="sxs-lookup"><span data-stu-id="80db4-171">Handling speech events</span></span>

<span data-ttu-id="80db4-172">Mithilfe der Remote Sprachschnittstelle ist es möglich, sprach Trigger bei hololens 2 zu registrieren und Sie Remote mit der Remote Anwendung zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="80db4-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="80db4-173">Dieser zusätzliche Member ist erforderlich, um den Status der Remote Sprache zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="80db4-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="80db4-174">Zuerst muss die Remote Sprachschnittstelle abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="80db4-175">Mithilfe einer asynchronen Hilfsmethode können Sie dann die Remote Sprache initialisieren.</span><span class="sxs-lookup"><span data-stu-id="80db4-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="80db4-176">Dies sollte asynchron erfolgen, da die Initialisierung eine beträchtliche Zeit in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="80db4-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="80db4-177">[Parallelitäts-und asynchrone Vorgänge C++mit/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) erläutert, wie asynchrone Funktionen mit C++/WinRT. erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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

<span data-ttu-id="80db4-178">Es gibt zwei Möglichkeiten zum Angeben von Ausdrücken, die erkannt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="80db4-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="80db4-179">Spezifikation in einer Sprachgrammatik-XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="80db4-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="80db4-180">Weitere Informationen finden [Sie unter Erstellen einer grundlegenden XML-Grammatik](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="80db4-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="80db4-181">Geben Sie an, indem Sie Sie im Wörterbuch Vektor an ```ApplyParameters```übergeben.</span><span class="sxs-lookup"><span data-stu-id="80db4-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="80db4-182">Innerhalb des onerkenzedspeech-Rückrufs können die sprach Ereignisse verarbeitet werden:</span><span class="sxs-lookup"><span data-stu-id="80db4-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="80db4-183">Vorschau der lokal gestreuten Inhalte</span><span class="sxs-lookup"><span data-stu-id="80db4-183">Preview streamed content locally</span></span>

<span data-ttu-id="80db4-184">Um denselben Inhalt in der Remote-app anzuzeigen, der an das Gerät gesendet wird, kann das ```OnSendFrame```-Ereignis des Remote Kontexts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-184">To display the same content in the remote app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="80db4-185">Das ```OnSendFrame``` Ereignis wird jedes Mal ausgelöst, wenn die Holographic Remoting-Bibliothek den aktuellen Frame an das Remote Gerät sendet.</span><span class="sxs-lookup"><span data-stu-id="80db4-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="80db4-186">Dies ist der ideale Zeitpunkt, um den Inhalt zu übernehmen und ihn im Desktop-oder UWP-Fenster zu blitten.</span><span class="sxs-lookup"><span data-stu-id="80db4-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="depth-reprojection"></a><span data-ttu-id="80db4-187">Tiefen neuprojektion</span><span class="sxs-lookup"><span data-stu-id="80db4-187">Depth Reprojection</span></span>

<span data-ttu-id="80db4-188">Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)unterstützt Holographic Remoting die [tiefen neuprojektion](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="80db4-188">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="80db4-189">Dies erfordert zusätzlich zum Farb Puffer, dass auch der tiefen Puffer von der Remote Anwendung auf die hololens 2 gestreamt wird.</span><span class="sxs-lookup"><span data-stu-id="80db4-189">This requires, in addition to the color buffer, to also stream the depth buffer from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="80db4-190">Standardmäßig wird der tiefen Puffer bei der Hälfte der Auflösung des Farb Puffers gestreamt.</span><span class="sxs-lookup"><span data-stu-id="80db4-190">By default the depth buffer is streamed at half the resolution of the color buffer.</span></span> <span data-ttu-id="80db4-191">Dies kann wie folgt geändert werden:</span><span class="sxs-lookup"><span data-stu-id="80db4-191">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="80db4-192">Beachten Sie, dass ```ConfigureDepthVideoStream``` vor dem Herstellen einer Verbindung mit den hololens 2 aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="80db4-192">Note, ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="80db4-193">Der beste Ort ist direkt, nachdem Sie den Remote Kontext erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="80db4-193">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="80db4-194">Mögliche Werte sind Full, half und Quarter Resolution.</span><span class="sxs-lookup"><span data-stu-id="80db4-194">Possible values are full, half, and quater resolution.</span></span> <span data-ttu-id="80db4-195">Der Standardwert ist die halbauflösung.</span><span class="sxs-lookup"><span data-stu-id="80db4-195">Default is half resolution.</span></span> <span data-ttu-id="80db4-196">Beachten Sie, dass die Verwendung eines tiefen Puffers für die vollständige Auflösung auch die Bandbreitenanforderungen beeinflusst und in dem maximalen Bandbreitenwert berücksichtigt werden muss, den Sie für ```CreateRemoteContext```bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="80db4-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="80db4-197">Neben dem Konfigurieren der Auflösung müssen Sie auch einen tiefen Puffer über [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)übertragen.</span><span class="sxs-lookup"><span data-stu-id="80db4-197">Beside configuring the resolution you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

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

<span data-ttu-id="80db4-198">Um zu überprüfen, ob die Tiefe Reprojektion auf hololens 2 korrigiert wird, können Sie über das Geräte Portal eine tiefen Schnellansicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="80db4-198">To verify if depth reprojection is correclty working on HoloLens 2 you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="80db4-199">Weitere Informationen finden Sie unter über [Prüfen der Tiefe festgelegt wurde](hologram-stability.md#verifying-depth-is-set-correctly) .</span><span class="sxs-lookup"><span data-stu-id="80db4-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="80db4-200">Optional: benutzerdefinierte Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="80db4-200">Optional: Custom data channels</span></span>

<span data-ttu-id="80db4-201">Benutzerdefinierte Datenkanäle können zum Senden von Benutzerdaten über die bereits festgelegte Remote Verbindung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="80db4-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="80db4-202">Weitere Informationen finden Sie unter [benutzerdefinierte Datenkanäle](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="80db4-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="80db4-203">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="80db4-203">See Also</span></span>
* [<span data-ttu-id="80db4-204">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="80db4-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="80db4-205">Benutzerdefinierte Holographic Remoting-Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="80db4-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="80db4-206">Einrichten einer sicheren Verbindung mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="80db4-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="80db4-207">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="80db4-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="80db4-208">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="80db4-208">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="80db4-209">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="80db4-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
