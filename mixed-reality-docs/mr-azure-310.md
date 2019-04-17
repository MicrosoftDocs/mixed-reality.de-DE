---
title: 'MR und Azure-310: Erkennung von Objekten'
description: Führen Sie diesen Kurs Informationen zum Trainieren von Machine Learning-Modell, und klicken Sie dann verwenden Sie das trainierte Modell, um ähnliche Objekte und ihre Position in der realen Welt von innerhalb einer mixed Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, benutzerdefiniertes maschinelles sehen, objekterkennung, mixed Reality, Academy, Unity, Tutorials, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593285"
---
>[!NOTE]
><span data-ttu-id="ca2f0-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ca2f0-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ca2f0-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ca2f0-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ca2f0-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ca2f0-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="ca2f0-110">Mr und Azure-310: Erkennung von Objekten</span><span class="sxs-lookup"><span data-stu-id="ca2f0-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="ca2f0-111">In diesem Kurs erfahren Sie, wie zur Erkennung von benutzerdefinierten visuellen Inhalt und die räumliche Position in einem bereitgestellten Image mithilfe von Azure Custom Vision "Objekt" Erkennungsfunktionen in einer mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="ca2f0-112">Dieser Dienst ermöglicht Ihnen zum Trainieren von Machine Learning-Modellen mithilfe von Objekt-Images.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="ca2f0-113">Anschließend verwenden Sie das trainierte Modell ähnlicher Objekte zu erkennen und Ungefährer ihren Standort in der realen Welt, gemäß Bereitstellung durch die Kamera-Aufnahme von Microsoft HoloLens oder Anschließen einer Kamera auf einem PC für immersive Headsets von (VR).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="ca2f0-115">**Azure Custom Vision, Objekterkennung** ist ein Microsoft-Service dem Entwickler benutzerdefinierte bildklassifizierungen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="ca2f0-116">Diese Klassifizierungen können dann mit neuen Images verwendet werden, um Objekte innerhalb dieses Image, zu erkennen, durch die Bereitstellung **Begrenzungsrahmen** im Abbild.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="ca2f0-117">Der Dienst bietet eine einfache, benutzerfreundliche, online-Portal, um diesen Prozess optimieren.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="ca2f0-118">Weitere Informationen finden Sie auf den folgenden Links:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="ca2f0-119">Seite "Azure Custom Vision"</span><span class="sxs-lookup"><span data-stu-id="ca2f0-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="ca2f0-120">Einschränkungen und Kontingenten</span><span class="sxs-lookup"><span data-stu-id="ca2f0-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="ca2f0-121">Nach Abschluss dieses Kurses verfügen Sie über ein mixed Reality-Anwendung die können die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="ca2f0-122">Der Benutzer kann *bestaunen* auf ein Objekt, das sie trainiert haben, mit der Azure Custom Vision Service, Erkennung von Objekten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="ca2f0-123">Der Benutzer verwendet die *Tippen Sie auf* Geste zum Erfassen eines Images für die sie betrachten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="ca2f0-124">Die app wird das Bild an der Azure Custom Vision Service senden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="ca2f0-125">Es werden eine Antwort aus dem Dienst, der das Ergebnis der Erkennung als Raum Text angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="ca2f0-126">Dies wird durch die Nutzung der Microsoft HoloLens räumliche nachverfolgen, als eine Möglichkeit, verstehen die World-Position des erkannten-Objekts, und klicken Sie dann mithilfe der *Tag* zugeordnet, was in der Abbildung zu erkannt wird Geben Sie den Text der Bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="ca2f0-127">Der Kurs behandelt auch manuell Hochladen von Images, Tags erstellen und Trainieren den Dienst zur Erkennung von anderen Objekte (im bereitgestellten Beispiel einer Tasse), durch Festlegen der *Grenze im* innerhalb des Bilds, das Sie übermitteln.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ca2f0-128">Nach der Erstellung und Verwendung der app, der Entwickler sollte navigieren Sie zurück zum Azure Custom Vision Service, die vom Dienst getroffenen Vorhersagen zu identifizieren und zu bestimmen, ob sie richtig oder nicht waren (durch Tags nichts des Diensts nicht teilnehmen konnten, und Anpassen der *umgebende Felder*).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="ca2f0-129">Der Dienst kann dann neu trainiert werden müssen die erhöht der Wahrscheinlichkeit, dass sie die Objekte der realen Welt erkennen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="ca2f0-130">In diesem Kurs erfahren Sie, wie die Ergebnisse aus der Azure Custom Vision Service, Erkennung von Objekten, in eine Unity-basierten Anwendung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="ca2f0-131">Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="ca2f0-132">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="ca2f0-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ca2f0-133">Kurs</span><span class="sxs-lookup"><span data-stu-id="ca2f0-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ca2f0-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ca2f0-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ca2f0-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="ca2f0-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ca2f0-136">MR und Azure-310: Erkennung von Objekten</span><span class="sxs-lookup"><span data-stu-id="ca2f0-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca2f0-137">✔️</span><span class="sxs-lookup"><span data-stu-id="ca2f0-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="ca2f0-138">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ca2f0-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ca2f0-139">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ca2f0-140">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="ca2f0-141">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="ca2f0-142">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ca2f0-143">Eine Entwicklungs-PC</span><span class="sxs-lookup"><span data-stu-id="ca2f0-143">A development PC</span></span>
- [<span data-ttu-id="ca2f0-144">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="ca2f0-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="ca2f0-145">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="ca2f0-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="ca2f0-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="ca2f0-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="ca2f0-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ca2f0-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="ca2f0-148">Ein [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="ca2f0-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="ca2f0-149">Zugriff auf das Internet für die Einrichtung von Azure und Custom Vision Service abrufen</span><span class="sxs-lookup"><span data-stu-id="ca2f0-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="ca2f0-150">Eine Reihe von Bildern mindestens fünfzehn (15) sind erforderlich) für jedes Objekt, das Custom Vision erkennen soll.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="ca2f0-151">Wenn Sie möchten, können Sie die mit diesem Kurs bereits bereitgestellten Images, [eine Reihe von Cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ca2f0-152">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="ca2f0-152">Before you start</span></span>

1.  <span data-ttu-id="ca2f0-153">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="ca2f0-154">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="ca2f0-155">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="ca2f0-156">Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="ca2f0-157">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="ca2f0-158">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="ca2f0-159">Kapitel 1: das Portal für benutzerdefiniertes maschinelles sehen</span><span class="sxs-lookup"><span data-stu-id="ca2f0-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="ca2f0-160">Verwenden der **Azure Custom Vision Service**, müssen Sie so konfigurieren Sie eine Instanz davon für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="ca2f0-161">Navigieren Sie [auf die **Custom Vision Service** Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="ca2f0-162">Klicken Sie auf **Einstieg**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="ca2f0-163">Melden Sie sich an das Portal für benutzerdefiniertes maschinelles sehen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="ca2f0-164">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ca2f0-165">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="ca2f0-166">Nachdem Sie sich zum ersten Mal angemeldet sind, Sie werden aufgefordert, mit der *Vertragsbedingungen* Bereich.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="ca2f0-167">Klicken Sie auf das Kontrollkästchen, um *stimmen Sie den Bedingungen*.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="ca2f0-168">Klicken Sie dann auf **ich stimme zu**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="ca2f0-169">Die Begriffe zugestimmt haben, Sie sind jetzt in der *Meine Projekte* Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="ca2f0-170">Klicken Sie auf **neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="ca2f0-171">Eine Registerkarte wird auf der rechten Seite angezeigt, wodurch Sie angeben, einige Felder für das Projekt angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="ca2f0-172">Fügen Sie einen Namen für Ihr Projekt</span><span class="sxs-lookup"><span data-stu-id="ca2f0-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="ca2f0-173">Fügen Sie eine Beschreibung für Ihr Projekt (**Optional**)</span><span class="sxs-lookup"><span data-stu-id="ca2f0-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="ca2f0-174">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ca2f0-175">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ca2f0-176">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diese Kurse) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="ca2f0-177">Wenn Sie möchten [erfahren Sie mehr über Azure-Ressourcengruppen, navigieren Sie zu den zugeordneten Dokumenten](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="ca2f0-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="ca2f0-178">Legen Sie die **Projekttypen** als **Objekterkennung (Vorschau)**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="ca2f0-179">Sobald Sie fertig sind, klicken Sie auf **projekterstellung**, und Sie gelangen auf der Projektseite Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="ca2f0-180">Kapitel 2 – trainieren Ihr Projekt Custom Vision</span><span class="sxs-lookup"><span data-stu-id="ca2f0-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="ca2f0-181">Einmal ist im Custom Vision-Portal Ihr Hauptziel zum Trainieren des Projekts für bestimmte Objekte in Bildern zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="ca2f0-182">Für jedes Objekt, das Sie Ihre Anwendung erkennen möchten, benötigen Sie die Bilder mindestens fünfzehn (15).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="ca2f0-183">Sie können die in diesem Kurs bereitgestellten Images ([eine Reihe von Cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="ca2f0-184">Um Ihr Projekt Custom Vision zu trainieren:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="ca2f0-185">Klicken Sie auf die **+** neben **Tags**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="ca2f0-186">Hinzufügen einer **Namen** für den Tag, das verwendet wird, um Ihre Images mit zuordnen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="ca2f0-187">In diesem Beispiel verwenden wir die Bilder der Cups für die Erkennung, damit das Tag für diese, mit dem Namen **Cup**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="ca2f0-188">Klicken Sie auf **speichern** wenn fertig gestellt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="ca2f0-189">Sie sehen Ihre **Tag** hinzugefügt wurde (möglicherweise müssen Sie Ihrer Seite angezeigt werden neu laden).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="ca2f0-190">Klicken Sie auf **Hinzufügen von Bildern** in der Mitte der Seite.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="ca2f0-191">Klicken Sie auf **lokale Dateien durchsuchen**, und navigieren Sie zu den Images, die Sie für ein Objekt, wobei das mindestens 15 (15) hochladen möchten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="ca2f0-192">Sie können mehrere Images zu einem Zeitpunkt, zum Hochladen auswählen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="ca2f0-193">Drücken Sie **Hochladen von Dateien** Nachdem Sie alle Bilder ausgewählt haben, möchten das Projekt zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="ca2f0-194">Hochladen beginnt die Dateien.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-194">The files will begin uploading.</span></span> <span data-ttu-id="ca2f0-195">Nachdem Sie die Bestätigung für das Hochladen haben, klicken Sie auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="ca2f0-196">An diesem Punkt sind Ihre Images hochgeladen, aber nicht mit Tags versehen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="ca2f0-197">Um Ihre Images markieren möchten, verwenden Sie die Maus aus.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="ca2f0-198">Wie Sie auf das Bild zeigen, wird eine Markierung für die Auswahl Sie unterstützen, indem Sie einen Auswahlbereich für das Objekt automatisch zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="ca2f0-199">Wenn sie nicht genau ist, können Sie Ihre eigenen zeichnen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="ca2f0-200">Dies erfolgt durch Klicken auf die Maus enthält, und ziehen den Auswahlbereich um das Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="ca2f0-201">Eine kleine Eingabeaufforderung fragt nach der Auswahl Ihres Objekts innerhalb des Bilds Sie *Region-Tag hinzufügen*.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="ca2f0-202">Wählen Sie Ihre zuvor erstellten Tags (im obigen Beispiel "Cup"), oder wenn Sie weitere Tags hinzufügen, geben Sie, dass in, und klicken Sie auf die **+ (plus)** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="ca2f0-203">Um die nächste Abbildung zu markieren, können Sie klicken Sie auf den Pfeil rechts neben dem Blatt ", oder schließen Sie das Blatt" Tags "(durch Klicken auf die **X** in der oberen rechten Ecke auf dem Blatt) und klicken Sie dann auf der nächsten Abbildung.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="ca2f0-204">Nachdem Sie die nächste Abbildung bereit haben, wiederholen Sie das gleiche Verfahren.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="ca2f0-205">Dies gilt für alle Images, die Sie hochgeladen haben, bis sie alle mit Tags versehen sind.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="ca2f0-206">Sie können mehrere Objekte auswählen, in dem gleichen Image, wie die folgende Abbildung:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="ca2f0-207">Nachdem Sie alle gekennzeichnet haben, klicken Sie auf die **markierten** Schaltfläche auf der linken Seite des Bildschirms, um die markierte Bilder anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="ca2f0-208">Sie können nun zum Trainieren Ihres Diensts.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-208">You are now ready to train your Service.</span></span> <span data-ttu-id="ca2f0-209">Klicken Sie auf die **Train** Schaltfläche und die erste Iteration der Schulung beginnt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="ca2f0-210">Nachdem es erstellt wurde, werden Sie zwei Schaltflächen angezeigt werden **Standard** und **Vorhersage URL**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="ca2f0-211">Klicken Sie auf **Standard** zuerst, klicken Sie dann auf auf **Vorhersage URL**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="ca2f0-212">Der Endpunkt, der aus diesem bereitgestellt werden, je nachdem, was je nastaven *Iteration* als Standard gekennzeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="ca2f0-213">Also, wenn Sie später einen neuen vornehmen *Iteration* und als Standard zu aktualisieren, müssen Sie nicht zum Ändern Ihres Codes.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="ca2f0-214">Nachdem Sie auf geklickt haben **Vorhersage URL**öffnen *Editor*, und kopieren und Einfügen der **URL** (so genannte Ihre **Vorhersage-Endpunkt**) und die **Vorhersage-Dienstschlüssel**, sodass Sie sie bei Bedarf später im Code abrufen können.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="ca2f0-215">Kapitel 3: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="ca2f0-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="ca2f0-216">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ca2f0-217">Open **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="ca2f0-218">Sie müssen jetzt einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="ca2f0-219">Fügen Sie **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="ca2f0-220">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**, und legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ca2f0-221">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="ca2f0-222">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ca2f0-223">Wechseln Sie zu **bearbeiten* > *Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ca2f0-224">Änderung **externen Skript-Editors** zu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="ca2f0-225">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="ca2f0-226">Navigieren Sie anschließend auf **Datei > Buildeinstellungen** , und wechseln Sie die **Plattform** zu *universelle Windows-Plattform*, und klicken Sie dann auf die **-Plattformwechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="ca2f0-227">In der gleichen **Buildeinstellungen** Fenster legen Sie Folgendes fest:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="ca2f0-228">**Geräte** nastaven NA hodnotu **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="ca2f0-229">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="ca2f0-230">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="ca2f0-231">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="ca2f0-232">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="ca2f0-233">Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="ca2f0-234">In der gleichen **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dies wird im entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspector** befindet.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="ca2f0-235">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ca2f0-236">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ca2f0-237">**Scripting Runtime Version** muss **experimentell** (.NET 4.6 entspricht), löst der Editor neu starten müssen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="ca2f0-238">**Back-End-Scripting** muss **.NET**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="ca2f0-239">**API-Kompatibilitätsebene** muss **.NET 4.6**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="ca2f0-240">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ca2f0-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="ca2f0-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-242">**Webcam**</span></span>

        3. <span data-ttu-id="ca2f0-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-243">**SpatialPerception**</span></span>

            <span data-ttu-id="ca2f0-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="ca2f0-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="ca2f0-245">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, dann stellen Sie sicher, dass die **gemischten Windows Realität SDK** hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="ca2f0-246">Im **Buildeinstellungen**, *Unity C\# Projekte* ist nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="ca2f0-247">Schließen der **Buildeinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="ca2f0-248">In der **Editor**, klicken Sie auf **bearbeiten** > **Projekteinstellungen** > **Grafiken**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="ca2f0-249">In der **Inspektor Bereich** der *für Grafiken* geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="ca2f0-250">Scrollen Sie nach unten, bis Sie sehen, dass ein Array namens **immer enthalten Shader**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="ca2f0-251">Slot hinzufügen, indem Sie erhöhen die **Größe** Variable, indem Sie eine (in diesem Beispiel 8 vorlag, daher haben wir es 9).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="ca2f0-252">Ein neuer Slot wird in der letzten Position des Arrays angezeigt, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="ca2f0-253">Klicken Sie auf den Slot auf den kleinen Kreis neben den Slot aus, um eine Liste von Shadern öffnen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="ca2f0-254">Suchen Sie nach der **Legacy Shader/Transparent / "Diffus"** Shader und doppelklicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="ca2f0-255">Kapitel 4: Importieren des CustomVisionObjDetection Unity-Pakets</span><span class="sxs-lookup"><span data-stu-id="ca2f0-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="ca2f0-256">Für diesen Kurs ein Unity Asset-Paket bereitgestellt wird aufgerufen, **Azure-MR-310.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="ca2f0-257">[TIPP] Alle Objekte, die von Unity, einschließlich der gesamte Szenen unterstützt können verpackt werden, in einem **.unitypackage** -Datei, und exportiert / importiert, die in anderen Projekten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="ca2f0-258">Dies ist die sicherste und effizienteste, Möglichkeit zum Verschieben von Ressourcen zwischen verschiedenen **Unity-Projekte**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="ca2f0-259">Sie finden die [Azure-MR-310-Paket, das Sie hier herunterladen müssen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="ca2f0-260">Mit dem Sie Unity-Dashboard, klicken Sie auf **Assets** klicken Sie dann im Menü am oberen Rand des Bildschirms auf **Paket importieren > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="ca2f0-261">Verwenden Sie die Dateiauswahl zum Auswählen der **Azure-MR-310.unitypackage** packen, und klicken Sie auf **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="ca2f0-262">Eine Liste der Komponenten für dieses Medienobjekt wird Ihnen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="ca2f0-263">Bestätigen Sie den Import, indem Sie auf die **importieren** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="ca2f0-264">Wenn es abgeschlossen ist, importieren, werden Sie sehen, dass die Ordner aus dem Paket jetzt hinzugefügt wurden Ihre **Assets** Ordner.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="ca2f0-265">Diese Art von Struktur ist typisch für ein Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="ca2f0-266">Die **Materialien** Ordner enthält das Material verwendet wird, durch die **bestaunen Cursor**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="ca2f0-267">Die **-Plug-Ins** Ordner enthält die Newtonsoft-DLL, die vom Code verwendet werden, um die Web-Antwort des Diensts zu deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="ca2f0-268">Die zwei (2) sind unterschiedliche Versionen enthalten, die in den Ordner und Unterordner, erforderlich, damit die Bibliothek von Unity-Editor und der UWP-Build erstellt und verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="ca2f0-269">Die **Prefabs** Ordner enthält die prefabs (Vorlagen) in der Szene enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="ca2f0-270">Dies sind:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-270">Those are:</span></span>

        1.  <span data-ttu-id="ca2f0-271">Die **GazeCursor**, den Cursor in der Anwendung verwendet.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="ca2f0-272">Funktioniert zusammen mit den SpatialMapping Prefab in der Szene auf physische Objekte platziert werden können.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="ca2f0-273">Die **Bezeichnung**, die das UI-Objekt, das zum Anzeigen der Object-Tag in der Szene, bei Bedarf verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="ca2f0-274">Die **SpatialMapping**, die das Objekt, das die Anwendung verwenden kann, erstellen eine virtuelle Zuordnung mithilfe der Microsoft HoloLens räumliche nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="ca2f0-275">Die **Szenen** Ordner mit dem derzeit die vorab erstellte Szene für diesen Kurs.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="ca2f0-276">Öffnen der **Szenen** Ordner, in der **Projektbereich**, und doppelklicken Sie auf die **ObjDetectionScene**, um die Szene laden, die Sie für diesen Kurs verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="ca2f0-277">**Es ist kein Code enthalten**, Schreiben Sie Code anhand dieses Kurses.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="ca2f0-278">Kapitel 5 – erstellen Sie die CustomVisionAnalyser-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="ca2f0-279">An diesem Punkt können Sie Code schreiben.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="ca2f0-280">Beginnen Sie mit der **CustomVisionAnalyser** Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="ca2f0-281">Die Aufrufe an die **Custom Vision Service**, in den folgenden Code vorgenommen wurden, erfolgen mithilfe der **Custom Vision-REST-API**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="ca2f0-282">Durch die Verwendung dieser, erfahren Sie, wie zu implementieren und Verwenden dieser API (nützlich, um zu verstehen, wie etwa selbst implementiert).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="ca2f0-283">Darüber im Klaren sein, dass Microsoft bietet eine **Custom Vision SDK** , auch für Aufrufe an den Dienst verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="ca2f0-284">Weitere Informationen finden Sie auf die [Custom Vision SDK Artikel](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="ca2f0-285">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-285">This class is responsible for:</span></span>

- <span data-ttu-id="ca2f0-286">Laden das neueste Image als ein Array von Bytes erfasst.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="ca2f0-287">Das Bytearray an Azure senden **Custom Vision Service** Instanz für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="ca2f0-288">Empfangen der Antwort als JSON-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="ca2f0-289">Die Antwort zu deserialisieren, und übergeben die resultierenden **Vorhersage** auf die **SceneOrganiser** -Klasse, die kümmern wird wie die Antwort angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="ca2f0-290">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-290">To create this class:</span></span>

1.  <span data-ttu-id="ca2f0-291">Mit der rechten Maustaste den **Ordner "Assets"** befindet sich in der **Projektfenster**, klicken Sie dann auf **erstellen** > **Ordner**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="ca2f0-292">Rufen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="ca2f0-293">Doppelklicken Sie auf den neu erstellten Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="ca2f0-294">Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ca2f0-295">Nennen Sie das Skript **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="ca2f0-296">Doppelklicken Sie auf die neue **CustomVisionAnalyser** Skript öffnen Sie ihn mit **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="ca2f0-297">Stellen Sie sicher, dass Sie die folgenden Namespaces am Anfang der Datei verwiesen haben:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="ca2f0-298">In der **CustomVisionAnalyser** -Klasse verwenden, fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="ca2f0-299">Stellen Sie sicher, dass Sie Einfügen Ihrer **Vorhersage-Dienstschlüssel** in die **PredictionKey** Variable und Ihr **Vorhersage-Endpoint** in die **PredictionEndpoint**  Variable.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="ca2f0-300">Sie kopiert haben, diese [Editor früher in Kapitel 2, Schritt 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="ca2f0-301">Code für **Awake()** muss nun hinzugefügt werden, um die Instanz-Variable zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="ca2f0-302">Fügen Sie die Coroutine (mit der statischen **GetImageAsByteArray()** Methode darunter), die erhalten die Ergebnisse der Analyse des Bilds von erfasst die **digitale Bilder** Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ca2f0-303">In der **AnalyseImageCapture** Coroutine, erfolgt ein Aufruf von der **SceneOrganiser** -Klasse, die Sie noch erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="ca2f0-304">Aus diesem Grund **lassen Sie diese Zeilen jetzt kommentiert**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="ca2f0-305">Löschen der **Start()** und **Update()** Methoden, wie sie nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="ca2f0-306">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca2f0-307">Wie bereits erwähnt, aber keine Sorge, über Code, die einen Fehler, angezeigt werden kann, wie Sie weitere Klassen bald angeben werden, die diese behoben werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="ca2f0-308">Kapitel 6: Erstellen Sie die CustomVisionObjects-Klasse</span><span class="sxs-lookup"><span data-stu-id="ca2f0-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="ca2f0-309">Die Klasse, die Sie erstellen nun ist die **CustomVisionObjects** Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="ca2f0-310">Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe für den Custom Vision Service verwendet.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="ca2f0-311">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-311">To create this class:</span></span>

1.  <span data-ttu-id="ca2f0-312">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ca2f0-313">Rufen Sie das Skript **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="ca2f0-314">Doppelklicken Sie auf die neue **CustomVisionObjects** Skript öffnen Sie ihn mit **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="ca2f0-315">Stellen Sie sicher, dass Sie die folgenden Namespaces am Anfang der Datei verwiesen haben:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="ca2f0-316">Löschen der **Start()** und **Update()** Methoden innerhalb der **CustomVisionObjects** -Klasse, diese Klasse sollte jetzt leer sein.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="ca2f0-317">Es ist wichtig, dass Sie sorgfältig die nächste Anweisung ausführen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="ca2f0-318">Wenn Sie die neue Klassendeklarationen in Ablegen der **CustomVisionObjects** -Klasse, Sie erhalten Kompilierungsfehler in [Kapitel 10](#chapter-10---create-the-imagecapture-class), mit der Nachricht, **AnalysisRootObject** und  **BoundingBox** wurden nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="ca2f0-319">Fügen Sie die folgenden Klassen *außerhalb* der **CustomVisionObjects** Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="ca2f0-320">Diese Objekte werden verwendet, durch die **Newtonsoft** Bibliothek zum Serialisieren und Deserialisieren die Antwortdaten werden:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="ca2f0-321">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="ca2f0-322">Kapitel 7: Erstellen Sie die SpatialMapping-Klasse</span><span class="sxs-lookup"><span data-stu-id="ca2f0-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="ca2f0-323">Diese Klasse wird festgelegt. die **räumliche Zuordnung "collider"** in der Szene, um Konflikte zwischen virtuellen und echte Objekten erkennen können.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="ca2f0-324">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-324">To create this class:</span></span>

1.  <span data-ttu-id="ca2f0-325">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ca2f0-326">Rufen Sie das Skript **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="ca2f0-327">Doppelklicken Sie auf die neue **SpatialMapping** Skript öffnen Sie ihn mit **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="ca2f0-328">Stellen Sie sicher, dass die folgenden Namespaces, die oben genannten der **SpatialMapping** Klasse:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="ca2f0-329">Fügen Sie dann die folgenden Variablen in der **SpatialMapping** Klasse, über die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="ca2f0-330">Hinzufügen der **Awake()** und **Start()**:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="ca2f0-331">Löschen der **Update()** Methode.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="ca2f0-332">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="ca2f0-333">Kapitel 8 – erstellen Sie die GazeCursor-Klasse</span><span class="sxs-lookup"><span data-stu-id="ca2f0-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="ca2f0-334">Diese Klasse ist zuständig für das Einrichten des Cursors am korrekten Ort im realen Bereich dafür können Sie von der **SpatialMappingCollider**, in dem vorhergehenden Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="ca2f0-335">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-335">To create this class:</span></span>

1.  <span data-ttu-id="ca2f0-336">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ca2f0-337">Rufen Sie das Skript **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="ca2f0-338">Doppelklicken Sie auf die neue **GazeCursor** Skript öffnen Sie ihn mit **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="ca2f0-339">Stellen Sie sicher, dass Sie den folgenden Namespace, der oben genannten der **GazeCursor** Klasse:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="ca2f0-340">Dann fügen die folgende Variable innerhalb der **GazeCursor** Klasse, über die **Start()** Methode.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="ca2f0-341">Update der **Start()** Methode durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="ca2f0-342">Update der **Update()** Methode durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="ca2f0-343">Aber keine Sorge, über den Fehler für die **SceneOrganiser** Klasse nicht gefunden wird, erstellen Sie ihn im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="ca2f0-344">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="ca2f0-345">Kapitel 9 – erstellen Sie die SceneOrganiser-Klasse</span><span class="sxs-lookup"><span data-stu-id="ca2f0-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="ca2f0-346">Diese Klasse führt Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-346">This class will:</span></span>

-   <span data-ttu-id="ca2f0-347">Einrichten der *Main Camera* durch Anfügen der entsprechenden Komponenten zu.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="ca2f0-348">Wenn ein Objekt erkannt wird, ist sie werden verantwortlich für die Berechnung von seiner Position in der realen Welt und den Ort einer **Tag-Bezeichnung** es mit dem entsprechenden in der Nähe **Tagnamen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="ca2f0-349">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-349">To create this class:</span></span>

1.  <span data-ttu-id="ca2f0-350">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ca2f0-351">Nennen Sie das Skript **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="ca2f0-352">Doppelklicken Sie auf die neue **SceneOrganiser** Skript öffnen Sie ihn mit **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="ca2f0-353">Stellen Sie sicher, dass die folgenden Namespaces, die oben genannten der **SceneOrganiser** Klasse:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="ca2f0-354">Klicken Sie dann fügen Sie die folgenden Variablen in der **SceneOrganiser** Klasse, über die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="ca2f0-355">Löschen der **Start()** und **Update()** Methoden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="ca2f0-356">Fügen Sie unterhalb der Variablen, die **Awake()** -Methode, die Initialisieren der Klasse und der Szene eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="ca2f0-357">Hinzufügen der **PlaceAnalysisLabel()** -Methode, die wird *Instantiate* die Bezeichnung in der Szene (was an diesem Punkt für den Benutzer unsichtbar ist).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="ca2f0-358">Es wird auch die Quad (auch nicht sichtbar), in dem das Bild wird gespeichert und überschneidet sich mit der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="ca2f0-359">Dies ist wichtig, da die Koordinaten des Felds aus dem Dienst abgerufen werden, nach der Analyse wird zurück in diese Quad bestimmt die ungefähre Position des Objekts in der realen Welt verfolgt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="ca2f0-360">Hinzufügen der **FinaliseLabel()** Methode.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="ca2f0-361">Er ist verantwortlich für:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-361">It is responsible for:</span></span>

    *   <span data-ttu-id="ca2f0-362">Festlegen der *Bezeichnung* Text mit der *Tag* der Vorhersage mit der höchsten Sicherheit.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="ca2f0-363">Die Berechnung von Aufrufen der *umgebende Feld* auf das Vierfache Objekt, das zuvor positioniert und die Bezeichnung in der Szene platzieren.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="ca2f0-364">Anpassen der Bezeichnung Tiefe mithilfe einer Raycast für die *umgebende Feld*, die für das Objekt in der realen Welt in Konflikt stehen sollten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="ca2f0-365">Zurücksetzen des Capture-Prozess, um dem Benutzer ermöglichen, ein anderes Bild zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="ca2f0-366">Hinzufügen der **CalculateBoundingBoxPosition()** -Methode, die eine Anzahl von Berechnungen, die zum Übersetzen hostet die *umgebende Feld* Koordinaten aus dem Dienst abgerufen und neu erstellen proportional in der Quad.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="ca2f0-367">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ca2f0-368">Bevor Sie fortfahren, öffnen Sie die **CustomVisionAnalyser** -Klasse, und innerhalb der **AnalyseLastImageCaptured()** -Methode, *heben Sie die auskommentierung* die folgenden Zeilen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="ca2f0-369">Führen Sie sich keine Gedanken über die **digitale Bilder** Klasse 'konnte nicht gefunden werden kann'-Nachricht, erstellen Sie ihn im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="ca2f0-370">Kapitel 10 – erstellen Sie die digitale Bilder-Klasse</span><span class="sxs-lookup"><span data-stu-id="ca2f0-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="ca2f0-371">Die nächste Klasse, die Sie erstellen wollen ist die **digitale Bilder** Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="ca2f0-372">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-372">This class is responsible for:</span></span>

*   <span data-ttu-id="ca2f0-373">Erfassen eines Abbilds verwenden der Kamera HoloLens und speichern ihn in das *App* Ordner.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="ca2f0-374">Behandeln von *Tippen Sie auf* Bewegungen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="ca2f0-375">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-375">To create this class:</span></span>

1.  <span data-ttu-id="ca2f0-376">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="ca2f0-377">Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen** > **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ca2f0-378">Nennen Sie das Skript **digitale Bilder**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="ca2f0-379">Doppelklicken Sie auf die neue **digitale Bilder** Skript öffnen Sie ihn mit **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="ca2f0-380">Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="ca2f0-381">Klicken Sie dann fügen Sie die folgenden Variablen in der **digitale Bilder** Klasse, über die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="ca2f0-382">Code für **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="ca2f0-383">Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Bewegung erfolgt:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="ca2f0-384">Wenn der Cursor befindet sich **Grün**, bedeutet dies, dass die Kamera verfügbar ist, wird das Bild.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="ca2f0-385">Wenn der Cursor befindet sich **roten**, bedeutet dies, dass die Kamera ausgelastet.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="ca2f0-386">Fügen Sie die Methode, die die Anwendung verwendet wird, starten den Prozess der abbilderfassung aus, und speichern Sie das Abbild hinzu:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="ca2f0-387">Fügen Sie die Handler, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und wann es analysiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="ca2f0-388">Das Ergebnis wird dann zum Übergeben der **CustomVisionAnalyser** für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="ca2f0-389">Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="ca2f0-390">Kapitel 11: die Skripts in der Szene einrichten</span><span class="sxs-lookup"><span data-stu-id="ca2f0-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="ca2f0-391">Nun, da Sie alle für dieses Projekt erforderlichen Code geschrieben haben, ist an der Zeit, um die Skripts in der Szene, und klicken Sie auf den prefabs (Vorlagen für ordnungsgemäß Verhalten) einzurichten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="ca2f0-392">In der **Unity-Editor**in die **Hierarchie Bereich**, wählen die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="ca2f0-393">In der **Inspektor Bereich**, mit der **Main Camera** ausgewählt haben, klicken Sie auf **Add Component**, suchen Sie nach **SceneOrganiser** Skript und Doppelklicken Sie auf, um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="ca2f0-394">In der **Projektfenster**öffnen die **Ordner "Prefabs"**, ziehen Sie die **Bezeichnung** prefab in die *Bezeichnung* leere Verweisziel Geben Sie im Bereich der **SceneOrganiser** -Skript, das Sie gerade hinzugefügt haben die *Main Camera*, wie in der folgenden Abbildung gezeigt:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="ca2f0-395">In der **Hierarchie Bereich**, wählen die **GazeCursor** untergeordnetes Element von der **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="ca2f0-396">In der **Inspektor Bereich**, mit der **GazeCursor** ausgewählt haben, klicken Sie auf **Add Component**, suchen Sie nach **GazeCursor** Skript und Doppelklicken Sie auf, um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="ca2f0-397">Auch hier gilt die **Hierarchie Bereich**, wählen die **SpatialMapping** untergeordnetes Element von der **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="ca2f0-398">In der **Inspektor Bereich**, mit der **SpatialMapping** ausgewählt haben, klicken Sie auf **Add Component**, suchen Sie nach **SpatialMapping** Skript und doppelklicken Sie darauf, um es hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="ca2f0-399">Die verbleibenden Skripts, die Sie haben keine Gruppe wird hinzugefügt werden, indem der Code in die **SceneOrganiser** Skript während der Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="ca2f0-400">Kapitel 12 – vor dem Erstellen</span><span class="sxs-lookup"><span data-stu-id="ca2f0-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="ca2f0-401">Zur Durchführung einer gründliche Tests Ihrer Anwendung werden Sie querladen möchten sie auf Ihre Microsoft HoloLens benötigen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="ca2f0-402">Vor dem Ausführen, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="ca2f0-403">Alle Einstellungen, die bereits erwähnt, der [Kapitel 3](#chapter-3---set-up-the-unity-project) ordnungsgemäß festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="ca2f0-404">Das Skript **SceneOrganiser** angefügt ist die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="ca2f0-405">Das Skript **GazeCursor** angefügt ist die **GazeCursor** Objekt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="ca2f0-406">Das Skript **SpatialMapping** angefügt ist die **SpatialMapping** Objekt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="ca2f0-407">In [Kapitel 5](#chapter-5---create-the-customvisionanalyser-class), Schritt 6:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="ca2f0-408">Stellen Sie sicher, Sie fügen Ihre **Dienstschlüssel für die Vorhersage** in die **PredictionKey** Variable.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="ca2f0-409">Sie eingefügt haben Ihre **Endpunkt der Vorhersage** in die **PredictionEndpoint** Klasse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="ca2f0-410">Kapitel 13 – erstellen Sie die UWP-Projektmappe, und Laden Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="ca2f0-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="ca2f0-411">Sie können nun möchten Sie die Anwendung als UWP-Lösung zu erstellen, die Sie an den Microsoft HoloLens bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="ca2f0-412">Um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-412">To begin the build process:</span></span>

1.  <span data-ttu-id="ca2f0-413">Wechseln Sie zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="ca2f0-414">Teilstriche **Unity C\# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="ca2f0-415">Klicken Sie auf **Hinzufügen von Open Szenen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="ca2f0-416">Dadurch wird die derzeit geöffnete Szene mit dem Build hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="ca2f0-417">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-417">Click **Build**.</span></span> <span data-ttu-id="ca2f0-418">Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="ca2f0-419">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="ca2f0-420">Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="ca2f0-421">Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="ca2f0-422">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="ca2f0-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="ca2f0-423">Um sich bei Microsoft HoloLens bereitzustellen, benötigen Sie die IP-Adresse des Geräts (für Remote bereitstellen), und um außerdem sicherzustellen, dass es hat **Entwicklermodus** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="ca2f0-424">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-424">To do this:</span></span>

    1.  <span data-ttu-id="ca2f0-425">Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="ca2f0-426">Wechseln Sie zu **Netzwerk und Internet** > **Wi-Fi** > **erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="ca2f0-427">Beachten Sie die **IPv4** Adresse.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="ca2f0-428">Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit** > **für Entwickler**</span><span class="sxs-lookup"><span data-stu-id="ca2f0-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="ca2f0-429">Legen Sie **Entwicklermodus** *auf*.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="ca2f0-430">Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="ca2f0-431">In der Projektmappenkonfiguration Select **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="ca2f0-432">Wählen Sie in der Plattform für die Projektmappe **X86, Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="ca2f0-433">Werden Sie aufgefordert, fügen Sie der **IP-Adresse** von einem Remotegerät (die Microsoft HoloLens, in diesem Fall, den Sie notiert haben).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="ca2f0-434">Wechseln Sie zu der **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="ca2f0-435">Ihre app sollte nun in der Liste der installierten apps auf Ihre Microsoft HoloLens, möchten Sie die gestartet werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="ca2f0-436">Die Anwendung zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="ca2f0-436">To use the application:</span></span>

* <span data-ttu-id="ca2f0-437">Sehen Sie sich ein Objekt, das mit dem Sie trainiert haben Ihre **Azure Custom Vision Service, Objekterkennung**, und verwenden Sie die **tippen**.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="ca2f0-438">Wenn das Objekt erfolgreich erkannt wird, einen Raum *Bezeichnungstext* wird mit den Namen des Tags angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca2f0-439">Jedes Mal, wenn Sie ein Foto zu erfassen und an den Dienst senden, können Sie wechseln Sie zurück zu der Seite des Diensts und Trainieren den Dienst mit den neu aufgenommenen Bildern.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="ca2f0-440">Zu Beginn, wahrscheinlich werden Sie müssen auch korrigieren der *umgebende Felder* genauer sein und den Dienst erneut zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="ca2f0-441">Der Text der Bezeichnung platziert möglicherweise nicht in der Nähe des Objekts angezeigt, wenn der Microsoft HoloLens-Sensor und/oder die SpatialTrackingComponent in Unity ein Fehler auftritt, platzieren Sie den entsprechenden collider, relativ zu der realen Welt-Objekten.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="ca2f0-442">Versuchen Sie, die die Anwendung auf einer anderen Oberfläche verwenden, wenn dies der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="ca2f0-443">Ihre Custom Vision, Objekterkennung-Anwendung</span><span class="sxs-lookup"><span data-stu-id="ca2f0-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="ca2f0-444">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Azure Custom Vision, Detection-API-Objekt, das ein Objekt aus einem Bild erkennen können, und geben Sie eine ungefähre Position für das Objekt im 3D-Raum, nutzt.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ca2f0-445">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="ca2f0-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ca2f0-446">Übung 1</span><span class="sxs-lookup"><span data-stu-id="ca2f0-446">Exercise 1</span></span>

<span data-ttu-id="ca2f0-447">Hinzufügen, das die Textbezeichnung einen semitransparente Cube verwenden, um das eigentliche Objekt in ein 3D-Diagrammlayout zu umschließen *umgebende Feld*.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ca2f0-448">Übung 2</span><span class="sxs-lookup"><span data-stu-id="ca2f0-448">Exercise 2</span></span>

<span data-ttu-id="ca2f0-449">Schulen Sie Ihre Custom Vision Service, weitere Objekte zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="ca2f0-450">Übung 3</span><span class="sxs-lookup"><span data-stu-id="ca2f0-450">Exercise 3</span></span>

<span data-ttu-id="ca2f0-451">Wiedergeben Sie Sound, wenn ein Objekt erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="ca2f0-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="ca2f0-452">Übung 4</span><span class="sxs-lookup"><span data-stu-id="ca2f0-452">Exercise 4</span></span>

<span data-ttu-id="ca2f0-453">Verwenden Sie die API des Diensts mit der gleichen Images erneut zu trainieren Ihrer app analysiert, also um den Dienst mehr Genauigkeit zu gewährleisten (sowohl Vorhersagen und Trainieren gleichzeitig ausgeführt werden).</span><span class="sxs-lookup"><span data-stu-id="ca2f0-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
