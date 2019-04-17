---
title: Unity-Spielmodus
description: Verwendung des Modus spielen in der Unity-Editor, Ihre Änderungen auf einem Gerät ohne Bereitstellen einer app.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, holographic Remoting, holographic Remoting-player
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593356"
---
# <a name="unity-play-mode"></a><span data-ttu-id="b81cb-104">Unity-Spielmodus</span><span class="sxs-lookup"><span data-stu-id="b81cb-104">Unity Play Mode</span></span>

<span data-ttu-id="b81cb-105">Eine schnelle Möglichkeit zum Arbeiten in Ihrem Unity-Projekt ist die Verwendung von "Modus wiedergeben".</span><span class="sxs-lookup"><span data-stu-id="b81cb-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="b81cb-106">Dies führt Ihre app lokal im Unity-Editor auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="b81cb-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="b81cb-107">Unity wird Holographic Remoting verwendet, um eine schnelle Möglichkeit, Ihre Inhalte auf einem echten Gerät mit HoloLens Vorschau bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="b81cb-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="b81cb-108">Unity-Spielmodus Holographic-Remoting</span><span class="sxs-lookup"><span data-stu-id="b81cb-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="b81cb-109">Bei Holographic-Remoting können Sie Ihre app auf die HoloLens, kommen, während der Ausführung im Unity-Editor auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="b81cb-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="b81cb-110">Blicke, Gesten, Sprach- und räumliche Zuordnung, die Eingabe wird von Ihrem HoloLens auf Ihren PC gesendet.</span><span class="sxs-lookup"><span data-stu-id="b81cb-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="b81cb-111">Gerenderter Frames werden dann zurück an Ihre HoloLens gesendet.</span><span class="sxs-lookup"><span data-stu-id="b81cb-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="b81cb-112">Dies ist eine hervorragende Möglichkeit, Ihre app schnell zu debuggen, ohne die Erstellung und Bereitstellung von einem vollständigen Projekt.</span><span class="sxs-lookup"><span data-stu-id="b81cb-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="b81cb-113">Ihre HoloLens, wechseln Sie zu der **Microsoft Store** herunter, und Installieren der **[Holographic Remoting-Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span><span class="sxs-lookup"><span data-stu-id="b81cb-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="b81cb-114">Starten Sie auf Ihre HoloLens, die **Holographic Remoting-Player** app.</span><span class="sxs-lookup"><span data-stu-id="b81cb-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="b81cb-115">Wechseln Sie in Unity, zu der **Fenster** Menü **Holographic Emulation**.</span><span class="sxs-lookup"><span data-stu-id="b81cb-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="b81cb-116">Legen Sie **Emulationsmodus** zu **Gerät Remote**.</span><span class="sxs-lookup"><span data-stu-id="b81cb-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="b81cb-117">Für **Remotecomputer**, geben Sie die IP-Adresse Ihrer HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b81cb-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="b81cb-118">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="b81cb-118">Click **Connect**.</span></span> <span data-ttu-id="b81cb-119">Daraufhin sollte **Verbindungsstatus** ändern in **verbunden** und der Bildschirm wechseln in der HoloLens leer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b81cb-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="b81cb-120">Klicken Sie auf die **spielen** Schaltfläche zum Starten von Spielen-Modus, und erleben die app auf Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b81cb-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="b81cb-121">Holographic Remoting ist eine schnelle PC und Wi-Fi-Verbindung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b81cb-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="b81cb-122">Finden Sie unter [Holographic Remoting-Player](holographic-remoting-player.md) Weitere Details.</span><span class="sxs-lookup"><span data-stu-id="b81cb-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="b81cb-123">Für optimale Ergebnisse sicherzustellen, dass Ihre app ordnungsgemäß legt die [konzentrieren Punkt](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="b81cb-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="b81cb-124">Dadurch wird die Holographic Remoting zu Ihrer Szene, um die Latenz der drahtlosen Verbindung am besten passen.</span><span class="sxs-lookup"><span data-stu-id="b81cb-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="b81cb-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b81cb-125">See Also</span></span>
* [<span data-ttu-id="b81cb-126">Holographic Remoting-Player</span><span class="sxs-lookup"><span data-stu-id="b81cb-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
