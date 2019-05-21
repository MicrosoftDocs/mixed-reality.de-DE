---
title: MR und Azure 304 - gesichtserkennung
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, gesichtserkennungs, Hololens, immersive Vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596465"
---
>[!NOTE]
><span data-ttu-id="fbc35-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="fbc35-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fbc35-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fbc35-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="fbc35-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fbc35-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fbc35-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="fbc35-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fbc35-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="fbc35-110">MR und Azure 304: Gesichtserkennung</span><span class="sxs-lookup"><span data-stu-id="fbc35-110">MR and Azure 304: Face recognition</span></span>

![Ergebnis der Abschluss dieses Kurses](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="fbc35-112">In diesem Kurs erfahren Sie das Hinzufügen von Funktionen für die Erkennung von Face einer mixed Reality-Anwendung mithilfe von Azure Cognitive Services, mit der Gesichtserkennungs-API von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fbc35-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="fbc35-113">*Gesichtserkennungs-API von Azure* ist ein Microsoft-Dienst, die Entwickler mit den fortschrittlichsten gesichtserkennungsalgorithmen, alles in der Cloud bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="fbc35-114">Die *Gesichtserkennungs-API* verfügt über zwei Hauptfunktionen: gesichtserkennung mit Attributen und gesichtserkennungs.</span><span class="sxs-lookup"><span data-stu-id="fbc35-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="fbc35-115">Dadurch können Entwickler legen Sie einfach einen Satz von Gruppen für Flächen, und klicken Sie dann Abfrage Bilder an den Dienst später senden, um zu bestimmen, zu denen ein Gesicht gehört.</span><span class="sxs-lookup"><span data-stu-id="fbc35-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="fbc35-116">Weitere Informationen finden Sie auf die [Azure Gesichtserkennung Seite](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="fbc35-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="fbc35-117">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality HoloLens-Anwendung, die für die folgenden Aufgaben werden können</span><span class="sxs-lookup"><span data-stu-id="fbc35-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="fbc35-118">Verwenden einer **tippen Geste** initiiert die Erfassung eines Abbilds mithilfe der integrierten Kamera für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fbc35-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="fbc35-119">Senden Sie das erfasste Abbild der *Gesichtserkennungs-API von Azure* Service.</span><span class="sxs-lookup"><span data-stu-id="fbc35-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="fbc35-120">Erhalten Sie die Ergebnisse der *Gesichtserkennungs-API* Algorithmus.</span><span class="sxs-lookup"><span data-stu-id="fbc35-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="fbc35-121">Verwenden Sie eine einfache Benutzeroberfläche, um den Namen der übereinstimmenden Personen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="fbc35-122">Dadurch erfahren Sie, wie die Ergebnisse aus der Gesichtserkennungs-API-Dienst in Ihre Unity-basierte mixed Reality-Anwendung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="fbc35-123">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="fbc35-124">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="fbc35-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="fbc35-125">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="fbc35-126">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="fbc35-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fbc35-127">Kurs</span><span class="sxs-lookup"><span data-stu-id="fbc35-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fbc35-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fbc35-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fbc35-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="fbc35-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="fbc35-130">MR und Azure 304: Gesichtserkennung</span><span class="sxs-lookup"><span data-stu-id="fbc35-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="fbc35-131">✔️</span><span class="sxs-lookup"><span data-stu-id="fbc35-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fbc35-132">✔️</span><span class="sxs-lookup"><span data-stu-id="fbc35-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="fbc35-133">Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="fbc35-134">Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="fbc35-135">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fbc35-136">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fbc35-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="fbc35-137">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="fbc35-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="fbc35-138">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="fbc35-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="fbc35-139">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="fbc35-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="fbc35-140">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="fbc35-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="fbc35-141">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="fbc35-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="fbc35-142">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="fbc35-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="fbc35-143">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="fbc35-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="fbc35-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="fbc35-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="fbc35-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fbc35-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="fbc35-146">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="fbc35-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="fbc35-147">Eine Kamera, die Verbindung mit Ihrem PC (für immersive Kopfhörer Entwicklung)</span><span class="sxs-lookup"><span data-stu-id="fbc35-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="fbc35-148">Zugriff auf das Internet für die Einrichtung von Azure und Gesichtserkennungs-API abrufen</span><span class="sxs-lookup"><span data-stu-id="fbc35-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="fbc35-149">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="fbc35-149">Before you start</span></span>

1.  <span data-ttu-id="fbc35-150">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="fbc35-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="fbc35-151">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fbc35-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="fbc35-152">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="fbc35-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="fbc35-153">Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="fbc35-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="fbc35-154">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="fbc35-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="fbc35-155">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="fbc35-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="fbc35-156">Kapitel 1: das Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="fbc35-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="fbc35-157">Verwenden der *Gesichtserkennungs-API* Service in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="fbc35-158">Melden Sie sich zunächst auf die [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="fbc35-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="fbc35-159">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="fbc35-160">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="fbc35-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="fbc35-161">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Gesichtserkennungs-API*, drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Suchen Sie nach gesichtserkennungs-api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="fbc35-163">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="fbc35-164">Die neue Seite bietet eine Beschreibung der *Gesichtserkennungs-API* Service.</span><span class="sxs-lookup"><span data-stu-id="fbc35-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="fbc35-165">Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![gesichtserkennungs-API-Informationen](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="fbc35-167">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="fbc35-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="fbc35-168">Fügen Sie dem gewünschten Namen für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="fbc35-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="fbc35-169">Wählen Sie ein Abonnement.</span><span class="sxs-lookup"><span data-stu-id="fbc35-169">Select a subscription.</span></span>

    3. <span data-ttu-id="fbc35-170">Wählen Sie der Tarif für Sie geeignet, ist dies das erste Mal erstellen eine *Gesichtserkennungs-API-Dienst*, freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="fbc35-171">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fbc35-172">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fbc35-173">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="fbc35-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="fbc35-174">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="fbc35-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="fbc35-175">Der UWP-app **Person Maker**, die Sie später verwenden, erfordert die Verwendung von "USA, Westen", Speicherort.</span><span class="sxs-lookup"><span data-stu-id="fbc35-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="fbc35-176">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="fbc35-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="fbc35-177">Wählen Sie **erstellen\*.**</span><span class="sxs-lookup"><span data-stu-id="fbc35-177">Select **Create\*.**</span></span>

        ![Erstellen Sie gesichtserkennungs-API-Dienst](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="fbc35-179">Nachdem Sie auf geklickt haben **erstellen**\* müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="fbc35-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="fbc35-180">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Benachrichtigung über Erstellung des Diensts](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="fbc35-182">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-182">Click on the notifications to explore your new Service instance.</span></span>

    ![Wechseln Sie zu ressourcenbenachrichtigung](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="fbc35-184">Wenn Sie bereit sind, klicken Sie auf **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![Zugriff gesichtserkennungs-API-Schlüssel](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="fbc35-186">In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, die durch die Verwendung Ihres Diensts Abonnement 'Key' ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fbc35-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="fbc35-187">Von der *Schnellstart* Seite, der Ihre *Gesichtserkennungs-API* Dienst, den ersten Punkt ist 1, number, zu *nehmen Sie Ihre Schlüssel.*</span><span class="sxs-lookup"><span data-stu-id="fbc35-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="fbc35-188">Auf der *Service* Seite Wählen Sie entweder das blaue **Schlüssel** Hyperlink (sofern auf der Seite "Schnellstart"), oder die **Schlüssel** Link im Navigationsmenü Services (auf der linken Seite, gekennzeichnet durch die " Schlüssel "Symbol"), um Ihre Schlüssel anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fbc35-189">Notieren Sie sich einer der Schlüssel, und schützen Sie, wie Sie es später benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="fbc35-190">Kapitel 2: verwenden die "Person Maker" UWP-Anwendung</span><span class="sxs-lookup"><span data-stu-id="fbc35-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="fbc35-191">Vergewissern Sie sich zum Herunterladen der vorgefertigten UWP-Anwendung namens [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="fbc35-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="fbc35-192">Diese app ist nicht das Endprodukt für diesen Kurs, nur ein Tool, mit denen Sie Ihre Azure-Einträge, die spätere Projekt abhängig sind, wird zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="fbc35-193">**Person Maker** können Sie Azure-Einträge zu erstellen, die Personen und Personengruppen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="fbc35-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="fbc35-194">Die Anwendung werden alle erforderliche Informationen in einem Format platzieren, die dann später von der FaceAPI verwendet werden kann um die Gesichter von Personen zu erkennen, die Sie hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="fbc35-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="fbc35-195">[WICHTIG] **Person Maker** verwendet einige grundlegende Einschränkungen, um sicherzustellen, dass Sie nicht die Anzahl der Aufrufe pro Minute überschritten, werden die **kostenloses Abonnement Tarif**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="fbc35-196">Der grüne Text am Anfang wird sich in Rot ändern und als "Aktiv" zu aktualisieren, wenn die Drosselung auftritt; Wenn dies der Fall ist, warten Sie einfach die Anwendung (es wird gewartet, bis sie als Nächstes fortgesetzt werden kann den Zugriff auf den gesichtserkennungs-Dienst "IN-aktiv" aktualisiert werden, wenn Sie ihn erneut verwenden können).</span><span class="sxs-lookup"><span data-stu-id="fbc35-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="fbc35-197">Diese Anwendung verwendet die *Microsoft.ProjectOxford.Face* verwenden der Gesichtserkennungs-API-Bibliotheken, die Sie die vollständige vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="fbc35-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="fbc35-198">Diese Bibliothek steht kostenlos als NuGet-Paket zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="fbc35-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="fbc35-199">Weitere Informationen zu diesem und ähnlichen APIs [stellen Sie sicher, dass die API-Referenzartikel finden Sie unter](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="fbc35-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="fbc35-200">Hierbei handelt es sich um nur die erforderlichen Schritte, die Anweisungen dazu, wie all dies wird weiter unten in das Dokument.</span><span class="sxs-lookup"><span data-stu-id="fbc35-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="fbc35-201">Die **Person Maker** app können Sie:</span><span class="sxs-lookup"><span data-stu-id="fbc35-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="fbc35-202">Erstellen Sie eine *Personengruppe*, eine Gruppe besteht aus mehreren Personen, die Sie es zuordnen möchten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="fbc35-203">Mit Ihrem Azure-Konto können Sie mehrere Personengruppen hosten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="fbc35-204">Erstellen Sie eine *Person*, dies ist ein Mitglied der Gruppe eine Person.</span><span class="sxs-lookup"><span data-stu-id="fbc35-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="fbc35-205">Jede Person hat eine Reihe von *Gesicht* Abbilder zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="fbc35-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="fbc35-206">Weisen Sie *stehen Images* zu eine *Person*, um Ihre Azure-Gesichtserkennungs-API-Dienst zur Erkennung von zuzulassen eine *Person* mit den entsprechenden *Gesicht*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="fbc35-207">*Train* Ihre *Azure Gesichtserkennungs-API-Dienst*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="fbc35-208">Denken Sie daran, also um diese app zur Erkennung von Personen zu trainieren, Sie zehn (10) vergrößerte Fotos von jeder Person benötigen, die Sie zu Ihrer Person-Gruppe hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="fbc35-209">Der Windows 10-Cam-App können Sie diese Verknüpfungen gelangen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="fbc35-210">Müssen Sie sicherstellen, dass jedes Foto deaktiviert ist (vermeiden Sie Unschärfe, verdeckt oder versteht, aus dem Subjekt wird), müssen Sie das Foto im JPG- oder Png-Dateiformat mit der Größe einer Bilddatei wird nicht größer **4 MB**, und nicht weniger als **1 KB**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="fbc35-211">Wenn Sie dieses Lernprogramm durcharbeiten, verwenden Sie nicht Ihre eigenen Gesicht für das Training, als wenn Sie die HoloLens auf Einfügen, Sie selbst ansehen können nicht.</span><span class="sxs-lookup"><span data-stu-id="fbc35-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="fbc35-212">Verwenden Sie das Gesicht von Kollegen oder Fellow Schüler/Student ein.</span><span class="sxs-lookup"><span data-stu-id="fbc35-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="fbc35-213">Ausführung **Person Maker**:</span><span class="sxs-lookup"><span data-stu-id="fbc35-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="fbc35-214">Öffnen Sie die **PersonMaker** Ordner und doppelklicken klicken Sie auf die *PersonMaker Lösung* , öffnen Sie ihn mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="fbc35-215">Sobald die *PersonMaker Lösung* geöffnet ist, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="fbc35-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="fbc35-216">Die *Projektmappenkonfiguration* nastaven NA hodnotu **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="fbc35-217">Die *Projektmappenplattform* nastaven NA hodnotu **X86**</span><span class="sxs-lookup"><span data-stu-id="fbc35-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="fbc35-218">Die *Zielplattform* ist **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="fbc35-219">Außerdem müssen Sie möglicherweise *NuGet-Pakete wiederherstellen* (mit der rechten Maustaste die *Lösung* , und wählen Sie **NuGet-Pakete wiederherstellen**).</span><span class="sxs-lookup"><span data-stu-id="fbc35-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="fbc35-220">Klicken Sie auf *lokalen Computer* und die Anwendung wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="fbc35-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="fbc35-221">Beachten Sie, auf kleineren Bildschirmen, alle Inhalte möglicherweise nicht sichtbar, obwohl Sie weiteren unten zum Anzeigen einen Bildlauf durchführen können.</span><span class="sxs-lookup"><span data-stu-id="fbc35-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![Person Maker-Benutzeroberfläche](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="fbc35-223">Fügen Sie Ihrer **Authentifizierungsschlüssel für die Azure**, der Sie enthalten soll, aus Ihrer *Gesichtserkennungs-API* innerhalb von Azure Service.</span><span class="sxs-lookup"><span data-stu-id="fbc35-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="fbc35-224">Fügen Sie ein:</span><span class="sxs-lookup"><span data-stu-id="fbc35-224">Insert:</span></span>

    1. <span data-ttu-id="fbc35-225">Die *ID* Sie zuweisen möchten die *Personengruppe*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="fbc35-226">Die ID muss in Kleinbuchstaben ohne Leerzeichen sein.</span><span class="sxs-lookup"><span data-stu-id="fbc35-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="fbc35-227">Notieren Sie sich diese ID an, wie sie weiter unten in Ihrem Unity-Projekt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="fbc35-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="fbc35-228">Die *Namen* Sie zuweisen möchten die *Personengruppe* (können Leerzeichen enthalten).</span><span class="sxs-lookup"><span data-stu-id="fbc35-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="fbc35-229">Drücken Sie **Personengruppe erstellen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="fbc35-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="fbc35-230">Eine bestätigungsmeldung sollte unterhalb der Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="fbc35-231">Wenn Sie einen Fehler "Zugriff verweigert" haben, überprüfen Sie den Speicherort, die, den Sie für Ihr Azure-Dienst festlegen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="fbc35-232">Wie bereits erwähnt, dient diese app für "USA, Westen".</span><span class="sxs-lookup"><span data-stu-id="fbc35-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbc35-233">Sie werden feststellen, dass Sie, auch klicken können die **Abrufen einer bekannten Gruppe** Schaltfläche: sind über, wenn Sie eine Person bereits erstellt haben, Gruppe und die möchten, verwenden, anstatt ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="fbc35-234">Beachten Sie, wenn Sie auf *erstellen Sie eine Gruppe von Personen* mit einer bekannten Gruppe, dies wird auch "abrufen" eine Gruppe.</span><span class="sxs-lookup"><span data-stu-id="fbc35-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="fbc35-235">Fügen Sie der *Namen* von der *Person* erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc35-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="fbc35-236">Klicken Sie auf die **Person erstellen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="fbc35-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="fbc35-237">Eine bestätigungsmeldung sollte unterhalb der Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="fbc35-238">Wenn Sie eine Person zu löschen. möchten Sie zuvor erstellt haben, können Sie den Namen in das Textfeld, und drücken Sie schreiben **Person löschen**</span><span class="sxs-lookup"><span data-stu-id="fbc35-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="fbc35-239">Stellen Sie sicher, dass Sie den Speicherort des Fotos zehn (10) der Person kennen, die Sie zur Gruppe hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="fbc35-240">Drücken Sie **erstellen "und" Ordner öffnen** , öffnen Sie Windows Explorer zu dem Ordner, die die Person, die zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="fbc35-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="fbc35-241">Hinzufügen von Bildern zehn (10) im Ordner "".</span><span class="sxs-lookup"><span data-stu-id="fbc35-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="fbc35-242">Diese muss der *JPG* oder *PNG* Dateiformat.</span><span class="sxs-lookup"><span data-stu-id="fbc35-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="fbc35-243">Klicken Sie auf **an Azure übermitteln**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="fbc35-244">Ein Zähler zeigt den Status der Übermittlung, gefolgt von einer Meldung, wenn er abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="fbc35-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="fbc35-245">Klicken Sie nach der Zähler beendet wurde und eine bestätigungsmeldung angezeigt wurde auf **trainieren** zum Trainieren Ihres Diensts.</span><span class="sxs-lookup"><span data-stu-id="fbc35-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="fbc35-246">Sobald der Vorgang abgeschlossen wurde, können Sie in Unity zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="fbc35-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="fbc35-247">Kapitel 3: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="fbc35-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="fbc35-248">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="fbc35-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="fbc35-249">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-249">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="fbc35-251">Sie müssen nun einen Namen für die Unity-Projekt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="fbc35-252">Fügen Sie **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="fbc35-253">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="fbc35-254">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="fbc35-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fbc35-255">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-255">Then, click **Create project**.</span></span>

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="fbc35-257">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fbc35-258">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fbc35-259">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fbc35-260">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="fbc35-260">Close the **Preferences** window.</span></span>

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="fbc35-262">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="fbc35-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="fbc35-264">Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="fbc35-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="fbc35-265">**Geräte** nastaven NA hodnotu **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="fbc35-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="fbc35-266">Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="fbc35-267">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="fbc35-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="fbc35-268">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="fbc35-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="fbc35-269">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="fbc35-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="fbc35-270">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="fbc35-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="fbc35-271">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="fbc35-272">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fbc35-273">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-273">A save window will appear.</span></span>

            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="fbc35-275">Wählen Sie die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="fbc35-277">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname**: Textfeld **FaceRecScene**, drücken Sie dann die **speichern**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="fbc35-279">Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="fbc35-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="fbc35-280">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="fbc35-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="fbc35-282">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="fbc35-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="fbc35-283">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="fbc35-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="fbc35-284">**Scripting** **Laufzeitversion** muss **experimentell** (.NET 4.6 entspricht).</span><span class="sxs-lookup"><span data-stu-id="fbc35-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="fbc35-285">Das Ändern dieser Eigenschaft löst eine Editor-Neustart erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fbc35-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="fbc35-286">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="fbc35-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="fbc35-287">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="fbc35-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="fbc35-289">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="fbc35-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="fbc35-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fbc35-290">**InternetClient**</span></span>
        - <span data-ttu-id="fbc35-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="fbc35-291">**Webcam**</span></span>

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="fbc35-293">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="fbc35-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="fbc35-295">Im *Buildeinstellungen*, **Unity C# Projekte** nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="fbc35-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="fbc35-296">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="fbc35-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="fbc35-297">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="fbc35-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="fbc35-298">Kapitel 4: Main Camera-setup</span><span class="sxs-lookup"><span data-stu-id="fbc35-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbc35-299">Wenn Sie, überspringen möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortfahren, können Sie [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), und importieren Sie es in Ihr Projekt als eine [benutzerdefinierte Paket](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="fbc35-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="fbc35-300">Beachten Sie, dass dieses Paket auch den Import von enthält der *Newtonsoft-DLL*, abgedeckte in [Kapitel 5](#chapter-5--import-the-newtonsoft.json-library).</span><span class="sxs-lookup"><span data-stu-id="fbc35-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="fbc35-301">Mit diesem nicht importiert haben, können Sie weiterhin von [Kapitel 6](#chapter-6-create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="fbc35-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="fbc35-302">In der *Hierarchie* Panel, wählen Sie die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="fbc35-303">Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="fbc35-304">Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="fbc35-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="fbc35-305">Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="fbc35-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="fbc35-306">Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="fbc35-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="fbc35-307">Legen Sie **Kennzeichnungen löschen** zu **Volltonfarbe**</span><span class="sxs-lookup"><span data-stu-id="fbc35-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="fbc35-308">Legen Sie die **Hintergrund** Farbe der Kamera-Komponente auf **Schwarz, Alpha 0 (Hex-Code: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="fbc35-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![Richten Sie die Kamera-Komponenten](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="fbc35-310">Kapitel 5: Importieren der Bibliothek "newtonsoft.JSON"</span><span class="sxs-lookup"><span data-stu-id="fbc35-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbc35-311">Wenn Sie in der '.unitypackage"importiert die [letzte Kapitel](#chapter-4--main-camera-setup), können Sie in diesem Kapitel überspringen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="fbc35-312">Können Sie deserialisieren und Serialisieren von Objekten, die empfangen und an den Bot-Dienst gesendet, die Sie herunterladen müssen die *"newtonsoft.JSON"* Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="fbc35-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="fbc35-313">Sehen Sie eine kompatible Version, die bereits mit der richtigen Struktur der Unity-Ordner in diesem organisiert [Unity-Paketdatei](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="fbc35-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="fbc35-314">So importieren Sie die Bibliothek:</span><span class="sxs-lookup"><span data-stu-id="fbc35-314">To import the library:</span></span>

1.  <span data-ttu-id="fbc35-315">Herunterladen des Unity-Pakets.</span><span class="sxs-lookup"><span data-stu-id="fbc35-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="fbc35-316">Klicken Sie auf **Assets**, **Paket importieren**, **Anpassungspaket**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importieren der Bibliothek "newtonsoft.JSON"](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="fbc35-318">Suchen Sie nach der Unity-Paket, das Sie heruntergeladen haben, und klicken Sie auf Öffnen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="fbc35-319">Stellen Sie sicher, dass alle Komponenten des Pakets ausgewählt werden, und klicken Sie auf **Import**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importieren der Bibliothek "newtonsoft.JSON"](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="fbc35-321">Kapitel 6: Erstellen Sie die FaceAnalysis-Klasse</span><span class="sxs-lookup"><span data-stu-id="fbc35-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="fbc35-322">Der Zweck der FaceAnalysis-Klasse werden die Methoden, die zum Kommunizieren mit Ihrem Azure-Face-Erkennung-Dienst zu hosten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="fbc35-323">Nach dem Senden des Diensts ein Aufzeichnungsabbild, wird es analysieren sie identifizieren die Gesichter von und bestimmen, ob alle mit einer bekannten Person angehören.</span><span class="sxs-lookup"><span data-stu-id="fbc35-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="fbc35-324">Wenn eine bekannte Person gefunden wird, wird diese Klasse den Namen als Benutzeroberflächentext in der Szene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="fbc35-325">Zum Erstellen der *FaceAnalysis* Klasse:</span><span class="sxs-lookup"><span data-stu-id="fbc35-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="fbc35-326">Mit der rechten Maustaste den *Ordner "Assets"* im Projektfenster befindet, klicken Sie dann auf **erstellen** > **Ordner**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="fbc35-327">Rufen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-327">Call the folder **Scripts**.</span></span> 

    ![Erstellen Sie die FaceAnalysis-Klasse.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="fbc35-329">Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="fbc35-330">Mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **erstellen**  >   **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="fbc35-331">Rufen Sie das Skript *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="fbc35-332">Doppelklicken Sie auf dem neuen *FaceAnalysis* Skript, um ihn mit Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="fbc35-333">Geben Sie die folgenden Namespaces, die oben genannten der *FaceAnalysis* Klasse:</span><span class="sxs-lookup"><span data-stu-id="fbc35-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="fbc35-334">Jetzt müssen Sie alle Objekte hinzufügen, die für die deserialising verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="fbc35-335">Diese Objekte müssen hinzugefügt werden **außerhalb** von der *FaceAnalysis* Skript (unterhalb der untere geschweifte Klammer).</span><span class="sxs-lookup"><span data-stu-id="fbc35-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="fbc35-336">Die *Start()* und *Update()* Methoden nicht verwendet werden, also jetzt löschen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="fbc35-337">In der *FaceAnalysis* -Klasse verwenden, fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="fbc35-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="fbc35-338">Ersetzen Sie die **Schlüssel** und **PersonGroupId** mit Ihrem Dienstschlüssel und die Id der Gruppe, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="fbc35-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="fbc35-339">Hinzufügen der *Awake()* -Methode, die in der Klasse initialisiert, Hinzufügen der *digitale Bilder* Klasse, um die Main Camera und ruft die Methode zum Erstellen von Bezeichnung:</span><span class="sxs-lookup"><span data-stu-id="fbc35-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="fbc35-340">Hinzufügen der *CreateLabel()* -Methode, die erstellt die *Bezeichnung* Objekt, das das Analyseergebnis anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="fbc35-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="fbc35-341">Hinzufügen der *DetectFacesFromImage()* und *GetImageAsByteArray()* Methode.</span><span class="sxs-lookup"><span data-stu-id="fbc35-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="fbc35-342">Die erste fordert des Erkennung Gesicht, um alle möglichen Gesicht in der Abbildung übermittelten zu erkennen, während Letzteres erforderlich, um das erfasste Abbild in ein Array von Bytes zu konvertieren ist:</span><span class="sxs-lookup"><span data-stu-id="fbc35-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="fbc35-343">Hinzufügen der *IdentifyFaces()* -Methode, die Anforderungen der *Gesicht Anerkennung Service* zum Identifizieren von jeder bekannten Fläche, die zuvor im übermittelten Bild erkannt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="fbc35-344">Die Anforderung gibt die Id identifizierten Person jedoch nicht den Namen zurück:</span><span class="sxs-lookup"><span data-stu-id="fbc35-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="fbc35-345">Hinzufügen der *GetPerson()* Methode.</span><span class="sxs-lookup"><span data-stu-id="fbc35-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="fbc35-346">Durch die Person bereitstellen, Id, dieser Methode und die Anforderungen für die *Gesicht Anerkennung Service* der Name der identifizierten Person zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="fbc35-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="fbc35-347">Denken Sie daran, **speichern** die Änderungen vor dem Wechsel zurück zu Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="fbc35-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="fbc35-348">Im Unity-Editor, ziehen Sie das Skript FaceAnalysis aus dem Ordner "Scripts" im Projektpanel auf das Main Camera-Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="fbc35-349">Die neue Skriptkomponente wird also die Main Camera hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-349">The new script component will be so added to the Main Camera.</span></span> 

![Platzieren Sie FaceAnalysis auf die Hauptkamera](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="fbc35-351">Kapitel 7: Erstellen Sie die digitale Bilder-Klasse</span><span class="sxs-lookup"><span data-stu-id="fbc35-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="fbc35-352">Der Zweck der *digitale Bilder* Klasse wird zum Hosten der Methoden, die für die Kommunikation mit Ihrer *Azure Gesicht Anerkennung Service* auf das Bild zu analysieren, Sie erfasst werden, identifiziert Gesichter darin, und bestimmen, wenn er zu einer bekannten Person gehört.</span><span class="sxs-lookup"><span data-stu-id="fbc35-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="fbc35-353">Wenn eine bekannte Person gefunden wird, wird diese Klasse den Namen als Benutzeroberflächentext in der Szene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="fbc35-354">Zum Erstellen der *digitale Bilder* Klasse:</span><span class="sxs-lookup"><span data-stu-id="fbc35-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="fbc35-355">Klicken Sie auf auf die **Skripts** Ordner, die Sie zuvor erstellt haben, und klicken Sie dann auf **erstellen**,  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="fbc35-356">Rufen Sie das Skript *digitale Bilder*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="fbc35-357">Doppelklicken Sie auf dem neuen *digitale Bilder* Skript, um ihn mit Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="fbc35-358">Geben Sie die folgenden Namespaces über die digitale Bilder-Klasse:</span><span class="sxs-lookup"><span data-stu-id="fbc35-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="fbc35-359">In der *digitale Bilder* -Klasse verwenden, fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="fbc35-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="fbc35-360">Hinzufügen der *Awake()* und *Start()* Methoden, die zum Initialisieren der Klasse und ermöglichen die HoloLens zum Erfassen des Benutzers Gesten erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="fbc35-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="fbc35-361">Hinzufügen der *TapHandler()* die aufgerufen wird, wenn der Benutzer führt eine *Tippen Sie auf* Geste:</span><span class="sxs-lookup"><span data-stu-id="fbc35-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="fbc35-362">Hinzufügen der *ExecuteImageCaptureAndAnalysis()* -Methode, die Image-Erfassung beginnen, werden:</span><span class="sxs-lookup"><span data-stu-id="fbc35-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="fbc35-363">Fügen Sie die Handler, die aufgerufen werden, wenn der Foto-Capture-Prozess abgeschlossen wurde:</span><span class="sxs-lookup"><span data-stu-id="fbc35-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="fbc35-364">Denken Sie daran, **speichern** die Änderungen vor dem Wechsel zurück zu Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="fbc35-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="fbc35-365">Kapitel 8 – Erstellen der Projektmappe</span><span class="sxs-lookup"><span data-stu-id="fbc35-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="fbc35-366">Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="fbc35-367">Vor dem Ausführen, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="fbc35-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="fbc35-368">Alle Einstellungen, die in Kapitel 3 genannten sind ordnungsgemäß festgelegt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="fbc35-369">Das Skript *FaceAnalysis* Main Camera-Objekts angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="fbc35-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="fbc35-370">Sowohl die **Authentication Key** und **Gruppen-Id** festgelegt wurden innerhalb der *FaceAnalysis* Skript.</span><span class="sxs-lookup"><span data-stu-id="fbc35-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="fbc35-371">A: Hierbei weisen Sie können die Projektmappe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="fbc35-372">Nachdem die Lösung erstellt wurde, werden Sie zum Bereitstellen der Anwendung bereit.</span><span class="sxs-lookup"><span data-stu-id="fbc35-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="fbc35-373">Um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="fbc35-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="fbc35-374">Speichern Sie die aktuelle Szene durch Klicken auf in Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="fbc35-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="fbc35-375">Wechseln Sie zur Datei, die Einstellungen zu erstellen, klicken Sie auf Öffnen Szenen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="fbc35-376">Stellen Sie sicher, dass zu Teilstrich Unity C# Projekte.</span><span class="sxs-lookup"><span data-stu-id="fbc35-376">Make sure to tick Unity C# Projects.</span></span>

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="fbc35-378">Drücken Sie die Builds.</span><span class="sxs-lookup"><span data-stu-id="fbc35-378">Press Build.</span></span> <span data-ttu-id="fbc35-379">Dies der Fall, wird Unity ein Datei-Explorer-Fenster geöffnet, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="fbc35-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="fbc35-380">Erstellen Sie diesen Ordner jetzt, in der Unity-Projekt, und rufen sie die App.</span><span class="sxs-lookup"><span data-stu-id="fbc35-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="fbc35-381">Drücken Sie mit den App-Ordner ausgewählt haben die Ordner auswählen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="fbc35-382">Unity beginnt mit der Ihr Projekt, um den App-Ordner erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="fbc35-383">Nachdem Unity die erstellen (es kann einige Zeit dauern) abgeschlossen ist, an der Position des Builds ein Datei-Explorer-Fenster wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="fbc35-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="fbc35-385">Öffnen Sie Ihre App-Ordner, und öffnen Sie dann die neue Projektmappe (wie oben MR_FaceRecognition.sln dargestellt).</span><span class="sxs-lookup"><span data-stu-id="fbc35-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="fbc35-386">Kapitel 9: Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="fbc35-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="fbc35-387">Für HoloLens bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="fbc35-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="fbc35-388">Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="fbc35-389">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="fbc35-389">To do this:</span></span>

    1. <span data-ttu-id="fbc35-390">Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="fbc35-391">Wechseln Sie zu **Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="fbc35-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="fbc35-392">Beachten Sie die **IPv4** Adresse.</span><span class="sxs-lookup"><span data-stu-id="fbc35-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="fbc35-393">Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit > für Entwickler**</span><span class="sxs-lookup"><span data-stu-id="fbc35-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="fbc35-394">Festlegen des Entwicklermodus auf.</span><span class="sxs-lookup"><span data-stu-id="fbc35-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="fbc35-395">Navigieren Sie zu Ihrem neuen Unity-Build (die *App* Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="fbc35-396">In der Projektmappenkonfiguration Select **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="fbc35-397">Wählen Sie in der Plattform für die Projektmappe **X86**, **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="fbc35-399">Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen**, zum querladen der Anwendung in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fbc35-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="fbc35-400">Ihre App sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fbc35-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="fbc35-401">Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**.</span><span class="sxs-lookup"><span data-stu-id="fbc35-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="fbc35-402">Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **Menü "Build"**, wählen *Projektmappe bereitstellen*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="fbc35-403">Kapitel 10 – verwenden die Anwendung</span><span class="sxs-lookup"><span data-stu-id="fbc35-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="fbc35-404">Trägt die HoloLens, um die app zu starten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="fbc35-405">Sehen Sie sich die Person, die Sie bei registriert haben, die die *Gesichtserkennungs-API*.</span><span class="sxs-lookup"><span data-stu-id="fbc35-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="fbc35-406">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="fbc35-406">Make sure that:</span></span>

    -  <span data-ttu-id="fbc35-407">Dieser Person ist nicht zu entfernten und deutlich sichtbar</span><span class="sxs-lookup"><span data-stu-id="fbc35-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="fbc35-408">Die umgebungsbeleuchtung ist nicht zu dunkel</span><span class="sxs-lookup"><span data-stu-id="fbc35-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="fbc35-409">Verwenden Sie die tippbewegung, um das Bild der Person zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="fbc35-410">Die App auf die Analysis-Anforderung senden und Empfangen einer Antwort warten.</span><span class="sxs-lookup"><span data-stu-id="fbc35-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="fbc35-411">Wenn die Person, die erfolgreich erkannt wurde, wird der Name der Person als Benutzeroberflächen-Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="fbc35-412">Sie können den Capture-Prozess mit der tippbewegung alle paar Sekunden wiederholen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="fbc35-413">Der fertigen Azure Gesichtserkennungs-API-Anwendung</span><span class="sxs-lookup"><span data-stu-id="fbc35-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="fbc35-414">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die den Dienst Azure-Gesichtserkennung erkennen Sie Gesichter in einem Image, und alle bekannten Gesichtern nutzt.</span><span class="sxs-lookup"><span data-stu-id="fbc35-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![Ergebnis der Abschluss dieses Kurses](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="fbc35-416">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="fbc35-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="fbc35-417">Übung 1</span><span class="sxs-lookup"><span data-stu-id="fbc35-417">Exercise 1</span></span>

<span data-ttu-id="fbc35-418">Die **Gesichtserkennungs-API von Azure** ist leistungsstark genug, um bis zu 64 Gesichter in ein einzelnes Abbild zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="fbc35-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="fbc35-419">Erweitern Sie die Anwendung, damit sie zwei oder drei Gesichter für viele andere Personen erkennen kann.</span><span class="sxs-lookup"><span data-stu-id="fbc35-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="fbc35-420">Übung 2</span><span class="sxs-lookup"><span data-stu-id="fbc35-420">Exercise 2</span></span>

<span data-ttu-id="fbc35-421">Die **Gesichtserkennungs-API von Azure** kann darüber hinaus geben Sie alle Arten von Informationen über Bildattribute zurück.</span><span class="sxs-lookup"><span data-stu-id="fbc35-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="fbc35-422">Integrieren Sie dies bei der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="fbc35-422">Integrate this into the application.</span></span> <span data-ttu-id="fbc35-423">Dies ist möglicherweise noch interessanter, in Kombination mit der [Emotionen-API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="fbc35-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
