---
title: MR und Azure 306 - Video-Streaming
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Media Services in einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Media Services Videostreaming, 360, immersive vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594020"
---
>[!NOTE]
><span data-ttu-id="ce8ec-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ce8ec-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ce8ec-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ce8ec-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ce8ec-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ce8ec-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="ce8ec-110">MR und Azure 306: Streaming-Videos</span><span class="sxs-lookup"><span data-stu-id="ce8ec-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="ce8ec-111">![Endprodukt-start](images/AzureLabs-Lab6-00.png)
![Endprodukt-starten](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="ce8ec-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="ce8ec-112">In diesem Kurs erfahren Sie, wie Azure Media Services in eine Windows Mixed Reality-VR-Erfahrung, dass Stream-360-Grad-Videowiedergabe auf immersive Headsets verbinden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="ce8ec-113">**Azure Media Services** sind eine Sammlung von Diensten, die Sie Videostreamingdienste in broadcastqualität streamen Videodienste auf ein größeres Publikum auf den heute gängigen Mobilgeräten erreichen kann.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="ce8ec-114">Weitere Informationen finden Sie auf die [Azure Media Services-Seite](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="ce8ec-115">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung, die für die folgenden Aufgaben werden können:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="ce8ec-116">Abrufen von einem 360-Grad-Video von einer **Azure Storage**, über die **Azure Media Services**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="ce8ec-117">Zeigen Sie die abgerufenen 360-Grad-Video in einem Unity-Szene.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="ce8ec-118">Navigieren Sie zwischen den beiden Szenen, mit zwei verschiedenen Videos.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="ce8ec-119">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ce8ec-120">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ce8ec-121">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="ce8ec-122">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="ce8ec-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ce8ec-123">Kurs</span><span class="sxs-lookup"><span data-stu-id="ce8ec-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ce8ec-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ce8ec-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ce8ec-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="ce8ec-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ce8ec-126">MR und Azure 306: Streaming-Videos</span><span class="sxs-lookup"><span data-stu-id="ce8ec-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="ce8ec-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ce8ec-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="ce8ec-128">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ce8ec-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ce8ec-129">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ce8ec-130">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ce8ec-131">Sie können zur Verwendung der neuesten Software, wie in der [installieren Sie die Tools-Artikel](install-the-tools.md), obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="ce8ec-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ce8ec-132">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ce8ec-133">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="ce8ec-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ce8ec-134">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="ce8ec-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ce8ec-135">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="ce8ec-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ce8ec-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ce8ec-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ce8ec-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ce8ec-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ce8ec-138">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ce8ec-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="ce8ec-139">Zugriff auf das Internet für den Abruf von Setup- und Azure</span><span class="sxs-lookup"><span data-stu-id="ce8ec-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="ce8ec-140">Zwei 360-Grad-Videos in mp4-Format (finden Sie einige Videos lizenzgebührenfreie [auf dieser Downloadseite](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="ce8ec-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ce8ec-141">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="ce8ec-141">Before you start</span></span>

1.  <span data-ttu-id="ce8ec-142">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="ce8ec-143">Richten Sie ein und Testen Sie Ihrer Mixed Reality Kopfhörer Immersive.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce8ec-144">Sie **nicht** Motion-Controller für dieses Kurses erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="ce8ec-145">Wenn Sie die Einrichtung der Immersive Kopfhörer unterstützen müssen, klicken Sie auf [Link zum Einrichten von Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="ce8ec-146">Kapitel 1: das Azure-Portal: Erstellen des Azure-Speicherkontos</span><span class="sxs-lookup"><span data-stu-id="ce8ec-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="ce8ec-147">Verwenden der **Azure Storage-Dienst**, Sie benötigen zum Erstellen und Konfigurieren einer **Speicherkonto** im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="ce8ec-148">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce8ec-149">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ce8ec-150">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ce8ec-151">Sobald Sie angemeldet sind, klicken Sie auf **Speicherkonten** im linken Menü.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="ce8ec-153">Auf der **Speicherkonten** Registerkarte, klicken Sie auf **hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="ce8ec-155">In der **Storage-Konto erstellen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="ce8ec-156">Fügen Sie eine **Namen** für Ihr Konto bedenken, dass dieses Feld akzeptiert nur Ziffern und Kleinbuchstaben zulässig.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="ce8ec-157">Für **Bereitstellungsmodell** wählen **RM**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="ce8ec-158">Für **Kontoart**Option **Speicher (Allgemein v1)**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="ce8ec-159">Für **Leistung**Option **Standard\*.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="ce8ec-160">Für **Replikation** wählen **lokal redundanter Speicher (LRS)**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="ce8ec-161">Lassen Sie **sichere Übertragung erforderlich** als **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="ce8ec-162">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="ce8ec-163">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="ce8ec-164">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="ce8ec-165">Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ce8ec-166">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ce8ec-167">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="ce8ec-168">Sie benötigen, um sicherzustellen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="ce8ec-170">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="ce8ec-171">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="ce8ec-173">Sie müssen an diesem Punkt nicht, führen die Ressource, verschieben Sie einfach zum nächsten Kapitel zu können.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="ce8ec-174">Kapitel 2: das Azure-Portal: Erstellen von Media Service</span><span class="sxs-lookup"><span data-stu-id="ce8ec-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="ce8ec-175">Um die Azure Media Services verwenden zu können, müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden (bei dem der Besitzer des Kontos muss ein Administrator sein).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="ce8ec-176">Klicken Sie im Azure-Portal auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach **Mediendienst,** drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="ce8ec-177">Die Ressource, die Sie verwenden möchten verfügt über ein Symbol "rosa"; Klicken Sie hierauf, um eine neue Seite anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="ce8ec-179">Die neue Seite bietet eine Beschreibung der **Mediendienst**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="ce8ec-180">Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="ce8ec-182">Nachdem Sie auf geklickt haben **erstellen** ein Panel wird angezeigt, in denen Sie einige Details zu Ihrem neuen Mediendienst bereitstellen müssen:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="ce8ec-183">Fügen Sie Ihre bevorzugte **Kontoname** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="ce8ec-184">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="ce8ec-185">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ce8ec-186">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ce8ec-187">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="ce8ec-188">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Azure-Ressourcengruppen verwalten](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="ce8ec-189">Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ce8ec-190">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ce8ec-191">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="ce8ec-192">Für die **Speicherkonto** auf die **wählen Sie bitte...**  Abschnitt, und klicken Sie dann die **Speicherkonto** Sie im letzten Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="ce8ec-193">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="ce8ec-194">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-194">Click **Create**.</span></span>

        ![Das Azure-Portal](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="ce8ec-196">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="ce8ec-197">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="ce8ec-199">Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-199">Click on the notification to explore your new Service instance.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="ce8ec-201">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="ce8ec-202">Klicken Sie auf der Seite der neue Media Service, innerhalb des Bereichs auf der linken Seite auf die **Assets** Link, der in der Mitte nach unten geht.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="ce8ec-203">Klicken Sie auf der nächsten Seite in der oberen linken Ecke der Seite auf **hochladen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="ce8ec-205">Klicken Sie auf die **Ordner** Symbol, um Ihre Dateien auszuwählen, das zuerst 360 Video, das Sie streamen möchten.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="ce8ec-206">Führen Sie dies [Link zum Herunterladen von ein beispielvideo](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="ce8ec-208">Lange Dateinamen verursacht möglicherweise Probleme mit dem Encoder: um sicherzustellen, dass Videos keine Probleme, daher sollten Sie mit den Namen Ihrer Videodatei verkürzen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="ce8ec-209">Die Statusanzeige wird grün, wenn das Video Hochladen abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="ce8ec-211">Klicken Sie auf der obige Text (**Yourservicename - Assets**) zum Zurückgeben der **Assets** Seite.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="ce8ec-212">Beachten Sie, dass Ihr Video wurde erfolgreich hochgeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="ce8ec-213">Klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-213">Click on it.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="ce8ec-215">Die Seite, der Sie zur umgeleitet werden zeigt, dass ausführliche Informationen zu Ihrem Video.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="ce8ec-216">In der Lage, Ihr Video zu verwenden, müssen Sie es, zu codieren, indem Sie auf, die **Encode** auf der oberen linken Ecke der Seite.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="ce8ec-218">Ein neuer Bereich wird auf der rechten Seite angezeigt, sodass Sie zum Codieren der Optionen für die Datei können.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="ce8ec-219">Legen Sie die folgenden Eigenschaften (einige wird bereits standardmäßig festgelegt):</span><span class="sxs-lookup"><span data-stu-id="ce8ec-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="ce8ec-220">**Media Encoder-Name *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="ce8ec-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="ce8ec-221">**Codierungsvoreinstellung *Content Adaptive Multiple Bitrate MP4***</span><span class="sxs-lookup"><span data-stu-id="ce8ec-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="ce8ec-222">**Auftragsname *Media Encoder Standard Verarbeitung Video1.mp4***</span><span class="sxs-lookup"><span data-stu-id="ce8ec-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="ce8ec-223">**Name des ausgabemedienobjekts *Video1.mp4 – Media Encoder Standard codiert***</span><span class="sxs-lookup"><span data-stu-id="ce8ec-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Das Azure-Portal](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="ce8ec-225">Klicken Sie auf die Schaltfläche **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="ce8ec-226">Sie sehen eine Leiste mit **Codierung Auftrags hinzugefügt**, klicken Sie auf diese Leiste, und ein Bereich wird angezeigt, mit der Codierung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-17.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="ce8ec-229">Warten Sie, bis der Auftrag abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="ce8ec-230">Wenn dies abgeschlossen ist, können Sie den Bereich mit der "X" in der rechten oberen Bereich zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-19.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ce8ec-233">Der Zeitaufwand, hängt von der Größe Ihres Videos ab.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="ce8ec-234">Dieser Vorgang kann einige Zeit dauern.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="ce8ec-235">Nun, dass die codierte Version des Videos erstellt wurde, können Sie darauf, um darauf zugegriffen werden kann veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="ce8ec-236">Zu diesem Zweck klicken Sie auf den blauen Link **Assets** um zurück auf der Seite "Bestand" zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="ce8ec-238">Sehen Sie Ihr Video zusammen mit einem anderen vom \*\*Ressourcentyp \*Multi-Bitrate-MP4\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="ce8ec-240">Sie möglicherweise feststellen, dass das neue Medienobjekt, zusammen mit Ihrer ersten Video *unbekannte*, und weist '0' Bytes für sie **Größe**, aktualisieren Sie das Fenster für die sie aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="ce8ec-241">Klicken Sie auf diese neue Anlage.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-241">Click this new asset.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="ce8ec-243">Sie sehen einen ähnlichen Bereich für die, die Sie verwendet werden, bevor dies auf eine andere Ressource ist.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="ce8ec-244">Klicken Sie auf die **veröffentlichen** Schaltfläche am oben in der Mitte der Seite.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="ce8ec-246">Werden Sie aufgefordert, Sie legen eine **Locator**, dies ist der Einstiegspunkt, auf die Datei/s in Ihren Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="ce8ec-247">Legen für Ihr Szenario die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="ce8ec-248">**Locatortyp** > **Progressive**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="ce8ec-249">Die **Datum** und **Zeit** festgelegt, die Sie aus Ihrer aktuellen Datum, zu einem Zeitpunkt in der Zukunft (100 Jahre in diesem Fall).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="ce8ec-250">Lassen Sie unverändert verwenden oder ändern Sie ihn entsprechend.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce8ec-251">Weitere Informationen zu Locators, und was Sie auswählen können, finden Sie auf die [Azure Media Services-Dokumentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="ce8ec-252">Am unteren Bereich, klicken Sie auf die **hinzufügen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="ce8ec-254">Ihr Video wurde veröffentlicht und kann mithilfe des zugehörigen Endpunkts gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="ce8ec-255">Weiter unten die Seite ist eine **Dateien** Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="ce8ec-256">Dies ist das, wo die verschiedenen codierten Versionen Ihres Videos werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="ce8ec-257">Wählen Sie die höchste mögliche Lösung eine (in der Abbildung unten sie ist die 1920 x 960-Datei), und klicken Sie dann ein Bereich auf der rechten Seite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="ce8ec-258">Dort sehen Sie eine **Download-URL**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="ce8ec-259">Kopieren Sie diese **Endpunkt** , wie Sie es später in Ihrem Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-26.png)    

    ![Das Azure-Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="ce8ec-262">Drücken Sie die **spielen** Schaltfläche, um das Video abspielen, und Testen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="ce8ec-263">Sie müssen jetzt das zweite Video hochladen, das Sie in dieser Übung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="ce8ec-264">Führen Sie die Schritte oben, wiederholen Sie den Vorgang für das zweite Video aus.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="ce8ec-265">Stellen Sie sicher, Sie kopieren das zweite **Endpunkt** auch.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="ce8ec-266">Verwenden Sie die folgenden [Link zum Herunterladen von einem zweiten Video](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="ce8ec-267">Nachdem beide Videos veröffentlicht wurden, sind Sie bereit sind, finden Sie im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="ce8ec-268">Kapitel 3 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="ce8ec-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="ce8ec-269">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem Mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ce8ec-270">Open **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-270">Open **Unity** and click **New**.</span></span> 

    ![Das Azure-Portal](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="ce8ec-272">Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **MR\_360VideoStreaming.**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="ce8ec-273">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ce8ec-274">Legen Sie den Speicherort, an eine Position, die für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ce8ec-275">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-275">Then, click **Create project**.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="ce8ec-277">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="ce8ec-278">Wechseln Sie zu ***bearbeiten* *Voreinstellungen*** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ce8ec-279">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ce8ec-280">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-280">Close the **Preferences** window.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="ce8ec-282">Öffnen Sie als Nächstes ***Datei* *Buildeinstellungen*** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="ce8ec-283">Außerdem stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-283">Also make sure that:</span></span>

    1. <span data-ttu-id="ce8ec-284">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="ce8ec-285">**Buildtyp** nastaven NA hodnotu **D3D.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="ce8ec-286">**SDK** nastaven NA hodnotu **zuletzt installiert.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="ce8ec-287">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installiert.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="ce8ec-288">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="ce8ec-289">Aber keine Sorge, über das Einrichten von **Szenen** jetzt, wie Sie diese später eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="ce8ec-290">Die übrigen Einstellungen sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-290">The remaining settings should be left as default for now.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="ce8ec-292">In der **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="ce8ec-293">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ce8ec-294">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ce8ec-295">**Scripting** **Laufzeitversion** muss **stabile** (.NET 3.5 entspricht).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="ce8ec-296">**Back-End-Scripting** muss **.NET.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="ce8ec-297">**API-Kompatibilitätsebene** muss **.NET 4.6.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="ce8ec-299">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="ce8ec-301">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ce8ec-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-302">**InternetClient**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="ce8ec-304">Wenn Sie diese Änderungen vorgenommen haben, schließen Sie die **Buildeinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="ce8ec-305">Speichern Sie das Projekt \**Datei* \*speichern Projekt\*\*.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="ce8ec-306">Kapitel 4: Importieren des InsideOutSphere Unity-Pakets</span><span class="sxs-lookup"><span data-stu-id="ce8ec-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce8ec-307">Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung **Kapitel 5**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="ce8ec-308">Sie müssen immer noch ein Unity-Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="ce8ec-309">Für diesen Kurs an, Sie ein Unity Asset-Paket herunterladen müssen, aufgerufen [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="ce8ec-310">Gewusst-wie-Import der **vstu**:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="ce8ec-311">Mit dem Sie Unity-Dashboard, klicken Sie auf **Assets** klicken Sie dann im Menü am oberen Rand des Bildschirms auf **Paket importieren > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="ce8ec-313">Verwenden Sie die Dateiauswahl zum Auswählen der **InsideOutSphere.unitypackage** packen, und klicken Sie auf **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="ce8ec-314">Eine Liste der Komponenten für dieses Medienobjekt wird Ihnen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="ce8ec-315">Bestätigen Sie den Import, indem Sie auf **importieren**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-315">Confirm the import by clicking **Import**.</span></span>

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="ce8ec-317">Anschließend importieren, werden Sie feststellen, dass drei neue Ordner **Materialien**, **Modelle**, und **Prefabs**, wurden hinzugefügt, um Ihre **Assets**Ordner.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="ce8ec-318">Diese Art von Struktur ist typisch für ein Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="ce8ec-320">Öffnen der **Modelle** Ordner, und Sie sehen, die die **InsideOutSphere** Modell importiert wurde.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="ce8ec-321">Innerhalb der **Materialien** Ordner Sie finden die **InsideOutSpheres** Material *lambert1*, sowie ein Material namens *ButtonMaterial*, die von der GazeButton, die in Kürze angezeigt werden, verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="ce8ec-322">Die **prefabs (Vorlagen)** Ordner enthält die **InsideOutSphere** Prefab enthält sowohl die **InsideOutSphere** *Modell* und die  *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="ce8ec-323">**Es ist kein Code enthalten**, Schreiben Sie Code anhand dieses Kurses.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="ce8ec-324">In der **Hierarchie**, wählen die **Main Camera** Objekt aus, und aktualisieren Sie die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="ce8ec-325">**Transform**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-325">**Transform**</span></span>

        1.  <span data-ttu-id="ce8ec-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="ce8ec-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="ce8ec-328">Skalierung **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="ce8ec-329">**Kamera**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-329">**Camera**</span></span>

        1. <span data-ttu-id="ce8ec-330">**Deaktivieren Sie Flags**: Volltonfarbe entspricht.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="ce8ec-331">**Clipping Planes**: In der Nähe von: 0,1, weit: 6.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="ce8ec-333">Navigieren Sie zu der **Prefab** Ordner, und ziehen Sie dann die **InsideOutSphere** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="ce8ec-335">Erweitern Sie die **InsideOutSphere** -Objekts innerhalb der **Hierarchie** durch Klicken auf den kleinen Pfeil daneben.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="ce8ec-336">Sie sehen eine **untergeordneten** Objekt unter dem Namen **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="ce8ec-337">Dies wird verwendet um Szenen und somit auf Videos zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-337">This will be used to change scenes and thus videos.</span></span>

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="ce8ec-339">Klicken Sie im Inspektor-Fenster auf die **InsideOutSphere**Transformationskomponente, stellen Sie sicher, dass die folgenden Eigenschaften festgelegt sind:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="ce8ec-340">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="ce8ec-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ce8ec-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-341">**X** 0</span></span>  |          <span data-ttu-id="ce8ec-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-342">**Y** 0</span></span>          |  <span data-ttu-id="ce8ec-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="ce8ec-344">TRANSFORM - DREHUNG</span><span class="sxs-lookup"><span data-stu-id="ce8ec-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ce8ec-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-345">**X** 0</span></span>  |          <span data-ttu-id="ce8ec-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="ce8ec-346">**Y** -50</span></span>        |  <span data-ttu-id="ce8ec-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="ce8ec-348">TRANSFORM - SKALIERUNG</span><span class="sxs-lookup"><span data-stu-id="ce8ec-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="ce8ec-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-349">**X** 1</span></span>   |          <span data-ttu-id="ce8ec-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-350">**Y** 1</span></span>          |  <span data-ttu-id="ce8ec-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-351">**Z** 1</span></span>  |

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="ce8ec-353">Klicken Sie auf die **GazeButton** untergeordnetes Objekt, und legen dessen **transformieren** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="ce8ec-354">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="ce8ec-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ce8ec-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="ce8ec-355">**X** 3.6</span></span>|          <span data-ttu-id="ce8ec-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="ce8ec-356">**Y** 1.3</span></span>        |  <span data-ttu-id="ce8ec-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="ce8ec-358">TRANSFORM - DREHUNG</span><span class="sxs-lookup"><span data-stu-id="ce8ec-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ce8ec-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-359">**X** 0</span></span>  |          <span data-ttu-id="ce8ec-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-360">**Y** 0</span></span>          |  <span data-ttu-id="ce8ec-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="ce8ec-362">TRANSFORM - SKALIERUNG</span><span class="sxs-lookup"><span data-stu-id="ce8ec-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="ce8ec-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-363">**X** 1</span></span>   |          <span data-ttu-id="ce8ec-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-364">**Y** 1</span></span>          |  <span data-ttu-id="ce8ec-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-365">**Z** 1</span></span>  |

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="ce8ec-367">Kapitel 5 – erstellen Sie die VideoController-Klasse</span><span class="sxs-lookup"><span data-stu-id="ce8ec-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="ce8ec-368">Die **VideoController** Klasse hostet die beiden video Endpunkte, die zum Streamen des Inhalts aus der Azure Media Services verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="ce8ec-369">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-369">To create this class:</span></span>

1.  <span data-ttu-id="ce8ec-370">Mit der rechten Maustaste den **Ordner "Assets"** befindet sich in der **Projekt** Bereich, und klicken Sie auf **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="ce8ec-371">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-371">Name the folder **Scripts**.</span></span>

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-43.png)

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="ce8ec-374">Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner aus, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="ce8ec-375">Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen > C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="ce8ec-376">Nennen Sie das Skript **VideoController**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-376">Name the script **VideoController**.</span></span>

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="ce8ec-378">Doppelklicken Sie auf dem neuen **VideoController** Skript öffnen Sie ihn mit **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="ce8ec-380">Aktualisieren Sie die Namespaces am Anfang der Codedatei wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="ce8ec-381">Geben Sie die folgenden Variablen in der **VideoController** -Klasse ermöglicht zusammen mit den **Awake()** Methode:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="ce8ec-382">Jetzt ist die Zeit, die Endpunkte aus Ihren Azure Media Services-Videos einzugeben:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="ce8ec-383">Die erste in der *video1endpoint* Variable.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="ce8ec-384">Das zweite in der *video2endpoint* Variable.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="ce8ec-385">Es ist ein bekanntes Problem mit der Verwendung von *Https* in Unity, mit der Version 2017.4.1f1.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="ce8ec-386">Wenn die Videos einen Fehler auf Play zur Verfügung, versuchen Sie es stattdessen mit "http".</span><span class="sxs-lookup"><span data-stu-id="ce8ec-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="ce8ec-387">Als Nächstes die **Start()** -Methode muss bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="ce8ec-388">Diese Methode wird jedes Mal, wenn der Benutzer Szene (wechseln daher das Video) wechselt, indem Sie die Schaltfläche mit den bestaunen ansehen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="ce8ec-389">Nach der **Start()** -Methode, fügen Sie der **PlayVideo()** *IEnumerator* -Methode, die verwendet wird, um Videos zu starten, nahtlos (also ohne Stottern zu sehen ist).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="ce8ec-390">Die letzte Methode, die für diese Klasse ist, müssen Sie die **ChangeScene()** -Methode, die zum Wechseln zwischen Szenen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="ce8ec-391">Die **ChangeScene()** -Methode verwendet eine praktische C\# Feature mit dem Namen der *Bedingungsoperator*.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="ce8ec-392">Dies ermöglicht die Bedingungen, die überprüft werden, und klicken Sie dann Werte zurückgegeben, auf das Ergebnis der Überprüfung in einer einzelnen Anweisung basiert.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="ce8ec-393">Gehen Sie folgendermaßen vor [Link Weitere Informationen zum bedingten Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="ce8ec-394">Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="ce8ec-395">Zurück in die Unity-Editor zu klicken und ziehen Sie die **VideoController** Klasse [from] {.underline} die **Skripts** Ordner, um die **Main Camera** -Objekt in der  **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="ce8ec-396">Klicken Sie auf die **Main Camera** und sehen Sie sich die **Inspektor Bereich**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="ce8ec-397">Sie werden feststellen, dass in der neu hinzugefügten Komponente, ein Feld mit einem leeren Wert vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="ce8ec-398">Dies ist ein Verweisfeld, das auf die öffentlichen Variablen innerhalb des Codes.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="ce8ec-399">Ziehen Sie die **InsideOutSphere** -Objekt aus der **Hierarchie Bereich** auf die **Kugel** slot, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="ce8ec-400">![Erstellen Sie die Klasse VideoController](images/AzureLabs-Lab6-47.png)
    ![erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="ce8ec-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="ce8ec-401">Kapitel 6: Erstellen Sie die Blicke-Klasse</span><span class="sxs-lookup"><span data-stu-id="ce8ec-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="ce8ec-402">Diese Klasse ist zuständig für das Erstellen einer **Raycast** Beprojected weitergeleitet wird, aus der **Main Camera**, welches Objekt erkannt, wird der Benutzer ansehen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="ce8ec-403">In diesem Fall die **Raycast** benötigen, um festzustellen, ob der Benutzer ansieht der **GazeButton** Objekt in der Szene, und lösen Sie ein Verhalten.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="ce8ec-404">Zum Erstellen dieser Klasse:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-404">To create this Class:</span></span>

1.  <span data-ttu-id="ce8ec-405">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="ce8ec-406">Mit der rechten Maustaste den **Projekt** Bereich \**erstellen* \*C\# Script\*\*.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="ce8ec-407">Nennen Sie das Skript **bestaunen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="ce8ec-408">Doppelklicken Sie auf dem neuen ***bestaunen*** Skript öffnen Sie ihn mit **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="ce8ec-409">Stellen Sie sicher, dass die folgende Namespace am Anfang des Skripts ist, und entfernen Sie alle anderen:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="ce8ec-410">Klicken Sie dann fügen Sie die folgenden Variablen in der **bestaunen** Klasse:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="ce8ec-411">Code für die **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="ce8ec-412">Fügen Sie den folgenden Code in die **Update()** Methode, um eine Raycast Projekt, und erkennen das Ziel erreicht:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="ce8ec-413">Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="ce8ec-414">Klicken Sie auf, und ziehen Sie die **bestaunen** Klasse aus dem Ordner Scripts, um die Main Camera-Objekts in der **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="ce8ec-415">Kapitel 7 – Setup die beiden Unity im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="ce8ec-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="ce8ec-416">Dieses Kapitel dient zum Einrichten von der beiden Szenen, die jeder ein Video in Stream hostet.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="ce8ec-417">Die Szene, die Sie bereits erstellt haben, wird dupliziert werden, sodass Sie nicht benötigen diesen erneut einrichten, aber Sie Sie dann die neue Szene bearbeiten, sodass die *GazeButton* Objekt in einen anderen Speicherort und verfügt über eine andere Darstellung.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="ce8ec-418">Dies ist veranschaulichen, wie Sie zwischen Szenen zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="ce8ec-419">Zu diesem Zweck sollen **Datei > Szene speichern als...** . Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="ce8ec-420">Klicken Sie auf die **neuer Ordner** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-420">Click the **New folder** button.</span></span>

    ![Kapitel 7 – Setup die beiden Unity im Hintergrund](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="ce8ec-422">Nennen Sie den Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="ce8ec-423">Die **Szene speichern** Fenster werden weiterhin öffnen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="ce8ec-424">Öffnen Sie den neu erstellten **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="ce8ec-425">In der **Dateiname:** Textfeld **VideoScene1**, drücken Sie dann die **speichern**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="ce8ec-426">Öffnen Sie in Unity, Ihre **Szenen** Ordner, und klicken Sie auf Ihre **VideoScene1** Datei.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="ce8ec-427">Verwenden die Tastatur, und drücken Sie die **STRG + D** werden Sie diese Szene duplizieren</span><span class="sxs-lookup"><span data-stu-id="ce8ec-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="ce8ec-428">Die **doppelte** Befehl kann auch ausgeführt werden, durch Navigieren zu **Bearbeiten > duplizieren**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="ce8ec-429">Unity wird automatisch erhöhen Sie die Anzahl der Szene-Namen, aber es jedenfalls überprüfen, um sicherzustellen, dass sie dem zuvor eingefügten Code entspricht.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="ce8ec-430">Sie müssen **VideoScene1** und **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="ce8ec-431">Mit den beiden Szenen, wechseln Sie zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="ce8ec-432">Mit der **Buildeinstellungen** Fenster geöffnet ist, ziehen Sie die Szenen, die **Szenen in Build** Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="ce8ec-434">Können Sie wählen Sie beide den Szenen aus Ihrer **Szenen** Ordner enthalten das **STRG** Schaltfläche, und klicken Sie dann mit der linken Maustaste jeder Szene, und zum Schluss ziehen Sie sowohl über.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="ce8ec-435">Schließen der **Buildeinstellungen** Fenster, und doppelklicken Sie auf **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="ce8ec-436">Öffnen Sie die zweite Szene, und klicken Sie auf die **GazeButton** untergeordnetes Objekt der **InsideOutSphere**, und legen Sie seine Transformation wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="ce8ec-437">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="ce8ec-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ce8ec-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-438">**X** 0</span></span>  |         <span data-ttu-id="ce8ec-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="ce8ec-439">**Y** 1.3</span></span>         | <span data-ttu-id="ce8ec-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="ce8ec-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="ce8ec-441">TRANSFORM - DREHUNG</span><span class="sxs-lookup"><span data-stu-id="ce8ec-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ce8ec-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-442">**X** 0</span></span>  |          <span data-ttu-id="ce8ec-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-443">**Y** 0</span></span>          |  <span data-ttu-id="ce8ec-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ce8ec-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="ce8ec-445">TRANSFORM - SKALIERUNG</span><span class="sxs-lookup"><span data-stu-id="ce8ec-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="ce8ec-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-446">**X** 1</span></span>   |          <span data-ttu-id="ce8ec-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-447">**Y** 1</span></span>          |  <span data-ttu-id="ce8ec-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="ce8ec-448">**Z** 1</span></span>  |

10. <span data-ttu-id="ce8ec-449">Mit der **GazeButton** ausgewählt, und suchen am untergeordneten der **Inspektor** und die **Mesh Filter**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="ce8ec-450">Klicken Sie auf das kleine Ziel neben der **Mesh** Referenzfeld:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="ce8ec-452">Ein **wählen Mesh** Popupfenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="ce8ec-453">Doppelklicken dem **Cube** aus der Liste der mesh **Assets**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="ce8ec-455">Die **Mesh Filter** aktualisiert, und jetzt eine **Cube**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="ce8ec-456">Klicken Sie nun die **Zahnradsymbol** Symbol neben dem **Kugel "collider"** , und klicken Sie auf **Komponente entfernen**, um die "collider" von diesem Objekt zu löschen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="ce8ec-458">Mit der **GazeButton** immer noch ausgewählt ist, klicken Sie auf die **Add Component** Schaltfläche am unteren Rand der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="ce8ec-459">Geben Sie in das Suchfeld ein, **Feld**, und **Box-Collider** wird eine Option: Klicken Sie auf, dass zum Hinzufügen einer **Box-Collider** auf Ihre **GazeButton** Objekt .</span><span class="sxs-lookup"><span data-stu-id="ce8ec-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="ce8ec-461">Die **GazeButton** ist jetzt teilweise aktualisiert wird, anders, suchen jedoch jetzt erstellen Sie ein neues **Material**, damit es völlig anders aussieht, und einfacher ist zu erkennen, wie ein anderes Objekt, als die Objekt in die erste Szene.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="ce8ec-462">Navigieren Sie zu Ihrem **Materialien** Ordner, der innerhalb der **Projektfenster**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="ce8ec-463">Duplizieren der **ButtonMaterial** Material (drücken Sie die **STRG** + **D** auf der Tastatur, oder klicken Sie auf die **Material**, klicken Sie dann von der **bearbeiten** Datei Menüoption wählen **doppelte**).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="ce8ec-464">![Kapitel 7: Einrichten von zwei Unity im Hintergrund](images/AzureLabs-Lab6-55.png)
    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="ce8ec-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="ce8ec-465">Wählen Sie die neue **ButtonMaterial** Material (hier mit dem Namen **ButtonMaterial 1**), und innerhalb der **Inspektor**, klicken Sie auf die **Albedo** Farbe Fenster.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="ce8ec-466">Ein Popupfenster angezeigt wird, können Sie eine andere Farbe auswählen (Wählen Sie je nachdem, was Ihnen gefällt), klicken Sie dann das Popup zu schließen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="ce8ec-467">Das Material werden ihre eigene Instanz, und mit dem Original unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-467">The Material will be its own instance, and different to the original.</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="ce8ec-469">Ziehen Sie die neue **Material** auf die **GazeButton** untergeordnete, jetzt vollständig die aussehen, aktualisieren, damit sie problemlos von der ersten im Hintergrund-Schaltfläche zu unterscheiden ist.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="ce8ec-471">An diesem Punkt können Sie das Projekt im Editor testen, bevor Sie das UWP-Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="ce8ec-472">Drücken Sie die **spielen** Schaltfläche der **Editor** und Ihre Kopfhörer wear.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="ce8ec-474">Sehen Sie sich die beiden **GazeButton** Objekte zwischen der ersten und zweiten Video wechseln.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="ce8ec-475">Kapitel 8 – erstellen Sie die UWP-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="ce8ec-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="ce8ec-476">Nachdem Sie sichergestellt haben, dass der Editor keine Fehler aufweist, sind Sie bereit für Build.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="ce8ec-477">So erstellen Sie:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-477">To Build:</span></span>

1.  <span data-ttu-id="ce8ec-478">Speichern Sie durch Klicken auf die aktuelle Szene **Datei > Speichern**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="ce8ec-479">Aktivieren Sie das Kontrollkästchen namens **Unity C\# Projekte** (Dies ist wichtig, da er kann Sie die Klassen zu bearbeiten, nachdem der Build abgeschlossen ist).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="ce8ec-480">Wechseln Sie zu **Datei > Buildeinstellungen**, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="ce8ec-481">Sie werden aufgefordert werden, um den Ordner auszuwählen, in dem Sie Buildthe Lösung möchten.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="ce8ec-482">Erstellen Sie eine **erstellt** Ordner, und erstellen Sie einen anderen Ordner in diesem Ordner mit einem entsprechenden Namen Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="ce8ec-483">Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, also auf diesen Ordner ein, um den Build an diesem Speicherort zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="ce8ec-484">![Kapitel 8 – Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab6-60.png)
    ![Kapitel 8 – erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="ce8ec-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="ce8ec-485">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="ce8ec-486">Kapitel 9 – bereitstellen, auf dem lokalen Computer</span><span class="sxs-lookup"><span data-stu-id="ce8ec-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="ce8ec-487">Nachdem der Build abgeschlossen wurde, eine **Datei-Explorer** Fenster wird angezeigt, an der Position des Builds.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="ce8ec-488">Öffnen Sie den Ordner, die Sie mit dem Namen und integriert, und klicken Sie dann einen Doppelklick auf die Projektmappendatei (.sln) in diesem Ordner, um die Projektmappe mit Visual Studio 2017 geöffnet haben.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="ce8ec-489">Müssen Sie nur noch tun wird Ihre app auf Ihrem Computer bereitstellen (oder *lokalen Computer*).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="ce8ec-490">So stellen Sie auf dem lokalen Computer bereit:</span><span class="sxs-lookup"><span data-stu-id="ce8ec-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="ce8ec-491">In **Visual Studio 2017**, öffnen Sie die Projektmappendatei, die gerade erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="ce8ec-492">In der **Projektmappenplattform**Option **X86, lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ce8ec-493">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Kapitel 9 – Bereitstellen Sie, auf dem lokalen Computer](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="ce8ec-495">Sie müssen jetzt alle Pakete der Projektmappe wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="ce8ec-496">Mit der rechten Maustaste auf Ihre **Lösung**, und klicken Sie auf **Wiederherstellen von NuGet-Pakete für Projektmappe...**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ce8ec-497">Dies geschieht, da die Pakete, die den erstellt Unity bereitgestellt werden soll, um die Arbeit mit Ihrem lokalen Computer verweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="ce8ec-498">Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="ce8ec-499">Visual Studio zum ersten Mal erstellen und anschließend bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="ce8ec-500">Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Kapitel 9 – Bereitstellen Sie, auf dem lokalen Computer](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="ce8ec-502">Wenn Sie die Mixed Reality-Anwendung ausführen, Sie sehen werden innerhalb der **InsideOutSphere** Modell, die Sie in Ihrer app verwendet.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="ce8ec-503">Diese Kugel werden, in dem das Video gestreamt wird, bietet eine 360 °-Sicht auf, der den eingehenden Videostream (die für diese Art von Perspektive gedreht wurde).</span><span class="sxs-lookup"><span data-stu-id="ce8ec-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="ce8ec-504">Führen Sie nicht überrascht sein, wenn das Video ein paar Sekunden zum Laden akzeptiert, unterliegen der verfügbaren internetgeschwindigkeit, Ihre app ist wie das Video muss abgerufen werden, und klicken Sie dann heruntergeladen, also zum Streamen in Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="ce8ec-505">Wenn Sie bereit sind, ändern Sie im Hintergrund zu, und öffnen Sie Ihre zweite Video, indem Sie auf die rote Kugel gazing!</span><span class="sxs-lookup"><span data-stu-id="ce8ec-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="ce8ec-506">Klicken Sie dann gerne zurück, mit dem blauen Cube in der zweiten Szene!</span><span class="sxs-lookup"><span data-stu-id="ce8ec-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="ce8ec-507">Der fertigen Anwendung für Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="ce8ec-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="ce8ec-508">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die die Azure Media Services zum Streamen von Videos mit 360 nutzt.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab6-00.png)

![Lab-Ergebnis](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ce8ec-511">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="ce8ec-511">Bonus Exercises</span></span>

<span data-ttu-id="ce8ec-512">**Übung 1**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-512">**Exercise 1**</span></span>

<span data-ttu-id="ce8ec-513">Es ist durchaus möglich, mit nur einer einzigen Szene auf Videos in diesem Lernprogramm ändern.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="ce8ec-514">Experimentieren Sie mit Ihrer Anwendung, und legen Sie ihn in einer einzigen Szene auf.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="ce8ec-515">Vielleicht sogar ein anderes Video zur Mischung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="ce8ec-516">**Übung 2**</span><span class="sxs-lookup"><span data-stu-id="ce8ec-516">**Exercise 2**</span></span>

<span data-ttu-id="ce8ec-517">Experimentieren Sie mit Azure und Unity, und versuchen Sie, implementieren Sie die Möglichkeit, dass die app automatisch ein Video mit einer anderen Dateigröße, je nach die Stärke des eine Internetverbindung auswählen.</span><span class="sxs-lookup"><span data-stu-id="ce8ec-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


