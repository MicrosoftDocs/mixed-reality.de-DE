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
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="5ca46-104">Herstellen einer Verbindung mit Wi-Fi für HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ca46-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="5ca46-105">HoloLens enthält eine 802. 11ac-fähig ist, 2 x 2 Wi-Fi-Radio.</span><span class="sxs-lookup"><span data-stu-id="5ca46-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="5ca46-106">Verbinden von HoloLens mit einem Wi-Fi-Netzwerk ähnelt der ein Windows 10 Desktop oder Mobile-Gerät mit einem Wi-Fi-Netzwerk verbinden.</span><span class="sxs-lookup"><span data-stu-id="5ca46-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens-WLAN-Einstellungen](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="5ca46-108">Herstellen einer Verbindung mit einem Wi-Fi-Netzwerk auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ca46-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="5ca46-109">[Bloom](gestures.md#bloom) auf die **starten** Menü.</span><span class="sxs-lookup"><span data-stu-id="5ca46-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="5ca46-110">Wählen Sie die **Einstellungen** app vom Anfang oder das **alle Apps** auf der rechten Seite des Startmenüs auf.</span><span class="sxs-lookup"><span data-stu-id="5ca46-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="5ca46-111">Die **Einstellungen** Anwendung kann automatisch platzierte vor Ihnen.</span><span class="sxs-lookup"><span data-stu-id="5ca46-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="5ca46-112">Wählen Sie **Netzwerk und Internet**.</span><span class="sxs-lookup"><span data-stu-id="5ca46-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="5ca46-113">Achten Sie darauf, dass das WLAN aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5ca46-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="5ca46-114">Wählen Sie ein WLAN-Netzwerk aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="5ca46-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="5ca46-115">Geben Sie das Kennwort der Wi-Fi-Netzwerk (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="5ca46-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="5ca46-116">Deaktivieren Wi-Fi für HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ca46-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="5ca46-117">Mithilfe der Einstellungen-app auf HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ca46-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="5ca46-118">[Bloom](gestures.md#bloom) auf die **starten** Menü.</span><span class="sxs-lookup"><span data-stu-id="5ca46-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="5ca46-119">Wählen Sie die **Einstellungen** app vom Anfang oder das **alle Apps** auf der rechten Seite des Startmenüs auf.</span><span class="sxs-lookup"><span data-stu-id="5ca46-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="5ca46-120">Die **Einstellungen** Anwendung kann automatisch platzierte vor Ihnen.</span><span class="sxs-lookup"><span data-stu-id="5ca46-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="5ca46-121">Wählen Sie **Netzwerk und Internet**.</span><span class="sxs-lookup"><span data-stu-id="5ca46-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="5ca46-122">Wählen Sie den Wi-Fi-Schieberegler-Switch zum Verschieben in die Position "Off".</span><span class="sxs-lookup"><span data-stu-id="5ca46-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="5ca46-123">Die RF-Komponenten des Optionsfelds Wi-Fi deaktivieren wird und deaktivieren Sie alle Wi-Fi-Funktionalität für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5ca46-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="5ca46-124">HoloLens werden nicht automatisch laden Ihre [Leerzeichen](environment-considerations-for-hololens.md#WiFi fingerprint considerations) bei der Wi-Fi-Radio ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="5ca46-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="5ca46-125">Verschieben Sie den Schieberegler-Schalter an die Position "On", auf die Wi-Fi-Radio-und Wi-Fi-Wiederherstellungsfunktionen für Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5ca46-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="5ca46-126">Dem ausgewählten Wi-Fi-Radio-Status ("On" von "Off") nach einem Neustart beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="5ca46-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="5ca46-127">Gewusst wie: Überprüfen, ob Sie mit einem Wi-Fi-Netzwerk verbunden sind</span><span class="sxs-lookup"><span data-stu-id="5ca46-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="5ca46-128">[Bloom](gestures.md#bloom) um die **starten** Menü.</span><span class="sxs-lookup"><span data-stu-id="5ca46-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="5ca46-129">Sehen Sie am oberen Rand des Startmenüs für Wi-Fi-Status bleibt.</span><span class="sxs-lookup"><span data-stu-id="5ca46-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="5ca46-130">Die Status von Wi-Fi und die SSID des verbundenen Netzwerks werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5ca46-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="5ca46-131">Identifizieren die IP-Adresse Ihrer HoloLens im Wi-Fi-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="5ca46-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="5ca46-132">Mithilfe der Einstellungen-app</span><span class="sxs-lookup"><span data-stu-id="5ca46-132">Using the Settings app</span></span>

1. <span data-ttu-id="5ca46-133">[Bloom](gestures.md#bloom) auf die **starten** Menü.</span><span class="sxs-lookup"><span data-stu-id="5ca46-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="5ca46-134">Wählen Sie die **Einstellungen** app vom Anfang oder das **alle Apps** auf der rechten Seite des Startmenüs auf.</span><span class="sxs-lookup"><span data-stu-id="5ca46-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="5ca46-135">Die **Einstellungen** Anwendung kann automatisch platzierte vor Ihnen.</span><span class="sxs-lookup"><span data-stu-id="5ca46-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="5ca46-136">Wählen Sie **Netzwerk und Internet**.</span><span class="sxs-lookup"><span data-stu-id="5ca46-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="5ca46-137">Führen Sie einen Bildlauf nach unten, um unterhalb der Liste der verfügbaren WLAN-Netzwerke, und wählen Sie **Hardwareeigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="5ca46-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Hardwareeigenschaften im WLAN-Einstellungen](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="5ca46-139">Die IP-Adresse neben angezeigt **IPv4-Adresse**.</span><span class="sxs-lookup"><span data-stu-id="5ca46-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="5ca46-140">Mithilfe von Cortana</span><span class="sxs-lookup"><span data-stu-id="5ca46-140">Using Cortana</span></span>

<span data-ttu-id="5ca46-141">Sagen Sie "*Hey Cortana, was Meine IP-Adresse ist?*"</span><span class="sxs-lookup"><span data-stu-id="5ca46-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="5ca46-142">und Cortana angezeigt, und Lesen Sie die IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="5ca46-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="5ca46-143">Mithilfe von Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="5ca46-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="5ca46-144">Öffnen der [geräteportal](using-the-windows-device-portal.md#networking) in einem Webbrowser auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ca46-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="5ca46-145">Navigieren Sie zu der **Networking** Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="5ca46-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="5ca46-146">Ihre IP-Adresse und andere Netzwerkinformationen werden dort angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5ca46-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="5ca46-147">Dieser Methode können sich für einfach kopieren und Einfügen der IP-Adresse auf Ihrem Entwicklungs-PC.</span><span class="sxs-lookup"><span data-stu-id="5ca46-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
