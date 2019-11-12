---
title: Mr-und Azure 306-Streaming-Video
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Media Services in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Media Services, Streaming-Video, 360, immersive, VR
ms.openlocfilehash: e0350d69eed9b922e174bc521107beac7d11b1bc
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926829"
---
>[!NOTE]
><span data-ttu-id="c841c-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="c841c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c841c-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="c841c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c841c-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c841c-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="c841c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c841c-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="c841c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c841c-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="c841c-110">Mr und Azure 306: Streaming-Video</span><span class="sxs-lookup"><span data-stu-id="c841c-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="c841c-111">![endgültige Product-Start](images/AzureLabs-Lab6-00.png)
![endgültige Produktstart](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="c841c-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="c841c-112">In diesem Kurs erfahren Sie, wie Sie Ihre Azure Media Services mit einer Windows Mixed Reality-VR-Benutzer Verbindung verbinden, um das Streaming von 360-Grad-Videowiedergabe auf immersiven Headsets zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="c841c-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="c841c-113">Bei **Azure Media Services** handelt es sich um eine Sammlung von Diensten, die Ihnen Broadcast-Quality-Videostreamingdienste zur Erreichung größerer Zielgruppen auf den heute beliebtesten mobilen Geräten bietet.</span><span class="sxs-lookup"><span data-stu-id="c841c-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="c841c-114">Weitere Informationen finden Sie auf der [Seite Azure Media Services](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="c841c-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="c841c-115">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, mit der Sie die folgenden Aktionen ausführen können:</span><span class="sxs-lookup"><span data-stu-id="c841c-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="c841c-116">Abrufen eines 360-Grad-Videos aus einer **Azure Storage**über den **Azure Media Service**.</span><span class="sxs-lookup"><span data-stu-id="c841c-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="c841c-117">Anzeigen des abgerufenen 360-Grad-Videos in einer Unity-Szene.</span><span class="sxs-lookup"><span data-stu-id="c841c-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="c841c-118">Navigieren Sie zwischen zwei Kulissen mit zwei verschiedenen Videos.</span><span class="sxs-lookup"><span data-stu-id="c841c-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="c841c-119">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c841c-120">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c841c-121">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="c841c-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c841c-122">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="c841c-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c841c-123">Natürlich</span><span class="sxs-lookup"><span data-stu-id="c841c-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c841c-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c841c-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c841c-125"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="c841c-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c841c-126">Mr und Azure 306: Streaming-Video</span><span class="sxs-lookup"><span data-stu-id="c841c-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="c841c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c841c-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="c841c-128">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c841c-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c841c-129">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="c841c-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c841c-130">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="c841c-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c841c-131">Sie können die neueste Software verwenden, die im [Artikel Installieren der Tools](install-the-tools.md)aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="c841c-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c841c-132">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="c841c-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c841c-133">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="c841c-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c841c-134">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="c841c-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c841c-135">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c841c-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c841c-136">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="c841c-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c841c-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c841c-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c841c-138">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="c841c-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="c841c-139">Internet Zugriff für Azure-Setup und Datenabruf</span><span class="sxs-lookup"><span data-stu-id="c841c-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="c841c-140">2 360-Grad-Videos im MP4-Format ( [auf dieser Downloadseite](https://www.mettle.com/360vr-master-series-free-360-downloads-page)finden Sie einige gebührenfreie Videos)</span><span class="sxs-lookup"><span data-stu-id="c841c-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c841c-141">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="c841c-141">Before you start</span></span>

1.  <span data-ttu-id="c841c-142">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="c841c-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c841c-143">Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="c841c-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c841c-144">Für diesen Kurs benötigen Sie **keine** Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="c841c-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="c841c-145">Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, klicken Sie [auf verknüpfen, um Windows Mixed Reality einzurichten](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="c841c-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="c841c-146">Kapitel 1: Azure-Portal: Erstellen des Azure Storage Kontos</span><span class="sxs-lookup"><span data-stu-id="c841c-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="c841c-147">Um den **Azure Storage-Dienst**zu verwenden, müssen Sie ein **Speicherkonto** in der Azure-Portal erstellen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="c841c-148">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="c841c-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c841c-149">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="c841c-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c841c-150">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c841c-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c841c-151">Wenn Sie angemeldet sind, klicken Sie im linken Menü auf **Speicher Konten** .</span><span class="sxs-lookup"><span data-stu-id="c841c-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="c841c-153">Klicken Sie auf der Registerkarte **Speicher Konten** auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="c841c-155">Auf der Registerkarte **Speicherkonto erstellen** :</span><span class="sxs-lookup"><span data-stu-id="c841c-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="c841c-156">Fügen Sie einen **Namen** für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="c841c-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="c841c-157">Wählen Sie **unter Bereitstellungs Modell** die Option **Resource Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="c841c-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="c841c-158">Wählen Sie unter **Kontoart**die Option **Speicher (universell, Version v1)** aus.</span><span class="sxs-lookup"><span data-stu-id="c841c-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="c841c-159">Wählen Sie für **Leistung**die Option **Standard \* aus.**</span><span class="sxs-lookup"><span data-stu-id="c841c-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="c841c-160">Wählen Sie für **Replikation** die Option **lokal redundanter Speicher (LRS)** aus.</span><span class="sxs-lookup"><span data-stu-id="c841c-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="c841c-161">Lassen Sie die Option " **sichere Übertragung erforderlich** " **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="c841c-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="c841c-162">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="c841c-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="c841c-163">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="c841c-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="c841c-164">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="c841c-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="c841c-165">Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="c841c-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c841c-166">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c841c-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c841c-167">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c841c-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="c841c-168">Sie müssen bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="c841c-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="c841c-170">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="c841c-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="c841c-171">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="c841c-173">An diesem Punkt müssen Sie die Ressource nicht befolgen, sondern einfach zum nächsten Kapitel wechseln.</span><span class="sxs-lookup"><span data-stu-id="c841c-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="c841c-174">Kapitel 2: Azure-Portal: Erstellen des Medien Dienstanbieter</span><span class="sxs-lookup"><span data-stu-id="c841c-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="c841c-175">Zum Verwenden von Azure Media Service müssen Sie eine Instanz des Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird (wobei der Kontoinhaber ein Administrator sein muss).</span><span class="sxs-lookup"><span data-stu-id="c841c-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="c841c-176">Klicken Sie im Azure-Portal in der oberen linken Ecke auf **Ressource erstellen** , und suchen Sie nach **Media Service,** und drücken **Sie die Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="c841c-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="c841c-177">Die gewünschte Ressource hat zurzeit ein rosa Symbol. Klicken Sie hierauf, um eine neue Seite anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c841c-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="c841c-179">Auf der neuen Seite wird eine Beschreibung des **Medien Dienstanbieter**bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="c841c-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="c841c-180">Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c841c-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="c841c-182">Nachdem Sie auf **Erstellen** geklickt haben, wird ein Panel angezeigt, in dem Sie einige Details über den neuen Mediendienst angeben müssen:</span><span class="sxs-lookup"><span data-stu-id="c841c-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="c841c-183">Fügen Sie den gewünschten **Kontonamen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="c841c-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="c841c-184">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="c841c-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="c841c-185">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="c841c-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c841c-186">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="c841c-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c841c-187">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c841c-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="c841c-188">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten von Azure-Ressourcengruppen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c841c-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="c841c-189">Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="c841c-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c841c-190">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c841c-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c841c-191">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c841c-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="c841c-192">Klicken Sie im Abschnitt **Speicherkonto** auf den Abschnitt **auswählen...** , und klicken Sie dann auf das **Speicherkonto** , das Sie im letzten Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c841c-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="c841c-193">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="c841c-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="c841c-194">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-194">Click **Create**.</span></span>

        ![Das Azure-Portal](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="c841c-196">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="c841c-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="c841c-197">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="c841c-199">Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c841c-199">Click on the notification to explore your new Service instance.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="c841c-201">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c841c-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="c841c-202">Klicken Sie auf der Seite neuer Mediendienst im linken Bereich auf den Link **Assets** , der ungefähr in der Mitte liegt.</span><span class="sxs-lookup"><span data-stu-id="c841c-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="c841c-203">Klicken Sie auf der nächsten Seite in der oberen linken Ecke der Seite auf **hochladen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="c841c-205">Klicken Sie auf das **Ordner** Symbol, um die Dateien zu durchsuchen, und wählen Sie das erste 360-Video aus, das Sie streamen möchten.</span><span class="sxs-lookup"><span data-stu-id="c841c-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="c841c-206">Sie können diesem [Link folgen, um ein Beispiel Video herunterzuladen](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="c841c-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="c841c-208">Lange Dateinamen können ein Problem mit dem Encoder verursachen: um sicherzustellen, dass Videos keine Probleme haben, sollten Sie die Länge der Video Dateinamen verkürzen.</span><span class="sxs-lookup"><span data-stu-id="c841c-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="c841c-209">Wenn der Upload des Videos abgeschlossen ist, wird die Statusleiste grün.</span><span class="sxs-lookup"><span data-stu-id="c841c-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="c841c-211">Klicken Sie auf den obigen Text (**yourservicename-Assets**), um zur Seite **Assets** zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="c841c-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="c841c-212">Sie werden feststellen, dass Ihr Video erfolgreich hochgeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="c841c-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="c841c-213">Klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="c841c-213">Click on it.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="c841c-215">Auf der Seite, zu der Sie umgeleitet werden, werden ausführliche Informationen zu Ihrem Video angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="c841c-216">Um Ihr Video verwenden zu können, müssen Sie es codieren, indem Sie auf die Schaltfläche **Codieren** oben links auf der Seite klicken.</span><span class="sxs-lookup"><span data-stu-id="c841c-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="c841c-218">Auf der rechten Seite wird ein neuer Bereich angezeigt, in dem Sie Codierungsoptionen für die Datei festlegen können.</span><span class="sxs-lookup"><span data-stu-id="c841c-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="c841c-219">Legen Sie die folgenden Eigenschaften fest (einige werden bereits standardmäßig festgelegt):</span><span class="sxs-lookup"><span data-stu-id="c841c-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="c841c-220">**Media Encoder-Name *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="c841c-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="c841c-221">**Codierungs voreingestellten *Inhalt Adaptive Multi-Bitrate-MP4***</span><span class="sxs-lookup"><span data-stu-id="c841c-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="c841c-222">**Auftrags Name *Media Encoder Standard Verarbeitung von video1. MP4***</span><span class="sxs-lookup"><span data-stu-id="c841c-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="c841c-223">**Ausgabemedien Medienobjekt Name *video1. MP4--Media Encoder Standard codiert***</span><span class="sxs-lookup"><span data-stu-id="c841c-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Das Azure-Portal](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="c841c-225">Klicken Sie auf die Schaltfläche **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="c841c-226">Sie werden feststellen, dass ein Balken mit dem **hinzugefügten Codierungs Auftrag hinzugefügt**wurde. Klicken Sie auf diese Leiste, und ein Panel mit dem darin angezeigten Codierungs Fortschritt</span><span class="sxs-lookup"><span data-stu-id="c841c-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-17.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="c841c-229">Warten Sie, bis der Auftrag abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c841c-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="c841c-230">Nachdem der Vorgang abgeschlossen ist, können Sie den Bereich mit dem "X" oben rechts in diesem Panel schließen.</span><span class="sxs-lookup"><span data-stu-id="c841c-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-19.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="c841c-233">Die Zeit, die dies dauert, hängt von der Dateigröße Ihres Videos ab.</span><span class="sxs-lookup"><span data-stu-id="c841c-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="c841c-234">Dieser Vorgang kann einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="c841c-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="c841c-235">Nachdem Sie nun die codierte Version des Videos erstellt haben, können Sie Sie veröffentlichen, um Sie zugänglich zu machen.</span><span class="sxs-lookup"><span data-stu-id="c841c-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="c841c-236">Klicken Sie hierzu auf die blauen **linkassets** , um zur Seite Assets zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="c841c-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="c841c-238">Ihr Video wird zusammen mit einem anderen angezeigt, d. h. vom **Ressourcentyp mit _Multi-Bitrate-MP4_** .</span><span class="sxs-lookup"><span data-stu-id="c841c-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="c841c-240">Sie werden feststellen, dass das neue Medienobjekt neben dem ersten Video *unbekannt*ist und für seine **Größe**0 Bytes aufweist. aktualisieren Sie einfach das Fenster, um es zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="c841c-241">Klicken Sie auf dieses neue Asset.</span><span class="sxs-lookup"><span data-stu-id="c841c-241">Click this new asset.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="c841c-243">Es wird ein ähnlicher Bereich angezeigt, den Sie zuvor verwendet haben, nur dies ist ein anderes Asset.</span><span class="sxs-lookup"><span data-stu-id="c841c-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="c841c-244">Klicken Sie in der oberen Mitte der Seite auf die Schaltfläche **veröffentlichen** .</span><span class="sxs-lookup"><span data-stu-id="c841c-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="c841c-246">Sie werden aufgefordert, einen **Locator**(den Einstiegspunkt) auf Datei/s in ihren Assets festzulegen.</span><span class="sxs-lookup"><span data-stu-id="c841c-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="c841c-247">Legen Sie für Ihr Szenario die folgenden Eigenschaften fest:</span><span class="sxs-lookup"><span data-stu-id="c841c-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="c841c-248">Der **Locatortyp** > **progressiv**.</span><span class="sxs-lookup"><span data-stu-id="c841c-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="c841c-249">Das **Datum** und die **Uhrzeit** werden von Ihrem aktuellen Datum auf eine Uhrzeit in der Zukunft (in diesem Fall 100 Jahre) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c841c-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="c841c-250">Lassen Sie den Wert unverändert, oder ändern Sie ihn entsprechend.</span><span class="sxs-lookup"><span data-stu-id="c841c-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c841c-251">Weitere Informationen zu Locators und den Optionen, die Sie auswählen können, finden Sie in der [Azure Media Services-Dokumentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="c841c-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="c841c-252">Klicken Sie unten in diesem Bereich auf die Schaltfläche **Hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="c841c-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="c841c-254">Ihr Video ist nun veröffentlicht und kann über seinen Endpunkt gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="c841c-255">Im weiteren Verlauf der Seite befindet sich ein Abschnitt " **Dateien** ".</span><span class="sxs-lookup"><span data-stu-id="c841c-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="c841c-256">An dieser Stelle werden die unterschiedlichen codierten Versionen Ihres Videos verwendet.</span><span class="sxs-lookup"><span data-stu-id="c841c-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="c841c-257">Wählen Sie die höchstmögliche Auflösung aus (in der folgenden Abbildung ist die Datei 1920 x960), und dann wird ein Bereich rechts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="c841c-258">Dort finden Sie eine **Download-URL**.</span><span class="sxs-lookup"><span data-stu-id="c841c-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="c841c-259">Kopieren Sie diesen **Endpunkt** , da Sie ihn später in Ihrem Code verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-26.png)    

    ![Das Azure-Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="c841c-262">Sie können auch auf die **Wiedergabe** Schaltfläche klicken, um Ihr Video wiederzugeben und zu testen.</span><span class="sxs-lookup"><span data-stu-id="c841c-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="c841c-263">Sie müssen nun das zweite Video hochladen, das Sie in diesem Lab verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="c841c-264">Führen Sie die oben beschriebenen Schritte aus, und wiederholen Sie den Vorgang für das zweite Video.</span><span class="sxs-lookup"><span data-stu-id="c841c-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="c841c-265">Stellen Sie sicher, dass Sie auch den zweiten **Endpunkt** kopieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="c841c-266">Verwenden Sie den folgenden [Link, um ein zweites Video herunterzuladen](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="c841c-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="c841c-267">Nachdem beide Videos veröffentlicht wurden, können Sie mit dem nächsten Kapitel fortfahren.</span><span class="sxs-lookup"><span data-stu-id="c841c-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="c841c-268">Kapitel 3: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="c841c-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="c841c-269">Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="c841c-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c841c-270">Öffnen Sie **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="c841c-270">Open **Unity** and click **New**.</span></span> 

    ![Das Azure-Portal](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="c841c-272">Sie müssen nun einen Unity-Projektnamen angeben und **Mr\_360videostreaming einfügen.**</span><span class="sxs-lookup"><span data-stu-id="c841c-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="c841c-273">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c841c-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c841c-274">Legen Sie den Speicherort auf einen geeigneten Speicherort fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="c841c-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c841c-275">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-275">Then, click **Create project**.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="c841c-277">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c841c-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="c841c-278">Wechseln Sie zu  ***Einstellungen* bearbeiten** , und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="c841c-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c841c-279">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c841c-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c841c-280">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="c841c-280">Close the **Preferences** window.</span></span>

    ![Das Azure-Portal](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="c841c-282">Navigieren Sie als nächstes zu ***dateibuildeinstellungen*** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="c841c-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="c841c-283">Stellen Sie außerdem Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="c841c-283">Also make sure that:</span></span>

    1. <span data-ttu-id="c841c-284">Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c841c-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="c841c-285">Der **Buildtyp** ist auf D3D festgelegt **.**</span><span class="sxs-lookup"><span data-stu-id="c841c-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="c841c-286">**SDK** ist auf **zuletzt installiert** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c841c-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="c841c-287">Die **Visual Studio-Version** ist auf die **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c841c-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="c841c-288">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c841c-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="c841c-289">Machen Sie sich keine Gedanken über das Einrichten von **Szenen** , da Sie diese später festlegen werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="c841c-290">Die restlichen Einstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-290">The remaining settings should be left as default for now.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="c841c-292">Klicken Sie im Fenster **Buildeinstellungen** auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="c841c-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="c841c-293">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="c841c-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c841c-294">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="c841c-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c841c-295">Die **Lauf Zeit Version** der **Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="c841c-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="c841c-296">Das Skript für die **Skript** Erstellung sollte **.net sein.**</span><span class="sxs-lookup"><span data-stu-id="c841c-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="c841c-297">Der **API-Kompatibilitäts Grad** sollte **.NET 4,6 lauten.**</span><span class="sxs-lookup"><span data-stu-id="c841c-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="c841c-299">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="c841c-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="c841c-301">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c841c-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="c841c-302">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="c841c-302">**InternetClient**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="c841c-304">Nachdem Sie diese Änderungen vorgenommen haben, schließen Sie das Fenster mit den **Buildeinstellungen** .</span><span class="sxs-lookup"><span data-stu-id="c841c-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="c841c-305">Speichern Sie Ihr Projekt \**File* \* Save Project \* \*.</span><span class="sxs-lookup"><span data-stu-id="c841c-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="c841c-306">Kapitel 4: Importieren des insideoutsphere Unity-Pakets</span><span class="sxs-lookup"><span data-stu-id="c841c-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c841c-307">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus **Kapitel 5**fortfahren.</span><span class="sxs-lookup"><span data-stu-id="c841c-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="c841c-308">Sie müssen dennoch ein Unity-Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="c841c-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="c841c-309">Für diesen Kurs müssen Sie ein Unity-Ressourcenpaket mit dem Namen [**insideoutsphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="c841c-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="c841c-310">Gewusst wie: Importieren von **vstu**:</span><span class="sxs-lookup"><span data-stu-id="c841c-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="c841c-311">Klicken Sie oben auf dem Bildschirm mit dem Unity-Dashboard auf **Assets** , und klicken Sie dann auf **Paket > benutzerdefiniertes Paket importieren**.</span><span class="sxs-lookup"><span data-stu-id="c841c-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="c841c-313">Wählen Sie mit der Dateiauswahl das Paket **insideoutsphere. unitypackage** aus, und klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="c841c-314">Eine Liste der Komponenten für dieses Asset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="c841c-315">Bestätigen Sie den Import, indem Sie auf **importieren**klicken.</span><span class="sxs-lookup"><span data-stu-id="c841c-315">Confirm the import by clicking **Import**.</span></span>

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="c841c-317">Nachdem der Import abgeschlossen wurde, bemerken Sie, dass drei neue Ordner, **Materialien**, **Modelle**und **Prefabs**dem Ordner " **Assets** " hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="c841c-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="c841c-318">Diese Art von Ordnerstruktur ist typisch für ein Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="c841c-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="c841c-320">Öffnen Sie den Ordner **Modelle** , und Sie sehen, dass das **insienoutsphere** -Modell importiert wurde.</span><span class="sxs-lookup"><span data-stu-id="c841c-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="c841c-321">Im Ordner **Material** finden Sie das Material **insiweoutsphären** *LAMBERT1*zusammen mit einem Material namens *Button Material*, das von der Schaltfläche "Pavillon" verwendet wird, die Sie in Kürze sehen werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="c841c-322">Der Ordner " **Prefabs** " enthält das **insienoutsphere** -präfab, das sowohl das **insienoutsphere** - *Modell* als auch das " *gazebutton*" enthält.</span><span class="sxs-lookup"><span data-stu-id="c841c-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="c841c-323">Es **ist kein Code enthalten**. Sie schreiben den Code, indem Sie diesen Kurs befolgen.</span><span class="sxs-lookup"><span data-stu-id="c841c-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="c841c-324">Wählen Sie in der **Hierarchie**das **Hauptkamera** Objekt aus, und aktualisieren Sie die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="c841c-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="c841c-325">**Sin**</span><span class="sxs-lookup"><span data-stu-id="c841c-325">**Transform**</span></span>

        1.  <span data-ttu-id="c841c-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="c841c-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="c841c-327">Drehung = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="c841c-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="c841c-328">Skalieren Sie **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="c841c-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="c841c-329">**Kamera**</span><span class="sxs-lookup"><span data-stu-id="c841c-329">**Camera**</span></span>

        1. <span data-ttu-id="c841c-330">**Clear Flags**: Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="c841c-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="c841c-331">**Clipping-Ebenen**: fast: 0,1, weit: 6.</span><span class="sxs-lookup"><span data-stu-id="c841c-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="c841c-333">Navigieren Sie zum Ordner " **Prefab** ", und ziehen Sie dann den " **insidebug outsphere** "-Prefab in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="c841c-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="c841c-335">Erweitern Sie das **insideoutsphere** -Objekt in der **Hierarchie** , indem Sie auf den kleinen Pfeil daneben klicken.</span><span class="sxs-lookup"><span data-stu-id="c841c-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="c841c-336">Darunter **wird ein unter** geordnetes Objekt mit dem Namen " **gazebutton**" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="c841c-337">Diese wird verwendet, um Szenen und somit Videos zu ändern.</span><span class="sxs-lookup"><span data-stu-id="c841c-337">This will be used to change scenes and thus videos.</span></span>

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="c841c-339">Klicken Sie im Inspektor-Fenster auf die Transformations Komponente von **insideoutsphere**, und stellen Sie sicher, dass die folgenden Eigenschaften festgelegt sind:</span><span class="sxs-lookup"><span data-stu-id="c841c-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="c841c-340">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="c841c-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="c841c-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-341">**X** 0</span></span>  |          <span data-ttu-id="c841c-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-342">**Y** 0</span></span>          |  <span data-ttu-id="c841c-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="c841c-344">Transformation-Drehung</span><span class="sxs-lookup"><span data-stu-id="c841c-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="c841c-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-345">**X** 0</span></span>  |          <span data-ttu-id="c841c-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="c841c-346">**Y** -50</span></span>        |  <span data-ttu-id="c841c-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="c841c-348">Transformieren: Skalieren</span><span class="sxs-lookup"><span data-stu-id="c841c-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="c841c-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-349">**X** 1</span></span>   |          <span data-ttu-id="c841c-350">**J** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-350">**Y** 1</span></span>          |  <span data-ttu-id="c841c-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-351">**Z** 1</span></span>  |

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="c841c-353">Klicken Sie auf das untergeordnete **gazebutton** -Objekt, und legen Sie die zugehörige **Transformation** wie folgt fest:</span><span class="sxs-lookup"><span data-stu-id="c841c-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="c841c-354">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="c841c-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="c841c-355">**X** 3,6</span><span class="sxs-lookup"><span data-stu-id="c841c-355">**X** 3.6</span></span>|          <span data-ttu-id="c841c-356">**J** 1,3</span><span class="sxs-lookup"><span data-stu-id="c841c-356">**Y** 1.3</span></span>        |  <span data-ttu-id="c841c-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="c841c-358">Transformation-Drehung</span><span class="sxs-lookup"><span data-stu-id="c841c-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="c841c-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-359">**X** 0</span></span>  |          <span data-ttu-id="c841c-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-360">**Y** 0</span></span>          |  <span data-ttu-id="c841c-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="c841c-362">Transformieren: Skalieren</span><span class="sxs-lookup"><span data-stu-id="c841c-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="c841c-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-363">**X** 1</span></span>   |          <span data-ttu-id="c841c-364">**J** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-364">**Y** 1</span></span>          |  <span data-ttu-id="c841c-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-365">**Z** 1</span></span>  |

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="c841c-367">Kapitel 5: Erstellen der Videocontroller-Klasse</span><span class="sxs-lookup"><span data-stu-id="c841c-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="c841c-368">Die **Videocontroller** -Klasse hostet die beiden Video Endpunkte, die zum Streamen der Inhalte aus dem Azure Media Service verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="c841c-369">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c841c-369">To create this class:</span></span>

1.  <span data-ttu-id="c841c-370">Klicken Sie mit der rechten Maustaste in den **Ordner Asset**, der sich im **Projekt** Panel befindet, und klicken Sie auf **> Ordner erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="c841c-371">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="c841c-371">Name the folder **Scripts**.</span></span>

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-43.png)

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="c841c-374">Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c841c-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="c841c-375">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **> C\# Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="c841c-376">Benennen Sie das Skript **Videocontroller**.</span><span class="sxs-lookup"><span data-stu-id="c841c-376">Name the script **VideoController**.</span></span>

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="c841c-378">Doppelklicken Sie auf das neue **Videocontroller** -Skript, um es mit **Visual Studio 2017** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c841c-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="c841c-380">Aktualisieren Sie die Namespaces oben in der Codedatei wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c841c-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="c841c-381">Geben Sie die folgenden Variablen in der **Videocontroller** -Klasse zusammen mit der **Awa()** -Methode ein:</span><span class="sxs-lookup"><span data-stu-id="c841c-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="c841c-382">Nun ist die Zeit, die Endpunkte aus ihren Azure Media Service-Videos einzugeben:</span><span class="sxs-lookup"><span data-stu-id="c841c-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="c841c-383">Der erste in die *video1endpoint* -Variable.</span><span class="sxs-lookup"><span data-stu-id="c841c-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="c841c-384">Der zweite in die *video2endpoint* -Variable.</span><span class="sxs-lookup"><span data-stu-id="c841c-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c841c-385">Es gibt ein bekanntes Problem bei der Verwendung von *https* in Unity mit der Version 2017.4.1 F1.</span><span class="sxs-lookup"><span data-stu-id="c841c-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="c841c-386">Wenn die Videos einen Fehler bei der Wiedergabe bereitstellen, versuchen Sie stattdessen, stattdessen "http" zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c841c-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="c841c-387">Als nächstes muss die Methode **Start ()** bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="c841c-388">Diese Methode wird jedes Mal ausgelöst, wenn der Benutzer die Szene wechselt (folglich wird das Video gewechselt), indem er sich die Schaltfläche "Blick" ansieht.</span><span class="sxs-lookup"><span data-stu-id="c841c-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="c841c-389">Fügen Sie nach der Methode **Start ()** die *IEnumerator* -Methode **playVideo ()** ein, die verwendet wird, um Videos nahtlos zu starten (sodass kein ruckeln sichtbar ist).</span><span class="sxs-lookup"><span data-stu-id="c841c-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="c841c-390">Die letzte Methode, die Sie für diese Klasse benötigen, ist die **changescene ()** -Methode, die verwendet wird, um zwischen Szenen auszutauschen.</span><span class="sxs-lookup"><span data-stu-id="c841c-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="c841c-391">Die **changescene ()** -Methode verwendet ein praktisches C-\# Feature, das als *Bedingter Operator*bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="c841c-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="c841c-392">Dies ermöglicht, dass Bedingungen überprüft werden und dann basierend auf dem Ergebnis der Überprüfung zurückgegebene Werte in einer einzigen Anweisung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="c841c-393">[Weitere Informationen zum bedingten Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)finden Sie unter diesem Link.</span><span class="sxs-lookup"><span data-stu-id="c841c-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="c841c-394">Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c841c-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="c841c-395">Klicken Sie im Unity-Editor auf die **Videocontroller** -Klasse [from] {. Unterstreichung} der Ordner **Scripts** , und ziehen Sie Sie im **Hierarchie** Panel auf das **Hauptkamera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="c841c-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="c841c-396">Klicken Sie auf die **Hauptkamera** , und sehen Sie sich den Bereich **Inspector**an.</span><span class="sxs-lookup"><span data-stu-id="c841c-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="c841c-397">Sie werden feststellen, dass in der neu hinzugefügten Skript Komponente ein Feld mit einem leeren Wert vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c841c-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="c841c-398">Dies ist ein Verweis Feld, das die öffentlichen Variablen in Ihrem Code als Ziel hat.</span><span class="sxs-lookup"><span data-stu-id="c841c-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="c841c-399">Ziehen Sie das **insidebug** -Objekt aus dem Bereich **Hierarchie** in den **Sphere** -Slot, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c841c-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="c841c-400">![erstellen Sie die Videocontroller-Klasse](images/AzureLabs-Lab6-47.png)
    ![die Videocontroller-Klasse erstellen](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="c841c-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="c841c-401">Kapitel 6: Erstellen der "Blick"-Klasse</span><span class="sxs-lookup"><span data-stu-id="c841c-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="c841c-402">Diese Klasse ist für das Erstellen eines **raycast** verantwortlich, der von der **Hauptkamera**projiziert wird, um zu erkennen, welches Objekt der Benutzer untersucht.</span><span class="sxs-lookup"><span data-stu-id="c841c-402">This class is responsible for creating a **Raycast** that will be projected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="c841c-403">In diesem Fall muss der **raycast** ermitteln, ob der Benutzer das **gazebutton** -Objekt in der Szene prüft und ein Verhalten auslöst.</span><span class="sxs-lookup"><span data-stu-id="c841c-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="c841c-404">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c841c-404">To create this Class:</span></span>

1.  <span data-ttu-id="c841c-405">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c841c-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="c841c-406">Klicken Sie mit der rechten Maustaste in das **Projekt** Panel, und klicken Sie auf \* C\# Skript \* \**Erstellen* .</span><span class="sxs-lookup"><span data-stu-id="c841c-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="c841c-407">Benennen Sie das **Skript mit**dem Namen.</span><span class="sxs-lookup"><span data-stu-id="c841c-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="c841c-408">Doppelklicken Sie auf das neue ***Blick*** Skript, um es mit **Visual Studio 2017** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c841c-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="c841c-409">Stellen Sie sicher, dass sich der folgende Namespace oben im Skript befindet, und entfernen Sie alle anderen:</span><span class="sxs-lookup"><span data-stu-id="c841c-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="c841c-410">Fügen Sie dann die folgenden Variablen in der " **Blick** "-Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="c841c-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="c841c-411">Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c841c-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="c841c-412">Fügen Sie den folgenden Code in der **Update ()** -Methode hinzu, um ein raycast zu projizieren und den zieltreffer zu erkennen:</span><span class="sxs-lookup"><span data-stu-id="c841c-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="c841c-413">Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c841c-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="c841c-414">Klicken und ziehen Sie die Klasse " **Blick** " aus dem Ordner Scripts auf das Hauptkamera Objekt im Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="c841c-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="c841c-415">Kapitel 7: Einrichten der beiden Unity-Szenen</span><span class="sxs-lookup"><span data-stu-id="c841c-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="c841c-416">In diesem Kapitel wird erläutert, wie Sie die beiden Kulissen einrichten, die jeweils ein Video zum Streamen von Daten erstellen.</span><span class="sxs-lookup"><span data-stu-id="c841c-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="c841c-417">Sie duplizieren die Szene, die Sie bereits erstellt haben, sodass Sie Sie nicht erneut einrichten müssen, obwohl Sie die neue Szene bearbeiten, sodass sich das *gazebutton* -Objekt an einem anderen Speicherort befindet und über eine andere Darstellung verfügt.</span><span class="sxs-lookup"><span data-stu-id="c841c-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="c841c-418">Dies soll zeigen, wie Sie zwischen Szenen wechseln können.</span><span class="sxs-lookup"><span data-stu-id="c841c-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="c841c-419">Wechseln Sie dazu zu **Datei > Szene speichern unter...** . Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="c841c-420">Klicken Sie auf die Schaltfläche **neuer Ordner** .</span><span class="sxs-lookup"><span data-stu-id="c841c-420">Click the **New folder** button.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="c841c-422">Nennen Sie den Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="c841c-423">Das Fenster zum **Speichern der Szene** ist weiterhin geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c841c-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="c841c-424">Öffnen Sie den neu erstellten Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="c841c-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="c841c-425">Geben Sie im Feld **Dateiname:** Text **VideoScene1**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="c841c-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="c841c-426">Öffnen Sie in Unity den Ordner **Szenen** , und klicken Sie mit der linken Maustaste auf die Datei **VideoScene1** .</span><span class="sxs-lookup"><span data-stu-id="c841c-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="c841c-427">Verwenden Sie die Tastatur, und drücken Sie **STRG + D** , um die Szene zu duplizieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="c841c-428">Der Befehl **Duplizieren** kann auch ausgeführt werden, indem Sie zu **Edit > Duplicate**navigieren.</span><span class="sxs-lookup"><span data-stu-id="c841c-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="c841c-429">Unity erhöht automatisch die Namen Nummer der Szene, aber überprüfen Sie Sie trotzdem, um sicherzustellen, dass Sie mit dem zuvor eingefügten Code übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="c841c-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="c841c-430">Sie sollten über **VideoScene1** und **VideoScene2**verfügen.</span><span class="sxs-lookup"><span data-stu-id="c841c-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="c841c-431">Navigieren Sie in den beiden Kulissen zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="c841c-432">Wenn das Fenster " **Buildeinstellungen** " geöffnet ist, ziehen Sie die Kulissen in den Bereich " **Build** ".</span><span class="sxs-lookup"><span data-stu-id="c841c-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="c841c-434">Sie können beide Szenen aus dem Ordner " **Szenen** " auswählen, indem Sie die **STRG** -Taste gedrückt halten und dann mit der linken Maustaste auf jede Szene klicken und schließlich beides ziehen.</span><span class="sxs-lookup"><span data-stu-id="c841c-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="c841c-435">Schließen Sie das Fenster **Buildeinstellungen** , und doppelklicken Sie auf **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="c841c-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="c841c-436">Wenn die zweite Szene geöffnet ist, klicken Sie auf das untergeordnete **gazebutton** -Objekt von **insienoutsphere**, und legen Sie die Transformation wie folgt fest:</span><span class="sxs-lookup"><span data-stu-id="c841c-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="c841c-437">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="c841c-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="c841c-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-438">**X** 0</span></span>  |         <span data-ttu-id="c841c-439">**J** 1,3</span><span class="sxs-lookup"><span data-stu-id="c841c-439">**Y** 1.3</span></span>         | <span data-ttu-id="c841c-440">**Z** 3,6</span><span class="sxs-lookup"><span data-stu-id="c841c-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="c841c-441">Transformation-Drehung</span><span class="sxs-lookup"><span data-stu-id="c841c-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="c841c-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-442">**X** 0</span></span>  |          <span data-ttu-id="c841c-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-443">**Y** 0</span></span>          |  <span data-ttu-id="c841c-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="c841c-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="c841c-445">Transformieren: Skalieren</span><span class="sxs-lookup"><span data-stu-id="c841c-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="c841c-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-446">**X** 1</span></span>   |          <span data-ttu-id="c841c-447">**J** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-447">**Y** 1</span></span>          |  <span data-ttu-id="c841c-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="c841c-448">**Z** 1</span></span>  |

10. <span data-ttu-id="c841c-449">Wenn das untergeordnete **gazebutton** -Element noch ausgewählt ist, sehen Sie sich den **Inspektor** und den **Mesh-Filter**an.</span><span class="sxs-lookup"><span data-stu-id="c841c-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="c841c-450">Klicken Sie neben dem Feld **Mesh** Reference auf das kleine Ziel:</span><span class="sxs-lookup"><span data-stu-id="c841c-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="c841c-452">Ein **Gitter** Popup Fenster auswählen wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="c841c-453">Doppelklicken Sie in der Liste der **Assets**auf das **Cube** -Mesh.</span><span class="sxs-lookup"><span data-stu-id="c841c-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="c841c-455">Der **Mesh-Filter** wird aktualisiert und ist jetzt ein **Cube**.</span><span class="sxs-lookup"><span data-stu-id="c841c-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="c841c-456">Klicken Sie nun auf das **Zahnrad** Symbol neben **Sphere Collider** , und klicken Sie auf **Komponente entfernen**, um den Collider aus diesem Objekt zu löschen.</span><span class="sxs-lookup"><span data-stu-id="c841c-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="c841c-458">Klicken Sie bei ausgewähltem **gazebutton** auf die Schaltfläche **Komponente hinzufügen** am unteren Rand des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="c841c-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="c841c-459">Geben Sie im Suchfeld **Box**ein, und **Box Collider** ist eine Option. Klicken Sie auf diese Option, um dem **gazebutton** -Objekt einen **Feld-Collider** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c841c-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="c841c-461">Die " **gazebutton"-Schaltfläche** ist nun teilweise aktualisiert, um anders aussehen zu können. Sie erstellen nun jedoch ein neues **Material**, damit es vollständig anders aussieht und leichter als ein anderes Objekt erkannt werden kann, als das Objekt in der ersten Szene.</span><span class="sxs-lookup"><span data-stu-id="c841c-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="c841c-462">Navigieren Sie im **Projekt Panel**zum Ordner **Material** .</span><span class="sxs-lookup"><span data-stu-id="c841c-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="c841c-463">Duplizieren Sie das Inhalts **Inhalts Material (** drücken Sie auf der Tastatur **STRG** + **D** , oder klicken Sie mit der linken Maustaste auf das **Material**, und wählen Sie dann in der Menüoption Datei **Bearbeiten** die Option **Duplizieren**aus.)</span><span class="sxs-lookup"><span data-stu-id="c841c-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="c841c-464">![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-55.png)
    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="c841c-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="c841c-465">Wählen Sie das neue **buttonmaterial** -Material (hier **Button Material 1**) aus, und klicken Sie im **Inspektor**auf das Fenster **Albedo** -Farbe.</span><span class="sxs-lookup"><span data-stu-id="c841c-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="c841c-466">Es wird ein Popup Fenster angezeigt, in dem Sie eine andere Farbe auswählen können (Wählen Sie die gewünschten Optionen aus), und schließen Sie dann das Popup Fenster.</span><span class="sxs-lookup"><span data-stu-id="c841c-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="c841c-467">Das Material ist eine eigene Instanz und unterscheidet sich von der ursprünglichen.</span><span class="sxs-lookup"><span data-stu-id="c841c-467">The Material will be its own instance, and different to the original.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="c841c-469">Ziehen Sie das neue **Material** auf das untergeordnete **gazebutton** -Element, um das Erscheinungsbild vollständig zu aktualisieren, damit es von der Schaltfläche "erste Szenen" aus leicht unterschieden werden kann.</span><span class="sxs-lookup"><span data-stu-id="c841c-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="c841c-471">An diesem Punkt können Sie das Projekt im Editor testen, bevor Sie das UWP-Projekt entwickeln.</span><span class="sxs-lookup"><span data-stu-id="c841c-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="c841c-472">Klicken Sie im **Editor** auf die **Wiedergabe** Schaltfläche, und tragen Sie das Headset ein.</span><span class="sxs-lookup"><span data-stu-id="c841c-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="c841c-474">Sehen Sie sich die beiden **gazebutton** -Objekte an, um zwischen dem ersten und zweiten Video zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="c841c-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="c841c-475">Kapitel 8: Erstellen der UWP-Lösung</span><span class="sxs-lookup"><span data-stu-id="c841c-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="c841c-476">Nachdem Sie sichergestellt haben, dass der Editor keine Fehler aufweist, können Sie den Build erstellen.</span><span class="sxs-lookup"><span data-stu-id="c841c-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="c841c-477">So erstellen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c841c-477">To Build:</span></span>

1.  <span data-ttu-id="c841c-478">Speichern Sie die aktuelle Szene, indem Sie auf **Datei > Speichern**klicken.</span><span class="sxs-lookup"><span data-stu-id="c841c-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="c841c-479">Aktivieren Sie das Kontrollkästchen **Unity-C-\# Projekte** (Dies ist wichtig, da Sie die Klassen nach Abschluss des Builds bearbeiten können).</span><span class="sxs-lookup"><span data-stu-id="c841c-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="c841c-480">Wechseln Sie zu **Datei > Buildeinstellungen**, und klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="c841c-481">Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projekt Mappe erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="c841c-481">You will be prompted to select the folder where you want to build the Solution.</span></span>

5.  <span data-ttu-id="c841c-482">Erstellen Sie einen Ordner **BUILDS** , und erstellen Sie in diesem Ordner einen anderen Ordner mit einem entsprechenden Namen Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="c841c-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="c841c-483">Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, um diesen Ordner auszuwählen, um den Build an diesem Speicherort zu starten.</span><span class="sxs-lookup"><span data-stu-id="c841c-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="c841c-484">![Kapitel 8: Erstellen der UWP-Lösung](images/AzureLabs-Lab6-60.png)
    ![Kapitel 8: Erstellen der UWP-Lösung](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="c841c-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="c841c-485">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c841c-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="c841c-486">Kapitel 9: Bereitstellung auf lokalem Computer</span><span class="sxs-lookup"><span data-stu-id="c841c-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="c841c-487">Nachdem der Build abgeschlossen wurde, wird ein **Datei-Explorer** -Fenster am Speicherort des Builds angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c841c-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="c841c-488">Öffnen Sie den Ordner, den Sie benannt und erstellt haben, und doppelklicken Sie dann auf die Projektmappendatei (. sln) in diesem Ordner, um die Projekt Mappe mit Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c841c-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="c841c-489">Das einzige, was Sie tun müssen, ist die Bereitstellung Ihrer APP auf Ihrem Computer (oder auf dem *lokalen*Computer).</span><span class="sxs-lookup"><span data-stu-id="c841c-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="c841c-490">Zum Bereitstellen auf dem lokalen Computer:</span><span class="sxs-lookup"><span data-stu-id="c841c-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="c841c-491">Öffnen Sie in **Visual Studio 2017**die soeben erstellte Projektmappendatei.</span><span class="sxs-lookup"><span data-stu-id="c841c-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="c841c-492">Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="c841c-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="c841c-493">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="c841c-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Kapitel 9: Bereitstellung auf lokalem Computer](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="c841c-495">Sie müssen nun alle Pakete in der Projekt Mappe wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="c841c-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="c841c-496">Klicken Sie mit der rechten Maustaste **auf Ihre Projekt**Mappe, und klicken Sie auf **nuget-Pakete für Projekt Mappe wiederherstellen.**</span><span class="sxs-lookup"><span data-stu-id="c841c-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c841c-497">Dies geschieht, da die Pakete, die von Unity erstellt werden, für die Arbeit mit Ihren lokalen Computer verweisen verwendet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="c841c-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="c841c-498">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="c841c-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="c841c-499">Visual Studio erstellt zunächst eine Anwendung und stellt Sie dann bereit.</span><span class="sxs-lookup"><span data-stu-id="c841c-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="c841c-500">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="c841c-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Kapitel 9: Bereitstellung auf lokalem Computer](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="c841c-502">Wenn Sie die Mixed Reality-Anwendung ausführen, befinden Sie sich innerhalb des **insidebug** -Modells, das Sie in Ihrer APP verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="c841c-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="c841c-503">Diese Kugel wird an den Speicherort des Videos gestreamt und bietet eine 360-Grad-Ansicht des eingehenden Videos (für diese Art von Perspektive gefilmt).</span><span class="sxs-lookup"><span data-stu-id="c841c-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="c841c-504">Seien Sie nicht überrascht, wenn das Laden des Videos einige Sekunden dauert, Ihre APP ihrer verfügbaren Internet Geschwindigkeit unterliegt, da das Video abgerufen und dann heruntergeladen werden muss, damit Sie in Ihre APP streamen können.</span><span class="sxs-lookup"><span data-stu-id="c841c-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="c841c-505">Wenn Sie bereit sind, können Sie Szenen ändern und das zweite Video öffnen, indem Sie die rote Kugel ansehen!</span><span class="sxs-lookup"><span data-stu-id="c841c-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="c841c-506">Dann können Sie mit dem blauen Cube in der zweiten Szene wieder zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c841c-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="c841c-507">Ihre fertige Azure Media Service-Anwendung</span><span class="sxs-lookup"><span data-stu-id="c841c-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="c841c-508">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure Media Service zum Streamen von 360-Videos nutzt.</span><span class="sxs-lookup"><span data-stu-id="c841c-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab6-00.png)

![Lab-Ergebnis](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c841c-511">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="c841c-511">Bonus Exercises</span></span>

<span data-ttu-id="c841c-512">**Übung 1**</span><span class="sxs-lookup"><span data-stu-id="c841c-512">**Exercise 1**</span></span>

<span data-ttu-id="c841c-513">Es ist durchaus möglich, nur eine einzige Szene zu verwenden, um Videos in diesem Tutorial zu ändern.</span><span class="sxs-lookup"><span data-stu-id="c841c-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="c841c-514">Experimentieren Sie mit Ihrer Anwendung, und machen Sie Sie in einer einzigen Szene.</span><span class="sxs-lookup"><span data-stu-id="c841c-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="c841c-515">Fügen Sie der Mischung vielleicht sogar ein weiteres Video hinzu.</span><span class="sxs-lookup"><span data-stu-id="c841c-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="c841c-516">**Übung 2**</span><span class="sxs-lookup"><span data-stu-id="c841c-516">**Exercise 2**</span></span>

<span data-ttu-id="c841c-517">Experimentieren Sie mit Azure und Unity, und versuchen Sie, die Fähigkeit der APP zu implementieren, automatisch ein Video mit einer anderen Dateigröße auszuwählen, abhängig von der Stärke einer Internet Verbindung.</span><span class="sxs-lookup"><span data-stu-id="c841c-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


