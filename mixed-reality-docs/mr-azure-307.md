---
title: Mr und Azure 307-Machine Learning
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Machine Learning Studio in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Machine Learning, ml, Machine Learning Studio, hololens, immersive, VR
ms.openlocfilehash: c86c592573dd39d926869d8cce6025fa264cc90f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437924"
---
>[!NOTE]
><span data-ttu-id="c4a30-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c4a30-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c4a30-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c4a30-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="c4a30-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c4a30-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c4a30-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="c4a30-110">Mr und Azure 307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="c4a30-110">MR and Azure 307: Machine learning</span></span>

![Endgültiges Produkt-Start](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="c4a30-112">In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Machine Learning Studio Machine Learning (ml)-Funktionen zu einer gemischten Reality-Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="c4a30-113">*Azure Machine Learning Studio* ist ein Microsoft-Dienst, der Entwicklern eine große Anzahl von Machine Learning-Algorithmen bereitstellt, die Ihnen bei der Eingabe, Ausgabe, Vorbereitung und Visualisierung von Daten helfen können.</span><span class="sxs-lookup"><span data-stu-id="c4a30-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="c4a30-114">Aus diesen Komponenten ist es dann möglich, ein Predictive Analytics Experiment zu entwickeln, zu durchlaufen und es zum Trainieren des Modells zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="c4a30-115">Im Anschluss an die Schulung können Sie das Modell in der Azure-Cloud funktionstüchtig machen, damit es neue Daten bewerten kann.</span><span class="sxs-lookup"><span data-stu-id="c4a30-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="c4a30-116">Weitere Informationen finden Sie auf der [Seite Azure Machine Learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="c4a30-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="c4a30-117">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die die folgenden Aktionen durchführt:</span><span class="sxs-lookup"><span data-stu-id="c4a30-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="c4a30-118">Stellen Sie eine Tabelle mit Umsatzdaten für das *Azure Machine Learning Studio* Portal bereit, und entwerfen Sie einen Algorithmus, um zukünftige Umsätze beliebter Artikel vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="c4a30-119">Erstellen Sie ein **Unity-Projekt**, das Vorhersagedaten vom ml-Dienst empfangen und interpretieren kann.</span><span class="sxs-lookup"><span data-stu-id="c4a30-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="c4a30-120">Zeigen Sie die prädikationsdaten visuell im **Unity-Projekt**an, indem Sie die beliebtesten Verkaufs Elemente in einem Regal bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="c4a30-121">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="c4a30-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c4a30-122">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="c4a30-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c4a30-123">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="c4a30-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="c4a30-124">Dieser Kurs ist ein eigenständiges Tutorial, das sich nicht direkt mit anderen Mixed Reality-Labs befasst.</span><span class="sxs-lookup"><span data-stu-id="c4a30-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="c4a30-125">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="c4a30-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c4a30-126">Natürlich</span><span class="sxs-lookup"><span data-stu-id="c4a30-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c4a30-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c4a30-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c4a30-128"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="c4a30-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c4a30-129">Mr und Azure 307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="c4a30-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4a30-130">✔️</span><span class="sxs-lookup"><span data-stu-id="c4a30-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4a30-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c4a30-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c4a30-132">Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="c4a30-133">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="c4a30-134">Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.</span><span class="sxs-lookup"><span data-stu-id="c4a30-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4a30-135">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c4a30-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c4a30-136">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c4a30-137">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="c4a30-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c4a30-138">Sie können die neueste Software verwenden, die im [Artikel Installieren der Tools](install-the-tools.md)aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="c4a30-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c4a30-139">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="c4a30-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c4a30-140">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="c4a30-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c4a30-141">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="c4a30-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c4a30-142">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c4a30-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c4a30-143">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="c4a30-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c4a30-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c4a30-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c4a30-145">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="c4a30-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c4a30-146">Internet Zugriff für Azure-Setup und ml-Datenabruf</span><span class="sxs-lookup"><span data-stu-id="c4a30-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c4a30-147">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="c4a30-147">Before you start</span></span>

<span data-ttu-id="c4a30-148">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="c4a30-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="c4a30-149">Kapitel 1: Einrichten des Azure Storage Kontos</span><span class="sxs-lookup"><span data-stu-id="c4a30-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="c4a30-150">Um die Azure Translator-API zu verwenden, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="c4a30-151">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="c4a30-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c4a30-152">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c4a30-153">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c4a30-154">Wenn Sie angemeldet sind, klicken Sie im linken Menü auf **Speicher Konten** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="c4a30-156">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="c4a30-157">Klicken Sie auf der Registerkarte **Speicher Konten** auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="c4a30-159">Im Bereich **Speicherkonto erstellen** :</span><span class="sxs-lookup"><span data-stu-id="c4a30-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="c4a30-160">Fügen Sie einen **Namen** für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="c4a30-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="c4a30-161">Wählen Sie **unter Bereitstellungs Modell** die Option **Resource Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="c4a30-162">Wählen Sie unter **Kontoart**die Option **Speicher (universell, Version v1)** aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="c4a30-163">Wählen Sie für **Leistung**die Option **Standard**aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="c4a30-164">Wählen Sie für die **Replikation** den **georedundanten Speicher mit Lesezugriff (RA-GRS)** aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="c4a30-165">Lassen Sie die Option " **sichere Übertragung erforderlich** " **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="c4a30-166">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="c4a30-167">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c4a30-168">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c4a30-169">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c4a30-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="c4a30-170">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c4a30-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="c4a30-171">Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="c4a30-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c4a30-172">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c4a30-173">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c4a30-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="c4a30-174">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="c4a30-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="c4a30-176">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="c4a30-177">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="c4a30-179">Kapitel 2: der Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="c4a30-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="c4a30-180">Um das *Azure Machine Learning*verwenden zu können, müssen Sie eine Instanz des Machine Learning Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="c4a30-181">Klicken Sie im Azure-Portal in der oberen linken Ecke auf " **neu** ", und suchen Sie nach **Machine Learning Studio Arbeitsbereich**, und drücken **Sie die Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="c4a30-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="c4a30-183">Auf der neuen Seite wird eine Beschreibung des **Machine Learning Studio Arbeits** Bereichs Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="c4a30-184">Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="c4a30-185">Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt, in dem Sie einige Details über den neuen **Machine Learning Studio Dienst**angeben müssen:</span><span class="sxs-lookup"><span data-stu-id="c4a30-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="c4a30-186">Fügen Sie den gewünschten **Arbeitsbereichs Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="c4a30-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="c4a30-187">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="c4a30-188">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c4a30-189">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c4a30-190">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c4a30-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c4a30-191">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c4a30-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="c4a30-192">Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="c4a30-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c4a30-193">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c4a30-194">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c4a30-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="c4a30-195">Sie sollten die gleiche Ressourcengruppe verwenden, die Sie zum Erstellen des Azure Storage im vorherigen Kapitel verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="c4a30-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="c4a30-196">Klicken Sie im Bereich **Speicherkonto** auf **vorhandene verwenden**, klicken Sie dann auf das Dropdown Menü, und klicken Sie dann auf das **Speicherkonto** , das Sie im letzten Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c4a30-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="c4a30-197">Wählen Sie im Dropdown Menü den entsprechenden Tarif des **Arbeits** Bereichs für Sie aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="c4a30-198">Klicken Sie im Abschnitt **Webdienst Plan** auf neu **Erstellen** **, und** fügen Sie dann einen Namen für die Datei in das Textfeld ein.</span><span class="sxs-lookup"><span data-stu-id="c4a30-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="c4a30-199">Wählen Sie im Abschnitt **Tarif des Webdienst** Tarifs den Tarif Ihrer Wahl aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="c4a30-200">Eine Entwicklungs Test Ebene mit dem Namen **devtest Standard** sollte Ihnen kostenlos zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="c4a30-201">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="c4a30-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="c4a30-202">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-202">Click **Create**.</span></span>

        ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="c4a30-204">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="c4a30-205">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="c4a30-207">Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-207">Click on the notification to explore your new Service instance.</span></span>

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="c4a30-209">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="c4a30-210">Klicken Sie auf der angezeigten Seite im Abschnitt **zusätzliche Links** auf **Machine Learning Studio starten**, um den Browser zum **Machine Learning Studio** Portal zu leiten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="c4a30-212">Verwenden Sie die Schaltfläche **Anmelden** oben rechts oder in der Mitte, um sich bei Ihrem Machine Learning Studio anzumelden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="c4a30-214">Kapitel 3: die Machine Learning Studio: DataSet-Setup</span><span class="sxs-lookup"><span data-stu-id="c4a30-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="c4a30-215">Eine der Möglichkeiten Machine Learning Algorithmen besteht darin, vorhandene Daten zu analysieren und dann basierend auf dem vorhandenen DataSet zu versuchen, zukünftige Ergebnisse vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="c4a30-216">Dies bedeutet im Allgemeinen, dass die vorhandenen Daten, umso besser der Algorithmus ist, um zukünftige Ergebnisse vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="c4a30-217">Sie erhalten für diesen Kurs eine Beispiel Tabelle mit dem Namen [productstablecsv und können hier heruntergeladen werden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="c4a30-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4a30-218">Die obige ZIP-Datei enthält sowohl **productstablecsv** als auch das **. unitypackage**, das Sie in [Kapitel 6](#chapter-6---importing-the-mlproducts-unity-package)benötigen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="c4a30-219">Dieses Paket wird auch in diesem Kapitel bereitgestellt, jedoch getrennt von der CSV-Datei.</span><span class="sxs-lookup"><span data-stu-id="c4a30-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="c4a30-220">Dieses Beispiel DataSet enthält einen Datensatz der am besten verkauften Objekte für jede Stunde des Jahres 2017.</span><span class="sxs-lookup"><span data-stu-id="c4a30-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="c4a30-222">Beispielsweise war am Tag 1 von 2017 bei 1 Uhr (Stunde 13) das am besten verkaufte Element Salt und Pepper.</span><span class="sxs-lookup"><span data-stu-id="c4a30-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="c4a30-223">Diese Beispiel Tabelle enthält 9998 Einträge.</span><span class="sxs-lookup"><span data-stu-id="c4a30-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="c4a30-224">Wechseln Sie zurück zum **Machine Learning Studio** -Portal, und fügen Sie diese Tabelle als **DataSet** für Ihr ml hinzu.</span><span class="sxs-lookup"><span data-stu-id="c4a30-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="c4a30-225">Klicken Sie hierzu auf die Schaltfläche **+ neu** in der unteren linken Ecke des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="c4a30-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="c4a30-227">Ein Abschnitt wird von unten nach oben angezeigt, und darin befindet sich auf der linken Seite ein Navigations Panel.</span><span class="sxs-lookup"><span data-stu-id="c4a30-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="c4a30-228">Klicken Sie dann auf das **DataSet**, und klicken Sie dann auf die **lokale Datei**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="c4a30-230">Laden Sie das neue **DataSet** hoch, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="c4a30-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="c4a30-231">Das Fenster hochladen wird angezeigt, in dem Sie die Festplatte nach dem neuen DataSet **Durchsuchen** können.</span><span class="sxs-lookup"><span data-stu-id="c4a30-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="c4a30-233">Wenn Sie diese Option ausgewählt haben und wieder im Fenster Upload angezeigt werden, lassen Sie das Kontrollkästchen deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="c4a30-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="c4a30-234">Geben Sie im Textfeld unten den Namen **productstablecsv. CSV** als Namen für das Dataset ein (wird jedoch automatisch hinzugefügt).</span><span class="sxs-lookup"><span data-stu-id="c4a30-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="c4a30-235">Wählen Sie im Dropdown Menü für **Typ**die Option **generische CSV-Datei mit einem Header (. CSV)** aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="c4a30-236">Drücken Sie unten rechts im Uploadfenster den Tick, und das **DataSet** wird hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="c4a30-237">Kapitel Machine Learning Studio 4: das Experiment</span><span class="sxs-lookup"><span data-stu-id="c4a30-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="c4a30-238">Bevor Sie Ihr Machine Learning-System erstellen können, müssen Sie ein Experiment erstellen, um Ihre Theorie zu Ihren Daten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="c4a30-239">Mit den Ergebnissen wissen Sie, ob Sie mehr Daten benötigen, oder ob es keine Korrelation zwischen den Daten und einem möglichen Ergebnis gibt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="c4a30-240">So beginnen Sie mit dem Erstellen eines Experiments:</span><span class="sxs-lookup"><span data-stu-id="c4a30-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="c4a30-241">Klicken Sie erneut auf die Schaltfläche **+ neu** unten links auf der Seite, und klicken Sie dann auf **Experiment** > **leeres Experiment**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="c4a30-243">Eine neue Seite wird mit einem leeren Experiment angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c4a30-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="c4a30-244">Erweitern Sie im linken Bereich **gespeicherte Datasets** > **meine Datasets** , und ziehen Sie **productstablecsv** auf den **Experiment**Bereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="c4a30-246">Erweitern Sie im Panel auf der linken Seite die Option **Data Transformation** > **Sample, und teilen**Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="c4a30-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="c4a30-247">Ziehen Sie dann das Element **Split Data** in in den **Experiment**Bereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="c4a30-248">Mit dem Split Data-Element wird das Dataset in zwei Teile aufgeteilt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="c4a30-249">Ein Teil, der zum Trainieren des Machine Learning-Algorithmus verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="c4a30-250">Der zweite Teil wird verwendet, um die Genauigkeit des generierten Algorithmus auszuwerten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="c4a30-252">Im rechten Bereich (während das geteilte Datenelement auf der Canvas ausgewählt ist), bearbeiten Sie den **Bruchteil der Zeilen im ersten Ausgabe DataSet** in **0,7**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="c4a30-253">Dadurch werden die Daten in zwei Teile aufgeteilt, der erste Teil ist 70% der Daten und der zweite Teil die verbleibenden 30%.</span><span class="sxs-lookup"><span data-stu-id="c4a30-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="c4a30-254">Vergewissern Sie sich, dass die Daten **nach dem Zufalls** Prinzip aufgeteilt werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="c4a30-256">Ziehen Sie eine Verbindung von der Basis des Elements **productstablecsv** in der Canvas an den oberen Rand des Elements Split Data.</span><span class="sxs-lookup"><span data-stu-id="c4a30-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="c4a30-257">Dadurch werden die Elemente verbunden, und die Ausgabe des Datasets **productstablecsv** (die Daten) wird an die unterteilte Dateneingabe gesendet.</span><span class="sxs-lookup"><span data-stu-id="c4a30-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="c4a30-259">Erweitern Sie im Bereich **Experimente** auf der linken Seite **Machine Learning** > **trainieren**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="c4a30-260">Ziehen Sie das Element **Train Model** in den Experiment Bereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="c4a30-261">Der Canvas sollte wie unten dargestellt aussehen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-261">Your canvas should look the same as the below.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="c4a30-263">Ziehen Sie ***unten links*** im Element " **Split Data** " eine Verbindung mit der **rechten oberen** Ecke des Moduls " **Train Model** ".</span><span class="sxs-lookup"><span data-stu-id="c4a30-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="c4a30-264">Die erste 70%-Aufteilung aus dem DataSet wird vom Train-Modell zum Trainieren des Algorithmus verwendet.</span><span class="sxs-lookup"><span data-stu-id="c4a30-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="c4a30-266">Wählen Sie das **Modellelement trainieren** im Zeichenbereich aus, und klicken Sie im **Eigenschaften** Panel (auf der rechten Seite Ihres Browserfensters) auf die Schaltfläche **Launch Column Selector** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="c4a30-267">Geben Sie im Textfeld **Product** ein, und drücken Sie dann die **Eingabe**Taste. *Product* wird als Spalte zum Trainieren von Vorhersagen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="c4a30-268">Klicken Sie anschließend auf den **Tick** in der unteren rechten Ecke, um das Auswahl Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="c4a30-270">Sie trainieren einen **MultiClass Logistic Regression** -Algorithmus, um das am häufigsten verkaufte **Produkt** basierend auf der Tageszeit und dem Datum vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="c4a30-271">Es geht über den Rahmen dieses Dokuments hinaus, die Details der verschiedenen Algorithmen zu erläutern, die von der Azure Machine Learning Studio bereitgestellt werden. Sie können jedoch weitere Informationen aus dem [Machine Learning algorithmusspickzettel](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="c4a30-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="c4a30-272">Erweitern Sie im Bereich Experiment Elemente auf der linken Seite **Machine Learning** > **initialisieren Sie Model** > **Classification**, und ziehen Sie das Element für die **mehr klassige logistische Regression** in den Experiment Bereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="c4a30-273">Verbinden Sie die Ausgabe vom Ende der **mehr klassigen logistischen Regression**mit der Eingabe oben links des **Train Model** -Elements.</span><span class="sxs-lookup"><span data-stu-id="c4a30-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="c4a30-275">Erweitern Sie in der Liste der Experiment Elemente im Panel auf der linken Seite **Machine Learning** > **Score**, und ziehen Sie das **Score Model** -Element auf den Zeichenbereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="c4a30-276">Verbinden Sie die Ausgabe vom unteren Rand des Trainings **Modells**mit der oberen linken Eingabe des Bewertungs **Modells**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="c4a30-277">Verbinden Sie die untere rechte Ausgabe von **Split Data**mit der oberen rechten Eingabe des **Score Model** -Elements.</span><span class="sxs-lookup"><span data-stu-id="c4a30-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="c4a30-279">Erweitern Sie in der Liste der **Experiment** Elemente im Panel auf der linken Seite **Machine Learning** > **Auswerten**, und ziehen Sie das **Modellelement auswerten** auf den Zeichenbereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="c4a30-280">Verbinden Sie die Ausgabe des Bewertungs **Modells** mit der oberen linken Eingabe des **evaluatormodells**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="c4a30-282">Sie haben ihr erstes Machine Learning Experiment erstellt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="c4a30-283">Sie können das Experiment jetzt speichern und ausführen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-283">You can now save and run the experiment.</span></span> <span data-ttu-id="c4a30-284">Klicken Sie im Menü unten auf der Seite auf die Schaltfläche **Speichern** , um das Experiment zu speichern, und klicken Sie dann auf **Ausführen** , um das Experiment zu starten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="c4a30-286">Sie können den **Status** des Experiments in der oberen rechten Ecke der Canvas sehen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="c4a30-287">Warten Sie einen Moment, bis das Experiment abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="c4a30-288">Wenn Sie über ein großes Dataset (Real World) verfügen, ist es wahrscheinlich, dass das Experiment mehrere Stunden dauern kann.</span><span class="sxs-lookup"><span data-stu-id="c4a30-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="c4a30-290">Klicken Sie mit der rechten Maustaste auf das **Modellelement auswerten** im Zeichenbereich, und zeigen Sie im Kontextmenü auf **Auswertungs Ergebnisse**, und wählen Sie dann **visualisieren**aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="c4a30-292">Die Auswertungs Ergebnisse werden angezeigt, die die vorhergesagten Ergebnisse im Vergleich zu den tatsächlichen Ergebnissen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="c4a30-293">Dabei werden die 30% des ursprünglichen Datasets, das zuvor geteilt wurde, zum Auswerten des Modells verwendet.</span><span class="sxs-lookup"><span data-stu-id="c4a30-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="c4a30-294">Sie sehen, dass die Ergebnisse nicht groß sind. Idealerweise haben Sie in jeder Zeile die höchste Zahl, die das markierte Element in den Spalten ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="c4a30-296">Schließen Sie die **Ergebnisse**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-296">Close the **Results**.</span></span>

24. <span data-ttu-id="c4a30-297">Um das neu trainierte Machine Learning Modell zu verwenden, müssen Sie es als **Webdienst**verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="c4a30-298">Klicken Sie hierzu im Menü unten auf der Seite auf das Menü Element **Set Up Web Service** , und klicken Sie auf **Predictive Web Service**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="c4a30-300">Es wird eine neue Registerkarte erstellt, und das Train-Modell wird zusammengeführt, um den neuen Webdienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="c4a30-301">Klicken Sie im Menü unten auf der Seite auf **Speichern**, und klicken Sie dann auf **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="c4a30-302">Der Status wird in der oberen rechten Ecke des Experiment Bereichs angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="c4a30-304">Nachdem die Ausführung abgeschlossen ist, wird unten auf der Seite die Schaltfläche " **Webdienst** bereitstellen" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="c4a30-305">Sie können den Webdienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="c4a30-306">Klicken Sie im Menü unten auf der Seite auf **Webdienst** bereitstellen (klassisch).</span><span class="sxs-lookup"><span data-stu-id="c4a30-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="c4a30-308">In Ihrem Browser werden Sie möglicherweise aufgefordert, ein Popup zuzulassen, das Sie **zulassen**sollten. Sie müssen jedoch möglicherweise erneut den **Webdienst** bereitstellen verwenden, wenn die Seite bereitstellen nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="c4a30-309">Nachdem das Experiment erstellt wurde, werden Sie zu einer **Dashboardseite** umgeleitet, auf der Sie Ihren **API-Schlüssel** anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="c4a30-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="c4a30-310">Kopieren Sie die Datei in einen Editor für den Moment. Sie benötigen Sie in Ihrem Code sehr bald.</span><span class="sxs-lookup"><span data-stu-id="c4a30-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="c4a30-311">Nachdem Sie Ihren API-Schlüssel notiert haben, klicken Sie auf die Schaltfläche " **Anforderung/Antwort** " im Abschnitt " **Standard Endpunkt** " unterhalb des Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="c4a30-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="c4a30-313">Wenn Sie auf dieser Seite auf "testen" klicken, können Sie Eingabedaten eingeben und die Ausgabe anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="c4a30-314">Geben Sie den **Tag** und die **Stunde**ein.</span><span class="sxs-lookup"><span data-stu-id="c4a30-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="c4a30-315">Lassen Sie den **Produkt** Eintrag leer.</span><span class="sxs-lookup"><span data-stu-id="c4a30-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="c4a30-316">Klicken Sie dann auf die Schaltfläche **bestätigen** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="c4a30-317">Die Ausgabe am unteren Rand der Seite zeigt den JSON-Code, der die Wahrscheinlichkeit für die einzelnen Produkte darstellt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="c4a30-318">Es wird eine neue Webseite geöffnet, auf der die Anweisungen und einige Beispiele zur Anforderungs Struktur angezeigt werden, die für die Machine Learning Studio erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="c4a30-319">Kopieren Sie den auf dieser Seite angezeigten **Anforderungs-URI** in den Editor.</span><span class="sxs-lookup"><span data-stu-id="c4a30-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="c4a30-321">Sie haben jetzt ein Machine Learning-System erstellt, das das wahrscheinlichste Produkt bereitstellt, das auf der Grundlage von Verlaufs Daten zu verkaufen ist, die mit der Tageszeit und dem Tag des Jahrs korreliert sind.</span><span class="sxs-lookup"><span data-stu-id="c4a30-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="c4a30-322">Um den Webdienst aufzurufen, benötigen Sie die URL für den Dienst Endpunkt und einen API-Schlüssel für den Dienst.</span><span class="sxs-lookup"><span data-stu-id="c4a30-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="c4a30-323">Klicken Sie im oberen Menü auf die Registerkarte **Verbrauch** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="c4a30-324">Auf der Seite " **Verbrauchs** Informationen" werden die Informationen angezeigt, die Sie benötigen, um den Webdienst aus Ihrem Code aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="c4a30-325">Erstellen Sie eine Kopie des **Primärschlüssels** und der **Anforderungs Antwort-** URL.</span><span class="sxs-lookup"><span data-stu-id="c4a30-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="c4a30-326">Sie benötigen diese im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="c4a30-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="c4a30-327">Kapitel 5: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="c4a30-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="c4a30-328">Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="c4a30-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="c4a30-329">Für diesen Kurs benötigen Sie **keine** Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="c4a30-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="c4a30-330">Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, klicken Sie [hier](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="c4a30-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="c4a30-331">Öffnen Sie **Unity** , und erstellen Sie ein neues Unity-Projekt mit dem Namen **Mr\_machinelearning.**</span><span class="sxs-lookup"><span data-stu-id="c4a30-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="c4a30-332">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="c4a30-333">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c4a30-334">Wechseln Sie zu Edit > **Preferences (Einstellungen** **Bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c4a30-335">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c4a30-336">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="c4a30-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="c4a30-337">Navigieren Sie als nächstes zu **Datei** > **Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche ***Plattform wechseln*** klicken.</span><span class="sxs-lookup"><span data-stu-id="c4a30-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="c4a30-338">Stellen Sie außerdem Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="c4a30-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="c4a30-339">Das **Zielgerät** ist auf **ein beliebiges Gerät**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="c4a30-340">Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.</span><span class="sxs-lookup"><span data-stu-id="c4a30-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="c4a30-341">Der **Buildtyp** ist auf **D3D**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="c4a30-342">**SDK** ist auf **zuletzt installiert**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="c4a30-343">Die **Visual Studio-Version** ist auf die **neueste installierte**Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="c4a30-344">**Build und Run** sind auf **lokaler Computer**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="c4a30-345">Machen Sie sich keine Gedanken über das Einrichten von **Szenen** , da diese später bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="c4a30-346">Die restlichen Einstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-346">The remaining settings should be left as default for now.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="c4a30-348">Klicken Sie im Fenster **Buildeinstellungen** auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="c4a30-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="c4a30-349">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="c4a30-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c4a30-350">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="c4a30-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c4a30-351">Die **Skript** **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="c4a30-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="c4a30-352">**Skript** -Back-End sollte ***.net*** sein</span><span class="sxs-lookup"><span data-stu-id="c4a30-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="c4a30-353">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="c4a30-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="c4a30-355">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c4a30-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="c4a30-356">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="c4a30-356">**InternetClient**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="c4a30-358">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, wird sichergestellt, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="c4a30-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="c4a30-360">Zurück in **Buildeinstellungen** : *Unity C#*  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="c4a30-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="c4a30-361">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="c4a30-362">Speichern Sie Ihr Projekt (**Datei > Projekt speichern**).</span><span class="sxs-lookup"><span data-stu-id="c4a30-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="c4a30-363">Kapitel 6: Importieren des Unity-Pakets "mlproducts"</span><span class="sxs-lookup"><span data-stu-id="c4a30-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="c4a30-364">Für diesen Kurs müssen Sie ein Unity-Ressourcenpaket mit dem Namen " [**Azure-Mr-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)" herunterladen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="c4a30-365">Dieses Paket ist vollständig in einer Szene, bei der alle Objekte in dieser vorerstellt wurden, sodass Sie sich darauf konzentrieren können, alles zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c4a30-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="c4a30-366">Das **shelbkeeper** -Skript wird bereitgestellt, enthält jedoch nur die öffentlichen Variablen für den Zweck der Struktur der Szenen Einrichtung.</span><span class="sxs-lookup"><span data-stu-id="c4a30-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="c4a30-367">Sie müssen alle anderen Abschnitte durchführen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="c4a30-368">So importieren Sie das Paket:</span><span class="sxs-lookup"><span data-stu-id="c4a30-368">To import this package:</span></span>

1.  <span data-ttu-id="c4a30-369">Klicken Sie oben auf dem Bildschirm mit dem Unity-Dashboard auf **Assets** , und klicken Sie dann auf **Import Package, Custom Package**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="c4a30-371">Wählen Sie mit der Dateiauswahl das Paket **Azure-Mr-307. unitypackage** aus, und klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="c4a30-372">Eine Liste der Komponenten für dieses Asset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="c4a30-373">Bestätigen Sie den Import, indem Sie auf **importieren**klicken.</span><span class="sxs-lookup"><span data-stu-id="c4a30-373">Confirm the import by clicking **Import**.</span></span>

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="c4a30-375">Nachdem der Import abgeschlossen ist, werden Sie feststellen, dass einige neue Ordner im Unity- **Projekt Panel**angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="c4a30-376">Dabei handelt es sich um die 3D-Modelle und die jeweiligen Materialien, die Teil der vorgefertigten Szene sind, an der Sie arbeiten werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="c4a30-377">In diesem Kurs schreiben Sie den Großteil des Codes.</span><span class="sxs-lookup"><span data-stu-id="c4a30-377">You will write the majority of the code in this course.</span></span>

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="c4a30-379">Klicken Sie im **Projekt Panel** Ordner auf den Ordner **Szenen** , und doppelklicken Sie auf die Szene in ( **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="c4a30-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="c4a30-380">Die Szene wird geöffnet (siehe Abbildung unten).</span><span class="sxs-lookup"><span data-stu-id="c4a30-380">The scene will open (see image below).</span></span> <span data-ttu-id="c4a30-381">Wenn die roten Diamanten fehlen, klicken Sie einfach auf die **Gizmos** -Schaltfläche oben rechts im **Spiel**Bereich.</span><span class="sxs-lookup"><span data-stu-id="c4a30-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="c4a30-383">Kapitel 7: Überprüfen der DLLs in Unity</span><span class="sxs-lookup"><span data-stu-id="c4a30-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="c4a30-384">Um die Verwendung von JSON-Bibliotheken (die für die Serialisierung und Deserialisierung verwendet wird) zu nutzen, wurde eine newtonsoft-dll mit dem Paket implementiert, das Sie in integriert haben.</span><span class="sxs-lookup"><span data-stu-id="c4a30-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="c4a30-385">Die Bibliothek sollte über die richtige Konfiguration verfügen, obwohl Sie überprüft werden muss (insbesondere, wenn Probleme mit dem Code nicht funktionieren).</span><span class="sxs-lookup"><span data-stu-id="c4a30-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="c4a30-386">Gehen Sie hierzu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="c4a30-386">To do so:</span></span>

-  <span data-ttu-id="c4a30-387">Klicken Sie mit der linken Maustaste auf die newtonsoft-Datei im Ordner Plug-ins, und sehen Sie sich den Bereich **Inspector**an.</span><span class="sxs-lookup"><span data-stu-id="c4a30-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="c4a30-388">Stellen Sie sicher, dass **jede Plattform** getickt ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="c4a30-389">Wechseln Sie zur **Registerkarte UWP** , und stellen Sie sicher, dass die Option **nicht verarbeiten nicht** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importieren der DLLs in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="c4a30-391">Kapitel 8: Erstellen der Shelf Keeper-Klasse</span><span class="sxs-lookup"><span data-stu-id="c4a30-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="c4a30-392">Die **shelskeeper** -Klasse hostet Methoden, die die Benutzeroberfläche und die in der Szene erzeugten Produkte steuern.</span><span class="sxs-lookup"><span data-stu-id="c4a30-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="c4a30-393">Als Teil des importierten Pakets erhalten Sie diese Klasse, obwohl sie unvollständig ist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="c4a30-394">Nun ist es an der Zeit, diese Klasse abzuschließen:</span><span class="sxs-lookup"><span data-stu-id="c4a30-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="c4a30-395">Doppelklicken Sie auf das **shelfkeeper** -Skript im Ordner " **Scripts** ", um es mit **Visual Studio 2017**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="c4a30-396">Ersetzen Sie den gesamten Code, der im Skript vorhanden ist, durch den folgenden Code, der das Datum und die Uhrzeit festlegt und eine-Methode zum Anzeigen eines Produkts aufweist.</span><span class="sxs-lookup"><span data-stu-id="c4a30-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="c4a30-397">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c4a30-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="c4a30-398">Überprüfen Sie im Unity-Editor, ob die **shelbkeeper** -Klasse wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="c4a30-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Erstellen der Shelf Keeper-Klasse](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="c4a30-400">Wenn das Skript nicht über die Verweis *Ziele (z. &* # 160; & # 160; & # 160; & # 160; & # 160; & # 160; & # 160; & # 160; a.</span><span class="sxs-lookup"><span data-stu-id="c4a30-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="c4a30-401">Weitere Erläuterungen finden Sie unten:</span><span class="sxs-lookup"><span data-stu-id="c4a30-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="c4a30-402">Öffnen Sie das Element für das Erzeugen von **Punkten** innerhalb des **shelfkeeper** -Komponenten Skripts, indem Sie darauf klicken.</span><span class="sxs-lookup"><span data-stu-id="c4a30-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="c4a30-403">Es wird ein unter Abschnitt mit dem Namen **size**angezeigt, der die Größe des Arrays angibt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="c4a30-404">Geben Sie **3** in das Textfeld neben **Größe** ein, und drücken **Sie die Eingabe**Taste, und es werden drei Slots unterhalb von erstellt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="c4a30-405">Erweitern Sie in der **Hierarchie** das **Zeitanzeige** Objekt (indem Sie mit der linken Maustaste auf den Pfeil daneben klicken).</span><span class="sxs-lookup"><span data-stu-id="c4a30-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="c4a30-406">Klicken Sie dann in der **Hierarchie**auf die ***Hauptkamera*** , damit der **Inspektor** seine Informationen anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="c4a30-407">Wählen Sie im **Hierarchie Panel**die **Hauptkamera** aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="c4a30-408">Ziehen Sie **die Datums** -und **Uhrzeit** Objekte aus dem Bereich **Hierarchie** in die **Text** Slots **Date Text** und Time innerhalb des **Inspektors** der **Hauptkamera** der **shelfkeeper** -Komponente.</span><span class="sxs-lookup"><span data-stu-id="c4a30-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="c4a30-409">Ziehen Sie die- **erstellungspunkte** aus dem **Hierarchie Panel** (unterhalb des *Shelf* -Objekts) auf die **drei** **Element** Verweis Ziele unterhalb des-Elements des- **Punkt** Arrays, wie in der Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Erstellen der Shelf Keeper-Klasse](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="c4a30-411">Kapitel 9: Erstellen der productvorhersage-Klasse</span><span class="sxs-lookup"><span data-stu-id="c4a30-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="c4a30-412">Die nächste Klasse, die Sie erstellen, ist die **productvorhersage** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="c4a30-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="c4a30-413">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="c4a30-413">This class is responsible for:</span></span>

-   <span data-ttu-id="c4a30-414">Abfragen der **Machine Learning Dienst** Instanz, die das aktuelle Datum und die Uhrzeit bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="c4a30-415">Deserialisieren der JSON-Antwort in verwendbare Daten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="c4a30-416">Interpretieren der Daten, Abrufen der drei empfohlenen Produkte.</span><span class="sxs-lookup"><span data-stu-id="c4a30-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="c4a30-417">Aufrufen der **shelfkeeper** -Klassen Methoden, um die Daten in der Szene anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="c4a30-418">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c4a30-418">To create this class:</span></span>

1.  <span data-ttu-id="c4a30-419">Wechseln Sie im **Projekt Panel**zum Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="c4a30-420">Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen** Sie >  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="c4a30-421">Nennen Sie das Skript **productvorhersage**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="c4a30-422">Doppelklicken Sie auf das neue **productvorhersage** -Skript, um es mit **Visual Studio 2017**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="c4a30-423">Wenn das Dialogfeld **Datei Änderung erkannt** angezeigt wird, klicken Sie auf \* Projekt Mappe neu**Laden**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="c4a30-424">Fügen Sie am Anfang der productvorhersage-Klasse die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="c4a30-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="c4a30-425">Fügen Sie innerhalb der **productvorhersage** -Klasse die folgenden beiden Objekte ein, die aus einer Reihe von geschachtelten Klassen bestehen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="c4a30-426">Diese Klassen werden zum Serialisieren und Deserialisieren des JSON-Code für den Machine Learning-Dienst verwendet.</span><span class="sxs-lookup"><span data-stu-id="c4a30-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="c4a30-427">Fügen Sie dann die folgenden Variablen oberhalb des vorherigen Codes hinzu (sodass sich der JSON-bezogene Code am Ende des Skripts befindet, unter dem gesamten anderen Code und nicht mehr):</span><span class="sxs-lookup"><span data-stu-id="c4a30-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="c4a30-428">Stellen Sie sicher, dass Sie den **Primärschlüssel** und den **Anforderungs Antwort-Endpunkt**aus dem Machine Learning-Portal in die Variablen hier einfügen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="c4a30-429">Die folgenden Bilder zeigen, wo Sie den Schlüssel und den Endpunkt von übernommen hätten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Der Machine Learning Studio: das Experiment](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="c4a30-432">Fügen Sie diesen Code in die Methode " **Start ()** " ein.</span><span class="sxs-lookup"><span data-stu-id="c4a30-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="c4a30-433">Die Methode " **Start ()** " wird aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="c4a30-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="c4a30-434">Im folgenden finden Sie die-Methode, die das Datum und die Uhrzeit von Windows erfasst und in ein Format konvertiert, das unser Machine Learning Experiment zum Vergleichen mit den in der Tabelle gespeicherten Daten verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="c4a30-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="c4a30-435">Sie können die **Update ()** -Methode **Löschen** , da Sie von dieser Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c4a30-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="c4a30-436">Fügen Sie die folgende Methode hinzu, die das aktuelle Datum und die aktuelle Uhrzeit an den Machine Learning-Endpunkt kommuniziert und eine Antwort im JSON-Format empfängt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

12. <span data-ttu-id="c4a30-437">Fügen Sie die folgende Methode hinzu, die für das Deserialisieren der JSON-Antwort zuständig ist, und das Ergebnis der Deserialisierung an die **shelfkeeper** -Klasse zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="c4a30-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="c4a30-438">Bei diesem Ergebnis handelt es sich um die Namen der drei Elemente, die zum aktuellen Datum und zur aktuellen Uhrzeit am häufigsten verkauft werden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="c4a30-439">Fügen Sie den folgenden Code in die **productvorhersage** -Klasse ein, unterhalb der vorherigen Methode.</span><span class="sxs-lookup"><span data-stu-id="c4a30-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="c4a30-440">Speichern Sie **Visual Studio** , und wechseln Sie zurück zu **Unity**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="c4a30-441">Ziehen Sie das **productvorhersage** -Klassen Skript aus dem **Skript** Ordner auf das **Hauptkamera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="c4a30-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="c4a30-442">Speichern Sie Ihre Szene und Projekt **Datei** > speichern Sie die **Szene/Datei** > speichern Sie das **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="c4a30-443">Kapitel 10: Erstellen der UWP-Lösung</span><span class="sxs-lookup"><span data-stu-id="c4a30-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="c4a30-444">Nun ist es an der Zeit, das Projekt als UWP-Lösung zu erstellen, damit es als eigenständige Anwendung ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c4a30-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="c4a30-445">So erstellen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c4a30-445">To Build:</span></span>

1.  <span data-ttu-id="c4a30-446">Speichern Sie die aktuelle Szene, indem Sie auf **Datei** > **Szenen speichern**klicken.</span><span class="sxs-lookup"><span data-stu-id="c4a30-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="c4a30-447">Gehe zu **Datei** > **Buildeinstellungen**</span><span class="sxs-lookup"><span data-stu-id="c4a30-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="c4a30-448">Aktivieren Sie das Kontroll **Kästchen C# Unity-Projekte** (Dies ist wichtig, da es Ihnen ermöglicht, die Klassen zu bearbeiten, nachdem der Build abgeschlossen wurde).</span><span class="sxs-lookup"><span data-stu-id="c4a30-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="c4a30-449">Klicken Sie auf **offene Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="c4a30-450">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-450">Click **Build**.</span></span>

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="c4a30-452">Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projekt Mappe erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="c4a30-453">Erstellen Sie einen Ordner **BUILDS** , und erstellen Sie in diesem Ordner einen anderen Ordner mit einem entsprechenden Namen Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="c4a30-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="c4a30-454">Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, um den Build an diesem Speicherort zu starten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-55.png)

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="c4a30-457">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="c4a30-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="c4a30-458">Kapitel 11: Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="c4a30-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="c4a30-459">So stellen Sie die Anwendung bereit:</span><span class="sxs-lookup"><span data-stu-id="c4a30-459">To deploy your application:</span></span>

1.  <span data-ttu-id="c4a30-460">Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="c4a30-461">Wenn Visual Studio geöffnet ist, müssen Sie die nuget-Pakete wiederherstellen, indem Sie mit der rechten Maustaste auf Projektmappen-Explorer die MachineLearningLab_Build-Projekt Mappe Klicken (auf der rechten Seite von Visual Studio) und dann auf nuget-Pakete wiederherstellen klicken:</span><span class="sxs-lookup"><span data-stu-id="c4a30-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Hinzufügen von nuget-Paketen](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="c4a30-463">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="c4a30-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="c4a30-464">Wählen Sie auf der Projektmappenplattform die Option **x86**, **lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="c4a30-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="c4a30-465">Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="c4a30-466">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="c4a30-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="c4a30-467">Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den *Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen*; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="c4a30-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="c4a30-468">Stellen Sie sicher, dass der **Entwicklermodus** **auf**dem in den *Einstellungen > Update & Sicherheits > für Entwickler*gefunden.</span><span class="sxs-lookup"><span data-stu-id="c4a30-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Hinzufügen von nuget-Paketen](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="c4a30-470">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf Lösung bereitstellen, um die Anwendung per querladen auf Ihren PC zu **verlagern** .</span><span class="sxs-lookup"><span data-stu-id="c4a30-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="c4a30-471">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="c4a30-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="c4a30-472">Wenn Sie die Mixed Reality-Anwendung ausführen, wird die Bench angezeigt, die in ihrer Unity-Szene eingerichtet wurde. von der Initialisierung werden die in Azure eingerichteten Daten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="c4a30-473">Die Daten werden in Ihrer Anwendung deserialisiert, und die drei wichtigsten Ergebnisse für das aktuelle Datum und die aktuelle Uhrzeit werden visuell bereitgestellt, wie drei Modelle auf der Bench.</span><span class="sxs-lookup"><span data-stu-id="c4a30-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="c4a30-474">Ihre fertiggestellte Machine Learning Anwendung</span><span class="sxs-lookup"><span data-stu-id="c4a30-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="c4a30-475">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Azure Machine Learning nutzt, um Daten Vorhersagen zu treffen und in Ihrer Szene anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4a30-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Hinzufügen von nuget-Paketen](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="c4a30-477">Trainiert</span><span class="sxs-lookup"><span data-stu-id="c4a30-477">Exercise</span></span>

<span data-ttu-id="c4a30-478">**Übung 1**</span><span class="sxs-lookup"><span data-stu-id="c4a30-478">**Exercise 1**</span></span>

<span data-ttu-id="c4a30-479">Experimentieren Sie mit der Sortierreihenfolge Ihrer Anwendung, und lassen Sie die drei untersten Vorhersagen im Regal anzeigen, da diese Daten möglicherweise auch nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="c4a30-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="c4a30-480">**Übung 2**</span><span class="sxs-lookup"><span data-stu-id="c4a30-480">**Exercise 2**</span></span>

<span data-ttu-id="c4a30-481">Die Verwendung von **Azure-Tabellen** füllt eine neue Tabelle mit Wetterinformationen auf und erstellt mithilfe der Daten ein neues Experiment.</span><span class="sxs-lookup"><span data-stu-id="c4a30-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
