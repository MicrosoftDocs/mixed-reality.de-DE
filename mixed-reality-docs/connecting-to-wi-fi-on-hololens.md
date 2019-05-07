---
title: Herstellen einer Verbindung mit Wi-Fi für HoloLens
description: Anweisungen zum Herstellen einer Verbindung mit HoloLens drahtlose Internet und die IP-Adresse des Geräts zu identifizieren.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wifi, drahtlos, Internet, Ip, IP-Adresse
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670115"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Herstellen einer Verbindung mit Wi-Fi für HoloLens

HoloLens enthält eine 802. 11ac-fähig ist, 2 x 2 Wi-Fi-Radio. Verbinden von HoloLens mit einem Wi-Fi-Netzwerk ähnelt der ein Windows 10 Desktop oder Mobile-Gerät mit einem Wi-Fi-Netzwerk verbinden.

![HoloLens-WLAN-Einstellungen](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Herstellen einer Verbindung mit einem Wi-Fi-Netzwerk auf HoloLens

1. [Bloom](gestures.md#bloom) auf die **starten** Menü.
2. Wählen Sie die **Einstellungen** app vom Anfang oder das **alle Apps** auf der rechten Seite des Startmenüs auf.
3. Die **Einstellungen** Anwendung kann automatisch platzierte vor Ihnen.
4. Wählen Sie **Netzwerk und Internet**.
5. Achten Sie darauf, dass das WLAN aktiviert ist.
6. Wählen Sie ein WLAN-Netzwerk aus der Liste aus.
7. Geben Sie das Kennwort der Wi-Fi-Netzwerk (falls erforderlich).

## <a name="disabling-wi-fi-on-hololens"></a>Deaktivieren Wi-Fi für HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Mithilfe der Einstellungen-app auf HoloLens

1. [Bloom](gestures.md#bloom) auf die **starten** Menü.
2. Wählen Sie die **Einstellungen** app vom Anfang oder das **alle Apps** auf der rechten Seite des Startmenüs auf.
3. Die **Einstellungen** Anwendung kann automatisch platzierte vor Ihnen.
4. Wählen Sie **Netzwerk und Internet**.
5. Wählen Sie den Wi-Fi-Schieberegler-Switch zum Verschieben in die Position "Off". Die RF-Komponenten des Optionsfelds Wi-Fi deaktivieren wird und deaktivieren Sie alle Wi-Fi-Funktionalität für HoloLens. 

    >[!WARNING]
    >HoloLens werden nicht automatisch laden Ihre [Leerzeichen](environment-considerations-for-hololens.md#WiFi fingerprint considerations) bei der Wi-Fi-Radio ist deaktiviert.
    
6. Verschieben Sie den Schieberegler-Schalter an die Position "On", auf die Wi-Fi-Radio-und Wi-Fi-Wiederherstellungsfunktionen für Microsoft HoloLens. Dem ausgewählten Wi-Fi-Radio-Status ("On" von "Off") nach einem Neustart beibehalten wird.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Gewusst wie: Überprüfen, ob Sie mit einem Wi-Fi-Netzwerk verbunden sind

1. [Bloom](gestures.md#bloom) um die **starten** Menü.
2. Sehen Sie am oberen Rand des Startmenüs für Wi-Fi-Status bleibt. Die Status von Wi-Fi und die SSID des verbundenen Netzwerks werden angezeigt.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Identifizieren die IP-Adresse Ihrer HoloLens im Wi-Fi-Netzwerk

### <a name="using-the-settings-app"></a>Mithilfe der Einstellungen-app

1. [Bloom](gestures.md#bloom) auf die **starten** Menü.
2. Wählen Sie die **Einstellungen** app vom Anfang oder das **alle Apps** auf der rechten Seite des Startmenüs auf.
3. Die **Einstellungen** Anwendung kann automatisch platzierte vor Ihnen.
4. Wählen Sie **Netzwerk und Internet**.
5. Führen Sie einen Bildlauf nach unten, um unterhalb der Liste der verfügbaren WLAN-Netzwerke, und wählen Sie **Hardwareeigenschaften**.

    ![Hardwareeigenschaften im WLAN-Einstellungen](images/wifi-hololens-hwdetails.jpg)

Die IP-Adresse neben angezeigt **IPv4-Adresse**.

### <a name="using-cortana"></a>Mithilfe von Cortana

Sagen Sie "*Hey Cortana, was Meine IP-Adresse ist?*" und Cortana angezeigt, und Lesen Sie die IP-Adresse.

### <a name="using-windows-device-portal"></a>Mithilfe von Windows Device Portal

1. Öffnen der [geräteportal](using-the-windows-device-portal.md#networking) in einem Webbrowser auf Ihrem PC.
2. Navigieren Sie zu der **Networking** Abschnitt.

Ihre IP-Adresse und andere Netzwerkinformationen werden dort angezeigt werden. Dieser Methode können sich für einfach kopieren und Einfügen der IP-Adresse auf Ihrem Entwicklungs-PC.
