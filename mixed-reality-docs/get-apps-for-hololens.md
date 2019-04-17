---
title: Abrufen von apps für HoloLens
description: Beschreibt die Installation von apps für HoloLens, sowohl über die Microsoft Store und querladen.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: per sideload übertragen, clientseitige auslastungs-, sideloading, Store, Uwp, -app installieren
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593248"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="1a3b2-104">Abrufen von apps für HoloLens</span><span class="sxs-lookup"><span data-stu-id="1a3b2-104">Get apps for HoloLens</span></span>

<span data-ttu-id="1a3b2-105">HoloLens unterstützt viele vorhandene UWP-Anwendungen aus dem appstore als auch neue apps, die speziell für HoloLens, als ein Windows 10-Gerät.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="1a3b2-106">Zusätzlich dazu, möglicherweise sogar möchten [entwickeln](development-overview.md) herunter, und installieren Sie Ihre eigenen apps oder der Anmeldeinformationen Ihren Freunden!</span><span class="sxs-lookup"><span data-stu-id="1a3b2-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="1a3b2-107">Installieren von Apps</span><span class="sxs-lookup"><span data-stu-id="1a3b2-107">Installing Apps</span></span>

<span data-ttu-id="1a3b2-108">Es gibt drei Möglichkeiten, neue apps auf Ihre HoloLens zu installieren.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="1a3b2-109">Die primäre Methode werden neue Anwendungen aus dem Windows Store installiert werden.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="1a3b2-110">Allerdings können Sie auch Ihre eigenen Anwendungen mithilfe des Verwaltungsportals Gerät installieren oder indem Sie sie aus Visual Studio bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="1a3b2-111">Aus dem Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1a3b2-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="1a3b2-112">Führen Sie eine [Bloom](gestures.md#bloom) Geste zum Öffnen der [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="1a3b2-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="1a3b2-113">Wählen Sie die Store-app, und tippen Sie dann auf diese Kachel in Ihre Welt zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="1a3b2-114">Wenn die Store-app geöffnet wird, verwenden Sie die Suchleiste, um für alle gewünschten Anwendungen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="1a3b2-115">Wählen Sie **erhalten** oder **installieren** auf der Seite der Anwendung (eine Bestellung kann erforderlich sein).</span><span class="sxs-lookup"><span data-stu-id="1a3b2-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="1a3b2-116">Installieren ein Anwendungspaket mit dem Device Portal</span><span class="sxs-lookup"><span data-stu-id="1a3b2-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="1a3b2-117">Herstellen einer Verbindung zwischen [Device Portal](using-the-windows-device-portal.md) an das Ziel HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="1a3b2-118">Navigieren Sie zu der **Apps** Seite im linken Navigationsbereich.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="1a3b2-119">Klicken Sie unter **App-Paket** navigieren Sie zu der AppX-Datei Ihrer Anwendung zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="1a3b2-120">Stellen Sie sicher, dass alle zugehörigen Abhängigkeiten und Zertifikat-Dateien zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="1a3b2-121">Klicken Sie auf **wechseln**.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-121">Click **Go**.</span></span>

<span data-ttu-id="1a3b2-122">![Installieren von app-Formular in Windows Device Portal für Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a3b2-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="1a3b2-123">Mithilfe von Windows Device Portal-Installation eine app für HoloLens</span><span class="sxs-lookup"><span data-stu-id="1a3b2-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="1a3b2-124">Bereitstellen von Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="1a3b2-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="1a3b2-125">Öffnen Sie Visual Studio-Projektmappe (SLN-Datei) Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="1a3b2-126">Öffnen des Projekts **Eigenschaften** .</span><span class="sxs-lookup"><span data-stu-id="1a3b2-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="1a3b2-127">Wählen Sie die folgenden Build-Konfiguration: Master/X86/Remote-Computer.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="1a3b2-128">Wenn Sie Remotecomputer auswählen:</span><span class="sxs-lookup"><span data-stu-id="1a3b2-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="1a3b2-129">Stellen Sie sicher die adresspunkte, die HoloLens' WiFi IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="1a3b2-130">Festlegen der Authentifizierung auf universell (unverschlüsseltes Protokoll).</span><span class="sxs-lookup"><span data-stu-id="1a3b2-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="1a3b2-131">Erstellen Sie die Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-131">Build your solution.</span></span>
6. <span data-ttu-id="1a3b2-132">Klicken Sie auf die **Remotecomputer** Schaltfläche, um die app von Ihrem Entwicklungs-PC auf Ihre HoloLens bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="1a3b2-133">Wenn Sie bereits einen vorhandenen Build auf die HoloLens haben, wählen Sie Ja aus, um diese neuere Version neu installieren.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="1a3b2-134">![Remote-computerbereitstellung für apps, Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a3b2-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="1a3b2-135">Die Anwendung installiert und automatisch zu starten, auf Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a3b2-135">The application will install and auto launch on your HoloLens.</span></span>
