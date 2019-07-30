---
title: Mr und Azure 302b-benutzerdefinierte Vision
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie ein Machine Learning-Modell trainieren, und verwenden Sie dann das trainierte Modell, um ähnliche Objekte in einer gemischten Realität zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Custom Vision, hololens, immersive, VR
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63553544"
---
>[!NOTE]
><span data-ttu-id="c3713-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="c3713-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c3713-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="c3713-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c3713-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c3713-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="c3713-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c3713-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="c3713-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c3713-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="c3713-110">Mr und Azure 302b: Benutzerdefinierte Vision</span><span class="sxs-lookup"><span data-stu-id="c3713-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="c3713-111">In diesem Kurs erfahren Sie, wie Sie benutzerdefinierte visuelle Inhalte in einem bereitgestellten Image erkennen können, indem Sie die Funktionen von Azure Custom Vision in einer Mixed Reality-Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="c3713-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="c3713-112">Mit diesem Dienst können Sie ein Machine Learning-Modell mithilfe von Objekt Images trainieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="c3713-113">Sie verwenden dann das trainierte Modell, um ähnliche Objekte zu erkennen, die von der Kamera Erfassung von Microsoft hololens oder einer Kamera bereitgestellt werden, die mit Ihrem PC für immersive (VR) Headsets verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="c3713-115">Bei Azure Custom Vision handelt es sich um einen Microsoft Cognitive Service, der Entwicklern das Erstellen benutzerdefinierter Image Klassifizierer ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c3713-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="c3713-116">Diese Klassifizierungen können dann mit neuen Bildern verwendet werden, um Objekte innerhalb dieses neuen Bilds zu erkennen oder zu klassifizieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="c3713-117">Der Dienst bietet ein einfaches, leicht zu verwendende Onlineportal, um den Prozess zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="c3713-118">Weitere Informationen finden Sie auf der [Seite Azure Custom Vision Service](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="c3713-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="c3713-119">Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die in zwei Modi arbeiten kann:</span><span class="sxs-lookup"><span data-stu-id="c3713-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="c3713-120">**Analysemodus**: Manuelles Einrichten der Custom Vision Service durch Hochladen von Bildern, Erstellen von Tags und trainieren des Dienstanbieter, um unterschiedliche Objekte (in diesem Fall Maus und Tastatur) zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c3713-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="c3713-121">Anschließend erstellen Sie eine hololens-APP, mit der Bilder mithilfe der Kamera erfasst werden, und versuchen, diese Objekte in der realen Welt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c3713-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="c3713-122">**Schulungs Modus**: Sie implementieren Code, der einen "Schulungs Modus" in ihrer App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c3713-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="c3713-123">Der Trainingsmodus ermöglicht Ihnen das Erfassen von Bildern mithilfe der Kamera von hololens, das Hochladen der aufgezeichneten Images in den Dienst und das Trainieren des benutzerdefinierten Vision-Modells.</span><span class="sxs-lookup"><span data-stu-id="c3713-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="c3713-124">In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus dem Custom Vision Service in einer Unity-basierten Beispielanwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="c3713-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="c3713-125">Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.</span><span class="sxs-lookup"><span data-stu-id="c3713-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="c3713-126">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="c3713-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c3713-127">Natürlich</span><span class="sxs-lookup"><span data-stu-id="c3713-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c3713-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c3713-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c3713-129"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="c3713-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c3713-130">Mr und Azure 302b: Benutzerdefinierte Vision</span><span class="sxs-lookup"><span data-stu-id="c3713-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3713-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c3713-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3713-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c3713-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c3713-133">Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets.</span><span class="sxs-lookup"><span data-stu-id="c3713-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c3713-134">Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c3713-135">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="c3713-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3713-136">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c3713-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c3713-137">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="c3713-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c3713-138">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018).</span><span class="sxs-lookup"><span data-stu-id="c3713-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="c3713-139">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="c3713-140">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="c3713-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c3713-141">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="c3713-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c3713-142">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="c3713-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c3713-143">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c3713-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c3713-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="c3713-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c3713-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c3713-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c3713-146">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="c3713-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c3713-147">Eine Kamera, die mit Ihrem PC verbunden ist (für die immersive Headset-Entwicklung)</span><span class="sxs-lookup"><span data-stu-id="c3713-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="c3713-148">Internet Zugriff für den Azure-Setup-und Custom Vision-API-Abruf</span><span class="sxs-lookup"><span data-stu-id="c3713-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="c3713-149">Für jedes Objekt, das von der Custom Vision Service erkannt werden soll, wird eine Reihe von mindestens fünf (10) Bildern empfohlen.</span><span class="sxs-lookup"><span data-stu-id="c3713-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="c3713-150">Wenn Sie möchten, können Sie [die Images verwenden, die bereits mit diesem Kurs bereitgestellt werden (Computermaus und Tastatur) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="c3713-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c3713-151">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="c3713-151">Before you start</span></span>

1.  <span data-ttu-id="c3713-152">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="c3713-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c3713-153">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="c3713-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="c3713-154">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="c3713-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c3713-155">Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="c3713-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c3713-156">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="c3713-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="c3713-157">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="c3713-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="c3713-158">Kapitel 1: das Custom Vision Service-Portal</span><span class="sxs-lookup"><span data-stu-id="c3713-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="c3713-159">Um die *Custom Vision Service* in Azure verwenden zu können, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="c3713-160">[Navigieren Sie zunächst zur *Custom Vision Service* Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="c3713-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="c3713-161">Klicken Sie auf die Schaltfläche **Get Started** .</span><span class="sxs-lookup"><span data-stu-id="c3713-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="c3713-162">Melden Sie sich beim *Custom Vision Service* -Portal an.</span><span class="sxs-lookup"><span data-stu-id="c3713-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="c3713-163">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="c3713-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c3713-164">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c3713-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="c3713-165">Wenn Sie sich zum ersten Mal angemeldet haben, werden Sie im Bereich mit den *Nutzungsbedingungen* aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="c3713-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="c3713-166">Aktivieren Sie das Kontrollkästchen, um den Bedingungen zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="c3713-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="c3713-167">Klicken Sie dann auf **Ich stimme**zu.</span><span class="sxs-lookup"><span data-stu-id="c3713-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="c3713-168">Nachdem Sie die Bedingungen zugestimmt haben, werden Sie zum Abschnitt " *Projekte* " im Portal navigiert.</span><span class="sxs-lookup"><span data-stu-id="c3713-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="c3713-169">Klicken Sie auf **Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="c3713-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="c3713-170">Eine Registerkarte wird auf der rechten Seite angezeigt, auf der Sie aufgefordert werden, einige Felder für das Projekt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="c3713-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="c3713-171">Fügen Sie einen *Namen* für das Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="c3713-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="c3713-172">Fügen Sie eine *Beschreibung* für das Projekt ein (*optional*).</span><span class="sxs-lookup"><span data-stu-id="c3713-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="c3713-173">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue *Ressourcengruppe* .</span><span class="sxs-lookup"><span data-stu-id="c3713-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="c3713-174">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="c3713-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3713-175">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c3713-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="c3713-176">Festlegen der *Projekttypen* auf **Klassifizierung**</span><span class="sxs-lookup"><span data-stu-id="c3713-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="c3713-177">Legen Sie die *Domänen* als **Allgemein**fest.</span><span class="sxs-lookup"><span data-stu-id="c3713-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="c3713-178">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c3713-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="c3713-179">Wenn Sie fertig sind, klicken Sie auf **Projekt erstellen**. Sie werden auf die Seite Custom Vision Service, Projekt, umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="c3713-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="c3713-180">Kapitel 2: trainieren Ihres Custom Vision Projekts</span><span class="sxs-lookup"><span data-stu-id="c3713-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="c3713-181">Wenn Sie sich im Custom Vision Portal befinden, besteht das Hauptziel darin, das Projekt zu trainieren, um bestimmte Objekte in Bildern zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c3713-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="c3713-182">Sie benötigen mindestens fünf (5) Images, obwohl zehn (10) für jedes Objekt bevorzugt werden, das Ihre Anwendung erkennen soll.</span><span class="sxs-lookup"><span data-stu-id="c3713-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="c3713-183">[Sie können die Bilder verwenden, die mit diesem Kurs bereitgestellt werden (Computermaus und Tastatur)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="c3713-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="c3713-184">So trainieren Sie das Custom Vision Service Projekt:</span><span class="sxs-lookup"><span data-stu-id="c3713-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="c3713-185">Klicken Sie auf **+** die Schaltfläche neben **Tags.**</span><span class="sxs-lookup"><span data-stu-id="c3713-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="c3713-186">Fügen Sie den **Namen** des Objekts hinzu, das Sie erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="c3713-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="c3713-187">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="c3713-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="c3713-188">Sie werden feststellen, dass Ihr **Tag** hinzugefügt wurde (möglicherweise müssen Sie die Seite erneut laden, damit es angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="c3713-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="c3713-189">Aktivieren Sie das Kontrollkästchen neben dem neuen Tag, wenn es nicht bereits aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="c3713-190">Klicken Sie in der Mitte der Seite auf **Bilder hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="c3713-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="c3713-191">Klicken Sie auf **lokale Dateien durchsuchen**, suchen Sie, und wählen Sie dann die Images aus, die Sie hochladen möchten, mit dem Minimalwert fünf (5).</span><span class="sxs-lookup"><span data-stu-id="c3713-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="c3713-192">Denken Sie daran, dass alle diese Images das Objekt enthalten sollten, das Sie trainieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c3713-193">Sie können mehrere Bilder gleichzeitig zum Hochladen auswählen.</span><span class="sxs-lookup"><span data-stu-id="c3713-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="c3713-194">Wenn Sie die Bilder auf der Registerkarte sehen können, wählen Sie im Feld **Meine Tags** das entsprechende Tag aus.</span><span class="sxs-lookup"><span data-stu-id="c3713-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="c3713-195">Klicken Sie auf **Dateien hochladen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-195">Click on **Upload files**.</span></span> <span data-ttu-id="c3713-196">Die Dateien werden hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="c3713-196">The files will begin uploading.</span></span> <span data-ttu-id="c3713-197">Nachdem Sie den Upload bestätigt haben, klicken Sie auf **done**.</span><span class="sxs-lookup"><span data-stu-id="c3713-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="c3713-198">Wiederholen Sie den Vorgang, um ein neues **Tag** mit dem Namen **Tastatur** zu erstellen, und laden Sie die entsprechenden Fotos dafür hoch.</span><span class="sxs-lookup"><span data-stu-id="c3713-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="c3713-199">Wenn Sie die neuen Tags erstellt haben, **Deaktivieren** Sie die *Maus* , um das Fenster *Bilder hinzufügen* anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c3713-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="c3713-200">Nachdem Sie beide Tags eingerichtet haben, klicken Sie auf **trainieren**, und die erste Trainings Iterationen wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="c3713-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="c3713-201">Nachdem Sie erstellt wurde, können Sie zwei Schaltflächen mit dem Namen " **default** " und die **Vorhersage-URL**anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c3713-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="c3713-202">Klicken Sie zuerst auf **Standardwert erstellen** , und klicken Sie dann auf **Vorhersage-URL**.</span><span class="sxs-lookup"><span data-stu-id="c3713-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="c3713-203">Die Endpunkt-URL, die von diesem bereitgestellt wird, wird auf den Wert festgelegt, welcher *iterations* Wert als Standard markiert wurde.</span><span class="sxs-lookup"><span data-stu-id="c3713-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="c3713-204">Wenn Sie später eine neue *iterations* Zeit erstellen und diese als Standard aktualisieren, müssen Sie den Code nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="c3713-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="c3713-205">Nachdem Sie auf die *Vorhersage-URL*geklickt haben, öffnen Sie *Notepad*, kopieren Sie die **URL** und den **Vorhersage Schlüssel**, und fügen Sie Sie ein, damit Sie Sie später im Code abrufen können.</span><span class="sxs-lookup"><span data-stu-id="c3713-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="c3713-206">Klicken Sie rechts oben auf dem Bildschirm auf das **Zahnrad** Symbol.</span><span class="sxs-lookup"><span data-stu-id="c3713-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="c3713-207">Kopieren Sie den **Trainings Schlüssel** *, und*fügen Sie ihn zur späteren Verwendung in einen Editor ein.</span><span class="sxs-lookup"><span data-stu-id="c3713-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="c3713-208">Kopieren Sie auch die **Projekt-ID**, und fügen Sie Sie zur späteren Verwendung in die *Notepad* -Datei ein.</span><span class="sxs-lookup"><span data-stu-id="c3713-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="c3713-209">Kapitel 3: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="c3713-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="c3713-210">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="c3713-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c3713-211">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="c3713-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="c3713-212">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="c3713-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="c3713-213">Fügen Sie **azurecustomvision ein.**</span><span class="sxs-lookup"><span data-stu-id="c3713-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="c3713-214">Stellen Sie sicher, dass die Projektvorlage auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="c3713-215">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="c3713-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c3713-216">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="c3713-217">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c3713-218">Wechseln Sie zu \**Einstellungen* *Bearbeiten* > \* , und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="c3713-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c3713-219">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c3713-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c3713-220">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="c3713-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="c3713-221">Navigieren Sie als nächstes zu **Datei >** Buildeinstellungen, wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen</span><span class="sxs-lookup"><span data-stu-id="c3713-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="c3713-222">In **Datei >** Buildeinstellungen, und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="c3713-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="c3713-223">**Zielgerät** ist auf **hololens** festgelegt</span><span class="sxs-lookup"><span data-stu-id="c3713-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="c3713-224">Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.</span><span class="sxs-lookup"><span data-stu-id="c3713-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="c3713-225">Der Buildtyp ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3713-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="c3713-226">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3713-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="c3713-227">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3713-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="c3713-228">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3713-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="c3713-229">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="c3713-230">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="c3713-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c3713-231">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c3713-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="c3713-232">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="c3713-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="c3713-233">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname:* Text den Text **customvisionscene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="c3713-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="c3713-234">Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="c3713-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="c3713-235">Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="c3713-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="c3713-236">Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="c3713-237">Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="c3713-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="c3713-238">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="c3713-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c3713-239">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="c3713-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c3713-240">Die CLR- **Lauf Zeit Version** sollte **experimentell sein (.NET 4,6-Entsprechung)** , wodurch der Editor neu gestartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="c3713-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="c3713-241">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="c3713-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="c3713-242">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="c3713-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="c3713-243">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c3713-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="c3713-244">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="c3713-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="c3713-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="c3713-245">**Webcam**</span></span>

        3. <span data-ttu-id="c3713-246">**Tritt**</span><span class="sxs-lookup"><span data-stu-id="c3713-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="c3713-247">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="c3713-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="c3713-248">Zurück in Buildeinstellungen: *Unity-C\# -Projekte* sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="c3713-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="c3713-249">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="c3713-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="c3713-250">Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).</span><span class="sxs-lookup"><span data-stu-id="c3713-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="c3713-251">Kapitel 4: Importieren der newtonsoft-dll in Unity</span><span class="sxs-lookup"><span data-stu-id="c3713-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3713-252">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 6 fortfahren. ](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="c3713-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="c3713-253">Für diesen Kurs muss die **newtonsoft** -Bibliothek verwendet werden, die Sie Ihren Assets als dll hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="c3713-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="c3713-254">Das Paket, das [Diese Bibliothek enthält, kann von diesem Link heruntergeladen werden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="c3713-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="c3713-255">Verwenden Sie das Unity-Paket, das in diesem Kurs verwendet wurde, um die newtonsoft-Bibliothek in Ihr Projekt zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="c3713-256">Fügen Sie das *. unitypackage* zu Unity hinzu, indem Sie die Menüoption **Assets* > *Import* *Package* > *Custom* *Package** verwenden.</span><span class="sxs-lookup"><span data-stu-id="c3713-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="c3713-257">Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und **einschließlich) Plug** -ins ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="c3713-258">Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c3713-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="c3713-259">Wechseln Sie in der Projektansicht in den Ordner **Newton Soft** unter Plug-in, und wählen Sie das *Newton Soft. JSON-Plug*-in aus.</span><span class="sxs-lookup"><span data-stu-id="c3713-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="c3713-260">Vergewissern **Sie sich**, dass die Option " *newtonsoft. JSON* " ausgewählt **ist,** und stellen Sie sicher, dass **alle Plattformen** deaktiviert sind. Stellen Sie dann sicher, dass **wsaplayer** **ebenfalls deaktiviert**ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="c3713-261">Dies dient nur zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="c3713-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="c3713-262">Wenn Sie diese Plug-ins markieren, werden Sie nur im Unity-Editor verwendet.</span><span class="sxs-lookup"><span data-stu-id="c3713-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="c3713-263">Im WSA-Ordner gibt es eine andere Gruppe, die verwendet wird, nachdem das Projekt aus Unity exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="c3713-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="c3713-264">Als nächstes müssen Sie den Ordner " **WSA** " im Ordner " **newtonsoft** " öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="c3713-265">Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="c3713-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="c3713-266">Wählen Sie die Datei aus, und vergewissern Sie sich dann im Inspektor, dass</span><span class="sxs-lookup"><span data-stu-id="c3713-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="c3713-267">**Jede Plattform** ist **deaktiviert** .</span><span class="sxs-lookup"><span data-stu-id="c3713-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="c3713-268">**nur** **Wsaplayer** ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="c3713-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="c3713-269">"Nicht **verarbeiten** " ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="c3713-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="c3713-270">Kapitel 5: Kamera Einrichtung</span><span class="sxs-lookup"><span data-stu-id="c3713-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="c3713-271">Wählen Sie im Bereich Hierarchie die *Hauptkamera*aus.</span><span class="sxs-lookup"><span data-stu-id="c3713-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="c3713-272">Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der *Hauptkamera* im *Inspektor-Panel*sehen.</span><span class="sxs-lookup"><span data-stu-id="c3713-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="c3713-273">Das *Kamera* Objekt muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="c3713-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="c3713-274">Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="c3713-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="c3713-275">Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="c3713-276">Legen Sie **klar Flags** auf voll Tonfarbe fest (diese Einstellung wird für immersives Headset ignoriert).</span><span class="sxs-lookup"><span data-stu-id="c3713-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="c3713-277">Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest (Dies wird für das immersive Headset ignoriert).</span><span class="sxs-lookup"><span data-stu-id="c3713-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="c3713-278">Kapitel 6: Erstellen der customvisionanalyser-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c3713-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="c3713-279">An diesem Punkt können Sie Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="c3713-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="c3713-280">Sie beginnen mit der *customvisionanalyser* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="c3713-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="c3713-281">Die Aufrufe der **Custom Vision Service** , die im unten gezeigten Code vorgenommen wurden, werden mithilfe der **Custom Vision Rest-API**vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="c3713-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="c3713-282">Durch die Verwendung dieser API sehen Sie, wie Sie diese API implementieren und nutzen können (nützlich, um zu verstehen, wie Sie etwas ähnliches implementieren können).</span><span class="sxs-lookup"><span data-stu-id="c3713-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="c3713-283">Beachten Sie, dass Microsoft ein **Custom Vision Service SDK** bietet, das auch zum Aufrufen des Dienstanbieter verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c3713-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="c3713-284">Weitere Informationen finden Sie im [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) -Artikel.</span><span class="sxs-lookup"><span data-stu-id="c3713-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="c3713-285">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="c3713-285">This class is responsible for:</span></span>

-   <span data-ttu-id="c3713-286">Das letzte als Bytearray erfasste Bild wird geladen.</span><span class="sxs-lookup"><span data-stu-id="c3713-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="c3713-287">Das Bytearray wird zur Analyse an Ihre Azure *Custom Vision Service* -Instanz gesendet.</span><span class="sxs-lookup"><span data-stu-id="c3713-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="c3713-288">Die Antwort wird als JSON-Zeichenfolge empfangen.</span><span class="sxs-lookup"><span data-stu-id="c3713-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="c3713-289">Deserialisieren der Antwort und übergeben der resultierenden *Vorhersage* an die *sceneorganisator* -Klasse, um die Anzeige der Antwort zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="c3713-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="c3713-290">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-290">To create this class:</span></span>

1.  <span data-ttu-id="c3713-291">Klicken Sie im *Projekt Panel*mit der rechten Maustaste in den *Ordner Asset* , und klicken Sie dann auf **> Ordner erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="c3713-292">Nennen Sie die Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="c3713-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="c3713-293">Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="c3713-294">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **\# Skript** **Erstellen** > .</span><span class="sxs-lookup"><span data-stu-id="c3713-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3713-295">Benennen Sie das Skript *customvisionanalyser*.</span><span class="sxs-lookup"><span data-stu-id="c3713-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="c3713-296">Doppelklicken Sie auf das neue *customvisionanalyser* -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="c3713-297">Aktualisieren Sie die Namespaces am Anfang der Datei so, dass Sie den folgenden entsprechen:</span><span class="sxs-lookup"><span data-stu-id="c3713-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="c3713-298">Fügen Sie in der *customvisionanalyser* -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

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
    > <span data-ttu-id="c3713-299">Stellen Sie sicher, dass Sie den **Vorhersage Schlüssel** in die " **prätionkey** "-Variable und den **Vorhersage Endpunkt** in die " **prätionendpoint** "-Variable</span><span class="sxs-lookup"><span data-stu-id="c3713-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="c3713-300">Sie haben diese zuvor im Kurs in *Notepad* kopiert.</span><span class="sxs-lookup"><span data-stu-id="c3713-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="c3713-301">Code für **Awa()** muss nun hinzugefügt werden, um die Instanzvariable zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="c3713-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="c3713-302">Löschen Sie die Methoden " **Start ()** " und " **Update ()** ".</span><span class="sxs-lookup"><span data-stu-id="c3713-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="c3713-303">Fügen Sie als nächstes die Coroutine hinzu (mit der statischen **getimageasbytearray ()** -Methode darunter), die die Ergebnisse der Analyse des Bilds erhält, das von der *imagecapture* -Klasse erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3713-304">In der **analyseimagecapture** -Coroutine gibt es einen Aufrufen der *sceneorganisator* -Klasse, die Sie noch erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="c3713-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="c3713-305">Deshalb sollten Sie **diese Zeilen jetzt kommentiert lassen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-305">Therefore, **leave those lines commented for now**.</span></span>

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

10.  <span data-ttu-id="c3713-306">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c3713-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="c3713-307">Kapitel 7: Erstellen der customvisionobjects-Klasse</span><span class="sxs-lookup"><span data-stu-id="c3713-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="c3713-308">Die Klasse, die Sie jetzt erstellen, ist die *customvisionobjects* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="c3713-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="c3713-309">Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe an die *Custom Vision Service*verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="c3713-310">Beachten Sie, dass Sie den Endpunkt beachten, den die Custom Vision Service bereitstellt, da die folgende JSON-Struktur für die Arbeit mit [*Custom Vision Vorhersage v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="c3713-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="c3713-311">Wenn Sie über eine andere Version verfügen, müssen Sie möglicherweise die folgende Struktur aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="c3713-312">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-312">To create this class:</span></span>

1.  <span data-ttu-id="c3713-313">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3713-314">Nennen Sie das Skript *customvisionobjects*.</span><span class="sxs-lookup"><span data-stu-id="c3713-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="c3713-315">Doppelklicken Sie auf das neue **customvisionobjects** -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3713-316">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="c3713-317">Löschen Sie die Methoden " **Start ()** " und " **Update ()** " in der Klasse " *customvisionobjects* ". Diese Klasse sollte nun leer sein.</span><span class="sxs-lookup"><span data-stu-id="c3713-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="c3713-318">Fügen Sie die folgenden Klassen **außerhalb** der *customvisionobjects* -Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="c3713-319">Diese Objekte werden von der *newtonsoft* -Bibliothek verwendet, um die Antwortdaten zu serialisieren und zu deserialisieren:</span><span class="sxs-lookup"><span data-stu-id="c3713-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="c3713-320">Kapitel 8: Erstellen der voicerecognizer-Klasse</span><span class="sxs-lookup"><span data-stu-id="c3713-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="c3713-321">Diese Klasse erkennt die Spracheingabe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="c3713-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="c3713-322">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-322">To create this class:</span></span>

1.  <span data-ttu-id="c3713-323">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3713-324">Nennen Sie das Skript *voicerecognizer*.</span><span class="sxs-lookup"><span data-stu-id="c3713-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="c3713-325">Doppelklicken Sie auf das neue **voicerecognizer** -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3713-326">Fügen Sie die folgenden Namespaces oberhalb der *voicerecognizer* -Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="c3713-327">Fügen Sie dann die folgenden Variablen in der *voicerecognizer* -Klasse oberhalb der *Start ()* -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

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

5.  <span data-ttu-id="c3713-328">Fügen Sie die Methoden " **Awa()** " und " **Start ()** " hinzu, bei denen die Benutzer Schlüsselwörter so eingerichtet werden, dass Sie beim Zuordnen eines Tags zu einem Bild erkannt werden:</span><span class="sxs-lookup"><span data-stu-id="c3713-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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

6.  <span data-ttu-id="c3713-329">Löschen Sie die **Update ()** -Methode.</span><span class="sxs-lookup"><span data-stu-id="c3713-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="c3713-330">Fügen Sie den folgenden Handler hinzu, der immer dann aufgerufen wird, wenn die Spracheingabe erkannt wird:</span><span class="sxs-lookup"><span data-stu-id="c3713-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

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

8.  <span data-ttu-id="c3713-331">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c3713-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="c3713-332">Machen Sie sich keine Sorgen um Code, der möglicherweise einen Fehler enthält, da Sie bald weitere Klassen bereitstellen werden, die diese beheben.</span><span class="sxs-lookup"><span data-stu-id="c3713-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="c3713-333">Kapitel 9: Erstellen der customvisiontrainer-Klasse</span><span class="sxs-lookup"><span data-stu-id="c3713-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="c3713-334">Diese Klasse verkettet eine Reihe von webaufrufen, um die *Custom Vision Service*zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="c3713-335">Jeder-Befehl wird direkt oberhalb des Codes ausführlich erläutert.</span><span class="sxs-lookup"><span data-stu-id="c3713-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="c3713-336">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-336">To create this class:</span></span>

1.  <span data-ttu-id="c3713-337">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3713-338">Nennen Sie das Skript *customvisiontrainer*.</span><span class="sxs-lookup"><span data-stu-id="c3713-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="c3713-339">Doppelklicken Sie auf das neue *customvisiontrainer* -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3713-340">Fügen Sie die folgenden Namespaces oberhalb der *customvisiontrainer* -Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="c3713-341">Fügen Sie dann die folgenden Variablen in der *customvisiontrainer* -Klasse oberhalb der **Start ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="c3713-342">Die hier verwendete Schulungs-URL wird in der Dokumentation zum *Custom Vision Training 1,2* bereitgestellt und hat eine Struktur von: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="c3713-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="c3713-343">Weitere Informationen finden Sie in der [*Referenz-API zu Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="c3713-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="c3713-344">Beachten Sie, dass Sie den Endpunkt beachten, den der Custom Vision Service für den Trainingsmodus bereitstellt, da die JSON-Struktur (innerhalb der **customvisionobjects** -Klasse) für die Arbeit mit [*Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="c3713-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="c3713-345">Wenn Sie über eine andere Version verfügen, müssen Sie möglicherweise die Struktur der *Objekte* aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

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
    > <span data-ttu-id="c3713-346">Stellen Sie sicher, dass Sie den Wert für den **Dienst Schlüssel** (Trainings Schlüssel) und den **Projekt-ID** -Wert hinzufügen, den Sie zuvor notiert haben. Dies sind die Werte, die Sie [zuvor im Portal im Kurs erfasst haben (Kapitel 2, Schritt 10)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="c3713-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="c3713-347">Fügen Sie die folgenden Methoden " **Start ()** " und " **Awa()** " hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="c3713-348">Diese Methoden werden bei der Initialisierung aufgerufen und enthalten den Aufruf, um die Benutzeroberfläche einzurichten:</span><span class="sxs-lookup"><span data-stu-id="c3713-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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

6.  <span data-ttu-id="c3713-349">Löschen Sie die **Update ()** -Methode.</span><span class="sxs-lookup"><span data-stu-id="c3713-349">Delete the **Update()** method.</span></span> <span data-ttu-id="c3713-350">Diese Klasse wird nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="c3713-350">This class will not need it.</span></span>

7.  <span data-ttu-id="c3713-351">Fügen Sie die **requesttagselection ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="c3713-352">Diese Methode ist die erste, die aufgerufen wird, wenn ein Abbild aufgezeichnet und auf dem Gerät gespeichert wird. es kann nun an die *Custom Vision Service*übermittelt werden, um es zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="c3713-353">Diese Methode zeigt in der Trainings Benutzeroberfläche eine Reihe von Schlüsselwörtern an, mit denen der Benutzer das erfasste Bild markieren kann.</span><span class="sxs-lookup"><span data-stu-id="c3713-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="c3713-354">Außerdem wird die *voicerecognizer* -Klasse darauf aufmerksam, dass Sie mit dem lauschen an den Benutzer für die Spracheingabe beginnt.</span><span class="sxs-lookup"><span data-stu-id="c3713-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="c3713-355">Fügen Sie die **verifytag ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="c3713-356">Diese Methode empfängt die von der **voicerecognizer** -Klasse erkannte Spracheingabe und überprüft deren Gültigkeit und beginnt dann mit dem Trainings Vorgang.</span><span class="sxs-lookup"><span data-stu-id="c3713-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

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

9.  <span data-ttu-id="c3713-357">Fügen Sie die **subentschärmagefortraining ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="c3713-358">Mit dieser Methode wird der Custom Vision Service trainingprozess gestartet.</span><span class="sxs-lookup"><span data-stu-id="c3713-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="c3713-359">Der erste Schritt besteht darin, die **Tag-ID** aus dem Dienst abzurufen, der der überprüften Spracheingabe des Benutzers zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="c3713-360">Die **Tag-ID** wird dann zusammen mit dem Bild hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="c3713-360">The **Tag Id** will then be uploaded along with the image.</span></span>

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

10. <span data-ttu-id="c3713-361">Fügen Sie die Methode **traincustomvisionproject ()** hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="c3713-362">Nachdem das Bild übermittelt und markiert wurde, wird diese Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="c3713-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="c3713-363">Es wird eine neue Iterations Vorlage erstellt, die mit allen vorherigen Bildern, die an den Dienst gesendet werden, sowie dem soeben hochgeladenen Image trainiert wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="c3713-364">Nachdem das Training abgeschlossen ist, ruft diese Methode eine Methode auf, um die neu erstellte **iterations** Eigenschaft als **Standard**festzulegen, sodass der Endpunkt, den Sie für die Analyse verwenden, die letzte trainierte Iterations Methode ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

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

11. <span data-ttu-id="c3713-365">Fügen Sie die **setdefaultiterations ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="c3713-366">Mit dieser Methode wird die zuvor erstellte und trainierte Iterations Methode als *Standard*festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3713-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="c3713-367">Nachdem dieser Vorgang abgeschlossen ist, muss diese Methode die vorherige Iterationen löschen, die im Dienst vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c3713-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="c3713-368">Zum Zeitpunkt der Erstellung dieses Kurses gibt es eine Beschränkung von maximal zehn (10) Iterationen, die gleichzeitig im Dienst vorhanden sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="c3713-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

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

12. <span data-ttu-id="c3713-369">Fügen Sie die **deletepreviousiterations ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3713-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="c3713-370">Diese Methode findet und löscht die vorherige nicht standardmäßige Iterationen:</span><span class="sxs-lookup"><span data-stu-id="c3713-370">This method will find and delete the previous non-default iteration:</span></span>

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

13. <span data-ttu-id="c3713-371">Die letzte Methode, die dieser Klasse hinzugefügt werden soll, ist die **getimageasbytearray ()** -Methode, die für die Webaufrufe verwendet wird, um das in ein Bytearray erfasste Bild zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

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

14. <span data-ttu-id="c3713-372">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c3713-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="c3713-373">Kapitel 10: Erstellen der sceneorganisator-Klasse</span><span class="sxs-lookup"><span data-stu-id="c3713-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="c3713-374">Diese Klasse führt Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="c3713-374">This class will:</span></span>

-   <span data-ttu-id="c3713-375">Erstellen Sie ein **Cursor** Objekt, das an die Hauptkamera angehängt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c3713-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="c3713-376">Erstellen Sie **ein** Bezeichnungs Objekt, das angezeigt wird, wenn der Dienst die Objekte der realen Welt erkennt.</span><span class="sxs-lookup"><span data-stu-id="c3713-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="c3713-377">Richten Sie die Hauptkamera ein, indem Sie die entsprechenden Komponenten an Sie anfügen.</span><span class="sxs-lookup"><span data-stu-id="c3713-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="c3713-378">Wenn Sie sich im **Analysemodus**befinden, können Sie die Bezeichnungen zur Laufzeit im entsprechenden Raum relativ zur Position der Hauptkamera erzeugen und die vom Custom Vision Service empfangenen Daten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c3713-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="c3713-379">Erzeugen Sie im **Trainingsmodus**die Benutzeroberfläche, auf der die verschiedenen Phasen des Trainingsprozesses angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="c3713-380">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-380">To create this class:</span></span>

1.  <span data-ttu-id="c3713-381">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3713-382">Nennen Sie das Skript *sceneorganisator*.</span><span class="sxs-lookup"><span data-stu-id="c3713-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="c3713-383">Doppelklicken Sie auf das neue *sceneorganisator* -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3713-384">Sie benötigen nur einen Namespace, und entfernen Sie die anderen aus der *sceneorganisator* -Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="c3713-385">Fügen Sie dann die folgenden Variablen in der *sceneorganisator* -Klasse oberhalb der **Start ()** -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="c3713-386">Löschen Sie die Methoden " **Start ()** " und " **Update ()** ".</span><span class="sxs-lookup"><span data-stu-id="c3713-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="c3713-387">Fügen Sie direkt unterhalb der Variablen die **Awa()** -Methode hinzu, die die Klasse initialisiert und die Szene einrichtet.</span><span class="sxs-lookup"><span data-stu-id="c3713-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="c3713-388">Fügen Sie nun die Methode " **samatecameracursor ()** " hinzu, die den Hauptkamera Cursor erstellt und positioniert, sowie die Methode "Methode **()** ", die das Objekt " **Analyse Bezeichnung** " erstellt.</span><span class="sxs-lookup"><span data-stu-id="c3713-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

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

8. <span data-ttu-id="c3713-389">Fügen Sie die **setcamerastatus ()** -Methode hinzu, die Nachrichten verarbeitet, die für das textnetz vorgesehen sind, das den Status der Kamera bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c3713-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

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

9. <span data-ttu-id="c3713-390">Fügen Sie die Methoden **placeanalysislabel ()** und **settagstolastlabel ()** hinzu, die die Daten der Custom Vision Service in der Szene erzeugen und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c3713-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

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

10. <span data-ttu-id="c3713-391">Fügen Sie abschließend die Methode " **itatetrainingui ()** " hinzu, die die Benutzeroberfläche erzeugt, die die verschiedenen Phasen des Trainingsprozesses anzeigt, wenn sich die Anwendung im Trainingsmodus befindet.</span><span class="sxs-lookup"><span data-stu-id="c3713-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="c3713-392">Diese Methode wird auch zum Erstellen des Kamera Status Objekts verwendet.</span><span class="sxs-lookup"><span data-stu-id="c3713-392">This method will also be harnessed to create the camera status object.</span></span>

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

11. <span data-ttu-id="c3713-393">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c3713-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3713-394">Bevor Sie fortfahren, öffnen Sie die **customvisionanalyser** -Klasse, und heben Sie die Auskommentierung der folgenden Zeilen innerhalb der **analyselastimageaufgezeichnet ()** -Methode auf:</span><span class="sxs-lookup"><span data-stu-id="c3713-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="c3713-395">Kapitel 11: Erstellen der imagecapture-Klasse</span><span class="sxs-lookup"><span data-stu-id="c3713-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="c3713-396">Die nächste Klasse, die Sie erstellen, ist die *imagecapture* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="c3713-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="c3713-397">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="c3713-397">This class is responsible for:</span></span>

-   <span data-ttu-id="c3713-398">Erfassen eines Bilds mithilfe der hololens-Kamera und speichern im *App* -Ordner.</span><span class="sxs-lookup"><span data-stu-id="c3713-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="c3713-399">Behandlung von TAP-Gesten vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c3713-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="c3713-400">Beibehalten des Enumerationswerts, der bestimmt, ob die Anwendung im *Analyse* Modus oder im *Trainings* Modus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="c3713-401">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="c3713-401">To create this class:</span></span>

1.  <span data-ttu-id="c3713-402">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c3713-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="c3713-403">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Create > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="c3713-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="c3713-404">Benennen Sie das Skript mit *imagecapture*.</span><span class="sxs-lookup"><span data-stu-id="c3713-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="c3713-405">Doppelklicken Sie auf das neue **imagecapture** -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="c3713-406">Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c3713-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="c3713-407">Fügen Sie dann die folgenden Variablen in der *imagecapture* -Klasse oberhalb der **Start ()** -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="c3713-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="c3713-408">Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="c3713-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="c3713-409">Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Geste auftritt.</span><span class="sxs-lookup"><span data-stu-id="c3713-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

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
    > <span data-ttu-id="c3713-410">Im *Analyse* Modus fungiert die **taphandler** -Methode als Switch zum Starten oder Abbrechen der Foto Erfassungs Schleife.</span><span class="sxs-lookup"><span data-stu-id="c3713-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="c3713-411">Im *Trainings* Modus wird ein Bild von der Kamera aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c3713-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="c3713-412">Wenn der Cursor grün ist, bedeutet dies, dass die Kamera verfügbar ist, um das Bild zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="c3713-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="c3713-413">Wenn der Cursor rot ist, bedeutet dies, dass die Kamera ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="c3713-414">Fügen Sie die Methode hinzu, die die Anwendung verwendet, um den Bild Aufzeichnungsprozess zu starten und das Bild zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c3713-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

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

9.  <span data-ttu-id="c3713-415">Fügen Sie die Handler hinzu, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und für die Analyse bereit ist.</span><span class="sxs-lookup"><span data-stu-id="c3713-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="c3713-416">Das Ergebnis wird dann in Abhängigkeit vom Modus, für den der Code festgelegt ist, an *customvisionanalyser* oder *customvisiontrainer* weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="c3713-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

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

10. <span data-ttu-id="c3713-417">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c3713-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="c3713-418">Nachdem alle Skripts abgeschlossen sind, wechseln Sie zurück zum Unity-Editor, und klicken Sie dann auf die Klasse **sceneorganisator** aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="c3713-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="c3713-419">Kapitel 12: vor dem Aufbau</span><span class="sxs-lookup"><span data-stu-id="c3713-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="c3713-420">Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.</span><span class="sxs-lookup"><span data-stu-id="c3713-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="c3713-421">Bevor Sie vorgehen, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="c3713-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="c3713-422">Alle in [Kapitel 2](#chapter-2---training-your-custom-vision-project) erwähnten Einstellungen sind richtig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3713-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="c3713-423">Alle Felder in der **Hauptkamera**, Inspektor Panel, sind ordnungsgemäß zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="c3713-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="c3713-424">Das Skript **sceneorganisator** ist an das **Hauptkamera** Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="c3713-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="c3713-425">Stellen Sie sicher, dass Sie den **Vorhersage Schlüssel** in die Variable " **vorhersag Schlüssel** " einfügen.</span><span class="sxs-lookup"><span data-stu-id="c3713-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="c3713-426">Sie haben den **Vorhersage Endpunkt** in die " **prätionendpoint** "-Variable eingefügt.</span><span class="sxs-lookup"><span data-stu-id="c3713-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="c3713-427">Sie haben ihren **Trainings Schlüssel** in die Variable " **trainingkey** " der Klasse " *customvisiontrainer* " eingefügt.</span><span class="sxs-lookup"><span data-stu-id="c3713-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="c3713-428">Sie haben Ihre **Projekt-ID** in die **ProjectId** -Variable der *customvisiontrainer* -Klasse eingefügt.</span><span class="sxs-lookup"><span data-stu-id="c3713-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="c3713-429">Kapitel 13: Erstellen und querladen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="c3713-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="c3713-430">So beginnen Sie *den* Buildprozess:</span><span class="sxs-lookup"><span data-stu-id="c3713-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="c3713-431">Wechseln Sie zu **Datei >** Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="c3713-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="c3713-432">Teil Strich **Unity\# -C-Projekte**.</span><span class="sxs-lookup"><span data-stu-id="c3713-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="c3713-433">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-433">Click **Build**.</span></span> <span data-ttu-id="c3713-434">Unity startet ein **Datei-Explorer** -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c3713-435">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**".</span><span class="sxs-lookup"><span data-stu-id="c3713-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="c3713-436">Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="c3713-437">Unity startet das Projekt in den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="c3713-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="c3713-438">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="c3713-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="c3713-439">So stellen Sie auf hololens bereit:</span><span class="sxs-lookup"><span data-stu-id="c3713-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c3713-440">Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden.</span><span class="sxs-lookup"><span data-stu-id="c3713-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="c3713-441">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="c3713-441">To do this:</span></span>

    1.  <span data-ttu-id="c3713-442">Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.</span><span class="sxs-lookup"><span data-stu-id="c3713-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="c3713-443">Navigieren Sie zu **Netzwerk &**  > erweiterte**Wi-Fi** > -**Optionen** für das Internet.</span><span class="sxs-lookup"><span data-stu-id="c3713-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="c3713-444">Notieren Sie sich die **IPv4** -Adresse.</span><span class="sxs-lookup"><span data-stu-id="c3713-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="c3713-445">Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie die **& Sicherheit** > **für Entwickler** .</span><span class="sxs-lookup"><span data-stu-id="c3713-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="c3713-446">Legen Sie **den Entwicklermodus auf**fest.</span><span class="sxs-lookup"><span data-stu-id="c3713-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="c3713-447">Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c3713-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3713-448">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="c3713-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="c3713-449">Wählen Sieauf der Projektmappenplattform die Option **x86, Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="c3713-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="c3713-450">Sie werden aufgefordert, die **IP-Adresse** eines Remote Geräts (in diesem Fall die hololens) einzufügen, die Sie notiert haben.</span><span class="sxs-lookup"><span data-stu-id="c3713-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="c3713-451">Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf die hololens quer zuladen.</span><span class="sxs-lookup"><span data-stu-id="c3713-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="c3713-452">Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="c3713-453">Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest.</span><span class="sxs-lookup"><span data-stu-id="c3713-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="c3713-454">Stellen Sie dann auf dem lokalen Computer bereit, *und wählen Sie*dann Projekt Mappe bereitstellen aus.</span><span class="sxs-lookup"><span data-stu-id="c3713-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="c3713-455">So verwenden Sie die Anwendung:</span><span class="sxs-lookup"><span data-stu-id="c3713-455">To use the application:</span></span>

<span data-ttu-id="c3713-456">Um die APP-Funktionalität zwischen *Trainings* Modus und *Vorhersage* Modus zu wechseln, müssen Sie die **appmode** -Variable aktualisieren, die sich in der " **Awa()** "-Methode innerhalb der *imagecapture* -Klasse befindet.</span><span class="sxs-lookup"><span data-stu-id="c3713-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="c3713-457">oder</span><span class="sxs-lookup"><span data-stu-id="c3713-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="c3713-458">Im *Trainings* Modus:</span><span class="sxs-lookup"><span data-stu-id="c3713-458">In *Training* mode:</span></span>

- <span data-ttu-id="c3713-459">Sehen Sie sich **Maus** oder **Tastatur** an, und verwenden Sie die **Tap-Geste**.</span><span class="sxs-lookup"><span data-stu-id="c3713-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="c3713-460">Als nächstes wird Text angezeigt, in dem Sie aufgefordert werden, ein Tag anzugeben.</span><span class="sxs-lookup"><span data-stu-id="c3713-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="c3713-461">Sagen Sie entweder **Maus** oder **Tastatur**.</span><span class="sxs-lookup"><span data-stu-id="c3713-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="c3713-462">Im *Vorhersage* Modus:</span><span class="sxs-lookup"><span data-stu-id="c3713-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="c3713-463">Betrachten Sie ein Objekt, und verwenden Sie die **Tap-Geste**.</span><span class="sxs-lookup"><span data-stu-id="c3713-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="c3713-464">Es wird Text angezeigt, der das erkannte Objekt mit der höchsten Wahrscheinlichkeit (normalisiert) bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c3713-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="c3713-465">Kapitel 14: auswerten und verbessern des Custom Vision Modells</span><span class="sxs-lookup"><span data-stu-id="c3713-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="c3713-466">Um den Dienst genauer zu gestalten, müssen Sie das Modell, das für die Vorhersage verwendet wird, weiter trainieren.</span><span class="sxs-lookup"><span data-stu-id="c3713-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="c3713-467">Dies erfolgt über die Verwendung der neuen Anwendung mit den *Trainings* -und *Vorhersage* Modi, bei denen letztere das Portal besuchen muss, was in diesem Kapitel behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="c3713-468">Bereiten Sie Ihr Portal mehrmals vor, um das Modell kontinuierlich zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="c3713-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="c3713-469">Wechseln Sie erneut in Ihr Azure Custom Vision-Portal, und wählen Sie die Registerkarte *Vorhersagen* aus, sobald Sie in Ihrem Projekt sind (in der oberen Mitte der Seite):</span><span class="sxs-lookup"><span data-stu-id="c3713-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="c3713-470">Alle Images, die während der Ausführung Ihrer Anwendung an den Dienst gesendet wurden, werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c3713-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="c3713-471">Wenn Sie mit dem Mauszeiger auf die Bilder zeigen, erhalten Sie die Vorhersagen, die für das Image erstellt wurden:</span><span class="sxs-lookup"><span data-stu-id="c3713-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="c3713-472">Wählen Sie eines der Images aus, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c3713-472">Select one of your images to open it.</span></span> <span data-ttu-id="c3713-473">Sobald das Bild geöffnet ist, werden die Vorhersagen für dieses Bild auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c3713-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="c3713-474">Wenn die Vorhersagen richtig waren und Sie dieses Bild dem Schulungs Modell Ihres dienstanders hinzufügen möchten, klicken Sie auf das Eingabefeld " *Meine Tags* ", und wählen Sie das Tag aus, das Sie zuordnen möchten.</span><span class="sxs-lookup"><span data-stu-id="c3713-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="c3713-475">Wenn Sie fertig sind, klicken Sie unten rechts auf die Schaltfläche *Speichern und schließen* , und fahren Sie mit dem nächsten Bild fort.</span><span class="sxs-lookup"><span data-stu-id="c3713-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="c3713-476">Wenn Sie wieder zum Bild Raster zurückkehren, werden Sie feststellen, dass die Bilder, denen Sie Tags hinzugefügt haben (und gespeichert), entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="c3713-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="c3713-477">Wenn Sie Bilder suchen, für die Sie nicht über das markierte Element verfügen, können Sie Sie löschen, indem Sie auf den Tick dieses Bilds klicken (kann dies für mehrere Bilder tun) und dann in der oberen rechten Ecke der Raster Seite auf *Löschen* klicken.</span><span class="sxs-lookup"><span data-stu-id="c3713-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="c3713-478">Im folgenden Popup Fenster können Sie auf *Ja, löschen* oder *Nein*klicken, um den Löschvorgang zu bestätigen bzw. abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="c3713-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="c3713-479">Wenn Sie den Vorgang fortsetzen möchten, klicken Sie oben rechts auf die grüne Schaltfläche " *Train* ".</span><span class="sxs-lookup"><span data-stu-id="c3713-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="c3713-480">Ihr Dienstmodell wird mit allen Images trainiert, die Sie jetzt bereitgestellt haben (wodurch es präziser wird).</span><span class="sxs-lookup"><span data-stu-id="c3713-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="c3713-481">Wenn das Training vollständig ist, klicken Sie erneut auf die Schaltfläche *Standard erstellen* , damit Ihre *Vorhersage-URL* weiterhin die aktuellste Iterationen des Dienes verwendet.</span><span class="sxs-lookup"><span data-stu-id="c3713-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="c3713-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="c3713-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="c3713-483">Ihre fertiggestellte Custom Vision-API-Anwendung</span><span class="sxs-lookup"><span data-stu-id="c3713-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="c3713-484">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Azure-Custom Vision-API nutzt, um reale Objekte zu erkennen, das Dienstmodell zu trainieren und sich über das gesehene Vertrauen zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="c3713-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c3713-485">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="c3713-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c3713-486">Übung 1</span><span class="sxs-lookup"><span data-stu-id="c3713-486">Exercise 1</span></span>

<span data-ttu-id="c3713-487">Trainieren Sie Ihre **Custom Vision Service** , um weitere Objekte zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c3713-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c3713-488">Übung 2</span><span class="sxs-lookup"><span data-stu-id="c3713-488">Exercise 2</span></span>

<span data-ttu-id="c3713-489">Um zu erfahren, was Sie gelernt haben, führen Sie die folgenden Übungen aus:</span><span class="sxs-lookup"><span data-stu-id="c3713-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="c3713-490">Spielen Sie einen Sound wieder, wenn ein Objekt erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="c3713-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="c3713-491">Übung 3</span><span class="sxs-lookup"><span data-stu-id="c3713-491">Exercise 3</span></span>

<span data-ttu-id="c3713-492">Verwenden Sie die API zum erneuten trainieren Ihres diensmit denselben Images, die von Ihrer APP analysiert werden, um den Dienst genauer zu gestalten (führen Sie sowohl Vorhersagen als auch Schulungen gleichzeitig aus).</span><span class="sxs-lookup"><span data-stu-id="c3713-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
