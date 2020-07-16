---
title: Bereitstellen auf Gerät in Unreal
description: Leitfaden für die Bereitstellung auf dem Gerät in Unreal für hololens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, Bereitstellung auf Gerät, PC, Dokumentation
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408178"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="8864e-104">Bereitstellen auf Gerät in Unreal</span><span class="sxs-lookup"><span data-stu-id="8864e-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="8864e-105">Überblick</span><span class="sxs-lookup"><span data-stu-id="8864e-105">Overview</span></span>
<span data-ttu-id="8864e-106">Es gibt zwei Möglichkeiten, eine Unreal-Anwendung auf hololens 2 bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="8864e-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span> 
* <span data-ttu-id="8864e-107">Direkt aus dem Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="8864e-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="8864e-108">Als Paket, das über das Geräte Portal hochgeladen wird</span><span class="sxs-lookup"><span data-stu-id="8864e-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="8864e-109">Für beide Optionen müssen Sie die hololens einrichten, damit das [Geräte Portal](using-the-windows-device-portal.md) für die Entwicklung verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="8864e-109">Both options require you to set up your HoloLens to use the [device portal](using-the-windows-device-portal.md) for development.</span></span> 

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="8864e-110">Bereitstellen auf einem Gerät über den Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="8864e-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="8864e-111">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche **starten** .</span><span class="sxs-lookup"><span data-stu-id="8864e-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="8864e-112">Anfänglich ist die hololens-Geräte Option ausgegraut.</span><span class="sxs-lookup"><span data-stu-id="8864e-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Startmenü Optionen](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="8864e-114">Öffnen Sie die **Geräte-Manager**.</span><span class="sxs-lookup"><span data-stu-id="8864e-114">Open the **Device Manager**.</span></span> <span data-ttu-id="8864e-115">Beachten Sie, dass Ihre hololens nicht automatisch in der Geräteliste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8864e-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="8864e-116">Erweitern Sie den Abschnitt **nicht aufgelisteten Gerät hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="8864e-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="8864e-117">Wählen Sie **hololens** als **Plattform**aus.</span><span class="sxs-lookup"><span data-stu-id="8864e-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="8864e-118">Geben Sie die IP-Adresse und die Port Informationen Ihrer Geräte als Geräte Bezeichner getrennt durch einen Doppelpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="8864e-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="8864e-119">Beispiel: "127.0.0.1:10080" (bei Verbindung über USB).</span><span class="sxs-lookup"><span data-stu-id="8864e-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="8864e-120">Verwenden Sie die Anmelde Informationen für den Benutzernamen Ihres Geräte Portals.</span><span class="sxs-lookup"><span data-stu-id="8864e-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="8864e-121">Schließen **Sie** den Geräte-Manager, und schließen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="8864e-121">Hit **Add** and close the device manager.</span></span> 
    * <span data-ttu-id="8864e-122">Im Falle eines Fehlers (z. b. falsche Adresse, Benutzername oder Kennwort) wird eine Meldung in das Ausgabeprotokoll ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="8864e-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Hinzufügen eines nicht aufgelisteten Geräts](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="8864e-124">Klicken Sie erneut auf den Dropdown Pfeil neben der Schaltfläche " **Start** ". dieses Mal sollte das von Ihnen soeben hinzugefügte hololens-Gerät angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8864e-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="8864e-125">Wählen Sie das hololens-Gerät zum Erstellen und Bereitstellen Ihrer hololens aus.</span><span class="sxs-lookup"><span data-stu-id="8864e-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span> 

>[!NOTE]
><span data-ttu-id="8864e-126">Das Erstellen für das Gerät erfordert möglicherweise die Neukompilierung von Shadern (insbesondere bei der ersten Ausführung). Dies kann einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="8864e-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="8864e-127">Lassen Sie das Gerät erst wieder in den Standbymodus wechseln, wenn die app ausgeführt wird (möglicherweise müssen Sie es verwenden).</span><span class="sxs-lookup"><span data-stu-id="8864e-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="8864e-128">Andernfalls tritt bei der shaderkompilierung ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="8864e-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="8864e-129">Bereitstellen auf einem Gerät über das Geräte Portal</span><span class="sxs-lookup"><span data-stu-id="8864e-129">Deploying to device via device portal</span></span>

<span data-ttu-id="8864e-130">Ausführliche Anweisungen zum [Verpacken und Bereitstellen einer APP](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) finden Sie im letzten Abschnitt der Reihe "Getting Started with Unreal Tutorial".</span><span class="sxs-lookup"><span data-stu-id="8864e-130">You can find detailed instructions on [packaging and deploying an app](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>
