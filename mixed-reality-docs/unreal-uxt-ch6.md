---
title: 6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator
description: Teil 6 eines Tutorials zum Erstellen einer einfachen Schach-App mit Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519966"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="b07cd-104">6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator</span><span class="sxs-lookup"><span data-stu-id="b07cd-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="b07cd-105">In diesem Abschnitt erfahren Sie Schritt für Schritt, wie Sie Ihre App für die Ausführung auf einem HoloLens 2-Gerät oder in einem Emulator vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="b07cd-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="b07cd-106">Wenn Sie über ein Gerät verfügen, können Sie die App entweder von Ihrem Computer an das Gerät streamen oder die App verpacken, um sie direkt auf dem Gerät auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b07cd-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="b07cd-107">Wenn Sie über kein Gerät verfügen, müssen Sie die App verpacken, um sie im Emulator ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="b07cd-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="b07cd-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="b07cd-108">Objectives</span></span>

* <span data-ttu-id="b07cd-109">Streamen der App an HoloLens 2 mittels holografischem App-Remoting (nur Gerät)</span><span class="sxs-lookup"><span data-stu-id="b07cd-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="b07cd-110">Verpacken und Bereitstellen der App auf einem HoloLens 2-Gerät oder in einem Emulator</span><span class="sxs-lookup"><span data-stu-id="b07cd-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="b07cd-111">Streamen (nur Gerät)</span><span class="sxs-lookup"><span data-stu-id="b07cd-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="b07cd-112">Installieren Sie den **Holographic Remoting-Player** aus dem Microsoft Store auf Ihrem HoloLens 2-Gerät, und führen Sie die App aus.</span><span class="sxs-lookup"><span data-stu-id="b07cd-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="b07cd-113">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="b07cd-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="b07cd-114">Aktivieren Sie im Abschnitt „Holographic Remoting“ (Holografisches Remoting) das Kontrollkästchen zum Aktivieren des Remotings, und starten Sie den Editor neu.</span><span class="sxs-lookup"><span data-stu-id="b07cd-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="b07cd-115">Geben Sie die IP-Adresse Ihres Geräts ein, und klicken Sie auf „Connect“ (Verbinden).</span><span class="sxs-lookup"><span data-stu-id="b07cd-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="b07cd-116">Wenn die Verbindung hergestellt wurde, klicken Sie in Ihrem UE4-Editor rechts neben der Schaltfläche „Play“ (Spielen) auf den Dropdownpfeil, und wählen Sie „VR Preview“ (VR-Vorschau) aus.</span><span class="sxs-lookup"><span data-stu-id="b07cd-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="b07cd-117">Verpacken und Bereitstellen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="b07cd-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="b07cd-118">Wenn Sie zum ersten Mal eine Unreal-App für HoloLens verpacken, müssen Sie unterstützende Dateien aus dem Epic-Startprogramm herunterladen.</span><span class="sxs-lookup"><span data-stu-id="b07cd-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="b07cd-119">Wechseln Sie dazu zur Registerkarte **Library** (Bibliothek) im Startprogramm von Epic Games.</span><span class="sxs-lookup"><span data-stu-id="b07cd-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="b07cd-120">Wählen Sie den Dropdownpfeil neben **Launch** (Starten) und dann **Options** (Optionen) aus.</span><span class="sxs-lookup"><span data-stu-id="b07cd-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="b07cd-121">Wählen Sie unter **Target Platforms** (Zielplattformen) **HoloLens 2** aus, und klicken Sie auf **Apply** (Übernehmen).</span><span class="sxs-lookup"><span data-stu-id="b07cd-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="b07cd-122">![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="b07cd-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="b07cd-123">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="b07cd-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="b07cd-124">Geben Sie unter **Project > Description > About > Project Name** („Projekt“ > „Beschreibung“ > „Info“ > „Projektname“) einen Namen für Ihr Projekt an.</span><span class="sxs-lookup"><span data-stu-id="b07cd-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="b07cd-125">Geben Sie unter **Project > Description > Publisher > Company Distinguished Name** („Projekt“ > „Beschreibung“ > „Herausgeber“ > „Definierter Name des Unternehmens“) Folgendes ein: CN={NAME DES UNTERNEHMENS}.</span><span class="sxs-lookup"><span data-stu-id="b07cd-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="b07cd-126">Wenn Sie eines dieser Felder leer lassen, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="b07cd-126">Leaving either of these fields blank will result in an error.</span></span> 

![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="b07cd-128">Wählen Sie unter **Platforms > HoloLens** („Plattformen“ > „HoloLens“) je nach gewünschtem Ziel „Emulation“ und/oder „Device“ (Gerät) aus.</span><span class="sxs-lookup"><span data-stu-id="b07cd-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="b07cd-129">Klicken Sie im Abschnitt **Packaging** (Verpacken) neben **Signing Certificate** (Signaturzertifikat) auf die Schaltfläche **Generate new** (Neu generieren), um ein neues Signaturzertifikat zu generieren.</span><span class="sxs-lookup"><span data-stu-id="b07cd-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="b07cd-130">Kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="b07cd-130">Return to the Main window.</span></span>

![Projekteinstellungen: Plattformen (HoloLens)](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="b07cd-132">Navigieren Sie zu **File > Package Project** („Datei“ > „Projekt verpacken“), und wählen Sie **HoloLens** aus.</span><span class="sxs-lookup"><span data-stu-id="b07cd-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="b07cd-133">Erstellen Sie einen neuen Ordner zum Speichern Ihres Pakets, und klicken Sie auf **Select Folder** (Ordner auswählen).</span><span class="sxs-lookup"><span data-stu-id="b07cd-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="b07cd-134">Nachdem die App erfolgreich verpackt wurde, öffnen Sie das **Windows-Geräteportal**, navigieren Sie zu **Ansichten > Apps**, und suchen Sie nach dem Abschnitt **Deploy apps** (Apps bereitstellen).</span><span class="sxs-lookup"><span data-stu-id="b07cd-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="b07cd-135">Klicken Sie auf **Durchsuchen...** , und navigieren Sie zur Datei **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="b07cd-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="b07cd-136">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="b07cd-136">Click **Open**.</span></span> 

    * <span data-ttu-id="b07cd-137">Wenn Sie die App zum ersten Mal auf Ihrem Gerät installieren, aktivieren Sie das Kontrollkästchen neben **Allow me to select framework packages** (Auswählen von Framework-Paketen zulassen).</span><span class="sxs-lookup"><span data-stu-id="b07cd-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="b07cd-138">Schließen Sie im nächsten Dialogfeld die entsprechende VCLibs-APPX-Datei ein („arm64“ für Gerät, „x64“ für Emulator).</span><span class="sxs-lookup"><span data-stu-id="b07cd-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="b07cd-139">Klicken Sie auf **Install** (Installieren).</span><span class="sxs-lookup"><span data-stu-id="b07cd-139">Click **Install**</span></span>

<span data-ttu-id="b07cd-140">Damit ist dieses Tutorial abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="b07cd-140">Congratulations on finishing this tutorial!</span></span>  