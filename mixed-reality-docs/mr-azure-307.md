---
title: MR und Azure 307 - Machine-learning
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Machine Learning Studio in einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, für maschinelles lernen, ml, Machine Learning Studio, Hololens, immersive, vr
ms.openlocfilehash: 726a6cce91d46ad878f8502381d085fb979ac72a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594337"
---
>[!NOTE]
><span data-ttu-id="f4de9-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="f4de9-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f4de9-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f4de9-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f4de9-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f4de9-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f4de9-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="f4de9-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f4de9-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="f4de9-110">MR und Azure-307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="f4de9-110">MR and Azure 307: Machine learning</span></span>

![Endprodukt-starten](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="f4de9-112">In diesem Kurs lernen Sie, wie Sie Machine Learning (ML)-Funktionen zu einer mixed Reality-Anwendung mit Azure Machine Learning Studio hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="f4de9-113">*Azure Machine Learning Studio* ist ein Microsoft-Dienst, der Entwickler mit Dateneingabe, Ausgabe, Vorbereitung und Visualisierung kann nützlich sein, eine große Anzahl von Machine Learning-Algorithmen, gewährt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="f4de9-114">Aus dieser Komponenten ist es dann möglich, ein predictive Analytics-Experiment entwickeln, iterativ durchlaufen und verwenden dieses Zugriffstokens zum Trainieren Ihres Modells.</span><span class="sxs-lookup"><span data-stu-id="f4de9-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="f4de9-115">Folgende Training können machen Sie Ihr Modell operational innerhalb der Azure-Cloud, damit es dann neue Daten zu bewerten kann.</span><span class="sxs-lookup"><span data-stu-id="f4de9-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="f4de9-116">Weitere Informationen finden Sie auf die [Azure Machine Learning Studio-Seite](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="f4de9-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="f4de9-117">Nach Abschluss dieses Kurses, Sie müssen eine mixed Reality immersive Kopfhörer-Anwendung und werden haben gelernt, wie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="f4de9-118">Geben Sie eine Tabelle mit Umsatzdaten, die für die *Azure Machine Learning Studio* -Portal und der Entwurf einen Algorithmus zur Vorhersage zukünftiger Umsätze beliebte Artike.</span><span class="sxs-lookup"><span data-stu-id="f4de9-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="f4de9-119">Erstellen Sie eine **Unity-Projekt**, die empfangen und Interpretieren der Daten zur werbungsklickvorhersage aus dem ML-Dienst.</span><span class="sxs-lookup"><span data-stu-id="f4de9-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="f4de9-120">Zeigen Sie die Predication-Daten visuell in der **Unity-Projekt**, über die am häufigsten verwendeten Elemente sales im Regal verstauben bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="f4de9-121">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f4de9-122">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="f4de9-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="f4de9-123">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="f4de9-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="f4de9-124">Dieser Kurs ist eine eigenständige Tutorials, das aller anderen Mixed Reality-Labs nicht direkt betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="f4de9-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="f4de9-125">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="f4de9-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f4de9-126">Kurs</span><span class="sxs-lookup"><span data-stu-id="f4de9-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f4de9-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f4de9-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f4de9-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="f4de9-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f4de9-129">MR und Azure-307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="f4de9-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="f4de9-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f4de9-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f4de9-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f4de9-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f4de9-132">Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f4de9-133">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f4de9-134">Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4de9-135">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f4de9-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f4de9-136">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="f4de9-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f4de9-137">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="f4de9-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f4de9-138">Sie können zur Verwendung der neuesten Software, wie in der [installieren Sie die Tools-Artikel](install-the-tools.md), obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="f4de9-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f4de9-139">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="f4de9-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f4de9-140">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="f4de9-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f4de9-141">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="f4de9-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f4de9-142">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="f4de9-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f4de9-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f4de9-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f4de9-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f4de9-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f4de9-145">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="f4de9-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f4de9-146">Zugriff auf das Internet für die Einrichtung von Azure und ML-Datenabruf</span><span class="sxs-lookup"><span data-stu-id="f4de9-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f4de9-147">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="f4de9-147">Before you start</span></span>

<span data-ttu-id="f4de9-148">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="f4de9-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="f4de9-149">Kapitel 1: Azure Storage-Konto</span><span class="sxs-lookup"><span data-stu-id="f4de9-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="f4de9-150">Um die Translator-API von Azure zu verwenden, müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="f4de9-151">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="f4de9-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f4de9-152">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f4de9-153">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="f4de9-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f4de9-154">Sobald Sie angemeldet sind, klicken Sie auf **Speicherkonten** im linken Menü.</span><span class="sxs-lookup"><span data-stu-id="f4de9-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="f4de9-156">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="f4de9-157">Auf der **Speicherkonten** Registerkarte, klicken Sie auf **hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="f4de9-159">In der **Create Storage Account** Bereich:</span><span class="sxs-lookup"><span data-stu-id="f4de9-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="f4de9-160">Fügen Sie eine **Namen** für Ihr Konto bedenken, dass dieses Feld akzeptiert nur Ziffern und Kleinbuchstaben zulässig.</span><span class="sxs-lookup"><span data-stu-id="f4de9-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="f4de9-161">Für **Bereitstellungsmodell** wählen **RM**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="f4de9-162">Für **Kontoart**Option **Speicher (Allgemein v1)**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="f4de9-163">Für **Leistung**Option **Standard**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="f4de9-164">Für **Replikation** wählen **Read-Access-georedundanter Speicher (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="f4de9-165">Lassen Sie **sichere Übertragung erforderlich** als **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="f4de9-166">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="f4de9-167">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f4de9-168">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f4de9-169">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="f4de9-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="f4de9-170">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f4de9-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="f4de9-171">Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="f4de9-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f4de9-172">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f4de9-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f4de9-173">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4de9-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="f4de9-174">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="f4de9-176">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="f4de9-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="f4de9-177">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="f4de9-179">Kapitel 2: Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="f4de9-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="f4de9-180">Verwenden der *Azure Machine Learning*, müssen Sie so konfigurieren Sie eine Instanz von Machine Learning-Dienst für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="f4de9-181">Klicken Sie im Azure-Portal auf **neu** in der oberen linken Ecke, und suchen Sie nach **Machine Learning Studio Workspace**, drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="f4de9-183">Die neue Seite bietet eine Beschreibung der **Machine Learning Studio Workspace** Service.</span><span class="sxs-lookup"><span data-stu-id="f4de9-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="f4de9-184">Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="f4de9-185">Nachdem Sie auf geklickt haben **erstellen**, ein Bereich wird angezeigt, in denen Sie einige Details zu den neuen bereitstellen müssen **Machine Learning Studio-Dienst**:</span><span class="sxs-lookup"><span data-stu-id="f4de9-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="f4de9-186">Fügen Sie Ihre bevorzugte **Arbeitsbereichsname** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="f4de9-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="f4de9-187">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="f4de9-188">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f4de9-189">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f4de9-190">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="f4de9-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="f4de9-191">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f4de9-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="f4de9-192">Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="f4de9-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f4de9-193">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f4de9-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f4de9-194">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f4de9-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="f4de9-195">Sie sollten die gleiche Ressourcengruppe verwenden, die Sie zum Erstellen von Azure Storage im vorherigen Kapitel verwendet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="f4de9-196">Für die **Speicherkonto** auf **vorhandene**klicken Sie auf das Dropdownmenü, und anschließend von dort aus, klicken Sie auf die **Speicherkonto** Sie im letzten Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f4de9-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="f4de9-197">Wählen Sie das entsprechende **Tarif des Arbeitsbereichs** für Sie aus dem Dropdownmenü aus.</span><span class="sxs-lookup"><span data-stu-id="f4de9-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="f4de9-198">In der **Web Service-Plan** auf **erstellen** **neue** fügen Sie dann einen Namen ein, in das Textfeld ein.</span><span class="sxs-lookup"><span data-stu-id="f4de9-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="f4de9-199">Von der **Web Service-Plan, den Tarif** wählen den Tarif Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="f4de9-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="f4de9-200">Eine Entwicklungstests Ebene namens **DEVTEST Standard** sollte Ihnen kostenlos zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="f4de9-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="f4de9-201">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="f4de9-202">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="f4de9-204">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="f4de9-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="f4de9-205">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="f4de9-207">Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="f4de9-209">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="f4de9-210">Auf der Seite angezeigt, unter der **zusätzliche Links** auf **starten Machine Learning Studio**, die im Browser leitet der **Machine Learning Studio** das Portal.</span><span class="sxs-lookup"><span data-stu-id="f4de9-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="f4de9-212">Verwenden der **Anmeldung** Schaltfläche oben rechts oder in der Mitte, bei Ihrer Machine Learning Studio anmelden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="f4de9-214">Kapitel 3 – Machine Learning Studio: DataSet-setup</span><span class="sxs-lookup"><span data-stu-id="f4de9-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="f4de9-215">Eine der Methoden, mit denen Machine Learning-Algorithmen funktionieren basiert auf das vorhandene Dataset durch Analysieren der vorhandene Daten und anschließend versucht wird, um zukünftige Ergebnisse vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="f4de9-216">Dies bedeutet im Allgemeinen mehr vorhandenen Daten, die Ihre können, desto besser, findet der Algorithmus sich auf zukünftige Ergebnisse vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="f4de9-217">Eine Beispiel für die Tabelle wird bereitgestellt, um Sie für diesen Kurs aufgerufen [ProductsTableCSV und kann hier heruntergeladen werden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="f4de9-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4de9-218">Die oben genannten ZIP-Datei enthält sowohl die **ProductsTableCSV** und **.unitypackage**, müssen Sie in [Kapitel 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="f4de9-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="f4de9-219">Dieses Paket wird auch in diesem Kapitel, obwohl der Csv-Datei getrennt bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="f4de9-220">Dieses Beispiel-DataSet enthält einen Datensatz der meistverkauften Objekte auf einmal pro Stunde, der jeden Tag des Jahres 2017.</span><span class="sxs-lookup"><span data-stu-id="f4de9-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="f4de9-222">Zum Beispiel wurde auf 1 Tag von 2017, 13 Uhr (Stunde 13), der umsatzstärksten Artikel an: Salz und Pfeffer.</span><span class="sxs-lookup"><span data-stu-id="f4de9-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="f4de9-223">Dieses Beispiel für die Tabelle enthält die 9998 Einträge.</span><span class="sxs-lookup"><span data-stu-id="f4de9-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="f4de9-224">Navigieren Sie wieder zum die **Machine Learning Studio** Portal, und fügen Sie diese Tabelle als eine **Dataset** für Ihre ML.</span><span class="sxs-lookup"><span data-stu-id="f4de9-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="f4de9-225">Durch Klicken auf die **+ neu** -Schaltfläche in der unteren linken Ecke des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="f4de9-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="f4de9-227">Ein Abschnitt wird im unteren Bereich, und klicken Sie in das Fenster angezeigt, dass es im Navigationsbereich auf der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="f4de9-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="f4de9-228">Klicken Sie auf **Dataset**, und nach rechts, und klicken Sie dann **From Local File**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="f4de9-230">Hochladen der neuen **Dataset** mit folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="f4de9-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="f4de9-231">Der Uploadfenster wird angezeigt, können Sie **Durchsuchen** der Festplatte für das neue Dataset.</span><span class="sxs-lookup"><span data-stu-id="f4de9-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="f4de9-233">Nachdem ausgewählt und im Fenster "Upload" Sichern, lassen Sie das Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="f4de9-234">Geben Sie im Textfeld folgenden **ProductsTableCSV.csv** als Namen für das Dataset (wenn auch automatisch hinzugefügt werden soll).</span><span class="sxs-lookup"><span data-stu-id="f4de9-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="f4de9-235">Verwenden das Dropdownmenü für **Typ**Option **generische CSV-Datei mit einer Kopfzeile (.csv)**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="f4de9-236">Drücken Sie die Teilstriche in der unteren rechten Rand des Fensters hochladen und die **Dataset** hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="f4de9-237">Kapitel 4 – Machine Learning Studio: Das Experiment</span><span class="sxs-lookup"><span data-stu-id="f4de9-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="f4de9-238">Bevor Sie Ihre Machine learning-System erstellen können, müssen Sie beim Erstellen eines Experiments, um Ihre Theorie zu Ihren Daten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="f4de9-239">Mit den Ergebnissen wissen Sie, ob Sie weitere Daten benötigen oder wenn keine Abhängigkeit zwischen den Daten und ein mögliches Ergebnis vorliegt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="f4de9-240">So starten Sie ein Experiment zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="f4de9-241">Klicken Sie erneut auf die **+ neu** in der unteren linken Rand der Seite auf die Schaltfläche, und klicken Sie dann auf **Experiment** > **Blank Experiment**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="f4de9-243">Mit der ein leeres Experiment wird eine neue Seite angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f4de9-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="f4de9-244">Im Bereich auf der linken erweitern \**Saved Datasets* > \* Meine Datasets \*\*, und ziehen Sie die **ProductsTableCSV** auf die **Experimentbereich**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-244">From the panel on the left expand \**Saved Datasets* > \*My Datasets\*\* and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="f4de9-246">Erweitern Sie im Bereich auf der linken Seite **Datentransformation** > **Sample and Split**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="f4de9-247">Ziehen Sie dann die **Split Data** zum Element der **Experimentbereich**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="f4de9-248">Das Split-Datenelement wird das Dataset in zwei Teile aufgeteilt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="f4de9-249">Ein Teil verwenden Sie zum Trainieren von Machine Learning-Algorithmus.</span><span class="sxs-lookup"><span data-stu-id="f4de9-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="f4de9-250">Im zweite Teil wird zum Auswerten der Genauigkeit des-Algorithmus generiert verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="f4de9-252">Bearbeiten Sie im rechten Bereich (während die Split-Daten, das Element im Zeichenbereich ausgewählt ist), die **Anteil der Zeilen im ersten Ausgabedatensatz** zu **0,7**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="f4de9-253">Dadurch werden die Daten in zwei Bereiche aufgeteilt, der erste Teil werden 70 % der Daten und der zweite Teil werden die verbleibenden 30 %.</span><span class="sxs-lookup"><span data-stu-id="f4de9-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="f4de9-254">Um sicherzustellen, dass die Daten nach dem Zufallsprinzip aufgeteilt wird, stellen Sie sicher, dass die **zufällige Aufteilung** Kontrollkästchen aktiviert bleibt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="f4de9-256">Ziehen Sie eine Verbindung aus der Basis der **ProductsTableCSV** Element auf der Leinwand und dem oberen Rand der Split-Datenelement.</span><span class="sxs-lookup"><span data-stu-id="f4de9-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="f4de9-257">Wird die Elemente verbinden und senden die **ProductsTableCSV** Dataset-Ausgabe (Daten), die aufgeteilten Daten eingeben.</span><span class="sxs-lookup"><span data-stu-id="f4de9-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="f4de9-259">In der **Experimente** auf der linken Seite im Bereich, erweitern Sie \**Machine Learning* > \* Train **. Ziehen Sie die **Train Model \*\* Element, in in den experimentbereich.</span><span class="sxs-lookup"><span data-stu-id="f4de9-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train **. Drag the **Train Model\*\* item out in to the Experiment canvas.</span></span> <span data-ttu-id="f4de9-260">Zeichenbereich sollte identisch aussehen der folgenden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-260">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="f4de9-262">Von der ***unten links*** von der **Split Data** Element ziehen, eine Verbindung mit der **oben rechts** von der **Train Model** Element.</span><span class="sxs-lookup"><span data-stu-id="f4de9-262">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="f4de9-263">Die erste Teilung von 70 % aus dem Dataset wird durch das Modell trainieren verwendet werden, den Algorithmus trainiert.</span><span class="sxs-lookup"><span data-stu-id="f4de9-263">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="f4de9-265">Wählen Sie die **Train Model** Element im Zeichenbereich, und klicken Sie in der **Eigenschaften** (auf der rechten Seite im Browserfenster) klicken Sie auf die **Spaltenauswahl starten**  Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f4de9-265">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="f4de9-266">In das Textfeld **Produkt** , und drücken Sie dann die **EINGABETASTE**, *Produkt* wird als eine Spalte festgelegt werden, um vorhersagen zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="f4de9-266">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="f4de9-267">Anschluss klicken Sie auf die **Tick** in der Ecke unten rechts, um das Dialogfeld "Auswahl" zu schließen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-267">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="f4de9-269">Sie sind dabei, zu trainieren einer **Mehrklassige logistische Regression** Algorithmus, um die Angaben zu Käufer vorherzusagen **Produkt** basierend auf der Stunde des Tages und dem Datum.</span><span class="sxs-lookup"><span data-stu-id="f4de9-269">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="f4de9-270">Es ist nicht Gegenstand dieses Dokument wird erläutert, die Details der bereitgestellten Azure Machine Learning Studio, jedoch unterschiedlichen Algorithmen finden Sie mehr über die [Cheat Sheet für Machine Learning-Algorithmus](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="f4de9-270">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="f4de9-271">Erweitern Sie im Experiment Elemente im Bereich mit auf der linken Seite \*\**Machine Learning* > *Modell initialisieren* > \* Klassifizierung \***, und ziehen Sie die **Multiclass Die logistische Regression \*\* Element auf dem experimentbereich befindet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-271">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\***, and drag the **Multiclass Logistic Regression\*\* item on to the experiment canvas.</span></span>

13. <span data-ttu-id="f4de9-272">Verbinden Sie die Ausgabe, zwischen dem unteren Rand der **Mehrklassige logistische Regression**, mit der linken oberen Eingabe der **Train Model** Element.</span><span class="sxs-lookup"><span data-stu-id="f4de9-272">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="f4de9-274">Erweitern Sie in der Experiment-Elemente im Bereich auf der linken Seite \**Machine Learning* > \* Bewertung **, und ziehen Sie die **Score-Model \*\* Element an der Leinwand.</span><span class="sxs-lookup"><span data-stu-id="f4de9-274">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score **, and drag the **Score Model\*\* item on to the canvas.</span></span>

15. <span data-ttu-id="f4de9-275">Verbinden Sie die Ausgabe, zwischen dem unteren Rand der **Train Model**, mit der linken oberen Eingabe der **Score Model**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-275">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="f4de9-276">Verbinden Sie die Ausgabe unten rechts von **Split Data**, mit der rechten oberen Eingabe der \**Score Model* Element \*.</span><span class="sxs-lookup"><span data-stu-id="f4de9-276">Connect the bottom-right output from **Split Data**, to the top-right input of the \**Score Model* item\*.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="f4de9-278">In der Liste der **Experiment** Elemente im Bereich auf der linken Seite zu erweitern \*\**Machine Learning* > \* auswerten \***, und ziehen Sie die **Element bewerten Modell \*\* in den experimentbereich.</span><span class="sxs-lookup"><span data-stu-id="f4de9-278">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\***, and drag the **Evaluate Model\*\* item onto the canvas.</span></span>

18. <span data-ttu-id="f4de9-279">Verbinden Sie die Ausgabe aus dem **Score Model** mit der linken oberen Eingabe der **Evaluate Model**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-279">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="f4de9-281">Sie haben Ihr erstes Machine Learning-Experiment erstellt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-281">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="f4de9-282">Sie können jetzt speichern, und führen Sie das Experiment.</span><span class="sxs-lookup"><span data-stu-id="f4de9-282">You can now save and run the experiment.</span></span> <span data-ttu-id="f4de9-283">Klicken Sie im Menü am unteren Rand der Seite klicken Sie auf die **speichern** Schaltfläche, um das Experiment speichern und dann auf **ausführen** an den Anfang des Experiments.</span><span class="sxs-lookup"><span data-stu-id="f4de9-283">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="f4de9-285">Sie sehen die **Status** des Experiments in der oberen rechten Rand des Zeichenbereichs.</span><span class="sxs-lookup"><span data-stu-id="f4de9-285">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="f4de9-286">Warten Sie einige Augenblicke, bis das Experiment aus, um den Vorgang abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-286">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="f4de9-287">Wenn eine große (real World) Dataset vorhanden ist, ist es wahrscheinlich, dass das Experiment Stunden in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="f4de9-287">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="f4de9-289">Klicken Sie mit der rechten Maustaste auf die **Evaluate Model** Element im Zeichenbereich und von der Kontext-Menü zeigen Sie die Maus über **Auswertungsergebnisse**, und wählen Sie dann **Visualize**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-289">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="f4de9-291">Die Ergebnisse der Auswertung werden mit die vorhergesagten Ergebnisse im Vergleich zu den tatsächlichen Ergebnissen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-291">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="f4de9-292">Dabei wird die 30 % des ursprünglichen Datasets, das zuvor, zum Auswerten des Modells geteilt wurde verwendet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-292">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="f4de9-293">Sie sehen, dass die Ergebnisse sind nicht toll, im Idealfall die höchste Anzahl in jeder Zeile haben würde das markierte Element in den Spalten sein.</span><span class="sxs-lookup"><span data-stu-id="f4de9-293">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="f4de9-295">Schließen der **Ergebnisse**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-295">Close the **Results**.</span></span>

24. <span data-ttu-id="f4de9-296">Um das neu trainierte Machine Learning-Modell zu verwenden, Sie sie als verfügbar machen müssen, eine **Webdienst**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-296">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="f4de9-297">Zu diesem Zweck klicken Sie auf die **Set Up Web Service** Menü Element im Menü am unteren Rand der Seite, und klicken Sie auf **Predictive Web Service**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-297">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="f4de9-299">Eine neue Registerkarte erstellt werden, und das trainingsmodell zusammengeführt, um den neuen Webdienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-299">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="f4de9-300">Klicken Sie im Menü am unteren Rand der Seite auf **speichern**, klicken Sie dann auf **ausführen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-300">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span><span data-ttu-id="f4de9-301"> Sie sehen, dass den Status aktualisiert, in der Ecke oben rechts neben dem experimentbereich befindet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-301"> You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="f4de9-303">Nachdem sie ausgeführt, wurde eine **Deploy Web Service** Schaltfläche am unteren Rand der Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-303">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="f4de9-304">Sie können den Webdienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-304">You are ready to deploy the web service.</span></span> <span data-ttu-id="f4de9-305">Klicken Sie auf **Deploy Web Service** (klassisch) im Menü am unteren Rand der Seite.</span><span class="sxs-lookup"><span data-stu-id="f4de9-305">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="f4de9-307">Ihrem Browser unter Umständen aufgefordert, um ein Popup, ermöglichen das sollten Sie **ermöglichen**, müssen Sie unter Umständen, drücken **Deploy Web Service** erneut, wenn die Seite "Deploy" nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f4de9-307">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="f4de9-308">Nach dem Erstellen des Experiments gelangen Sie zu einer **Dashboard** Seite, in dem Sie müssen, Ihre **API-Schlüssel** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-308">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="f4de9-309">Kopieren Sie sie in einen Editor für den Moment, benötigen Sie es in Ihrem Code sehr bald.</span><span class="sxs-lookup"><span data-stu-id="f4de9-309">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="f4de9-310">Wenn Sie Ihren API-Schlüssel notiert haben, klicken Sie auf die **ANFORDERUNGS-/Antwort** Schaltfläche der **Default Endpoint** Abschnitt unter dem Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="f4de9-310">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="f4de9-312">Wenn Sie Tests auf dieser Seite klicken, werden Sie Lage, Daten einzugeben, und die Ausgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-312">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="f4de9-313">Geben Sie die **Tag** und **Stunde**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-313">Enter the **day** and **hour**.</span></span> <span data-ttu-id="f4de9-314">Lassen Sie die **Produkt** Eintrag leer.</span><span class="sxs-lookup"><span data-stu-id="f4de9-314">Leave the **product** entry blank.</span></span> <span data-ttu-id="f4de9-315">Klicken Sie dann auf die **bestätigen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f4de9-315">Then click the **Confirm** button.</span></span><span data-ttu-id="f4de9-316"> Die Ausgabe am unteren Rand der Seite zeigt den JSON-Code, der die Wahrscheinlichkeit, dass jedes Produkt werden die Wahl darstellt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-316"> The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="f4de9-317">Eine neue Webseite wird, geöffnet und zeigt die Anweisungen und Beispiele, über die Anforderung-Struktur, die erforderlich sind, indem das Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="f4de9-317">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="f4de9-318">Kopieren der **Anforderungs-URI** auf dieser Seite in Ihrem Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-318">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="f4de9-320">Sie haben jetzt ein Machine learning-System, das zeigt das wahrscheinlichste Produkt verkauft werden gemäß Erwerb Verlaufsdaten, die Korrelation mit der Uhrzeit und den Tag des Jahres erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-320">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="f4de9-321">Um den Webdienst aufrufen zu können, benötigen Sie die URL für den Dienstendpunkt und einen API-Schlüssel für den Dienst.</span><span class="sxs-lookup"><span data-stu-id="f4de9-321">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="f4de9-322">Klicken Sie auf die **Consume** Registerkarte im oberen Menü aus.</span><span class="sxs-lookup"><span data-stu-id="f4de9-322">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="f4de9-323">Die **Verbrauch** Seite "Info" zeigt die Informationen, die Sie benötigen zum Aufrufen des Webdiensts aus Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="f4de9-323">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="f4de9-324">Kopieren Sie die **Primärschlüssel** und **Anforderung / Antwort** URL.</span><span class="sxs-lookup"><span data-stu-id="f4de9-324">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="f4de9-325">Sie benötigen diese im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="f4de9-325">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="f4de9-326">Kapitel 5 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f4de9-326">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="f4de9-327">Richten Sie ein und Testen Sie Ihrer Mixed Reality Kopfhörer Immersive.</span><span class="sxs-lookup"><span data-stu-id="f4de9-327">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="f4de9-328">Sie **nicht** Motion-Controller für dieses Kurses erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f4de9-328">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="f4de9-329">Wenn Sie die Einrichtung der Immersive Kopfhörer unterstützen müssen, klicken Sie auf [hier](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="f4de9-329">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="f4de9-330">Open **Unity** , und erstellen Sie ein neues Unity-Projekt namens **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="f4de9-330">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="f4de9-331">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-331">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="f4de9-332">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-332">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f4de9-333">Wechseln Sie zu ***bearbeiten* > *Voreinstellungen*** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-333">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f4de9-334">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-334">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f4de9-335">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="f4de9-335">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="f4de9-336">Öffnen Sie als Nächstes ***Datei* > *Buildeinstellungen*** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die ***Plattform wechseln*** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f4de9-336">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="f4de9-337">Außerdem stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="f4de9-337">Also make sure that:</span></span>

    1.  <span data-ttu-id="f4de9-338">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-338">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="f4de9-339">Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="f4de9-339">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="f4de9-340">**Buildtyp** nastaven NA hodnotu **D3D**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-340">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="f4de9-341">**SDK** nastaven NA hodnotu **zuletzt installierte**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-341">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="f4de9-342">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-342">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="f4de9-343">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-343">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="f4de9-344">Aber keine Sorge, über das Einrichten von **Szenen** jetzt, da diese später bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-344">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="f4de9-345">Die übrigen Einstellungen sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="f4de9-345">The remaining settings should be left as default for now.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="f4de9-347">In der **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-347">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="f4de9-348">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="f4de9-348">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="f4de9-349">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="f4de9-349">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f4de9-350">**Scripting** **Laufzeitversion** muss **experimentell** (.NET 4.6 Äquivalent)</span><span class="sxs-lookup"><span data-stu-id="f4de9-350">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="f4de9-351">**Back-End-Scripting** muss ***.NET***</span><span class="sxs-lookup"><span data-stu-id="f4de9-351">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="f4de9-352">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="f4de9-352">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="f4de9-354">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-354">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="f4de9-355">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f4de9-355">**InternetClient**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="f4de9-357">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  wird hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="f4de9-357">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="f4de9-359">Im **Buildeinstellungen** *Unity C#*  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="f4de9-359">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="f4de9-360">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="f4de9-360">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="f4de9-361">Speichern Sie das Projekt (**Datei > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="f4de9-361">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="f4de9-362">Kapitel 6: Importieren des MLProducts Unity-Pakets</span><span class="sxs-lookup"><span data-stu-id="f4de9-362">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="f4de9-363">Für diesen Kurs, müssen Sie ein Unity Asset-Paket namens herunterladen [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="f4de9-363">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="f4de9-364">Dieses Paket ist mit einer Szene mit allen Objekten in das vordefinierte, daher können Sie sich auf die erste es alles funktioniert.</span><span class="sxs-lookup"><span data-stu-id="f4de9-364">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="f4de9-365">Die **ShelfKeeper** Skript angegeben wird, enthält jedoch nur die öffentlichen Variablen, für die Szene-Setup-Struktur.</span><span class="sxs-lookup"><span data-stu-id="f4de9-365">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="f4de9-366">Sie müssen Sie alle anderen Abschnitte.</span><span class="sxs-lookup"><span data-stu-id="f4de9-366">You will need to do all other sections.</span></span> 

<span data-ttu-id="f4de9-367">Um dieses Paket zu importieren:</span><span class="sxs-lookup"><span data-stu-id="f4de9-367">To import this package:</span></span>

1.  <span data-ttu-id="f4de9-368">Mit dem Sie Unity-Dashboard, klicken Sie auf **Assets** klicken Sie dann im Menü am oberen Rand des Bildschirms auf **Import Package, das benutzerdefinierte Paket**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-368">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="f4de9-370">Verwenden Sie die Dateiauswahl zum Auswählen der **Azure-MR-307.unitypackage** packen, und klicken Sie auf **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-370">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="f4de9-371">Eine Liste der Komponenten für dieses Medienobjekt wird Ihnen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-371">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="f4de9-372">Bestätigen Sie den Import, indem Sie auf **importieren**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-372">Confirm the import by clicking **Import**.</span></span>

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="f4de9-374">Sobald er abgeschlossen ist, importieren, werden Sie sehen, dass einige neue Ordner in Ihrem Unity Anmeldeinformationsdialogfeld **Projektfenster**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-374">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="f4de9-375">Dies sind die-3D-Modelle und die jeweiligen Materialien, die Teil der Szene vorgefertigte, an denen Sie arbeiten werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-375">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="f4de9-376">Schreiben Sie den Großteil des Codes in diesem Kurs.</span><span class="sxs-lookup"><span data-stu-id="f4de9-376">You will write the majority of the code in this course.</span></span>

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="f4de9-378">In der **Projektfenster** Ordner, klicken Sie auf die **Szenen** Ordner und doppelklicken klicken Sie auf die Szene in (namens **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="f4de9-378">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="f4de9-379">Die Szene wird geöffnet (siehe Abbildung unten).</span><span class="sxs-lookup"><span data-stu-id="f4de9-379">The scene will open (see image below).</span></span> <span data-ttu-id="f4de9-380">Wenn die roten Rauten fehlt, klicken Sie einfach auf die **Gizmos** oben die Schaltfläche rechts von der **Spiel Bereich**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-380">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="f4de9-382">Kapitel 7 – überprüfen die DLLs in Unity</span><span class="sxs-lookup"><span data-stu-id="f4de9-382">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="f4de9-383">Um die Verwendung der JSON-Bibliotheken (verwendet für die Serialisierung und Deserialisierung) nutzen zu können, wurde ein Newtonsoft-DLL mit dem Paket implementiert, die Sie in weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-383">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="f4de9-384">Die Bibliothek sollten die ordnungsgemäße Konfiguration verfügen, wäre es prüfen, ob (insbesondere, wenn Sie Probleme mit Code nicht funktioniert haben).</span><span class="sxs-lookup"><span data-stu-id="f4de9-384">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="f4de9-385">Gehen Sie hierzu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="f4de9-385">To do so:</span></span>

-  <span data-ttu-id="f4de9-386">Klicken Sie auf die Newtonsoft-Datei in den Ordner "Plug-Ins" aus, und sehen Sie sich die **Inspektor Bereich**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-386">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="f4de9-387">Stellen Sie sicher, dass **Any Platform** ist.</span><span class="sxs-lookup"><span data-stu-id="f4de9-387">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="f4de9-388">Wechseln Sie zu der **UWP Registerkarte** und vergewissern Sie sich außerdem **nicht verarbeiten** ist.</span><span class="sxs-lookup"><span data-stu-id="f4de9-388">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importieren die DLLs in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="f4de9-390">Kapitel 8 – erstellen Sie die ShelfKeeper-Klasse</span><span class="sxs-lookup"><span data-stu-id="f4de9-390">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="f4de9-391">Die **ShelfKeeper** Klasse hostet, Methoden, die die Benutzeroberfläche und die Produkte, die in der Szene erzeugt steuern.</span><span class="sxs-lookup"><span data-stu-id="f4de9-391">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="f4de9-392">Als Teil des importierten Paket werden Sie diese Klasse stellt erhalten haben, obwohl dies nicht zutrifft.</span><span class="sxs-lookup"><span data-stu-id="f4de9-392">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="f4de9-393">Jetzt ist es Zeit zum Abschließen dieser Klasse:</span><span class="sxs-lookup"><span data-stu-id="f4de9-393">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="f4de9-394">Einen Doppelklick auf die **ShelfKeeper** Skript zu erstellen, in der **Skripts** Ordner, öffnen Sie ihn mit **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-394">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="f4de9-395">Der gesamte Code in das Skript mit den folgenden Code, der legt das Datum und die und verfügt über eine Methode zum Anzeigen eines Produkts vorhandene zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-395">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="f4de9-396">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-396">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="f4de9-397">Zurück im Unity-Editor, überprüfen Sie, ob die **ShelfKeeper** Klasse sieht wie der unten:</span><span class="sxs-lookup"><span data-stu-id="f4de9-397">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Erstellen Sie die ShelfKeeper-Klasse](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="f4de9-399">Wenn das Skript keinen Verweis Ziele (d. h. *Datum (Text-Mesh)*), ziehen Sie einfach die entsprechenden Objekte in der **Hierarchie Bereich**, in die Zielfelder.</span><span class="sxs-lookup"><span data-stu-id="f4de9-399">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="f4de9-400">Finden Sie weiter unten erläutert, bei Bedarf:</span><span class="sxs-lookup"><span data-stu-id="f4de9-400">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="f4de9-401">Öffnen der **Spawn Punkt** im array der **ShelfKeeper** Komponentenskript, indem sie mit der linken Maustaste.</span><span class="sxs-lookup"><span data-stu-id="f4de9-401">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="f4de9-402">Ein Unterbereich angezeigt namens **Größe**, die die Größe des Arrays angibt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-402">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="f4de9-403">Typ **3** in das Textfeld neben **Größe** , und drücken Sie **EINGABETASTE**, und unter drei Slots erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-403">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="f4de9-404">In der **Hierarchie** erweitern Sie die **Zeitanzeige** Objekt (durch den Pfeil neben dem mit der linken Maustaste).</span><span class="sxs-lookup"><span data-stu-id="f4de9-404">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="f4de9-405">Klicken Sie dann auf die ***Main Camera*** innerhalb der **Hierarchie**, sodass die **Inspektor** zeigt die Informationen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-405">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="f4de9-406">Wählen Sie die **Hauptkamera** in die **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-406">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="f4de9-407">Ziehen Sie die **Datum** und **Zeit** Objekte aus der **Hierarchie Bereich** auf die **-Textformat** und **Wenn Text** Slots innerhalb der **Inspektor** von der **Main Camera** in die **ShelfKeeper** Komponente.</span><span class="sxs-lookup"><span data-stu-id="f4de9-407">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="f4de9-408">Ziehen Sie die **Spawn Punkte** aus der **Hierarchie Bereich** (unter der *Regal* Objekt), die **3** **Element**verweisen Ziele unterhalb der **Spawn Punkt** array, da in der Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-408">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Erstellen Sie die ShelfKeeper-Klasse](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="f4de9-410">Kapitel 9 – erstellen Sie die ProductPrediction-Klasse</span><span class="sxs-lookup"><span data-stu-id="f4de9-410">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="f4de9-411">Die nächste Klasse, die Sie erstellen wollen ist die **ProductPrediction** Klasse.</span><span class="sxs-lookup"><span data-stu-id="f4de9-411">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="f4de9-412">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="f4de9-412">This class is responsible for:</span></span>

-   <span data-ttu-id="f4de9-413">Abfragen der **Machine Learning-Dienst** Instanz, die das aktuelle Datum und eine Uhrzeit angeben.</span><span class="sxs-lookup"><span data-stu-id="f4de9-413">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="f4de9-414">Deserialisiert die JSON-Antwort in nutzbare Daten.</span><span class="sxs-lookup"><span data-stu-id="f4de9-414">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="f4de9-415">Interpretieren von Daten, die 3 empfohlene Produkte abrufen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-415">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="f4de9-416">Aufrufen der **ShelfKeeper** -Klassenmethoden, um die Daten in der Szene anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-416">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="f4de9-417">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-417">To create this class:</span></span>

1.  <span data-ttu-id="f4de9-418">Wechseln Sie zu der **Skripts** Ordner, in der **Projektfenster**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-418">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="f4de9-419">Mit der rechten Maustaste in den Ordner **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-419">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="f4de9-420">Rufen Sie das Skript **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-420">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="f4de9-421">Doppelklicken Sie auf dem neuen **ProductPrediction** Skript öffnen Sie ihn mit **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-421">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="f4de9-422">Wenn die **Datei Dateiänderung festgestellt** Dialogfeld erscheint, klicken Sie auf \***Projektmappe erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-422">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="f4de9-423">Fügen Sie am oberen Rand der ProductPrediction-Klasse die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="f4de9-423">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="f4de9-424">In der **ProductPrediction** Klasse fügen Sie die folgenden zwei Objekte, die sich aus einer Reihe von geschachtelten Klassen zusammensetzen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-424">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="f4de9-425">Diese Klassen werden zum Serialisieren und Deserialisieren des JSON-Codes für die Machine Learning-Dienst verwendet.</span><span class="sxs-lookup"><span data-stu-id="f4de9-425">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="f4de9-426">Fügen Sie dann die folgenden Variablen über dem vorherigen Code, (sodass der JSON-Code im Zusammenhang, dass Code unten auf der das Skript unter allen anderen Code, und aus dem Weg ist):</span><span class="sxs-lookup"><span data-stu-id="f4de9-426">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f4de9-427">Achten Sie darauf, fügen Sie der **Primärschlüssel** und **Anforderung / Antwort-Endpunkt**, aus der Machine Learning-Portal, in der Variablen hier.</span><span class="sxs-lookup"><span data-stu-id="f4de9-427">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="f4de9-428">Die unterhalb des Images angezeigt, in dem Sie den Schlüssel und Endpunkt von erforderlich gewesen wäre.</span><span class="sxs-lookup"><span data-stu-id="f4de9-428">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="f4de9-431">Fügen Sie diesen Code innerhalb der **Start()** Methode.</span><span class="sxs-lookup"><span data-stu-id="f4de9-431">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="f4de9-432">Die **Start()** Methode wird aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="f4de9-432">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="f4de9-433">Im folgenden finden die Methode, die erfasst das Datum und Uhrzeit von Windows und konvertiert es in ein Format, die von unseren Machine Learning-Experiment verwenden können, mit den in der Tabelle gespeicherten Daten verglichen werden soll.</span><span class="sxs-lookup"><span data-stu-id="f4de9-433">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="f4de9-434">Sie können **löschen** der **Update()** Methode, da diese Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f4de9-434">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="f4de9-435">Fügen Sie die folgende Methode wird das aktuelle Datum und die Uhrzeit an den Machine Learning-Endpunkt zu kommunizieren, und erhalten eine Antwort im JSON-Format hinzu.</span><span class="sxs-lookup"><span data-stu-id="f4de9-435">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="f4de9-436">Fügen Sie die folgende Methode, die verantwortlich für das Deserialisieren der JSON-Antwort und das Ergebnis der Deserialisierung in der Kommunikation ist die **ShelfKeeper** Klasse.</span><span class="sxs-lookup"><span data-stu-id="f4de9-436">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="f4de9-437">Dieses Ergebnis werden die Namen der drei Elemente vorhergesagt, dass Sie um am meisten am aktuellen Datum und Uhrzeit zu verkaufen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-437">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="f4de9-438">Fügen Sie den folgenden Code in die **ProductPrediction** -Klasse, unter der vorherigen Methode.</span><span class="sxs-lookup"><span data-stu-id="f4de9-438">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="f4de9-439">Speichern Sie **Visual Studio** und navigieren Sie wieder zum **Unity**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-439">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="f4de9-440">Ziehen Sie die **ProductPrediction** Klasse-Skript aus der **Skript** Ordner, auf die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-440">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="f4de9-441">Speichern Sie Ihre Szene und das Projekt **Datei** > ***Szene speichern* / *Datei***   >  **Projekt speichern**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-441">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="f4de9-442">Kapitel 10 – erstellen Sie die UWP-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="f4de9-442">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="f4de9-443">Es ist nun Zeit, Ihr Projekt als UWP-Lösung zu erstellen, damit es als eigenständige Anwendung ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f4de9-443">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="f4de9-444">So erstellen Sie:</span><span class="sxs-lookup"><span data-stu-id="f4de9-444">To Build:</span></span>

1.  <span data-ttu-id="f4de9-445">Speichern Sie durch Klicken auf die aktuelle Szene **Datei** **speichern Szenen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-445">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="f4de9-446">Wechseln Sie zu **Datei** **Buildeinstellungen**</span><span class="sxs-lookup"><span data-stu-id="f4de9-446">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="f4de9-447">Aktivieren Sie das Kontrollkästchen namens **Unity C\# Projekte** (Dies ist wichtig, da er kann Sie die Klassen zu bearbeiten, nachdem der Build abgeschlossen ist).</span><span class="sxs-lookup"><span data-stu-id="f4de9-447">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="f4de9-448">Klicken Sie auf **Hinzufügen von Open Szenen**,</span><span class="sxs-lookup"><span data-stu-id="f4de9-448">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="f4de9-449">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-449">Click **Build**.</span></span>

    ![Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="f4de9-451">Sie werden aufgefordert werden, um den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="f4de9-451">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="f4de9-452">Erstellen Sie eine **erstellt** Ordner, und erstellen Sie einen anderen Ordner in diesem Ordner mit einem entsprechenden Namen Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="f4de9-452">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="f4de9-453">Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, um den Build an diesem Speicherort zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-453">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab7-55.png)

    ![Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="f4de9-456">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="f4de9-456">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="f4de9-457">Kapitel 11 – Ihre Anwendung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-457">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="f4de9-458">Um die Anwendung bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-458">To deploy your application:</span></span>

1.  <span data-ttu-id="f4de9-459">Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-459">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="f4de9-460">Mit Visual Studio öffnen müssen Sie NuGet-Pakete wiederherstellen, die ausgeführt werden kann, mit der rechten Maustaste in der Projektmappe MachineLearningLab_Build Projektmappen-Explorer (rechts neben Visual Studio gefunden), und klicken Sie dann auf NuGet-Pakete wiederherstellen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-460">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="f4de9-462">In der Projektmappenkonfiguration Select **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-462">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="f4de9-463">Wählen Sie in der Plattform für die Projektmappe **X86**, **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="f4de9-463">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="f4de9-464">Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="f4de9-464">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f4de9-465">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f4de9-465">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f4de9-466">Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="f4de9-466">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f4de9-467">Stellen Sie sicher **Entwicklermodus** ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.</span><span class="sxs-lookup"><span data-stu-id="f4de9-467">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="f4de9-469">Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihren PC.</span><span class="sxs-lookup"><span data-stu-id="f4de9-469">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="f4de9-470">Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-470">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="f4de9-471">Wenn Sie die Mixed Reality-Anwendung ausführen, sehen Sie die Bench, die in Ihrer Unity-Szene eingerichtet wurde, und von Initialisierung, die Daten, die Sie in Azure eingerichtet werden abgerufen.</span><span class="sxs-lookup"><span data-stu-id="f4de9-471">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="f4de9-472">Deserialisiert die Daten in Ihrer Anwendung, und die ersten drei Ergebnisse für Ihre aktuellen Datum und Uhrzeit werden als drei Modelle für die Bench visuell bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f4de9-472">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="f4de9-473">Der fertigen Machine Learning-Anwendung</span><span class="sxs-lookup"><span data-stu-id="f4de9-473">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="f4de9-474">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Azure Machine Learning Daten Vorhersagen machen, und zeigen Sie es in Ihrer Szene nutzt.</span><span class="sxs-lookup"><span data-stu-id="f4de9-474">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="f4de9-476">Übung</span><span class="sxs-lookup"><span data-stu-id="f4de9-476">Exercise</span></span>

<span data-ttu-id="f4de9-477">**Übung 1**</span><span class="sxs-lookup"><span data-stu-id="f4de9-477">**Exercise 1**</span></span>

<span data-ttu-id="f4de9-478">Experimentieren Sie mit der Sortierreihenfolge nach Ihrer Anwendung, und haben Sie die drei unteren Vorhersagen im Regal, angezeigt werden, wie diese Daten möglicherweise auch Interesse sein könnte.</span><span class="sxs-lookup"><span data-stu-id="f4de9-478">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="f4de9-479">**Übung 2**</span><span class="sxs-lookup"><span data-stu-id="f4de9-479">**Exercise 2**</span></span>

<span data-ttu-id="f4de9-480">Mithilfe von **Azure-Tabellen** eine neue Tabelle mit Wetterdaten füllen, und erstellen Sie ein neues Experiment unter Verwendung der Daten.</span><span class="sxs-lookup"><span data-stu-id="f4de9-480">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
