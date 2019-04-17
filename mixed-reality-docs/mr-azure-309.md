---
title: MR und Azure 309 – Application insights
description: Führen Sie diesen Kurs Informationen zum Sammeln von Analysen in Bezug auf das Benutzerverhalten innerhalb einer mixed Reality-Anwendung, die mithilfe von Azure Application Insights-Diensts.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Application Insights, Hololens, immersive vr
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604774"
---
>[!NOTE]
><span data-ttu-id="b18d7-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="b18d7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b18d7-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b18d7-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b18d7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b18d7-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b18d7-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="b18d7-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b18d7-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="b18d7-110">MR und Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="b18d7-110">MR and Azure 309: Application insights</span></span>

![Endprodukt-starten](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="b18d7-112">In diesem Kurs erfahren Sie zum Hinzufügen von Application Insights-Funktionen einer mixed Reality-Anwendung mithilfe der Azure Application Insights-API zum Sammeln von Analysen in Bezug auf das Benutzerverhalten.</span><span class="sxs-lookup"><span data-stu-id="b18d7-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="b18d7-113">Application Insights ist ein Microsoft-Dienst, sodass Entwickler Analysedaten aus ihren Anwendungen erfassen und verwalten sie über ein Portal leicht zu bedienende.</span><span class="sxs-lookup"><span data-stu-id="b18d7-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="b18d7-114">Die Analyse kann von der Leistung, um benutzerdefinierte Informationen sein, die Sie sammeln möchten.</span><span class="sxs-lookup"><span data-stu-id="b18d7-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="b18d7-115">Weitere Informationen finden Sie auf die [Application Insights-Seite](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="b18d7-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="b18d7-116">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung die können die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="b18d7-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="b18d7-117">Ermöglicht dem Benutzer bestaunen und eine Szene verschieben.</span><span class="sxs-lookup"><span data-stu-id="b18d7-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="b18d7-118">Lösen Sie das Senden von Analytics, um die *Application Insights-Dienst*, durch die Verwendung von Blicke und NEAR-Scene-Objekten.</span><span class="sxs-lookup"><span data-stu-id="b18d7-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="b18d7-119">Die app wird auch aufrufen, auf den Dienst, Abrufen von Informationen, die am häufigsten durch den Benutzer dazu, welche wurde innerhalb der letzten 24 Stunden erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="b18d7-120">Dieses Objekt wird dessen Farbe in Grün geändert.</span><span class="sxs-lookup"><span data-stu-id="b18d7-120">That object will change its color to green.</span></span>

<span data-ttu-id="b18d7-121">In diesem Kurs erfahren Sie, wie die Ergebnisse aus den Application Insights-Dienst in eine Unity-basierten Anwendung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b18d7-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="b18d7-122">Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b18d7-123">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="b18d7-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b18d7-124">Kurs</span><span class="sxs-lookup"><span data-stu-id="b18d7-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b18d7-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b18d7-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b18d7-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="b18d7-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b18d7-127">MR und Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="b18d7-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="b18d7-128">✔️</span><span class="sxs-lookup"><span data-stu-id="b18d7-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b18d7-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b18d7-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b18d7-130">Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="b18d7-131">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="b18d7-132">Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b18d7-133">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b18d7-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b18d7-134">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="b18d7-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b18d7-135">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="b18d7-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b18d7-136">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.</span><span class="sxs-lookup"><span data-stu-id="b18d7-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b18d7-137">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="b18d7-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b18d7-138">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="b18d7-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b18d7-139">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b18d7-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b18d7-140">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="b18d7-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b18d7-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b18d7-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b18d7-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b18d7-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b18d7-143">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b18d7-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b18d7-144">Eine Reihe von Kopfhörer mit ein eingebautes Mikrofon verfügen (wenn die Kopfhörer nicht über eine integrierte mic und die Lautsprecher verfügt)</span><span class="sxs-lookup"><span data-stu-id="b18d7-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="b18d7-145">Zugriff auf das Internet für die Einrichtung von Azure und Abrufen von Application Insights-Daten</span><span class="sxs-lookup"><span data-stu-id="b18d7-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b18d7-146">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="b18d7-146">Before you start</span></span>

<span data-ttu-id="b18d7-147">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="b18d7-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="b18d7-148">Denken Sie daran, Daten, *Application Insights* Zeit in Anspruch nimmt daher etwas Geduld.</span><span class="sxs-lookup"><span data-stu-id="b18d7-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="b18d7-149">Wenn Sie möchten überprüfen, ob der Dienst Ihre Daten erhalten hat, sehen Sie sich [Kapitel 14](#chapter-14---the-application-insights-service-portal), die erfahren Sie, wie im Portal navigieren.</span><span class="sxs-lookup"><span data-stu-id="b18d7-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="b18d7-150">Kapitel 1: das Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="b18d7-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="b18d7-151">Verwendung von *Application Insights*, Sie benötigen zum Erstellen und Konfigurieren einer *Application Insights-Dienst* im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="b18d7-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="b18d7-152">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b18d7-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b18d7-153">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b18d7-154">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="b18d7-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b18d7-155">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Application Insights*, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b18d7-156">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="b18d7-158">Die neue Seite auf der rechten Seite bietet eine Beschreibung der *Azure Application Insights* Service.</span><span class="sxs-lookup"><span data-stu-id="b18d7-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="b18d7-159">Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="b18d7-161">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="b18d7-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="b18d7-162">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="b18d7-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="b18d7-163">Als **Anwendungstyp**Option **allgemeine**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="b18d7-164">Wählen Sie einen geeigneten **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="b18d7-165">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b18d7-166">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b18d7-167">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="b18d7-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="b18d7-168">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="b18d7-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="b18d7-169">Wählen Sie eine **Speicherort**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="b18d7-170">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="b18d7-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="b18d7-171">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="b18d7-171">Select **Create**.</span></span>

        ![Azure-Portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="b18d7-173">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="b18d7-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="b18d7-174">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="b18d7-176">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="b18d7-178">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b18d7-179">Sie gelangen in die neue *Application Insights-Dienst* Instanz.</span><span class="sxs-lookup"><span data-stu-id="b18d7-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="b18d7-181">Lassen Sie die Seite geöffnet, und leicht zugänglich, Sie kommen hier häufig, um die gesammelten Daten finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="b18d7-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b18d7-182">Um Application Insights zu implementieren, müssen Sie drei (3) bestimmte Werte verwenden: **Instrumentierungsschlüssel**, **Anwendungs-ID**, und **API-Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="b18d7-183">Im folgenden sehen Sie, wie Sie diese Werte aus Ihrem Dienst abrufen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="b18d7-184">Achten Sie darauf, beachten Sie diese Werte auf einen leeren *Editor* Seite, da Sie bald in Ihrem Code verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="b18d7-185">Finden der **Instrumentierungsschlüssel**, müssen Sie einen Bildlauf nach unten der Liste der Service-Funktionen, und klicken auf **Eigenschaften**, informiert, auf die Registerkarte angezeigt, die **Dienstschlüssel**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="b18d7-187">Ein wenig unten **Eigenschaften**, finden Sie **API-Zugriff**, die Sie klicken müssen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="b18d7-188">Im Bereich rechts stellt die **Anwendungs-ID** Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b18d7-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="b18d7-190">Mit der **Anwendungs-ID** Bereich immer noch geöffnet ist, klicken Sie auf **API-Schlüssel erstellen**, wird geöffnet die *API-Schlüssel erstellen* Bereich.</span><span class="sxs-lookup"><span data-stu-id="b18d7-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="b18d7-192">In der jetzt eröffnet *API-Schlüssel erstellen* Bereich, und geben Sie eine Beschreibung und **aktivieren Sie die drei Felder**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="b18d7-193">Klicken Sie auf **Schlüssel generieren**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-193">Click **Generate Key**.</span></span> <span data-ttu-id="b18d7-194">Ihre **API-Schlüssel** wird erstellt und angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure-Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="b18d7-196">Dies ist das einzige Mal Ihre **Dienstschlüssel** angezeigt wird, müssen Sie sicherstellen Sie jetzt eine Kopie der Datei vornehmen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="b18d7-197">Kapitel 2: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="b18d7-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="b18d7-198">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="b18d7-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b18d7-199">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-199">Open *Unity* and click **New**.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="b18d7-201">Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **MR\_Azure\_Anwendung\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="b18d7-202">Stellen Sie sicher, dass die *Vorlage* nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="b18d7-203">Legen Sie die *Speicherort* auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="b18d7-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b18d7-204">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-204">Then, click **Create project**.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="b18d7-206">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b18d7-207">Wechseln Sie zu **bearbeiten \> Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b18d7-208">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b18d7-209">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="b18d7-209">Close the **Preferences** window.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="b18d7-211">Öffnen Sie als Nächstes **Datei \> Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="b18d7-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="b18d7-213">Wechseln Sie zu **Datei \> Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="b18d7-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="b18d7-214">**Geräte** nastaven NA hodnotu **jedes Gerät**</span><span class="sxs-lookup"><span data-stu-id="b18d7-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="b18d7-215">Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="b18d7-216">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="b18d7-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="b18d7-217">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="b18d7-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="b18d7-218">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="b18d7-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="b18d7-219">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="b18d7-220">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b18d7-221">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-221">A save window will appear.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="b18d7-223">Erstellen Sie einen neuen Ordner für dieses und alle zukünftigen Szene, und klicken Sie dann die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="b18d7-225">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname:* Textfeld **ApplicationInsightsScene**, klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="b18d7-227">Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="b18d7-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="b18d7-228">In der **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="b18d7-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="b18d7-230">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="b18d7-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b18d7-231">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="b18d7-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b18d7-232">**Scripting** **Laufzeitversion** muss **experimentell (.NET 4.6 Äquivalent)**, löst der Editor neu starten müssen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="b18d7-233">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="b18d7-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="b18d7-234">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="b18d7-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="b18d7-236">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="b18d7-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="b18d7-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b18d7-237">**InternetClient**</span></span>     

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="b18d7-239">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality SDK** hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="b18d7-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="b18d7-241">Im **Buildeinstellungen**, **Unity C\# Projekte** nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="b18d7-241">Back in **Build Settings**, **Unity C\# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="b18d7-242">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="b18d7-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="b18d7-243">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="b18d7-243">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="b18d7-244">Kapitel 3: Importieren des Unity-Pakets</span><span class="sxs-lookup"><span data-stu-id="b18d7-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b18d7-245">Wenn Sie, überspringen möchten die *Unity einrichten* Komponenten dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Anpassungspaket**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="b18d7-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="b18d7-246">Dies wird auch die DLLs aus dem nächsten Kapitel enthalten.</span><span class="sxs-lookup"><span data-stu-id="b18d7-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="b18d7-247">Ist eine Fortsetzung nach dem Import, [ **Kapitel 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="b18d7-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b18d7-248">Um Application Insights in Unity verwenden zu können, müssen Sie die DLL, und die Newtonsoft-DLL zu importieren.</span><span class="sxs-lookup"><span data-stu-id="b18d7-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="b18d7-249">Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert.</span><span class="sxs-lookup"><span data-stu-id="b18d7-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="b18d7-250">Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="b18d7-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="b18d7-251">Um Application Insights in Ihrem eigenen Projekt zu importieren, stellen Sie sicher, dass [heruntergeladen haben die ".unitypackage", die Plug-Ins mit](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b18d7-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="b18d7-252">Führen Sie anschließend folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b18d7-252">Then, do the following:</span></span>

1.  <span data-ttu-id="b18d7-253">Hinzufügen der **.unitypackage** in Unity mithilfe der **Assets \> Paket importieren \> Custom Package** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="b18d7-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="b18d7-254">In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="b18d7-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="b18d7-256">Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="b18d7-257">Wechseln Sie zu der **Insights** Unterordner **-Plug-Ins** im Projekt anzuzeigen, und wählen Sie die folgenden Plug-Ins *nur*:</span><span class="sxs-lookup"><span data-stu-id="b18d7-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="b18d7-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="b18d7-258">Microsoft.ApplicationInsights</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="b18d7-260">Mit diesem *-Plug-Ins* ausgewählt haben, stellen sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **WSAPlayer** auch  **unchecked**, klicken Sie dann auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="b18d7-261">Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="b18d7-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="b18d7-263">Markieren die Plug-Ins wie folgt, konfiguriert sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="b18d7-264">Es gibt ein anderen Satz von DLLs im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="b18d7-265">Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **Insights** Ordner.</span><span class="sxs-lookup"><span data-stu-id="b18d7-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="b18d7-266">Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="b18d7-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="b18d7-267">Wählen Sie diese Datei, und klicken Sie dann im Inspector sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **nur** **WSAPlayer** ist**überprüft**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="b18d7-268">Klicken Sie auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-268">Click **Apply**.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="b18d7-270">Sie müssen jetzt folgen **Schritte 4 bis 6**, aber für die *Newtonsoft* -Plug-Ins stattdessen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="b18d7-271">Finden Sie unter den folgenden Screenshot für das Ergebnis sollte folgendermaßen aussehen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="b18d7-273">Kapitel 4: Einrichten der Kamera und Benutzer Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="b18d7-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="b18d7-274">In diesem Kapitel richten Sie die Kamera und die Steuerelemente, damit Benutzer anzeigen und in der Szene verschieben.</span><span class="sxs-lookup"><span data-stu-id="b18d7-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="b18d7-275">Mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, klicken Sie dann auf **erstellen > leere**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-275">Right-click in an empty area in the Hierarchy Panel, then on **Create > Empty**.</span></span>

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="b18d7-277">Benennen Sie die neue leere "gameobject" zu **Kamera übergeordneten**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="b18d7-279">Mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, klicken Sie dann auf **3D-Objekt**, klicken Sie dann auf **Kugel**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="b18d7-280">Benennen Sie die Kugel **rechten**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="b18d7-281">Legen Sie die **transformieren Skalierung** auf der rechten Hand **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="b18d7-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="b18d7-283">Entfernen der **Kugel "collider"** -Komponente aus der rechten Seite durch Klicken auf die **Zahnradsymbol** in die *Kugel "collider"* -Komponente, und klicken Sie dann **Komponente entfernen** .</span><span class="sxs-lookup"><span data-stu-id="b18d7-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="b18d7-285">In den Bereich der Hierarchie ziehen Sie die **Main Camera** und **rechten** Objekte ablegen der **Kamera übergeordneten** Objekt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="b18d7-287">Legen Sie die **transformieren Position** beider der **Main Camera** und die **rechten** -Objekt **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-31.png)

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="b18d7-290">Kapitel 5: Einrichten der Objekte in der Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="b18d7-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="b18d7-291">Sie werden nun einige grundlegenden Formen für Ihre Szene erstellen, mit denen der Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="b18d7-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="b18d7-292">Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt**, und wählen Sie dann **Ebene**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="b18d7-293">Legen Sie die Ebene **transformieren Position** zu **0, -1, 0**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="b18d7-294">Legen Sie die Ebene **transformieren Skalierung** zu **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="b18d7-296">Erstellen Sie eine grundlegende Material für die Verwendung mit Ihrem **Ebene** Objekt, sodass die anderen Formen leichter zu erkennen sind.</span><span class="sxs-lookup"><span data-stu-id="b18d7-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="b18d7-297">Navigieren Sie zu Ihrem *Projektfenster*, mit der rechten Maustaste, klicken Sie dann **erstellen**, gefolgt von **Ordner**, um einen neuen Ordner zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="b18d7-298">Nennen Sie sie **Materialien**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-298">Name it **Materials**.</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-34.png) ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="b18d7-301">Öffnen der **Materialien** Ordner, und dann mit der rechten Maustaste, klicken Sie auf **erstellen**, klicken Sie dann **Material**, um ein neues Material zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="b18d7-302">Nennen Sie sie **blaue**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-302">Name it **Blue**.</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-36.png) ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="b18d7-305">Mit dem neuen **blaue** Material ausgewählt haben, suchen auf der *Inspektor*, und klicken Sie auf das rechteckfenster zusammen mit **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="b18d7-306">Wählen Sie eine blaue Farbe (die einen der folgenden Abbildung ist **Hexadezimalfarbe: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="b18d7-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="b18d7-307">Klicken Sie auf die Schaltfläche "Schließen", nachdem Sie ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="b18d7-307">Click the close button once you have chosen.</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="b18d7-309">Ziehen Sie Ihr neue Material aus der **Materialien** Ordner auf den neu erstellten **Ebene**, innerhalb der Szene (oder legen Sie diese auf die **Ebene** -Objekts innerhalb der  *Hierarchie*).</span><span class="sxs-lookup"><span data-stu-id="b18d7-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="b18d7-311">Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt, Capsule**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="b18d7-312">Mit der **Capsule** ausgewählt haben, Ändern seiner **transformieren** *Position* auf: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="b18d7-313">Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt, Cube**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="b18d7-314">Mit der **Cube** ausgewählt haben, Ändern seiner **transformieren** *Position* auf: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="b18d7-315">Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt, Kugel**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="b18d7-316">Mit der **Kugel** ausgewählt haben, Ändern seiner **transformieren** *Position* auf: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="b18d7-318">Diese *Position* Werte *Vorschläge*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="b18d7-319">Sie können sich die Positionen der Objekte, was auch immer Sie möchten, festlegen, aber es einfacher, für den Benutzer der Anwendung, ist wenn die Objekte in Abständen nicht zu weit von der Kamera sind.</span><span class="sxs-lookup"><span data-stu-id="b18d7-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="b18d7-320">Wenn Ihre Anwendung ausgeführt wird, muss es zum Identifizieren der Objekte in der Szene, um dies zu erreichen können, müssen sie gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="b18d7-321">Wählen Sie eines der Objekte, und klicken Sie in der *Inspektor* auf **Tag hinzufügen...** , dem Austauschen wird die *Inspektor* mit der **Tags und Ebenen** Bereich.</span><span class="sxs-lookup"><span data-stu-id="b18d7-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="b18d7-322">![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="b18d7-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="b18d7-323">Klicken Sie auf die **+ (plus)** symbol, und geben Sie den Namen des Tags als **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="b18d7-325">Wenn Sie einen anderen Namen für Ihr Tag verwenden, müssen Sie sicherstellen, diese Änderung auch die *DataFromAnalytics*, *ObjectTrigger*, und *bestaunen*, später, Skripts, damit Ihre Objekte gefunden, und erkannt werden, innerhalb der Szene.</span><span class="sxs-lookup"><span data-stu-id="b18d7-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="b18d7-326">Mit dem Tag, der erstellt wird müssen Sie jetzt diese auf alle drei der Objekte anwenden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="b18d7-327">Von der *Hierarchie*, enthalten die **UMSCHALT** Schlüssel, und klicken Sie dann die **Capsule**, **Cube**, und **Kugel**, Objekte, klicken Sie dann in der *Inspektor*, klicken Sie auf das Dropdownmenü neben **Tag**, klicken Sie dann auf die *ObjectInScene* markieren Sie Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="b18d7-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="b18d7-328">![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="b18d7-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="b18d7-329">Kapitel 6: Erstellen Sie die ApplicationInsightsTracker-Klasse</span><span class="sxs-lookup"><span data-stu-id="b18d7-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="b18d7-330">Ist das erste Skript, das Sie erstellen müssen **ApplicationInsightsTracker**, die für verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="b18d7-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="b18d7-331">Erstellen von Ereignissen, die basierend auf Benutzerinteraktionen zum Übermitteln an Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="b18d7-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="b18d7-332">Erstellen die entsprechenden Ereignisnamen, je nach Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="b18d7-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="b18d7-333">Übermitteln von Ereignissen an die Application Insights-Dienst-Instanz.</span><span class="sxs-lookup"><span data-stu-id="b18d7-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="b18d7-334">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b18d7-334">To create this class:</span></span>

1.  <span data-ttu-id="b18d7-335">Mit der rechten Maustaste den *Projekt Bereich*, klicken Sie dann **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-335">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="b18d7-336">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-336">Name the folder **Scripts**.</span></span>

    ![Erstellen Sie die ApplicationInsightsTracker-Klasse](images/AzureLabs-Lab309-46.png)  ![Erstellen Sie die ApplicationInsightsTracker-Klasse](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="b18d7-339">Mit der **Skripts** Ordner erstellt haben, doppelklicken Sie darauf, um zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="b18d7-340">Klicken Sie dann in diesem Ordner mit der rechten Maustaste, **erstellen > C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-340">Then, within that folder, right-click, **Create > C\# Script**.</span></span> <span data-ttu-id="b18d7-341">Nennen Sie das Skript **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="b18d7-342">Doppelklicken Sie auf die neue **ApplicationInsightsTracker** Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b18d7-343">Aktualisieren Sie die Namespaces am Anfang des Skripts werden wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b18d7-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="b18d7-344">Fügen Sie in der Klasse die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="b18d7-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="b18d7-345">Legen Sie die **InstrumentationKey "," ApplicationId und "api_key"** Werte entsprechend mithilfe der *Dienstschlüssel* über das Azure-Verwaltungsportal, wie im [Kapitel 1](#chapter-1---the-azure-portal), Schritt 9 oder höher.</span><span class="sxs-lookup"><span data-stu-id="b18d7-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="b18d7-346">Fügen Sie dann die **Start()** und **Awake()** -Methoden, die aufgerufen werden, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="b18d7-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="b18d7-347">Fügen Sie die Methoden, die verantwortlich für das Senden der Ereignisse und Metriken, die von der Anwendung registriert:</span><span class="sxs-lookup"><span data-stu-id="b18d7-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="b18d7-348">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="b18d7-349">Kapitel 7: Erstellen Sie das Skript für die Blicke</span><span class="sxs-lookup"><span data-stu-id="b18d7-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="b18d7-350">Ist das nächste Skript zum Erstellen der **bestaunen** Skript.</span><span class="sxs-lookup"><span data-stu-id="b18d7-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="b18d7-351">Dieses Skript ist verantwortlich für das Erstellen einer *Raycast* , projiziert weiterleiten aus der *Main Camera*, welches Objekt erkannt, wird der Benutzer ansehen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="b18d7-352">In diesem Fall die *Raycast* benötigen, um festzustellen, ob der Benutzer auf ein Objekt mit sieht die **ObjectInScene** markieren, und wie langen den Benutzer zählen *gazes* auf dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="b18d7-353">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b18d7-354">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-354">Right-click inside the **Scripts** folder, click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b18d7-355">Nennen Sie das Skript **bestaunen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="b18d7-356">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b18d7-357">Ersetzen Sie den vorhandenen Code durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b18d7-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="b18d7-358">Code für die **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="b18d7-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="b18d7-359">In der **bestaunen** -Klasse verwenden, fügen Sie den folgenden Code in die **Update()** Methode, um das Projekt ein *Raycast* und erkennen Sie das Ziel erreicht:</span><span class="sxs-lookup"><span data-stu-id="b18d7-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="b18d7-360">Hinzufügen der **ResetFocusedObject()** Methode zum Senden von Daten zu **Application Insights** Wenn der Benutzer auf ein Objekt gesucht wurde.</span><span class="sxs-lookup"><span data-stu-id="b18d7-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="b18d7-361">Sie haben jetzt die **bestaunen** Skript.</span><span class="sxs-lookup"><span data-stu-id="b18d7-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="b18d7-362">Speichern Sie die Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="b18d7-363">Kapitel 8 – erstellen Sie die ObjectTrigger-Klasse</span><span class="sxs-lookup"><span data-stu-id="b18d7-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="b18d7-364">Ist das nächste Skript, das Sie erstellen müssen **ObjectTrigger**, die für verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="b18d7-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="b18d7-365">Hinzufügen von Komponenten, die Kollision bis zur Kamera Main erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="b18d7-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="b18d7-366">Ermitteln, ob die Kamera in der Nähe eines Objekts als ist **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="b18d7-367">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="b18d7-367">To create the script:</span></span>

1.  <span data-ttu-id="b18d7-368">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b18d7-369">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** **C\# > Skript**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-369">Right-click inside the **Scripts** folder, click **Create** **C\# > Script**.</span></span> <span data-ttu-id="b18d7-370">Nennen Sie das Skript **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="b18d7-371">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="b18d7-372">Ersetzen Sie den vorhandenen Code durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b18d7-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="b18d7-373">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="b18d7-374">Kapitel 9 – erstellen Sie die DataFromAnalytics-Klasse</span><span class="sxs-lookup"><span data-stu-id="b18d7-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="b18d7-375">Sie müssen nun zum Erstellen der **DataFromAnalytics** Skripts, die dafür verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="b18d7-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="b18d7-376">Beim Abrufen von Analytics-Daten darüber, welche Objekt von der Kamera die erreicht wurden hat.</span><span class="sxs-lookup"><span data-stu-id="b18d7-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="b18d7-377">Mithilfe der *Dienstschlüssel*, die mit Ihrer Instanz von Azure Application Insights-Dienst zulassen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="b18d7-378">Sortieren die Objekte in der Szene, die höchste Anzahl von Ereignissen, nach denen hat.</span><span class="sxs-lookup"><span data-stu-id="b18d7-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="b18d7-379">Farbänderungen Material, das am häufigsten approached-Objekt zu *Grün*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="b18d7-380">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="b18d7-380">To create the script:</span></span>

1.  <span data-ttu-id="b18d7-381">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b18d7-382">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** **C\# > Skript**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-382">Right-click inside the **Scripts** folder, click **Create** **C\# > Script**.</span></span> <span data-ttu-id="b18d7-383">Nennen Sie das Skript **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="b18d7-384">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b18d7-385">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="b18d7-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="b18d7-386">Fügen Sie innerhalb des Skripts die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b18d7-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="b18d7-387">In der **DataFromAnalytics** Klasse, die nach der rechten Maustaste die **Start()** -Methode, fügen Sie die folgende Methode wird aufgerufen, **FetchAnalytics()**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="b18d7-388">Diese Methode ist verantwortlich für das Auffüllen der Liste der Schlüssel-/Wertpaaren, mit einem *"gameobject"* und eine Anzahl der Platzhalter-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="b18d7-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="b18d7-389">Klicken Sie dann initialisiert die **GetWebRequest()** Coroutine.</span><span class="sxs-lookup"><span data-stu-id="b18d7-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="b18d7-390">Die Abfragestruktur des Aufrufs von *Application Insights* können innerhalb dieser Methode finden Sie auch, wie die *Abfrage-URL* Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="b18d7-391">Direkt unterhalb der **FetchAnalytics()** -Methode, fügen Sie eine Methode namens **GetWebRequest()**, gibt ein *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="b18d7-392">Diese Methode ist verantwortlich für die Anforderung an, wie oft ein Ereignis, das mit einem bestimmten entspricht *"gameobject"*, aufgerufen wurde in *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="b18d7-393">Wenn alle gesendeten Abfragen zurückgegeben, die **DetermineWinner()** Methode wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="b18d7-394">Die nächste Methode ist **DetermineWinner()**, sortiert die Liste der *"gameobject"* und *Int* -Paare, anhand der höchsten Anzahl von Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="b18d7-395">Er ändert dann die Material Farbe, *"gameobject"* zu *Grün* (als Feedback, damit es mit der höchsten Anzahl).</span><span class="sxs-lookup"><span data-stu-id="b18d7-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="b18d7-396">Dadurch werden eine Meldung mit den Ergebnissen der Analyse angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="b18d7-397">Fügen Sie die Klassenstruktur, der verwendet wird, deserialisiert das JSON-Objekt, das Empfangen von *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="b18d7-398">Fügen Sie diese Klassen am Ende Ihrer **DataFromAnalytics** -Klassendatei **außerhalb** der Definition der Klasse.</span><span class="sxs-lookup"><span data-stu-id="b18d7-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="b18d7-399">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="b18d7-400">Kapitel 10 – erstellen Sie die Bewegung-Klasse</span><span class="sxs-lookup"><span data-stu-id="b18d7-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="b18d7-401">Die **Bewegung** Skript ist das nächste Skript, das Sie erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="b18d7-402">Er ist verantwortlich für:</span><span class="sxs-lookup"><span data-stu-id="b18d7-402">It is responsible for:</span></span>

- <span data-ttu-id="b18d7-403">Verschieben die Main Camera entsprechend der Richtung der Kamera sucht in Richtung.</span><span class="sxs-lookup"><span data-stu-id="b18d7-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="b18d7-404">Alle anderen Skripts und szeneobjekte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="b18d7-405">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="b18d7-405">To create the script:</span></span>

1.  <span data-ttu-id="b18d7-406">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b18d7-407">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-407">Right-click inside the **Scripts** folder, click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b18d7-408">Nennen Sie das Skript **Bewegung**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="b18d7-409">Doppelklicken Sie auf das Skript mit öffnen *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="b18d7-410">Ersetzen Sie den vorhandenen Code durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b18d7-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="b18d7-411">In der **Bewegung** -Klasse, *unten* die leere **Update()** -Methode, fügen Sie die folgenden Methoden, die der Benutzer auf den Hand-Controller verwenden, um im virtuellen Raum zu verschieben:</span><span class="sxs-lookup"><span data-stu-id="b18d7-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="b18d7-412">Fügen Sie schließlich den Aufruf der Methode innerhalb der **Update()** Methode.</span><span class="sxs-lookup"><span data-stu-id="b18d7-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="b18d7-413">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="b18d7-414">Kapitel 11: Festlegen der Verweise auf die Skripts</span><span class="sxs-lookup"><span data-stu-id="b18d7-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="b18d7-415">In diesem Kapitel es erforderlich, die **Datenverschiebung** Skript auf die **Kamera übergeordneten** und legen Sie Ziele Verweis.</span><span class="sxs-lookup"><span data-stu-id="b18d7-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="b18d7-416">Dieses Skript behandelt platzieren den anderen Skripts, in denen sie sein müssen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="b18d7-417">Aus der **Skripts** Ordner in der *Projektfenster*, ziehen Sie die **Bewegung** Skript aus, um die **Kamera übergeordneten** Objekt befindet sich in der  *Hierarchie-Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Die Skripts verweisen in der Unity-Szene einrichten](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="b18d7-419">Klicken Sie auf die **Kamera übergeordneten**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="b18d7-420">In der *Hierarchie Bereich*, ziehen Sie die **rechten** -Objekt aus der *Hierarchie Bereich* mit dem Verweisziel **Controller**in der *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="b18d7-421">Legen Sie die **Benutzer Geschwindigkeit** zu **5**, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Die Skripts verweisen in der Unity-Szene einrichten](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="b18d7-423">Kapitel 12: Erstellen Sie das Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="b18d7-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="b18d7-424">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.</span><span class="sxs-lookup"><span data-stu-id="b18d7-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b18d7-425">Navigieren Sie zu **Buildeinstellungen**, **(Datei > Buildeinstellungen...)** .</span><span class="sxs-lookup"><span data-stu-id="b18d7-425">Navigate to **Build Settings**, **(File > Build Settings...)**.</span></span>

2.  <span data-ttu-id="b18d7-426">Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="b18d7-428">Ein **Datei-Explorer** Fenster werden Popupfenster, dem Sie aufgefordert werden, eines Speicherorts für den Build.</span><span class="sxs-lookup"><span data-stu-id="b18d7-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="b18d7-429">Erstellen Sie einen neuen Ordner (indem Sie auf **neuer Ordner** in der oberen linken Ecke), und nennen Sie sie **erstellt**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="b18d7-431">Öffnen Sie die neue **erstellt** Ordner, und erstellen Sie einen anderen Ordner (mit **neuer Ordner** einmal), und nennen Sie sie **MR\_Azure\_Anwendung\_ Insights**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="b18d7-433">Mit der **MR\_Azure\_Anwendung\_Insights** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="b18d7-434">Das Projekt wird eine Minute erstellen dauern.</span><span class="sxs-lookup"><span data-stu-id="b18d7-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="b18d7-435">Folgende *erstellen*, **Datei-Explorer** wird angezeigt, die Sie den Standort des neuen Projekts.</span><span class="sxs-lookup"><span data-stu-id="b18d7-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="b18d7-436">Kapitel 13 – MR_Azure_Application_Insights-app auf Ihrem Computer bereitstellen</span><span class="sxs-lookup"><span data-stu-id="b18d7-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="b18d7-437">Zum Bereitstellen der **MR\_Azure\_Anwendung\_Insights** -app auf Ihrem lokalen Computer:</span><span class="sxs-lookup"><span data-stu-id="b18d7-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="b18d7-438">Öffnen Sie die Projektmappendatei, die von Ihrem **MR\_Azure\_Anwendung\_Insights** -app in **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="b18d7-439">In der **Projektmappenplattform**Option **X86, lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="b18d7-440">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="b18d7-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="b18d7-442">Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="b18d7-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="b18d7-443">Ihre app sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b18d7-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="b18d7-444">Starten Sie die mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b18d7-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="b18d7-445">Verschieben der Szene annähert, die Objekte aus, und betrachten, wenn die *Azure Insights-Dienst* wurden genügend Ereignisdaten erfasst, die sie legt das Objekt, das die meisten in Grün erreicht wurde, hat.</span><span class="sxs-lookup"><span data-stu-id="b18d7-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="b18d7-446">Während die durchschnittliche Wartezeit für die *Ereignisse und Metriken* dauert ca. 15 Minuten vom Dienst erfasst werden, in einigen Fällen kann es bis zu einer Stunde dauern.</span><span class="sxs-lookup"><span data-stu-id="b18d7-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="b18d7-447">Kapitel 14: das Application Insights-Dienst-portal</span><span class="sxs-lookup"><span data-stu-id="b18d7-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="b18d7-448">Nachdem Sie in der Szene gewechselt haben und auf mehrere Objekte gazed Sie die Datensammlung sehen in der *Application Insights-Dienst* Portal.</span><span class="sxs-lookup"><span data-stu-id="b18d7-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="b18d7-449">Wechseln Sie zurück zu Ihrem Application Insights-Dienst-Portal.</span><span class="sxs-lookup"><span data-stu-id="b18d7-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="b18d7-450">Klicken Sie auf *Metrik-Explorer*.</span><span class="sxs-lookup"><span data-stu-id="b18d7-450">Click on *Metrics Explorer*.</span></span>

    ![Sehen Sie gesammelte Daten](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="b18d7-452">Es wird geöffnet, auf einer Registerkarte mit dem Diagramm die darstellen der *Ereignisse und Metriken* im Zusammenhang mit Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b18d7-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="b18d7-453">Wie bereits erwähnt, dauert es einige Zeit (bis zu 1 Stunde) für die Daten, die im Diagramm angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="b18d7-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Sehen Sie gesammelte Daten](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="b18d7-455">Klicken Sie auf die *Ereignisse Leiste* in die *Gesamtanzahl von Ereignissen* von Version der Anwendung, um eine detaillierte Aufschlüsselung der Ereignisse mit ihren Namen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b18d7-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Sehen Sie gesammelte Daten](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="b18d7-457">Ihre fertige Ihrer Anwendung Application Insights-Dienst</span><span class="sxs-lookup"><span data-stu-id="b18d7-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="b18d7-458">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Application Insights-Diensts zum Überwachen der Aktivität des Benutzers in Ihrer app nutzt.</span><span class="sxs-lookup"><span data-stu-id="b18d7-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b18d7-460">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="b18d7-460">Bonus Exercises</span></span>

<span data-ttu-id="b18d7-461">**Übung 1**</span><span class="sxs-lookup"><span data-stu-id="b18d7-461">**Exercise 1**</span></span>

<span data-ttu-id="b18d7-462">Versuchen Sie es erstellen, anstatt manuell erstellen, die ObjectInScene Objekte aus, und legen Sie die Koordinaten in der Ebene in Ihren Skripts.</span><span class="sxs-lookup"><span data-stu-id="b18d7-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="b18d7-463">Auf diese Weise können Sie Fragen Azure welches der am häufigsten verwendete Objekt (entweder aus Blicke oder NEAR-Ergebnissen) wurde, und erzeugen eine *zusätzliche* eines dieser Objekte.</span><span class="sxs-lookup"><span data-stu-id="b18d7-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="b18d7-464">**Übung 2**</span><span class="sxs-lookup"><span data-stu-id="b18d7-464">**Exercise 2**</span></span>

<span data-ttu-id="b18d7-465">Sortieren Sie die Application Insights-Ergebnisse bis zu Zeitpunkt, damit Sie die relevantesten Daten abzurufen, und dieser Uhrzeit sensiblen Daten in Ihrer Anwendung implementieren.</span><span class="sxs-lookup"><span data-stu-id="b18d7-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

