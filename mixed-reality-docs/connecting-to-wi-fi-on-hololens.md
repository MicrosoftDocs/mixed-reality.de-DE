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
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="2cf15-104">Herstellen einer Verbindung mit Wi-Fi auf hololens</span><span class="sxs-lookup"><span data-stu-id="2cf15-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="2cf15-105">Hololens enthält ein 802.11 AC-fähiges, 2 x 2-Wi-Fi-Radio.</span><span class="sxs-lookup"><span data-stu-id="2cf15-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="2cf15-106">Das Herstellen einer Verbindung von hololens mit einem WLAN-Netzwerk ähnelt dem Verbinden eines Windows 10-Desktops oder eines mobilen Geräts mit einem WLAN.</span><span class="sxs-lookup"><span data-stu-id="2cf15-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Hololens-WLAN-Einstellungen](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="2cf15-108">Herstellen einer Verbindung mit einem WLAN-Netzwerk auf hololens</span><span class="sxs-lookup"><span data-stu-id="2cf15-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="2cf15-109">[Zum](gestures.md#bloom) Startmenü  .</span><span class="sxs-lookup"><span data-stu-id="2cf15-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="2cf15-110">Wählen Sie auf der rechten Seite des Menüs Start oder in der Liste **alle apps** die APP **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="2cf15-111">Die **Einstellungs** -APP wird automatisch vor Ihnen platziert.</span><span class="sxs-lookup"><span data-stu-id="2cf15-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="2cf15-112">Wählen Sie **Netzwerk & Internet**aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="2cf15-113">Achten Sie darauf, dass das WLAN aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2cf15-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="2cf15-114">Wählen Sie ein Wi-Fi-Netzwerk aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="2cf15-115">Geben Sie das Kennwort für das WLAN-Netzwerk ein (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="2cf15-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="2cf15-116">Deaktivieren von Wi-Fi auf hololens</span><span class="sxs-lookup"><span data-stu-id="2cf15-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="2cf15-117">Verwenden der App "Einstellungen" auf hololens</span><span class="sxs-lookup"><span data-stu-id="2cf15-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="2cf15-118">[Zum](gestures.md#bloom) Startmenü  .</span><span class="sxs-lookup"><span data-stu-id="2cf15-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="2cf15-119">Wählen Sie auf der rechten Seite des Menüs Start oder in der Liste **alle apps** die APP **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="2cf15-120">Die **Einstellungs** -APP wird automatisch vor Ihnen platziert.</span><span class="sxs-lookup"><span data-stu-id="2cf15-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="2cf15-121">Wählen Sie **Netzwerk & Internet**aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="2cf15-122">Wählen Sie den Schalter für den WLAN-Schieberegler aus, um ihn an die Position "aus" zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="2cf15-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="2cf15-123">Dadurch werden die RF-Komponenten des WLAN-Radios ausgeschaltet und alle WLAN-Funktionen auf hololens deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="2cf15-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="2cf15-124">Hololens sind nicht in der Lage, Ihre [Leerzeichen](environment-considerations-for-hololens.md#WiFi fingerprint considerations) automatisch zu laden, wenn das Wi-Fi-Radio deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2cf15-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="2cf15-125">Verschieben Sie den Schieberegler an die Position "an", um das Wi-Fi-Radio zu aktivieren und die Wi-Fi-Funktionalität für Microsoft hololens wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="2cf15-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="2cf15-126">Der ausgewählte Wi-Fi-Radio Zustand ("on" von "Off") wird über die Neustarts hinweg beibehalten.</span><span class="sxs-lookup"><span data-stu-id="2cf15-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="2cf15-127">Stellen Sie sicher, dass eine Verbindung mit einem WLAN-Netzwerk besteht</span><span class="sxs-lookup"><span data-stu-id="2cf15-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="2cf15-128">[Mit dieser](gestures.md#bloom) Option können Sie  das Startmenü öffnen.</span><span class="sxs-lookup"><span data-stu-id="2cf15-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="2cf15-129">Sehen Sie sich den WLAN-Status oben links im Startmenü an.</span><span class="sxs-lookup"><span data-stu-id="2cf15-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="2cf15-130">Der Status von Wi-Fi und SSID des verbundenen Netzwerks wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2cf15-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="2cf15-131">Identifizieren der IP-Adresse Ihrer hololens im WLAN-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="2cf15-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="2cf15-132">Verwenden der App "Einstellungen"</span><span class="sxs-lookup"><span data-stu-id="2cf15-132">Using the Settings app</span></span>

1. <span data-ttu-id="2cf15-133">[Zum](gestures.md#bloom) Startmenü  .</span><span class="sxs-lookup"><span data-stu-id="2cf15-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="2cf15-134">Wählen Sie auf der rechten Seite des Menüs Start oder in der Liste **alle apps** die APP **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="2cf15-135">Die **Einstellungs** -APP wird automatisch vor Ihnen platziert.</span><span class="sxs-lookup"><span data-stu-id="2cf15-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="2cf15-136">Wählen Sie **Netzwerk & Internet**aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="2cf15-137">Scrollen Sie nach unten zur Liste der verfügbaren WLAN-Netzwerke, und wählen Sie **Hardware Eigenschaften**aus.</span><span class="sxs-lookup"><span data-stu-id="2cf15-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Hardware Eigenschaften in WLAN-Einstellungen](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="2cf15-139">Die IP-Adresse wird neben IPv4- **Adresse**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2cf15-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="2cf15-140">Verwenden von Cortana</span><span class="sxs-lookup"><span data-stu-id="2cf15-140">Using Cortana</span></span>

<span data-ttu-id="2cf15-141">Sagen Sie: "*Hey Cortana, was ist meine IP-Adresse?* "</span><span class="sxs-lookup"><span data-stu-id="2cf15-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="2cf15-142">und Cortana wird Ihre IP-Adresse anzeigen und auslesen.</span><span class="sxs-lookup"><span data-stu-id="2cf15-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="2cf15-143">Verwenden des Windows-Geräte Portals</span><span class="sxs-lookup"><span data-stu-id="2cf15-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="2cf15-144">Öffnen Sie das [Geräte Portal](using-the-windows-device-portal.md#networking) in einem Webbrowser auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="2cf15-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="2cf15-145">Navigieren Sie zum Abschnitt " **Netzwerk** ".</span><span class="sxs-lookup"><span data-stu-id="2cf15-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="2cf15-146">Dort werden Ihre IP-Adresse und andere Netzwerkinformationen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2cf15-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="2cf15-147">Diese Methode ermöglicht das einfache kopieren und Einfügen der IP-Adresse auf dem Entwicklungs-PC.</span><span class="sxs-lookup"><span data-stu-id="2cf15-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
