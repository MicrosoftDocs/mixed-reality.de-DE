---
title: MR und Azure 302b - Custom vision
description: Führen Sie diesen Kurs Informationen zum Trainieren von Machine Learning-Modell, und klicken Sie dann verwenden Sie das trainierte Modell zur Erkennung von ähnlicher Objekte innerhalb einer mixed Reality-Anwendung.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, benutzerdefiniertes maschinelles sehen, Hololens, immersive vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594225"
---
>[!NOTE]
><span data-ttu-id="66aec-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="66aec-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="66aec-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="66aec-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="66aec-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="66aec-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="66aec-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="66aec-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="66aec-110">MR und Azure 302b: Benutzerdefiniertes maschinelles sehen</span><span class="sxs-lookup"><span data-stu-id="66aec-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="66aec-111">In diesem Kurs erfahren Sie erkennen der benutzerdefinierten visuellen Inhalt in einem bereitgestellten Image mithilfe von Azure Custom Vision-Funktionen in einer mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="66aec-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="66aec-112">Dieser Dienst ermöglicht Ihnen zum Trainieren von Machine Learning-Modellen mithilfe von Objekt-Images.</span><span class="sxs-lookup"><span data-stu-id="66aec-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="66aec-113">Dann werden das trainierte Modell können Sie erkennen ähnliche Objekte, gemäß Bereitstellung durch die Kamera-Aufnahme von Microsoft HoloLens oder eine Kamera, die mit Ihrem PC für immersive Headsets von (VR) verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="66aec-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="66aec-115">Azure Custom Vision ist ein Microsoft Cognitive der Dienst Entwicklern ermöglicht, benutzerdefinierte bildklassifizierungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="66aec-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="66aec-116">Diese Klassifizierungen können dann mit neuen Images zur Erkennung von verwendet werden, oder klassifizieren, Objekte innerhalb dieses Image.</span><span class="sxs-lookup"><span data-stu-id="66aec-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="66aec-117">Der Dienst bietet eine einfache, benutzerfreundliche, online-Portal, um den Prozess zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="66aec-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="66aec-118">Weitere Informationen finden Sie auf die [Azure Custom Vision Service Seite](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="66aec-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="66aec-119">Nach Abschluss dieses Kurses verfügen Sie über ein mixed Reality-Anwendung die in zwei Modi arbeiten:</span><span class="sxs-lookup"><span data-stu-id="66aec-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="66aec-120">**Analysemodus**: Einrichten der Custom Vision Service manuell durch Hochladen von Images, Tags erstellen und Trainieren den Dienst zur Erkennung von verschiedenen Objekten (in diesem Fall Maus und Tastatur).</span><span class="sxs-lookup"><span data-stu-id="66aec-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="66aec-121">Sie erstellen dann eine HoloLens-app, die Erfassen von Abbildern, die Verwendung der Kamera, und versuchen, diese Objekte in der realen Welt erkennen.</span><span class="sxs-lookup"><span data-stu-id="66aec-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="66aec-122">**Trainieren Modus**: Implementieren Sie Code, mit denen ein "Training-Modus" in Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="66aec-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="66aec-123">Der Testmodus können Sie zum Erfassen von Abbildern verwenden die HoloLens Kamera, die erfassten Abbilder in den Dienst hochgeladen und Trainieren des Modells für benutzerdefiniertes maschinelles sehen.</span><span class="sxs-lookup"><span data-stu-id="66aec-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="66aec-124">In diesem Kurs erfahren Sie, wie die Ergebnisse in eine Unity-basierte Anwendung aus der Custom Vision Service zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="66aec-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="66aec-125">Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="66aec-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="66aec-126">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="66aec-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="66aec-127">Kurs</span><span class="sxs-lookup"><span data-stu-id="66aec-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="66aec-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="66aec-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="66aec-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="66aec-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="66aec-130">MR und Azure 302b: Benutzerdefiniertes maschinelles sehen</span><span class="sxs-lookup"><span data-stu-id="66aec-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="66aec-131">✔️</span><span class="sxs-lookup"><span data-stu-id="66aec-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="66aec-132">✔️</span><span class="sxs-lookup"><span data-stu-id="66aec-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="66aec-133">Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen.</span><span class="sxs-lookup"><span data-stu-id="66aec-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="66aec-134">Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden.</span><span class="sxs-lookup"><span data-stu-id="66aec-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="66aec-135">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="66aec-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66aec-136">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="66aec-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="66aec-137">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="66aec-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="66aec-138">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="66aec-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="66aec-139">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.</span><span class="sxs-lookup"><span data-stu-id="66aec-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="66aec-140">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="66aec-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="66aec-141">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="66aec-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="66aec-142">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="66aec-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="66aec-143">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="66aec-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="66aec-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="66aec-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="66aec-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="66aec-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="66aec-146">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="66aec-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="66aec-147">Eine Kamera, die Verbindung mit Ihrem PC (für immersive Kopfhörer Entwicklung)</span><span class="sxs-lookup"><span data-stu-id="66aec-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="66aec-148">Zugriff auf das Internet für die Einrichtung von Azure und Datenabruf für benutzerdefiniertes maschinelles sehen-API</span><span class="sxs-lookup"><span data-stu-id="66aec-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="66aec-149">Eine Reihe von mindestens fünf (5) Bildern (zehn (10) empfohlen) für jedes Objekt, das Sie mit der Custom Vision Service erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="66aec-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="66aec-150">Wenn Sie möchten, können Sie [die bereits in diesem Kurs (Computermaus und Tastatur) bereitgestellten Images ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="66aec-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="66aec-151">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="66aec-151">Before you start</span></span>

1.  <span data-ttu-id="66aec-152">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="66aec-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="66aec-153">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="66aec-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="66aec-154">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="66aec-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="66aec-155">Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-app (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="66aec-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="66aec-156">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="66aec-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="66aec-157">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="66aec-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="66aec-158">Kapitel 1: das Custom Vision Service-Portal</span><span class="sxs-lookup"><span data-stu-id="66aec-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="66aec-159">Verwenden der *Custom Vision Service* in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="66aec-160">Zuerst [navigieren Sie zu der *Custom Vision Service* Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="66aec-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="66aec-161">Klicken Sie auf die **Einstieg** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="66aec-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="66aec-162">Melden Sie sich bei der *Custom Vision Service* Portal.</span><span class="sxs-lookup"><span data-stu-id="66aec-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="66aec-163">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="66aec-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="66aec-164">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="66aec-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="66aec-165">Nachdem Sie sich zum ersten Mal angemeldet sind, Sie werden aufgefordert, mit der *Vertragsbedingungen* Bereich.</span><span class="sxs-lookup"><span data-stu-id="66aec-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="66aec-166">Klicken Sie auf das Kontrollkästchen, um den Bedingungen zustimmen.</span><span class="sxs-lookup"><span data-stu-id="66aec-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="66aec-167">Klicken Sie dann auf **ich stimme zu**.</span><span class="sxs-lookup"><span data-stu-id="66aec-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="66aec-168">Die Begriffe zugestimmt haben, Sie werden navigiert werden, die *Projekte* -Abschnitt des Portals.</span><span class="sxs-lookup"><span data-stu-id="66aec-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="66aec-169">Klicken Sie auf **neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="66aec-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="66aec-170">Eine Registerkarte wird auf der rechten Seite angezeigt, wodurch Sie angeben, einige Felder für das Projekt angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="66aec-171">Fügen Sie eine *Namen* für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="66aec-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="66aec-172">Fügen Sie eine *Beschreibung* für Ihr Projekt (*optional*).</span><span class="sxs-lookup"><span data-stu-id="66aec-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="66aec-173">Wählen Sie eine *Ressourcengruppe* oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="66aec-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="66aec-174">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="66aec-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="66aec-175">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="66aec-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="66aec-176">Legen Sie die *Projekttypen* zu **Klassifizierung**</span><span class="sxs-lookup"><span data-stu-id="66aec-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="66aec-177">Legen Sie die *Domänen* als **allgemeine**.</span><span class="sxs-lookup"><span data-stu-id="66aec-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="66aec-178">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="66aec-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="66aec-179">Sobald Sie fertig sind, klicken Sie auf **projekterstellung**, Sie zu dem Custom Vision Service, Projekt – Seite umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="66aec-180">Kapitel 2 – trainieren Ihr Projekt Custom Vision</span><span class="sxs-lookup"><span data-stu-id="66aec-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="66aec-181">Einmal ist im Custom Vision-Portal Ihr Hauptziel zum Trainieren des Projekts für bestimmte Objekte in Bildern zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="66aec-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="66aec-182">Sie benötigen mindestens fünf (5) Bilder, obwohl zehn (10) wird empfohlen, für jedes Objekt, das Ihre Anwendung erkennen soll.</span><span class="sxs-lookup"><span data-stu-id="66aec-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="66aec-183">[Sie können die in diesem Kurs (Computermaus und Tastatur) bereitgestellten Images](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="66aec-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="66aec-184">Trainieren Sie Ihr Projekt Custom Vision Service:</span><span class="sxs-lookup"><span data-stu-id="66aec-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="66aec-185">Klicken Sie auf die **+** neben **Tags.**</span><span class="sxs-lookup"><span data-stu-id="66aec-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="66aec-186">Hinzufügen der **Namen** des Objekts, die Sie erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="66aec-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="66aec-187">Klicken Sie auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="66aec-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="66aec-188">Sie sehen Ihre **Tag** hinzugefügt wurde (möglicherweise müssen Sie Ihrer Seite angezeigt werden neu laden).</span><span class="sxs-lookup"><span data-stu-id="66aec-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="66aec-189">Aktivieren Sie das Kontrollkästchen neben Ihr neues Tag, wenn er noch nicht aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="66aec-190">Klicken Sie auf **Hinzufügen von Abbildern** in der Mitte der Seite.</span><span class="sxs-lookup"><span data-stu-id="66aec-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="66aec-191">Klicken Sie auf **lokale Dateien durchsuchen**, und suchen, und wählen Sie dann, die Bilder, Sie möchten, und die minimale hochladen, fünf (5).</span><span class="sxs-lookup"><span data-stu-id="66aec-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="66aec-192">Denken Sie daran, dass alle diese Images auf das Objekt enthalten sollte, die Sie trainieren werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="66aec-193">Sie können mehrere Images zu einem Zeitpunkt, zum Hochladen auswählen.</span><span class="sxs-lookup"><span data-stu-id="66aec-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="66aec-194">Nachdem Sie die Bilder auf der Registerkarte sehen können, wählen Sie das entsprechende Tag in die **Meine Tags** Feld.</span><span class="sxs-lookup"><span data-stu-id="66aec-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="66aec-195">Klicken Sie auf **Hochladen von Dateien**.</span><span class="sxs-lookup"><span data-stu-id="66aec-195">Click on **Upload files**.</span></span> <span data-ttu-id="66aec-196">Hochladen beginnt die Dateien.</span><span class="sxs-lookup"><span data-stu-id="66aec-196">The files will begin uploading.</span></span> <span data-ttu-id="66aec-197">Nachdem Sie die Bestätigung für das Hochladen haben, klicken Sie auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="66aec-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="66aec-198">Wiederholen Sie den gleichen Prozess zum Erstellen eines neuen **Tag** mit dem Namen **Tastatur** und die entsprechenden Fotos dafür hochladen.</span><span class="sxs-lookup"><span data-stu-id="66aec-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="66aec-199">Stellen Sie sicher, dass **deaktivieren** *Maus* nach dem Erstellen der neuen Tags, zum Anzeigen der *Hinzufügen von Bildern* Fenster.</span><span class="sxs-lookup"><span data-stu-id="66aec-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="66aec-200">Sobald Sie beide Tags eingerichtet haben, klicken Sie auf **Train**, und die erste Iteration von Schulungen mit der Erstellung.</span><span class="sxs-lookup"><span data-stu-id="66aec-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="66aec-201">Nachdem es erstellt wurde, werden Sie zwei Schaltflächen angezeigt werden **Standard** und **Vorhersage URL**.</span><span class="sxs-lookup"><span data-stu-id="66aec-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="66aec-202">Klicken Sie auf **Standard** zuerst, klicken Sie dann auf auf **Vorhersage URL**.</span><span class="sxs-lookup"><span data-stu-id="66aec-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="66aec-203">Die Endpunkt-URL, die von diesem bereitgestellt wird, je nachdem, was je nastaven *Iteration* als Standard gekennzeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="66aec-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="66aec-204">Also, wenn Sie später einen neuen vornehmen *Iteration* und als Standard zu aktualisieren, müssen Sie nicht zum Ändern Ihres Codes.</span><span class="sxs-lookup"><span data-stu-id="66aec-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="66aec-205">Sobald Sie auf geklickt haben *Vorhersage URL*öffnen *Editor*, und kopieren und Einfügen der **URL** und **Vorhersage-Schlüssel**, damit können Sie bei Bedarf später im Code abrufen.</span><span class="sxs-lookup"><span data-stu-id="66aec-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="66aec-206">Klicken Sie auf die **Zahnrad** am oberen rechten Rand des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="66aec-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="66aec-207">Kopieren der **Training Schlüssel** , und fügen Sie ihn in eine *Editor*, für die spätere Verwendung.</span><span class="sxs-lookup"><span data-stu-id="66aec-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="66aec-208">Kopieren Sie außerdem Ihre **Projekt-Id**, und außerdem fügen Sie ihn in Ihre *Editor* -Datei für die spätere Verwendung.</span><span class="sxs-lookup"><span data-stu-id="66aec-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="66aec-209">Kapitel 3: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="66aec-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="66aec-210">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="66aec-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="66aec-211">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="66aec-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="66aec-212">Sie müssen jetzt einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="66aec-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="66aec-213">Fügen Sie **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="66aec-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="66aec-214">Stellen Sie sicher, dass die Projektvorlage nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="66aec-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="66aec-215">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="66aec-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="66aec-216">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="66aec-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="66aec-217">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="66aec-218">Wechseln Sie zu **bearbeiten* > *Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="66aec-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="66aec-219">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="66aec-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="66aec-220">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="66aec-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="66aec-221">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="66aec-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="66aec-222">In der **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="66aec-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="66aec-223">**Geräte** nastaven NA hodnotu **Hololens**</span><span class="sxs-lookup"><span data-stu-id="66aec-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="66aec-224">Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.</span><span class="sxs-lookup"><span data-stu-id="66aec-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="66aec-225">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="66aec-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="66aec-226">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="66aec-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="66aec-227">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="66aec-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="66aec-228">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="66aec-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="66aec-229">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="66aec-230">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="66aec-231">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="66aec-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="66aec-232">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="66aec-233">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname:* Textfeld **CustomVisionScene**, klicken Sie dann auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="66aec-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="66aec-234">Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen.</span><span class="sxs-lookup"><span data-stu-id="66aec-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="66aec-235">Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="66aec-236">Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="66aec-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="66aec-237">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="66aec-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="66aec-238">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="66aec-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="66aec-239">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="66aec-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="66aec-240">**Scripting Runtime Version** muss **experimentell (.NET 4.6 Äquivalent)**, löst der Editor neu starten müssen.</span><span class="sxs-lookup"><span data-stu-id="66aec-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="66aec-241">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="66aec-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="66aec-242">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="66aec-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="66aec-243">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="66aec-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="66aec-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="66aec-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="66aec-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="66aec-245">**Webcam**</span></span>

        3. <span data-ttu-id="66aec-246">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="66aec-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="66aec-247">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="66aec-248">Im *Buildeinstellungen* *Unity C\# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="66aec-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="66aec-249">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="66aec-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="66aec-250">Speichern Sie Ihre Szene und das Projekt (**Datei > SZENE speichern / FILE > Projekt speichern**).</span><span class="sxs-lookup"><span data-stu-id="66aec-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="66aec-251">Kapitel 4: importieren die Newtonsoft-DLL in Unity</span><span class="sxs-lookup"><span data-stu-id="66aec-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66aec-252">Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="66aec-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="66aec-253">Dieser Kurs erfordert die Verwendung der **Newtonsoft** -Bibliothek, die Sie als eine DLL-Datei mit Ihren Ressourcen hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="66aec-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="66aec-254">Das Paket mit [dieser Bibliothek heruntergeladen werden kann, über diesen Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="66aec-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="66aec-255">Um die Newtonsoft-Bibliothek in Ihr Projekt zu importieren, verwenden Sie das Unity-Paket, das in diesem Kurs stammt.</span><span class="sxs-lookup"><span data-stu-id="66aec-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="66aec-256">Hinzufügen der *.unitypackage* in Unity mithilfe der **Assets* > *Import* *Paket*  >  *Benutzerdefinierte* *Paket** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="66aec-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="66aec-257">In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="66aec-258">Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="66aec-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="66aec-259">Wechseln Sie zu der **Newtonsoft** Unterordner **-Plug-Ins** im Projekt anzeigen, und wählen die *"newtonsoft.JSON"-Plug-Ins*.</span><span class="sxs-lookup"><span data-stu-id="66aec-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="66aec-260">Mit der *"newtonsoft.JSON"-Plug-Ins* ausgewählt haben, stellen sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **WSAPlayer** ist auch **deaktiviert**, klicken Sie dann auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="66aec-261">Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="66aec-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="66aec-262">Markieren diese-Plug-Ins konfiguriert sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="66aec-263">Es gibt ein anderen Satz von ihnen im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="66aec-264">Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **Newtonsoft** Ordner.</span><span class="sxs-lookup"><span data-stu-id="66aec-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="66aec-265">Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="66aec-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="66aec-266">Wählen Sie die Datei, und klicken Sie dann im Inspector sicher, dass</span><span class="sxs-lookup"><span data-stu-id="66aec-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="66aec-267">**Jede Plattform** ist **deaktiviert**</span><span class="sxs-lookup"><span data-stu-id="66aec-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="66aec-268">**nur** **WSAPlayer** ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="66aec-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="66aec-269">**Nicht verarbeiten** ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="66aec-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="66aec-270">Kapitel 5 – kamerasetup</span><span class="sxs-lookup"><span data-stu-id="66aec-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="66aec-271">Wählen Sie im Bereich mit den-Hierarchie der *Main Camera*.</span><span class="sxs-lookup"><span data-stu-id="66aec-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="66aec-272">Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den *Main Camera* in die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="66aec-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="66aec-273">Die *Kamera* Objekt muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="66aec-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="66aec-274">Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="66aec-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="66aec-275">Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="66aec-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="66aec-276">Legen Sie **löschen Flags** zu **Volltonfarbe** (ignorieren Sie dies für immersive Kopfhörer).</span><span class="sxs-lookup"><span data-stu-id="66aec-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="66aec-277">Legen Sie die **Hintergrund** Farbe der Kamera Komponente **Schwarz, Alpha 0 (Hex-Code: #00000000)** (ignorieren Sie dies für immersive Kopfhörer).</span><span class="sxs-lookup"><span data-stu-id="66aec-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="66aec-278">Kapitel 6: Erstellen Sie die CustomVisionAnalyser-Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="66aec-279">An diesem Punkt können Sie Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="66aec-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="66aec-280">Beginnen Sie mit der *CustomVisionAnalyser* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="66aec-281">Die Aufrufe an die **Custom Vision Service** vorgenommen werden, in dem gezeigten Code unten erfolgen mithilfe der **Custom Vision-REST-API**.</span><span class="sxs-lookup"><span data-stu-id="66aec-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="66aec-282">Durch die Verwendung dieser, erfahren Sie, wie zu implementieren und Verwenden dieser API (nützlich, um zu verstehen, wie etwa selbst implementiert).</span><span class="sxs-lookup"><span data-stu-id="66aec-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="66aec-283">Denken Sie, dass Microsoft bietet eine **Custom Vision Service SDK** , auch für Aufrufe an den Dienst verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="66aec-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="66aec-284">Weitere Informationen finden Sie auf die [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) Artikel.</span><span class="sxs-lookup"><span data-stu-id="66aec-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="66aec-285">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="66aec-285">This class is responsible for:</span></span>

-   <span data-ttu-id="66aec-286">Laden das neueste Image als ein Array von Bytes erfasst.</span><span class="sxs-lookup"><span data-stu-id="66aec-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="66aec-287">Das Bytearray an Azure senden *Custom Vision Service* Instanz für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="66aec-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="66aec-288">Empfangen der Antwort als JSON-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="66aec-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="66aec-289">Die Antwort zu deserialisieren, und übergeben die resultierenden *Vorhersage* auf die *SceneOrganiser* -Klasse, die kümmern wird wie die Antwort angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="66aec-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="66aec-290">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-290">To create this class:</span></span>

1.  <span data-ttu-id="66aec-291">Mit der rechten Maustaste den *Ordner "Assets"* befindet sich in der *Projektfenster*, klicken Sie dann auf **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="66aec-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="66aec-292">Rufen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="66aec-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="66aec-293">Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="66aec-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="66aec-294">Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="66aec-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="66aec-295">Nennen Sie das Skript *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="66aec-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="66aec-296">Doppelklicken Sie auf die neue *CustomVisionAnalyser* Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="66aec-297">Aktualisieren Sie die Namespaces am Anfang der Datei mit folgendem übereinstimmt:</span><span class="sxs-lookup"><span data-stu-id="66aec-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="66aec-298">In der *CustomVisionAnalyser* -Klasse verwenden, fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="66aec-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="66aec-299">Stellen Sie sicher, dass Sie Einfügen Ihrer **Vorhersage Schlüssel** in die **PredictionKey** Variable und Ihr **Endpunkt der Vorhersage** in die **PredictionEndpoint** Variable.</span><span class="sxs-lookup"><span data-stu-id="66aec-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="66aec-300">Sie kopiert haben, diese *Editor* weiter oben in diesem Kurs.</span><span class="sxs-lookup"><span data-stu-id="66aec-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="66aec-301">Code für **Awake()** muss nun hinzugefügt werden, um die Instanz-Variable zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="66aec-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="66aec-302">Löschen Sie die Methoden **Start()** und **Update()**.</span><span class="sxs-lookup"><span data-stu-id="66aec-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="66aec-303">Fügen Sie als Nächstes die Coroutine (mit der statischen **GetImageAsByteArray()** Methode darunter), die erhalten die Ergebnisse der Analyse des Bilds von erfasst die *digitale Bilder* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66aec-304">In der **AnalyseImageCapture** Coroutine, erfolgt ein Aufruf von der *SceneOrganiser* -Klasse, die Sie noch erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="66aec-305">Aus diesem Grund **lassen Sie diese Zeilen jetzt kommentiert**.</span><span class="sxs-lookup"><span data-stu-id="66aec-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="66aec-306">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="66aec-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="66aec-307">Kapitel 7: Erstellen Sie die CustomVisionObjects-Klasse</span><span class="sxs-lookup"><span data-stu-id="66aec-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="66aec-308">Die Klasse, die Sie erstellen nun ist die *CustomVisionObjects* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="66aec-309">Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen verwendet werden, zum Serialisieren und Deserialisieren der Aufrufe an die *Custom Vision Service*.</span><span class="sxs-lookup"><span data-stu-id="66aec-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="66aec-310">Es ist wichtig, dass Sie den Endpunkt, die Ihnen notieren, als von der Custom Vision Service bietet die folgenden JSON-Code Struktur eingerichtet wurde, arbeiten mit [ *Custom Vision Vorhersage v2. 0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="66aec-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="66aec-311">Wenn Sie eine andere Version haben, müssen Sie möglicherweise zum Aktualisieren der folgenden Struktur.</span><span class="sxs-lookup"><span data-stu-id="66aec-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="66aec-312">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-312">To create this class:</span></span>

1.  <span data-ttu-id="66aec-313">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="66aec-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="66aec-314">Rufen Sie das Skript *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="66aec-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="66aec-315">Doppelklicken Sie auf die neue **CustomVisionObjects** Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="66aec-316">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="66aec-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="66aec-317">Löschen der **Start()** und **Update()** Methoden innerhalb der *CustomVisionObjects* Klasse; diese Klasse sollte jetzt leer sein.</span><span class="sxs-lookup"><span data-stu-id="66aec-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="66aec-318">Fügen Sie die folgenden Klassen **außerhalb** der *CustomVisionObjects* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="66aec-319">Diese Objekte werden verwendet, durch die *Newtonsoft* Bibliothek zum Serialisieren und Deserialisieren die Antwortdaten werden:</span><span class="sxs-lookup"><span data-stu-id="66aec-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="66aec-320">Kapitel 8 – erstellen Sie die VoiceRecognizer-Klasse</span><span class="sxs-lookup"><span data-stu-id="66aec-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="66aec-321">Diese Klasse erkennt die Spracheingabe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="66aec-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="66aec-322">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-322">To create this class:</span></span>

1.  <span data-ttu-id="66aec-323">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="66aec-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="66aec-324">Rufen Sie das Skript *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="66aec-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="66aec-325">Doppelklicken Sie auf die neue **VoiceRecognizer** Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="66aec-326">Fügen Sie die folgenden Namespaces, die oben genannten der *VoiceRecognizer* Klasse:</span><span class="sxs-lookup"><span data-stu-id="66aec-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="66aec-327">Klicken Sie dann fügen Sie die folgenden Variablen in der *VoiceRecognizer* Klasse, über die *Start()* Methode:</span><span class="sxs-lookup"><span data-stu-id="66aec-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="66aec-328">Hinzufügen der **Awake()** und **Start()** Methoden, von denen letzterer, nach dem Benutzer festgelegt wird *Schlüsselwörter* erkannt werden, wenn Sie ein Tag zu einem Bild zu verknüpfen:</span><span class="sxs-lookup"><span data-stu-id="66aec-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="66aec-329">Löschen der **Update()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="66aec-330">Fügen Sie den folgenden Ereignishandler, der aufgerufen wird, wenn Sie Spracheingabe erkannt wird:</span><span class="sxs-lookup"><span data-stu-id="66aec-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="66aec-331">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="66aec-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="66aec-332">Aber keine Sorge, über Code, die einen Fehler, angezeigt werden kann, wie Sie bald weitere Klassen bereitstellen möchten, die diese behoben werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="66aec-333">Kapitel 9 – erstellen Sie die CustomVisionTrainer-Klasse</span><span class="sxs-lookup"><span data-stu-id="66aec-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="66aec-334">Diese Klasse wird eine Reihe von Web-Aufrufe zum Trainieren Verketten der *Custom Vision Service*.</span><span class="sxs-lookup"><span data-stu-id="66aec-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="66aec-335">Jeder Aufruf werden direkt über den Code ausführlich erläutert.</span><span class="sxs-lookup"><span data-stu-id="66aec-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="66aec-336">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-336">To create this class:</span></span>

1.  <span data-ttu-id="66aec-337">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="66aec-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="66aec-338">Rufen Sie das Skript *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="66aec-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="66aec-339">Doppelklicken Sie auf die neue *CustomVisionTrainer* Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="66aec-340">Fügen Sie die folgenden Namespaces, die oben genannten der *CustomVisionTrainer* Klasse:</span><span class="sxs-lookup"><span data-stu-id="66aec-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="66aec-341">Klicken Sie dann fügen Sie die folgenden Variablen in der *CustomVisionTrainer* Klasse, über die **Start()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="66aec-342">Die hier verwendete Training-URL finden Sie in der *Custom Vision Training 1.2* Dokumentation und verfügt über eine Struktur von: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="66aec-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="66aec-343">Weitere Informationen finden Sie auf die [ *Custom Vision Training v1. 2-Referenz zur API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="66aec-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="66aec-344">Es ist wichtig, dass Sie den Endpunkt notieren, die der Custom Vision Service Sie für den Testmodus, wie die JSON-Struktur verwendet bereitstellt (innerhalb der **CustomVisionObjects** Klasse) eingerichtet wurde, arbeiten mit [  *Custom Vision Training v1. 2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="66aec-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="66aec-345">Wenn Sie eine andere Version haben, müssen Sie möglicherweise zum Aktualisieren der *Objekte* Struktur.</span><span class="sxs-lookup"><span data-stu-id="66aec-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="66aec-346">Stellen Sie sicher, dass Sie beim Hinzufügen Ihrer **Dienstschlüssel** (Training Schlüsselwert) und **Projekt-Id** Wert, der Sie notiert vorherigen; Dies sind die Werte Sie [gesammelt, die über das Portal weiter oben in der Kurs ( Kapitel 2, Schritt 10 oder höher)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="66aec-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="66aec-347">Fügen Sie die folgenden **Start()** und **Awake()** Methoden.</span><span class="sxs-lookup"><span data-stu-id="66aec-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="66aec-348">Diese Methoden werden während der Initialisierung aufgerufen und den Aufruf zum Einrichten der Benutzeroberflächenautomatisierungs nicht enthalten:</span><span class="sxs-lookup"><span data-stu-id="66aec-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="66aec-349">Löschen der **Update()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-349">Delete the **Update()** method.</span></span> <span data-ttu-id="66aec-350">Diese Klasse wird dies nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66aec-350">This class will not need it.</span></span>

7.  <span data-ttu-id="66aec-351">Hinzufügen der **RequestTagSelection()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="66aec-352">Diese Methode ist das erste, die aufgerufen werden, wenn ein Image erfasst und im Gerät gespeichert wurden und ist nun bereit für die Übermittlung an die *Custom Vision Service*, um es zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="66aec-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="66aec-353">Diese Methode zeigt im Training-Benutzeroberfläche einen Satz von Schlüsselwörtern, mit denen der Benutzer das Image zu kennzeichnen, das aufgezeichnet wurden.</span><span class="sxs-lookup"><span data-stu-id="66aec-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="66aec-354">Sie erhalten ebenfalls eine Warnung der *VoiceRecognizer* Klasse, die überwacht, die dem Benutzer für die Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="66aec-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="66aec-355">Hinzufügen der **VerifyTag()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="66aec-356">Diese Methode erhält die Spracheingabe erkannt werden, indem die **VoiceRecognizer** Klasse und seine Gültigkeit zu überprüfen und damit beginnen, den Training.</span><span class="sxs-lookup"><span data-stu-id="66aec-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="66aec-357">Hinzufügen der **SubmitImageForTraining()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="66aec-358">Diese Methode wird der Trainingsprozess Custom Vision Service gestartet.</span><span class="sxs-lookup"><span data-stu-id="66aec-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="66aec-359">Der erste Schritt ist zum Abrufen der **Transponder-Id** aus dem Dienst, das das überprüfte Spracheingabe des Benutzers zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="66aec-360">Die **Transponder-Id** wird dann zusammen mit dem Bild hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="66aec-361">Hinzufügen der **TrainCustomVisionProject()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="66aec-362">Nachdem das Image übermittelt und markiert wurde, wird diese Methode aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="66aec-363">Erstellen sie eine neue Iteration, die mit all den vorherigen Abbildern, die an den Dienst und das Bild übermittelt trainiert werden gerade hochgeladen haben.</span><span class="sxs-lookup"><span data-stu-id="66aec-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="66aec-364">Nachdem das Training abgeschlossen wurde, ruft diese Methode eine Methode, um die neu erstellte festzulegen **Iteration** als **Standard**, sodass der Endpunkt, die Sie für die Analyse verwenden der aktuellen Iteration trainierten sind.</span><span class="sxs-lookup"><span data-stu-id="66aec-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="66aec-365">Hinzufügen der **SetDefaultIteration()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="66aec-366">Dieser Methode wird festgelegt, die zuvor erstellte und trainierte Iteration als *Standard*.</span><span class="sxs-lookup"><span data-stu-id="66aec-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="66aec-367">Nach Abschluss müssen dieser Methode Sie die vorhergehenden Iteration im Dienst vorhandene zu löschen.</span><span class="sxs-lookup"><span data-stu-id="66aec-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="66aec-368">Zum Zeitpunkt des Schreibens von diesem Kurs ist es maximal eine maximale Anzahl zehn (10) von Iterationen gleichzeitig im Dienst vorhanden sein können.</span><span class="sxs-lookup"><span data-stu-id="66aec-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="66aec-369">Hinzufügen der **DeletePreviousIteration()** Methode.</span><span class="sxs-lookup"><span data-stu-id="66aec-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="66aec-370">Diese Methode wird suchen und Löschen von der vorhergehenden Iteration für nicht standardmäßige:</span><span class="sxs-lookup"><span data-stu-id="66aec-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="66aec-371">Die letzte Methode in dieser Klasse hinzufügen ist die **GetImageAsByteArray()** Methode, die auf die Webserviceaufrufe verwendet, um das Bild erfasst in ein Bytearray zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="66aec-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="66aec-372">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="66aec-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="66aec-373">Kapitel 10 – erstellen Sie die SceneOrganiser-Klasse</span><span class="sxs-lookup"><span data-stu-id="66aec-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="66aec-374">Diese Klasse führt Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="66aec-374">This class will:</span></span>

-   <span data-ttu-id="66aec-375">Erstellen Sie eine **Cursor** bis zur Kamera Main anzufügendes Objekt.</span><span class="sxs-lookup"><span data-stu-id="66aec-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="66aec-376">Erstellen Sie eine **Bezeichnung** -Objekt, das angezeigt wird, wenn der Dienst die reale Objekte erkennt.</span><span class="sxs-lookup"><span data-stu-id="66aec-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="66aec-377">Richten Sie die Main Camera aus, indem Sie die entsprechenden Komponenten anfügen, zu.</span><span class="sxs-lookup"><span data-stu-id="66aec-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="66aec-378">Im **Analysemodus**, erzeugen die Bezeichnungen zur Laufzeit in die entsprechenden Raum relativ zur Position der Kamera, Main und Anzeigen der Daten, die von der Custom Vision Service erhalten.</span><span class="sxs-lookup"><span data-stu-id="66aec-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="66aec-379">Im **Testmodus**, erzeugen Sie die Benutzeroberfläche, die die verschiedenen Phasen des trainingsprozesses angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="66aec-380">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-380">To create this class:</span></span>

1.  <span data-ttu-id="66aec-381">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="66aec-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="66aec-382">Nennen Sie das Skript *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="66aec-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="66aec-383">Doppelklicken Sie auf die neue *SceneOrganiser* Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="66aec-384">Sie benötigen nur einen Namespace, entfernen Sie die anderen oben die *SceneOrganiser* Klasse:</span><span class="sxs-lookup"><span data-stu-id="66aec-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="66aec-385">Klicken Sie dann fügen Sie die folgenden Variablen in der *SceneOrganiser* Klasse, über die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="66aec-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="66aec-386">Löschen der **Start()** und **Update()** Methoden.</span><span class="sxs-lookup"><span data-stu-id="66aec-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="66aec-387">Fügen Sie direkt unterhalb der Variablen, die **Awake()** -Methode, die Initialisieren der Klasse und der Szene eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="66aec-388">Jetzt hinzufügen der **CreateCameraCursor()** Methode, die erstellt und platziert den Cursor Main Camera und **CreateLabel()** -Methode, die erstellt die **Analysis Bezeichnung** Objekt .</span><span class="sxs-lookup"><span data-stu-id="66aec-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="66aec-389">Hinzufügen der **SetCameraStatus()** -Methode, die Nachrichten für die Bereitstellung des Status der Kamera Mesh Text behandelt.</span><span class="sxs-lookup"><span data-stu-id="66aec-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="66aec-390">Hinzufügen der **PlaceAnalysisLabel()** und **SetTagsToLastLabel()** -Methoden, die erzeugt werden, und zeigen die Daten aus der Custom Vision Service, in der Szene.</span><span class="sxs-lookup"><span data-stu-id="66aec-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="66aec-391">Abschließend fügen die **CreateTrainingUI()** -Methode, die erzeugt wird die Benutzeroberfläche, die mehrere Phasen des trainingsprozesses angezeigt, wenn die Anwendung im Training-Modus befindet.</span><span class="sxs-lookup"><span data-stu-id="66aec-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="66aec-392">Diese Methode wird auch ein Showcase werden, um die Kamera-Status-Objekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="66aec-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="66aec-393">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="66aec-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66aec-394">Bevor Sie fortfahren, öffnen Sie die **CustomVisionAnalyser** -Klasse, und innerhalb der **AnalyseLastImageCaptured()** -Methode, *heben Sie die auskommentierung* die folgenden Zeilen:</span><span class="sxs-lookup"><span data-stu-id="66aec-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="66aec-395">Kapitel 11: Erstellen Sie die digitale Bilder-Klasse</span><span class="sxs-lookup"><span data-stu-id="66aec-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="66aec-396">Die nächste Klasse, die Sie erstellen wollen ist die *digitale Bilder* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="66aec-397">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="66aec-397">This class is responsible for:</span></span>

-   <span data-ttu-id="66aec-398">Erfassen eines Abbilds verwenden der Kamera HoloLens und speichern ihn in das *App* Ordner.</span><span class="sxs-lookup"><span data-stu-id="66aec-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="66aec-399">Behandeln von Tap-Gesten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="66aec-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="66aec-400">Verwalten der *Enum* -Wert, der bestimmt, ob die Anwendung, im ausgeführt wird *Analysis* Modus oder *Training* Modus.</span><span class="sxs-lookup"><span data-stu-id="66aec-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="66aec-401">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-401">To create this class:</span></span>

1.  <span data-ttu-id="66aec-402">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="66aec-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="66aec-403">Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen > C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="66aec-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="66aec-404">Nennen Sie das Skript *digitale Bilder*.</span><span class="sxs-lookup"><span data-stu-id="66aec-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="66aec-405">Doppelklicken Sie auf die neue **digitale Bilder** Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="66aec-406">Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="66aec-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="66aec-407">Klicken Sie dann fügen Sie die folgenden Variablen in der *digitale Bilder* Klasse, über die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="66aec-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="66aec-408">Code für **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss:</span><span class="sxs-lookup"><span data-stu-id="66aec-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="66aec-409">Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Bewegung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="66aec-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="66aec-410">In *Analysis* -Modus die **TapHandler** Methode fungiert als Option zum Starten oder Beenden der Schleife Capture Photo.</span><span class="sxs-lookup"><span data-stu-id="66aec-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="66aec-411">In *Training* Modus, es wird ein Image von der Kamera.</span><span class="sxs-lookup"><span data-stu-id="66aec-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="66aec-412">Wenn der Cursor grün ist, bedeutet dies, dass die Kamera verfügbar ist, wird das Bild ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="66aec-413">Wenn der Cursor Rot ist, bedeutet dies, dass die Kamera ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="66aec-414">Fügen Sie die Methode, die die Anwendung verwendet wird, starten den Prozess der abbilderfassung aus, und speichern Sie das Abbild hinzu.</span><span class="sxs-lookup"><span data-stu-id="66aec-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="66aec-415">Fügen Sie die Handler, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und wann es analysiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="66aec-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="66aec-416">Das Ergebnis wird dann zum Übergeben der *CustomVisionAnalyser* oder *CustomVisionTrainer* je nach verwendetem Modus der Code auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="66aec-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="66aec-417">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="66aec-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="66aec-418">Nun, dass alle Skripts abgeschlossen haben, wechseln Sie zurück im Unity-Editor, und ziehen dann die **SceneOrganiser** -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="66aec-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="66aec-419">Kapitel 12 – vor dem Erstellen</span><span class="sxs-lookup"><span data-stu-id="66aec-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="66aec-420">Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.</span><span class="sxs-lookup"><span data-stu-id="66aec-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="66aec-421">Vor dem Ausführen, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="66aec-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="66aec-422">Alle Einstellungen, die bereits erwähnt, der [Kapitel 2](#chapter-2---training-your-custom-vision-project) ordnungsgemäß festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="66aec-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="66aec-423">Alle Felder in der **Main Camera**, im Bereich "Inspector" ordnungsgemäß zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="66aec-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="66aec-424">Das Skript **SceneOrganiser** angefügt ist die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="66aec-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="66aec-425">Stellen Sie sicher, Sie fügen Ihre **Vorhersage Schlüssel** in die **PredictionKey** Variable.</span><span class="sxs-lookup"><span data-stu-id="66aec-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="66aec-426">Sie eingefügt haben Ihre **Endpunkt der Vorhersage** in die **PredictionEndpoint** Variable.</span><span class="sxs-lookup"><span data-stu-id="66aec-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="66aec-427">Sie eingefügt haben Ihre **Training Schlüssel** in die **TrainingKey** Variablen, der die *CustomVisionTrainer* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="66aec-428">Sie eingefügt haben Ihre **Projekt-ID** in die **ProjectId** Variablen, der die *CustomVisionTrainer* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="66aec-429">Kapitel 13 – Build herunter, und Laden Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="66aec-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="66aec-430">Um zu beginnen die *erstellen* Prozess:</span><span class="sxs-lookup"><span data-stu-id="66aec-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="66aec-431">Wechseln Sie zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="66aec-432">Teilstriche **Unity C\# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="66aec-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="66aec-433">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-433">Click **Build**.</span></span> <span data-ttu-id="66aec-434">Unity startet eine **Datei-Explorer** Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="66aec-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="66aec-435">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**.</span><span class="sxs-lookup"><span data-stu-id="66aec-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="66aec-436">Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="66aec-437">Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="66aec-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="66aec-438">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="66aec-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="66aec-439">Für HoloLens bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="66aec-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="66aec-440">Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="66aec-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="66aec-441">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="66aec-441">To do this:</span></span>

    1.  <span data-ttu-id="66aec-442">Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="66aec-443">Wechseln Sie zu **Netzwerk und Internet** > **Wi-Fi** > **erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="66aec-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="66aec-444">Beachten Sie die **IPv4** Adresse.</span><span class="sxs-lookup"><span data-stu-id="66aec-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="66aec-445">Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit** > **für Entwickler**</span><span class="sxs-lookup"><span data-stu-id="66aec-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="66aec-446">Legen Sie **Entwicklermodus auf**.</span><span class="sxs-lookup"><span data-stu-id="66aec-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="66aec-447">Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="66aec-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="66aec-448">In der *Projektmappenkonfiguration* wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="66aec-449">In der *Projektmappenplattform*Option **X86, Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="66aec-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="66aec-450">Werden Sie aufgefordert, fügen Sie der **IP-Adresse** von einem Remotegerät (die HoloLens, in diesem Fall, den Sie notiert haben).</span><span class="sxs-lookup"><span data-stu-id="66aec-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="66aec-451">Wechseln Sie zu **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="66aec-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="66aec-452">Ihre app sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="66aec-453">Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**.</span><span class="sxs-lookup"><span data-stu-id="66aec-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="66aec-454">Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **erstellen** Menüelement auswählen *Projektmappe bereitstellen*.</span><span class="sxs-lookup"><span data-stu-id="66aec-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="66aec-455">Die Anwendung zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="66aec-455">To use the application:</span></span>

<span data-ttu-id="66aec-456">So wechseln Sie die app-Funktionalität zwischen *Training* Modus und *Vorhersage* Modus Sie zum aktualisieren müssen der **AppMode** Variablen, befindet sich in der **Awake()** Methode befindet sich innerhalb der *digitale Bilder* Klasse.</span><span class="sxs-lookup"><span data-stu-id="66aec-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="66aec-457">oder</span><span class="sxs-lookup"><span data-stu-id="66aec-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="66aec-458">In *Training* Modus:</span><span class="sxs-lookup"><span data-stu-id="66aec-458">In *Training* mode:</span></span>

- <span data-ttu-id="66aec-459">Sehen Sie sich **Maus** oder **Tastatur** und verwenden Sie die **tippen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="66aec-460">Als Nächstes wird Text angezeigt werden Sie aufgefordert werden, geben Sie ein Tag.</span><span class="sxs-lookup"><span data-stu-id="66aec-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="66aec-461">Angenommen, eine **Maus** oder **Tastatur**.</span><span class="sxs-lookup"><span data-stu-id="66aec-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="66aec-462">In *Vorhersage* Modus:</span><span class="sxs-lookup"><span data-stu-id="66aec-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="66aec-463">Ein Objekt, und verwenden Sie die **tippen**.</span><span class="sxs-lookup"><span data-stu-id="66aec-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="66aec-464">Text wird angezeigt, die das Objekt erkannt, mit der höchsten Wahrscheinlichkeit (Dies wird normalisiert) bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="66aec-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="66aec-465">Kapitel 14 – bewerten und verbessern Ihre Custom Vision-Modell</span><span class="sxs-lookup"><span data-stu-id="66aec-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="66aec-466">Um den Dienst mehr Genauigkeit zu gewährleisten, müssen Sie zum Trainieren des Modells für die Vorhersage verwendet weiterhin.</span><span class="sxs-lookup"><span data-stu-id="66aec-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="66aec-467">Dies erfolgt durch die Verwendung Ihrer neuen Anwendung und mit der *Training* und *Vorhersage* Modi, mit der zweiten müssen im Portal finden Sie auf die ist, was in diesem Kapitel behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="66aec-468">Bereiten Sie Ihr Portal oft noch einmal, um Ihr Modell kontinuierlich zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="66aec-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="66aec-469">Navigieren Sie zu Ihrem Azure Custom Vision-Portal erneut, und wählen Sie nach der Sie in Ihrem Projekt sind, die *Vorhersagen* Registerkarte (von oben in der Mitte der Seite):</span><span class="sxs-lookup"><span data-stu-id="66aec-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="66aec-470">Sie sehen alle Images, die an den Dienst gesendet wurden, während die Anwendung ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="66aec-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="66aec-471">Wenn Sie über die Bilder zeigen, werden sie Sie mit den Vorhersagen bereitstellen, die für das Bild vorgenommen wurden:</span><span class="sxs-lookup"><span data-stu-id="66aec-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="66aec-472">Wählen Sie eine Ihrer Images, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="66aec-472">Select one of your images to open it.</span></span> <span data-ttu-id="66aec-473">Sobald geöffnet ist, wird der Vorhersagefehler für das Bild auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="66aec-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="66aec-474">Wenn Sie die Vorhersagen korrekt waren, und Sie möchten dieses Image Ihres Diensts trainingsmodell hinzufügen, klicken Sie auf die *Meine Tags* Eingabefeld ein, und wählen Sie das Tag, das Sie zuordnen möchten.</span><span class="sxs-lookup"><span data-stu-id="66aec-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="66aec-475">Wenn Sie fertig sind, klicken Sie auf die *speichern und schließen Sie* Schaltfläche unten rechts, und fahren Sie mit der nächsten Abbildung fort.</span><span class="sxs-lookup"><span data-stu-id="66aec-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="66aec-476">Sobald Sie sich an das Raster der Images sind, werden Sie feststellen, dass die Bilder, die Sie Tags hinzugefügt (und gespeichert haben), entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="66aec-477">Wenn keine Bilder Sie Sie denken müssen sich nicht auf Ihr markierte Element enthaltenen finden, können Sie sie löschen, klicken Sie auf der Teilstriche auf diesem Image (hierzu können für verschiedene Images zu finden), und klicken Sie dann auf *löschen* in der oberen rechten Ecke der Rasterseite.</span><span class="sxs-lookup"><span data-stu-id="66aec-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="66aec-478">Klicken Sie auf das Popupfenster, das folgt, Sie können auf eine *Ja, löschen Sie* oder *keine*, um den Löschvorgang zu bestätigen, oder brechen Sie den Befehl ein, bzw.</span><span class="sxs-lookup"><span data-stu-id="66aec-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="66aec-479">Wenn Sie fortfahren möchten, klicken Sie auf die grüne *Train* Schaltfläche oben rechts.</span><span class="sxs-lookup"><span data-stu-id="66aec-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="66aec-480">Mit all den Abbildern, die Sie nun bereitgestellt haben (wodurch sie genauere wird), wird Ihr Dienstmodell trainiert werden.</span><span class="sxs-lookup"><span data-stu-id="66aec-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="66aec-481">Nachdem das Training abgeschlossen ist, stellen Sie sicher, auf die *Standard* , Schaltfläche, damit Ihre *Vorhersage URL* weiterhin die aktuelle Iteration des Diensts verwendet.</span><span class="sxs-lookup"><span data-stu-id="66aec-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="66aec-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="66aec-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="66aec-483">Der fertigen Anwendung für benutzerdefiniertes maschinelles sehen-API</span><span class="sxs-lookup"><span data-stu-id="66aec-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="66aec-484">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die nutzt Azure benutzerdefiniertes maschinelles sehen-API zum Erkennen von realen Objekten, das Dienst-Modell zu trainieren und Anzeigen von Gewissheit wie wir gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="66aec-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="66aec-485">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="66aec-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="66aec-486">Übung 1</span><span class="sxs-lookup"><span data-stu-id="66aec-486">Exercise 1</span></span>

<span data-ttu-id="66aec-487">Trainieren Ihrer **Custom Vision Service** , weitere Objekte zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="66aec-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="66aec-488">Übung 2</span><span class="sxs-lookup"><span data-stu-id="66aec-488">Exercise 2</span></span>

<span data-ttu-id="66aec-489">Als Möglichkeit erweitern, was Sie gelernt haben führen Sie die folgenden Übungen:</span><span class="sxs-lookup"><span data-stu-id="66aec-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="66aec-490">Wiedergeben Sie Sound, wenn ein Objekt erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="66aec-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="66aec-491">Übung 3</span><span class="sxs-lookup"><span data-stu-id="66aec-491">Exercise 3</span></span>

<span data-ttu-id="66aec-492">Verwenden Sie die API des Diensts mit der gleichen Images erneut zu trainieren Ihrer app analysiert, also um den Dienst mehr Genauigkeit zu gewährleisten (sowohl Vorhersagen und Trainieren gleichzeitig ausgeführt werden).</span><span class="sxs-lookup"><span data-stu-id="66aec-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
