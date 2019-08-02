---
title: Benutzerdefinierte Holographic-Remoting-Datenkanäle
description: Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits festgelegte Holographic Remoting-Verbindung zu senden.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 9f7f20023d496412b331606e03d0c5110bb4864f
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718084"
---
# <a name="custom-holographic-remoting-data-channels"></a>Benutzerdefinierte Holographic-Remoting-Datenkanäle

>[!NOTE]
>Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

Verwenden Sie benutzerdefinierte Datenkanäle, um benutzerdefinierte Daten über eine festgelegte remotingverbindung zu senden.

>[!IMPORTANT]
>Benutzerdefinierte Datenkanäle erfordern eine benutzerdefinierte Host-APP und eine benutzerdefinierte Player-App, da Sie die Kommunikation zwischen den beiden benutzerdefinierten Apps ermöglicht.

>[!TIP]
>Ein einfaches Ping-Pong-Beispiel finden Sie in den Beispielen für Host und Player im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)". Heben Sie ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` die Auskommentierung in den Dateien samplehostmain. h/sampleplayermain. h auf, um den Beispielcode zu aktivieren.


# <a name="create-a-custom-data-channel"></a>Erstellen eines benutzerdefinierten Daten Kanals


Zum Erstellen eines benutzerdefinierten Daten Kanals sind die folgenden Felder erforderlich:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Nachdem eine Verbindung hergestellt wurde, kann die Erstellung neuer Datenkanäle entweder von der Hostseite und/oder von der Player Seite initiiert werden. Sowohl remotecontext als auch playercontext stellen hierfür eine ```CreateDataChannel()``` -Methode bereit. Der erste Parameter ist die Kanal-ID, die verwendet wird, um den Datenkanal in untergeordneten Vorgängen zu identifizieren. Der zweite Parameter ist die Priorität, die die Priorität angibt, mit der Daten dieses Kanals auf die andere Seite übertragen werden. Der gültige Bereich für Channel-IDs beträgt 0 bis einschließlich 63 für die Hostseite und 64 bis einschließlich 127 für die Player Seite. Gültige Prioritäten sind ```Low``` ```Medium``` oder```High``` (auf beiden Seiten).

So initiieren Sie die Erstellung eines Daten Kanals auf der **Hostseite** :
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

So initiieren Sie die Erstellung eines Daten Kanals auf der **Player** Seite:
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Zum Erstellen eines neuen benutzerdefinierten Daten Kanals muss nur eine Seite (Host oder Spieler) die ```CreateDataChannel``` -Methode aufruft.

## <a name="handling-custom-data-channel-events"></a>Behandeln von benutzerdefinierten Datenkanal Ereignissen

Zum Einrichten eines benutzerdefinierten Daten Kanals muss ```OnDataChannelCreated``` das Ereignis behandelt werden (sowohl auf dem Player als auch auf der Hostseite). Es wird ausgelöst, wenn ein Benutzerdaten Kanal von beiden Seiten erstellt wurde, und ```IDataChannel``` stellt ein-Objekt bereit, das zum Senden und empfangen von Daten über diesen Kanal verwendet werden kann.

So registrieren Sie einen Listener für ```OnDataChannelCreated``` das Ereignis:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Um beim Empfang von Daten benachrichtigt zu werden, registrieren Sie ```OnDataReceived``` sich für das ```IDataChannel``` -Ereignis für das ```OnDataChannelCreated``` vom-Handler bereitgestellte Objekt. Registrieren Sie sich ```OnClosed``` für das Ereignis, um benachrichtigt zu werden, wenn der Datenkanal geschlossen wurde.

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

## <a name="sending-data"></a>Senden von Daten

Verwenden Sie die ```IDataChannel::SendData()``` -Methode, um Daten über einen benutzerdefinierten Datenkanal zu senden. Der erste Parameter ist ein ```winrt::array_view<const uint8_t>``` für die Daten, die gesendet werden sollen. Der zweite Parameter gibt an, ob die Daten erneut gesendet werden sollen, bis die andere Seite den Empfang bestätigt. 

>[!IMPORTANT]
>Im Falle fehlerhafter Netzwerkbedingungen kann das gleiche Datenpaket mehrmals eintreffen. Der empfangende Code muss in der Lage sein, diese Situation zu verarbeiten.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Schließen eines benutzerdefinierten Daten Kanals

Verwenden Sie die ```IDataChannel::Close()``` -Methode, um einen benutzerdefinierten Datenkanal zu schließen. Beide Seiten werden durch das ```OnClosed``` Ereignis benachrichtigt, sobald der benutzerdefinierte Datenkanal geschlossen wurde.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Siehe auch
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Software Lizenzbedingungen für Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)