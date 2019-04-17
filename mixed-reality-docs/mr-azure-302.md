---
title: MR und Azure-302 - maschinelles sehen
description: Führen Sie diesen Kurs Informationen zum visuellen Inhalten in einem bereitgestellten Image mithilfe von Azure-Computer Vision in einer mixed Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, maschinelles sehen, Hololens, immersive vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593381"
---
>[!NOTE]
><span data-ttu-id="b5149-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="b5149-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b5149-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b5149-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b5149-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b5149-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b5149-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="b5149-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b5149-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="b5149-110">MR und Azure 302: Maschinelles sehen</span><span class="sxs-lookup"><span data-stu-id="b5149-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="b5149-111">In diesem Kurs erfahren Sie wie zur Erkennung von visuellem Inhalt in einem bereitgestellten Image mithilfe von Azure-Computer Vision-Funktionen in einer mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b5149-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="b5149-112">Erkennungsergebnisse werden als beschreibende Tags angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="b5149-113">Sie können diesen Dienst verwenden, ohne, um ein Machine learning-Modell zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="b5149-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="b5149-114">Wenn Ihre Implementierung erfordert das Trainieren von Machine Learning-Modellen, finden Sie unter [MR und Azure 302b](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="b5149-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="b5149-116">Die Computer Vision von Microsoft ist ein Satz von APIs, die mithilfe von erweiterten Algorithmen, alles über die Cloud entwickelt, um Entwicklern bieten, bildverarbeitung und-Analyse (mit Informationen) zurück, an.</span><span class="sxs-lookup"><span data-stu-id="b5149-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="b5149-117">Entwickler hochzuladen, ein Bild oder die Bild-URL und die Algorithmen für maschinelles sehen-API von Microsoft Computer Analysieren des visuellen Inhalts, auf Grundlage von Eingaben, die ausgewählten Benutzers aus, klicken Sie dann Informationen zurückgegeben werden kann, einschließlich, identifizieren den Typ und die Qualität eines Bilds, menschliche Gesichter (erkennen Zurückgeben von ihren Koordinaten), und kennzeichnen und Kategorisieren von Bildern.</span><span class="sxs-lookup"><span data-stu-id="b5149-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="b5149-118">Weitere Informationen finden Sie auf die [Azure Computer Vision-API-Seite](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="b5149-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="b5149-119">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality HoloLens-Anwendung, die für die folgenden Aufgaben werden können</span><span class="sxs-lookup"><span data-stu-id="b5149-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="b5149-120">Verwenden die tippbewegung, wird die Kamera und die HoloLens ein Bild zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="b5149-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="b5149-121">Das Bild wird an der Azure-Computer Vision-API-Dienst gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="b5149-122">Die Objekte, die erkannt werden in einer einfachen Benutzeroberfläche-Gruppe, die in der Unity-Szene positioniert aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b5149-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="b5149-123">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="b5149-124">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="b5149-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="b5149-125">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="b5149-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="b5149-126">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="b5149-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b5149-127">Kurs</span><span class="sxs-lookup"><span data-stu-id="b5149-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b5149-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b5149-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b5149-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="b5149-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b5149-130">MR und Azure 302: Maschinelles sehen</span><span class="sxs-lookup"><span data-stu-id="b5149-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="b5149-131">✔️</span><span class="sxs-lookup"><span data-stu-id="b5149-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b5149-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b5149-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b5149-133">Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen.</span><span class="sxs-lookup"><span data-stu-id="b5149-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="b5149-134">Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden.</span><span class="sxs-lookup"><span data-stu-id="b5149-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="b5149-135">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="b5149-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5149-136">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b5149-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b5149-137">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="b5149-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b5149-138">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="b5149-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="b5149-139">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="b5149-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="b5149-140">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="b5149-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b5149-141">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="b5149-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b5149-142">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b5149-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b5149-143">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="b5149-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b5149-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b5149-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b5149-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b5149-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b5149-146">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b5149-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b5149-147">Eine Kamera, die Verbindung mit Ihrem PC (für immersive Kopfhörer Entwicklung)</span><span class="sxs-lookup"><span data-stu-id="b5149-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="b5149-148">Zugriff auf das Internet für die Einrichtung von Azure und Computer Vision-API abrufen</span><span class="sxs-lookup"><span data-stu-id="b5149-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b5149-149">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="b5149-149">Before you start</span></span>

1.  <span data-ttu-id="b5149-150">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="b5149-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b5149-151">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5149-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="b5149-152">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="b5149-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b5149-153">Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="b5149-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b5149-154">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="b5149-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="b5149-155">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="b5149-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="b5149-156">Kapitel 1 – Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="b5149-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="b5149-157">Verwenden der *Computer Vision-API* Service in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="b5149-158">Melden Sie sich zunächst auf die [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b5149-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="b5149-159">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="b5149-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b5149-160">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="b5149-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b5149-161">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Computer Vision-API*, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="b5149-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Erstellen Sie eine neue Ressource in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="b5149-163">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="b5149-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="b5149-164">Die neue Seite bietet eine Beschreibung der *Computer Vision-API* Service.</span><span class="sxs-lookup"><span data-stu-id="b5149-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="b5149-165">Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b5149-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Über das Computer Vision-API-Dienst](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="b5149-167">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="b5149-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="b5149-168">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="b5149-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="b5149-169">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="b5149-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="b5149-170">Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *Computer Vision-API* -Dienst ein freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="b5149-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="b5149-171">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="b5149-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b5149-172">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="b5149-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b5149-173">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="b5149-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="b5149-174">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="b5149-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="b5149-175">Bestimmen Sie den Speicherort für die Ressourcengruppe, (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="b5149-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b5149-176">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b5149-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b5149-177">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b5149-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="b5149-178">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="b5149-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="b5149-179">Klicken Sie auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="b5149-179">Click Create.</span></span>

        ![Erstellen von Dienstinformationen](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="b5149-181">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="b5149-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="b5149-182">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b5149-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Die neue Benachrichtigung für den neuen Dienst angezeigt.](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="b5149-184">Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="b5149-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Wählen Sie die Schaltfläche zu Ressource wechseln.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="b5149-186">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="b5149-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b5149-187">Sie werden für Ihre neue Computer Vision-API-Dienstinstanz weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="b5149-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Dem neuen Computer Vision-API-Dienst](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="b5149-189">In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, was durch die Verwendung von Subscription-Key Ihres Diensts erfolgt.</span><span class="sxs-lookup"><span data-stu-id="b5149-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="b5149-190">Von der *Schnellstart* Seite von Ihrer *Computer Vision-API* service, navigieren Sie zum ersten Schritt *nehmen Sie Ihre Schlüssel*, und klicken Sie auf **Schlüssel** ( auch erreichen dies Sie durch Klicken auf den blauen Link Schlüssel befindet sich im Navigationsmenü Dienste durch ein Schlüsselsymbol gekennzeichnet).</span><span class="sxs-lookup"><span data-stu-id="b5149-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="b5149-191">Dadurch wird angezeigt, den Dienst *Schlüssel*.</span><span class="sxs-lookup"><span data-stu-id="b5149-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="b5149-192">Erstellen Sie eine Kopie eines der angezeigten Schlüssel wird, da Sie dies später in Ihr Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="b5149-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="b5149-193">Wechseln Sie zurück zu den *Schnellstart* Seite, und von dort Abrufen Ihres Endpunkts.</span><span class="sxs-lookup"><span data-stu-id="b5149-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="b5149-194">Denken Sie möglicherweise Ihre unterschiedlich, abhängig von Ihrer Region (die, wenn es sich handelt, müssen Sie den Code später ändern).</span><span class="sxs-lookup"><span data-stu-id="b5149-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="b5149-195">Erstellen Sie eine Kopie dieses Endpunkts für die spätere Verwendung:</span><span class="sxs-lookup"><span data-stu-id="b5149-195">Take a copy of this endpoint for use later:</span></span>

    ![Dem neuen Computer Vision-API-Dienst](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="b5149-197">Sie können überprüfen, was die verschiedenen Endpunkte sind [hier](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="b5149-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="b5149-198">Kapitel 2: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="b5149-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="b5149-199">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="b5149-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b5149-200">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="b5149-200">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="b5149-202">Sie müssen nun einen Namen für die Unity-Projekt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b5149-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="b5149-203">Fügen Sie **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="b5149-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="b5149-204">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="b5149-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="b5149-205">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="b5149-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b5149-206">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="b5149-206">Then, click **Create project**.</span></span>

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="b5149-208">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5149-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b5149-209">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="b5149-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b5149-210">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="b5149-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b5149-211">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="b5149-211">Close the **Preferences** window.</span></span>

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="b5149-213">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="b5149-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="b5149-215">In der **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="b5149-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="b5149-216">**Geräte** nastaven NA hodnotu **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b5149-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="b5149-217">Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.</span><span class="sxs-lookup"><span data-stu-id="b5149-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="b5149-218">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="b5149-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="b5149-219">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="b5149-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="b5149-220">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="b5149-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="b5149-221">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="b5149-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="b5149-222">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="b5149-223">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b5149-224">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b5149-224">A save window will appear.</span></span>
        
            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="b5149-226">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="b5149-228">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_ComputerVisionScene**, klicken Sie dann auf **speichern** .</span><span class="sxs-lookup"><span data-stu-id="b5149-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="b5149-230">Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen.</span><span class="sxs-lookup"><span data-stu-id="b5149-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="b5149-231">Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.</span><span class="sxs-lookup"><span data-stu-id="b5149-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="b5149-232">Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="b5149-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="b5149-233">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="b5149-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="b5149-235">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="b5149-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="b5149-236">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="b5149-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="b5149-237">**Scripting Runtime Version** muss **stabile** (.NET 3.5 entspricht).</span><span class="sxs-lookup"><span data-stu-id="b5149-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="b5149-238">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="b5149-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="b5149-239">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="b5149-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="b5149-241">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="b5149-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b5149-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b5149-242">**InternetClient**</span></span>
        2. <span data-ttu-id="b5149-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="b5149-243">**Webcam**</span></span>

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="b5149-245">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="b5149-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="b5149-247">Im *Buildeinstellungen* _Unity C#_  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="b5149-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="b5149-248">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="b5149-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="b5149-249">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="b5149-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="b5149-250">Kapitel 3 – Main Camera-setup</span><span class="sxs-lookup"><span data-stu-id="b5149-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5149-251">Wenn Sie, überspringen möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importieren Sie es in Ihr Projekt als eine [benutzerdefinierten Paket ](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="b5149-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="b5149-252">In der *Hierarchie Bereich*, wählen die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="b5149-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="b5149-253">Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b5149-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="b5149-254">Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="b5149-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="b5149-255">Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="b5149-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="b5149-256">Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="b5149-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="b5149-257">Legen Sie **löschen Flags** zu **Volltonfarbe** (ignorieren Sie dies für immersive Kopfhörer).</span><span class="sxs-lookup"><span data-stu-id="b5149-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="b5149-258">Legen Sie die **Hintergrund** Farbe der Kamera-Komponente auf **Schwarz, Alpha 0 (Hex-Code: #00000000)** (ignorieren Sie dies für immersive Kopfhörer).</span><span class="sxs-lookup"><span data-stu-id="b5149-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Aktualisieren Sie die Kamera-Komponenten.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="b5149-260">Als Nächstes müssen Sie zum Erstellen eines einfachen "Cursor"-Objekts angefügt der **Main Camera**, dem gibt Hilfe, positionieren Sie die Image-Analyse bei die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b5149-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="b5149-261">Dieser Cursor bestimmt den Mittelpunkt der Kamera-Fokus.</span><span class="sxs-lookup"><span data-stu-id="b5149-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="b5149-262">So erstellen Sie den Cursor auf:</span><span class="sxs-lookup"><span data-stu-id="b5149-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="b5149-263">In der *Hierarchie Bereich*, mit der rechten Maustaste auf die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="b5149-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="b5149-264">Klicken Sie unter **3D-Objekt**, klicken Sie auf **Kugel**.</span><span class="sxs-lookup"><span data-stu-id="b5149-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Wählen Sie den Cursorobjekt.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="b5149-266">Benennen Sie die **Kugel** zu **Cursor** (das Cursorobjekt doppelklicken oder drücken Sie die Schaltfläche "F2"-Tastatur bei ausgewähltem Objekt), und stellen Sie sicher, dass es sich als untergeordnetes Element des der **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="b5149-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="b5149-267">In der *Hierarchie Bereich*, links, klicken Sie auf die **Cursor**.</span><span class="sxs-lookup"><span data-stu-id="b5149-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="b5149-268">Mit dem Cursor ausgewählt haben, passen Sie die folgenden Variablen in der *Inspektor Bereich*:</span><span class="sxs-lookup"><span data-stu-id="b5149-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="b5149-269">Legen Sie die *transformieren Position* zu **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="b5149-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="b5149-270">Legen Sie die *Skalierung* zu **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="b5149-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Aktualisieren Sie die Transformation positionieren und skalieren.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="b5149-272">Kapitel 4 – Setup das Label-system</span><span class="sxs-lookup"><span data-stu-id="b5149-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="b5149-273">Nachdem Sie ein Image mit dem HoloLens Kamera erfasst haben, wird dieses Bild an gesendet werden Ihre *maschinelles sehen-API von Azure-Computer* -Dienstinstanz für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="b5149-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="b5149-274">Die Ergebnisse dieser Analyse werden eine Liste der erkannten Objekte mit dem Namen **Tags**.</span><span class="sxs-lookup"><span data-stu-id="b5149-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="b5149-275">Sie werden Bezeichnungen (als eine 3D-Text im Raum) verwenden, zu diesen Tags an der Position, an dem das Foto aufgenommen wurde.</span><span class="sxs-lookup"><span data-stu-id="b5149-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="b5149-276">Die folgenden Schritte zeigen, wie Setup die **Bezeichnung** Objekt.</span><span class="sxs-lookup"><span data-stu-id="b5149-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="b5149-277">Mit der rechten Maustaste an einer beliebigen Stelle in der Hierarchie im Panel (die Position spielt keine Rolle an diesem Punkt) unter **3D-Objekt**, Hinzufügen einer **3D-Text**.</span><span class="sxs-lookup"><span data-stu-id="b5149-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="b5149-278">Nennen Sie sie **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="b5149-278">Name it **LabelText**.</span></span>

    ![Erstellen Sie 3D Text-Objekt.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="b5149-280">In der *Hierarchie Bereich*, links, klicken Sie auf die **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="b5149-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="b5149-281">Mit der **LabelText** ausgewählt haben, passen Sie die folgenden Variablen in der *Inspektor Bereich*:</span><span class="sxs-lookup"><span data-stu-id="b5149-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="b5149-282">Legen Sie die **Position** zu **0,0,0**</span><span class="sxs-lookup"><span data-stu-id="b5149-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="b5149-283">Legen Sie die **Skalierung** zu **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="b5149-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="b5149-284">In der Komponente **Text Mesh**:</span><span class="sxs-lookup"><span data-stu-id="b5149-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="b5149-285">Ersetzen Sie den Text in **Text**, mit "..."</span><span class="sxs-lookup"><span data-stu-id="b5149-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="b5149-286">Legen Sie die **Anker** zu **Mitte zentriert**</span><span class="sxs-lookup"><span data-stu-id="b5149-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="b5149-287">Legen Sie die **Ausrichtung** zu **Center**</span><span class="sxs-lookup"><span data-stu-id="b5149-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="b5149-288">Legen Sie die **Tabulatorgröße** zu **4**</span><span class="sxs-lookup"><span data-stu-id="b5149-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="b5149-289">Legen Sie die **Schriftgrad** zu **50**</span><span class="sxs-lookup"><span data-stu-id="b5149-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="b5149-290">Legen Sie die **Farbe** zu **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="b5149-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Textkomponente](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="b5149-292">Ziehen Sie die **LabelText-Element** aus der *Hierarchie Bereich*, in der *Ordner "Assets"* in in der *Projekt Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b5149-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="b5149-293">Dies veranlasst das **LabelText** eines Prefabs, damit die It in Code instanziiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b5149-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Erstellen eines prefabs des LabelText-Objekts.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="b5149-295">Löschen Sie die **LabelText** aus der *Hierarchie Bereich*, sodass sie in der Szene Öffnen nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b5149-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="b5149-296">Im aktuellen Zustand eines prefabs, die Sie auf für einzelne Instanzen aus Ihrem Ordner "Assets" aufgerufen werden, besteht keine Notwendigkeit, sie in der Szene zu halten.</span><span class="sxs-lookup"><span data-stu-id="b5149-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="b5149-297">Die Struktur der endgültige Objekt in der *Hierarchie Bereich* sollte wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="b5149-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Letzte Struktur der Hierarchie-Bereich.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="b5149-299">Kapitel 5 – Erstellen der ResultsLabel-Klasse</span><span class="sxs-lookup"><span data-stu-id="b5149-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="b5149-300">Ist das erste Skript, das Sie erstellen müssen die *ResultsLabel* -Klasse, die für Folgendes verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="b5149-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="b5149-301">Erstellen die Bezeichnungen in der entsprechenden Raum relativ zur Position der Kamera an.</span><span class="sxs-lookup"><span data-stu-id="b5149-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="b5149-302">Die Tags aus der Wegfall Bild wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b5149-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="b5149-303">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b5149-303">To create this class:</span></span> 

1.  <span data-ttu-id="b5149-304">Mit der rechten Maustaste den *Projekt Bereich*, klicken Sie dann **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="b5149-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="b5149-305">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="b5149-305">Name the folder **Scripts**.</span></span> 

    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="b5149-307">Mit der **Skripts** Ordner erstellen, öffnen sie das Doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="b5149-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="b5149-308">In diesem Ordner, die mit der rechten Maustaste und wählen Sie dann **erstellen >** dann  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="b5149-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="b5149-309">Nennen Sie das Skript *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="b5149-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="b5149-310">Doppelklicken Sie auf dem neuen *ResultsLabel* Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5149-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b5149-311">Fügen Sie in der Klasse den folgenden Code in die *ResultsLabel* Klasse:</span><span class="sxs-lookup"><span data-stu-id="b5149-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

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

6.  <span data-ttu-id="b5149-312">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5149-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="b5149-313">In der *Unity-Editor*, klicken Sie auf, und ziehen Sie die *ResultsLabel* -Klasse aus der **Skripts** Ordner, um die **Main Camera** Objekt in der  *Hierarchie-Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b5149-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="b5149-314">Klicken Sie auf die **Main Camera** und sehen Sie sich die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b5149-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="b5149-315">Sie werden feststellen, dass das Skript, das Sie gerade in die Kamera gezogen haben, zwei Felder stehen: **Cursor** und **Bezeichnung Prefab**.</span><span class="sxs-lookup"><span data-stu-id="b5149-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="b5149-316">Ziehen Sie das Objekt mit dem Namen **Cursor** aus der *Hierarchie Bereich* im Slot mit dem Namen **Cursor**, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b5149-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="b5149-317">Ziehen Sie das Objekt mit dem Namen **LabelText** aus der *Ordner "Assets"* in der *Projektfenster* im Slot mit dem Namen **Bezeichnung Prefab**, siehe die Die Abbildung unten.</span><span class="sxs-lookup"><span data-stu-id="b5149-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Legen Sie die Referenz-Ziele in Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="b5149-319">Kapitel 6: Erstellen der digitale Bilder-Klasse</span><span class="sxs-lookup"><span data-stu-id="b5149-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="b5149-320">Die nächste Klasse, die Sie erstellen wollen ist die *digitale Bilder* Klasse.</span><span class="sxs-lookup"><span data-stu-id="b5149-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="b5149-321">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="b5149-321">This class is responsible for:</span></span>

-   <span data-ttu-id="b5149-322">Erfassen ein Bild verwenden der Kamera HoloLens und in den App-Ordner speichern.</span><span class="sxs-lookup"><span data-stu-id="b5149-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="b5149-323">Erfassen von Tap-Gesten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="b5149-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="b5149-324">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b5149-324">To create this class:</span></span> 

1.  <span data-ttu-id="b5149-325">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="b5149-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="b5149-326">Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="b5149-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="b5149-327">Rufen Sie das Skript *digitale Bilder*.</span><span class="sxs-lookup"><span data-stu-id="b5149-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="b5149-328">Doppelklicken Sie auf dem neuen *digitale Bilder* Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5149-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="b5149-329">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="b5149-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="b5149-330">Klicken Sie dann fügen Sie die folgenden Variablen in der *digitale Bilder* Klasse, über die *Start()* Methode:</span><span class="sxs-lookup"><span data-stu-id="b5149-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="b5149-331">Die **TapsCount** Variable speichert die Anzahl der Tap-Aktionen, die vom Benutzer erfasst.</span><span class="sxs-lookup"><span data-stu-id="b5149-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="b5149-332">Diese Zahl wird verwendet, bei der Benennung der Images, die erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="b5149-333">Code für *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="b5149-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="b5149-334">Diese werden aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="b5149-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="b5149-335">Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Bewegung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="b5149-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

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
 
<span data-ttu-id="b5149-336">Die *TapHandler()* Methode inkrementiert die Anzahl der abtaststellen, die vom Benutzer erfasst und die aktuelle Cursorposition verwendet, zu bestimmen, wo eine neue Bezeichnung zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="b5149-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="b5149-337">Diese Methode ruft dann die *ExecuteImageCaptureAndAnalysis()* Methode damit beginnt, die Kernfunktionen der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b5149-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="b5149-338">Sobald ein Image erfasst und gespeichert wurde, werden die folgenden Handler aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="b5149-339">Wenn der Vorgang erfolgreich ist, wird das Ergebnis übergeben, um die *VisionManager* (was noch zu erstellen) für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="b5149-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

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
 
9.  <span data-ttu-id="b5149-340">Fügen Sie dann die Methode, die die Anwendung verwendet wird, starten den Prozess der abbilderfassung aus, und speichern Sie das Abbild hinzu.</span><span class="sxs-lookup"><span data-stu-id="b5149-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

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
> <span data-ttu-id="b5149-341">An diesem Punkt werden Sie feststellen, einen Fehler angezeigt werden, der *Unity-Editor-Konsole Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b5149-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="b5149-342">Dies ist, da der Code verweist auf die *VisionManager* Klasse, die im nächsten Kapitel erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="b5149-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="b5149-343">Kapitel 7 – Aufruf von Azure und Bildanalyse</span><span class="sxs-lookup"><span data-stu-id="b5149-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="b5149-344">Ist das letzte Skript Sie müssen die *VisionManager* Klasse.</span><span class="sxs-lookup"><span data-stu-id="b5149-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="b5149-345">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="b5149-345">This class is responsible for:</span></span>

-   <span data-ttu-id="b5149-346">Laden das neueste Image als ein Array von Bytes erfasst.</span><span class="sxs-lookup"><span data-stu-id="b5149-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="b5149-347">Senden das Bytearray, Ihre *maschinelles sehen-API von Azure-Computer* -Dienstinstanz für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="b5149-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="b5149-348">Empfangen der Antwort als JSON-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="b5149-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="b5149-349">Die Antwort zu deserialisieren, und übergeben die resultierende Tags auf der *ResultsLabel* Klasse.</span><span class="sxs-lookup"><span data-stu-id="b5149-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="b5149-350">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b5149-350">To create this class:</span></span>

1.  <span data-ttu-id="b5149-351">Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b5149-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b5149-352">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="b5149-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5149-353">Nennen Sie das Skript *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="b5149-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="b5149-354">Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b5149-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="b5149-355">Aktualisieren Sie die Namespaces, um Folgendes am Anfang entsprechen den *VisionManager* Klasse:</span><span class="sxs-lookup"><span data-stu-id="b5149-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="b5149-356">Am Anfang Ihres Skripts *in* der *VisionManager* Klasse (über die *Start()* Methode), müssen Sie nun zwei *Klassen* , Stellt die deserialisierte JSON-Antwort von Azure dar:</span><span class="sxs-lookup"><span data-stu-id="b5149-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

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
    > <span data-ttu-id="b5149-357">Die *"TagData"* und *AnalysedObject* Klassen haben, müssen die *[System.Serializable]* Attribut hinzugefügt werden, vor der Deklaration mit der Unity deserialisiert werden können -Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="b5149-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="b5149-358">In der Klasse VisionManager sollten Sie die folgenden Variablen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="b5149-358">In the VisionManager class, you should add the following variables:</span></span>

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
    > <span data-ttu-id="b5149-359">Stellen Sie sicher, Sie fügen Ihre **Authentication Key** in die **"authorizationkey"** Variable.</span><span class="sxs-lookup"><span data-stu-id="b5149-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="b5149-360">Sie haben angemerkt Ihre **Authentication Key** am Anfang dieses Kurses, [Kapitel 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="b5149-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="b5149-361">Die **VisionAnalysisEndpoint** Variable unterscheiden sich von dem in diesem Beispiel angegeben.</span><span class="sxs-lookup"><span data-stu-id="b5149-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="b5149-362">Die **West-USA** bezieht sich ausschließlich auf die Dienstinstanzen erstellt wurden, für die Region USA, Westen.</span><span class="sxs-lookup"><span data-stu-id="b5149-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="b5149-363">Aktualisieren Sie mit Ihrem [Endpunkt-URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); hier sind einige Beispiele, könnte folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="b5149-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="b5149-364">Europa, Westen: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="b5149-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="b5149-365">Asien, Südosten: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="b5149-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="b5149-366">Australien, Osten;: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="b5149-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="b5149-367">Code für Awake muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="b5149-368">Fügen Sie als Nächstes die Coroutine (mit der statischen Stream Methode darunter), die die Ergebnisse der Analyse des Bilds von erfasst zu erhalten, wird die *digitale Bilder* Klasse.</span><span class="sxs-lookup"><span data-stu-id="b5149-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

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

9.  <span data-ttu-id="b5149-369">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5149-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="b5149-370">Zurück im Unity-Editor, klicken Sie auf, und ziehen Sie die *VisionManager* und *digitale Bilder* Klassen aus der **Skripts** Ordner die **Main Camera**-Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="b5149-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="b5149-371">Kapitel 8 – vor dem Erstellen</span><span class="sxs-lookup"><span data-stu-id="b5149-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="b5149-372">Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.</span><span class="sxs-lookup"><span data-stu-id="b5149-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="b5149-373">Vor dem Ausführen, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="b5149-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="b5149-374">Alle Einstellungen, die im erwähnten [Kapitel 2](#chapter-2--set-up-the-unity-project) ordnungsgemäß festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="b5149-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="b5149-375">Alle Skripts werden angefügt, um die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="b5149-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="b5149-376">Alle Felder in der *Kamera Inspector-Hauptbereich* ordnungsgemäß zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="b5149-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="b5149-377">Stellen Sie sicher, Sie fügen Ihre **Authentication Key** in die **"authorizationkey"** Variable.</span><span class="sxs-lookup"><span data-stu-id="b5149-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="b5149-378">Stellen Sie sicher, dass Sie auch den Endpunkt, in aktiviert haben Ihre *VisionManager* Skript, und sie entspricht *Ihre* Region (in diesem Dokument wird *West-USA* standardmäßig).</span><span class="sxs-lookup"><span data-stu-id="b5149-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="b5149-379">Kapitel 9 – erstellen die UWP-Projektmappe, und Laden Sie die Anwendung</span><span class="sxs-lookup"><span data-stu-id="b5149-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="b5149-380">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.</span><span class="sxs-lookup"><span data-stu-id="b5149-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b5149-381">Navigieren Sie zu *Buildeinstellungen* - **Datei > Buildeinstellungen...**</span><span class="sxs-lookup"><span data-stu-id="b5149-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="b5149-382">Von der *Buildeinstellungen* Fenster, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Erstellen der app von Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="b5149-384">Falls noch nicht geschehen, aktivieren Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="b5149-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="b5149-385">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-385">Click **Build**.</span></span> <span data-ttu-id="b5149-386">Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="b5149-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b5149-387">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es *App*.</span><span class="sxs-lookup"><span data-stu-id="b5149-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="b5149-388">Klicken Sie dann mit der *App* Ordner ausgewählt haben, drücken Sie **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="b5149-389">Erstellen Ihres Projekts zu Unity beginnt die *App* Ordner.</span><span class="sxs-lookup"><span data-stu-id="b5149-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="b5149-390">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein *Datei-Explorer* Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="b5149-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="b5149-391">Kapitel 10 – bereitstellen, um HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5149-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="b5149-392">Für HoloLens bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="b5149-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="b5149-393">Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="b5149-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="b5149-394">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="b5149-394">To do this:</span></span>

    1. <span data-ttu-id="b5149-395">Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="b5149-396">Wechseln Sie zu **Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="b5149-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="b5149-397">Beachten Sie die **IPv4** Adresse.</span><span class="sxs-lookup"><span data-stu-id="b5149-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="b5149-398">Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit > für Entwickler**</span><span class="sxs-lookup"><span data-stu-id="b5149-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="b5149-399">Festlegen des Entwicklermodus auf.</span><span class="sxs-lookup"><span data-stu-id="b5149-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="b5149-400">Navigieren Sie zu Ihrem neuen Unity-Build (die *App* Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="b5149-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="b5149-401">In der Projektmappenkonfiguration Select **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="b5149-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="b5149-402">Wählen Sie in der Plattform für die Projektmappe **X86**, **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="b5149-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="b5149-404">Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen**, zum querladen der Anwendung in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5149-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="b5149-405">Ihre App sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b5149-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="b5149-406">Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**.</span><span class="sxs-lookup"><span data-stu-id="b5149-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="b5149-407">Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **Menü "Build"**, wählen *Projektmappe bereitstellen*.</span><span class="sxs-lookup"><span data-stu-id="b5149-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="b5149-408">Der fertigen Anwendung für die Computer Vision-API</span><span class="sxs-lookup"><span data-stu-id="b5149-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="b5149-409">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die nutzt das Computer Vision-API von Azure realen Objekte zu erkennen, und zeigen Gewissheit wie wir gesehen haben.</span><span class="sxs-lookup"><span data-stu-id="b5149-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b5149-411">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="b5149-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b5149-412">Übung 1</span><span class="sxs-lookup"><span data-stu-id="b5149-412">Exercise 1</span></span>

<span data-ttu-id="b5149-413">Wie Sie verwendet haben, der *Tags* Parameter (wie gezeigt in der *Endpunkt* innerhalb der *VisionManager*), erweitern Sie die app aus, um weitere Informationen zu ermitteln, sehen Sie sich Welche anderen Parameter haben Sie Zugriff auf [hier](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="b5149-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b5149-414">Übung 2</span><span class="sxs-lookup"><span data-stu-id="b5149-414">Exercise 2</span></span>

<span data-ttu-id="b5149-415">Anzuzeigen Sie die zurückgegebenen Azure Daten, auf eine Weise mehr conversational und besser lesbar, z. B. durch das Ausblenden der Zahlen.</span><span class="sxs-lookup"><span data-stu-id="b5149-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="b5149-416">Als ob ein Bot für den Benutzer sprechen kann.</span><span class="sxs-lookup"><span data-stu-id="b5149-416">As though a bot might be speaking to the user.</span></span>
