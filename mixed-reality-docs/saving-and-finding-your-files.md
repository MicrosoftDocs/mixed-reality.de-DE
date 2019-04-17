---
title: Speichern und Suchen nach Dateien
description: So suchen, speichern und Freigeben von Dateien auf HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, mit der Dateiauswahl, Dateien, Fotos, Videos, Bilder, OneDrive, Speicher, Datei-Explorer
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595664"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="b18c8-104">Speichern und Suchen nach Dateien</span><span class="sxs-lookup"><span data-stu-id="b18c8-104">Saving and finding your files</span></span>

<span data-ttu-id="b18c8-105">Dateien können gespeichert und auf ähnliche Weise für andere Windows 10 Desktop und Mobile Geräte verwaltet werden:</span><span class="sxs-lookup"><span data-stu-id="b18c8-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="b18c8-106">Verwenden die Datei-Explorer-app den Zugriff auf lokale Ordner</span><span class="sxs-lookup"><span data-stu-id="b18c8-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="b18c8-107">In einem app eigenen Speicher</span><span class="sxs-lookup"><span data-stu-id="b18c8-107">Within an app's own storage</span></span>
* <span data-ttu-id="b18c8-108">In einem speziellen bekannte Ordner (z. B. die Videos oder Musik-Standardbibliothek)</span><span class="sxs-lookup"><span data-stu-id="b18c8-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="b18c8-109">Verwenden einen Storage-Dienst, die eine app und Datei-Auswahl (z.B. OneDrive) enthält</span><span class="sxs-lookup"><span data-stu-id="b18c8-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="b18c8-110">Mit einem desktop-PC verbunden auf Ihre HoloLens über USB, über die Unterstützung von MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="b18c8-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="b18c8-111">Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="b18c8-111">File Explorer</span></span>

<span data-ttu-id="b18c8-112">Sie können die Datei-Explorer-app verwenden, verschieben und Löschen von Dateien in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b18c8-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="b18c8-113">Wenn Sie alle Dateien im Datei-Explorer nicht angezeigt wird, der "Zuletzt verwendet"-Filter aktiv sein (Uhrsymbol wird im linken Bereich hervorgehoben).</span><span class="sxs-lookup"><span data-stu-id="b18c8-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="b18c8-114">Wählen Sie zum Beheben dieses Problems die **dieses Gerät** dokumentieren Symbol im linken Bereich (unterhalb der Uhrsymbol), oder öffnen Sie das Menü, und wählen **dieses Gerät**.</span><span class="sxs-lookup"><span data-stu-id="b18c8-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="b18c8-115">Dateien in einer app</span><span class="sxs-lookup"><span data-stu-id="b18c8-115">Files within an app</span></span>

<span data-ttu-id="b18c8-116">Wenn eine Anwendung Dateien auf Ihrem Gerät gespeichert wird, können Sie die Anwendung, für den Zugriff darauf.</span><span class="sxs-lookup"><span data-stu-id="b18c8-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="b18c8-117">Wo sind Meine Fotos bzw. Videos?</span><span class="sxs-lookup"><span data-stu-id="b18c8-117">Where are my photos/videos?</span></span>

<span data-ttu-id="b18c8-118">[Mixed Reality-Erfassung](mixed-reality-capture.md) Fotos und Videos werden auf das Gerät die-Ordner Eigene Aufnahmen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="b18c8-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="b18c8-119">Diese können auf das über die [Fotos-app](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="b18c8-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="b18c8-120">Sie können die Fotos-app verwenden, um Ihre Fotos und Videos in OneDrive zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="b18c8-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="b18c8-121">Sie können auch Ihre Fotos und Videos über die Seite Mixed Reality-Erfassen von Aufrufen der [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="b18c8-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="b18c8-122">Dateien von einer anderen app anfordern</span><span class="sxs-lookup"><span data-stu-id="b18c8-122">Requesting files from another app</span></span>

<span data-ttu-id="b18c8-123">Eine Anwendung kann eine Datei speichern oder öffnen Sie eine Datei von einer anderen app über anfordern [Datei Datumsauswahl](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="b18c8-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="b18c8-124">Bekannte Ordner</span><span class="sxs-lookup"><span data-stu-id="b18c8-124">Known folders</span></span>

<span data-ttu-id="b18c8-125">HoloLens unterstützt eine Reihe von [bekannte Ordner](app-model.md#known-folders) , dass apps über die Berechtigung zum Zugriff auf anfordern können.</span><span class="sxs-lookup"><span data-stu-id="b18c8-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="b18c8-126">Dateien in einem Dienst</span><span class="sxs-lookup"><span data-stu-id="b18c8-126">Files in a service</span></span>

<span data-ttu-id="b18c8-127">Eine Datei zu speichern (oder auf Dateien aus zugreifen) einen Dienst, die app, die Verbindung mit dem Dienst muss installiert sein.</span><span class="sxs-lookup"><span data-stu-id="b18c8-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="b18c8-128">Um Dateien zu speichern und auf die Dateien aus OneDrive zugreifen, müssen Sie installieren die [OneDrive-app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="b18c8-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="b18c8-129">MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="b18c8-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="b18c8-130">Ähnlich wie andere mobile Geräte, Herstellen einer Verbindung Ihrer Desktop-PC mit HoloLens und öffnen Datei-Explorer auf dem PC auf Ihre HoloLens-Bibliotheken (Fotos, Videos, Dokumente) zugreifen, für die einfache Übertragung an.</span><span class="sxs-lookup"><span data-stu-id="b18c8-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="b18c8-131">Erläuterungen</span><span class="sxs-lookup"><span data-stu-id="b18c8-131">Clarifications</span></span>

* <span data-ttu-id="b18c8-132">HoloLens unterstützt nicht das Herstellen einer Verbindung mit externen Festplatten oder SD-Karten.</span><span class="sxs-lookup"><span data-stu-id="b18c8-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="b18c8-133">Ab der [Windows 10 April 2018 Update (RS4) für HoloLens](release-notes-april-2018.md), HoloLens enthält die Datei-Explorer für speichern und Verwalten von Dateien im Gerät.</span><span class="sxs-lookup"><span data-stu-id="b18c8-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="b18c8-134">Das Hinzufügen von Datei-Explorer gibt Ihnen außerdem die Möglichkeit, Ihre Dateiauswahl (z. B. Speichern einer Datei auf Ihrem Gerät oder in OneDrive) auswählen.</span><span class="sxs-lookup"><span data-stu-id="b18c8-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
