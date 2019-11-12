---
title: Mr und Azure 303-Natural Language Understanding (Luis)
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Language Understanding Intelligence Service (Luis) in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Language Understanding Intelligence Service, Luis, hololens, immersive, VR
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926806"
---
>[!NOTE]
><span data-ttu-id="ec15f-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ec15f-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ec15f-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ec15f-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="ec15f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ec15f-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ec15f-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="ec15f-110">Mr und Azure 303: verstehen in natürlicher Sprache (Luis)</span><span class="sxs-lookup"><span data-stu-id="ec15f-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="ec15f-111">In diesem Kurs erfahren Sie, wie Sie Language Understanding mithilfe von Azure Cognitive Services mit dem Language Understanding-API in eine gemischte Reality-Anwendung integrieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="ec15f-113">Bei *Language Understanding (Luis)* handelt es sich um einen Microsoft Azure Dienst, der Anwendungen die Möglichkeit bietet, die Bedeutung von Benutzereingaben zu machen, z. b. durch das Extrahieren der gewünschten Person in ihren eigenen Worten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="ec15f-114">Dies wird durch Machine Learning erreicht, das die Eingabeinformationen versteht und erfährt und dann mit detaillierten, relevanten Informationen Antworten kann.</span><span class="sxs-lookup"><span data-stu-id="ec15f-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="ec15f-115">Weitere Informationen finden Sie auf der [Seite Azure Language Understanding (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="ec15f-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="ec15f-116">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="ec15f-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="ec15f-117">Erfassen Sie die Sprache für Benutzereingaben, indem Sie das Mikrofon verwenden, das dem immersiven Headset zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="ec15f-118">Senden Sie das erfasste Diktat an den *Azure-Language Understanding Intelligent Service* (*Luis*).</span><span class="sxs-lookup"><span data-stu-id="ec15f-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="ec15f-119">Achten Sie darauf, dass Luis aus den Sende Informationen Bedeutung hat, die analysiert werden, und versuchen Sie zu bestimmen, ob die Anforderung des Benutzers hergestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ec15f-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="ec15f-120">Die Entwicklung umfasst das Erstellen einer APP, in der der Benutzer die Sprach-und/oder den Blick verwenden kann, um die Größe und die Farbe der Objekte in der Szene zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ec15f-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="ec15f-121">Die Verwendung von Bewegungs Controllern wird nicht abgedeckt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="ec15f-122">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ec15f-123">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ec15f-124">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="ec15f-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="ec15f-125">Seien Sie darauf vorbereitet, Luis mehrmals zu trainieren. Dies wird in [Kapitel 12](#chapter-12--improving-your-luis-service)behandelt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="ec15f-126">Wenn Luis schneller trainiert wurde, erhalten Sie bessere Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="ec15f-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="ec15f-127">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="ec15f-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ec15f-128">Natürlich</span><span class="sxs-lookup"><span data-stu-id="ec15f-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ec15f-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ec15f-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ec15f-130"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="ec15f-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="ec15f-131">Mr und Azure 303: verstehen in natürlicher Sprache (Luis)</span><span class="sxs-lookup"><span data-stu-id="ec15f-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="ec15f-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ec15f-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ec15f-133">✔️</span><span class="sxs-lookup"><span data-stu-id="ec15f-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ec15f-134">Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ec15f-135">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ec15f-136">Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.</span><span class="sxs-lookup"><span data-stu-id="ec15f-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec15f-137">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ec15f-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ec15f-138">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ec15f-139">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="ec15f-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ec15f-140">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="ec15f-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ec15f-141">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="ec15f-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ec15f-142">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="ec15f-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ec15f-143">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="ec15f-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="ec15f-144">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ec15f-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="ec15f-145">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="ec15f-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="ec15f-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ec15f-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="ec15f-147">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="ec15f-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ec15f-148">Eine Reihe von Kopfhörern mit einem integrierten Mikrofon (wenn das Headset nicht über eine integrierte Mic-und-Sprech Anwendung verfügt)</span><span class="sxs-lookup"><span data-stu-id="ec15f-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="ec15f-149">Internet Zugriff für Azure-Setup und Luis-Abruf</span><span class="sxs-lookup"><span data-stu-id="ec15f-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ec15f-150">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="ec15f-150">Before you start</span></span>

1.  <span data-ttu-id="ec15f-151">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="ec15f-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="ec15f-152">Damit Ihr Computer das Diktat aktivieren kann, wechseln Sie zu **Windows-Einstellungen > Datenschutz > Sprache, & eingeben,** und drücken Sie dann die Schaltfläche **Sprachdienste aktivieren und Vorschläge eingeben**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="ec15f-153">Der Code in diesem Tutorial ermöglicht Ihnen das Aufzeichnen der standardmäßigen **Mikrofon Geräte** , die auf Ihrem Computer festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="ec15f-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="ec15f-154">Stellen Sie sicher, dass das standardmikrofon als das Mikrofon festgelegt ist, das Sie zum Erfassen Ihrer Stimme verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="ec15f-155">Wenn Ihr Headset über ein integriertes Mikrofon verfügt, stellen Sie sicher, dass die Option *"Wenn ich mein Headset verwende, zu Headset mic wechseln"* in den Einstellungen für das *gemischte Reality-Portal* aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Einrichten des immersiven Headsets](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="ec15f-157">Kapitel 1 – Einrichten des Azure-Portals</span><span class="sxs-lookup"><span data-stu-id="ec15f-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="ec15f-158">Wenn Sie den *Language Understanding* -Dienst in Azure verwenden möchten, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="ec15f-159">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="ec15f-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ec15f-160">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ec15f-161">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ec15f-162">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Language Understanding*, und drücken Sie die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="ec15f-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Erstellen einer Luis-Ressource](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="ec15f-164">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="ec15f-165">Die neue Seite auf der rechten Seite enthält eine Beschreibung des Language Understanding Dienstanbieter.</span><span class="sxs-lookup"><span data-stu-id="ec15f-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="ec15f-166">Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Luis-Dienst Erstellung-rechtliche Hinweise](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="ec15f-168">Nachdem Sie auf erstellen geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="ec15f-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="ec15f-169">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="ec15f-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="ec15f-170">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="ec15f-171">Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen *Luis-Dienst*erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="ec15f-172">Die kostenlose Zuweisung sollte für diesen Kurs mehr als ausreichend sein.</span><span class="sxs-lookup"><span data-stu-id="ec15f-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="ec15f-173">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="ec15f-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ec15f-174">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ec15f-175">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="ec15f-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="ec15f-176">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ec15f-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="ec15f-177">Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="ec15f-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ec15f-178">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ec15f-179">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ec15f-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="ec15f-180">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="ec15f-181">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-181">Select **Create**.</span></span>

        ![Erstellen eines Luis-Dienstanbieter-Benutzereingabe](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="ec15f-183">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="ec15f-184">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Neues Azure-Benachrichtigungs Image](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="ec15f-186">Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-186">Click on the notification to explore your new Service instance.</span></span>

    ![Benachrichtigung bei erfolgreicher Ressourcen Erstellung](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="ec15f-188">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ec15f-189">Sie gelangen zu ihrer neuen Luis-Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="ec15f-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Zugriff auf Luis-Schlüssel](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="ec15f-191">In diesem Lernprogramm muss Ihre Anwendung Aufrufe an Ihren Dienst durchführen. Dies erfolgt über den Abonnement Schlüssel Ihres dienstanzschlüssels.</span><span class="sxs-lookup"><span data-stu-id="ec15f-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="ec15f-192">Navigieren Sie auf der Seite " *Schnellstart* " Ihres *Luis-API* -Diensts zum ersten Schritt, rufen Sie *Ihre Schlüssel*ab, und klicken Sie auf " **Schlüssel** " (Sie können dies auch erreichen, indem Sie auf die blauen Hyperlink-Schlüssel klicken, die sich im Navigationsmenü der Dienste befinden und durch das Schlüsselsymbol gekennzeichnet sind).</span><span class="sxs-lookup"><span data-stu-id="ec15f-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="ec15f-193">Dadurch werden die Dienst *Schlüssel*angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="ec15f-194">Erstellen Sie eine Kopie von einem der angezeigten Schlüssel, da Sie dies später in Ihrem Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="ec15f-195">Klicken Sie auf der Seite *Dienst* auf *Language Understanding Portal* , um zu der Webseite umgeleitet zu werden, die Sie zum Erstellen des neuen Dienstanbieter in der Luis-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="ec15f-196">Kapitel 2 – das Language Understanding-Portal</span><span class="sxs-lookup"><span data-stu-id="ec15f-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="ec15f-197">In diesem Abschnitt erfahren Sie, wie Sie eine Luis-App im Luis-Portal erstellen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ec15f-198">Beachten Sie, dass das Einrichten von *Entitäten*, *Intents*und *Äußerungen* in diesem Kapitel nur der erste Schritt beim Erstellen eines Luis-diengs ist: Sie müssen den Dienst auch mehrmals neu trainieren, um ihn genauer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="ec15f-199">Das erneute Trainieren Ihres Dienstanbieter wird im [letzten Kapitel](#chapter-12--improving-your-luis-service) dieses Kurses behandelt. Stellen Sie also sicher, dass Sie den Dienst fertiggestellt haben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="ec15f-200">Wenn Sie das *Language Understanding-Portal*erreicht haben, müssen Sie sich ggf. mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden, falls Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Luis-Anmeldeseite](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="ec15f-202">Wenn Sie zum ersten Mal Luis verwenden, müssen Sie zum unteren Rand der Willkommensseite Scrollen, um die Schaltfläche " **Luis-app erstellen** " zu suchen und darauf zu klicken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Seite "Luis-app erstellen"](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="ec15f-204">Klicken Sie nach der Anmeldung auf " **meine apps** " (wenn Sie sich derzeit nicht in diesem Abschnitt befinden).</span><span class="sxs-lookup"><span data-stu-id="ec15f-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="ec15f-205">Klicken Sie dann auf **neue APP erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-205">You can then click on **Create new app**.</span></span>

    ![Luis-my Apps-Image](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="ec15f-207">*Benennen*Sie Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="ec15f-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="ec15f-208">Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die *Kultur* in die entsprechende Sprache ändern.</span><span class="sxs-lookup"><span data-stu-id="ec15f-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="ec15f-209">Hier können Sie auch eine *Beschreibung* ihrer neuen Luis-app hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![Luis: Erstellen einer neuen App](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="ec15f-211">Wenn Sie auf " **done**" klicken, geben Sie die buildseite *ihrer* neuen *Luis* -Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="ec15f-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="ec15f-212">Es gibt einige wichtige Konzepte, die Sie kennen sollten:</span><span class="sxs-lookup"><span data-stu-id="ec15f-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="ec15f-213">*Intent*stellt die Methode dar, die nach einer Abfrage des Benutzers aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="ec15f-214">Eine *Absicht* kann über eine oder mehrere *Entitäten*verfügen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="ec15f-215">Die *Entität*ist eine Komponente der Abfrage, die die für die *Absicht*relevanten Informationen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="ec15f-216">*Äußerungen*sind Beispiele für Abfragen, die vom Entwickler bereitgestellt werden, mit denen Luis sich selbst trainiert.</span><span class="sxs-lookup"><span data-stu-id="ec15f-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="ec15f-217">Wenn diese Konzepte nicht ganz klar sind, machen Sie sich keine Sorgen, da dieser Kurs Sie in diesem Kapitel näher erläutern wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="ec15f-218">Zunächst erstellen Sie die *Entitäten* , die zum Erstellen dieses Kurses benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="ec15f-219">Klicken Sie auf der linken Seite der Seite auf *Entitäten*, und klicken Sie dann auf **neue Entität erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Neue Entität erstellen](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="ec15f-221">Nennen Sie die neue Entitäts *Farbe*, legen Sie den Typ auf *Simple*fest, und drücken Sie dann auf **done**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Einfache Entitäts Farbe erstellen](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="ec15f-223">Wiederholen Sie diesen Vorgang, um drei (3) weitere einfache Entitäten namens zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="ec15f-224">*Upsizing*</span><span class="sxs-lookup"><span data-stu-id="ec15f-224">*upsize*</span></span>
    -   <span data-ttu-id="ec15f-225">*Verkleinern*</span><span class="sxs-lookup"><span data-stu-id="ec15f-225">*downsize*</span></span>
    -   <span data-ttu-id="ec15f-226">*Spar*</span><span class="sxs-lookup"><span data-stu-id="ec15f-226">*target*</span></span>

<span data-ttu-id="ec15f-227">Das Ergebnis sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-227">The result should look like the image below:</span></span>

![Ergebnis der Entitäts Erstellung](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="ec15f-229">An dieser Stelle können Sie mit dem Erstellen von *Intents*beginnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="ec15f-230">Löschen Sie nicht die Absicht " **keine** ".</span><span class="sxs-lookup"><span data-stu-id="ec15f-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="ec15f-231">Klicken Sie auf der linken Seite der Seite auf **Intents**, und klicken Sie dann auf **Create New Intent**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Neue Intents erstellen](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="ec15f-233">Nennen Sie die neue *Intent* **changeobjectcolor**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ec15f-234">Dieser *beabsichtigte Name wird* im Code weiter unten in diesem Kurs verwendet. verwenden Sie daher für optimale Ergebnisse den Namen genau wie angegeben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="ec15f-235">Nachdem Sie den Namen bestätigt haben, werden Sie zur Intents-Seite weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="ec15f-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![Seite "Luis-Intents"](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="ec15f-237">Sie werden feststellen, dass es ein Textfeld gibt, in dem Sie aufgefordert werden, 5 oder mehr unterschiedliche *Äußerungen*einzugeben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="ec15f-238">Luis konvertiert alle Äußerungen in Kleinbuchstaben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="ec15f-239">Fügen Sie die folgende *Äußerung* in das Textfeld Top ein (aktuell mit dem *Texttyp etwa 5 Beispiele...*</span><span class="sxs-lookup"><span data-stu-id="ec15f-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="ec15f-240">), und drücken **Sie die Eingabe**Taste:</span><span class="sxs-lookup"><span data-stu-id="ec15f-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="ec15f-241">Sie werden feststellen, dass die neue *Äußerung* in einer Liste unterhalb von angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="ec15f-242">Fügen Sie im Anschluss an denselben Prozess die folgenden sechs (6) Äußerungen ein:</span><span class="sxs-lookup"><span data-stu-id="ec15f-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="ec15f-243">Für jede Äußerung, die Sie erstellt haben, müssen Sie identifizieren, welche Wörter von Luis als Entitäten verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="ec15f-244">In diesem Beispiel müssen Sie alle Farben als *Farb* Entität und den gesamten möglichen Verweis auf ein Ziel als *Ziel* Entität bezeichnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="ec15f-245">Klicken Sie hierzu in der ersten Äußerung auf den Word- *Zylinder* , und wählen Sie *Ziel*aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Erkennen von Ausdrucks Zielen](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="ec15f-247">Klicken Sie nun auf das *Rote* Wort in der ersten Äußerung, und wählen Sie *Farbe*aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identifizieren von Ausdrucks Entitäten](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="ec15f-249">Bezeichnen Sie auch die nächste Zeile, wobei *Cube* ein *Ziel*sein sollte und *schwarz* eine *Farbe*sein sollte.</span><span class="sxs-lookup"><span data-stu-id="ec15f-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="ec15f-250">Beachten Sie auch die Verwendung der Wörter *' this '* , *' it '* und *' This Object '* , die wir bereitstellen, damit auch nicht spezifische Zieltypen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ec15f-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="ec15f-251">Wiederholen Sie den obigen Prozess, bis alle Äußerungen über die gekennzeichneten Entitäten verfügen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="ec15f-252">Wenn Sie Hilfe benötigen, sehen Sie sich das folgende Bild an.</span><span class="sxs-lookup"><span data-stu-id="ec15f-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="ec15f-253">Beim Auswählen von Wörtern, um Sie als Entitäten zu bezeichnen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="ec15f-254">Klicken Sie einfach auf die einzelnen Wörter.</span><span class="sxs-lookup"><span data-stu-id="ec15f-254">For single words just click them.</span></span>
    > - <span data-ttu-id="ec15f-255">Für einen Satz von zwei oder mehr Wörtern klicken Sie am Anfang und dann am Ende der Menge.</span><span class="sxs-lookup"><span data-stu-id="ec15f-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ec15f-256">Sie können die UMSCHALT Fläche *Tokens anzeigen* verwenden, um zwischen **Entitäten/Tokens anzuzeigen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="ec15f-257">Die Ergebnisse sollten wie in den folgenden Abbildungen dargestellt werden, die die **Entitäten/Tokens anzeigen**:</span><span class="sxs-lookup"><span data-stu-id="ec15f-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Token & Entitäts Sichten](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="ec15f-259">Klicken Sie an dieser Stelle oben rechts auf der Seite auf die Schaltfläche **trainieren** , und warten Sie, bis der kleine Round-Indikator darauf Grün zeigt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="ec15f-260">Dies deutet darauf hin, dass Luis erfolgreich trainiert wurde, um diese Absicht zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Train Luis](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="ec15f-262">Erstellen Sie als Übung eine neue Absicht namens **changeobjectsize**, indem Sie die Entitäten *target*, *Upsizing*und *verkleinern*verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="ec15f-263">Fügen Sie nach dem gleichen Prozess wie die vorherige Absicht die folgenden acht (8) Äußerungen für die *Größen* Änderung ein:</span><span class="sxs-lookup"><span data-stu-id="ec15f-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="ec15f-264">Das Ergebnis sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-264">The result should be like the one in the image below:</span></span>

    ![Einrichten der changeobjectsize-Token/-Entitäten](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="ec15f-266">Nachdem beide Intents, **changeobjectcolor** und **changeobjectsize**erstellt und trainiert wurden, klicken Sie oben auf der Seite auf die Schaltfläche **veröffentlichen** .</span><span class="sxs-lookup"><span data-stu-id="ec15f-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Luis-Dienst veröffentlichen](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="ec15f-268">Auf der *Veröffentlichungs* Seite beenden und veröffentlichen Sie Ihre Luis-APP, damit Sie von Ihrem Code aus darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="ec15f-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="ec15f-269">Legen Sie die Dropdown- *Veröffentlichung auf* **Production**fest.</span><span class="sxs-lookup"><span data-stu-id="ec15f-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="ec15f-270">Legen Sie die *Zeitzone* auf die Zeitzone fest.</span><span class="sxs-lookup"><span data-stu-id="ec15f-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="ec15f-271">Aktivieren Sie das Kontrollkästchen **alle vorhergesagten Intent-Ergebnisse einschließen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="ec15f-272">Klicken Sie auf **in Produktions Slot veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-272">Click on **Publish to Production Slot**.</span></span>

        ![Veröffentlichungs Einstellungen](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="ec15f-274">Im Abschnitt *Ressourcen und Schlüssel*:</span><span class="sxs-lookup"><span data-stu-id="ec15f-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="ec15f-275">Wählen Sie die Region aus, die Sie für die Dienst Instanz im Azure-Portal festlegen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="ec15f-276">Sie werden feststellen, dass ein **Starter_Key** -Element unten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="ec15f-277">Klicken Sie auf **Schlüssel hinzufügen** , und fügen Sie den *Schlüssel* ein, den Sie beim Erstellen Ihrer Dienst Instanz im Azure-Portal abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="ec15f-278">Wenn Ihr Azure-und das Luis-Portal beim gleichen Benutzer angemeldet sind, erhalten Sie Dropdown Menüs für den Mandanten *Namen*, den *Abonnement Namen*und den *Schlüssel* , den Sie verwenden möchten (hat denselben Namen wie zuvor im Azure-Portal angegeben).</span><span class="sxs-lookup"><span data-stu-id="ec15f-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="ec15f-279">Nehmen Sie unter *Endpunkt*eine Kopie des Endpunkts an, der dem von Ihnen eingefügten Schlüssel entspricht, und verwenden Sie ihn bald in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="ec15f-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="ec15f-280">Kapitel 3 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="ec15f-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="ec15f-281">Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="ec15f-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ec15f-282">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-282">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="ec15f-284">Sie müssen nun einen Unity-Projektnamen angeben und **MR_LUIS**einfügen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="ec15f-285">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ec15f-286">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="ec15f-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ec15f-287">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-287">Then, click **Create project**.</span></span>

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="ec15f-289">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ec15f-290">Wechseln Sie zu Edit > Preferences (Einstellungen bearbeiten), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ec15f-291">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ec15f-292">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="ec15f-292">Close the **Preferences** window.</span></span>

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="ec15f-294">Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="ec15f-296">Wechseln Sie zu **Datei > Build-Einstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="ec15f-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="ec15f-297">Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="ec15f-298">Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.</span><span class="sxs-lookup"><span data-stu-id="ec15f-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="ec15f-299">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="ec15f-300">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="ec15f-301">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="ec15f-302">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="ec15f-303">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="ec15f-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="ec15f-304">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ec15f-305">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-305">A save window will appear.</span></span>
        
            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="ec15f-307">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="ec15f-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="ec15f-309">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_LuisScene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="ec15f-311">Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="ec15f-312">Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="ec15f-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="ec15f-314">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="ec15f-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="ec15f-315">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="ec15f-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="ec15f-316">Die **Lauf Zeit Version der Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="ec15f-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="ec15f-317">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="ec15f-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="ec15f-318">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="ec15f-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="ec15f-320">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ec15f-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ec15f-321">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="ec15f-321">**InternetClient**</span></span>
        2. <span data-ttu-id="ec15f-322">**Tritt**</span><span class="sxs-lookup"><span data-stu-id="ec15f-322">**Microphone**</span></span>

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="ec15f-324">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="ec15f-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="ec15f-326">Zurück in *Buildeinstellungen* : _Unity C#_  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="ec15f-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="ec15f-327">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="ec15f-328">Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).</span><span class="sxs-lookup"><span data-stu-id="ec15f-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="ec15f-329">Kapitel 4 – Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="ec15f-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec15f-330">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)herunterladen, es als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5](#chapter-5--create-the-microphonemanager-class)fortfahren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="ec15f-331">Klicken Sie mit der rechten Maustaste in einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **3D-Objekt**eine **Ebene**hinzu.</span><span class="sxs-lookup"><span data-stu-id="ec15f-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Erstellen Sie eine Ebene.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="ec15f-333">Wenn Sie erneut mit der rechten Maustaste in der *Hierarchie* klicken, um weitere Objekte zu erstellen, ist das ausgewählte Objekt das übergeordnete Objekt des neuen Objekts, wenn Sie noch das letzte Objekt ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="ec15f-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="ec15f-334">Vermeiden Sie dieses Problem, indem Sie auf einen leeren Bereich innerhalb der Hierarchie klicken und dann mit der rechten Maustaste klicken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="ec15f-335">Wiederholen Sie das oben beschriebene Verfahren, um die folgenden Objekte hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="ec15f-336">*SP*</span><span class="sxs-lookup"><span data-stu-id="ec15f-336">*Sphere*</span></span>
    2. <span data-ttu-id="ec15f-337">*Sechs*</span><span class="sxs-lookup"><span data-stu-id="ec15f-337">*Cylinder*</span></span>
    3. <span data-ttu-id="ec15f-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="ec15f-338">*Cube*</span></span>
    4. <span data-ttu-id="ec15f-339">*3D-Text*</span><span class="sxs-lookup"><span data-stu-id="ec15f-339">*3D Text*</span></span>

4.  <span data-ttu-id="ec15f-340">Die resultierende Szenen *Hierarchie* sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Einrichtung der Szenen Hierarchie.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="ec15f-342">Klicken Sie mit der linken Maustaste auf die **Hauptkamera** , um Sie auszuwählen. im *Inspektor-Panel* sehen Sie das Kamera Objekt mit allen zugehörigen Komponenten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="ec15f-343">Klicken Sie auf die Schaltfläche **Komponente hinzufügen** , die sich am unteren Rand des *inspektorbereichs*befindet.</span><span class="sxs-lookup"><span data-stu-id="ec15f-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Audioquelle hinzufügen](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="ec15f-345">Suchen Sie nach der Komponente namens *Audioquelle*, wie oben gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="ec15f-346">Stellen Sie außerdem sicher, dass die *Transformations* Komponente der Hauptkamera auf (0, 0, 0) festgelegt ist. Klicken Sie hierzu auf das **Zahnrad** Symbol neben der *Transformations* Komponente der Kamera und dann auf **Zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="ec15f-347">Die *Transformations* Komponente sollte dann wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="ec15f-348">Die *Position* ist auf **0, 0, 0**(null) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="ec15f-349">*Drehung* ist auf **0, 0, 0**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ec15f-350">Für Microsoft hololens müssen Sie auch Folgendes ändern, das Teil der **Kamera** Komponente ist, die sich auf der **Hauptkamera**befindet:</span><span class="sxs-lookup"><span data-stu-id="ec15f-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="ec15f-351">**Flags löschen:** Voll Tonfarbe.</span><span class="sxs-lookup"><span data-stu-id="ec15f-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="ec15f-352">**Hintergrund** ' Black, Alpha 0 ' – hexadezimal Farbe: #00000000.</span><span class="sxs-lookup"><span data-stu-id="ec15f-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="ec15f-353">Klicken Sie mit der linken Maustaste auf die **Ebene** , um Sie auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="ec15f-354">Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:</span><span class="sxs-lookup"><span data-stu-id="ec15f-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ec15f-355">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="ec15f-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ec15f-356">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-356">**X**</span></span> | <span data-ttu-id="ec15f-357">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-357">**Y**</span></span>                  | <span data-ttu-id="ec15f-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-358">**Z**</span></span> |
    | <span data-ttu-id="ec15f-359">0</span><span class="sxs-lookup"><span data-stu-id="ec15f-359">0</span></span>     | <span data-ttu-id="ec15f-360">-1</span><span class="sxs-lookup"><span data-stu-id="ec15f-360">-1</span></span>                     | <span data-ttu-id="ec15f-361">0</span><span class="sxs-lookup"><span data-stu-id="ec15f-361">0</span></span>     |


10. <span data-ttu-id="ec15f-362">Klicken Sie mit der linken Maustaste auf die **Kugel** , um Sie auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="ec15f-363">Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:</span><span class="sxs-lookup"><span data-stu-id="ec15f-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ec15f-364">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="ec15f-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ec15f-365">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-365">**X**</span></span> | <span data-ttu-id="ec15f-366">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-366">**Y**</span></span>                  | <span data-ttu-id="ec15f-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-367">**Z**</span></span> |
    | <span data-ttu-id="ec15f-368">2</span><span class="sxs-lookup"><span data-stu-id="ec15f-368">2</span></span>     | <span data-ttu-id="ec15f-369">1</span><span class="sxs-lookup"><span data-stu-id="ec15f-369">1</span></span>                      | <span data-ttu-id="ec15f-370">2</span><span class="sxs-lookup"><span data-stu-id="ec15f-370">2</span></span>     |

11. <span data-ttu-id="ec15f-371">Klicken Sie mit der linken Maustaste auf den **Zylinder** , um ihn auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="ec15f-372">Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:</span><span class="sxs-lookup"><span data-stu-id="ec15f-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ec15f-373">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="ec15f-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ec15f-374">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-374">**X**</span></span> | <span data-ttu-id="ec15f-375">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-375">**Y**</span></span>                  | <span data-ttu-id="ec15f-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-376">**Z**</span></span> |
    | <span data-ttu-id="ec15f-377">-2</span><span class="sxs-lookup"><span data-stu-id="ec15f-377">-2</span></span>    | <span data-ttu-id="ec15f-378">1</span><span class="sxs-lookup"><span data-stu-id="ec15f-378">1</span></span>                      | <span data-ttu-id="ec15f-379">2</span><span class="sxs-lookup"><span data-stu-id="ec15f-379">2</span></span>     |

12. <span data-ttu-id="ec15f-380">Klicken Sie mit der linken Maustaste auf den **Cube** , um ihn auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="ec15f-381">Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:</span><span class="sxs-lookup"><span data-stu-id="ec15f-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="ec15f-382">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="ec15f-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="ec15f-383">Transformation- *Drehung*</span><span class="sxs-lookup"><span data-stu-id="ec15f-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ec15f-384">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-384">**X**</span></span> | <span data-ttu-id="ec15f-385">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-385">**Y**</span></span>                   | <span data-ttu-id="ec15f-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-386">**Z**</span></span> |  \| | <span data-ttu-id="ec15f-387">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-387">**X**</span></span> | <span data-ttu-id="ec15f-388">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-388">**Y**</span></span>                  | <span data-ttu-id="ec15f-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-389">**Z**</span></span> |
    | <span data-ttu-id="ec15f-390">0</span><span class="sxs-lookup"><span data-stu-id="ec15f-390">0</span></span>     | <span data-ttu-id="ec15f-391">1</span><span class="sxs-lookup"><span data-stu-id="ec15f-391">1</span></span>                       | <span data-ttu-id="ec15f-392">4</span><span class="sxs-lookup"><span data-stu-id="ec15f-392">4</span></span>     |  \| | <span data-ttu-id="ec15f-393">45</span><span class="sxs-lookup"><span data-stu-id="ec15f-393">45</span></span>    | <span data-ttu-id="ec15f-394">45</span><span class="sxs-lookup"><span data-stu-id="ec15f-394">45</span></span>                     | <span data-ttu-id="ec15f-395">0</span><span class="sxs-lookup"><span data-stu-id="ec15f-395">0</span></span>     | 

13. <span data-ttu-id="ec15f-396">Klicken Sie mit der linken Maustaste auf das **neue Text** Objekt, um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="ec15f-397">Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:</span><span class="sxs-lookup"><span data-stu-id="ec15f-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ec15f-398">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="ec15f-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="ec15f-399">Transformieren: *skalieren*</span><span class="sxs-lookup"><span data-stu-id="ec15f-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="ec15f-400">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-400">**X**</span></span> | <span data-ttu-id="ec15f-401">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-401">**Y**</span></span>                  | <span data-ttu-id="ec15f-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-402">**Z**</span></span> |  \| | <span data-ttu-id="ec15f-403">**Stuben**</span><span class="sxs-lookup"><span data-stu-id="ec15f-403">**X**</span></span> | <span data-ttu-id="ec15f-404">**Teenie**</span><span class="sxs-lookup"><span data-stu-id="ec15f-404">**Y**</span></span>               | <span data-ttu-id="ec15f-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="ec15f-405">**Z**</span></span> |
    | <span data-ttu-id="ec15f-406">-2</span><span class="sxs-lookup"><span data-stu-id="ec15f-406">-2</span></span>    | <span data-ttu-id="ec15f-407">6</span><span class="sxs-lookup"><span data-stu-id="ec15f-407">6</span></span>                      | <span data-ttu-id="ec15f-408">9</span><span class="sxs-lookup"><span data-stu-id="ec15f-408">9</span></span>     |  \| | <span data-ttu-id="ec15f-409">0,1</span><span class="sxs-lookup"><span data-stu-id="ec15f-409">0.1</span></span>   | <span data-ttu-id="ec15f-410">0,1</span><span class="sxs-lookup"><span data-stu-id="ec15f-410">0.1</span></span>                 | <span data-ttu-id="ec15f-411">0,1</span><span class="sxs-lookup"><span data-stu-id="ec15f-411">0.1</span></span>   | 

14. <span data-ttu-id="ec15f-412">Ändern Sie den **Schrift** Grad in der **texmesh** -Komponente in **50**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="ec15f-413">Ändern Sie den *Namen* des **textmesh** -Objekts in den **Diktat Text**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![3D-Text Objekt erstellen](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="ec15f-415">Ihre Hierarchie Panel-Struktur sollte nun wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![textmesh in der Szene Ansicht](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="ec15f-417">Die endgültige Szene sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-417">The final scene should look like the image below:</span></span>

    ![Die Szenen Ansicht.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="ec15f-419">Kapitel 5 – Erstellen der Klasse "mikrophonemanager"</span><span class="sxs-lookup"><span data-stu-id="ec15f-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="ec15f-420">Das erste Skript, das Sie erstellen, ist die Klasse " *mikrophonemanager* ".</span><span class="sxs-lookup"><span data-stu-id="ec15f-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="ec15f-421">Danach erstellen Sie den *luismanager* *, die Behaviour* -Klasse und schließlich die Klasse " *Blick* " (Sie können all diese jetzt erstellen, obwohl Sie in jedem Kapitel behandelt wird).</span><span class="sxs-lookup"><span data-stu-id="ec15f-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="ec15f-422">Die Klasse " *mikrophonemanager* " ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="ec15f-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="ec15f-423">Erkennen des Aufzeichnungs Geräts, das an das Headset oder den Computer angefügt ist (je nachdem, welches der Standard ist).</span><span class="sxs-lookup"><span data-stu-id="ec15f-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="ec15f-424">Erfassen Sie das Audiomaterial (Voice), und speichern Sie es als Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="ec15f-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="ec15f-425">Nachdem die Stimme angehalten wurde, senden Sie die Diktat an die *luismanager* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="ec15f-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="ec15f-426">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="ec15f-426">To create this class:</span></span> 

1.  <span data-ttu-id="ec15f-427">Klicken Sie im *Projekt Panel*mit der rechten Maustaste, und **Erstellen Sie > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="ec15f-428">Nennen Sie die Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-428">Call the folder **Scripts**.</span></span> 

    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="ec15f-430">Wenn Sie den Ordner **Skripts** erstellt haben, doppelklicken Sie darauf, um zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="ec15f-431">Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und **Erstellen Sie > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="ec15f-432">Nennen Sie das Skript " *mikrophonemanager*".</span><span class="sxs-lookup"><span data-stu-id="ec15f-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="ec15f-433">Doppelklicken Sie auf " *mikrophonemanager* ", um die Datei mit *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="ec15f-434">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="ec15f-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="ec15f-435">Fügen Sie dann die folgenden Variablen in der Klasse " *mikrophonemanager* " hinzu:</span><span class="sxs-lookup"><span data-stu-id="ec15f-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="ec15f-436">Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="ec15f-437">Diese werden aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="ec15f-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="ec15f-438">Nun benötigen Sie die Methode, die die APP verwendet, um die sprach Erfassung zu starten und anzuhalten, und Sie an die *luismanager* -Klasse weiterzuleiten, die Sie bald erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="ec15f-439">Fügen Sie einen *Diktat Handler* hinzu, der aufgerufen wird, wenn die Stimme angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="ec15f-440">Diese Methode übergibt den Diktat Text an die *luismanager* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="ec15f-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="ec15f-441">Löschen Sie die *Update ()* -Methode, da Sie von dieser Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="ec15f-442">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ec15f-443">An dieser Stelle bemerken Sie einen Fehler, der im *Konsolen Panel des Unity-Editors*angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="ec15f-444">Dies liegt daran, dass der Code auf die *luismanager* -Klasse verweist, die Sie im nächsten Kapitel erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="ec15f-445">Kapitel 6 – Erstellen der luismanager-Klasse</span><span class="sxs-lookup"><span data-stu-id="ec15f-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="ec15f-446">Es ist an der Zeit, die *luismanager* -Klasse zu erstellen, die den Aufruf an den Azure Luis-Dienst durchführt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="ec15f-447">Der Zweck dieser Klasse besteht darin, den Diktat Text von der Klasse " *mikrophonemanager* " zu empfangen und an die zu analysierende *Azure-Language Understanding-API* zu senden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="ec15f-448">Diese Klasse deserialisiert die *JSON* -Antwort und ruft die entsprechenden *Methoden der Behaviour-Klasse auf* , um eine Aktion zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="ec15f-449">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="ec15f-449">To create this class:</span></span> 

1.  <span data-ttu-id="ec15f-450">Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ec15f-451">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ec15f-452">Benennen Sie das Skript mit " *luismanager*".</span><span class="sxs-lookup"><span data-stu-id="ec15f-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="ec15f-453">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="ec15f-454">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="ec15f-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="ec15f-455">Beginnen Sie mit dem Erstellen von drei Klassen **innerhalb** der Klasse " *luismanager* " (innerhalb derselben Skriptdatei oberhalb der Methode " *Start ()* "), die die deserialisierte JSON-Antwort von Azure darstellt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="ec15f-456">Fügen Sie als nächstes die folgenden Variablen in der Klasse " *luismanager* " hinzu:</span><span class="sxs-lookup"><span data-stu-id="ec15f-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="ec15f-457">Stellen Sie sicher, dass Sie Ihren Luis-Endpunkt jetzt platzieren (über Ihr Luis-Portal).</span><span class="sxs-lookup"><span data-stu-id="ec15f-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="ec15f-458">Code für die *Awa()* -Methode muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="ec15f-459">Diese Methode wird aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="ec15f-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="ec15f-460">Nun benötigen Sie die Methoden, die von dieser Anwendung verwendet werden, um die von *der Klasse "* -Klasse" empfangene Diktat an *Luis*zu senden und die Antwort zu empfangen und zu deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="ec15f-461">Nachdem der Wert der Absicht und der zugeordneten Entitäten ermittelt wurden, werden Sie an die *Instanz der Behaviour-Klasse über* mittelt, um die beabsichtigte Aktion zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="ec15f-462">Erstellen Sie eine neue Methode mit dem Namen *analyseresponcelements ()* , mit der die resultierende *analysedquery* gelesen und die Entitäten bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="ec15f-463">Nachdem diese Entitäten ermittelt wurden, werden Sie an die *Instanz der Behaviour-Klasse zur* Verwendung in den Aktionen übermittelt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="ec15f-464">Löschen Sie die Methoden " *Start ()* " und " *Update ()* ", da Sie von dieser Klasse nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="ec15f-465">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="ec15f-466">An diesem Punkt sehen Sie mehrere Fehler, die im *Konsolen Panel des Unity-Editors angezeigt*werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="ec15f-467">Dies liegt daran, dass der Code auf die *Verhaltens* Klasse verweist, die Sie im nächsten Kapitel erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="ec15f-468">Kapitel 7 – Erstellen der Verhaltens Klasse</span><span class="sxs-lookup"><span data-stu-id="ec15f-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="ec15f-469">Die *Verhaltens* Klasse löst die Aktionen mithilfe der von der *luismanager* -Klasse bereitgestellten Entitäten aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="ec15f-470">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="ec15f-470">To create this class:</span></span> 

1.  <span data-ttu-id="ec15f-471">Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ec15f-472">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ec15f-473">Benennen Sie das Skript *Verhalten*.</span><span class="sxs-lookup"><span data-stu-id="ec15f-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="ec15f-474">Doppelklicken Sie auf das Skript, um es in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="ec15f-475">Fügen Sie dann die folgenden Variablen in der *Verhaltens* Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="ec15f-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="ec15f-476">Fügen Sie den *Awa()* -Methoden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="ec15f-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="ec15f-477">Diese Methode wird aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="ec15f-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="ec15f-478">Die folgenden Methoden werden von der *luismanager* -Klasse aufgerufen (die Sie zuvor erstellt haben), um zu bestimmen, welches Objekt das Ziel der Abfrage ist, und dann die entsprechende Aktion auslöst.</span><span class="sxs-lookup"><span data-stu-id="ec15f-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="ec15f-479">Fügen Sie die *findtarget ()* -Methode hinzu, um zu bestimmen, welches der *gameobjects* das Ziel der aktuellen Absicht ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="ec15f-480">Diese Methode verwendet standardmäßig das als Ziel festgelegte *gameobject* , wenn in den Entitäten kein explizites Ziel definiert ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="ec15f-481">Löschen Sie die Methoden " *Start ()* " und " *Update ()* ", da Sie von dieser Klasse nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="ec15f-482">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="ec15f-483">Kapitel 8 – Erstellen der "Blick"-Klasse</span><span class="sxs-lookup"><span data-stu-id="ec15f-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="ec15f-484">Die letzte Klasse, die Sie zum Durchführen dieser APP benötigen, ist die " *Gaze* "-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ec15f-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="ec15f-485">Diese Klasse aktualisiert den Verweis auf das *gameobject-Objekt* , das sich derzeit im visuellen Fokus des Benutzers befindet.</span><span class="sxs-lookup"><span data-stu-id="ec15f-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="ec15f-486">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="ec15f-486">To create this Class:</span></span> 

1.  <span data-ttu-id="ec15f-487">Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ec15f-488">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ec15f-489">Benennen Sie das *Skript mit*dem Namen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="ec15f-490">Doppelklicken Sie auf das Skript, um es in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="ec15f-491">Fügen Sie den folgenden Code für diese Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="ec15f-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="ec15f-492">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="ec15f-493">Kapitel 9 – Abschließen der Szenen Einrichtung</span><span class="sxs-lookup"><span data-stu-id="ec15f-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="ec15f-494">Um die Einrichtung der Szene abzuschließen, ziehen Sie jedes Skript, das Sie erstellt haben, aus dem Ordner Scripts auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="ec15f-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="ec15f-495">Wählen Sie die **Hauptkamera** aus, und sehen Sie sich im *Inspektor-Panel*an, dass jedes angefügte Skript angezeigt werden sollte. Sie werden feststellen, dass für jedes Skript Parameter vorhanden sind, die noch festgelegt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Die Kamera Verweis Ziele werden festgelegt.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="ec15f-497">Um diese Parameter korrekt festzulegen, befolgen Sie die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="ec15f-498">" *Mikrophonemanager*":</span><span class="sxs-lookup"><span data-stu-id="ec15f-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="ec15f-499">Ziehen Sie das **Diktat Text** Objekt aus dem Bereich *Hierarchie*in das Feld **Diktat Text** Parameter value.</span><span class="sxs-lookup"><span data-stu-id="ec15f-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="ec15f-500">*Verhalten*im *Hierarchie Panel*:</span><span class="sxs-lookup"><span data-stu-id="ec15f-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="ec15f-501">Ziehen Sie das **Sphere** -Objekt in das Feld *Kugel* Verweis Ziel.</span><span class="sxs-lookup"><span data-stu-id="ec15f-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="ec15f-502">Ziehen Sie den **Zylinder** in das Feld *Zylinder* Verweis Ziel.</span><span class="sxs-lookup"><span data-stu-id="ec15f-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="ec15f-503">Ziehen Sie den **Cube** in das Feld *Cube* Reference Target.</span><span class="sxs-lookup"><span data-stu-id="ec15f-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="ec15f-504">*Blick*:</span><span class="sxs-lookup"><span data-stu-id="ec15f-504">*Gaze*:</span></span>

        - <span data-ttu-id="ec15f-505">Legen Sie die *Maximale Länge des Blicks* auf **300** fest (sofern nicht bereits geschehen).</span><span class="sxs-lookup"><span data-stu-id="ec15f-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="ec15f-506">Das Ergebnis sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-506">The result should look like the image below:</span></span>

    ![Die angezeigte Kamera Verweis Ziele werden angezeigt.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="ec15f-508">Kapitel 10 – Testen im Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="ec15f-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="ec15f-509">Testen Sie, ob die Szenen Einrichtung ordnungsgemäß implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="ec15f-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="ec15f-510">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="ec15f-510">Ensure that:</span></span>

-   <span data-ttu-id="ec15f-511">Alle Skripts werden an das **Hauptkamera** Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="ec15f-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="ec15f-512">Alle Felder im Hauptbereich der *Kamera Inspektor* sind ordnungsgemäß zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="ec15f-513">Klicken Sie im *Unity-Editor*auf die Schaltfläche wieder **Gabe** .</span><span class="sxs-lookup"><span data-stu-id="ec15f-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="ec15f-514">Die APP sollte innerhalb des angefügten immersiven Headsets ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="ec15f-515">Probieren Sie einige Äußerungen aus, z. b.:</span><span class="sxs-lookup"><span data-stu-id="ec15f-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="ec15f-516">Wenn in der Unity-Konsole eine Fehlermeldung angezeigt wird, dass das Standardaudiogerät geändert wird, funktioniert die Szene möglicherweise nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="ec15f-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="ec15f-517">Der Grund hierfür ist die Art und Weise, wie das Mixed Reality-Portal mit integrierten Mikrofonen für Headsets umgeht, auf denen es sich befindet.</span><span class="sxs-lookup"><span data-stu-id="ec15f-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="ec15f-518">Wenn dieser Fehler angezeigt wird, halten Sie die Szene einfach an, und starten Sie Sie erneut, und die Dinge sollten erwartungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="ec15f-519">Kapitel 11 – erstellen und querladen der UWP-Lösung</span><span class="sxs-lookup"><span data-stu-id="ec15f-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="ec15f-520">Nachdem Sie sichergestellt haben, dass die Anwendung im Unity-Editor funktioniert, können Sie erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="ec15f-521">So erstellen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ec15f-521">To Build:</span></span>

1.  <span data-ttu-id="ec15f-522">Speichern Sie die aktuelle Szene, indem Sie auf **Datei > Speichern**klicken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="ec15f-523">Wechseln Sie zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="ec15f-524">Aktivieren Sie das Feld mit dem Namen **Unity C# -Projekte** (nützlich zum Anzeigen und Debuggen des Codes, nachdem das UWP-Projekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="ec15f-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="ec15f-525">Klicken Sie auf **offene Szenen hinzufügen**, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Fenster mit Buildeinstellungen](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="ec15f-527">Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projekt Mappe erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="ec15f-528">Erstellen Sie einen Ordner *BUILDS* , und erstellen Sie in diesem Ordner einen anderen Ordner mit einem entsprechenden Namen Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="ec15f-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="ec15f-529">Klicken Sie auf **Ordner auswählen** , um den Build an diesem Speicherort zu starten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="ec15f-530">![Ordner Create Builds](images/AzureLabs-Lab3-44.png)
    ![Ordner Builds auswählen](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="ec15f-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="ec15f-531">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), sollte ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="ec15f-532">Zum Bereitstellen auf dem lokalen Computer:</span><span class="sxs-lookup"><span data-stu-id="ec15f-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="ec15f-533">Öffnen Sie in *Visual Studio*die Projektmappendatei, die im [vorherigen Kapitel](#chapter-10--test-in-the-unity-editor)erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="ec15f-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="ec15f-534">Wählen Sie auf der Projektmappenplattform die Option **x86**, **lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="ec15f-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="ec15f-535">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="ec15f-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="ec15f-536">Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="ec15f-537">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="ec15f-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="ec15f-538">Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den *Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen*; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="ec15f-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="ec15f-539">Stellen Sie sicher, dass der **Entwicklermodus** **auf**dem in den *Einstellungen > Update & Sicherheits > für Entwickler*gefunden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![App bereitstellen](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="ec15f-541">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="ec15f-542">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, damit Sie gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="ec15f-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="ec15f-543">Nach dem Start werden Sie von der APP aufgefordert, den Zugriff auf das _Mikrofon_zu autorisieren.</span><span class="sxs-lookup"><span data-stu-id="ec15f-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="ec15f-544">Verwenden Sie die *Bewegungs Controller*, die *Spracheingabe*oder die *Tastatur* , um die Schaltfläche **Ja** zu drücken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="ec15f-545">Kapitel 12 – verbessern Ihres Luis-Dienstanbieter</span><span class="sxs-lookup"><span data-stu-id="ec15f-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="ec15f-546">Dieses Kapitel ist äußerst wichtig und muss möglicherweise mehrmals durchlaufen werden, da es zur Verbesserung der Genauigkeit ihres Luis-Dienstanbieter beiträgt: Stellen Sie sicher, dass Sie dies durchführen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="ec15f-547">Um das von Luis bereitgestellte Maß an Verständnis zu verbessern, müssen Sie neue Äußerungen erfassen und diese zum erneuten trainieren ihrer Luis-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="ec15f-548">Beispielsweise haben Sie Luis trainiert, um "Zunahme" und "Upsize" zu verstehen, aber möchten Sie nicht, dass Ihre APP auch Wörter wie "vergrößern" versteht?</span><span class="sxs-lookup"><span data-stu-id="ec15f-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="ec15f-549">Nachdem Sie die Anwendung mehrmals verwendet haben, wird alles, was Sie bereits erwähnt haben, von Luis gesammelt und im Luis-Portal verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="ec15f-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="ec15f-550">Wechseln Sie nach diesem [Link](https://www.luis.ai/home)zu ihrer Portal Anwendung, und melden Sie sich an.</span><span class="sxs-lookup"><span data-stu-id="ec15f-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="ec15f-551">Wenn Sie mit ihren MS-Anmelde Informationen angemeldet sind, klicken Sie auf den *Namen Ihrer APP*.</span><span class="sxs-lookup"><span data-stu-id="ec15f-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="ec15f-552">Klicken Sie Links auf der Seite auf die Schaltfläche **Endpunkt Äußerungen überprüfen** .</span><span class="sxs-lookup"><span data-stu-id="ec15f-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Überprüfen von Äußerungen](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="ec15f-554">Ihnen wird eine Liste der Äußerungen angezeigt, die von ihrer gemischten Reality-Anwendung an Luis gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Liste der Äußerungen](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="ec15f-556">Sie werden einige hervorgehobene *Entitäten*bemerken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="ec15f-557">Wenn Sie mit dem Mauszeiger auf jedes markierte Wort zeigen, können Sie jede Äußerung überprüfen und bestimmen, welche Entität korrekt erkannt wurde, welche Entitäten falsch sind und welche Entitäten übersehen werden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="ec15f-558">Im obigen Beispiel wurde festgestellt, dass das Wort "Spear" als Ziel hervorgehoben wurde. es ist daher notwendig, den Fehler zu korrigieren, indem Sie mit der Maus auf das Wort zeigen und auf " **Bezeichnung entfernen**" klicken.</span><span class="sxs-lookup"><span data-stu-id="ec15f-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="ec15f-559">![überprüfen Sie](images/AzureLabs-Lab3-49.png)
![Label-Image entfernen](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="ec15f-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="ec15f-560">Wenn Sie Äußerungen gefunden haben, die vollständig falsch sind, können Sie Sie mithilfe der Schaltfläche **Löschen** auf der rechten Seite des Bildschirms löschen.</span><span class="sxs-lookup"><span data-stu-id="ec15f-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Falsche Äußerungen löschen](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="ec15f-562">Wenn Sie der Meinung sind, dass Luis die Äußerung ordnungsgemäß interpretiert hat, können Sie das Verständnis überprüfen, indem Sie die Schaltfläche **zur ausgerichteten Absicht hinzufügen** verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Zu ausgerichtete Absicht hinzufügen](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="ec15f-564">Nachdem Sie alle angezeigten Äußerungen sortiert haben, versuchen Sie, die Seite erneut zu laden, um festzustellen, ob weitere Informationen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ec15f-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="ec15f-565">Es ist sehr wichtig, diesen Prozess so oft wie möglich zu wiederholen, um das Verständnis Ihrer Anwendungen zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="ec15f-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="ec15f-566">**Viel Spass!**</span><span class="sxs-lookup"><span data-stu-id="ec15f-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="ec15f-567">Ihre beendete Luis-integrierte Anwendung</span><span class="sxs-lookup"><span data-stu-id="ec15f-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="ec15f-568">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure Language Understanding Intelligence-Dienst nutzt, um zu verstehen, was ein Benutzer sagt und welche Informationen Sie tun.</span><span class="sxs-lookup"><span data-stu-id="ec15f-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ec15f-570">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="ec15f-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ec15f-571">Übung 1</span><span class="sxs-lookup"><span data-stu-id="ec15f-571">Exercise 1</span></span>

<span data-ttu-id="ec15f-572">Wenn Sie diese Anwendung verwenden, werden Sie möglicherweise bemerken, dass Sie bei der Betrachtung des Floor-Objekts sehen, dass die Farbe geändert wird.</span><span class="sxs-lookup"><span data-stu-id="ec15f-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="ec15f-573">Können Sie herausfinden, wie Sie Ihre Anwendung daran hindern, die Bodenfarbe zu ändern?</span><span class="sxs-lookup"><span data-stu-id="ec15f-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ec15f-574">Übung 2</span><span class="sxs-lookup"><span data-stu-id="ec15f-574">Exercise 2</span></span>

<span data-ttu-id="ec15f-575">Erweitern Sie die Luis-und App-Funktionen, und fügen Sie zusätzliche Funktionen für Objekte in der Szene hinzu. Erstellen Sie z. b. neue Objekte auf dem Blickpunkt, je nachdem, was der Benutzer sagt, und können Sie diese Objekte mit den vorhandenen Befehlen neben den aktuellen Szenen Objekten verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec15f-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
