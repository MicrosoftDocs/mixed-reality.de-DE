---
title: Apps für hololens erhalten
description: Beschreibt die Installation von Apps für hololens, beides über das Microsoft Store und das Sideloading.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Sideload, Seitenlast, Sideloading, Store, UWP, APP, Installation
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522561"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="73780-104">Apps für hololens erhalten</span><span class="sxs-lookup"><span data-stu-id="73780-104">Get apps for HoloLens</span></span>

<span data-ttu-id="73780-105">Als Windows 10-Gerät unterstützt hololens viele vorhandene UWP-Anwendungen aus dem App Store sowie neue apps, die speziell für hololens erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="73780-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="73780-106">Darüber hinaus können Sie sogar Ihre eigenen Apps oder die Ihrer Freunde [entwickeln](development-overview.md) und installieren.</span><span class="sxs-lookup"><span data-stu-id="73780-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="73780-107">Installieren von apps</span><span class="sxs-lookup"><span data-stu-id="73780-107">Installing Apps</span></span>

<span data-ttu-id="73780-108">Es gibt drei Möglichkeiten, neue apps auf Ihren hololens zu installieren.</span><span class="sxs-lookup"><span data-stu-id="73780-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="73780-109">Die primäre Methode ist die Installation neuer Anwendungen aus dem Windows Store.</span><span class="sxs-lookup"><span data-stu-id="73780-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="73780-110">Allerdings können Sie Ihre eigenen Anwendungen auch über das Geräte Portal oder durch Bereitstellung aus Visual Studio installieren.</span><span class="sxs-lookup"><span data-stu-id="73780-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="73780-111">Aus der Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="73780-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="73780-112">Führen Sie eine [Bloom-Geste](gestures.md#bloom) aus, um das [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="73780-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="73780-113">Wählen Sie die Store-App aus, und tippen Sie dann auf diese Kachel in die Welt.</span><span class="sxs-lookup"><span data-stu-id="73780-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="73780-114">Nachdem die Store-App geöffnet wurde, verwenden Sie die Suchleiste, um nach einer beliebigen gewünschten Anwendung zu suchen.</span><span class="sxs-lookup"><span data-stu-id="73780-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="73780-115">Wählen Sie auf der Seite der Anwendung die Option **Get** oder **install** (ein Kauf ist möglicherweise erforderlich).</span><span class="sxs-lookup"><span data-stu-id="73780-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="73780-116">Installieren eines Anwendungspakets mit dem Geräte Portal</span><span class="sxs-lookup"><span data-stu-id="73780-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="73780-117">Stellen Sie eine Verbindung zwischen dem [Geräte Portal](using-the-windows-device-portal.md) und den Ziel-hololens her.</span><span class="sxs-lookup"><span data-stu-id="73780-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="73780-118">Navigieren Sie im linken Navigationsbereich zur Seite **apps** .</span><span class="sxs-lookup"><span data-stu-id="73780-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="73780-119">Navigieren Sie unter **App-Paket** zu der AppX-Datei, die Ihrer Anwendung zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="73780-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="73780-120">Stellen Sie sicher, dass Sie auf verknüpfte Abhängigkeits-und Zertifikat Dateien verweisen</span><span class="sxs-lookup"><span data-stu-id="73780-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="73780-121">Klicken Sie auf **Go**.</span><span class="sxs-lookup"><span data-stu-id="73780-121">Click **Go**.</span></span>

<span data-ttu-id="73780-122">![App-Formular im Windows-Geräte Portal auf Microsoft hololens installieren](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="73780-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="73780-123">Verwenden des Windows-Geräte Portals zum Installieren einer APP auf hololens</span><span class="sxs-lookup"><span data-stu-id="73780-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="73780-124">Bereitstellen von Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="73780-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="73780-125">Öffnen Sie die Visual Studio-Projekt Mappe (SLN-Datei) Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="73780-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="73780-126">Öffnen Sie die **Eigenschaften** des Projekts.</span><span class="sxs-lookup"><span data-stu-id="73780-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="73780-127">Wählen Sie die folgende Buildkonfiguration aus: Master/x86/Remote Computer.</span><span class="sxs-lookup"><span data-stu-id="73780-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="73780-128">Wenn Sie Remote Computer auswählen:</span><span class="sxs-lookup"><span data-stu-id="73780-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="73780-129">Stellen Sie sicher, dass die Adresse auf die WiFi-IP-Adresse des hololens verweist.</span><span class="sxs-lookup"><span data-stu-id="73780-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="73780-130">Legen Sie die Authentifizierung auf Universal (unverschlüsseltes Protokoll) fest.</span><span class="sxs-lookup"><span data-stu-id="73780-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="73780-131">Erstellen Sie die Lösung.</span><span class="sxs-lookup"><span data-stu-id="73780-131">Build your solution.</span></span>
6. <span data-ttu-id="73780-132">Klicken Sie auf die Schaltfläche **Remote Computer** , um die APP von Ihrem Entwicklungs-PC in ihren hololens bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="73780-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="73780-133">Wenn Sie bereits über einen vorhandenen Build auf den hololens verfügen, wählen Sie ja aus, um diese neuere Version erneut zu installieren.</span><span class="sxs-lookup"><span data-stu-id="73780-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="73780-134">![Remote Computer Bereitstellung für Apps für Microsoft hololens in Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="73780-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="73780-135">Die Anwendung wird auf Ihren hololens installiert und automatisch gestartet.</span><span class="sxs-lookup"><span data-stu-id="73780-135">The application will install and auto launch on your HoloLens.</span></span>
