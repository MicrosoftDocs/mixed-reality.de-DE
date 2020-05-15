---
title: 6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator
description: Teil 6 eines Tutorials zum Erstellen einer einfachen Schach-App mit Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840379"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="ceb27-104">6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator</span><span class="sxs-lookup"><span data-stu-id="ceb27-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="ceb27-105">In diesem Abschnitt erfahren Sie Schritt für Schritt, wie Sie Ihre App für die Ausführung auf einem HoloLens 2-Gerät oder in einem Emulator vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="ceb27-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="ceb27-106">Wenn Sie über ein Gerät verfügen, können Sie die App entweder von Ihrem Computer an das Gerät streamen oder die App verpacken, um sie direkt auf dem Gerät auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ceb27-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="ceb27-107">Wenn Sie über kein Gerät verfügen, müssen Sie die App verpacken, um sie im Emulator ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="ceb27-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="ceb27-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="ceb27-108">Objectives</span></span>

* <span data-ttu-id="ceb27-109">Streamen der App an HoloLens 2 mittels holografischem App-Remoting (nur Gerät)</span><span class="sxs-lookup"><span data-stu-id="ceb27-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="ceb27-110">Verpacken und Bereitstellen der App auf einem HoloLens 2-Gerät oder in einem Emulator</span><span class="sxs-lookup"><span data-stu-id="ceb27-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="ceb27-111">Streamen (nur Gerät)</span><span class="sxs-lookup"><span data-stu-id="ceb27-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="ceb27-112">Installieren Sie den **Holographic Remoting-Player** aus dem Microsoft Store auf Ihrem HoloLens 2-Gerät, und führen Sie die App aus.</span><span class="sxs-lookup"><span data-stu-id="ceb27-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="ceb27-113">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="ceb27-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="ceb27-114">Aktivieren Sie im Abschnitt „Holographic Remoting“ (Holografisches Remoting) das Kontrollkästchen zum Aktivieren des Remotings, und starten Sie den Editor neu.</span><span class="sxs-lookup"><span data-stu-id="ceb27-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="ceb27-115">Geben Sie die IP-Adresse Ihres Geräts ein, und klicken Sie auf „Connect“ (Verbinden).</span><span class="sxs-lookup"><span data-stu-id="ceb27-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="ceb27-116">Wenn die Verbindung hergestellt wurde, klicken Sie in Ihrem UE4-Editor rechts neben der Schaltfläche „Play“ (Spielen) auf den Dropdownpfeil, und wählen Sie „VR Preview“ (VR-Vorschau) aus.</span><span class="sxs-lookup"><span data-stu-id="ceb27-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="ceb27-117">Verpacken und Bereitstellen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ceb27-117">Package and deploy your app</span></span> 

1.  <span data-ttu-id="ceb27-118">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="ceb27-118">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="ceb27-119">Geben Sie unter **Project > Description > About > Project Name** („Projekt“ > „Beschreibung“ > „Info“ > „Projektname“) einen Namen für Ihr Projekt an.</span><span class="sxs-lookup"><span data-stu-id="ceb27-119">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="ceb27-120">Geben Sie unter **Project > Description > Publisher > Company Distinguished Name** („Projekt“ > „Beschreibung“ > „Herausgeber“ > „Definierter Name des Unternehmens“) Folgendes ein: CN={NAME DES UNTERNEHMENS}.</span><span class="sxs-lookup"><span data-stu-id="ceb27-120">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="ceb27-121">Wenn Sie eines dieser Felder leer lassen, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="ceb27-121">Leaving either of these fields blank will result in an error.</span></span> 

![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="ceb27-123">Wählen Sie unter **Platforms > HoloLens** („Plattformen“ > „HoloLens“) je nach gewünschtem Ziel „Emulation“ und/oder „Device“ (Gerät) aus.</span><span class="sxs-lookup"><span data-stu-id="ceb27-123">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="ceb27-124">Klicken Sie im Abschnitt **Packaging** (Verpacken) neben **Signing Certificate** (Signaturzertifikat) auf die Schaltfläche **Generate new** (Neu generieren), um ein neues Signaturzertifikat zu generieren.</span><span class="sxs-lookup"><span data-stu-id="ceb27-124">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="ceb27-125">Kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="ceb27-125">Return to the Main window.</span></span>

![Projekteinstellungen: Plattformen (HoloLens)](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="ceb27-127">Navigieren Sie zu **File > Package Project** („Datei“ > „Projekt verpacken“), und wählen Sie **HoloLens** aus.</span><span class="sxs-lookup"><span data-stu-id="ceb27-127">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="ceb27-128">Erstellen Sie einen neuen Ordner zum Speichern Ihres Pakets, und klicken Sie auf **Select Folder** (Ordner auswählen).</span><span class="sxs-lookup"><span data-stu-id="ceb27-128">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="ceb27-129">Nachdem die App erfolgreich verpackt wurde, öffnen Sie das **Windows-Geräteportal**, navigieren Sie zu **Ansichten > Apps**, und suchen Sie nach dem Abschnitt **Deploy apps** (Apps bereitstellen).</span><span class="sxs-lookup"><span data-stu-id="ceb27-129">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="ceb27-130">Klicken Sie auf **Durchsuchen...** , und navigieren Sie zur Datei **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="ceb27-130">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="ceb27-131">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="ceb27-131">Click **Open**.</span></span> 

    * <span data-ttu-id="ceb27-132">Wenn Sie die App zum ersten Mal auf Ihrem Gerät installieren, aktivieren Sie das Kontrollkästchen neben **Allow me to select framework packages** (Auswählen von Framework-Paketen zulassen).</span><span class="sxs-lookup"><span data-stu-id="ceb27-132">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="ceb27-133">Schließen Sie im nächsten Dialogfeld die entsprechende VCLibs-APPX-Datei ein („arm64“ für Gerät, „x64“ für Emulator).</span><span class="sxs-lookup"><span data-stu-id="ceb27-133">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="ceb27-134">Klicken Sie auf **Install** (Installieren).</span><span class="sxs-lookup"><span data-stu-id="ceb27-134">Click **Install**</span></span>

<span data-ttu-id="ceb27-135">Damit ist dieses Tutorial abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ceb27-135">Congratulations on finishing this tutorial!</span></span>  