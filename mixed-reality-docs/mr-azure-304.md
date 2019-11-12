---
title: Mr und Azure 304-Gesichtserkennung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Gesichtserkennung, hololens, immersive, VR
ms.openlocfilehash: 23676684c2ec325f9d6f1924e7a0bad14d41f13e
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926783"
---
>[!NOTE]
><span data-ttu-id="945c1-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="945c1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="945c1-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="945c1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="945c1-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="945c1-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="945c1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="945c1-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="945c1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="945c1-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="945c1-110">Mr und Azure 304: Gesichtserkennung</span><span class="sxs-lookup"><span data-stu-id="945c1-110">MR and Azure 304: Face recognition</span></span>

![Ergebnis der Fertigstellung dieses Kurses](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="945c1-112">In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Cognitive Services mit dem Microsoft-Gesichtserkennungs-API Funktionen zur Gesichtserkennung zu einer gemischten Reality-Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="945c1-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="945c1-113">*Azure Gesichtserkennungs-API* ist ein Microsoft-Dienst, der Entwicklern die fortschrittlichsten Gesichts Algorithmen in der Cloud bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="945c1-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="945c1-114">Der *Gesichtserkennungs-API* verfügt über zwei Hauptfunktionen: Gesichtserkennung mit Attributen und Gesichtserkennung.</span><span class="sxs-lookup"><span data-stu-id="945c1-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="945c1-115">Dies ermöglicht es Entwicklern, einfach einen Satz von Gruppen für Gesichter festzulegen und dann Abfrage Images später an den Dienst zu senden, um zu bestimmen, wem ein Gesicht angehört.</span><span class="sxs-lookup"><span data-stu-id="945c1-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="945c1-116">Weitere Informationen finden Sie auf der [Seite mit der Gesichtserkennung in Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="945c1-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="945c1-117">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality hololens-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="945c1-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="945c1-118">Verwenden Sie eine **Tap-Geste** , um die Erfassung eines Bilds mithilfe der on-Board hololens-Kamera zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="945c1-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="945c1-119">Senden Sie das erfasste Abbild an den *Azure Gesichtserkennungs-API* -Dienst.</span><span class="sxs-lookup"><span data-stu-id="945c1-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="945c1-120">Empfangen der Ergebnisse des *Gesichtserkennungs-API* Algorithmus.</span><span class="sxs-lookup"><span data-stu-id="945c1-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="945c1-121">Verwenden Sie eine einfache Benutzeroberfläche, um den Namen der übereinstimmenden Personen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="945c1-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="945c1-122">Auf diese Weise erfahren Sie, wie Sie die Ergebnisse aus dem Gesichtserkennungs-API-Dienst in ihrer Unity-basierten gemischten Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="945c1-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="945c1-123">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="945c1-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="945c1-124">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="945c1-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="945c1-125">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="945c1-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="945c1-126">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="945c1-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="945c1-127">Natürlich</span><span class="sxs-lookup"><span data-stu-id="945c1-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="945c1-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="945c1-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="945c1-129"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="945c1-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="945c1-130">Mr und Azure 304: Gesichtserkennung</span><span class="sxs-lookup"><span data-stu-id="945c1-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="945c1-131">✔️</span><span class="sxs-lookup"><span data-stu-id="945c1-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="945c1-132">✔️</span><span class="sxs-lookup"><span data-stu-id="945c1-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="945c1-133">Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets.</span><span class="sxs-lookup"><span data-stu-id="945c1-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="945c1-134">Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="945c1-135">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="945c1-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="945c1-136">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="945c1-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="945c1-137">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="945c1-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="945c1-138">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="945c1-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="945c1-139">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="945c1-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="945c1-140">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="945c1-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="945c1-141">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="945c1-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="945c1-142">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="945c1-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="945c1-143">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="945c1-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="945c1-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="945c1-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="945c1-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="945c1-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="945c1-146">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="945c1-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="945c1-147">Eine Kamera, die mit Ihrem PC verbunden ist (für die immersive Headset-Entwicklung)</span><span class="sxs-lookup"><span data-stu-id="945c1-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="945c1-148">Internet Zugriff für Azure-Setup und Gesichtserkennungs-API-Abruf</span><span class="sxs-lookup"><span data-stu-id="945c1-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="945c1-149">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="945c1-149">Before you start</span></span>

1.  <span data-ttu-id="945c1-150">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="945c1-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="945c1-151">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="945c1-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="945c1-152">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="945c1-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="945c1-153">Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="945c1-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="945c1-154">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="945c1-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="945c1-155">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="945c1-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="945c1-156">Kapitel 1: Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="945c1-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="945c1-157">Wenn Sie den *Gesichtserkennungs-API* -Dienst in Azure verwenden möchten, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="945c1-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="945c1-158">Melden Sie sich zunächst beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="945c1-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="945c1-159">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="945c1-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="945c1-160">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="945c1-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="945c1-161">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf " **neu** ", und suchen Sie nach *Gesichtserkennungs-API*. Drücken Sie dann die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="945c1-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Suchen nach der Face-API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="945c1-163">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="945c1-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="945c1-164">Auf der neuen Seite wird eine Beschreibung des *Gesichtserkennungs-API* Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="945c1-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="945c1-165">Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="945c1-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Gesichts-API-Informationen](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="945c1-167">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="945c1-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="945c1-168">Fügen Sie den gewünschten Namen für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="945c1-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="945c1-169">Wählen Sie ein Abonnement aus.</span><span class="sxs-lookup"><span data-stu-id="945c1-169">Select a subscription.</span></span>

    3. <span data-ttu-id="945c1-170">Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen *Gesichtserkennungs-API Dienst*erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="945c1-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="945c1-171">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="945c1-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="945c1-172">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="945c1-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="945c1-173">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="945c1-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="945c1-174">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="945c1-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="945c1-175">Die UWP-app " **Person Maker**", die Sie später verwenden, erfordert die Verwendung von "USA, Westen" für den Standort.</span><span class="sxs-lookup"><span data-stu-id="945c1-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="945c1-176">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="945c1-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="945c1-177">Wählen Sie \**erstellen *.**</span><span class="sxs-lookup"><span data-stu-id="945c1-177">Select **Create\*.**</span></span>

        ![Face-API-Dienst erstellen](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="945c1-179">Nachdem Sie auf " **Erstellen** " geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="945c1-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="945c1-180">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="945c1-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Benachrichtigung zur Dienst Erstellung](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="945c1-182">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="945c1-182">Click on the notifications to explore your new Service instance.</span></span>

    ![zur Ressourcen Benachrichtigung wechseln](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="945c1-184">Wenn Sie bereit sind, klicken Sie auf die Schaltfläche **zum Ressourcen** Wechsel in der Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="945c1-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![Zugriffs Gesichts-API-Schlüssel](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="945c1-186">In diesem Tutorial muss Ihre Anwendung Aufrufe an den Dienst durchführen. Dies erfolgt über das Abonnement "Key" Ihres dienstanzdienstanz.</span><span class="sxs-lookup"><span data-stu-id="945c1-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="945c1-187">Auf der Seite " *Schnellstart* " Ihres *Gesichtserkennungs-API* dienstanens ist der erste Punkt Nummer 1, um *Ihre Schlüssel zu erfassen.*</span><span class="sxs-lookup"><span data-stu-id="945c1-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="945c1-188">Wählen Sie auf der Seite *Dienst* entweder den Hyperlink Blue **Keys** (wenn auf der Seite Schnellstart) oder den Link **Schlüssel** im Navigationsmenü Dienste (auf der linken Seite, gekennzeichnet durch das Symbol "Schlüssel") aus, um Ihre Schlüssel anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="945c1-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="945c1-189">Notieren Sie sich entweder einen der Schlüssel, und schützen Sie ihn, da Sie ihn später benötigen.</span><span class="sxs-lookup"><span data-stu-id="945c1-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="945c1-190">Kapitel 2: Verwenden der UWP-Anwendung "Person Maker"</span><span class="sxs-lookup"><span data-stu-id="945c1-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="945c1-191">Stellen Sie sicher, dass Sie die vorgefertigte UWP-Anwendung namens [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="945c1-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="945c1-192">Diese APP ist nicht das Endprodukt für diesen Kurs, sondern nur ein Tool, das Sie beim Erstellen Ihrer Azure-Einträge unterstützt, auf die sich das spätere Projekt verlassen wird.</span><span class="sxs-lookup"><span data-stu-id="945c1-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="945c1-193">**Person Maker** ermöglicht Ihnen das Erstellen von Azure-Einträgen, die Personen und Personengruppen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="945c1-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="945c1-194">Die Anwendung platziert alle benötigten Informationen in einem Format, das später von der faceapi verwendet werden kann, um die Gesichter der von Ihnen hinzugefügten Personen zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="945c1-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="945c1-195">Wichtig **Person Maker** verwendet einige grundlegende Einschränkungen, um sicherzustellen, dass Sie die Anzahl von Dienst aufrufen pro Minute für die **Kostenlose Abonnement Ebene**nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="945c1-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="945c1-196">Der grüne Text oben ändert sich in rot und wird als "aktiv" aktualisiert, wenn eine Drosselung auftritt. Wenn dies der Fall ist, warten Sie einfach auf die Anwendung (es wird gewartet, bis der Zugriff auf den Gesichts Dienst fortgesetzt werden kann, und aktualisieren Sie ihn als "aktiv", wenn Sie ihn wieder verwenden können).</span><span class="sxs-lookup"><span data-stu-id="945c1-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="945c1-197">Diese Anwendung verwendet die *Microsoft. projectoxford. Face* -Bibliotheken, die es Ihnen ermöglichen, den Gesichtserkennungs-API vollständig zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="945c1-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="945c1-198">Diese Bibliothek steht als nuget-Paket kostenlos zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="945c1-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="945c1-199">Weitere Informationen zu diesem und ähnlichen APIs [finden Sie im Artikel zur API-Referenz](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="945c1-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="945c1-200">Dabei handelt es sich nur um die erforderlichen Schritte. Anweisungen zum Ausführen dieser Schritte finden Sie weiter unten in diesem Dokument.</span><span class="sxs-lookup"><span data-stu-id="945c1-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="945c1-201">Die **Person Maker** -App ermöglicht Ihnen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="945c1-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="945c1-202">Erstellen Sie eine *Personengruppe*, die aus mehreren Personen besteht, denen Sie zugeordnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="945c1-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="945c1-203">Mit Ihrem Azure-Konto können Sie mehrere Personengruppen hosten.</span><span class="sxs-lookup"><span data-stu-id="945c1-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="945c1-204">Erstellen Sie eine *Person*, die Mitglied einer Person-Gruppe ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="945c1-205">Jeder Person sind mehrere *Gesichts* Bilder zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="945c1-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="945c1-206">Weisen Sie einer *Person* *Gesichtsbilder* zu, damit Ihr Azure Gesichtserkennungs-API-Dienst eine *Person* durch das entsprechende *Gesicht*erkennen kann.</span><span class="sxs-lookup"><span data-stu-id="945c1-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="945c1-207">*Trainieren* Sie Ihren *Azure Gesichtserkennungs-API-Dienst*.</span><span class="sxs-lookup"><span data-stu-id="945c1-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="945c1-208">Wenn Sie diese APP zum Erkennen von Benutzern Schulen möchten, benötigen Sie zehn (10) schließende Fotos für jede Person, die Sie der Person-Gruppe hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="945c1-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="945c1-209">Die Windows 10-CAM-App kann Sie dabei unterstützen.</span><span class="sxs-lookup"><span data-stu-id="945c1-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="945c1-210">Sie müssen sicherstellen, dass jedes Foto klar ist (vermeiden Sie die verwierung, verdeckt oder zu weit vom Betreff), dass das Foto im JPG-oder PNG-Dateiformat vorliegt, wobei die Bilddatei nicht größer als **4 MB**und nicht kleiner als **1 KB**ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="945c1-211">Wenn Sie dieses Lernprogramm befolgen, sollten Sie sich nicht für das Training mit ihrer eigenen Oberfläche beschäftigen, denn wenn Sie die hololens auf dem Datenblatt platzieren, können Sie sich selbst nicht selbst ansehen.</span><span class="sxs-lookup"><span data-stu-id="945c1-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="945c1-212">Verwenden Sie die Oberfläche eines Kollegen oder Kollegen.</span><span class="sxs-lookup"><span data-stu-id="945c1-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="945c1-213">**Mitarbeiter Hersteller**wird ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="945c1-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="945c1-214">Öffnen Sie den Ordner **personmaker** , und doppelklicken Sie auf die Projekt Mappe *personmaker* , um Sie in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="945c1-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="945c1-215">Nachdem die *personmaker-Lösung* geöffnet ist, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="945c1-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="945c1-216">Die *Projektmappenkonfiguration* ist auf **Debug**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="945c1-217">Die *Lösungsplattform* ist auf **x86** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="945c1-218">Die *Zielplattform* ist der **lokale Computer**.</span><span class="sxs-lookup"><span data-stu-id="945c1-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="945c1-219">Sie müssen auch *nuget-Pakete wiederherstellen* (Klicken Sie mit der rechten Maustaste auf die Projekt Mappe, und wählen Sie **nuget-Pakete wiederherstellen**).</span><span class="sxs-lookup"><span data-stu-id="945c1-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="945c1-220">Klicken Sie auf *lokaler Computer* , und die Anwendung wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="945c1-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="945c1-221">Beachten Sie, dass auf kleineren Bildschirmen der gesamte Inhalt möglicherweise nicht sichtbar ist, Sie können jedoch einen Bildlauf nach unten durchführen, um ihn anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="945c1-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![Person Maker-Benutzeroberfläche](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="945c1-223">Fügen Sie Ihren **Azure-Authentifizierungsschlüssel**, den Sie haben sollten, aus Ihrem *Gesichtserkennungs-API* Service in Azure ein.</span><span class="sxs-lookup"><span data-stu-id="945c1-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="945c1-224">Setze</span><span class="sxs-lookup"><span data-stu-id="945c1-224">Insert:</span></span>

    1. <span data-ttu-id="945c1-225">Die *ID* , die Sie der Person- *Gruppe*zuweisen möchten.</span><span class="sxs-lookup"><span data-stu-id="945c1-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="945c1-226">Die ID muss aus Kleinbuchstaben bestehen und darf keine Leerzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="945c1-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="945c1-227">Notieren Sie sich diese ID, da Sie später in Ihrem Unity-Projekt benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="945c1-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="945c1-228">Der *Name* , den Sie der Person- *Gruppe* zuweisen möchten (kann Leerzeichen enthalten).</span><span class="sxs-lookup"><span data-stu-id="945c1-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="945c1-229">Klicken Sie auf die Schaltfläche **Personengruppe erstellen** .</span><span class="sxs-lookup"><span data-stu-id="945c1-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="945c1-230">Unterhalb der Schaltfläche sollte eine Bestätigungsmeldung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="945c1-231">Wenn Sie den Fehler "Zugriff verweigert" haben, überprüfen Sie den Speicherort, den Sie für Ihren Azure-Dienst festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="945c1-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="945c1-232">Wie bereits erwähnt, ist diese APP für "USA, Westen" konzipiert.</span><span class="sxs-lookup"><span data-stu-id="945c1-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="945c1-233">Sie werden feststellen, dass Sie auch auf die Schaltfläche " **eine bekannte Gruppe abrufen** " klicken können: Dies ist für den Fall, dass Sie bereits eine Person-Gruppe erstellt haben und diese verwenden möchten, anstatt eine neue zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="945c1-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="945c1-234">Wenn Sie auf *eine Personengruppe* mit einer bekannten Gruppe erstellen klicken, wird auch eine Gruppe abgerufen.</span><span class="sxs-lookup"><span data-stu-id="945c1-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="945c1-235">Fügen Sie den *Namen* der *Person* ein, die Sie erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="945c1-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="945c1-236">Klicken Sie auf die Schaltfläche **Person erstellen** .</span><span class="sxs-lookup"><span data-stu-id="945c1-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="945c1-237">Unterhalb der Schaltfläche sollte eine Bestätigungsmeldung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="945c1-238">Wenn Sie eine Person löschen möchten, die Sie zuvor erstellt haben, können Sie den Namen in das Textfeld schreiben und **Person löschen** drücken.</span><span class="sxs-lookup"><span data-stu-id="945c1-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="945c1-239">Stellen Sie sicher, dass Sie den Speicherort von zehn (10) Fotos der Person kennen, die Sie der Gruppe hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="945c1-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="945c1-240">Klicken Sie auf **Ordner erstellen und öffnen** , um Windows-Explorer in dem Ordner zu öffnen, der der Person zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="945c1-241">Fügen Sie die zehn (10) Images im Ordner hinzu.</span><span class="sxs-lookup"><span data-stu-id="945c1-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="945c1-242">Diese müssen ein *JPG* -oder *PNG* -Dateiformat aufweisen.</span><span class="sxs-lookup"><span data-stu-id="945c1-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="945c1-243">Klicken Sie auf über **Mitteln an Azure**.</span><span class="sxs-lookup"><span data-stu-id="945c1-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="945c1-244">Ein Gegenstand zeigt den Status der Übermittlung an, gefolgt von einer Meldung, wenn Sie abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="945c1-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="945c1-245">Nachdem der Leistungs Dienst abgeschlossen und eine Bestätigungsmeldung angezeigt wurde, klicken Sie auf " **trainieren** ", um den Dienst zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="945c1-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="945c1-246">Nachdem der Prozess abgeschlossen wurde, können Sie in Unity wechseln.</span><span class="sxs-lookup"><span data-stu-id="945c1-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="945c1-247">Kapitel 3: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="945c1-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="945c1-248">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="945c1-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="945c1-249">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="945c1-249">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="945c1-251">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="945c1-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="945c1-252">Fügen Sie **MR_FaceRecognition**ein.</span><span class="sxs-lookup"><span data-stu-id="945c1-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="945c1-253">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="945c1-254">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="945c1-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="945c1-255">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="945c1-255">Then, click **Create project**.</span></span>

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="945c1-257">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="945c1-258">Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="945c1-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="945c1-259">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="945c1-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="945c1-260">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="945c1-260">Close the **Preferences** window.</span></span>

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="945c1-262">Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="945c1-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="945c1-264">Wechseln Sie zu **Datei > Build-Einstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="945c1-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="945c1-265">**Zielgerät** ist auf **hololens** festgelegt</span><span class="sxs-lookup"><span data-stu-id="945c1-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="945c1-266">Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.</span><span class="sxs-lookup"><span data-stu-id="945c1-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="945c1-267">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="945c1-268">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="945c1-269">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="945c1-270">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="945c1-271">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="945c1-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="945c1-272">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="945c1-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="945c1-273">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="945c1-273">A save window will appear.</span></span>

            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="945c1-275">Wählen Sie die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="945c1-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="945c1-277">Öffnen Sie den neu erstellten Ordner **Szenen** , und geben Sie dann im Feld **Dateiname**: Text die Zeichen **Fläche fakerecscene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="945c1-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="945c1-279">Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="945c1-280">Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="945c1-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="945c1-282">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="945c1-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="945c1-283">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="945c1-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="945c1-284">Die **Skript** **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="945c1-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="945c1-285">Wenn Sie diese Änderung ändern, muss der Editor neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="945c1-286">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="945c1-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="945c1-287">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="945c1-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="945c1-289">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="945c1-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="945c1-290">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="945c1-290">**InternetClient**</span></span>
        - <span data-ttu-id="945c1-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="945c1-291">**Webcam**</span></span>

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="945c1-293">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="945c1-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="945c1-295">Wieder in den *Buildeinstellungen*ist **Unity C# -Projekte** nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="945c1-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="945c1-296">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="945c1-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="945c1-297">Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).</span><span class="sxs-lookup"><span data-stu-id="945c1-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="945c1-298">Kapitel 4: Einrichtung der Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="945c1-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="945c1-299">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)und als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="945c1-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="945c1-300">Beachten Sie, dass dieses Paket auch den Import der *newtonsoft-dll*enthält, die in [Kapitel 5](#chapter-5--import-the-newtonsoftjson-library)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="945c1-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="945c1-301">Mit diesem importierten Vorgang können Sie in [Kapitel 6](#chapter-6---create-the-faceanalysis-class)fortfahren.</span><span class="sxs-lookup"><span data-stu-id="945c1-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="945c1-302">Wählen Sie im Bereich *Hierarchie* die **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="945c1-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="945c1-303">Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor-Panel*sehen.</span><span class="sxs-lookup"><span data-stu-id="945c1-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="945c1-304">Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="945c1-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="945c1-305">Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="945c1-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="945c1-306">Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="945c1-307">**Klartext** auf voll **Tonfarbe** festlegen</span><span class="sxs-lookup"><span data-stu-id="945c1-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="945c1-308">Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest.</span><span class="sxs-lookup"><span data-stu-id="945c1-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![Einrichten von Kamerakomponenten](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="945c1-310">Kapitel 5 – Importieren der newtonsoft. JSON-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="945c1-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="945c1-311">Wenn Sie das ". unitypackage" im [letzten Kapitel](#chapter-4---main-camera-setup)importiert haben, können Sie dieses Kapitel überspringen.</span><span class="sxs-lookup"><span data-stu-id="945c1-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="945c1-312">Zum Deserialisieren und Serialisieren von Objekten, die empfangen und an den bot-Dienst gesendet werden, müssen Sie die *newtonsoft. JSON* -Bibliothek herunterladen.</span><span class="sxs-lookup"><span data-stu-id="945c1-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="945c1-313">Sie werden feststellen, dass eine kompatible Version bereits mit der richtigen Unity-Ordnerstruktur in dieser [Unity-Paketdatei](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)organisiert ist.</span><span class="sxs-lookup"><span data-stu-id="945c1-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="945c1-314">So importieren Sie die Bibliothek:</span><span class="sxs-lookup"><span data-stu-id="945c1-314">To import the library:</span></span>

1.  <span data-ttu-id="945c1-315">Laden Sie das Unity-Paket herunter.</span><span class="sxs-lookup"><span data-stu-id="945c1-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="945c1-316">Klicken Sie auf **Assets**, **Import Package**, **Custom Package**.</span><span class="sxs-lookup"><span data-stu-id="945c1-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importieren der Bibliothek "newtonsoft. JSON"](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="945c1-318">Suchen Sie nach dem Paket Unity, das Sie heruntergeladen haben, und klicken Sie auf Öffnen.</span><span class="sxs-lookup"><span data-stu-id="945c1-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="945c1-319">Stellen Sie sicher, dass alle Komponenten des Pakets getickt sind, und klicken Sie auf **importieren**.</span><span class="sxs-lookup"><span data-stu-id="945c1-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importieren der Bibliothek "newtonsoft. JSON"](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="945c1-321">Kapitel 6: Erstellen der faceanalysis-Klasse</span><span class="sxs-lookup"><span data-stu-id="945c1-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="945c1-322">Der Zweck der faceanalysis-Klasse besteht darin, die Methoden zu hosten, die für die Kommunikation mit Ihrem Azure-Gesichts Erkennungsdienst erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="945c1-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="945c1-323">Nachdem der Dienst ein Erfassungs Abbild gesendet hat, wird es analysiert und die Gesichter innerhalb von identifiziert, und es wird bestimmt, ob eine beliebige zu einer bekannten Person gehört.</span><span class="sxs-lookup"><span data-stu-id="945c1-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="945c1-324">Wenn eine bekannte Person gefunden wird, wird der Name dieser Klasse in der Szene als Benutzeroberflächen Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="945c1-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="945c1-325">So erstellen Sie die *faceanalysis* -Klasse:</span><span class="sxs-lookup"><span data-stu-id="945c1-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="945c1-326">Klicken Sie im Projekt Panel mit der rechten Maustaste in den *Ordner Objekte* , und klicken Sie dann auf > **Ordner** **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="945c1-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="945c1-327">Nennen Sie die Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="945c1-327">Call the folder **Scripts**.</span></span> 

    ![Erstellen Sie die faceanalysis-Klasse.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="945c1-329">Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="945c1-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="945c1-330">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf >  **C# Skript** **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="945c1-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="945c1-331">Nennen Sie das Skript *faceanalysis*.</span><span class="sxs-lookup"><span data-stu-id="945c1-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="945c1-332">Doppelklicken Sie auf das neue *faceanalysis* -Skript, um es mit Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="945c1-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="945c1-333">Geben Sie die folgenden Namespaces oberhalb der *faceanalysis* -Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="945c1-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="945c1-334">Nun müssen Sie alle-Objekte hinzufügen, die für die Deserialisierung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="945c1-335">Diese Objekte müssen **außerhalb** des *faceanalysis* -Skripts hinzugefügt werden (unterhalb der unteren geschweiften Klammer).</span><span class="sxs-lookup"><span data-stu-id="945c1-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

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
7. <span data-ttu-id="945c1-336">Die Methoden " *Start ()* " und " *Update ()* " werden nicht verwendet. löschen Sie Sie jetzt.</span><span class="sxs-lookup"><span data-stu-id="945c1-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="945c1-337">Fügen Sie in der *faceanalysis* -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="945c1-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

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
    > <span data-ttu-id="945c1-338">Ersetzen Sie den **Schlüssel** und die **persongroupid** durch ihren Dienst Schlüssel und die ID der Gruppe, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="945c1-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="945c1-339">Fügen Sie die *Awa()* -Methode hinzu, die die-Klasse initialisiert, indem Sie der Hauptkamera die *imagecapture* -Klasse hinzufügen und die Erstellungs Methode der Bezeichnung aufrufen:</span><span class="sxs-lookup"><span data-stu-id="945c1-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

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

10. <span data-ttu-id="945c1-340">Fügen Sie die Methode " *kreatelabel ()* " hinzu, die das *Label* -Objekt erstellt, um das Analyseergebnis anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="945c1-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

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

11. <span data-ttu-id="945c1-341">Fügen Sie die *erkenctfacesfromimage ()* -und die *getimageasbytearray ()* -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="945c1-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="945c1-342">Der erste fordert den Gesichts Erkennungsdienst auf, um alle möglichen Gesichter im übermittelten Abbild zu erkennen, während Letzteres erforderlich ist, um das erfasste Bild in ein Bytearray zu konvertieren:</span><span class="sxs-lookup"><span data-stu-id="945c1-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

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

12. <span data-ttu-id="945c1-343">Fügen Sie die *identifyfaces ()* -Methode hinzu, die den *Gesichts Erkennungsdienst* anfordert, alle bekannten Gesichter zu identifizieren, die zuvor im übermittelten Bild erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="945c1-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="945c1-344">Von der Anforderung wird eine ID der identifizierten Person, jedoch nicht der Name zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="945c1-344">The request will return an id of the identified person but not the name:</span></span>

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

            // Serialize to Json format
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

13. <span data-ttu-id="945c1-345">Fügen Sie die *GetPerson ()* -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="945c1-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="945c1-346">Durch die Angabe der Person-ID fordert diese Methode dann an, dass der *Gesichts Erkennungsdienst* den Namen der identifizierten Person zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="945c1-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

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

14.  <span data-ttu-id="945c1-347">Vergessen Sie nicht, die Änderungen zu **Speichern** , bevor Sie zum Unity-Editor zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="945c1-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="945c1-348">Ziehen Sie im Unity-Editor das faceanalysis-Skript aus dem Ordner Scripts im Projekt Panel auf das Hauptkamera Objekt im *Hierarchie Panel*.</span><span class="sxs-lookup"><span data-stu-id="945c1-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="945c1-349">Die neue Skript Komponente wird der Hauptkamera so hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="945c1-349">The new script component will be so added to the Main Camera.</span></span> 

![Legen Sie faceanalysis auf der Hauptkamera ab.](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="945c1-351">Kapitel 7: Erstellen der imagecapture-Klasse</span><span class="sxs-lookup"><span data-stu-id="945c1-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="945c1-352">Der Zweck der *imagecapture* -Klasse besteht darin, die Methoden zu hosten, die für die Kommunikation mit Ihrem *Azure-Gesichts Erkennungsdienst* erforderlich sind, um das Abbild zu analysieren, das Sie erfassen möchten, und zu ermitteln, ob es zu einer bekannten Person gehört.</span><span class="sxs-lookup"><span data-stu-id="945c1-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="945c1-353">Wenn eine bekannte Person gefunden wird, wird der Name dieser Klasse in der Szene als Benutzeroberflächen Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="945c1-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="945c1-354">So erstellen Sie die *imagecapture* -Klasse:</span><span class="sxs-lookup"><span data-stu-id="945c1-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="945c1-355">Klicken Sie **mit der rechten** Maustaste in den Skript Ordner, den Sie zuvor erstellt haben, und klicken Sie dann auf **Erstellen**,  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="945c1-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="945c1-356">Nennen Sie das Skript *imagecapture*.</span><span class="sxs-lookup"><span data-stu-id="945c1-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="945c1-357">Doppelklicken Sie auf das neue *imagecapture* -Skript, um es mit Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="945c1-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="945c1-358">Geben Sie die folgenden Namespaces oberhalb der imagecapture-Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="945c1-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="945c1-359">Fügen Sie in der *imagecapture* -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="945c1-359">Inside the *ImageCapture* class, add the following variables:</span></span>

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

5.  <span data-ttu-id="945c1-360">Fügen Sie die " *Awake ()* "-und " *Start ()* "-Methoden hinzu, die erforderlich sind, um die Klasse zu initialisieren, und die hololens die Gesten des Benutzers</span><span class="sxs-lookup"><span data-stu-id="945c1-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

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

6.  <span data-ttu-id="945c1-361">Fügen Sie den " *taphandler ()* " hinzu, der aufgerufen wird, wenn der Benutzer eine *Tap* -Geste ausführt:</span><span class="sxs-lookup"><span data-stu-id="945c1-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

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

7.  <span data-ttu-id="945c1-362">Fügen Sie die *executeimagecaptureandanalysis ()* -Methode hinzu, die den Prozess der Bild Erfassung startet:</span><span class="sxs-lookup"><span data-stu-id="945c1-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

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

8.  <span data-ttu-id="945c1-363">Fügen Sie die Handler hinzu, die aufgerufen werden, wenn der Foto Erfassungsprozess abgeschlossen wurde:</span><span class="sxs-lookup"><span data-stu-id="945c1-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="945c1-364">Vergessen Sie nicht, die Änderungen zu **Speichern** , bevor Sie zum Unity-Editor zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="945c1-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="945c1-365">Kapitel 8: aufbauen der Lösung</span><span class="sxs-lookup"><span data-stu-id="945c1-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="945c1-366">Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.</span><span class="sxs-lookup"><span data-stu-id="945c1-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="945c1-367">Bevor Sie vorgehen, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="945c1-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="945c1-368">Alle im Kapitel 3 erwähnten Einstellungen sind richtig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="945c1-369">Die Skript- *faceanalysis* ist an das Hauptkamera Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="945c1-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="945c1-370">Der Authentifizierungs **Schlüssel** und die **Gruppen-ID** wurden innerhalb des *faceanalysis* -Skripts festgelegt.</span><span class="sxs-lookup"><span data-stu-id="945c1-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="945c1-371">A: an dieser Stelle können Sie die Projekt Mappe erstellen.</span><span class="sxs-lookup"><span data-stu-id="945c1-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="945c1-372">Nachdem die Lösung erstellt wurde, können Sie Ihre Anwendung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="945c1-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="945c1-373">So beginnen Sie den Buildprozess:</span><span class="sxs-lookup"><span data-stu-id="945c1-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="945c1-374">Speichern Sie die aktuelle Szene, indem Sie auf Datei und dann auf Speichern klicken.</span><span class="sxs-lookup"><span data-stu-id="945c1-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="945c1-375">Wechseln Sie zu Datei, Buildeinstellungen, und klicken Sie auf offene Szenen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="945c1-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="945c1-376">Stellen Sie sicher, dass C# Sie Unity-Projekte teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="945c1-376">Make sure to tick Unity C# Projects.</span></span>

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="945c1-378">Klicken Sie auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="945c1-378">Press Build.</span></span> <span data-ttu-id="945c1-379">Auf diese Weise startet Unity ein Datei-Explorer-Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="945c1-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="945c1-380">Erstellen Sie diesen Ordner jetzt innerhalb des Unity-Projekts, und rufen Sie ihn App auf.</span><span class="sxs-lookup"><span data-stu-id="945c1-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="945c1-381">Klicken Sie dann mit ausgewähltem app-Ordner auf Ordner auswählen.</span><span class="sxs-lookup"><span data-stu-id="945c1-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="945c1-382">Unity erstellt das Projekt in den app-Ordner.</span><span class="sxs-lookup"><span data-stu-id="945c1-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="945c1-383">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein Datei-Explorer-Fenster am Speicherort des Builds geöffnet.</span><span class="sxs-lookup"><span data-stu-id="945c1-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="945c1-385">Öffnen Sie den app-Ordner, und öffnen Sie dann die neue Projekt Mappe (wie oben gezeigt, MR_FaceRecognition. sln).</span><span class="sxs-lookup"><span data-stu-id="945c1-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="945c1-386">Kapitel 9: Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="945c1-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="945c1-387">So stellen Sie auf hololens bereit:</span><span class="sxs-lookup"><span data-stu-id="945c1-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="945c1-388">Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden.</span><span class="sxs-lookup"><span data-stu-id="945c1-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="945c1-389">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="945c1-389">To do this:</span></span>

    1. <span data-ttu-id="945c1-390">Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.</span><span class="sxs-lookup"><span data-stu-id="945c1-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="945c1-391">Navigieren Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="945c1-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="945c1-392">Notieren Sie sich die **IPv4** -Adresse.</span><span class="sxs-lookup"><span data-stu-id="945c1-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="945c1-393">Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie dann **& Sicherheits > für Entwickler** .</span><span class="sxs-lookup"><span data-stu-id="945c1-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="945c1-394">Legen Sie den Entwicklermodus auf fest.</span><span class="sxs-lookup"><span data-stu-id="945c1-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="945c1-395">Navigieren Sie zu Ihrem neuen Unity-Build ( *App* -Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="945c1-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="945c1-396">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="945c1-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="945c1-397">Wählen Sie auf der Projektmappenplattform die Option **x86**, **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="945c1-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="945c1-399">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung**bereitstellen, um die Anwendung auf die hololens quer zuladen.</span><span class="sxs-lookup"><span data-stu-id="945c1-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="945c1-400">Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="945c1-401">Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest.</span><span class="sxs-lookup"><span data-stu-id="945c1-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="945c1-402">Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen**die Option *Lösung*bereitstellen auswählen.</span><span class="sxs-lookup"><span data-stu-id="945c1-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="945c1-403">Kapitel 10: Verwenden der Anwendung</span><span class="sxs-lookup"><span data-stu-id="945c1-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="945c1-404">Wenn Sie die hololens ausführen, starten Sie die app.</span><span class="sxs-lookup"><span data-stu-id="945c1-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="945c1-405">Sehen Sie sich die Person an, die Sie beim *Gesichtserkennungs-API*registriert haben.</span><span class="sxs-lookup"><span data-stu-id="945c1-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="945c1-406">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="945c1-406">Make sure that:</span></span>

    -  <span data-ttu-id="945c1-407">Das Gesicht der Person ist nicht zu weit und klar sichtbar.</span><span class="sxs-lookup"><span data-stu-id="945c1-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="945c1-408">Die Umgebungsbeleuchtung ist nicht zu dunkel.</span><span class="sxs-lookup"><span data-stu-id="945c1-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="945c1-409">Verwenden Sie die Tap-Geste, um das Bild der Person zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="945c1-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="945c1-410">Warten Sie, bis die APP die Analyse Anforderung sendet und eine Antwort erhält.</span><span class="sxs-lookup"><span data-stu-id="945c1-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="945c1-411">Wenn die Person erfolgreich erkannt wurde, wird der Name der Person als Benutzeroberflächen Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="945c1-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="945c1-412">Sie können den Aufzeichnungsprozess mit der TAP-Geste alle paar Sekunden wiederholen.</span><span class="sxs-lookup"><span data-stu-id="945c1-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="945c1-413">Ihre fertiggestellte Azure Gesichtserkennungs-API-Anwendung</span><span class="sxs-lookup"><span data-stu-id="945c1-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="945c1-414">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure-Gesichts Erkennungsdienst nutzt, um Gesichter innerhalb eines Bilds zu erkennen und bekannte Gesichter zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="945c1-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![Ergebnis der Fertigstellung dieses Kurses](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="945c1-416">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="945c1-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="945c1-417">Übung 1</span><span class="sxs-lookup"><span data-stu-id="945c1-417">Exercise 1</span></span>

<span data-ttu-id="945c1-418">Der **Azure-Gesichtserkennungs-API** ist leistungsfähig genug, um bis zu 64 Gesichter in einem einzelnen Image zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="945c1-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="945c1-419">Erweitern Sie die Anwendung so, dass Sie unter vielen anderen Personen zwei oder drei Gesichter erkennen kann.</span><span class="sxs-lookup"><span data-stu-id="945c1-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="945c1-420">Übung 2</span><span class="sxs-lookup"><span data-stu-id="945c1-420">Exercise 2</span></span>

<span data-ttu-id="945c1-421">Der **Azure-Gesichtserkennungs-API** kann auch alle Arten von Attributinformationen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="945c1-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="945c1-422">Integrieren Sie diese in die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="945c1-422">Integrate this into the application.</span></span> <span data-ttu-id="945c1-423">Dies könnte noch interessanter sein, wenn Sie mit dem [Emotionen-API](https://azure.microsoft.com/services/cognitive-services/emotion/)kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="945c1-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/).</span></span>
