---
title: Speichern und suchen von Dateien
description: Suchen, speichern und Freigeben von Dateien auf hololens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Vorgehensweise, Dateiauswahl, Dateien, Fotos, Videos, Bilder, onedrive, Storage, Datei-Explorer
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524605"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="1efde-104">Speichern und suchen von Dateien</span><span class="sxs-lookup"><span data-stu-id="1efde-104">Saving and finding your files</span></span>

<span data-ttu-id="1efde-105">Dateien können auf ähnliche Weise wie andere Windows 10 Desktop-und mobile-Geräte gespeichert und verwaltet werden:</span><span class="sxs-lookup"><span data-stu-id="1efde-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="1efde-106">Verwenden der Datei-Explorer-App für den Zugriff auf lokale Ordner</span><span class="sxs-lookup"><span data-stu-id="1efde-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="1efde-107">Innerhalb des eigenen Speichers einer APP</span><span class="sxs-lookup"><span data-stu-id="1efde-107">Within an app's own storage</span></span>
* <span data-ttu-id="1efde-108">In einem speziellen bekannten Ordner (z. b. in der Video-oder Musikbibliothek)</span><span class="sxs-lookup"><span data-stu-id="1efde-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="1efde-109">Verwenden eines Speicher Dienstanbieter mit einer APP und einer Dateiauswahl (z. b. onedrive)</span><span class="sxs-lookup"><span data-stu-id="1efde-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="1efde-110">Verwenden eines Desktop-PCs, der über USB mit ihren hololens verbunden ist, über MTP (Media Transfer Protocol)-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="1efde-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="1efde-111">Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="1efde-111">File Explorer</span></span>

<span data-ttu-id="1efde-112">Sie können die Datei-Explorer-App verwenden, um Dateien aus hololens zu verschieben und zu löschen.</span><span class="sxs-lookup"><span data-stu-id="1efde-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="1efde-113">Wenn im Datei-Explorer keine Dateien angezeigt werden, ist der Filter "zuletzt" möglicherweise aktiv (das Clock-Symbol wird im linken Bereich hervorgehoben).</span><span class="sxs-lookup"><span data-stu-id="1efde-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="1efde-114">Um dieses Problem zu beheben, wählen Sie das Symbol **dieses Geräte** Dokument im linken Bereich aus (unterhalb des Takt Symbols), oder öffnen Sie das Menü, und wählen Sie **dieses Gerät**aus.</span><span class="sxs-lookup"><span data-stu-id="1efde-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="1efde-115">Dateien in einer APP</span><span class="sxs-lookup"><span data-stu-id="1efde-115">Files within an app</span></span>

<span data-ttu-id="1efde-116">Wenn eine Anwendung Dateien auf Ihrem Gerät speichert, können Sie diese Anwendung verwenden, um auf Sie zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="1efde-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="1efde-117">Wo sind meine Fotos/Videos?</span><span class="sxs-lookup"><span data-stu-id="1efde-117">Where are my photos/videos?</span></span>

<span data-ttu-id="1efde-118">Fotos und Videos mit [gemischter Realität](mixed-reality-capture.md) werden im Ordner für die Kamera Rollen des Geräts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1efde-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="1efde-119">Auf diese kann über die [Fotos-App](see-your-photos.md#photos-app)zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="1efde-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="1efde-120">Mit der Fotos-App können Sie Ihre Fotos und Videos mit onedrive synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="1efde-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="1efde-121">Sie können auch auf Ihre Fotos und Videos im [Windows-Geräte Portal](using-the-windows-device-portal.md#mixed-reality-capture)über die Seite zur Erfassung gemischter Realität zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1efde-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="1efde-122">Anfordern von Dateien aus einer anderen APP</span><span class="sxs-lookup"><span data-stu-id="1efde-122">Requesting files from another app</span></span>

<span data-ttu-id="1efde-123">Eine Anwendung kann zum Speichern einer Datei oder zum Öffnen einer Datei aus einer anderen APP über [Datei-Picker](app-model.md#file-pickers)aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="1efde-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="1efde-124">Bekannte Ordner</span><span class="sxs-lookup"><span data-stu-id="1efde-124">Known folders</span></span>

<span data-ttu-id="1efde-125">Hololens unterstützt eine Reihe [bekannter Ordner](app-model.md#known-folders) , für die apps eine Zugriffsberechtigung anfordern können.</span><span class="sxs-lookup"><span data-stu-id="1efde-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="1efde-126">Dateien in einem Dienst</span><span class="sxs-lookup"><span data-stu-id="1efde-126">Files in a service</span></span>

<span data-ttu-id="1efde-127">Zum Speichern einer Datei in einem Dienst (oder zum Zugreifen auf Dateien) muss die dem Dienst zugeordnete App installiert werden.</span><span class="sxs-lookup"><span data-stu-id="1efde-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="1efde-128">Um Dateien in onedrive zu speichern und auf Dateien zuzugreifen, müssen Sie die [onedrive-App](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)installieren.</span><span class="sxs-lookup"><span data-stu-id="1efde-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="1efde-129">MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="1efde-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="1efde-130">Stellen Sie wie bei anderen mobilen Geräten hololens mit Ihrem Desktop-PC her, und öffnen Sie den Datei-Explorer auf dem PC, um auf Ihre hololens-Bibliotheken (Fotos, Videos, Dokumente) zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="1efde-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="1efde-131">Erklärungen</span><span class="sxs-lookup"><span data-stu-id="1efde-131">Clarifications</span></span>

* <span data-ttu-id="1efde-132">Hololens unterstützt keine Verbindung mit externen Festplatten oder SD-Karten.</span><span class="sxs-lookup"><span data-stu-id="1efde-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="1efde-133">Ab [Windows 10 April 2018 Update (RS4) für hololens](release-notes-april-2018.md)enthält hololens den Datei-Explorer zum Speichern und Verwalten von Dateien auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="1efde-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="1efde-134">Durch das Hinzufügen des Datei-Explorers haben Sie auch die Möglichkeit, die Dateiauswahl auszuwählen (z. b. das Speichern einer Datei auf Ihrem Gerät oder onedrive).</span><span class="sxs-lookup"><span data-stu-id="1efde-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
