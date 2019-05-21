---
title: MR und Azure-305 - Funktionen und Speicher
description: Führen Sie diesen Kurs, um zu erfahren, wie Sie Azure Storage und-Funktionen innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Funktionen, Speicher, Hololens, immersive Vr
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593545"
---
>[!NOTE]
><span data-ttu-id="5d57b-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="5d57b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5d57b-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5d57b-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5d57b-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5d57b-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="5d57b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5d57b-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="5d57b-110">MR und Azure-305: Funktionen und Speicher</span><span class="sxs-lookup"><span data-stu-id="5d57b-110">MR and Azure 305: Functions and storage</span></span>

![Endprodukt-starten](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="5d57b-112">In diesem Kurs erfahren Sie, wie zum Erstellen und Verwenden von Azure Functions aus, und speichern Sie Daten mit einem Azure Storage-Ressource in einer mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="5d57b-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="5d57b-113">*Azure Functions* ist ein Microsoft-Dienst, die Entwickler kleine Teile des Codes ausgeführt werden kann, "Funktionen", in Azure.</span><span class="sxs-lookup"><span data-stu-id="5d57b-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="5d57b-114">Dadurch wird eine Möglichkeit zum Delegieren der Arbeit an Ihrer lokalen Anwendung, die viele Vorteile haben kann, anstatt die Cloud.</span><span class="sxs-lookup"><span data-stu-id="5d57b-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="5d57b-115">*Azure Functions* unterstützt verschiedene Entwicklungssprachen, darunter C\#, F\#, Node.js, Java und PHP.</span><span class="sxs-lookup"><span data-stu-id="5d57b-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="5d57b-116">Weitere Informationen finden Sie auf die [Azure Functions-Artikel](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="5d57b-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="5d57b-117">*Azure-Speicher* ist ein Microsoft-Cloud-Dienst, der ermöglicht es Entwicklern, die zum Speichern von Daten mit der Versicherung, dass es hoch verfügbar, sichere, permanenten, skalierbar und redundant ist.</span><span class="sxs-lookup"><span data-stu-id="5d57b-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="5d57b-118">Dies bedeutet, dass Microsoft alle Wartung und kritische Probleme für Sie übernimmt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="5d57b-119">Weitere Informationen finden Sie auf die [Azure Storage-Artikel](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="5d57b-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="5d57b-120">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung die können die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="5d57b-121">Ermöglicht dem Benutzer, die in einer Szene bestaunen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="5d57b-122">Das Erzeugen von Objekten, wenn der Benutzer auf ein 3D-Diagrammlayout "Button" gazes ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="5d57b-123">Die erzeugten Objekte werden durch eine Azure-Funktion ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="5d57b-124">Da jedes Objekt erzeugt wird, speichert die Anwendung den Objekttyp in einem *Azure File*befindet sich im *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="5d57b-125">Beim Laden eines zweiten Mal die *Azure File* Daten abgerufen, und zur Wiedergabe erzeugenden Aktionen auf der vorherigen Instanz der Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="5d57b-126">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="5d57b-127">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="5d57b-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="5d57b-128">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="5d57b-129">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5d57b-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5d57b-130">Kurs</span><span class="sxs-lookup"><span data-stu-id="5d57b-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5d57b-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5d57b-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5d57b-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="5d57b-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5d57b-133">MR und Azure-305: Funktionen und Speicher</span><span class="sxs-lookup"><span data-stu-id="5d57b-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="5d57b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="5d57b-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5d57b-135">✔️</span><span class="sxs-lookup"><span data-stu-id="5d57b-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="5d57b-136">Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="5d57b-137">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d57b-138">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5d57b-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5d57b-139">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="5d57b-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5d57b-140">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="5d57b-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="5d57b-141">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="5d57b-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="5d57b-142">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="5d57b-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5d57b-143">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="5d57b-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="5d57b-144">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="5d57b-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5d57b-145">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="5d57b-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5d57b-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="5d57b-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5d57b-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5d57b-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="5d57b-148">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="5d57b-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="5d57b-149">Ein Abonnement für ein Azure-Konto zum Erstellen von Azure-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="5d57b-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="5d57b-150">Zugriff auf das Internet für den Abruf von Setup- und Azure</span><span class="sxs-lookup"><span data-stu-id="5d57b-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5d57b-151">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="5d57b-151">Before you start</span></span>

<span data-ttu-id="5d57b-152">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="5d57b-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="5d57b-153">Kapitel 1: das Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="5d57b-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="5d57b-154">Verwenden der **Azure Storage-Dienst**, Sie benötigen zum Erstellen und Konfigurieren einer **Speicherkonto** im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="5d57b-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="5d57b-155">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="5d57b-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5d57b-156">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5d57b-157">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="5d57b-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="5d57b-158">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Speicherkonto*, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![Azure-Speicher-Suche](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="5d57b-160">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="5d57b-161">Die neue Seite bietet eine Beschreibung der *Azure Storage-Konto* Service.</span><span class="sxs-lookup"><span data-stu-id="5d57b-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="5d57b-162">Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Dienst erstellen](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="5d57b-164">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="5d57b-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="5d57b-165">Fügen Sie eine *Namen* für Ihr Konto bedenken, dass dieses Feld akzeptiert nur Ziffern und Kleinbuchstaben zulässig.</span><span class="sxs-lookup"><span data-stu-id="5d57b-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="5d57b-166">Für *Bereitstellungsmodell*Option **RM**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="5d57b-167">Für *Kontoart*Option **Speicher (Allgemein v1)**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="5d57b-168">Bestimmen der *Speicherort* für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="5d57b-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5d57b-169">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5d57b-170">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5d57b-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="5d57b-171">Für *Replikation* wählen **Read-Access-georedundanter Speicher (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="5d57b-172">Für *Leistung*Option **Standard**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="5d57b-173">Lassen Sie *sichere Übertragung erforderlich* als **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="5d57b-174">Wählen Sie eine *Abonnement*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="5d57b-175">Wählen Sie eine *Ressourcengruppe* oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="5d57b-176">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5d57b-177">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="5d57b-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="5d57b-178">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="5d57b-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="5d57b-179">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="5d57b-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="5d57b-180">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="5d57b-180">Select **Create**.</span></span>

        ![Eingabe Dienstinformationen](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="5d57b-182">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="5d57b-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="5d57b-183">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Neue Benachrichtigung im Azure-portal](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="5d57b-185">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-185">Click on the notifications to explore your new Service instance.</span></span>

    ![zu Ressource wechseln](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="5d57b-187">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="5d57b-188">Sie gelangen in die neue *Speicherkonto* Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="5d57b-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![Zugriffstasten](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="5d57b-190">Klicken Sie auf *Zugriffsschlüssel*, um die Endpunkte für diesen Cloud-Dienst anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="5d57b-191">Verwenden Sie *Editor* oder eine ähnliche Kopie einen Ihrer Schlüssel zur späteren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="5d57b-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="5d57b-192">Beachten Sie außerdem die *Verbindungszeichenfolge* -Wert fest, wie er in verwendet werden, wird die *AzureServices* -Klasse, die Sie später erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Verbindungszeichenfolge kopieren](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="5d57b-194">Kapitel 2: Einrichten einer Azure-Funktion</span><span class="sxs-lookup"><span data-stu-id="5d57b-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="5d57b-195">Schreiben Sie jetzt eine **Azure** **Funktion** im Azure-Dienst.</span><span class="sxs-lookup"><span data-stu-id="5d57b-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="5d57b-196">Sie können eine **Azure-Funktion** nahezu alles tun, die Sie mit einer klassischen-Funktion in Ihrem Code, den Unterschied ausführen würden, dass diese Funktion von jeder Anwendung zugegriffen werden kann, die Anmeldeinformationen zum Zugriff auf Ihr Azure-Konto verfügt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="5d57b-197">So erstellen Sie eine Azure-Funktion</span><span class="sxs-lookup"><span data-stu-id="5d57b-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="5d57b-198">Aus Ihrem *Azure-Portal*, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Funktions-App*, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Erstellen von Funktionen-app](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="5d57b-200">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="5d57b-201">Die neue Seite bietet eine Beschreibung der *Azure Function-App* Service.</span><span class="sxs-lookup"><span data-stu-id="5d57b-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="5d57b-202">Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Funktion-app-info](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="5d57b-204">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="5d57b-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="5d57b-205">Geben Sie eine *Anwendungsnamen*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-205">Provide an *App name*.</span></span> <span data-ttu-id="5d57b-206">Nur Buchstaben und Zahlen können hier verwendet werden (entweder Groß-/Kleinschreibung ist zulässig).</span><span class="sxs-lookup"><span data-stu-id="5d57b-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="5d57b-207">Wählen Sie die bevorzugte *Abonnement*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="5d57b-208">Wählen Sie eine *Ressourcengruppe* oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="5d57b-209">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5d57b-210">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="5d57b-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="5d57b-211">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="5d57b-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="5d57b-212">Wählen Sie für diese Übung *Windows* als das ausgewählte **OS**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="5d57b-213">Wählen Sie *Verbrauchsplan* für die **Hostingplan**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="5d57b-214">Bestimmen der *Speicherort* für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="5d57b-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5d57b-215">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5d57b-216">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5d57b-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="5d57b-217">Wählen Sie für eine optimale Leistung der gleichen Region wie das Speicherkonto aus.</span><span class="sxs-lookup"><span data-stu-id="5d57b-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="5d57b-218">Für *Storage*Option **vorhandene**, und klicken Sie dann mit dem Dropdown-Menü, Ihre zuvor erstellten speicherkontonamen finden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="5d57b-219">Lassen Sie *Application Insights* für diese Übung deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="5d57b-219">Leave *Application Insights* off for this exercise.</span></span>

        ![Eingabefunktion app-details](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="5d57b-221">Klicken Sie auf die Schaltfläche **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="5d57b-222">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="5d57b-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="5d57b-223">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![neue Azure-portalbenachrichtigungen](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="5d57b-225">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Wechseln Sie zur Ressource Funktions-app](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="5d57b-227">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="5d57b-228">Sie gelangen in die neue *Funktions-App* Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="5d57b-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="5d57b-229">Auf der *Funktions-App* Dashboard den Mauszeiger auf *Funktionen*, innerhalb des Bereichs auf der linken Seite gefunden, und klicken Sie dann auf die **+ (plus)** Symbol.</span><span class="sxs-lookup"><span data-stu-id="5d57b-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![Erstellen Sie neue Funktion](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="5d57b-231">Vergewissern Sie sich auf der nächsten Seite **Webhook + API** ausgewählt ist, und für *wählen Sie eine Sprache,* wählen **CSharp**, wie dies mit der Sprache, die für dieses Tutorial verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="5d57b-232">Klicken Sie abschließend auf die **diese Funktion erstellen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5d57b-232">Lastly, click the **Create this function** button.</span></span>

    ![Wählen Sie Hook-Csharp web](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="5d57b-234">Sie sind, um den Code Seite ("Run.csx"), wenn nicht jedoch für die neu erstellte Funktion in der Liste der Funktionen innerhalb des Bereichs auf der linken Seite klicken.</span><span class="sxs-lookup"><span data-stu-id="5d57b-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![Öffnen Sie die neue Funktion](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="5d57b-236">Kopieren Sie den folgenden Code in Ihrer Funktion.</span><span class="sxs-lookup"><span data-stu-id="5d57b-236">Copy the following code into your function.</span></span> <span data-ttu-id="5d57b-237">Diese Funktion gibt einfach eine zufällige ganze Zahl zwischen 0 und 2, die beim Aufruf zurück.</span><span class="sxs-lookup"><span data-stu-id="5d57b-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="5d57b-238">Gedanken um den vorhandenen Code, fügen Sie oberhalb des Zertifikats können nicht.</span><span class="sxs-lookup"><span data-stu-id="5d57b-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="5d57b-239">Wählen Sie **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-239">Select **Save**.</span></span>

14. <span data-ttu-id="5d57b-240">Das Ergebnis sollte wie in der folgenden Abbildung aussehen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="5d57b-241">Klicken Sie auf **Funktions-URL abrufen** und notieren Sie sich die *Endpunkt* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="5d57b-242">Sie benötigen, fügen Sie ihn in das *AzureServices* -Klasse, die Sie weiter unten in diesem Kurs erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![Rufen Sie Funktionsendpunkt](images/AzureLabs-Lab5-16.png)

    ![Rufen Sie Funktionsendpunkt](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="5d57b-245">Kapitel 3 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="5d57b-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="5d57b-246">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit Mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="5d57b-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="5d57b-247">Richten Sie ein und Testen Sie Ihrer mixed Reality immersive Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="5d57b-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="5d57b-248">Sie **nicht** Motion-Controller für dieses Kurses erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5d57b-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="5d57b-249">Wenn Sie die Einrichtung der immersive Kopfhörer unterstützen müssen, wenden Sie [finden Sie auf die gemischte Realität Artikel richten](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="5d57b-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="5d57b-250">Öffnen von Unity, und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-250">Open Unity and click **New**.</span></span>

    ![Erstellen der neuen Unity-Projekt](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="5d57b-252">Sie müssen nun einen Namen für die Unity-Projekt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="5d57b-253">Fügen Sie **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="5d57b-254">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="5d57b-255">Legen Sie die *Speicherort* auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="5d57b-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="5d57b-256">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-256">Then, click **Create project**.</span></span>

    ![Benennen Sie neue Unity-Projekt](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="5d57b-258">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5d57b-259">Wechseln Sie zu **bearbeiten* > *Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5d57b-260">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5d57b-261">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="5d57b-261">Close the **Preferences** window.</span></span>

    ![Satz von visual Studio als Skript-editor](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="5d57b-263">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5d57b-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Plattform für die Uwp wechseln](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="5d57b-265">Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="5d57b-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="5d57b-266">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="5d57b-267">Legen Sie für Microsoft HoloLens, **Zielgerät** zu *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="5d57b-268">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="5d57b-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="5d57b-269">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="5d57b-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="5d57b-270">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="5d57b-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="5d57b-271">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="5d57b-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="5d57b-272">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="5d57b-273">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="5d57b-274">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-274">A save window will appear.</span></span>

            ![Hinzufügen von öffnen-Szenen](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="5d57b-276">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Erstellen Sie im Hintergrund-Ordner](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="5d57b-278">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname:** Textfeld **FunctionsScene**, drücken Sie dann die **speichern**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![Functions-Szene speichern](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="5d57b-280">Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="5d57b-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![Functions-Szene speichern](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="5d57b-282">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="5d57b-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![Player-Einstellungen im Inspektor](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="5d57b-284">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="5d57b-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5d57b-285">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="5d57b-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5d57b-286">**Scripting Runtime Version** muss **experimentell** (.NET 4.6 entspricht), löst der Editor neu starten müssen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="5d57b-287">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="5d57b-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="5d57b-288">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="5d57b-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="5d57b-289">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="5d57b-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5d57b-290">**InternetClient**</span></span>

            ![Set-Funktionen](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="5d57b-292">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality SDK** hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einstellungen der Set-XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="5d57b-294">Im *Buildeinstellungen* *Unity C# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="5d57b-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![Teilstriche c#-Projekte](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="5d57b-296">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="5d57b-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="5d57b-297">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="5d57b-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="5d57b-298">Kapitel 4: Einrichtung Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="5d57b-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d57b-299">Wenn Sie, überspringen möchten die *Unity einrichten* Komponenten dieses Kurs, und direkt in Code fortfahren, können Sie [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), und importieren Sie es in Ihr Projekt als eine [benutzerdefinierte Paket](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="5d57b-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="5d57b-300">Dies wird auch die DLLs aus dem nächsten Kapitel enthalten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="5d57b-301">Ist eine Fortsetzung nach dem Import, [Kapitel 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="5d57b-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="5d57b-302">In der *Hierarchie Bereich*, sehen Sie ein Objekt namens **Main Camera**, diesem Objekt dargestellten Ihr "Head" Sicht aus, wenn Sie "in" Ihrer Anwendung sind.</span><span class="sxs-lookup"><span data-stu-id="5d57b-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="5d57b-303">Wählen Sie im Unity-Dashboard vor Ihnen die **Main Camera "gameobject"**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="5d57b-304">Sie werden feststellen, dass die *Inspektor Bereich* (in der Regel nach rechts im Dashboard gefunden) zeigt die verschiedenen Komponenten, die *"gameobject"*, mit *transformieren* oben, gefolgt von *Kamera*, und einige andere Komponenten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="5d57b-305">Sie müssen die Transformation der Main-Kamera, zurücksetzen, damit sie richtig positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="5d57b-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="5d57b-306">Wählen Sie zu diesem Zweck die **Zahnradsymbol** Symbol neben der Kamera *transformieren* Komponente, und wählen **zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Transformation zurücksetzen](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="5d57b-308">Aktualisieren Sie dann die **transformieren** Komponente, die wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="5d57b-309">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="5d57b-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="5d57b-310">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-310">**X**</span></span>   | <span data-ttu-id="5d57b-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-311">**Y**</span></span>                     | <span data-ttu-id="5d57b-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-312">**Z**</span></span> |
    | <span data-ttu-id="5d57b-313">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-313">0</span></span>       | <span data-ttu-id="5d57b-314">1</span><span class="sxs-lookup"><span data-stu-id="5d57b-314">1</span></span>                         | <span data-ttu-id="5d57b-315">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-315">0</span></span>     |    

    |       | <span data-ttu-id="5d57b-316">TRANSFORM - DREHUNG</span><span class="sxs-lookup"><span data-stu-id="5d57b-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="5d57b-317">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-317">**X**</span></span> | <span data-ttu-id="5d57b-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-318">**Y**</span></span>                | <span data-ttu-id="5d57b-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-319">**Z**</span></span> |
    | <span data-ttu-id="5d57b-320">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-320">0</span></span>     | <span data-ttu-id="5d57b-321">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-321">0</span></span>                    | <span data-ttu-id="5d57b-322">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-322">0</span></span>     |

    |       | <span data-ttu-id="5d57b-323">TRANSFORM - SKALIERUNG</span><span class="sxs-lookup"><span data-stu-id="5d57b-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="5d57b-324">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-324">**X**</span></span> | <span data-ttu-id="5d57b-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-325">**Y**</span></span>             | <span data-ttu-id="5d57b-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-326">**Z**</span></span> |
    | <span data-ttu-id="5d57b-327">1</span><span class="sxs-lookup"><span data-stu-id="5d57b-327">1</span></span>     | <span data-ttu-id="5d57b-328">1</span><span class="sxs-lookup"><span data-stu-id="5d57b-328">1</span></span>                 | <span data-ttu-id="5d57b-329">1</span><span class="sxs-lookup"><span data-stu-id="5d57b-329">1</span></span>     |

    ![Set-Kamera-Transformation](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="5d57b-331">Kapitel 5: Einrichten der Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="5d57b-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="5d57b-332">Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **3D-Objekt**, Hinzufügen einer **Ebene**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![Erstellen Sie neue Ebene](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="5d57b-334">Mit der **Ebene** Objekt ausgewählt haben, ändern Sie die folgenden Parameter in der *Inspektor Bereich*:</span><span class="sxs-lookup"><span data-stu-id="5d57b-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="5d57b-335">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="5d57b-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="5d57b-336">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-336">**X**</span></span> | <span data-ttu-id="5d57b-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-337">**Y**</span></span>                | <span data-ttu-id="5d57b-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-338">**Z**</span></span> |
    | <span data-ttu-id="5d57b-339">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-339">0</span></span>     | <span data-ttu-id="5d57b-340">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-340">0</span></span>                    | <span data-ttu-id="5d57b-341">4</span><span class="sxs-lookup"><span data-stu-id="5d57b-341">4</span></span>     |

    |       | <span data-ttu-id="5d57b-342">TRANSFORM - SKALIERUNG</span><span class="sxs-lookup"><span data-stu-id="5d57b-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="5d57b-343">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-343">**X**</span></span> | <span data-ttu-id="5d57b-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-344">**Y**</span></span>             | <span data-ttu-id="5d57b-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-345">**Z**</span></span> |
    | <span data-ttu-id="5d57b-346">10</span><span class="sxs-lookup"><span data-stu-id="5d57b-346">10</span></span>    | <span data-ttu-id="5d57b-347">1</span><span class="sxs-lookup"><span data-stu-id="5d57b-347">1</span></span>                 | <span data-ttu-id="5d57b-348">10</span><span class="sxs-lookup"><span data-stu-id="5d57b-348">10</span></span>    |

    ![Set-Ebene transformationsposition und-Skalierung](images/AzureLabs-Lab5-32.png)

    ![Szenenansicht Ebene](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="5d57b-351">Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **3D-Objekt**, Hinzufügen einer **Cube**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="5d57b-352">Benennen Sie den Cube zu **GazeButton** (mit dem Cube ausgewählt haben, drücken Sie "F2").</span><span class="sxs-lookup"><span data-stu-id="5d57b-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="5d57b-353">Ändern Sie die folgenden Parameter in der *Inspektor Bereich*:</span><span class="sxs-lookup"><span data-stu-id="5d57b-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="5d57b-354">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="5d57b-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="5d57b-355">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-355">**X**</span></span> | <span data-ttu-id="5d57b-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-356">**Y**</span></span>                | <span data-ttu-id="5d57b-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-357">**Z**</span></span> |
        | <span data-ttu-id="5d57b-358">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-358">0</span></span>     | <span data-ttu-id="5d57b-359">3</span><span class="sxs-lookup"><span data-stu-id="5d57b-359">3</span></span>                    | <span data-ttu-id="5d57b-360">5</span><span class="sxs-lookup"><span data-stu-id="5d57b-360">5</span></span>     |


        ![Set Blicke Schaltfläche Transformation](images/AzureLabs-Lab5-34.png)

        ![Schaltfläche Szenenansicht bestaunen](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="5d57b-363">Klicken Sie auf die **Tag** Dropdown-Schaltfläche, und klicken Sie auf **Tag hinzufügen** zum Öffnen der *Tags und im Bereich*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Neues Tag hinzufügen](images/AzureLabs-Lab5-36.png)

        ![Select plus](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="5d57b-366">Wählen Sie die **+ (plus)** Schaltfläche, und klicken Sie in der *neue Tagnamen* Feld **GazeButton**, und drücken Sie **speichern**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![Neues Tag Name](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="5d57b-368">Klicken Sie auf die **GazeButton** -Objekt in der *Hierarchie Bereich*, und klicken Sie in der *Inspektor Bereich*, weisen Sie den neu erstellten **GazeButton** Tag.</span><span class="sxs-lookup"><span data-stu-id="5d57b-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![Weisen Sie das neue Tag Blicke-Schaltfläche](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="5d57b-370">Mit der rechten Maustaste auf die **GazeButton** Objekt, in der *Hierarchie Bereich*, und fügen ein **leeres "gameobject"** (das wird als hinzugefügt eine *untergeordneten* -Objekt).</span><span class="sxs-lookup"><span data-stu-id="5d57b-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="5d57b-371">Wählen Sie das neue Objekt, und benennen Sie sie **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="5d57b-372">Ändern Sie die folgenden Parameter in der *Inspektor Bereich*:</span><span class="sxs-lookup"><span data-stu-id="5d57b-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="5d57b-373">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="5d57b-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="5d57b-374">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-374">**X**</span></span> |<span data-ttu-id="5d57b-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-375">**Y**</span></span>                 | <span data-ttu-id="5d57b-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-376">**Z**</span></span> |
        | <span data-ttu-id="5d57b-377">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-377">0</span></span>     | <span data-ttu-id="5d57b-378">-1</span><span class="sxs-lookup"><span data-stu-id="5d57b-378">-1</span></span>                   | <span data-ttu-id="5d57b-379">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-379">0</span></span>     |

        ![Aktualisieren Sie die Form Spawn Punkt Transformation](images/AzureLabs-Lab5-40.png)

        ![Form Spawn Szenenansicht](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="5d57b-382">Als Nächstes erstellen Sie eine **3D-Text** Objekt, das Feedback zu den Status des Azure-Diensts.</span><span class="sxs-lookup"><span data-stu-id="5d57b-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="5d57b-383">Klicken Sie mit der rechten Maustaste auf die **GazeButton** in der Hierarchie im Bereich erneut aus, und fügen eine **3D-Objekt > 3D-Text** als Objekt ein *untergeordneten*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![Erstellen Sie neue 3D-Text-Objekt](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="5d57b-385">Benennen Sie die **3D-Text** -Objekt **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="5d57b-386">Ändern der **AzureStatusText** -Objekt Transformation wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5d57b-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="5d57b-387">TRANSFORM - POSITION</span><span class="sxs-lookup"><span data-stu-id="5d57b-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="5d57b-388">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-388">**X**</span></span> | <span data-ttu-id="5d57b-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-389">**Y**</span></span>                | <span data-ttu-id="5d57b-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-390">**Z**</span></span> |
    | <span data-ttu-id="5d57b-391">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-391">0</span></span>     | <span data-ttu-id="5d57b-392">0</span><span class="sxs-lookup"><span data-stu-id="5d57b-392">0</span></span>                    | <span data-ttu-id="5d57b-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="5d57b-393">-0.6</span></span>  |

    |       | <span data-ttu-id="5d57b-394">TRANSFORM - SKALIERUNG</span><span class="sxs-lookup"><span data-stu-id="5d57b-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="5d57b-395">**X**</span><span class="sxs-lookup"><span data-stu-id="5d57b-395">**X**</span></span> | <span data-ttu-id="5d57b-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="5d57b-396">**Y**</span></span>             | <span data-ttu-id="5d57b-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="5d57b-397">**Z**</span></span> |
    | <span data-ttu-id="5d57b-398">0.1</span><span class="sxs-lookup"><span data-stu-id="5d57b-398">0.1</span></span>   | <span data-ttu-id="5d57b-399">0.1</span><span class="sxs-lookup"><span data-stu-id="5d57b-399">0.1</span></span>               | <span data-ttu-id="5d57b-400">0.1</span><span class="sxs-lookup"><span data-stu-id="5d57b-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="5d57b-401">Aber keine Sorge, wenn sie off-Center, scheint, wie dies bei behoben werden die folgenden Text Mesh Komponente aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="5d57b-402">Ändern der **Text Mesh** Komponente entsprechend der unten:</span><span class="sxs-lookup"><span data-stu-id="5d57b-402">Change the **Text Mesh** component to match the below:</span></span>

    ![Set Text Mesh-Komponente](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="5d57b-404">Die ausgewählte Farbe hier ist Hexadezimalfarbe: **000000FF (Schwarz)**, jedoch können Sie Ihre eigenen auswählen, nur sicherzustellen, dass er gelesen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="5d57b-405">Die Struktur der Hierarchie Bereich sollte jetzt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![mesh-Text in der Szenenansicht](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="5d57b-407">Die Szene sollte jetzt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-407">Your scene should now look like this:</span></span>

    ![mesh-Text in der Szenenansicht](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="5d57b-409">Kapitel 6: Importieren von Azure-Speicher für Unity</span><span class="sxs-lookup"><span data-stu-id="5d57b-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="5d57b-410">Verwenden Sie Azure Storage für Unity (die wiederum nutzt das .net SDK für Azure).</span><span class="sxs-lookup"><span data-stu-id="5d57b-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="5d57b-411">Weitere Informationen finden Sie unter den [Azure Storage für Unity-Artikel](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="5d57b-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="5d57b-412">Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert.</span><span class="sxs-lookup"><span data-stu-id="5d57b-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="5d57b-413">Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="5d57b-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="5d57b-414">Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie heruntergeladen haben, die neueste Version [".unitypackage" von GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="5d57b-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="5d57b-415">Führen Sie anschließend folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="5d57b-415">Then, do the following:</span></span>

1.  <span data-ttu-id="5d57b-416">Hinzufügen der **.unitypackage** Datei in Unity mithilfe der **Assets > Paket importieren > benutzerdefiniertes Paket** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="5d57b-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="5d57b-417">In der **Unity-Paket importieren** Feld angezeigt, alles unter können Sie auswählen \**-Plug-Ins* > \*Storage\*\*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="5d57b-418">Deaktivieren Sie alles andere, da sie für diesen Kurs nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Paket importieren](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="5d57b-420">Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="5d57b-421">Wechseln Sie zu der *Storage* Unterordner *-Plug-Ins*in der Projektansicht, und wählen Sie die folgenden Plug-Ins *nur*:</span><span class="sxs-lookup"><span data-stu-id="5d57b-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="5d57b-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="5d57b-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="5d57b-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="5d57b-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="5d57b-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="5d57b-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="5d57b-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="5d57b-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="5d57b-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="5d57b-426">System.Spatial</span></span>

        ![Deaktivieren Sie jede Plattform](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="5d57b-428">Mit *bestimmte Plug-Ins* ausgewählt, **deaktivieren** *Any Platform* und **deaktivieren** *WSAPlayer* Klicken Sie dann auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![Anwenden von Plattform-dlls](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="5d57b-430">Wir markieren diese bestimmten Plug-Ins, die nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="5d57b-431">Dies ist, da es gibt verschiedene Versionen der gleichen Plug-Ins in das WSA-Ordner, der verwendet wird und nachdem das Projekt aus Unity exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="5d57b-432">In der *Storage* -Plug-in-Ordner, wählen Sie nur:</span><span class="sxs-lookup"><span data-stu-id="5d57b-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="5d57b-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="5d57b-433">Microsoft.Data.Services.Client</span></span>

        ![Gruppe nicht für DLL-Dateien verarbeiten](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="5d57b-435">Überprüfen Sie die **Don't Prozess** Feld *Plattformeinstellungen* , und klicken Sie auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="5d57b-437">Wir werden dieses Plug-in "Nicht verarbeiten" markieren, da die Unity-Assembly-Patcher schwierigkeiten beim Verarbeiten dieses Plug-in ist.</span><span class="sxs-lookup"><span data-stu-id="5d57b-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="5d57b-438">Das Plug-in funktioniert weiterhin, auch wenn sie nicht verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="5d57b-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="5d57b-439">Kapitel 7: Erstellen Sie die AzureServices-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d57b-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="5d57b-440">Die erste Klasse, die Sie erstellen wollen ist die *AzureServices* Klasse.</span><span class="sxs-lookup"><span data-stu-id="5d57b-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="5d57b-441">Die *AzureServices* Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="5d57b-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="5d57b-442">Das Speichern von Anmeldeinformationen für Azure-Konto.</span><span class="sxs-lookup"><span data-stu-id="5d57b-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="5d57b-443">Aufrufen von Ihrer Azure-App-Funktion.</span><span class="sxs-lookup"><span data-stu-id="5d57b-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="5d57b-444">Der Upload und Download von der Datendatei in Ihrem Azure-Cloudspeicher.</span><span class="sxs-lookup"><span data-stu-id="5d57b-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="5d57b-445">Zum Erstellen dieser Klasse:</span><span class="sxs-lookup"><span data-stu-id="5d57b-445">To create this Class:</span></span>

1.  <span data-ttu-id="5d57b-446">Mit der rechten Maustaste den *Asset* Ordner befindet sich im Projektfenster **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="5d57b-447">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-447">Name the folder **Scripts**.</span></span>

    ![neuen Ordner erstellen](images/AzureLabs-Lab5-50.png)

    ![Rufen Sie die Ordner - Skripts](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="5d57b-450">Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="5d57b-451">Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="5d57b-452">Rufen Sie das Skript *AzureServices*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="5d57b-453">Doppelklicken Sie auf dem neuen *AzureServices* Klasse, öffnen Sie ihn mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="5d57b-454">Fügen Sie die folgenden Namespaces am Anfang der *AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="5d57b-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="5d57b-455">Fügen Sie die folgenden Inspektor-Felder in der *AzureServices* Klasse:</span><span class="sxs-lookup"><span data-stu-id="5d57b-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="5d57b-456">Fügen Sie dann die folgenden Membervariablen in der *AzureServices* Klasse:</span><span class="sxs-lookup"><span data-stu-id="5d57b-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="5d57b-457">Stellen Sie sicher, dass Sie ersetzen die *Endpunkt* und *Verbindungszeichenfolge* durch die Werte aus Ihrem Azure-Speicher finden Sie im Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="5d57b-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="5d57b-458">Code für *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5d57b-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="5d57b-459">Diese Methoden werden aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="5d57b-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="5d57b-460">Wir werden Geben Sie den Code für *CallAzureFunctionForNextShape()* in eine [zukünftige Kapitel](#chapter-10---completing-the-AzureServices-class).</span><span class="sxs-lookup"><span data-stu-id="5d57b-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="5d57b-461">Löschen der *Update()* Methode, da diese Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5d57b-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="5d57b-462">Speichern Sie die Änderungen in Visual Studio, und klicken Sie dann zurück zu Unity.</span><span class="sxs-lookup"><span data-stu-id="5d57b-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="5d57b-463">Klicken Sie auf, und ziehen Sie die *AzureServices* Klasse aus dem Ordner Scripts, um die Main Camera-Objekts in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="5d57b-464">Wählen Sie die Main Camera, und ziehen Sie die **AzureStatusText** untergeordnetes Objekt aus, unter der **GazeButton** Objekt aus, und platzieren Sie sie in der **AzureStatusText** Verweisziel Feld, in der *Inspektor*, geben Sie den Verweis auf die *AzureServices* Skript.</span><span class="sxs-lookup"><span data-stu-id="5d57b-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![Weisen Sie Azure-Status Text Verweisziel](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="5d57b-466">Kapitel 8 – erstellen Sie die ShapeFactory-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d57b-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="5d57b-467">Das nächste Skript zu erstellen, wird die *ShapeFactory* Klasse.</span><span class="sxs-lookup"><span data-stu-id="5d57b-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="5d57b-468">Die Rolle von dieser Klasse besteht darin, während der Erstellung einer neuen Form angefordert, und Speichern eines Verlaufs der Formen in erstellt eine *Form Verlaufsliste*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="5d57b-469">Jedes Mal ein Shape erstellt wird, die *Form Verlaufsliste* wird aktualisiert, der *AzureService* Klasse, und klicken Sie dann in gespeichert Ihre *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="5d57b-470">Beim Starten der Anwendung, wenn eine gespeicherte Datei, in gefunden wird Ihre *Azure Storage*, *Form Verlaufsliste* abgerufen und wiedergegeben, mit der **3D-Text** mit Gibt an, ob die generierte Form aus dem Speicher oder neuer ist.</span><span class="sxs-lookup"><span data-stu-id="5d57b-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="5d57b-471">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-471">To create this class:</span></span>

1.  <span data-ttu-id="5d57b-472">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="5d57b-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="5d57b-473">Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="5d57b-474">Rufen Sie das Skript *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="5d57b-475">Doppelklicken Sie auf dem neuen *ShapeFactory* Skript öffnen Sie ihn mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="5d57b-476">Stellen Sie sicher die *ShapeFactory* Klasse enthält die folgenden Namespaces:</span><span class="sxs-lookup"><span data-stu-id="5d57b-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="5d57b-477">Fügen Sie die folgenden Variablen das *ShapeFactory* Klasse, und Ersetzen Sie die *Start()* und *Awake()* Funktionen mit den folgenden:</span><span class="sxs-lookup"><span data-stu-id="5d57b-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="5d57b-478">Die *CreateShape()* Methode generiert, die primitiven Formen auf Grundlage der bereitgestellten *Ganzzahl* Parameter.</span><span class="sxs-lookup"><span data-stu-id="5d57b-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="5d57b-479">Der boolesche Parameter wird verwendet, um anzugeben, ob die gerade erstellte Form aus dem Speicher oder neuen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="5d57b-480">Platzieren Sie den folgenden Code in Ihre *ShapeFactory* -Klasse, unter der vorherigen Methoden:</span><span class="sxs-lookup"><span data-stu-id="5d57b-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="5d57b-481">Achten Sie darauf, dass Sie Ihre Änderungen vor der Rückgabe an Unity in Visual Studio zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5d57b-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="5d57b-482">Zurück in die Unity-Editor zu klicken und ziehen Sie die *ShapeFactory* -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="5d57b-483">Mit der Main-Kamera, die ausgewählt werden Sie feststellen der *ShapeFactory* Skriptkomponente fehlt die *Spawn Punkt* Verweis.</span><span class="sxs-lookup"><span data-stu-id="5d57b-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="5d57b-484">Um dies zu beheben, ziehen Sie die **ShapeSpawnPoint** -Objekt aus der *Hierarchie Bereich* auf die **Spawn Punkt** Verweisziel.</span><span class="sxs-lookup"><span data-stu-id="5d57b-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![Verweisziel Factory "Form" Gruppe](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="5d57b-486">Kapitel 9 – erstellen Sie die Blicke-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d57b-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="5d57b-487">Ist das letzte Skript Sie müssen die *bestaunen* Klasse.</span><span class="sxs-lookup"><span data-stu-id="5d57b-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="5d57b-488">Diese Klasse ist zuständig für das Erstellen einer **Raycast** , wird von der Main-Kamera, welches Objekt erkannt, wird der Benutzer betrachten, vorwärts projiziert werden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="5d57b-489">In diesem Fall müssen die Raycast um festzustellen, ob der Benutzer ansieht der **GazeButton** Objekt in der Szene, und lösen Sie ein Verhalten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="5d57b-490">Zum Erstellen dieser Klasse:</span><span class="sxs-lookup"><span data-stu-id="5d57b-490">To create this Class:</span></span>

1.  <span data-ttu-id="5d57b-491">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="5d57b-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="5d57b-492">Mit der rechten Maustaste im Projektpanel, **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="5d57b-493">Rufen Sie das Skript *bestaunen*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="5d57b-494">Doppelklicken Sie auf dem neuen *bestaunen* Skript öffnen Sie ihn mit *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="5d57b-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="5d57b-495">Stellen Sie sicher, dass es sich bei der folgende Namespace am Anfang des Skripts enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="5d57b-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="5d57b-496">Klicken Sie dann fügen Sie die folgenden Variablen in der *bestaunen* Klasse:</span><span class="sxs-lookup"><span data-stu-id="5d57b-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="5d57b-497">Einige dieser Variablen kann bearbeitet werden, in der *Editor*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="5d57b-498">Code für die *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5d57b-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="5d57b-499">Fügen Sie folgenden Code, der zusammen mit einem Cursor-Objekt am Anfang, erstellt die *Update()* -Methode, die ausgeführt wird, die Raycast-Methode, sowie, in dem der GazeEnabled boolesche ein-/ausgeschaltet wird:</span><span class="sxs-lookup"><span data-stu-id="5d57b-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="5d57b-500">Als Nächstes fügen die *UpdateRaycast()* Methode, dem Projekt eine Raycast und das Trefferanzahl-Ziel zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="5d57b-501">Abschließend fügen die *ResetFocusedObject()* -Methode, die umschalten wird die GazeButton Objekte aktuelle Farbe, der angibt, ob er eine neue Form oder nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="5d57b-502">Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.</span><span class="sxs-lookup"><span data-stu-id="5d57b-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="5d57b-503">Klicken und ziehen Sie die *bestaunen* Klasse aus dem Ordner Scripts, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="5d57b-504">Kapitel 10 – Abschließen der AzureServices-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d57b-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="5d57b-505">Mit den anderen Skripts vorhanden, ist es jetzt möglich, *vollständige* der *AzureServices* Klasse.</span><span class="sxs-lookup"><span data-stu-id="5d57b-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="5d57b-506">Dies wird durch erreicht werden:</span><span class="sxs-lookup"><span data-stu-id="5d57b-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="5d57b-507">Hinzufügen einer neuen Methode mit dem Namen *CreateCloudIdentityAsync()*, um die Authentifizierung-Variablen, die erforderlich sind, für die Kommunikation mit Azure einzurichten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="5d57b-508">Diese Methode überprüft auch das Vorhandensein einer zuvor gespeicherte Datei mit der Form-Liste.</span><span class="sxs-lookup"><span data-stu-id="5d57b-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="5d57b-509">**Wenn die Datei gefunden wird**, wird es den Benutzer deaktiviert *bestaunen*, und die Form erstellen, nach dem Muster von Formen, die ausgelöst werden, da in gespeichert der **Azure Storage-Datei**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="5d57b-510">Der Benutzer dies sehen, wie die **Text Mesh** bieten anzeigen "Storage" oder "New", abhängig vom Ursprung Formen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="5d57b-511">**Wenn keine Datei gefunden wird**, können sie die *bestaunen*, aktivieren den Benutzer aus, um Formen zu erstellen, bei Betrachtung der **GazeButton** Objekts in der Szene.</span><span class="sxs-lookup"><span data-stu-id="5d57b-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="5d57b-512">Der nächste Codeausschnitt ist innerhalb der *Start()* Methode, bei dem ein Aufruf an vorgenommen werden, die *CreateCloudIdentityAsync()* Methode.</span><span class="sxs-lookup"><span data-stu-id="5d57b-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="5d57b-513">Gerne über Ihre aktuellen kopieren *Start()* -Methode, mit der folgenden:</span><span class="sxs-lookup"><span data-stu-id="5d57b-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="5d57b-514">Geben Sie den Code für die Methode *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="5d57b-515">Verwenden Sie das zuvor erstellte *Azure Function-App* einen Index der Form "anfordern.</span><span class="sxs-lookup"><span data-stu-id="5d57b-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="5d57b-516">Sobald die neue Form empfangen wird, sendet diese Methode die Form, um die *ShapeFactory* Klasse, um die neue Form in der Szene zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="5d57b-517">Verwenden Sie den folgenden Code zum Abschließen des Texts der *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="5d57b-518">Fügen Sie eine Methode zum Erstellen von einer Zeichenfolge, durch die Verkettung von ganzen Zahlen gespeichert, in der Verlaufsliste Form, und speichern es in Ihrer *Azure Storage File*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="5d57b-519">Fügen Sie eine Methode zum Abrufen des Texts in der Datei im Verzeichnis gespeicherten Ihre *Azure Storage File* und *Deserialisieren* ihn in eine Liste.</span><span class="sxs-lookup"><span data-stu-id="5d57b-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="5d57b-520">Sobald der Vorgang abgeschlossen ist, aktiviert erneut die Methode die Blicke, damit der Benutzer weitere Formen der Szene hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5d57b-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="5d57b-521">Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.</span><span class="sxs-lookup"><span data-stu-id="5d57b-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="5d57b-522">Kapitel 11: Erstellen Sie die UWP-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="5d57b-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="5d57b-523">Um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="5d57b-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="5d57b-524">Wechseln Sie zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-524">Go to **File > Build Settings**.</span></span>

    ![Erstellen Sie die app](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="5d57b-526">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-526">Click **Build**.</span></span> <span data-ttu-id="5d57b-527">Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="5d57b-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="5d57b-528">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es *App*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="5d57b-529">Klicken Sie dann mit der *App* Ordner ausgewählt haben, drücken Sie **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="5d57b-530">Erstellen Ihres Projekts zu Unity beginnt die *App* Ordner.</span><span class="sxs-lookup"><span data-stu-id="5d57b-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="5d57b-531">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein *Datei-Explorer* Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="5d57b-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="5d57b-532">Kapitel 12: Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="5d57b-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="5d57b-533">Um die Anwendung bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-533">To deploy your application:</span></span>

1.  <span data-ttu-id="5d57b-534">Navigieren Sie zu der *App* Ordner, der erstellt wurde die [letzte Kapitel](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="5d57b-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="5d57b-535">Sehen Sie eine Datei durch den Namen der apps mit der Erweiterung ".sln", die Sie doppelklicken, sollten Sie so öffnen Sie sie in *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="5d57b-536">In der **Projektmappenplattform**Option **X86, lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="5d57b-537">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="5d57b-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="5d57b-538">Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="5d57b-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="5d57b-539">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="5d57b-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="5d57b-540">Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="5d57b-541">Stellen Sie sicher **Entwicklermodus** ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.</span><span class="sxs-lookup"><span data-stu-id="5d57b-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Bereitstellen der Lösung](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="5d57b-543">Wechseln Sie zu der **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="5d57b-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="5d57b-544">Ihre App sollte nun angezeigt werden, in der Liste der installierten apps, die gestartet und getestet werden können.</span><span class="sxs-lookup"><span data-stu-id="5d57b-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="5d57b-545">Die fertige Azure Functions und Storage-Anwendung</span><span class="sxs-lookup"><span data-stu-id="5d57b-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="5d57b-546">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die sowohl die Azure Functions und Azure Storage-Dienste nutzt.</span><span class="sxs-lookup"><span data-stu-id="5d57b-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="5d57b-547">Ihre app wird in der Lage gespeicherten Daten, und geben Sie eine Aktion, die auf Basis dieser Daten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![Endprodukt-Ende](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="5d57b-549">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="5d57b-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="5d57b-550">Übung 1</span><span class="sxs-lookup"><span data-stu-id="5d57b-550">Exercise 1</span></span>

<span data-ttu-id="5d57b-551">Erstellen Sie eine zweite erzeugen, Punkt und Datensatz, der Zeitpunkt zu erzeugen, die über ein Objekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="5d57b-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="5d57b-552">Wenn Sie die Datei laden, Wiedergeben von Formen erzeugt wird, von dem Speicherort, die, den Sie erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="5d57b-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="5d57b-553">Übung 2</span><span class="sxs-lookup"><span data-stu-id="5d57b-553">Exercise 2</span></span>

<span data-ttu-id="5d57b-554">Erstellen Sie eine Möglichkeit zum Starten der app, anstatt ihn jedes Mal erneut öffnen.</span><span class="sxs-lookup"><span data-stu-id="5d57b-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="5d57b-555">**Laden Szenen** ist ein guter Platz, um zu starten.</span><span class="sxs-lookup"><span data-stu-id="5d57b-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="5d57b-556">Anschließend erstellen Sie eine Möglichkeit zum Löschen der gespeicherten Liste *Azure Storage*, sodass sie problemlos von Ihrer app zurückgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5d57b-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
