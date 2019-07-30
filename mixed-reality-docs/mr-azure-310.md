---
title: Mr und Azure 310-Objekterkennung
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie ein Machine Learning-Modell trainieren, und verwenden Sie dann das trainierte Modell, um ähnliche Objekte und ihre Position in der realen Welt aus einer gemischten Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Custom Vision, Objekterkennung, gemischte Realität, Academy, Unity, Tutorial, API, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544418"
---
>[!NOTE]
><span data-ttu-id="0a532-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="0a532-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0a532-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="0a532-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0a532-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0a532-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="0a532-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0a532-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="0a532-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0a532-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="0a532-110">Mr und Azure 310: Objekterkennung</span><span class="sxs-lookup"><span data-stu-id="0a532-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="0a532-111">In diesem Kurs erfahren Sie, wie Sie benutzerdefinierte visuelle Inhalte und deren räumliche Position in einem bereitgestellten Image erkennen können, indem Sie Azure Custom Vision "Objekt Erkennungsfunktionen" in einer Mixed Reality-Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a532-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="0a532-112">Mit diesem Dienst können Sie ein Machine Learning-Modell mithilfe von Objekt Images trainieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="0a532-113">Anschließend verwenden Sie das trainierte Modell, um ähnliche Objekte zu erkennen und einander in der realen Welt zu erkennen, wie von der Kamera Erfassung von Microsoft hololens oder einer Kamera mit einem PC für immersive (VR)-Headsets bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="0a532-115">**Azure-Custom Vision, Objekterkennung** ist ein Microsoft-Dienst, mit dem Entwickler benutzerdefinierte Abbild Klassifizierungen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="0a532-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="0a532-116">Diese Klassifizierungen können dann mit neuen Bildern verwendet werden, um Objekte innerhalb dieses neuen Bilds zu erkennen, indem Sie die **Feld Begrenzungen** innerhalb des Bilds selbst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0a532-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="0a532-117">Der Dienst bietet ein einfaches, leicht zu verwendende Onlineportal, um diesen Prozess zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="0a532-118">Weitere Informationen finden Sie unter den folgenden Links:</span><span class="sxs-lookup"><span data-stu-id="0a532-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="0a532-119">Azure-Custom Vision Seite</span><span class="sxs-lookup"><span data-stu-id="0a532-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="0a532-120">Limits und Kontingente</span><span class="sxs-lookup"><span data-stu-id="0a532-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="0a532-121">Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="0a532-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="0a532-122">Der Benutzer *ist in der* Lage, ein Objekt zu sehen, das Sie mithilfe des Azure-Custom Vision Service (Objekterkennung) trainiert haben.</span><span class="sxs-lookup"><span data-stu-id="0a532-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="0a532-123">Der Benutzer verwendet die *Tap* -Geste, um ein Bild von dem zu erfassenden Bild zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="0a532-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="0a532-124">Die APP sendet das Image an den Azure-Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="0a532-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="0a532-125">Es wird eine Antwort vom Dienst angezeigt, die das Ergebnis der Erkennung als Welt Raum Text anzeigt.</span><span class="sxs-lookup"><span data-stu-id="0a532-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="0a532-126">Dies wird durch die Verwendung der räumlichen Nachverfolgung von Microsoft hololens erreicht, um die Weltposition des erkannten Objekts zu verstehen, und dann das *Tag* zu verwenden, das den im Bild erkannten Werten zugeordnet ist, um den Bezeichnungs Text bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="0a532-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="0a532-127">Der Kurs umfasst auch das manuelle Hochladen von Bildern, das Erstellen von Tags und das Trainieren des Dienstanbieter, um verschiedene Objekte (im bereitgestellten Beispiel a Cup) zu erkennen, indem das *Begrenzungsfeld* innerhalb des Abbilds festgelegt wird, das Sie senden.</span><span class="sxs-lookup"><span data-stu-id="0a532-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="0a532-128">Nach der Erstellung und Verwendung der APP sollte der Entwickler zurück zum Azure-Custom Vision Service navigieren, die vom Dienst vorgenommenen Vorhersagen ermitteln und ermitteln, ob Sie richtig waren (durch Markieren von etwas, das der Dienst verpasst hat). Anpassen der *Begrenzungs Felder*).</span><span class="sxs-lookup"><span data-stu-id="0a532-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="0a532-129">Der Dienst kann dann neu trainiert werden, wodurch die Wahrscheinlichkeit erhöht wird, dass reale Objekte erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="0a532-130">In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus dem Azure-Custom Vision Service, Objekterkennung, in einer Unity-basierten Beispielanwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="0a532-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="0a532-131">Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.</span><span class="sxs-lookup"><span data-stu-id="0a532-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="0a532-132">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="0a532-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0a532-133">Natürlich</span><span class="sxs-lookup"><span data-stu-id="0a532-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0a532-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0a532-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0a532-135"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="0a532-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0a532-136">Mr und Azure 310: Objekterkennung</span><span class="sxs-lookup"><span data-stu-id="0a532-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="0a532-137">✔️</span><span class="sxs-lookup"><span data-stu-id="0a532-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="0a532-138">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0a532-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0a532-139">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0a532-140">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018).</span><span class="sxs-lookup"><span data-stu-id="0a532-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="0a532-141">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="0a532-142">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="0a532-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0a532-143">Einen Entwicklungs-PC</span><span class="sxs-lookup"><span data-stu-id="0a532-143">A development PC</span></span>
- [<span data-ttu-id="0a532-144">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="0a532-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0a532-145">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="0a532-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0a532-146">Unity 2017,4 LTS</span><span class="sxs-lookup"><span data-stu-id="0a532-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0a532-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0a532-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="0a532-148">Ein [Microsoft hololens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="0a532-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="0a532-149">Internet Zugriff für Azure-Setup und Custom Vision Service-Abruf</span><span class="sxs-lookup"><span data-stu-id="0a532-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="0a532-150">Für jedes Objekt, das von der Custom Vision erkannt werden soll, ist eine Reihe von mindestens 15 (15) Bildern erforderlich).</span><span class="sxs-lookup"><span data-stu-id="0a532-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="0a532-151">Wenn Sie möchten, können Sie die Images verwenden, die bereits mit diesem Kurs, [einer Reihe von Tassen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip), bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0a532-152">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="0a532-152">Before you start</span></span>

1.  <span data-ttu-id="0a532-153">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="0a532-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="0a532-154">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="0a532-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="0a532-155">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="0a532-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="0a532-156">Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="0a532-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="0a532-157">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="0a532-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="0a532-158">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="0a532-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="0a532-159">Kapitel 1: das Custom Vision-Portal</span><span class="sxs-lookup"><span data-stu-id="0a532-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="0a532-160">Um das **Azure-Custom Vision Service**verwenden zu können, müssen Sie eine Instanz von der Anwendung so konfigurieren, dass Sie Ihrer Anwendung zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="0a532-161">Navigieren [Sie zur **Custom Vision Service** Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="0a532-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="0a532-162">Klicken Sie auf " **Getting Started**".</span><span class="sxs-lookup"><span data-stu-id="0a532-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="0a532-163">Melden Sie sich beim Custom Vision-Portal an.</span><span class="sxs-lookup"><span data-stu-id="0a532-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="0a532-164">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="0a532-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0a532-165">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0a532-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="0a532-166">Wenn Sie sich zum ersten Mal angemeldet haben, werden Sie im Bereich mit den *Nutzungsbedingungen* aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="0a532-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="0a532-167">Aktivieren Sie das Kontrollkästchen, um *den Bedingungen zuzustimmen*.</span><span class="sxs-lookup"><span data-stu-id="0a532-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="0a532-168">Klicken Sie dann auf **Ich stimme**zu.</span><span class="sxs-lookup"><span data-stu-id="0a532-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="0a532-169">Nachdem Sie die Bedingungen zugestimmt haben, befinden Sie sich jetzt im Abschnitt " *Meine Projekte* ".</span><span class="sxs-lookup"><span data-stu-id="0a532-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="0a532-170">Klicken Sie auf **Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="0a532-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="0a532-171">Eine Registerkarte wird auf der rechten Seite angezeigt, auf der Sie aufgefordert werden, einige Felder für das Projekt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="0a532-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="0a532-172">Fügen Sie einen Namen für Ihr Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="0a532-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="0a532-173">Fügen Sie eine Beschreibung für das Projekt ein (**optional**).</span><span class="sxs-lookup"><span data-stu-id="0a532-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="0a532-174">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="0a532-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0a532-175">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="0a532-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0a532-176">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0a532-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="0a532-177">Wenn Sie [mehr über Azure-Ressourcengruppen erfahren möchten, navigieren Sie zu den zugehörigen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="0a532-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="0a532-178">Legen Sie die **Projekttypen** als **Objekterkennung (Vorschauversion)** fest.</span><span class="sxs-lookup"><span data-stu-id="0a532-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="0a532-179">Wenn Sie fertig sind, klicken Sie auf **Projekt erstellen**, und Sie werden auf die Seite Custom Vision Service Projekt umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="0a532-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="0a532-180">Kapitel 2: trainieren Ihres Custom Vision Projekts</span><span class="sxs-lookup"><span data-stu-id="0a532-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="0a532-181">Wenn Sie sich im Custom Vision Portal befinden, besteht das Hauptziel darin, das Projekt zu trainieren, um bestimmte Objekte in Bildern zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="0a532-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="0a532-182">Sie benötigen mindestens 15 (15) Images für jedes Objekt, das von Ihrer Anwendung erkannt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0a532-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="0a532-183">Sie können die Bilder verwenden, die mit diesem Kurs bereitgestellt werden ([eine Reihe von Tassen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="0a532-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="0a532-184">So trainieren Sie das Custom Vision Projekt:</span><span class="sxs-lookup"><span data-stu-id="0a532-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="0a532-185">Klicken Sie auf **+** die Schaltfläche neben **Tags**.</span><span class="sxs-lookup"><span data-stu-id="0a532-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="0a532-186">Fügen Sie einen **Namen** für das Tag hinzu, mit dem die Bilder verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="0a532-187">In diesem Beispiel verwenden wir Bilder von Tassen für die Erkennung, benennen Sie also das-Tag für this, **Cup**.</span><span class="sxs-lookup"><span data-stu-id="0a532-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="0a532-188">Klicken Sie abschließend auf **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="0a532-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="0a532-189">Sie werden feststellen, dass Ihr **Tag** hinzugefügt wurde (möglicherweise müssen Sie die Seite erneut laden, damit es angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="0a532-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="0a532-190">Klicken Sie in der Mitte der Seite auf **Bilder hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="0a532-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="0a532-191">Klicken Sie auf **lokale Dateien durchsuchen**, und navigieren Sie zu den Images, die Sie für ein Objekt hochladen möchten, das mindestens 15 (15) ist.</span><span class="sxs-lookup"><span data-stu-id="0a532-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="0a532-192">Sie können mehrere Bilder gleichzeitig zum Hochladen auswählen.</span><span class="sxs-lookup"><span data-stu-id="0a532-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="0a532-193">Wenn Sie alle Images ausgewählt haben, mit denen Sie das Projekt trainieren möchten, klicken Sie auf **Dateien hochladen** .</span><span class="sxs-lookup"><span data-stu-id="0a532-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="0a532-194">Die Dateien werden hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="0a532-194">The files will begin uploading.</span></span> <span data-ttu-id="0a532-195">Nachdem Sie den Upload bestätigt haben, klicken Sie auf **done**.</span><span class="sxs-lookup"><span data-stu-id="0a532-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="0a532-196">An diesem Punkt werden die Images hochgeladen, aber nicht markiert.</span><span class="sxs-lookup"><span data-stu-id="0a532-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="0a532-197">Verwenden Sie die Maus, um die Bilder zu markieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="0a532-198">Wenn Sie mit dem Mauszeiger auf das Bild zeigen, werden Sie durch eine Auswahl Markierung unterstützt, indem Sie automatisch eine Auswahl um das Objekt ziehen.</span><span class="sxs-lookup"><span data-stu-id="0a532-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="0a532-199">Wenn dies nicht zutrifft, können Sie eigene zeichnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="0a532-200">Dies wird erreicht, indem Sie mit der linken Maustaste auf die Maus klicken und den Auswahlbereich auf das Objekt ziehen.</span><span class="sxs-lookup"><span data-stu-id="0a532-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="0a532-201">Nach der Auswahl des Objekts innerhalb des Bilds wird eine kleine Aufforderung aufgefordert, das Regions- *Tag hinzuzufügen*.</span><span class="sxs-lookup"><span data-stu-id="0a532-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="0a532-202">Wählen Sie das zuvor erstellte Tag ("Cup", im obigen Beispiel) aus, oder wenn Sie weitere Tags hinzufügen, geben Sie dieses in ein, und klicken Sie auf die Schaltfläche **+ (plus)** .</span><span class="sxs-lookup"><span data-stu-id="0a532-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="0a532-203">Um das nächste Bild zu markieren, klicken Sie auf den Pfeil rechts neben dem Blatt, oder schließen Sie das Tag-Blatt (durch Klicken auf das **X** in der oberen rechten Ecke des Blatts), und klicken Sie dann auf das nächste Bild.</span><span class="sxs-lookup"><span data-stu-id="0a532-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="0a532-204">Wenn Sie das nächste Bild bereit haben, wiederholen Sie das gleiche Verfahren.</span><span class="sxs-lookup"><span data-stu-id="0a532-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="0a532-205">Führen Sie diese Schritte für alle Images aus, die Sie hochgeladen haben, bis Sie alle gekennzeichnet sind.</span><span class="sxs-lookup"><span data-stu-id="0a532-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="0a532-206">Sie können mehrere Objekte im gleichen Bild auswählen, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="0a532-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="0a532-207">Wenn Sie alle markiert haben, klicken Sie auf der linken Seite des Bildschirms auf die **markierte** Schaltfläche, um die markierten Bilder anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0a532-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="0a532-208">Sie sind jetzt bereit, ihren Dienst zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-208">You are now ready to train your Service.</span></span> <span data-ttu-id="0a532-209">Klicken Sie auf die Schaltfläche **trainieren** , und die erste Trainings Iterationen wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="0a532-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="0a532-210">Nachdem Sie erstellt wurde, können Sie zwei Schaltflächen mit dem Namen " **default** " und die **Vorhersage-URL**anzeigen.</span><span class="sxs-lookup"><span data-stu-id="0a532-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="0a532-211">Klicken Sie zuerst auf **Standardwert erstellen** , und klicken Sie dann auf **Vorhersage-URL**.</span><span class="sxs-lookup"><span data-stu-id="0a532-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="0a532-212">Der Endpunkt, der aus diesem bereitgestellt wird, wird auf den Wert festgelegt, welcher *iterations* Wert als Standard markiert wurde.</span><span class="sxs-lookup"><span data-stu-id="0a532-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="0a532-213">Wenn Sie später eine neue *iterations* Zeit erstellen und diese als Standard aktualisieren, müssen Sie den Code nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="0a532-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="0a532-214">Nachdem Sie auf die **Vorhersage-URL**geklickt haben *, öffnen Sie*den Editor, und kopieren Sie die **URL** (auch als **Vorhersage Endpunkt**bezeichnet) und den **Dienst Vorhersage Schlüssel**, um Sie abzurufen, wenn Sie Sie später im Code benötigen.</span><span class="sxs-lookup"><span data-stu-id="0a532-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="0a532-215">Kapitel 3: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="0a532-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="0a532-216">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="0a532-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0a532-217">Öffnen Sie **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="0a532-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="0a532-218">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="0a532-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="0a532-219">Fügen Sie **customvisionobjerkennung**ein.</span><span class="sxs-lookup"><span data-stu-id="0a532-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="0a532-220">Stellen Sie sicher, dass der Projekttyp auf **3D**festgelegt ist, und legen Sie den **Speicherort** auf einen passenden Wert fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="0a532-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0a532-221">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="0a532-222">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0a532-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0a532-223">Wechseln Sie zu \**Einstellungen* *Bearbeiten* > \* , und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="0a532-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0a532-224">Ändern Sie den **Editor für externe Skripts** in **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0a532-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="0a532-225">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="0a532-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="0a532-226">Navigieren Sie als nächstes zu **Datei >** Buildeinstellungen, und wechseln Sie zur **Plattform** *universelle Windows-Plattform*, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** .</span><span class="sxs-lookup"><span data-stu-id="0a532-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="0a532-227">Vergewissern Sie sich , dass im gleichen Fenster mit den Buildeinstellungen Folgendes festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="0a532-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="0a532-228">**Zielgerät** ist auf **hololens** festgelegt</span><span class="sxs-lookup"><span data-stu-id="0a532-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="0a532-229">Der Buildtyp ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0a532-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="0a532-230">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0a532-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="0a532-231">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0a532-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="0a532-232">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0a532-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="0a532-233">Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="0a532-234">Klicken Sie im gleichen Fenster mit den Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="0a532-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="0a532-235">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="0a532-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0a532-236">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="0a532-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0a532-237">Die CLR- **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung), wodurch der Editor neu gestartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="0a532-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="0a532-238">Das Skript für die **Skript** Erstellung sollte **.net**sein.</span><span class="sxs-lookup"><span data-stu-id="0a532-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="0a532-239">Der **API-Kompatibilitäts Grad** sollte **.NET 4,6**lauten.</span><span class="sxs-lookup"><span data-stu-id="0a532-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="0a532-240">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="0a532-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="0a532-241">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="0a532-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="0a532-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="0a532-242">**Webcam**</span></span>

        3. <span data-ttu-id="0a532-243">**Spatialperception**</span><span class="sxs-lookup"><span data-stu-id="0a532-243">**SpatialPerception**</span></span>

            <span data-ttu-id="0a532-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="0a532-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="0a532-245">Weiter unten im Bereich können Sie in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**) die **unterstützte Tick Virtual Reality**und dann sicherstellen, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="0a532-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="0a532-246">Zurück inden Buildeinstellungen: *\# Unity C-Projekte* sind nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="0a532-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="0a532-247">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="0a532-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="0a532-248">Klicken Sie **im Editor**auf**Projekt Einstellungs** > **Grafik** **Bearbeiten** > .</span><span class="sxs-lookup"><span data-stu-id="0a532-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="0a532-249">Im **Inspektor** -Bereich werden die *Grafikeinstellungen* geöffnet.</span><span class="sxs-lookup"><span data-stu-id="0a532-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="0a532-250">Scrollen Sie nach unten, bis Sie ein Array mit der Bezeichnung **Always include-Shader**sehen.</span><span class="sxs-lookup"><span data-stu-id="0a532-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="0a532-251">Fügen Sie einen Slot hinzu, indem Sie die **Größen** Variable um eins erhöhen (in diesem Beispiel war es 8, daher haben wir es 9).</span><span class="sxs-lookup"><span data-stu-id="0a532-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="0a532-252">Ein neuer Slot wird an der letzten Position des Arrays angezeigt, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="0a532-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="0a532-253">Klicken Sie im Slot auf den kleinen Zielkreis neben dem Slot, um eine Liste der Shader zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="0a532-254">Suchen Sie nach dem Legacy-Shader " **Shaders/transparent/diffuser** ", und doppelklicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="0a532-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="0a532-255">Kapitel 4: Importieren des Unity-Pakets "customvisionobjerkennung"</span><span class="sxs-lookup"><span data-stu-id="0a532-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="0a532-256">Für diesen Kurs erhalten Sie ein Unity-Ressourcenpaket mit dem Namen " **Azure-Mr-310. unitypackage**".</span><span class="sxs-lookup"><span data-stu-id="0a532-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="0a532-257">PP Alle Objekte, die von Unity unterstützt werden, einschließlich ganzer Szenen, können in eine **. unitypackage** -Datei gepackt und in andere Projekte exportiert/importiert werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="0a532-258">Dies ist die sicherste und effizienteste Methode zum Verschieben von Ressourcen zwischen verschiedenen Unity- **Projekten**.</span><span class="sxs-lookup"><span data-stu-id="0a532-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="0a532-259">Sie finden das [Azure-Mr-310-Paket, das Sie hier herunterladen müssen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="0a532-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="0a532-260">Klicken Sie oben auf dem Bildschirm mit dem Unity-Dashboard auf **Assets** , und klicken Sie dann auf **Paket > benutzerdefiniertes Paket importieren**.</span><span class="sxs-lookup"><span data-stu-id="0a532-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="0a532-261">Wählen Sie mit der Dateiauswahl das Paket **Azure-Mr-310. unitypackage** aus, und klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="0a532-262">Eine Liste der Komponenten für dieses Asset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a532-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="0a532-263">Bestätigen Sie den Import, indem Sie auf die Schaltfläche **importieren** klicken.</span><span class="sxs-lookup"><span data-stu-id="0a532-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="0a532-264">Nachdem der Import abgeschlossen wurde, werden Sie feststellen, dass dem Ordner " **Assets** " nun Ordner aus dem Paket hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="0a532-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="0a532-265">Diese Art von Ordnerstruktur ist typisch für ein Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="0a532-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="0a532-266">Der Material **-Ordner enthält** das Material, das vom **Cursor Cursor**verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="0a532-267">Der **Ordner Plug** -in enthält die newtonsoft-dll, die vom Code zum Deserialisieren der Webantwort des Diensts verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="0a532-268">Die zwei (2) verschiedenen Versionen, die im Ordner und Unterordner enthalten sind, sind erforderlich, damit die Bibliothek vom Unity-Editor und dem UWP-Build verwendet und erstellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="0a532-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="0a532-269">Der Ordner " **Prefabs** " enthält die in der Szene enthaltenen Prefabs.</span><span class="sxs-lookup"><span data-stu-id="0a532-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="0a532-270">Dies sind die folgenden:</span><span class="sxs-lookup"><span data-stu-id="0a532-270">Those are:</span></span>

        1.  <span data-ttu-id="0a532-271">Der **gazecursor**, der Cursor, der in der Anwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="0a532-272">Wird zusammen mit der spatialmapping-präfab verwendet, um auf der Grundlage physischer Objekte in der Szene platziert werden zu können.</span><span class="sxs-lookup"><span data-stu-id="0a532-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="0a532-273">Die **Bezeichnung**, die das UI-Objekt ist, das verwendet wird, um bei Bedarf das Objekttag in der Szene anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0a532-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="0a532-274">Die **spatialmapping**, bei der es sich um das Objekt handelt, das es der Anwendung ermöglicht, eine virtuelle Karte mithilfe der räumlichen Nachverfolgung von Microsoft hololens zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a532-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="0a532-275">Der Ordner **Szenen** , der derzeit die vorgefertigte Szene für diesen Kurs enthält.</span><span class="sxs-lookup"><span data-stu-id="0a532-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="0a532-276">Öffnen Sie im **Projekt Panel**den Ordner **Szenen** , und doppelklicken Sie auf **objdetectionscene**, um die Szene zu laden, die Sie für diesen Kurs verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="0a532-277">Es **ist kein Code enthalten**. Sie schreiben den Code, indem Sie diesen Kurs befolgen.</span><span class="sxs-lookup"><span data-stu-id="0a532-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="0a532-278">Kapitel 5: Erstellen der customvisionanalyser-Klasse.</span><span class="sxs-lookup"><span data-stu-id="0a532-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="0a532-279">An diesem Punkt können Sie Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="0a532-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="0a532-280">Sie beginnen mit der **customvisionanalyser** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="0a532-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="0a532-281">Die Aufrufe an die **Custom Vision Service**, die im unten gezeigten Code vorgenommen wurden, werden mithilfe der **Custom Vision Rest-API**vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="0a532-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="0a532-282">Durch die Verwendung dieser API sehen Sie, wie Sie diese API implementieren und nutzen können (nützlich, um zu verstehen, wie Sie etwas ähnliches implementieren können).</span><span class="sxs-lookup"><span data-stu-id="0a532-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="0a532-283">Beachten Sie, dass Microsoft ein **Custom Vision SDK** bietet, das auch zum Aufrufen des Dienstanbieter verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0a532-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="0a532-284">Weitere Informationen finden Sie im [Custom Vision SDK-Artikel](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="0a532-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="0a532-285">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="0a532-285">This class is responsible for:</span></span>

- <span data-ttu-id="0a532-286">Das letzte als Bytearray erfasste Bild wird geladen.</span><span class="sxs-lookup"><span data-stu-id="0a532-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="0a532-287">Das Bytearray wird zur Analyse an Ihre Azure **Custom Vision Service** -Instanz gesendet.</span><span class="sxs-lookup"><span data-stu-id="0a532-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="0a532-288">Die Antwort wird als JSON-Zeichenfolge empfangen.</span><span class="sxs-lookup"><span data-stu-id="0a532-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="0a532-289">Deserialisieren der Antwort und übergeben der resultierenden **Vorhersage** an die **sceneorganisator** -Klasse, um die Anzeige der Antwort zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="0a532-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="0a532-290">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="0a532-290">To create this class:</span></span>

1.  <span data-ttu-id="0a532-291">Klicken Sie im **Projekt Panel**mit der rechten Maustaste in den **Ordner Asset**, und klicken Sie dann auf**Ordner** **Erstellen** > .</span><span class="sxs-lookup"><span data-stu-id="0a532-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="0a532-292">Nennen Sie die Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="0a532-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="0a532-293">Doppelklicken Sie auf den neu erstellten Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="0a532-294">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **\# Skript** **Erstellen** > .</span><span class="sxs-lookup"><span data-stu-id="0a532-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0a532-295">Benennen Sie das Skript **customvisionanalyser.**</span><span class="sxs-lookup"><span data-stu-id="0a532-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="0a532-296">Doppelklicken Sie auf das neue **customvisionanalyser** -Skript, um es in **Visual Studio** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="0a532-297">Stellen Sie sicher, dass am Anfang der Datei die folgenden Namespaces referenziert sind:</span><span class="sxs-lookup"><span data-stu-id="0a532-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="0a532-298">Fügen Sie in der **customvisionanalyser** -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a532-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="0a532-299">Stellen Sie sicher, dass Sie den **Dienst Vorhersage-Key** in die " **prätionkey** "-Variable und ihren **Vorhersage Endpunkt** in die " **prätionendpoint** "-Variable einfügen</span><span class="sxs-lookup"><span data-stu-id="0a532-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="0a532-300">Sie [haben diese zuvor in den Editor in Kapitel 2, Schritt 14](#chapter-2---training-your-custom-vision-project)kopiert.</span><span class="sxs-lookup"><span data-stu-id="0a532-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="0a532-301">Code für **Awa()** muss nun hinzugefügt werden, um die Instanzvariable zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="0a532-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="0a532-302">Fügen Sie die Coroutine hinzu (mit der statischen **getimageasbytearray ()** -Methode darunter), die die Ergebnisse der Analyse des Bilds erhält, die von der **imagecapture** -Klasse aufgezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0a532-303">In der **analyseimagecapture** -Coroutine gibt es einen Aufrufen der **sceneorganisator** -Klasse, die Sie noch erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="0a532-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="0a532-304">Deshalb sollten Sie **diese Zeilen jetzt kommentiert lassen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="0a532-305">Löschen Sie die Methoden " **Start ()** " und " **Update ()** ", da Sie nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="0a532-306">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0a532-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a532-307">Wie bereits erwähnt, machen Sie sich keine Gedanken über Code, der möglicherweise einen Fehler enthält, da Sie weitere Klassen bald bereitstellen werden, die diese beheben.</span><span class="sxs-lookup"><span data-stu-id="0a532-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="0a532-308">Kapitel 6: Erstellen der customvisionobjects-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a532-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="0a532-309">Die Klasse, die Sie jetzt erstellen, ist die **customvisionobjects** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="0a532-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="0a532-310">Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe an die Custom Vision Service verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="0a532-311">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="0a532-311">To create this class:</span></span>

1.  <span data-ttu-id="0a532-312">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0a532-313">Nennen Sie das Skript **customvisionobjects.**</span><span class="sxs-lookup"><span data-stu-id="0a532-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="0a532-314">Doppelklicken Sie auf das neue **customvisionobjects** -Skript, um es in **Visual Studio** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0a532-315">Stellen Sie sicher, dass am Anfang der Datei die folgenden Namespaces referenziert sind:</span><span class="sxs-lookup"><span data-stu-id="0a532-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="0a532-316">Löschen Sie die Methoden " **Start ()** " und " **Update ()** " innerhalb der **customvisionobjects** -Klasse. diese Klasse sollte nun leer sein.</span><span class="sxs-lookup"><span data-stu-id="0a532-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="0a532-317">Es ist wichtig, dass Sie die nächste Anweisung sorgfältig befolgen.</span><span class="sxs-lookup"><span data-stu-id="0a532-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="0a532-318">Wenn Sie die neuen Klassen Deklarationen in der **customvisionobjects** -Klasse platzieren, erhalten Sie Kompilierungsfehler in [Kapitel 10](#chapter-10---create-the-imagecapture-class), in der angegeben wird, dass **analysisrootobject** und **BoundingBox** nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="0a532-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="0a532-319">Fügen Sie die folgenden Klassen *außerhalb* der **customvisionobjects** -Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="0a532-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="0a532-320">Diese Objekte werden von der **newtonsoft** -Bibliothek verwendet, um die Antwortdaten zu serialisieren und zu deserialisieren:</span><span class="sxs-lookup"><span data-stu-id="0a532-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="0a532-321">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0a532-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="0a532-322">Kapitel 7: Erstellen der spatialmapping-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a532-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="0a532-323">Mit dieser Klasse wird der **Collider der räumlichen Zuordnung** in der Szene so festgelegt, dass Konflikte zwischen virtuellen Objekten und echten Objekten erkannt werden können.</span><span class="sxs-lookup"><span data-stu-id="0a532-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="0a532-324">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="0a532-324">To create this class:</span></span>

1.  <span data-ttu-id="0a532-325">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0a532-326">Nennen Sie das Skript **spatialmapping.**</span><span class="sxs-lookup"><span data-stu-id="0a532-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="0a532-327">Doppelklicken Sie auf das neue **spatialmapping** -Skript, um es in **Visual Studio** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0a532-328">Stellen Sie sicher, dass die folgenden Namespaces oberhalb der **spatialmapping** -Klasse referenziert sind:</span><span class="sxs-lookup"><span data-stu-id="0a532-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="0a532-329">Fügen Sie dann die folgenden Variablen in der **spatialmapping** -Klasse oberhalb der **Start ()** -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a532-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="0a532-330">Fügen Sie die " **Awake ()** " und " **Start ()** " hinzu</span><span class="sxs-lookup"><span data-stu-id="0a532-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="0a532-331">Löschen Sie die **Update ()** -Methode.</span><span class="sxs-lookup"><span data-stu-id="0a532-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="0a532-332">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0a532-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="0a532-333">Kapitel 8: Erstellen der "gazecursor"-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a532-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="0a532-334">Diese Klasse ist für das Einrichten des Cursors an der richtigen Position in einem echten Bereich verantwortlich, indem der **spatialmappingcollider**-Wert verwendet wird, der im vorherigen Kapitel erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="0a532-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="0a532-335">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="0a532-335">To create this class:</span></span>

1.  <span data-ttu-id="0a532-336">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0a532-337">Skript für " **gazecursor** " abrufen</span><span class="sxs-lookup"><span data-stu-id="0a532-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="0a532-338">Doppelklicken Sie auf das neue **gazecursor** -Skript, um es in **Visual Studio** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0a532-339">Stellen Sie sicher, dass der folgende Namespace oberhalb der Klasse " **gazecursor** " referenziert ist:</span><span class="sxs-lookup"><span data-stu-id="0a532-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="0a532-340">Fügen Sie dann die folgende Variable in der Klasse " **gazecursor** " oberhalb der Methode " **Start ()** " ein.</span><span class="sxs-lookup"><span data-stu-id="0a532-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="0a532-341">Aktualisieren Sie die Methode " **Start ()** " mit dem folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="0a532-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="0a532-342">Aktualisieren Sie die **Update ()** -Methode mit dem folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="0a532-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="0a532-343">Machen Sie sich keine Sorgen, dass der Fehler für die **sceneorganisator** -Klasse nicht gefunden wird. Sie erstellen Sie im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="0a532-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="0a532-344">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0a532-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="0a532-345">Kapitel 9: Erstellen der sceneorganisator-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a532-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="0a532-346">Diese Klasse führt Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="0a532-346">This class will:</span></span>

-   <span data-ttu-id="0a532-347">Richten Sie die *Hauptkamera* ein, indem Sie die entsprechenden Komponenten an Sie anfügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="0a532-348">Wenn ein Objekt erkannt wird, ist es dafür verantwortlich, seine Position in der realen Welt zu berechnen und eine **tagbezeichnung** in der Nähe des entsprechenden **Tagnamens**zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="0a532-349">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="0a532-349">To create this class:</span></span>

1.  <span data-ttu-id="0a532-350">Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0a532-351">Nennen Sie das Skript **sceneorganisator**.</span><span class="sxs-lookup"><span data-stu-id="0a532-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="0a532-352">Doppelklicken Sie auf das neue **sceneorganisator** -Skript, um es in **Visual Studio** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0a532-353">Stellen Sie sicher, dass die folgenden Namespaces oberhalb der **sceneorganisator** -Klasse referenziert sind:</span><span class="sxs-lookup"><span data-stu-id="0a532-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="0a532-354">Fügen Sie dann die folgenden Variablen in der **sceneorganisator** -Klasse oberhalb der **Start ()** -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a532-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="0a532-355">Löschen Sie die Methoden " **Start ()** " und " **Update ()** ".</span><span class="sxs-lookup"><span data-stu-id="0a532-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="0a532-356">Fügen Sie unterhalb der Variablen die **Awa()** -Methode hinzu, die die Klasse initialisiert und die Szene einrichtet.</span><span class="sxs-lookup"><span data-stu-id="0a532-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="0a532-357">Fügen Sie die **placeanalysislabel ()** -Methode hinzu, die die Bezeichnung in der Szene *instanziiert* (die zu diesem Zeitpunkt für den Benutzer unsichtbar ist).</span><span class="sxs-lookup"><span data-stu-id="0a532-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="0a532-358">Außerdem wird das Quad (auch unsichtbar) platziert, wo das Bild platziert ist, und es wird mit der realen Welt überlappt.</span><span class="sxs-lookup"><span data-stu-id="0a532-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="0a532-359">Dies ist wichtig, da die Feld Koordinaten, die nach der Analyse vom Dienst abgerufen werden, wieder in dieses vierfache zurückgeführt werden, um die ungefähre Position des Objekts in der realen Welt zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="0a532-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="0a532-360">Fügen Sie die **finaliselabel ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="0a532-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="0a532-361">Er ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="0a532-361">It is responsible for:</span></span>

    *   <span data-ttu-id="0a532-362">Der Bezeichnungs *Text wird* mit dem *Tag* der Vorhersage mit dem höchsten Vertrauen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0a532-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="0a532-363">Aufrufen der Berechnung des umgebenden *Felds auf dem* Quad-Objekt, das zuvor positioniert wurde, und Platzieren der Bezeichnung in der Szene.</span><span class="sxs-lookup"><span data-stu-id="0a532-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="0a532-364">Anpassung der Bezeichnungs Tiefe mithilfe eines Raycasts in das umgebende *Feld*, das mit dem Objekt in der realen Welt kollidieren soll.</span><span class="sxs-lookup"><span data-stu-id="0a532-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="0a532-365">Zurücksetzen des Aufzeichnungsprozesses, um dem Benutzer zu ermöglichen, ein anderes Bild zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="0a532-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="0a532-366">Fügen Sie die **calculateboundingboxposition ()** -Methode hinzu, die eine Reihe von Berechnungen hostet, die erforderlich sind, um die vom Dienst abgerufenen umgebenden *Feld* Koordinaten zu übersetzen und diese proportional zum Quad neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0a532-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="0a532-367">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0a532-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0a532-368">Bevor Sie fortfahren, öffnen Sie die **customvisionanalyser** -Klasse, und heben Sie die Auskommentierung der folgenden Zeilen innerhalb der **analyselastimageaufgezeichnet ()** -Methode auf:</span><span class="sxs-lookup"><span data-stu-id="0a532-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="0a532-369">Machen Sie sich keine Gedanken über die Meldung "die **imagecapture** -Klasse wurde nicht gefunden", Sie erstellen Sie im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="0a532-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="0a532-370">Kapitel 10: Erstellen der imagecapture-Klasse</span><span class="sxs-lookup"><span data-stu-id="0a532-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="0a532-371">Die nächste Klasse, die Sie erstellen, ist die **imagecapture** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="0a532-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="0a532-372">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="0a532-372">This class is responsible for:</span></span>

*   <span data-ttu-id="0a532-373">Erfassen eines Bilds mithilfe der hololens-Kamera und speichern im *App* -Ordner.</span><span class="sxs-lookup"><span data-stu-id="0a532-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="0a532-374">Behandlung von *Tap* -Gesten vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="0a532-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="0a532-375">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="0a532-375">To create this class:</span></span>

1.  <span data-ttu-id="0a532-376">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="0a532-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="0a532-377">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **\# Skript** **Erstellen** > .</span><span class="sxs-lookup"><span data-stu-id="0a532-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0a532-378">Benennen Sie das Skript mit **imagecapture**.</span><span class="sxs-lookup"><span data-stu-id="0a532-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="0a532-379">Doppelklicken Sie auf das neue **imagecapture** -Skript, um es in **Visual Studio** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0a532-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="0a532-380">Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="0a532-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="0a532-381">Fügen Sie dann die folgenden Variablen in der **imagecapture** -Klasse oberhalb der **Start ()** -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a532-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="0a532-382">Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="0a532-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="0a532-383">Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Geste auftritt:</span><span class="sxs-lookup"><span data-stu-id="0a532-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="0a532-384">Wenn der Cursor **grün**ist, bedeutet dies, dass die Kamera verfügbar ist, um das Bild zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="0a532-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="0a532-385">Wenn der Cursor **rot**ist, bedeutet dies, dass die Kamera ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="0a532-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="0a532-386">Fügen Sie die Methode hinzu, die die Anwendung verwendet, um den Bild Aufzeichnungsprozess zu starten und das Image zu speichern:</span><span class="sxs-lookup"><span data-stu-id="0a532-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="0a532-387">Fügen Sie die Handler hinzu, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und für die Analyse bereit ist.</span><span class="sxs-lookup"><span data-stu-id="0a532-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="0a532-388">Das Ergebnis wird dann zur Analyse an **customvisionanalyser** weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="0a532-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="0a532-389">Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0a532-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="0a532-390">Kapitel 11: Einrichten der Skripts in der Szene</span><span class="sxs-lookup"><span data-stu-id="0a532-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="0a532-391">Nachdem Sie den gesamten für dieses Projekt erforderlichen Code geschrieben haben, können Sie nun die Skripts in der Szene und in den Prefabs einrichten, damit Sie ordnungsgemäß Verhalten.</span><span class="sxs-lookup"><span data-stu-id="0a532-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="0a532-392">Wählen Sie im **Unity-Editor**im Bereich **Hierarchie**die **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="0a532-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="0a532-393">Klicken Sie **im Inspektor-Panel**mit ausgewählter **Hauptkamera** auf **Komponente hinzufügen**, suchen Sie nach **sceneorganisator** -Skript, und doppelklicken Sie darauf, um es hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="0a532-394">Öffnen Sie im **Projekt Panel**den Ordner " **Prefabs**", und ziehen Sie die **Bezeichnung** "Prefab" in das Eingabefeld für das leere Verweis Ziel der *Bezeichnung* , das Sie der *Hauptkamera*soeben hinzugefügt haben, wie in dargestellt. Das folgende Bild:</span><span class="sxs-lookup"><span data-stu-id="0a532-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="0a532-395">Wählen Sie im Bereich **Hierarchie**das untergeordnete Element **gazecursor** der **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="0a532-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="0a532-396">Klicken Sie **im Inspektor-Panel**mit ausgewähltem **gazecursor** auf **Komponente hinzufügen**, suchen Sie nach dem **gazecursor** -Skript, und doppelklicken Sie darauf, um es hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="0a532-397">Wählen Sie im Bereich **Hierarchie**das untergeordnete **spatialmapping** -Element der **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="0a532-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="0a532-398">Klicken Sie **im Inspektor-Panel**bei ausgewähltem **spatialmapping** auf **Komponente hinzufügen**, suchen Sie nach dem **spatialmapping** -Skript, und doppelklicken Sie darauf, um es hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="0a532-399">Die übrigen Skripts, die Sie nicht festgelegt haben, werden während der Laufzeit vom Code im **sceneorganisator** -Skript hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0a532-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="0a532-400">Kapitel 12: vor dem Aufbau</span><span class="sxs-lookup"><span data-stu-id="0a532-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="0a532-401">Wenn Sie Ihre Anwendung gründlich testen möchten, müssen Sie Sie per querladen auf Ihre Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="0a532-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="0a532-402">Bevor Sie vorgehen, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="0a532-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="0a532-403">Alle im [Kapitel 3](#chapter-3---set-up-the-unity-project) erwähnten Einstellungen sind richtig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0a532-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="0a532-404">Das Skript **sceneorganisator** ist an das **Hauptkamera** Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="0a532-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="0a532-405">Das Skript " **gazecursor** " ist an das Objekt " **gazecursor** " angefügt.</span><span class="sxs-lookup"><span data-stu-id="0a532-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="0a532-406">Das Skript **spatialmapping** ist an das **spatialmapping** -Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="0a532-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="0a532-407">In [Kapitel 5](#chapter-5---create-the-customvisionanalyser-class), Schritt 6:</span><span class="sxs-lookup"><span data-stu-id="0a532-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="0a532-408">Stellen Sie sicher, dass Sie den **Dienst Vorhersage Schlüssel** in die " **prätionkey** "-Variable einfügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="0a532-409">Sie haben ihren **Vorhersage Endpunkt** in die " **vorhertionendpoint** "-Klasse eingefügt.</span><span class="sxs-lookup"><span data-stu-id="0a532-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="0a532-410">Kapitel 13: Erstellen der UWP-Lösung und querladen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="0a532-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="0a532-411">Sie können nun Ihre Anwendung als UWP-Lösung erstellen, die Sie auf den Microsoft hololens bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="0a532-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="0a532-412">So beginnen Sie den Buildprozess:</span><span class="sxs-lookup"><span data-stu-id="0a532-412">To begin the build process:</span></span>

1.  <span data-ttu-id="0a532-413">Wechseln Sie zu **Datei >** Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="0a532-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="0a532-414">Teil Strich **Unity\# -C-Projekte**.</span><span class="sxs-lookup"><span data-stu-id="0a532-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="0a532-415">Klicken Sie auf **offene Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="0a532-416">Dadurch wird dem Build die aktuell geöffnete Szene hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0a532-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="0a532-417">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-417">Click **Build**.</span></span> <span data-ttu-id="0a532-418">Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0a532-419">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**".</span><span class="sxs-lookup"><span data-stu-id="0a532-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="0a532-420">Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="0a532-421">Unity startet das Projekt in den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="0a532-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="0a532-422">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="0a532-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="0a532-423">Zum Bereitstellen von auf Microsoft hololens benötigen Sie die IP-Adresse dieses Geräts (für die Remote Bereitstellung) und, um sicherzustellen, dass der **Entwicklermodus** ebenfalls festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0a532-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="0a532-424">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="0a532-424">To do this:</span></span>

    1.  <span data-ttu-id="0a532-425">Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.</span><span class="sxs-lookup"><span data-stu-id="0a532-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="0a532-426">Navigieren Sie zu **Netzwerk &**  > erweiterte**Wi-Fi** > -**Optionen** für das Internet.</span><span class="sxs-lookup"><span data-stu-id="0a532-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="0a532-427">Notieren Sie sich die **IPv4** -Adresse.</span><span class="sxs-lookup"><span data-stu-id="0a532-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="0a532-428">Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie die **& Sicherheit** > **für Entwickler** .</span><span class="sxs-lookup"><span data-stu-id="0a532-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="0a532-429">Legen Sie den **Entwicklermodus** *auf*fest.</span><span class="sxs-lookup"><span data-stu-id="0a532-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="0a532-430">Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0a532-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="0a532-431">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="0a532-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="0a532-432">Wählen Sie auf der Projektmappenplattform die Option **x86, Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="0a532-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="0a532-433">Sie werden aufgefordert, die **IP-Adresse** eines Remote Geräts (in diesem Fall die von Ihnen notierten Microsoft hololens) einzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a532-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="0a532-434">Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf die hololens quer zuladen.</span><span class="sxs-lookup"><span data-stu-id="0a532-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="0a532-435">Ihre APP sollte nun in der Liste der installierten apps auf Ihren Microsoft hololens angezeigt werden, die bereit sind, gestartet zu werden!</span><span class="sxs-lookup"><span data-stu-id="0a532-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="0a532-436">So verwenden Sie die Anwendung:</span><span class="sxs-lookup"><span data-stu-id="0a532-436">To use the application:</span></span>

* <span data-ttu-id="0a532-437">Sehen Sie sich ein Objekt an, das Sie mit Ihrer **Azure-Custom Vision Service trainiert haben, Objekterkennung**, und verwenden Sie die **Tap-Geste**.</span><span class="sxs-lookup"><span data-stu-id="0a532-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="0a532-438">Wenn das Objekt erfolgreich erkannt wird, wird ein Text der *Bezeichnung* "World-Space" mit dem Tagnamen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0a532-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a532-439">Jedes Mal, wenn Sie ein Foto erfassen und an den Dienst senden, können Sie zur Dienst Seite zurückkehren und den Dienst mit den neu aufgezeichneten Images neu trainieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="0a532-440">Zu Beginn müssen Sie wahrscheinlich auch die *Begrenzungs Felder* korrigieren, um präziser zu werden und den Dienst erneut zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="0a532-441">Der Bezeichnungs Text wird möglicherweise nicht in der Nähe des Objekts angezeigt, wenn die Microsoft hololens-Sensoren und/oder die spatialtrackingcomponent in Unity die entsprechenden Kollisionen relativ zu den realen Objekten nicht platzieren.</span><span class="sxs-lookup"><span data-stu-id="0a532-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="0a532-442">Versuchen Sie, die Anwendung auf einer anderen Oberfläche zu verwenden, wenn dies der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="0a532-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="0a532-443">Ihre Custom Vision, Objekt Erkennungs Anwendung</span><span class="sxs-lookup"><span data-stu-id="0a532-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="0a532-444">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die das Azure-Custom Vision, Objekterkennungs-API nutzt, das ein Objekt aus einem Image erkennen kann, und dann eine ungefähre Position für dieses Objekt im 3D-Raum bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0a532-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0a532-445">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="0a532-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0a532-446">Übung 1</span><span class="sxs-lookup"><span data-stu-id="0a532-446">Exercise 1</span></span>

<span data-ttu-id="0a532-447">Wenn Sie der Text Bezeichnung hinzufügen, verwenden Sie einen semitransparenten Cube, um das echte Objekt in einem umgebenden 3D- *Feld*zu schließen.</span><span class="sxs-lookup"><span data-stu-id="0a532-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0a532-448">Übung 2</span><span class="sxs-lookup"><span data-stu-id="0a532-448">Exercise 2</span></span>

<span data-ttu-id="0a532-449">Trainieren Sie Ihre Custom Vision Service, um weitere Objekte zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="0a532-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="0a532-450">Übung 3</span><span class="sxs-lookup"><span data-stu-id="0a532-450">Exercise 3</span></span>

<span data-ttu-id="0a532-451">Spielen Sie einen Sound wieder, wenn ein Objekt erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="0a532-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="0a532-452">Übung 4</span><span class="sxs-lookup"><span data-stu-id="0a532-452">Exercise 4</span></span>

<span data-ttu-id="0a532-453">Verwenden Sie die API zum erneuten trainieren Ihres diensmit denselben Images, die von Ihrer APP analysiert werden, um den Dienst genauer zu gestalten (führen Sie sowohl Vorhersagen als auch Schulungen gleichzeitig aus).</span><span class="sxs-lookup"><span data-stu-id="0a532-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
