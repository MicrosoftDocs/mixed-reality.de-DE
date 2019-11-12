---
title: Benutzerdefinierte Holographic-Remoting-Datenkanäle
description: Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits festgelegte Holographic Remoting-Verbindung zu senden.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 2861c780c5d7e516d5b7ddc757bbcba6da7e6559
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926667"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="97cf1-104">Benutzerdefinierte Holographic-Remoting-Datenkanäle</span><span class="sxs-lookup"><span data-stu-id="97cf1-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="97cf1-105">Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="97cf1-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="97cf1-106">Verwenden Sie benutzerdefinierte Datenkanäle, um benutzerdefinierte Daten über eine festgelegte remotingverbindung zu senden.</span><span class="sxs-lookup"><span data-stu-id="97cf1-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="97cf1-107">Benutzerdefinierte Datenkanäle erfordern eine benutzerdefinierte Host-APP und eine benutzerdefinierte Player-App, da Sie die Kommunikation zwischen den beiden benutzerdefinierten Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="97cf1-107">Custom data channels require a custom host app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="97cf1-108">Ein einfaches Ping-Pong-Beispiel finden Sie in den Beispielen für Host und Player im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".</span><span class="sxs-lookup"><span data-stu-id="97cf1-108">A simple ping-pong example can be found in the host and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="97cf1-109">Heben Sie die Auskommentierung ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` in den Dateien samplehostmain. h/sampleplayermain. h auf, um den Beispielcode zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="97cf1-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleHostMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="97cf1-110">Erstellen eines benutzerdefinierten Daten Kanals</span><span class="sxs-lookup"><span data-stu-id="97cf1-110">Create a custom data channel</span></span>


<span data-ttu-id="97cf1-111">Zum Erstellen eines benutzerdefinierten Daten Kanals sind die folgenden Felder erforderlich:</span><span class="sxs-lookup"><span data-stu-id="97cf1-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="97cf1-112">Nachdem eine Verbindung hergestellt wurde, kann die Erstellung neuer Datenkanäle entweder von der Hostseite und/oder von der Player Seite initiiert werden.</span><span class="sxs-lookup"><span data-stu-id="97cf1-112">After a connection was successfully established, the creation of new data channels can be initiated from either the host side and/or the player side.</span></span> <span data-ttu-id="97cf1-113">Sowohl remotecontext als auch playercontext stellen eine ```CreateDataChannel()```-Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="97cf1-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="97cf1-114">Der erste Parameter ist die Kanal-ID, die verwendet wird, um den Datenkanal in nachfolgenden Vorgängen zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="97cf1-114">The first parameter is the channel ID which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="97cf1-115">Der zweite Parameter ist die Priorität, die die Priorität angibt, mit der Daten dieses Kanals auf die andere Seite übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="97cf1-115">The second parameter is the priority which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="97cf1-116">Der gültige Bereich für Channel-IDs beträgt 0 bis einschließlich 63 für die Hostseite und 64 bis einschließlich 127 für die Player Seite.</span><span class="sxs-lookup"><span data-stu-id="97cf1-116">The valid range for channel IDs is 0 up to and including 63 for the host side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="97cf1-117">Gültige Prioritäten sind ```Low```, ```Medium``` oder ```High``` (auf beiden Seiten).</span><span class="sxs-lookup"><span data-stu-id="97cf1-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="97cf1-118">So initiieren Sie die Erstellung eines Daten Kanals auf der **Hostseite** :</span><span class="sxs-lookup"><span data-stu-id="97cf1-118">To initiate the creation of a data channel on the **host** side:</span></span>
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="97cf1-119">So initiieren Sie die Erstellung eines Daten Kanals auf der **Player** Seite:</span><span class="sxs-lookup"><span data-stu-id="97cf1-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="97cf1-120">Zum Erstellen eines neuen benutzerdefinierten Daten Kanals muss nur eine Seite (Host oder Spieler) die ```CreateDataChannel```-Methode aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="97cf1-120">To create a new custom data channel, only one side (either host or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="97cf1-121">Behandeln von benutzerdefinierten Datenkanal Ereignissen</span><span class="sxs-lookup"><span data-stu-id="97cf1-121">Handling custom data channel events</span></span>

<span data-ttu-id="97cf1-122">Zum Einrichten eines benutzerdefinierten Daten Kanals muss das ```OnDataChannelCreated``` Ereignis behandelt werden (sowohl auf dem Player als auch auf der Hostseite).</span><span class="sxs-lookup"><span data-stu-id="97cf1-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the host side).</span></span> <span data-ttu-id="97cf1-123">Es wird ausgelöst, wenn ein Benutzerdaten Kanal von beiden Seiten erstellt wurde und ein ```IDataChannel``` Objekt bereitstellt, das zum Senden und empfangen von Daten über diesen Kanal verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="97cf1-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="97cf1-124">So registrieren Sie einen Listener für das ```OnDataChannelCreated```-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="97cf1-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="97cf1-125">Um beim Empfang von Daten benachrichtigt zu werden, registrieren Sie sich beim ```OnDataReceived``` Ereignis für das ```IDataChannel``` Objekt, das vom ```OnDataChannelCreated``` Handler bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="97cf1-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="97cf1-126">Registrieren Sie sich beim ```OnClosed``` Ereignis, um benachrichtigt zu werden, wenn der Datenkanal geschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="97cf1-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a><span data-ttu-id="97cf1-127">Senden von Daten</span><span class="sxs-lookup"><span data-stu-id="97cf1-127">Sending data</span></span>

<span data-ttu-id="97cf1-128">Verwenden Sie die ```IDataChannel::SendData()```-Methode, um Daten über einen benutzerdefinierten Datenkanal zu senden.</span><span class="sxs-lookup"><span data-stu-id="97cf1-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="97cf1-129">Der erste Parameter ist eine ```winrt::array_view<const uint8_t>``` zu den Daten, die gesendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="97cf1-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="97cf1-130">Der zweite Parameter gibt an, wohin die Daten erneut gesendet werden sollen, bis die andere Seite den Empfang bestätigt.</span><span class="sxs-lookup"><span data-stu-id="97cf1-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="97cf1-131">Im Falle fehlerhafter Netzwerkbedingungen kann das gleiche Datenpaket mehrmals eintreffen.</span><span class="sxs-lookup"><span data-stu-id="97cf1-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="97cf1-132">Der empfangende Code muss in der Lage sein, diese Situation zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="97cf1-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="97cf1-133">Schließen eines benutzerdefinierten Daten Kanals</span><span class="sxs-lookup"><span data-stu-id="97cf1-133">Closing a custom data channel</span></span>

<span data-ttu-id="97cf1-134">Verwenden Sie die ```IDataChannel::Close()```-Methode, um einen benutzerdefinierten Datenkanal zu schließen.</span><span class="sxs-lookup"><span data-stu-id="97cf1-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="97cf1-135">Beide Seiten werden durch das ```OnClosed```-Ereignis benachrichtigt, sobald der benutzerdefinierte Datenkanal geschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="97cf1-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="97cf1-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="97cf1-136">See Also</span></span>
* [<span data-ttu-id="97cf1-137">Schreiben einer Holographic Remoting-Host-App</span><span class="sxs-lookup"><span data-stu-id="97cf1-137">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="97cf1-138">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="97cf1-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="97cf1-139">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="97cf1-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="97cf1-140">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="97cf1-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="97cf1-141">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="97cf1-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
