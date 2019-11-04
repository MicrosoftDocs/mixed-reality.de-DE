---
title: Mr und Azure 302-Maschinelles Sehen
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie visuelle Inhalte in einem bereitgestellten Image mithilfe von Azure Maschinelles sehen in einer Mixed Reality-Anwendung erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Maschinelles sehen, hololens, immersive, VR
ms.openlocfilehash: d6f792a67adfd1038ca4cdbc44b2ef1bf12a1173
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437942"
---
>[!NOTE]
><span data-ttu-id="1eefe-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1eefe-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="1eefe-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1eefe-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1eefe-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="1eefe-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1eefe-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1eefe-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="1eefe-110">Mr und Azure 302: Maschinelles Sehen</span><span class="sxs-lookup"><span data-stu-id="1eefe-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="1eefe-111">In diesem Kurs erfahren Sie, wie Sie visuelle Inhalte in einem bereitgestellten Image erkennen können, indem Sie die Funktionen von Azure Maschinelles sehen in einer Mixed Reality-Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="1eefe-112">Erkennungsergebnisse werden als beschreibende Tags angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="1eefe-113">Sie können diesen Dienst verwenden, ohne ein Machine Learning-Modell trainieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="1eefe-114">Wenn für Ihre Implementierung ein Machine Learning-Modell trainiert werden muss, finden Sie weitere Informationen unter [Mr und Azure 302b](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="1eefe-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="1eefe-116">Die Microsoft-Maschinelles sehen ist ein Satz von APIs, die Entwicklern die Bildverarbeitung und-Analyse (mit Rückgabe Informationen) zur Verfügung stellen, indem Sie erweiterte Algorithmen verwenden, die alle über die Cloud verfügen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="1eefe-117">Entwickler laden eine Bild-oder Bild-URL hoch, und die Microsoft Maschinelles Sehen-API-Algorithmen analysieren den visuellen Inhalt basierend auf den Eingaben, die der Benutzer ausgewählt hat. er kann dann Informationen zurückgeben, einschließlich, den Typ und die Qualität eines Bilds ermitteln und menschliche Gesichter erkennen. zurückgeben ihrer Koordinaten), Tagging oder Kategorisieren von Bildern.</span><span class="sxs-lookup"><span data-stu-id="1eefe-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="1eefe-118">Weitere Informationen finden Sie auf der [Seite Azure Maschinelles Sehen-API](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="1eefe-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="1eefe-119">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality hololens-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="1eefe-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="1eefe-120">Mithilfe der TAP-Geste wird ein Bild von der Kamera der hololens aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1eefe-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="1eefe-121">Das Image wird an den Azure Maschinelles Sehen-API-Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="1eefe-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="1eefe-122">Die erkannten Objekte werden in einer einfachen Benutzeroberflächen Gruppe aufgelistet, die in der Unity-Szene positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="1eefe-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="1eefe-123">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="1eefe-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1eefe-124">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="1eefe-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="1eefe-125">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="1eefe-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1eefe-126">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="1eefe-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1eefe-127">Natürlich</span><span class="sxs-lookup"><span data-stu-id="1eefe-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1eefe-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1eefe-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1eefe-129"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="1eefe-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1eefe-130">Mr und Azure 302: Maschinelles Sehen</span><span class="sxs-lookup"><span data-stu-id="1eefe-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="1eefe-131">✔️</span><span class="sxs-lookup"><span data-stu-id="1eefe-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1eefe-132">✔️</span><span class="sxs-lookup"><span data-stu-id="1eefe-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1eefe-133">Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets.</span><span class="sxs-lookup"><span data-stu-id="1eefe-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="1eefe-134">Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="1eefe-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="1eefe-135">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1eefe-136">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1eefe-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1eefe-137">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1eefe-138">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="1eefe-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="1eefe-139">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="1eefe-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="1eefe-140">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="1eefe-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1eefe-141">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="1eefe-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1eefe-142">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="1eefe-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1eefe-143">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1eefe-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1eefe-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="1eefe-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1eefe-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1eefe-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1eefe-146">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="1eefe-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1eefe-147">Eine Kamera, die mit Ihrem PC verbunden ist (für die immersive Headset-Entwicklung)</span><span class="sxs-lookup"><span data-stu-id="1eefe-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="1eefe-148">Internet Zugriff für Azure-Setup und Maschinelles Sehen-API-Abruf</span><span class="sxs-lookup"><span data-stu-id="1eefe-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1eefe-149">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="1eefe-149">Before you start</span></span>

1.  <span data-ttu-id="1eefe-150">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="1eefe-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1eefe-151">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="1eefe-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="1eefe-152">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="1eefe-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1eefe-153">Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="1eefe-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1eefe-154">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="1eefe-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="1eefe-155">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="1eefe-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="1eefe-156">Kapitel 1 – Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="1eefe-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="1eefe-157">Wenn Sie den *Maschinelles Sehen-API* -Dienst in Azure verwenden möchten, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="1eefe-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="1eefe-158">Melden Sie sich zunächst beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="1eefe-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="1eefe-159">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1eefe-160">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1eefe-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1eefe-161">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Maschinelles Sehen-API*, und drücken Sie die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="1eefe-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Erstellen einer neuen Ressource in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="1eefe-163">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="1eefe-164">Auf der neuen Seite wird eine Beschreibung des *Maschinelles Sehen-API* Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="1eefe-165">Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Informationen zum Maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="1eefe-167">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="1eefe-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="1eefe-168">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="1eefe-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="1eefe-169">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="1eefe-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="1eefe-170">Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen *Maschinelles Sehen-API* Dienst erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="1eefe-171">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="1eefe-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1eefe-172">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1eefe-173">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="1eefe-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="1eefe-174">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="1eefe-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="1eefe-175">Bestimmen Sie den Speicherort für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="1eefe-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1eefe-176">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1eefe-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1eefe-177">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1eefe-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="1eefe-178">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="1eefe-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="1eefe-179">Klicken Sie auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-179">Click Create.</span></span>

        ![Informationen zur Dienst Erstellung](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="1eefe-181">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="1eefe-182">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Anzeigen der neuen Benachrichtigung für den neuen Dienst](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="1eefe-184">Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Wählen Sie die Schaltfläche Gehe zu Ressource aus.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="1eefe-186">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1eefe-187">Sie gelangen zu ihrer neuen Maschinelles Sehen-API Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="1eefe-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Ihre neue Maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="1eefe-189">In diesem Lernprogramm muss Ihre Anwendung Aufrufe an Ihren Dienst durchführen. Dies erfolgt über den Abonnement Schlüssel Ihres dienstanzschlüssels.</span><span class="sxs-lookup"><span data-stu-id="1eefe-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="1eefe-190">Navigieren Sie auf der Seite " *Schnellstart* " Ihres *Maschinelles Sehen-API* Diensts zum ersten Schritt, rufen Sie *Ihre Schlüssel*ab, und klicken Sie auf " **Schlüssel** " (Sie können dies auch erreichen, indem Sie auf die blauen Hyperlink-Schlüssel im Navigationsmenü "Dienste" klicken. gekennzeichnet durch das Schlüsselsymbol).</span><span class="sxs-lookup"><span data-stu-id="1eefe-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="1eefe-191">Dadurch werden die Dienst *Schlüssel*angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="1eefe-192">Erstellen Sie eine Kopie von einem der angezeigten Schlüssel, da Sie dies später in Ihrem Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="1eefe-193">Wechseln Sie zurück zur Seite *Schnellstart* , und rufen Sie den Endpunkt ab.</span><span class="sxs-lookup"><span data-stu-id="1eefe-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="1eefe-194">Beachten Sie, dass Sie je nach Region unterschiedlich sein können (wenn dies der Fall ist, müssen Sie später eine Änderung an Ihrem Code vornehmen).</span><span class="sxs-lookup"><span data-stu-id="1eefe-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="1eefe-195">Erstellen Sie für die spätere Verwendung eine Kopie dieses Endpunkts:</span><span class="sxs-lookup"><span data-stu-id="1eefe-195">Take a copy of this endpoint for use later:</span></span>

    ![Ihre neue Maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="1eefe-197">Sie können überprüfen, [worum es sich](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)bei den verschiedenen Endpunkten handelt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="1eefe-198">Kapitel 2 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="1eefe-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="1eefe-199">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="1eefe-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1eefe-200">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-200">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="1eefe-202">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="1eefe-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="1eefe-203">Fügen Sie **MR_ComputerVision**ein.</span><span class="sxs-lookup"><span data-stu-id="1eefe-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="1eefe-204">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1eefe-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1eefe-205">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="1eefe-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1eefe-206">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-206">Then, click **Create project**.</span></span>

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="1eefe-208">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1eefe-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1eefe-209">Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1eefe-210">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1eefe-211">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="1eefe-211">Close the **Preferences** window.</span></span>

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="1eefe-213">Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen</span><span class="sxs-lookup"><span data-stu-id="1eefe-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="1eefe-215">In **Datei > Buildeinstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="1eefe-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="1eefe-216">**Zielgerät** ist auf **hololens** festgelegt</span><span class="sxs-lookup"><span data-stu-id="1eefe-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="1eefe-217">Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="1eefe-218">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="1eefe-219">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="1eefe-220">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="1eefe-221">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="1eefe-222">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="1eefe-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="1eefe-223">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="1eefe-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1eefe-224">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-224">A save window will appear.</span></span>
        
            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="1eefe-226">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="1eefe-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="1eefe-228">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_ComputerVisionScene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="1eefe-230">Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="1eefe-231">Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="1eefe-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="1eefe-232">Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="1eefe-233">Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="1eefe-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="1eefe-235">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="1eefe-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="1eefe-236">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="1eefe-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="1eefe-237">Die **Lauf Zeit Version der Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="1eefe-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="1eefe-238">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="1eefe-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="1eefe-239">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="1eefe-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="1eefe-241">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="1eefe-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="1eefe-242">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="1eefe-242">**InternetClient**</span></span>
        2. <span data-ttu-id="1eefe-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="1eefe-243">**Webcam**</span></span>

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="1eefe-245">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="1eefe-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="1eefe-247">Zurück in *Buildeinstellungen* : _Unity C#_  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="1eefe-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="1eefe-248">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="1eefe-249">Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).</span><span class="sxs-lookup"><span data-stu-id="1eefe-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="1eefe-250">Kapitel 3 – Hauptkamera Einrichtung</span><span class="sxs-lookup"><span data-stu-id="1eefe-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1eefe-251">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)herunterladen, es als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5](#chapter-5--create-the-resultslabel-class)fortfahren.</span><span class="sxs-lookup"><span data-stu-id="1eefe-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="1eefe-252">Wählen Sie im Bereich *Hierarchie*die **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="1eefe-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="1eefe-253">Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor-Panel*sehen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="1eefe-254">Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="1eefe-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="1eefe-255">Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="1eefe-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="1eefe-256">Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1eefe-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="1eefe-257">Legen Sie **klar Flags** auf voll **Tonfarbe** fest (diese Einstellung wird für immersives Headset ignoriert).</span><span class="sxs-lookup"><span data-stu-id="1eefe-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="1eefe-258">Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest (Dies wird für das immersive Headset ignoriert).</span><span class="sxs-lookup"><span data-stu-id="1eefe-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Aktualisieren Sie die Kamerakomponenten.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="1eefe-260">Als nächstes müssen Sie ein einfaches "Cursor"-Objekt erstellen, das an die **Hauptkamera**angeschlossen ist. Dadurch können Sie die Ausgabe der Bildanalyse beim Ausführen der Anwendung positionieren.</span><span class="sxs-lookup"><span data-stu-id="1eefe-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="1eefe-261">Mit diesem Cursor wird der Mittelpunkt des Kamerafokus bestimmt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="1eefe-262">So erstellen Sie den Cursor:</span><span class="sxs-lookup"><span data-stu-id="1eefe-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="1eefe-263">Klicken Sie im *Hierarchie Panel*mit der rechten Maustaste auf die **Hauptkamera**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="1eefe-264">Klicken Sie unter **3D-Objekt**auf **Kugel**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Wählen Sie das Cursor Objekt aus.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="1eefe-266">Benennen Sie die **Kugel** in den **Cursor** um (Doppelklicken Sie auf das Cursor Objekt, oder drücken Sie die Tastenkombination "F2", wenn das Objekt ausgewählt ist), und stellen Sie sicher, dass Sie sich als untergeordnetes Element der **Hauptkamera**befindet</span><span class="sxs-lookup"><span data-stu-id="1eefe-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="1eefe-267">Klicken Sie im *Hierarchie Panel*mit der linken Maustaste auf den **Cursor**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="1eefe-268">Wenn der Cursor ausgewählt ist, passen Sie die folgenden Variablen im *Inspektor-Panel*an:</span><span class="sxs-lookup"><span data-stu-id="1eefe-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="1eefe-269">Legen Sie die *Transformations Position* auf **0, 0, 5** fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="1eefe-270">Legen Sie die *Skala* auf **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="1eefe-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Aktualisieren der Transformations Position und-Skalierung.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="1eefe-272">Kapitel 4 – Einrichten des Bezeichnungs Systems</span><span class="sxs-lookup"><span data-stu-id="1eefe-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="1eefe-273">Nachdem Sie ein Bild mit der Kamera hololens erfasst haben, wird dieses Abbild zur Analyse an Ihre *Azure Maschinelles Sehen-API* -Dienst Instanz gesendet.</span><span class="sxs-lookup"><span data-stu-id="1eefe-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="1eefe-274">Die Ergebnisse dieser Analyse stellen eine Liste bekannter Objekte dar, die als **Tags**bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="1eefe-275">Sie verwenden Bezeichnungen (als 3D-Text im Raum), um diese Tags an der Stelle anzuzeigen, an der das Foto entnommen wurde.</span><span class="sxs-lookup"><span data-stu-id="1eefe-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="1eefe-276">In den folgenden Schritten wird gezeigt, wie Sie das **Label** -Objekt einrichten.</span><span class="sxs-lookup"><span data-stu-id="1eefe-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="1eefe-277">Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hierarchie Panel (der Standort ist an diesem Punkt nicht wichtig), und fügen Sie unter **3D-Objekt**einen **3D-Text**hinzu.</span><span class="sxs-lookup"><span data-stu-id="1eefe-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="1eefe-278">Nennen Sie es **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-278">Name it **LabelText**.</span></span>

    ![3D-Text Objekt erstellen.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="1eefe-280">Klicken Sie im *Hierarchie Panel*mit der linken Maustaste auf das **LabelText**-Element.</span><span class="sxs-lookup"><span data-stu-id="1eefe-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="1eefe-281">Passen Sie bei ausgewähltem **LabelText** die folgenden Variablen im *Inspektor-Panel*an:</span><span class="sxs-lookup"><span data-stu-id="1eefe-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="1eefe-282">Legen Sie die **Position** auf **0, 0, 0** fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="1eefe-283">Legen Sie die **Skala** auf **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="1eefe-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="1eefe-284">Im **textmesh**der Komponente:</span><span class="sxs-lookup"><span data-stu-id="1eefe-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="1eefe-285">Ersetzen Sie den gesamten Text im **Text**durch "..."</span><span class="sxs-lookup"><span data-stu-id="1eefe-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="1eefe-286">Legen Sie den **Anker** auf das **mittlere Zentrum** fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="1eefe-287">Festlegen der **Ausrichtung** auf **zentrieren**</span><span class="sxs-lookup"><span data-stu-id="1eefe-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="1eefe-288">Legen Sie die **Tabstopp Größe** auf **4** fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="1eefe-289">Legen Sie den **Schrift** Grad auf **50** fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="1eefe-290">Legen Sie die **Farbe** auf **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="1eefe-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Text Komponente](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="1eefe-292">Ziehen Sie den **LabelText** aus dem Bereich *Hierarchie*in den *Ordner Asset*innerhalb des *Projekt Panels*.</span><span class="sxs-lookup"><span data-stu-id="1eefe-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="1eefe-293">Dadurch wird der **LabelText** zu einem präfab, damit er im Code instanziiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1eefe-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Erstellen Sie eine vorfab des LabelText-Objekts.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="1eefe-295">Sie sollten das **LabelText** -Element aus dem *Hierarchie Panel*löschen, damit es nicht in der öffnenden Szene angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1eefe-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="1eefe-296">Da es sich nun um eine vorfab handelt, die Sie für einzelne Instanzen aus dem Ordner "Assets" abrufen, ist es nicht erforderlich, Sie in der Szene zu behalten.</span><span class="sxs-lookup"><span data-stu-id="1eefe-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="1eefe-297">Die endgültige Objektstruktur im *Hierarchie Panel* sollte wie die in der folgenden Abbildung gezeigt aussehen:</span><span class="sxs-lookup"><span data-stu-id="1eefe-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Endgültige Struktur des Hierarchie Bereichs.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="1eefe-299">Kapitel 5 – Erstellen der resultorlabel-Klasse</span><span class="sxs-lookup"><span data-stu-id="1eefe-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="1eefe-300">Das erste Skript, das Sie erstellen müssen, ist die Klasse " *resulttlabel* ", die für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="1eefe-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="1eefe-301">Erstellen der Bezeichnungen im entsprechenden Raum, relativ zur Position der Kamera.</span><span class="sxs-lookup"><span data-stu-id="1eefe-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="1eefe-302">Anzeigen der Tags aus der Bild anaysis</span><span class="sxs-lookup"><span data-stu-id="1eefe-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="1eefe-303">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="1eefe-303">To create this class:</span></span> 

1.  <span data-ttu-id="1eefe-304">Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und erstellen Sie dann **> Ordner**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="1eefe-305">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-305">Name the folder **Scripts**.</span></span> 

    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="1eefe-307">Wenn Sie den Ordner **Skripts** erstellen, doppelklicken Sie darauf, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="1eefe-308">Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und wählen **C#** Sie dann **> Skript erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="1eefe-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="1eefe-309">Nennen Sie das Skript " *ResultLabel*".</span><span class="sxs-lookup"><span data-stu-id="1eefe-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="1eefe-310">Doppelklicken Sie auf das neue *resulttlabel* -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="1eefe-311">Fügen Sie in der-Klasse den folgenden Code in die *resultorlabel* -Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="1eefe-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="1eefe-312">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="1eefe-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="1eefe-313">Klicken Sie im *Unity-Editor*auf die *resultslabel* -Klasse, und ziehen Sie Sie aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="1eefe-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="1eefe-314">Klicken Sie auf die **Hauptkamera** , und sehen Sie sich den Bereich *Inspector*an.</span><span class="sxs-lookup"><span data-stu-id="1eefe-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="1eefe-315">Sie werden feststellen, dass Sie aus dem Skript, das Sie soeben in die Kamera gezogen haben, zwei Felder haben: **Cursor** -und Bezeichnungs **präfab**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="1eefe-316">Ziehen Sie das Objekt **Cursor** aus dem Bereich *Hierarchie* in den Slot mit dem Namen **Cursor**, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="1eefe-317">Ziehen Sie das Objekt " **LabelText** " aus dem *Ordner "Assets* " im *Projekt Panel* in den Slot mit dem Namen " **Label Prefab**", wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Legen Sie die Verweis Ziele innerhalb von Unity fest.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="1eefe-319">Kapitel 6 – Erstellen der imagecapture-Klasse</span><span class="sxs-lookup"><span data-stu-id="1eefe-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="1eefe-320">Die nächste Klasse, die Sie erstellen, ist die *imagecapture* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="1eefe-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="1eefe-321">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="1eefe-321">This class is responsible for:</span></span>

-   <span data-ttu-id="1eefe-322">Erfassen eines Bilds mithilfe der hololens-Kamera und speichern im App-Ordner.</span><span class="sxs-lookup"><span data-stu-id="1eefe-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="1eefe-323">Das Erfassen von TAP-Gesten vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="1eefe-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="1eefe-324">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="1eefe-324">To create this class:</span></span> 

1.  <span data-ttu-id="1eefe-325">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="1eefe-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="1eefe-326">Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen Sie > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="1eefe-327">Nennen Sie das Skript *imagecapture*.</span><span class="sxs-lookup"><span data-stu-id="1eefe-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="1eefe-328">Doppelklicken Sie auf das neue *imagecapture* -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="1eefe-329">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="1eefe-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="1eefe-330">Fügen Sie dann die folgenden Variablen in der *imagecapture* -Klasse oberhalb der *Start ()* -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="1eefe-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="1eefe-331">Die Variable **tapscount** speichert die Anzahl der vom Benutzer erfassten Tap-Gesten.</span><span class="sxs-lookup"><span data-stu-id="1eefe-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="1eefe-332">Diese Zahl wird bei der Benennung der aufgezeichneten Bilder verwendet.</span><span class="sxs-lookup"><span data-stu-id="1eefe-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="1eefe-333">Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="1eefe-334">Diese werden aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="1eefe-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="1eefe-335">Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Geste auftritt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="1eefe-336">Die *taphandler ()* -Methode erhöht die Anzahl der vom Benutzer erfassten Abzweigungen und verwendet die aktuelle Cursor Position, um zu bestimmen, wo eine neue Bezeichnung positioniert werden soll.</span><span class="sxs-lookup"><span data-stu-id="1eefe-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="1eefe-337">Diese Methode ruft dann die *executeimagecaptureandanalysis ()* -Methode auf, um die Kernfunktionen dieser Anwendung zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="1eefe-338">Nachdem ein Bild aufgezeichnet und gespeichert wurde, werden die folgenden Handler aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="1eefe-339">Wenn der Prozess erfolgreich ist, wird das Ergebnis an den *visionmanager* (den Sie noch erstellen) für die Analyse übermittelt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="1eefe-340">Fügen Sie dann die-Methode hinzu, die die Anwendung verwendet, um den Bild Aufzeichnungsprozess zu starten und das Abbild zu speichern.</span><span class="sxs-lookup"><span data-stu-id="1eefe-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="1eefe-341">An dieser Stelle bemerken Sie einen Fehler, der im *Konsolen Panel des Unity-Editors*angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1eefe-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="1eefe-342">Dies liegt daran, dass der Code auf die Klasse " *visionmanager* " verweist, die Sie im nächsten Kapitel erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="1eefe-343">Kapitel 7 – Aufrufe von Azure und Image Analyse</span><span class="sxs-lookup"><span data-stu-id="1eefe-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="1eefe-344">Das letzte Skript, das Sie erstellen müssen, ist die Klasse " *visionmanager* ".</span><span class="sxs-lookup"><span data-stu-id="1eefe-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="1eefe-345">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="1eefe-345">This class is responsible for:</span></span>

-   <span data-ttu-id="1eefe-346">Das letzte als Bytearray erfasste Bild wird geladen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="1eefe-347">Das Bytearray wird zur Analyse an Ihre *Azure Maschinelles Sehen-API* -Dienst Instanz gesendet.</span><span class="sxs-lookup"><span data-stu-id="1eefe-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="1eefe-348">Die Antwort wird als JSON-Zeichenfolge empfangen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="1eefe-349">Deserialisieren der Antwort und übergeben der resultierenden Tags an die *ResultLabel* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="1eefe-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="1eefe-350">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="1eefe-350">To create this class:</span></span>

1.  <span data-ttu-id="1eefe-351">Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1eefe-352">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1eefe-353">Nennen Sie das Skript " *visionmanager*".</span><span class="sxs-lookup"><span data-stu-id="1eefe-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="1eefe-354">Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1eefe-355">Aktualisieren Sie die Namespaces so, dass Sie am Anfang der Klasse " *visionmanager* " wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="1eefe-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="1eefe-356">Am Anfang des Skripts in der Klasse " *visionmanager* " (oberhalb der Methode " *Start ()* ") müssen Sie nun zwei *Klassen* *erstellen, die* die deserialisierte JSON-Antwort von Azure darstellen:</span><span class="sxs-lookup"><span data-stu-id="1eefe-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="1eefe-357">Der " *TagData* "-Klasse und der *analysedobject* -Klasse muss das *[System. serialisierbare]* -Attribut vor der Deklaration hinzugefügt werden, damit Sie mit den Unity-Bibliotheken deserialisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1eefe-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="1eefe-358">Fügen Sie in der Klasse "visionmanager" die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="1eefe-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="1eefe-359">Stellen Sie sicher, dass Sie den Authentifizierungs **Schlüssel** in die **authorizationkey** -Variable einfügen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="1eefe-360">Sie haben den Authentifizierungs **Schlüssel** zu Beginn dieses Kurses notiert, [Kapitel 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="1eefe-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="1eefe-361">Die " **visionanalysisendpoint** "-Variable kann sich von der in diesem Beispiel angegebenen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="1eefe-362">**USA, Westen** bezieht sich strikt auf Dienst Instanzen, die für die Region "USA, Westen" erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="1eefe-363">Aktualisieren Sie dies mit der [Endpunkt-URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). Im folgenden finden Sie einige Beispiele dafür, wie Sie aussehen können:</span><span class="sxs-lookup"><span data-stu-id="1eefe-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="1eefe-364">Europa, Westen: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="1eefe-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="1eefe-365">Südostasien: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="1eefe-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="1eefe-366">Australien, Osten: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="1eefe-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="1eefe-367">Der Code für "awado" muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="1eefe-368">Fügen Sie als nächstes die Coroutine (mit der statischen streammethode darunter) hinzu, die die Ergebnisse der Analyse des Bilds erhält, das von der *imagecapture* -Klasse erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="1eefe-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="1eefe-369">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="1eefe-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="1eefe-370">Klicken Sie im Unity-Editor auf die Klassen " *visionmanager* " und " *imagecapture* ", und ziehen Sie Sie aus dem Ordner " **Scripts** " in das **Hauptkamera** Objekt im *Hierarchie Panel*.</span><span class="sxs-lookup"><span data-stu-id="1eefe-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="1eefe-371">Kapitel 8 – vor dem Aufbau</span><span class="sxs-lookup"><span data-stu-id="1eefe-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="1eefe-372">Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="1eefe-373">Bevor Sie vorgehen, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="1eefe-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="1eefe-374">Alle in [Kapitel 2](#chapter-2--set-up-the-unity-project) erwähnten Einstellungen sind richtig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="1eefe-375">Alle Skripts werden an das **Hauptkamera** Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="1eefe-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="1eefe-376">Alle Felder im Hauptbereich der *Kamera Inspektor* sind ordnungsgemäß zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="1eefe-377">Stellen Sie sicher, dass Sie den Authentifizierungs **Schlüssel** in die **authorizationkey** -Variable einfügen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="1eefe-378">Stellen Sie sicher, dass Sie auch ihren Endpunkt in Ihrem " *visionmanager* "-Skript geprüft haben und dass es sich an *ihrer* Region anpasst (standardmäßig verwendet dieses Dokument " *USA, Westen* ").</span><span class="sxs-lookup"><span data-stu-id="1eefe-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="1eefe-379">Kapitel 9 – Erstellen der UWP-Lösung und querladen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="1eefe-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="1eefe-380">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1eefe-381">Navigieren Sie zu *Buildeinstellungen* - **Datei > Buildeinstellungen...**</span><span class="sxs-lookup"><span data-stu-id="1eefe-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="1eefe-382">Klicken Sie im Fenster " *Buildeinstellungen* " auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="1eefe-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Entwickeln der APP aus Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="1eefe-384">Wenn dies nicht bereits geschehen ist, Tick **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="1eefe-385">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-385">Click **Build**.</span></span> <span data-ttu-id="1eefe-386">Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="1eefe-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1eefe-387">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " *App*".</span><span class="sxs-lookup"><span data-stu-id="1eefe-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="1eefe-388">Klicken Sie dann mit ausgewähltem *App* -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="1eefe-389">Unity startet das Projekt in den *App* -Ordner.</span><span class="sxs-lookup"><span data-stu-id="1eefe-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="1eefe-390">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein *Datei-Explorer* -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="1eefe-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="1eefe-391">Kapitel 10 – bereitstellen in hololens</span><span class="sxs-lookup"><span data-stu-id="1eefe-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="1eefe-392">So stellen Sie auf hololens bereit:</span><span class="sxs-lookup"><span data-stu-id="1eefe-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="1eefe-393">Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="1eefe-394">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="1eefe-394">To do this:</span></span>

    1. <span data-ttu-id="1eefe-395">Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="1eefe-396">Navigieren Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="1eefe-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="1eefe-397">Notieren Sie sich die **IPv4** -Adresse.</span><span class="sxs-lookup"><span data-stu-id="1eefe-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="1eefe-398">Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie dann **& Sicherheits > für Entwickler** .</span><span class="sxs-lookup"><span data-stu-id="1eefe-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="1eefe-399">Legen Sie den Entwicklermodus auf fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="1eefe-400">Navigieren Sie zu Ihrem neuen Unity-Build ( *App* -Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="1eefe-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="1eefe-401">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="1eefe-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="1eefe-402">Wählen Sie auf der Projektmappenplattform die Option **x86**, **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="1eefe-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="1eefe-404">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung**bereitstellen, um die Anwendung auf die hololens quer zuladen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="1eefe-405">Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.</span><span class="sxs-lookup"><span data-stu-id="1eefe-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="1eefe-406">Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest.</span><span class="sxs-lookup"><span data-stu-id="1eefe-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="1eefe-407">Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen**die Option *Lösung*bereitstellen auswählen.</span><span class="sxs-lookup"><span data-stu-id="1eefe-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="1eefe-408">Ihre fertiggestellte Maschinelles Sehen-API Anwendung</span><span class="sxs-lookup"><span data-stu-id="1eefe-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="1eefe-409">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Azure-Maschinelles Sehen-API nutzt, um reale Objekte zu erkennen, und zeigen Ihnen das Vertrauen an, was Sie gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="1eefe-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1eefe-411">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="1eefe-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1eefe-412">Übung 1</span><span class="sxs-lookup"><span data-stu-id="1eefe-412">Exercise 1</span></span>

<span data-ttu-id="1eefe-413">Ebenso wie Sie den Parameter " *Tags* " (wie in dem *Endpunkt* , der innerhalb von " *visionmanager*" verwendet wird) verwendet haben, erweitern Sie die APP, um weitere Informationen zu erkennen. Werfen Sie einen Blick auf die anderen Parameter, auf die Sie [hier](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="1eefe-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1eefe-414">Übung 2</span><span class="sxs-lookup"><span data-stu-id="1eefe-414">Exercise 2</span></span>

<span data-ttu-id="1eefe-415">Zeigen Sie die zurückgegebenen Azure-Daten in einer besser lesbaren und lesbaren Weise an, und verbergen Sie die Zahlen vielleicht.</span><span class="sxs-lookup"><span data-stu-id="1eefe-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="1eefe-416">So, als ob ein bot für den Benutzer sprechen könnte.</span><span class="sxs-lookup"><span data-stu-id="1eefe-416">As though a bot might be speaking to the user.</span></span>
