---
title: Holographic Remoting-Player
description: Der Holographic Remoting-Player ist eine Begleit-app, die eine Verbindung mit der PC-apps und Spiele, die Holographic Remoting unterstützen. Holographic Remoting streamt holographic Inhalte von einem PC in Ihrer Microsoft HoloLens in Echtzeit über eine Wi-Fi-Verbindung.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605004"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="f453a-105">Holographic Remoting-Player</span><span class="sxs-lookup"><span data-stu-id="f453a-105">Holographic Remoting Player</span></span>

<span data-ttu-id="f453a-106">Der Holographic Remoting-Player ist eine Begleit-app, die eine Verbindung mit der PC-apps und Spiele, die Holographic Remoting unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f453a-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="f453a-107">Holographic Remoting streamt holographic Inhalte von einem PC in Ihrer Microsoft HoloLens in Echtzeit über eine Wi-Fi-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="f453a-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="f453a-108">Der Holographic Remoting-Player kann nur mit PC-apps verwendet werden, die speziell zur Unterstützung von Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="f453a-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="f453a-109">Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="f453a-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="f453a-110">Herstellen einer Verbindung mit der Holographic Remoting-Player</span><span class="sxs-lookup"><span data-stu-id="f453a-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="f453a-111">Führen Sie die Ihrer app-Anleitungen zum Verbinden mit der Holographic Remoting-Player.</span><span class="sxs-lookup"><span data-stu-id="f453a-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="f453a-112">Sie benötigen die IP-Adresse des Geräts HoloLens eingeben, die Sie wie folgt auf den Remoting-Player-Hauptbildschirm sehen können:</span><span class="sxs-lookup"><span data-stu-id="f453a-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![Holographic Remoting-Player](images/holographicremotingplayer.png)

<span data-ttu-id="f453a-114">Wenn Sie im Hauptbildschirm sehen, wissen Sie, dass Sie nicht über eine verbundene app verfügen.</span><span class="sxs-lookup"><span data-stu-id="f453a-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="f453a-115">Beachten Sie, dass die holographic Remotingverbindung **nicht verschlüsselt**.</span><span class="sxs-lookup"><span data-stu-id="f453a-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="f453a-116">Sie sollten immer Holographic Remoting über eine sichere Wi-Fi-Verbindung verwenden, die Sie vertrauen.</span><span class="sxs-lookup"><span data-stu-id="f453a-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="f453a-117">Qualität und Leistung</span><span class="sxs-lookup"><span data-stu-id="f453a-117">Quality and Performance</span></span>

<span data-ttu-id="f453a-118">Die Qualität und Leistung Ihrer Erfahrung variieren basierend auf drei Faktoren ab:</span><span class="sxs-lookup"><span data-stu-id="f453a-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="f453a-119">**Sie führen holografischen Benutzeroberfläche** -Apps, die mit hoher Auflösung oder äußerst detaillierte Inhalt Rendern erfordern einen schnelleren PC oder schneller drahtlose Verbindung.</span><span class="sxs-lookup"><span data-stu-id="f453a-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="f453a-120">**Ihre PC Hardware** -Ihr PC benötigt wird, in der Lage, ausführen und Ihre holografischen Benutzeroberfläche mit 60 Bildern pro Sekunde zu codieren.</span><span class="sxs-lookup"><span data-stu-id="f453a-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="f453a-121">Für eine Grafikkarte empfehlen wir in der Regel eine GeForce GTX 970 oder AMD Radeon R9 290 oder höher.</span><span class="sxs-lookup"><span data-stu-id="f453a-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="f453a-122">In diesem Fall möglicherweise Ihre bestimmte Umgebung eine höhere oder Low-End-Karte.</span><span class="sxs-lookup"><span data-stu-id="f453a-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="f453a-123">**Die Wi-Fi-Verbindung** -Ihre holografischen Benutzeroberfläche über Wi-Fi gestreamt wird.</span><span class="sxs-lookup"><span data-stu-id="f453a-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="f453a-124">Verwenden Sie ein schnelles Netzwerk mit niedriger Überlastung, um die Qualität zu maximieren.</span><span class="sxs-lookup"><span data-stu-id="f453a-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="f453a-125">Verwenden Sie einen PC, der über ein Ethernetkabel verbunden ist, kann anstelle von Wi-Fi, auch Qualität verbessern.</span><span class="sxs-lookup"><span data-stu-id="f453a-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="f453a-126">Diagnose</span><span class="sxs-lookup"><span data-stu-id="f453a-126">Diagnostics</span></span>

<span data-ttu-id="f453a-127">Um die Qualität Ihrer Verbindung zu messen, z. B. **"Diagnose aktivieren"** zwar auf dem Hauptbildschirm des Holographic Remoting-Players.</span><span class="sxs-lookup"><span data-stu-id="f453a-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="f453a-128">Wenn die Diagnose aktiviert wurde, wird die app Sie angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f453a-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="f453a-129">**FPS** : die durchschnittliche Anzahl der Einzelbilder, die der Remoting-Player empfangen wird und Rendern pro Sekunde.</span><span class="sxs-lookup"><span data-stu-id="f453a-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="f453a-130">Ideal sind 60 FPS.</span><span class="sxs-lookup"><span data-stu-id="f453a-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="f453a-131">**Latenz** : die durchschnittliche Länge der Zeit, die für einen Frame aus, um von Ihrem PC zu wechseln, um die HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f453a-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="f453a-132">Je niedriger, desto besser.</span><span class="sxs-lookup"><span data-stu-id="f453a-132">The lower the better.</span></span> <span data-ttu-id="f453a-133">Dies ist in hohem Maße abhängig von Ihrem Wi-Fi-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="f453a-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="f453a-134">Sie können auf dem Hauptbildschirm, sagen **"Deaktivieren der Diagnose"** zum Deaktivieren der Diagnose zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f453a-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="f453a-135">PC-Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="f453a-135">PC System Requirements</span></span>
* <span data-ttu-id="f453a-136">Ihr PC **müssen** Windows 10 Anniversary Update ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f453a-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="f453a-137">Es wird empfohlen, eine GeForce GTX 970 oder AMD Radeon R9 290 oder bessere Grafikkarte.</span><span class="sxs-lookup"><span data-stu-id="f453a-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="f453a-138">Es wird empfohlen, dass Sie eine solche mit Ihrem Netzwerk über Ethernet zum Reduzieren der Anzahl der Hops, die drahtlose Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="f453a-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="f453a-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f453a-139">See Also</span></span>
* [<span data-ttu-id="f453a-140">Holographic Remoting-Software-Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="f453a-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="f453a-141">Datenschutzbestimmungen von Microsoft</span><span class="sxs-lookup"><span data-stu-id="f453a-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
