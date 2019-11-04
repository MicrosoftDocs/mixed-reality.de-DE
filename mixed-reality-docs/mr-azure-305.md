---
title: Mr und Azure 305-Funktionen und Speicher
description: Arbeiten Sie diesen Kurs durch, um zu erfahren, wie Sie Azure Storage und Funktionen innerhalb einer gemischten Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Funktionen, Speicher, hololens, immersive, VR
ms.openlocfilehash: 79c276d45163465c9921d02343d41d52d5f094e7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437991"
---
>[!NOTE]
><span data-ttu-id="128af-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="128af-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="128af-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="128af-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="128af-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="128af-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="128af-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="128af-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="128af-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="128af-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="128af-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="128af-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="128af-110">Mr und Azure 305: Funktionen und Speicher</span><span class="sxs-lookup"><span data-stu-id="128af-110">MR and Azure 305: Functions and storage</span></span>

![Endgültiges Produkt-Start](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="128af-112">In diesem Kurs erfahren Sie, wie Sie Azure Functions und Daten mit einer Azure Storage Ressource in einer gemischten Reality-Anwendung erstellen und verwenden.</span><span class="sxs-lookup"><span data-stu-id="128af-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="128af-113">*Azure Functions* ist ein Microsoft-Dienst, der Entwicklern das Ausführen von kleinen Code Elementen ("Functions") in Azure ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="128af-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="128af-114">Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, die viele Vorteile haben kann.</span><span class="sxs-lookup"><span data-stu-id="128af-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="128af-115">*Azure Functions* unterstützt mehrere Entwicklungs Sprachen, wie z. b. C\#, F\#, Node. js, Java und PHP.</span><span class="sxs-lookup"><span data-stu-id="128af-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="128af-116">Weitere Informationen finden Sie im [Artikel Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="128af-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="128af-117">*Azure Storage* ist ein Microsoft-clouddienst, der es Entwicklern ermöglicht, Daten zu speichern, mit der Versicherung, dass Sie hoch verfügbar, sicher, dauerhaft, skalierbar und redundant ist.</span><span class="sxs-lookup"><span data-stu-id="128af-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="128af-118">Dies bedeutet, dass Microsoft alle Wartungsarbeiten und kritischen Probleme für Sie behandelt.</span><span class="sxs-lookup"><span data-stu-id="128af-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="128af-119">Weitere Informationen finden Sie im [Artikel Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="128af-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="128af-120">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="128af-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="128af-121">Ermöglicht dem Benutzer das durchschauen einer Szene.</span><span class="sxs-lookup"><span data-stu-id="128af-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="128af-122">Löst das Erzeugen von Objekten aus, wenn der Benutzer auf einer 3D-Schaltfläche ' ' geklickt hat.</span><span class="sxs-lookup"><span data-stu-id="128af-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="128af-123">Die erzeugten Objekte werden von einer Azure-Funktion ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="128af-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="128af-124">Während jedes Objekt erzeugt wird, speichert die Anwendung den Objekttyp in einer *Azure-Datei*, die sich in *Azure Storage*befindet.</span><span class="sxs-lookup"><span data-stu-id="128af-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="128af-125">Beim Laden eines zweiten Zeitraums werden die *Azure-Datei* Daten abgerufen und verwendet, um die erstellenden Aktionen aus der vorherigen Instanz der Anwendung wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="128af-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="128af-126">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="128af-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="128af-127">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="128af-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="128af-128">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="128af-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="128af-129">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="128af-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="128af-130">Natürlich</span><span class="sxs-lookup"><span data-stu-id="128af-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="128af-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="128af-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="128af-132"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="128af-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="128af-133">Mr und Azure 305: Funktionen und Speicher</span><span class="sxs-lookup"><span data-stu-id="128af-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="128af-134">✔️</span><span class="sxs-lookup"><span data-stu-id="128af-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="128af-135">✔️</span><span class="sxs-lookup"><span data-stu-id="128af-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="128af-136">Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="128af-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="128af-137">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="128af-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="128af-138">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="128af-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="128af-139">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="128af-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="128af-140">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="128af-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="128af-141">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="128af-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="128af-142">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="128af-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="128af-143">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="128af-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="128af-144">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="128af-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="128af-145">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="128af-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="128af-146">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="128af-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="128af-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="128af-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="128af-148">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="128af-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="128af-149">Ein Abonnement für ein Azure-Konto zum Erstellen von Azure-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="128af-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="128af-150">Internet Zugriff für Azure-Setup und Datenabruf</span><span class="sxs-lookup"><span data-stu-id="128af-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="128af-151">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="128af-151">Before you start</span></span>

<span data-ttu-id="128af-152">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="128af-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="128af-153">Kapitel 1: Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="128af-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="128af-154">Um den **Azure Storage-Dienst**zu verwenden, müssen Sie ein **Speicherkonto** in der Azure-Portal erstellen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="128af-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="128af-155">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="128af-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="128af-156">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="128af-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="128af-157">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="128af-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="128af-158">Nachdem Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Speicherkonto*, und drücken Sie die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="128af-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![Azure Storage-Suche](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="128af-160">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="128af-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="128af-161">Auf der neuen Seite wird eine Beschreibung des *Azure Storage-Konto* Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="128af-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="128af-162">Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="128af-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Dienst erstellen](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="128af-164">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="128af-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="128af-165">Fügen Sie einen *Namen* für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="128af-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="128af-166">Wählen Sie unter *Bereitstellungs Modell*die Option **Resource Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="128af-167">Wählen Sie unter *Kontoart*die Option **Speicher (universell, Version v1)** aus.</span><span class="sxs-lookup"><span data-stu-id="128af-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="128af-168">Bestimmen Sie den *Speicherort* für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="128af-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="128af-169">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="128af-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="128af-170">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="128af-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="128af-171">Wählen Sie für die *Replikation* den **georedundanten Speicher mit Lesezugriff (RA-GRS)** aus.</span><span class="sxs-lookup"><span data-stu-id="128af-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="128af-172">Wählen Sie für *Leistung*die Option **Standard**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="128af-173">Lassen Sie die Option " *sichere Übertragung erforderlich* " **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="128af-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="128af-174">Wählen Sie ein *Abonnement*aus.</span><span class="sxs-lookup"><span data-stu-id="128af-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="128af-175">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue *Ressourcengruppe* .</span><span class="sxs-lookup"><span data-stu-id="128af-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="128af-176">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="128af-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="128af-177">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="128af-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="128af-178">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="128af-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="128af-179">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="128af-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="128af-180">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="128af-180">Select **Create**.</span></span>

        ![Eingabe Dienst Informationen](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="128af-182">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="128af-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="128af-183">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="128af-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![neue Benachrichtigung im Azure-Portal](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="128af-185">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="128af-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Gehe zu Ressource](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="128af-187">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="128af-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="128af-188">Sie gelangen zu ihrer neuen *Speicherkonto* -Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="128af-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![Zugriffstasten](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="128af-190">Klicken Sie auf *Zugriffsschlüssel*, um die Endpunkte für diesen Cloud-Dienst anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="128af-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="128af-191">Verwenden Sie *Notepad* oder ähnliches, um einen Ihrer Schlüssel zur späteren Verwendung zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="128af-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="128af-192">Beachten Sie auch den Wert der *Verbindungs Zeichenfolge* , wie er in der *azureservices* -Klasse verwendet wird, die Sie später erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="128af-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Verbindungs Zeichenfolge kopieren](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="128af-194">Kapitel 2: Einrichten einer Azure-Funktion</span><span class="sxs-lookup"><span data-stu-id="128af-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="128af-195">Sie schreiben jetzt eine **Azure** - **Funktion** im Azure-Dienst.</span><span class="sxs-lookup"><span data-stu-id="128af-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="128af-196">Sie können eine **Azure-Funktion** verwenden, um nahezu alles zu tun, was Sie mit einer klassischen Funktion in Ihrem Code tun würden. der Unterschied besteht darin, dass jede Anwendung, die über Anmelde Informationen für den Zugriff auf Ihr Azure-Konto verfügt, auf diese Funktion zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="128af-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="128af-197">So erstellen Sie eine Azure-Funktion:</span><span class="sxs-lookup"><span data-stu-id="128af-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="128af-198">Klicken Sie in Ihrem *Azure-Portal*in der oberen linken Ecke auf **neu** , suchen Sie nach *Funktionen-App*, und **drücken**Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="128af-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Erstellen einer Funktionen-App](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="128af-200">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="128af-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="128af-201">Auf der neuen Seite wird eine Beschreibung des *Azure-Funktionen-App* Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="128af-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="128af-202">Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="128af-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Funktions-APP-Informationen](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="128af-204">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="128af-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="128af-205">Geben Sie einen *APP-Namen*an.</span><span class="sxs-lookup"><span data-stu-id="128af-205">Provide an *App name*.</span></span> <span data-ttu-id="128af-206">Hier können nur Buchstaben und Ziffern verwendet werden (groß-oder Kleinbuchstaben sind zulässig).</span><span class="sxs-lookup"><span data-stu-id="128af-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="128af-207">Wählen Sie Ihr bevorzugtes *Abonnement*aus.</span><span class="sxs-lookup"><span data-stu-id="128af-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="128af-208">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue *Ressourcengruppe* .</span><span class="sxs-lookup"><span data-stu-id="128af-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="128af-209">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="128af-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="128af-210">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="128af-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="128af-211">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="128af-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="128af-212">Wählen Sie für diese Übung *Windows* als ausgewähltes **Betriebssystem**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="128af-213">Wählen Sie den *Verbrauchs Plan* für den **Hostingplan**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="128af-214">Bestimmen Sie den *Speicherort* für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="128af-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="128af-215">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="128af-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="128af-216">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="128af-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="128af-217">Wählen Sie die gleiche Region wie das Speicherkonto aus, um eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="128af-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="128af-218">Wählen Sie für *Speicher*die Option **vorhandene verwenden**aus, und suchen Sie dann mithilfe des Dropdown Menüs nach dem zuvor erstellten Speicher.</span><span class="sxs-lookup"><span data-stu-id="128af-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="128af-219">Lassen Sie für diese Übung *Application Insights* deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="128af-219">Leave *Application Insights* off for this exercise.</span></span>

        ![Details der Eingabefunktionen-App](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="128af-221">Klicken Sie auf die Schaltfläche **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="128af-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="128af-222">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="128af-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="128af-223">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="128af-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Benachrichtigung über das neue Azure-Portal](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="128af-225">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="128af-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Gehe zu Ressourcen Funktions-APP](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="128af-227">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="128af-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="128af-228">Sie gelangen zu ihrer neuen *Funktionen-App* Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="128af-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="128af-229">Zeigen Sie im *Funktionen-App* Dashboard mit der Maus auf *Funktionen*, die sich im Bereich auf der linken Seite befinden, und klicken Sie dann auf das Symbol **+ (plus)** .</span><span class="sxs-lookup"><span data-stu-id="128af-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![neue Funktion erstellen](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="128af-231">Vergewissern Sie sich auf der nächsten Seite, dass **webhook + API** ausgewählt ist, und wählen Sie für *Sprache auswählen* die Option **CSharp**aus, da es sich hierbei um die für dieses Tutorial verwendete Sprache handelt.</span><span class="sxs-lookup"><span data-stu-id="128af-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="128af-232">Klicken Sie abschließend auf die Schaltfläche **Diese Funktion erstellen** .</span><span class="sxs-lookup"><span data-stu-id="128af-232">Lastly, click the **Create this function** button.</span></span>

    ![webhook CSharp auswählen](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="128af-234">Sie sollten zur Codepage (Run. CSX) weitergeleitet werden. Klicken Sie auf der linken Seite auf die neu erstellte Funktion in der Liste der Funktionen, und klicken Sie dann auf der linken Seite auf die neu erstellte Funktion.</span><span class="sxs-lookup"><span data-stu-id="128af-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![neue Funktion öffnen](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="128af-236">Kopieren Sie den folgenden Code in die-Funktion.</span><span class="sxs-lookup"><span data-stu-id="128af-236">Copy the following code into your function.</span></span> <span data-ttu-id="128af-237">Diese Funktion gibt einfach eine zufällige Ganzzahl zwischen 0 und 2 zurück, wenn aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="128af-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="128af-238">Machen Sie sich keine Sorgen um den vorhandenen Code, und Sie können ihn über den Anfang einfügen.</span><span class="sxs-lookup"><span data-stu-id="128af-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="128af-239">Wählen Sie **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="128af-239">Select **Save**.</span></span>

14. <span data-ttu-id="128af-240">Das Ergebnis sollte wie in der folgenden Abbildung aussehen.</span><span class="sxs-lookup"><span data-stu-id="128af-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="128af-241">Klicken Sie auf **Get Function URL** , und notieren Sie sich den angezeigten *Endpunkt* .</span><span class="sxs-lookup"><span data-stu-id="128af-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="128af-242">Sie müssen Sie in die *azureservices* -Klasse einfügen, die Sie später in diesem Kurs erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="128af-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![Get-Funktions Endpunkt](images/AzureLabs-Lab5-16.png)

    ![Get-Funktions Endpunkt](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="128af-245">Kapitel 3: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="128af-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="128af-246">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="128af-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="128af-247">Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="128af-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="128af-248">Für diesen Kurs benötigen Sie **keine** Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="128af-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="128af-249">Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, [besuchen Sie den Artikel Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)-Einrichtung.</span><span class="sxs-lookup"><span data-stu-id="128af-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="128af-250">Öffnen Sie Unity, und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="128af-250">Open Unity and click **New**.</span></span>

    ![neues Unity-Projekt erstellen](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="128af-252">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="128af-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="128af-253">Fügen Sie **MR_Azure_Functions**ein.</span><span class="sxs-lookup"><span data-stu-id="128af-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="128af-254">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="128af-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="128af-255">Legen Sie den Speicherort auf einen geeigneten *Speicherort* fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="128af-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="128af-256">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="128af-256">Then, click **Create project**.</span></span>

    ![neues Unity-Projekt benennen](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="128af-258">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="128af-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="128af-259">Wechseln Sie zu Edit > **Preferences (Einstellungen** **Bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="128af-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="128af-260">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="128af-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="128af-261">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="128af-261">Close the **Preferences** window.</span></span>

    ![Festlegen von Visual Studio als Skript-Editor](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="128af-263">Navigieren Sie als nächstes zu **Datei** > **Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="128af-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Plattform zu UWP wechseln](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="128af-265">Wechseln Sie zu **Datei** > **Build-Einstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="128af-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="128af-266">Das **Zielgerät** ist auf **ein beliebiges Gerät**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="128af-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="128af-267">Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.</span><span class="sxs-lookup"><span data-stu-id="128af-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="128af-268">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="128af-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="128af-269">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="128af-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="128af-270">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="128af-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="128af-271">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="128af-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="128af-272">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="128af-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="128af-273">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="128af-274">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="128af-274">A save window will appear.</span></span>

            ![Hinzufügen offener Szenen](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="128af-276">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="128af-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Ordner "Create Szenen"](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="128af-278">Öffnen Sie den neu erstellten **Szenen** Ordner, geben Sie im Feld **Dateiname:** Text **functionsscene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="128af-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![Functions-Szene speichern](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="128af-280">Die restlichen Einstellungen in den **Buildeinstellungen**sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="128af-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![Functions-Szene speichern](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="128af-282">Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="128af-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![Player Einstellungen in Inspektor](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="128af-284">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="128af-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="128af-285">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="128af-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="128af-286">Die CLR- **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung), wodurch der Editor neu gestartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="128af-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="128af-287">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="128af-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="128af-288">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="128af-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="128af-289">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="128af-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="128af-290">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="128af-290">**InternetClient**</span></span>

            ![Festlegen von Funktionen](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="128af-292">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="128af-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![XR-Einstellungen festlegen](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="128af-294">Zurück in *Buildeinstellungen* : *Unity C# -Projekte* sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="128af-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![Tick-c#-Projekte](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="128af-296">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="128af-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="128af-297">Speichern Sie Ihre Szene und Ihr Projekt (**Datei** > **Speichern Sie Szenen/Dateien** > speichern Sie das **Projekt**).</span><span class="sxs-lookup"><span data-stu-id="128af-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="128af-298">Kapitel 4: Einrichten der Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="128af-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="128af-299">Wenn Sie die *Unity-Setup* Komponenten dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)und als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="128af-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="128af-300">Dies enthält auch die DLLs aus dem nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="128af-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="128af-301">Fahren Sie nach dem Import aus [Kapitel 7](#chapter-7---create-the-azureservices-class)fort.</span><span class="sxs-lookup"><span data-stu-id="128af-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="128af-302">Im *Hierarchie Panel*finden Sie ein Objekt mit dem Namen " **Main Camera**". dieses Objekt stellt den "Head"-Punkt dar, sobald Sie die Anwendung "in" haben.</span><span class="sxs-lookup"><span data-stu-id="128af-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="128af-303">Wählen Sie mit dem Unity-Dashboard vor Ihnen das **Hauptkamera-gameobject**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="128af-304">Sie werden feststellen, dass im *Inspektor-Panel* (in der Regel auf der rechten Seite im Dashboard) die verschiedenen Komponenten dieses *gameobject*angezeigt werden, mit der *Transformation* am oberen Rand, gefolgt von der *Kamera*und einigen anderen Komponenten.</span><span class="sxs-lookup"><span data-stu-id="128af-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="128af-305">Sie müssen die Transformation der Hauptkamera zurücksetzen, damit Sie ordnungsgemäß positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="128af-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="128af-306">Wählen Sie dazu das **Zahnrad** Symbol neben der *Transformations* Komponente der Kamera aus, und klicken Sie auf **Zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="128af-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Transformation zurücksetzen](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="128af-308">Aktualisieren Sie dann die **Transformations** Komponente so, dass Sie wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="128af-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="128af-309">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="128af-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="128af-310">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-310">**X**</span></span>   | <span data-ttu-id="128af-311">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-311">**Y**</span></span>                     | <span data-ttu-id="128af-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-312">**Z**</span></span> |
    | <span data-ttu-id="128af-313">0</span><span class="sxs-lookup"><span data-stu-id="128af-313">0</span></span>       | <span data-ttu-id="128af-314">1</span><span class="sxs-lookup"><span data-stu-id="128af-314">1</span></span>                         | <span data-ttu-id="128af-315">0</span><span class="sxs-lookup"><span data-stu-id="128af-315">0</span></span>     |    

    |       | <span data-ttu-id="128af-316">Transformation-Drehung</span><span class="sxs-lookup"><span data-stu-id="128af-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="128af-317">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-317">**X**</span></span> | <span data-ttu-id="128af-318">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-318">**Y**</span></span>                | <span data-ttu-id="128af-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-319">**Z**</span></span> |
    | <span data-ttu-id="128af-320">0</span><span class="sxs-lookup"><span data-stu-id="128af-320">0</span></span>     | <span data-ttu-id="128af-321">0</span><span class="sxs-lookup"><span data-stu-id="128af-321">0</span></span>                    | <span data-ttu-id="128af-322">0</span><span class="sxs-lookup"><span data-stu-id="128af-322">0</span></span>     |

    |       | <span data-ttu-id="128af-323">Transformieren: Skalieren</span><span class="sxs-lookup"><span data-stu-id="128af-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="128af-324">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-324">**X**</span></span> | <span data-ttu-id="128af-325">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-325">**Y**</span></span>             | <span data-ttu-id="128af-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-326">**Z**</span></span> |
    | <span data-ttu-id="128af-327">1</span><span class="sxs-lookup"><span data-stu-id="128af-327">1</span></span>     | <span data-ttu-id="128af-328">1</span><span class="sxs-lookup"><span data-stu-id="128af-328">1</span></span>                 | <span data-ttu-id="128af-329">1</span><span class="sxs-lookup"><span data-stu-id="128af-329">1</span></span>     |

    ![Kamera Transformation festlegen](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="128af-331">Kapitel 5: Einrichten der Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="128af-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="128af-332">Klicken Sie mit der rechten Maustaste in einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **3D-Objekt**eine **Ebene**hinzu.</span><span class="sxs-lookup"><span data-stu-id="128af-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![neue Ebene erstellen](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="128af-334">Ändern Sie bei ausgewähltem **Plane** -Objekt im Inspektor- *Panel*die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="128af-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="128af-335">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="128af-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="128af-336">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-336">**X**</span></span> | <span data-ttu-id="128af-337">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-337">**Y**</span></span>                | <span data-ttu-id="128af-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-338">**Z**</span></span> |
    | <span data-ttu-id="128af-339">0</span><span class="sxs-lookup"><span data-stu-id="128af-339">0</span></span>     | <span data-ttu-id="128af-340">0</span><span class="sxs-lookup"><span data-stu-id="128af-340">0</span></span>                    | <span data-ttu-id="128af-341">4</span><span class="sxs-lookup"><span data-stu-id="128af-341">4</span></span>     |

    |       | <span data-ttu-id="128af-342">Transformieren: Skalieren</span><span class="sxs-lookup"><span data-stu-id="128af-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="128af-343">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-343">**X**</span></span> | <span data-ttu-id="128af-344">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-344">**Y**</span></span>             | <span data-ttu-id="128af-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-345">**Z**</span></span> |
    | <span data-ttu-id="128af-346">10</span><span class="sxs-lookup"><span data-stu-id="128af-346">10</span></span>    | <span data-ttu-id="128af-347">1</span><span class="sxs-lookup"><span data-stu-id="128af-347">1</span></span>                 | <span data-ttu-id="128af-348">10</span><span class="sxs-lookup"><span data-stu-id="128af-348">10</span></span>    |

    ![Festlegen der Position und Skala der Ebene](images/AzureLabs-Lab5-32.png)

    ![Szenen Ansicht der Ebene](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="128af-351">Klicken Sie mit der rechten Maustaste in einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **3D-Objekt**einen **Cube**hinzu.</span><span class="sxs-lookup"><span data-stu-id="128af-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="128af-352">Benennen Sie den Cube in " **gazebutton** " um (während der Cube ausgewählt ist, drücken Sie "F2").</span><span class="sxs-lookup"><span data-stu-id="128af-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="128af-353">Ändern Sie im *Inspektor-Panel*die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="128af-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="128af-354">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="128af-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="128af-355">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-355">**X**</span></span> | <span data-ttu-id="128af-356">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-356">**Y**</span></span>                | <span data-ttu-id="128af-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-357">**Z**</span></span> |
        | <span data-ttu-id="128af-358">0</span><span class="sxs-lookup"><span data-stu-id="128af-358">0</span></span>     | <span data-ttu-id="128af-359">3</span><span class="sxs-lookup"><span data-stu-id="128af-359">3</span></span>                    | <span data-ttu-id="128af-360">5</span><span class="sxs-lookup"><span data-stu-id="128af-360">5</span></span>     |


        ![Schaltflächen Transformation für den Blick festlegen](images/AzureLabs-Lab5-34.png)

        ![Ansicht "Ansicht" der Ansicht](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="128af-363">Klicken Sie auf die Dropdown Schaltfläche **Tag** , und klicken Sie auf **Tag hinzufügen** , um den Bereich *Tags & Ebenen*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="128af-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![neues Tag hinzufügen](images/AzureLabs-Lab5-36.png)

        ![Plus auswählen](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="128af-366">Wählen Sie die Schaltfläche **+ (plus)** aus, und geben Sie im Feld *neuer Tagname den Namen* " **gazebutton**" ein, und klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="128af-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![neuer Tag benennen](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="128af-368">Klicken Sie im *Hierarchie Panel*auf das Objekt " **gazebutton** ", und weisen Sie im *Inspektor-Panel*das neu erstellte " **gazebutton** "-Tag zu.</span><span class="sxs-lookup"><span data-stu-id="128af-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![Schaltfläche "Blick" für den neuen Tag zuweisen](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="128af-370">Klicken Sie mit der rechten Maustaste auf das **gazebutton** -Objekt im Bereich *Hierarchie*, und fügen Sie ein **leeres gameobject-Objekt** hinzu (das als unter *geordnetes Objekt hinzu* gefügt wird).</span><span class="sxs-lookup"><span data-stu-id="128af-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="128af-371">Wählen Sie das neue Objekt aus, und benennen Sie es **shapespawnpoint**um.</span><span class="sxs-lookup"><span data-stu-id="128af-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="128af-372">Ändern Sie im *Inspektor-Panel*die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="128af-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="128af-373">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="128af-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="128af-374">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-374">**X**</span></span> |<span data-ttu-id="128af-375">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-375">**Y**</span></span>                 | <span data-ttu-id="128af-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-376">**Z**</span></span> |
        | <span data-ttu-id="128af-377">0</span><span class="sxs-lookup"><span data-stu-id="128af-377">0</span></span>     | <span data-ttu-id="128af-378">-1</span><span class="sxs-lookup"><span data-stu-id="128af-378">-1</span></span>                   | <span data-ttu-id="128af-379">0</span><span class="sxs-lookup"><span data-stu-id="128af-379">0</span></span>     |

        ![Transformation für Erstellungspunkt aktualisieren](images/AzureLabs-Lab5-40.png)

        ![Szenen Ansicht des Shape-Spawn-Punkts](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="128af-382">Als Nächstes erstellen Sie ein **3D-Text** Objekt, um Feedback zum Status des Azure-Dienstanbieter zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="128af-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="128af-383">Klicken Sie erneut mit der rechten Maustaste auf die **Schaltfläche** , und fügen Sie ein **3D-Objekt** > **3D-Text** Objekt als untergeordnetes Element *hinzu.*</span><span class="sxs-lookup"><span data-stu-id="128af-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![Erstellen eines neuen 3D-Text Objekts](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="128af-385">Benennen Sie das **3D-Text** Objekt in **azurestatustext**um.</span><span class="sxs-lookup"><span data-stu-id="128af-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="128af-386">Ändern Sie die **azurestatustext** -Objekt Transformation wie folgt:</span><span class="sxs-lookup"><span data-stu-id="128af-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="128af-387">Transformation-Position</span><span class="sxs-lookup"><span data-stu-id="128af-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="128af-388">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-388">**X**</span></span> | <span data-ttu-id="128af-389">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-389">**Y**</span></span>                | <span data-ttu-id="128af-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-390">**Z**</span></span> |
    | <span data-ttu-id="128af-391">0</span><span class="sxs-lookup"><span data-stu-id="128af-391">0</span></span>     | <span data-ttu-id="128af-392">0</span><span class="sxs-lookup"><span data-stu-id="128af-392">0</span></span>                    | <span data-ttu-id="128af-393">-0,6</span><span class="sxs-lookup"><span data-stu-id="128af-393">-0.6</span></span>  |

    |       | <span data-ttu-id="128af-394">Transformieren: Skalieren</span><span class="sxs-lookup"><span data-stu-id="128af-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="128af-395">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="128af-395">**X**</span></span> | <span data-ttu-id="128af-396">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="128af-396">**Y**</span></span>             | <span data-ttu-id="128af-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="128af-397">**Z**</span></span> |
    | <span data-ttu-id="128af-398">0,1</span><span class="sxs-lookup"><span data-stu-id="128af-398">0.1</span></span>   | <span data-ttu-id="128af-399">0,1</span><span class="sxs-lookup"><span data-stu-id="128af-399">0.1</span></span>               | <span data-ttu-id="128af-400">0,1</span><span class="sxs-lookup"><span data-stu-id="128af-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="128af-401">Machen Sie sich keine Sorgen, wenn Sie außerhalb der Mitte angezeigt werden, da dies korrigiert wird, wenn die folgende textmesh-Komponente aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="128af-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="128af-402">Ändern Sie die **textmesh** -Komponente entsprechend der folgenden:</span><span class="sxs-lookup"><span data-stu-id="128af-402">Change the **Text Mesh** component to match the below:</span></span>

    ![textmesh-Komponente festlegen](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="128af-404">Die hier ausgewählte Farbe ist hexadezimal Farbe: **000000FF**, aber Sie können selbst eine eigene Farbe auswählen, um sicherzustellen, dass Sie lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="128af-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="128af-405">Ihre Hierarchie Panel-Struktur sollte nun wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="128af-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![textmesh in der Szene Ansicht](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="128af-407">Ihre Szene sollte nun wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="128af-407">Your scene should now look like this:</span></span>

    ![textmesh in der Szene Ansicht](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="128af-409">Kapitel 6: Importieren von Azure Storage für Unity</span><span class="sxs-lookup"><span data-stu-id="128af-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="128af-410">Sie verwenden Azure Storage für Unity (das wiederum das .NET SDK für Azure nutzt).</span><span class="sxs-lookup"><span data-stu-id="128af-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="128af-411">Weitere Informationen hierzu finden Sie im [Artikel Azure Storage für Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="128af-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="128af-412">Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="128af-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="128af-413">Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="128af-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="128af-414">Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [". unitypackage" aus GitHub](https://aka.ms/azstorage-unitysdk)heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="128af-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="128af-415">Gehen Sie dann wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="128af-415">Then, do the following:</span></span>

1.  <span data-ttu-id="128af-416">Fügen Sie Unity die **. unitypackage** -Datei mithilfe der Menüoption **Assets** >  > **benutzerdefiniertes Paket** **importieren** hinzu.</span><span class="sxs-lookup"><span data-stu-id="128af-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="128af-417">Im Feld " **Unity-Paket importieren** ", das angezeigt wird, können Sie unter **Plug** -in > **Speicher**alles auswählen.</span><span class="sxs-lookup"><span data-stu-id="128af-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="128af-418">Deaktivieren Sie alles andere, da es für diesen Kurs nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="128af-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![in Paket importieren](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="128af-420">Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="128af-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="128af-421">Wechseln Sie in der Projektansicht *unter Plug*-in zum Ordner *Speicher* , und wählen Sie *nur*die folgenden Plug-ins aus:</span><span class="sxs-lookup"><span data-stu-id="128af-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="128af-422">Microsoft. Data. Edm</span><span class="sxs-lookup"><span data-stu-id="128af-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="128af-423">Microsoft. Data. odata</span><span class="sxs-lookup"><span data-stu-id="128af-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="128af-424">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="128af-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="128af-425">"Newtonsoft. JSON"</span><span class="sxs-lookup"><span data-stu-id="128af-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="128af-426">System. Spatial</span><span class="sxs-lookup"><span data-stu-id="128af-426">System.Spatial</span></span>

        ![alle Plattformen deaktivieren](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="128af-428">Wenn *Sie diese speziellen* Plug-Ins **ausgewählt haben, deaktivieren Sie** *eine beliebige Plattform* **, deaktivieren Sie** *wsaplayer* , und klicken Sie auf **anwenden**.</span><span class="sxs-lookup"><span data-stu-id="128af-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![Platt Form-DLLs anwenden](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="128af-430">Wir markieren diese bestimmten Plug-ins, sodass Sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="128af-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="128af-431">Dies liegt daran, dass im WSA-Ordner verschiedene Versionen der gleichen Plug-ins vorhanden sind, die nach dem Exportieren des Projekts aus Unity verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="128af-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="128af-432">Wählen Sie im Ordner *Storage* -Plug-in nur die Option:</span><span class="sxs-lookup"><span data-stu-id="128af-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="128af-433">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="128af-433">Microsoft.Data.Services.Client</span></span>

        !["nicht verarbeiten" für DLLs festlegen](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="128af-435">Aktivieren Sie das Kontrollkästchen **nicht verarbeiten** unter *Platt Form Einstellungen* , und klicken Sie auf **anwenden**.</span><span class="sxs-lookup"><span data-stu-id="128af-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="128af-437">Wir markieren dieses Plug-in "nicht verarbeiten", da das Unity-assemblypatcher Probleme beim Verarbeiten dieses Plug-ins hat.</span><span class="sxs-lookup"><span data-stu-id="128af-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="128af-438">Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="128af-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="128af-439">Kapitel 7: Erstellen der azureservices-Klasse</span><span class="sxs-lookup"><span data-stu-id="128af-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="128af-440">Die erste Klasse, die Sie erstellen, ist die *azureservices* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="128af-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="128af-441">Die *azureservices* -Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="128af-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="128af-442">Azure-Konto Anmelde Informationen werden gespeichert.</span><span class="sxs-lookup"><span data-stu-id="128af-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="128af-443">Der Azure-App-Funktion wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="128af-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="128af-444">Hochladen und Herunterladen der Datendatei in Ihrem Azure-cloudspeicher.</span><span class="sxs-lookup"><span data-stu-id="128af-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="128af-445">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="128af-445">To create this Class:</span></span>

1.  <span data-ttu-id="128af-446">Klicken Sie im Projekt Panel mit der rechten Maustaste in den Ordner *Asset* , und **Erstellen** Sie > **Ordner**.</span><span class="sxs-lookup"><span data-stu-id="128af-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="128af-447">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="128af-447">Name the folder **Scripts**.</span></span>

    ![neuen Ordner erstellen](images/AzureLabs-Lab5-50.png)

    ![callordnerskripts](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="128af-450">Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="128af-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="128af-451">Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen** Sie >  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="128af-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="128af-452">Nennen Sie das Skript *azureservices*.</span><span class="sxs-lookup"><span data-stu-id="128af-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="128af-453">Doppelklicken Sie auf die neue Klasse *azureservices* , um Sie in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="128af-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="128af-454">Fügen Sie am Anfang der *azureservices*die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="128af-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="128af-455">Fügen Sie die folgenden Inspektor-Felder in der *azureservices* -Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="128af-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="128af-456">Fügen Sie dann die folgenden Element Variablen in der *azureservices* -Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="128af-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="128af-457">Stellen Sie sicher, dass Sie die Werte für *Endpunkt* und *Verbindungs Zeichenfolge* durch die Werte aus Ihrem Azure-Speicher im Azure-Portal ersetzen.</span><span class="sxs-lookup"><span data-stu-id="128af-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="128af-458">Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="128af-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="128af-459">Diese Methoden werden aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="128af-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="128af-460">In einem [zukünftigen Kapitel](#chapter-10---completing-the-azureservices-class)wird der Code für *callazurefunctionfornextshape ()* ausgefüllt.</span><span class="sxs-lookup"><span data-stu-id="128af-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="128af-461">Löschen Sie die *Update ()* -Methode, da Sie von dieser Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="128af-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="128af-462">Speichern Sie die Änderungen in Visual Studio, und kehren Sie dann zu Unity zurück.</span><span class="sxs-lookup"><span data-stu-id="128af-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="128af-463">Klicken und ziehen Sie die Klasse *azureservices* aus dem Ordner Scripts auf das Hauptkamera Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="128af-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="128af-464">Wählen Sie die Hauptkamera aus, und rufen Sie dann das untergeordnete **azurestatustext** -Objekt unter dem **gazebutton** -Objekt ab, und platzieren Sie es innerhalb des Felds **azurestatustext** -Verweis Ziel im *Inspektor*, um den Verweis auf das  *Azureservices* -Skript.</span><span class="sxs-lookup"><span data-stu-id="128af-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![Azure-Status-Text Verweis Ziel zuweisen](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="128af-466">Kapitel 8: Erstellen der shapefactory-Klasse</span><span class="sxs-lookup"><span data-stu-id="128af-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="128af-467">Das nächste Skript, das erstellt werden soll, ist die *shapefactory* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="128af-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="128af-468">Die Rolle dieser Klasse besteht darin, eine neue Form zu erstellen, wenn Sie angefordert wird, und einen Verlauf der Formen beizubehalten, die in einer Shape-Verlaufs *Liste*erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="128af-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="128af-469">Jedes Mal, wenn eine Form erstellt wird, wird die Shape-Verlaufs *Liste* in der *azureservice* -Klasse aktualisiert und dann in Ihrem *Azure Storage*gespeichert.</span><span class="sxs-lookup"><span data-stu-id="128af-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="128af-470">Wenn die Anwendung gestartet wird und eine gespeicherte Datei in der *Azure Storage*gefunden wird, wird die *Shape* -Verlaufs Liste abgerufen und wiedergegeben, wobei das **3D-Text** Objekt bereitstellt, ob die generierte Form aus Storage oder New ist.</span><span class="sxs-lookup"><span data-stu-id="128af-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="128af-471">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="128af-471">To create this class:</span></span>

1.  <span data-ttu-id="128af-472">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="128af-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="128af-473">Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen** Sie >  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="128af-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="128af-474">Nennen Sie das Skript *shapefactory*.</span><span class="sxs-lookup"><span data-stu-id="128af-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="128af-475">Doppelklicken Sie auf das neue *shapefactory* -Skript, um es in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="128af-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="128af-476">Stellen Sie sicher, dass die *shapefactory* -Klasse die folgenden Namespaces umfasst:</span><span class="sxs-lookup"><span data-stu-id="128af-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="128af-477">Fügen Sie die unten gezeigten Variablen der *shapefactory* -Klasse hinzu, und ersetzen Sie die Funktionen " *Start ()* " und " *Awa()* " durch die folgenden:</span><span class="sxs-lookup"><span data-stu-id="128af-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="128af-478">Die Methode " *kreateshape ()* " generiert die primitiven Formen basierend auf dem bereitgestellten *ganzzahligen* Parameter.</span><span class="sxs-lookup"><span data-stu-id="128af-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="128af-479">Der boolesche Parameter wird verwendet, um anzugeben, ob die derzeit erstellte Form aus Storage oder New ist.</span><span class="sxs-lookup"><span data-stu-id="128af-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="128af-480">Platzieren Sie den folgenden Code in der *shapefactory* -Klasse unter den vorherigen Methoden:</span><span class="sxs-lookup"><span data-stu-id="128af-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="128af-481">Stellen Sie sicher, dass Sie die Änderungen in Visual Studio speichern, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="128af-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="128af-482">Klicken Sie im Unity-Editor auf die *shapefactory* -Klasse, und ziehen Sie Sie aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im *Hierarchie Panel*.</span><span class="sxs-lookup"><span data-stu-id="128af-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="128af-483">Wenn die Hauptkamera ausgewählt ist, sehen Sie, dass in der *shapefactory* -Skript Komponente der Verweis *Punkt* Verweis fehlt.</span><span class="sxs-lookup"><span data-stu-id="128af-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="128af-484">Um dieses Problem zu beheben, ziehen Sie das **shapespawnpoint** -Objekt aus dem Bereich *Hierarchie* in das Referenz Ziel des- **pullpunkts** .</span><span class="sxs-lookup"><span data-stu-id="128af-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![Shape-Factory-Verweis Ziel festlegen](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="128af-486">Kapitel 9: Erstellen der "Blick"-Klasse</span><span class="sxs-lookup"><span data-stu-id="128af-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="128af-487">Das letzte Skript, das Sie erstellen müssen, ist die " *Gaze* "-Klasse.</span><span class="sxs-lookup"><span data-stu-id="128af-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="128af-488">Diese Klasse ist für das Erstellen eines **raycast** verantwortlich, der von der Hauptkamera projiziert wird, um zu erkennen, welches Objekt der Benutzer untersucht.</span><span class="sxs-lookup"><span data-stu-id="128af-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="128af-489">In diesem Fall muss der raycast ermitteln, ob der Benutzer das **gazebutton** -Objekt in der Szene prüft und ein Verhalten auslöst.</span><span class="sxs-lookup"><span data-stu-id="128af-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="128af-490">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="128af-490">To create this Class:</span></span>

1.  <span data-ttu-id="128af-491">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="128af-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="128af-492">Klicken Sie im Projekt Panel mit der rechten Maustaste, und **Erstellen** Sie >  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="128af-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="128af-493">Ruft den Skript *Blick*auf.</span><span class="sxs-lookup"><span data-stu-id="128af-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="128af-494">Doppelklicken Sie auf das neue *Blick* Skript, um es in *Visual Studio* zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="128af-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="128af-495">Stellen Sie sicher, dass der folgende Namespace am Anfang des Skripts enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="128af-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="128af-496">Fügen Sie dann die folgenden Variablen in der " *Blick* "-Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="128af-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="128af-497">Einige dieser Variablen können im *Editor*bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="128af-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="128af-498">Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="128af-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="128af-499">Fügen Sie den folgenden Code hinzu, mit dem ein Cursor Objekt beim Start zusammen mit der *Update ()* -Methode erstellt wird, die die raycast-Methode ausgeführt wird, sowie den Speicherort für den booleschen Wert für die instanzaktivierung:</span><span class="sxs-lookup"><span data-stu-id="128af-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="128af-500">Fügen Sie als nächstes die *updateraycast ()* -Methode hinzu, die ein raycast-Projekt erstellt und das Treffer Ziel erkennt.</span><span class="sxs-lookup"><span data-stu-id="128af-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="128af-501">Fügen Sie abschließend die *resetfocusedobject ()* -Methode hinzu, die die aktuelle Farbe der gazebutton-Objekte umschalten und angibt, ob eine neue Form erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="128af-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="128af-502">Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="128af-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="128af-503">Klicken und ziehen Sie die Klasse " *Blick* " aus dem Ordner Scripts auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="128af-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="128af-504">Kapitel 10: vervollständigen der azureservices-Klasse</span><span class="sxs-lookup"><span data-stu-id="128af-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="128af-505">Wenn die anderen Skripts vorhanden sind, ist es jetzt möglich, die *azureservices* -Klasse *abzuschließen* .</span><span class="sxs-lookup"><span data-stu-id="128af-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="128af-506">Dies wird durch Folgendes erreicht:</span><span class="sxs-lookup"><span data-stu-id="128af-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="128af-507">Fügen Sie eine neue Methode mit dem Namen " *foratecloudidentityasync ()* " hinzu, um die Authentifizierungs Variablen einzurichten, die für die Kommunikation mit Azure erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="128af-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="128af-508">Mit dieser Methode wird auch überprüft, ob eine zuvor gespeicherte Datei mit der Form Liste vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="128af-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="128af-509">**Wenn die Datei gefunden**wird, deaktiviert Sie den Benutzer *Blick*und löst die Form Erstellung gemäß dem Muster der Formen aus, wie Sie in der Azure Storage- **Datei**gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="128af-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="128af-510">Der Benutzer kann dies sehen, da im **textmesh** abhängig vom Ursprung der Formen "Storage" oder "New" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="128af-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="128af-511">**Wenn keine Datei gefunden**wird, wird der *Blick*aktiviert, sodass der Benutzer bei der Betrachtung des **gazebutton** -Objekts in der Szene Formen erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="128af-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="128af-512">Der nächste Code Ausschnitt erfolgt innerhalb der Methode " *Start ()* ". Dabei wird ein-Rückruf an die Methode "Methode" von "| *atecloudidentityasync ()* " durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="128af-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="128af-513">Sie können Ihre aktuelle *Start ()* -Methode mit den folgenden Informationen kopieren:</span><span class="sxs-lookup"><span data-stu-id="128af-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="128af-514">Geben Sie den Code für die Methode *callazurefunctionfornextshape ()* ein.</span><span class="sxs-lookup"><span data-stu-id="128af-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="128af-515">Sie verwenden den zuvor erstellten *Azure-Funktionen-App* , um einen Form Index anzufordern.</span><span class="sxs-lookup"><span data-stu-id="128af-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="128af-516">Nachdem die neue Form empfangen wurde, sendet diese Methode die Form an die *shapefactory* -Klasse, um die neue Form in der Szene zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="128af-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="128af-517">Verwenden Sie den folgenden Code, um den Text von *callazurefunctionfornextshape ()* abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="128af-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="128af-518">Fügen Sie eine Methode hinzu, um eine Zeichenfolge zu erstellen, indem Sie die in der Form Verlaufs Liste gespeicherten Ganzzahlen verketten und in Ihrer *Azure Storage Datei*speichern.</span><span class="sxs-lookup"><span data-stu-id="128af-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="128af-519">Fügen Sie eine Methode hinzu, um den in der Datei gespeicherten Text in der *Azure Storage-Datei* abzurufen und in eine Liste zu *Deserialisieren* .</span><span class="sxs-lookup"><span data-stu-id="128af-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="128af-520">Sobald dieser Vorgang abgeschlossen ist, aktiviert die Methode den Blick erneut, sodass der Benutzer der Szene weitere Formen hinzufügen kann.</span><span class="sxs-lookup"><span data-stu-id="128af-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="128af-521">Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="128af-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="128af-522">Kapitel 11: Erstellen der UWP-Lösung</span><span class="sxs-lookup"><span data-stu-id="128af-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="128af-523">So beginnen Sie den Buildprozess:</span><span class="sxs-lookup"><span data-stu-id="128af-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="128af-524">Wechseln Sie zu **Datei** > **Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="128af-524">Go to **File** > **Build Settings**.</span></span>

    ![Erstellen der APP](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="128af-526">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="128af-526">Click **Build**.</span></span> <span data-ttu-id="128af-527">Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="128af-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="128af-528">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " *App*".</span><span class="sxs-lookup"><span data-stu-id="128af-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="128af-529">Klicken Sie dann mit ausgewähltem *App* -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="128af-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="128af-530">Unity startet das Projekt in den *App* -Ordner.</span><span class="sxs-lookup"><span data-stu-id="128af-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="128af-531">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein *Datei-Explorer* -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="128af-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="128af-532">Kapitel 12: Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="128af-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="128af-533">So stellen Sie die Anwendung bereit:</span><span class="sxs-lookup"><span data-stu-id="128af-533">To deploy your application:</span></span>

1.  <span data-ttu-id="128af-534">Navigieren Sie zum *App* -Ordner, der im [letzten Kapitel](#chapter-11---build-the-uwp-solution)erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="128af-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="128af-535">Es wird eine Datei mit dem Namen Ihrer Apps mit der Erweiterung ". sln" angezeigt, auf die Sie doppelklicken, um Sie in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="128af-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="128af-536">Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="128af-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="128af-537">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="128af-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="128af-538">Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen.</span><span class="sxs-lookup"><span data-stu-id="128af-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="128af-539">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="128af-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="128af-540">Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den **Einstellungen** > **Netzwerk & Internet** > **Wi-Fi-**  > **Erweiterte Optionen**; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="128af-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="128af-541">Stellen Sie sicher, dass der **Entwicklermodus** **auf**dem in den **Einstellungen** > **Update & Sicherheits** > **für Entwickler**gefunden.</span><span class="sxs-lookup"><span data-stu-id="128af-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![Lösung bereitstellen](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="128af-543">Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="128af-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="128af-544">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet und getestet werden können.</span><span class="sxs-lookup"><span data-stu-id="128af-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="128af-545">Ihre fertiggestellte Azure Functions-und Speicher Anwendung</span><span class="sxs-lookup"><span data-stu-id="128af-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="128af-546">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die sowohl die Azure Functions als auch die Azure Storage Dienste nutzt.</span><span class="sxs-lookup"><span data-stu-id="128af-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="128af-547">Ihre APP kann auf gespeicherten Daten zeichnen und eine auf diesen Daten basierende Aktion bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="128af-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![Endprodukt-Ende](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="128af-549">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="128af-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="128af-550">Übung 1</span><span class="sxs-lookup"><span data-stu-id="128af-550">Exercise 1</span></span>

<span data-ttu-id="128af-551">Erstellen Sie einen zweiten Erstellungs Punkt, und notieren Sie den-Punkt, aus dem ein Objekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="128af-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="128af-552">Wenn Sie die Datendatei laden, stellen Sie die Formen wieder her, die aus dem Speicherort der ursprünglichen Erstellung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="128af-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="128af-553">Übung 2</span><span class="sxs-lookup"><span data-stu-id="128af-553">Exercise 2</span></span>

<span data-ttu-id="128af-554">Erstellen Sie eine Möglichkeit, die APP neu zu starten, anstatt Sie jedes Mal erneut öffnen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="128af-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="128af-555">Das **Laden von Szenen** ist ein guter Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="128af-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="128af-556">Erstellen Sie anschließend eine Möglichkeit, die gespeicherte Liste in *Azure Storage*zu löschen, damit Sie problemlos von der APP zurückgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="128af-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
