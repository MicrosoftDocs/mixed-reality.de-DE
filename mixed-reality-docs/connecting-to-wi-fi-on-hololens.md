---
title: Herstellen einer Verbindung mit Wi-Fi auf hololens
description: Anweisungen zum Herstellen einer Verbindung mit dem drahtlos Internet mit hololens und zur Identifizierung der IP-Adresse des Geräts.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Hololens, WiFi, drahtlos, Internet, IP, IP-Adresse
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670115"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Herstellen einer Verbindung mit Wi-Fi auf hololens

Hololens enthält ein 802.11 AC-fähiges, 2 x 2-Wi-Fi-Radio. Das Herstellen einer Verbindung von hololens mit einem WLAN-Netzwerk ähnelt dem Verbinden eines Windows 10-Desktops oder eines mobilen Geräts mit einem WLAN.

![Hololens-WLAN-Einstellungen](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Herstellen einer Verbindung mit einem WLAN-Netzwerk auf hololens

1. [Zum](gestures.md#bloom) Startmenü  .
2. Wählen Sie auf der rechten Seite des Menüs Start oder in der Liste **alle apps** die APP **Einstellungen** aus.
3. Die **Einstellungs** -APP wird automatisch vor Ihnen platziert.
4. Wählen Sie **Netzwerk & Internet**aus.
5. Achten Sie darauf, dass das WLAN aktiviert ist.
6. Wählen Sie ein Wi-Fi-Netzwerk aus der Liste aus.
7. Geben Sie das Kennwort für das WLAN-Netzwerk ein (falls erforderlich).

## <a name="disabling-wi-fi-on-hololens"></a>Deaktivieren von Wi-Fi auf hololens

### <a name="using-the-settings-app-on-hololens"></a>Verwenden der App "Einstellungen" auf hololens

1. [Zum](gestures.md#bloom) Startmenü  .
2. Wählen Sie auf der rechten Seite des Menüs Start oder in der Liste **alle apps** die APP **Einstellungen** aus.
3. Die **Einstellungs** -APP wird automatisch vor Ihnen platziert.
4. Wählen Sie **Netzwerk & Internet**aus.
5. Wählen Sie den Schalter für den WLAN-Schieberegler aus, um ihn an die Position "aus" zu verschieben. Dadurch werden die RF-Komponenten des WLAN-Radios ausgeschaltet und alle WLAN-Funktionen auf hololens deaktiviert. 

    >[!WARNING]
    >Hololens sind nicht in der Lage, Ihre [Leerzeichen](environment-considerations-for-hololens.md#WiFi fingerprint considerations) automatisch zu laden, wenn das Wi-Fi-Radio deaktiviert ist.
    
6. Verschieben Sie den Schieberegler an die Position "an", um das Wi-Fi-Radio zu aktivieren und die Wi-Fi-Funktionalität für Microsoft hololens wiederherzustellen. Der ausgewählte Wi-Fi-Radio Zustand ("on" von "Off") wird über die Neustarts hinweg beibehalten.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Stellen Sie sicher, dass eine Verbindung mit einem WLAN-Netzwerk besteht

1. [Mit dieser](gestures.md#bloom) Option können Sie  das Startmenü öffnen.
2. Sehen Sie sich den WLAN-Status oben links im Startmenü an. Der Status von Wi-Fi und SSID des verbundenen Netzwerks wird angezeigt.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Identifizieren der IP-Adresse Ihrer hololens im WLAN-Netzwerk

### <a name="using-the-settings-app"></a>Verwenden der App "Einstellungen"

1. [Zum](gestures.md#bloom) Startmenü  .
2. Wählen Sie auf der rechten Seite des Menüs Start oder in der Liste **alle apps** die APP **Einstellungen** aus.
3. Die **Einstellungs** -APP wird automatisch vor Ihnen platziert.
4. Wählen Sie **Netzwerk & Internet**aus.
5. Scrollen Sie nach unten zur Liste der verfügbaren WLAN-Netzwerke, und wählen Sie **Hardware Eigenschaften**aus.

    ![Hardware Eigenschaften in WLAN-Einstellungen](images/wifi-hololens-hwdetails.jpg)

Die IP-Adresse wird neben IPv4- **Adresse**angezeigt.

### <a name="using-cortana"></a>Verwenden von Cortana

Sagen Sie: "*Hey Cortana, was ist meine IP-Adresse?* " und Cortana wird Ihre IP-Adresse anzeigen und auslesen.

### <a name="using-windows-device-portal"></a>Verwenden des Windows-Geräte Portals

1. Öffnen Sie das [Geräte Portal](using-the-windows-device-portal.md#networking) in einem Webbrowser auf Ihrem PC.
2. Navigieren Sie zum Abschnitt " **Netzwerk** ".

Dort werden Ihre IP-Adresse und andere Netzwerkinformationen angezeigt. Diese Methode ermöglicht das einfache kopieren und Einfügen der IP-Adresse auf dem Entwicklungs-PC.
