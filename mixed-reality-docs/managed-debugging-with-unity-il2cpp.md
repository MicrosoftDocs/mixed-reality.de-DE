---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie einen verwalteten Debugger auf Ihr Unity-IL2CPP-UWP-Projekt ausgeführt wird.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: Unity und visual Studio Debuggen, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148855"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="a573e-104">Verwaltetes Debuggen mit Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="a573e-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="a573e-105">Um Ihr Unity-IL2CPP-UWP-Build einen verwalteten Debugger anzufügen, gehen Sie wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="a573e-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="a573e-106">Dieses Handbuch wurde ursprünglich für HoloLens und 2 für HoloLens entwickelt.</span><span class="sxs-lookup"><span data-stu-id="a573e-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="a573e-107">Sicherstellen, dass **InternetClientServer** und **PrivateNetworkClientServer** im Unity unter Einstellungen für die UWP-Veröffentlichungsfunktionen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="a573e-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP-Einstellungen von Funktionen zu veröffentlichen](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="a573e-109">Konfigurieren Sie die UWP für Unity-Buildeinstellungen:</span><span class="sxs-lookup"><span data-stu-id="a573e-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="a573e-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="a573e-110">Development Build</span></span>
    - <span data-ttu-id="a573e-111">Skriptdebugging</span><span class="sxs-lookup"><span data-stu-id="a573e-111">Script Debugging</span></span>
    - <span data-ttu-id="a573e-112">Warten Sie auf den Managed Debugger (optional)</span><span class="sxs-lookup"><span data-stu-id="a573e-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="a573e-114">Erstellen Sie in Unity.</span><span class="sxs-lookup"><span data-stu-id="a573e-114">Build in Unity.</span></span>
1. <span data-ttu-id="a573e-115">Erstellen und Bereitstellen von Visual Studio-Projektmappe auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="a573e-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="a573e-116">Sie sollten die Erstellung mit der **Debuggen** oder **Version** Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a573e-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="a573e-117">Die **Master** Konfiguration den Unity-Profiler deaktiviert und können verhindern, dass eine optimale Debuggen.</span><span class="sxs-lookup"><span data-stu-id="a573e-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="a573e-118">Überprüfen Sie optional **Internet (Client & Server)** und **Private Netzwerke (Client & Server)** in der Liste "Funktionen" in "Package.appxmanifest" in der Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="a573e-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="a573e-119">Die app auf Ihrem Gerät zu starten.</span><span class="sxs-lookup"><span data-stu-id="a573e-119">Start the app on your device.</span></span> <span data-ttu-id="a573e-120">Stellen Sie sicher, dass Ihr Gerät mit dem gleichen Netzwerk wie Ihr PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="a573e-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="a573e-121">Stellen Sie sicher, dass das Gerät **nicht** auf Ihren PC über USB verbunden.</span><span class="sxs-lookup"><span data-stu-id="a573e-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="a573e-122">Wechseln Sie zu Visual Studio-Projektmappe, die erstellt wird, wenn Sie doppelklicken auf ein Skript in Unity klicken, können Sie anzeigen und Bearbeiten Ihrer C# Skripts.</span><span class="sxs-lookup"><span data-stu-id="a573e-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="a573e-123">Debuggen -> Unity-Debugger anfügen.</span><span class="sxs-lookup"><span data-stu-id="a573e-123">Debug -> Attach Unity Debugger.</span></span>

    ![Unity-Debugger anfügen](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="a573e-125">Wählen Sie Ihr Gerät in der Liste aus, und klicken Sie auf "OK" anfügen.</span><span class="sxs-lookup"><span data-stu-id="a573e-125">Select your device in the list and click "OK" to attach.</span></span>

    ![Geräteliste](images/il2cpp-debugging-machines.png)
