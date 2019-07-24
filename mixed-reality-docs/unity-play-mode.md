---
title: Unity-Wiedergabemodus
description: Verwenden Sie den Wiedergabemodus im Unity-Editor, um eine Vorschau der Änderungen auf einem Gerät anzuzeigen, ohne eine APP bereitzustellen.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, Holographic Remoting, Holographic Remoting Player
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548732"
---
# <a name="unity-play-mode"></a><span data-ttu-id="482db-104">Unity-Wiedergabemodus</span><span class="sxs-lookup"><span data-stu-id="482db-104">Unity Play Mode</span></span>

<span data-ttu-id="482db-105">Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus".</span><span class="sxs-lookup"><span data-stu-id="482db-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="482db-106">Dadurch wird Ihre APP lokal im Unity-Editor auf Ihrem PC ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="482db-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="482db-107">Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten hololens-Gerät bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="482db-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="482db-108">Unity-Wiedergabemodus mit Holographic-Remoting</span><span class="sxs-lookup"><span data-stu-id="482db-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="482db-109">Mit Holographic Remoting können Sie Ihre APP auf den hololens erleben, während Sie im Unity-Editor auf Ihrem PC ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="482db-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="482db-110">Eingaben, Gesten, Stimme und räumliche zuordnungseingaben werden von ihren hololens an Ihren PC gesendet.</span><span class="sxs-lookup"><span data-stu-id="482db-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="482db-111">Gerenderte Frames werden dann zurück an Ihre hololens gesendet.</span><span class="sxs-lookup"><span data-stu-id="482db-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="482db-112">Dies ist eine gute Möglichkeit, Ihre APP schnell zu debuggen, ohne ein vollständiges Projekt zu entwickeln und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="482db-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="482db-113">Wechseln Sie auf Ihren hololens zum **Microsoft Store** , und installieren Sie die **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** -app.</span><span class="sxs-lookup"><span data-stu-id="482db-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="482db-114">Starten Sie auf Ihren hololens die **Holographic Remoting Player** -app.</span><span class="sxs-lookup"><span data-stu-id="482db-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="482db-115">Wechseln Sie in Unity zum Menü **Fenster** , und wählen Sie **Holographic Emulation**aus.</span><span class="sxs-lookup"><span data-stu-id="482db-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="482db-116">Festlegen des **Emulations Modus** auf Remote- **zu-Gerät**.</span><span class="sxs-lookup"><span data-stu-id="482db-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="482db-117">Geben Sie für **Remote Computer**die IP-Adresse der hololens ein.</span><span class="sxs-lookup"><span data-stu-id="482db-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="482db-118">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="482db-118">Click **Connect**.</span></span> <span data-ttu-id="482db-119">Der **Verbindungs Status** sollte in **verbunden** angezeigt werden, und der Bildschirm wechselt in den hololens leer.</span><span class="sxs-lookup"><span data-stu-id="482db-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="482db-120">Klicken Sie auf die **Wiedergabe** Schaltfläche, um den Wiedergabemodus zu starten und die APP auf Ihren hololens zu erleben</span><span class="sxs-lookup"><span data-stu-id="482db-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="482db-121">Holographic Remoting erfordert eine schnelle PC-und Wi-Fi-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="482db-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="482db-122">Ausführliche Informationen finden Sie unter [Holographic Remoting Player](holographic-remoting-player.md) .</span><span class="sxs-lookup"><span data-stu-id="482db-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="482db-123">Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre APP den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt.</span><span class="sxs-lookup"><span data-stu-id="482db-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="482db-124">Dies hilft Holographic Remoting bei der optimalen Anpassung Ihrer Szene an die Latenz Ihrer drahtlosen Verbindung.</span><span class="sxs-lookup"><span data-stu-id="482db-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="482db-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="482db-125">See Also</span></span>
* [<span data-ttu-id="482db-126">Holographic Remoting-Player</span><span class="sxs-lookup"><span data-stu-id="482db-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
