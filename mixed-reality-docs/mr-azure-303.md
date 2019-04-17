---
title: MR und Azure 303 - natürlicher sprachverständnis (LUIS)
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Language Understanding Intelligence Service (LUIS) innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Language Understanding Intelligence Service, Luis, Hololens, immersive vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595913"
---
>[!NOTE]
><span data-ttu-id="f6b1b-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f6b1b-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f6b1b-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f6b1b-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f6b1b-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f6b1b-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="f6b1b-110">MR und Azure 303: Verstehen natürlicher Sprache (LUIS)</span><span class="sxs-lookup"><span data-stu-id="f6b1b-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="f6b1b-111">In diesem Kurs lernen Sie, wie Sie Language Understanding in einer mixed Reality-Anwendung, die mithilfe von Azure Cognitive Services, mit dem Language Understanding-API zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="f6b1b-113">*Language Understanding (LUIS)* ist ein Microsoft Azure-Dienst, bietet Anwendungen die Möglichkeit, extrahieren, was eine Person, in ihren eigenen Worten sollten Bedeutung aus Benutzereingaben, z. B. vornehmen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="f6b1b-114">Dies erfolgt über Machine Learning versteht und lernt die eingegebenen Informationen und können dann mit detaillierten Informationen relevant sind, Antworten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="f6b1b-115">Weitere Informationen finden Sie auf die [Azure Language Understanding (LUIS) Seite](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="f6b1b-116">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung die können die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="f6b1b-117">Erfassen Sie User input Sprache, die über das Mikrofon, die an die immersive Kopfhörer angeschlossen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="f6b1b-118">Senden Sie die erfassten Diktat der *Azure Language Understanding Intelligent Service* (*LUIS*).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="f6b1b-119">Haben Sie die LUIS-extrahieren, d. h. von der Send-Informationen analysiert, und versucht zu bestimmen, dass die Absicht der Anforderung des Benutzers vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="f6b1b-120">Entwicklung umfasst die Erstellung einer App, in denen der Benutzer Lage ist, verwenden und/oder bestaunen zum Ändern der Größe und die Farbe der Objekte in der Szene.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="f6b1b-121">Die Verwendung der Motion-Controller wird nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="f6b1b-122">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f6b1b-123">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="f6b1b-124">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="f6b1b-125">Mehrmals zu trainieren von LUIS darauf vorbereitet sein, die finden Sie im [Kapitel 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="f6b1b-126">Sie erzielen bessere Ergebnisse weitere Male, die LUIS trainiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="f6b1b-127">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="f6b1b-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f6b1b-128">Kurs</span><span class="sxs-lookup"><span data-stu-id="f6b1b-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f6b1b-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f6b1b-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f6b1b-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="f6b1b-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f6b1b-131">MR und Azure 303: Verstehen natürlicher Sprache (LUIS)</span><span class="sxs-lookup"><span data-stu-id="f6b1b-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="f6b1b-132">✔️</span><span class="sxs-lookup"><span data-stu-id="f6b1b-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f6b1b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="f6b1b-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f6b1b-134">Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f6b1b-135">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f6b1b-136">Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6b1b-137">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f6b1b-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f6b1b-138">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f6b1b-139">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f6b1b-140">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="f6b1b-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f6b1b-141">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f6b1b-142">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="f6b1b-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f6b1b-143">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="f6b1b-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="f6b1b-144">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="f6b1b-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="f6b1b-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f6b1b-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="f6b1b-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f6b1b-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="f6b1b-147">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="f6b1b-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f6b1b-148">Eine Reihe von Kopfhörer mit ein eingebautes Mikrofon verfügen (wenn der Kopfhörer nicht über eine integrierte mic und die Lautsprecher verfügt)</span><span class="sxs-lookup"><span data-stu-id="f6b1b-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="f6b1b-149">Zugriff auf das Internet für die Einrichtung von Azure und Abrufen von LUIS</span><span class="sxs-lookup"><span data-stu-id="f6b1b-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f6b1b-150">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="f6b1b-150">Before you start</span></span>

1.  <span data-ttu-id="f6b1b-151">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="f6b1b-152">Damit können Ihre Computer, um Spracheingaben zu aktivieren, wechseln Sie zu **Windows-Einstellungen > Datenschutz >-Sprache, Freihand & Eingabe** , und drücken Sie auf die Schaltfläche **Aktivieren von Sprachdienste und Typisierung Vorschläge**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="f6b1b-153">Der Code in diesem Tutorial können Sie zum Aufzeichnen von der **Mikrofon Standardgerät** auf Ihrem Computer festlegen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="f6b1b-154">Stellen Sie sicher, dass das Mikrofon-Standardgerät als den festgelegt ist, die Sie verwenden, um Ihre Stimme erfassen möchten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="f6b1b-155">Verfügt Ihre Kopfhörer ein eingebautes Mikrofon verfügen, stellen Sie sicher, dass die Option *"Ich meine Kopfhörer wear, wechseln Sie zur Kopfhörer-mic"* eingeschaltet ist, der *Mixed Reality-Portal* Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Einrichten von immersive Kopfhörer](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="f6b1b-157">Kapitel 1: Einrichten der Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="f6b1b-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="f6b1b-158">Verwenden der *Language Understanding* Service in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="f6b1b-159">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f6b1b-160">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f6b1b-161">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f6b1b-162">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Language Understanding*, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![LUIS-Ressource erstellen](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="f6b1b-164">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="f6b1b-165">Die neue Seite auf der rechten Seite stellt eine Beschreibung des Luis-Diensts bereit.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="f6b1b-166">Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Instanz dieses Diensts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Erstellung von LUIS-Dienst – rechtliche Hinweise](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="f6b1b-168">Nachdem Sie auf Erstellen geklickt haben:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="f6b1b-169">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="f6b1b-170">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="f6b1b-171">Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *LUIS Service*, freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="f6b1b-172">Die kostenlose Zuordnung sollte mehr als ausreichend, für diesen Kurs sein.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="f6b1b-173">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f6b1b-174">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f6b1b-175">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diese Kurse) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="f6b1b-176">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="f6b1b-177">Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f6b1b-178">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f6b1b-179">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="f6b1b-180">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="f6b1b-181">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-181">Select **Create**.</span></span>

        ![Erstellen von LUIS-Dienst - Benutzereingabe](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="f6b1b-183">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="f6b1b-184">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Neue Benachrichtigung zur Azure-image](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="f6b1b-186">Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-186">Click on the notification to explore your new Service instance.</span></span>

    ![Benachrichtigung zur Erstellung einer erfolgreichen Ressource](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="f6b1b-188">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="f6b1b-189">Sie werden auf die neue Instanz der LUIS-Dienst weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Schlüssel für den Zugriff auf LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="f6b1b-191">In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, was durch die Verwendung von Subscription-Key Ihres Diensts erfolgt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="f6b1b-192">Von der *Schnellstart* Seite von Ihrer *LUIS API* service, navigieren Sie zum ersten Schritt *nehmen Sie Ihre Schlüssel*, und klicken Sie auf **Schlüssel** (Sie können auch erreichen Sie dies, indem Sie auf den blauen Link Schlüssel befindet sich im Navigationsmenü Dienste durch ein Schlüsselsymbol gekennzeichnet).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="f6b1b-193">Dadurch wird angezeigt, den Dienst *Schlüssel*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="f6b1b-194">Erstellen Sie eine Kopie eines der angezeigten Schlüssel wird, da Sie dies später in Ihr Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="f6b1b-195">In der *Service* Seite, klicken Sie auf *Language Understanding-Portal* zur Webseite umgeleitet werden, das Sie verwenden werden, um den neuen Dienst, in der LUIS-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="f6b1b-196">Kapitel 2 – Language Understanding-Portal</span><span class="sxs-lookup"><span data-stu-id="f6b1b-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="f6b1b-197">In diesem Abschnitt lernen Sie, wie Sie einer LUIS-App auf das LUIS-Portal.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f6b1b-198">Beachten Sie, die Einrichtung der *Entitäten*, *Intents*, und *Äußerungen* in diesem Kapitel wird nur der erste Schritt bei der Erstellung von Ihrem LUIS-Dienst: Sie müssen auch Erneutes Trainieren von dem Dienst mehrere Male auf, also um genauer zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="f6b1b-199">Das erneute trainieren Ihres Diensts finden Sie in der [letzte Kapitel](#chapter-12--improving-your-luis-service) dieses Kurses, also stellen Sie sicher, dass Sie die Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="f6b1b-200">Beim Erreichen der *Language Understanding-Portal*, müssen Sie möglicherweise die Anmeldung, wenn Sie noch nicht mit den gleichen Anmeldeinformationen wie Ihr Azure-Portal sind.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS-Anmeldeseite](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="f6b1b-202">Ist dies zum ersten Mal LUIS verwenden, müssen Sie einen Bildlauf zum unteren Rand der Seite "Willkommen", um zu suchen, und klicken auf die **erstellen LUIS-app** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![LUIS-app-Seite erstellen](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="f6b1b-204">Sobald Sie angemeldet sind, klicken Sie auf **"Meine apps"** (Wenn Sie nicht in diesem Abschnitt, derzeit sind).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="f6b1b-205">Klicken Sie dann auf **neue Anwendung erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-205">You can then click on **Create new app**.</span></span>

    ![LUIS - Meine apps-image](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="f6b1b-207">Geben Sie Ihrer app eine *Namen*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="f6b1b-208">Wenn Ihre app um zu eine anderen Sprache als Englisch zu verstehen, sollten Sie ändern die *Kultur* auf die entsprechende Sprache.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="f6b1b-209">Hier können Sie auch Hinzufügen einer *Beschreibung* für Ihre neue LUIS-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS - Erstellen einer neuen app](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="f6b1b-211">Sobald Sie drücken **Fertig**, geben ein die *erstellen* Ihre neue Seite *LUIS* Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="f6b1b-212">Es gibt einige wichtige Konzepte, die hier zu verstehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="f6b1b-213">*Beabsichtigte*, stellt die Methode, die nach einer Abfrage vom Benutzer aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="f6b1b-214">Ein *Absicht* möglicherweise eine oder mehrere *ENTITÄTEN*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="f6b1b-215">*Entität*, ist eine Komponente von der Abfrage, die beschreibt, Informationen zu den *Absicht*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="f6b1b-216">*Äußerungen*, sind Beispiele für Abfragen, sofern vom Entwickler, LUIS verwenden wird, um sich selbst zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="f6b1b-217">Wenn diese Konzepte nicht perfekt sind löschen, aber keine Sorge, wie in diesem Kurs klären diese weiter in diesem Kapitel.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="f6b1b-218">Beginnen Sie mit dem Erstellen der *Entitäten* zum Erstellen dieses Kurses erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="f6b1b-219">Klicken Sie auf der linken Seite der Seite auf *Entitäten*, klicken Sie dann auf **neue Entität erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Neue Entität erstellen](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="f6b1b-221">Rufen Sie die neue Entität *Farbe*, legen Sie deren Typ auf *einfache*, drücken Sie dann die **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Erstellen Sie einfache Entität - Farbe](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="f6b1b-223">Wiederholen Sie diesen Vorgang, um drei (3) Weitere Simple Entities mit dem Namen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="f6b1b-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-224">*upsize*</span></span>
    -   <span data-ttu-id="f6b1b-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-225">*downsize*</span></span>
    -   <span data-ttu-id="f6b1b-226">*target*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-226">*target*</span></span>

<span data-ttu-id="f6b1b-227">Das Ergebnis sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-227">The result should look like the image below:</span></span>

![Ergebnis der Erstellung von Entitäten](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="f6b1b-229">An diesem Punkt können Sie beginnen, erstellen *Intents*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="f6b1b-230">Löschen Sie nicht die **keine** Absicht.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="f6b1b-231">Klicken Sie auf der linken Seite der Seite auf **Intents**, klicken Sie dann auf **erstellen neue Absicht**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Erstellen Sie neue intents](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="f6b1b-233">Rufen Sie die neue *Absicht* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f6b1b-234">Dies *Absicht* Name wird verwendet, in den Code weiter unten in diesem Kurs, also am besten verwenden Sie diesen Namen exakt wie angegeben.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="f6b1b-235">Nachdem Sie den Namen, die, den Sie auf der Seite "Intents" weitergeleitet werden überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS - Intent-Elemente-Seite](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="f6b1b-237">Sie werden bemerken, dass es ein Textfeld mit dem Sie aufgefordert werden, zum Typ 5 oder mehr verschiedene *Äußerungen*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b1b-238">LUIS konvertiert-Äußerungen alle in Kleinbuchstaben.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="f6b1b-239">Fügen Sie die folgenden *Äußerung* im Textfeld für die oberen (derzeit mit dem Text *gebe Sie etwa 5-Beispiele*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="f6b1b-240">), und drücken Sie die **EINGABETASTE**:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="f6b1b-241">Sie werden feststellen, dass die neue *Äußerung* wird in einer Liste darunter angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="f6b1b-242">Fügen Sie nach dem gleichen Verfahren die folgenden sechs (6) Äußerungen ein:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="f6b1b-243">Für jede Äußerung, die Sie erstellt haben, müssen Sie ermitteln, welche Wörter von LUIS als Entitäten verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="f6b1b-244">In diesem Beispiel müssen Sie alle Farben als Bezeichnung für eine *Farbe* Entität und alle möglichen Verweis zu einem Ziel als einen *Ziel* Entität.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="f6b1b-245">Zu diesem Zweck klicken Sie auf das Wort auf *Zylinder* in der ersten Äußerung und *Ziel*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identifizieren der Äußerung Ziele](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="f6b1b-247">Klicken Sie nun auf das Wort *roten* in der ersten Äußerung und *Farbe*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identifizieren von Äußerung Entitäten](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="f6b1b-249">Die nächste Zeile darüber hinaus bezeichnen, in denen *Cube* muss eine *Ziel*, und *Schwarz* muss eine *Farbe*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="f6b1b-250">Beachten Sie auch die Verwendung der Wörter *"this"*, *"it"*, und *"dieses Objekt"*, die, daher bieten wir sind auch nicht-spezifischen Zieltypen verfügbar zu sein.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="f6b1b-251">Wiederholen Sie den oben beschriebenen Prozess aus, bis alle Äußerungen die Entitäten, die mit der Bezeichnung haben.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="f6b1b-252">Finden Sie unter dem folgenden Bild aus, wenn Sie Hilfe benötigen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="f6b1b-253">Wenn Sie Wörter werden als Entitäten geben als Bezeichnung auswählen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="f6b1b-254">Für einzelne Wörter einfach darauf klicken.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-254">For single words just click them.</span></span>
    > - <span data-ttu-id="f6b1b-255">Klicken Sie auf eine Gruppe von mindestens zwei Wörtern am Anfang, und klicken Sie dann am Ende des Satzes.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f6b1b-256">Können Sie die *Token Ansicht* Umschaltfläche Wechsel zwischen **Entitäten / Token-Ansicht**!</span><span class="sxs-lookup"><span data-stu-id="f6b1b-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="f6b1b-257">Die Ergebnisse sollten wie in den Abbildungen unten dargestellt angezeigt, die **Entitäten / Token-Ansicht**:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Token und Sichten von Entitäten](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="f6b1b-259">An diesem Punkt drücken Sie die **Train** Schaltfläche in der oberen rechten Rand der Seite, und warten Sie darauf, um Grün für den kleinen round-Indikator.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="f6b1b-260">Dies bedeutet, dass es sich bei LUIS erkennt diese Absicht erfolgreich trainiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Trainieren von LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="f6b1b-262">Als Übung für Sie erstellen eine neue Absicht namens **ChangeObjectSize**, mit den Entitäten *Ziel*, *Upsizing*, und *verkleinern*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="f6b1b-263">Fügen Sie die folgenden acht (8) Äußerungen für folgt demselben Prozess wie die vorheriger Absicht *Größe* ändern:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="f6b1b-264">Das Ergebnis sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-264">The result should be like the one in the image below:</span></span>

    ![Richten Sie die Token ChangeObjectSize / Entitäten](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="f6b1b-266">Nachdem beide Intents, **ChangeObjectColor** und **ChangeObjectSize**, erstellt wurden, und klicken Sie mit der trainiert, auf die **veröffentlichen** Schaltfläche oben auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![LUIS-Dienst veröffentlichen](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="f6b1b-268">Auf der *veröffentlichen* Seite, die Sie abschließen und Ihrer LUIS-App veröffentlichen, sodass sie von Ihrem Code zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="f6b1b-269">Legen Sie die Dropdownliste unten *veröffentlichen,* als **Produktion**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="f6b1b-270">Legen Sie die *Timezone* in die relevante Zeitzone.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="f6b1b-271">Aktivieren Sie das Kontrollkästchen **einschließen, die alle vorhergesagt beabsichtigte Ergebnisse**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="f6b1b-272">Klicken Sie auf **Veröffentlichen in den Produktionsslot**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-272">Click on **Publish to Production Slot**.</span></span>

        ![Veröffentlichungseinstellungen](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="f6b1b-274">Im Abschnitt *Ressourcen und Schlüssel*:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="f6b1b-275">Wählen Sie die Region, die Sie für die Dienstinstanz im Azure-Portal festlegen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="f6b1b-276">Sie sehen eine **Starter_Key** folgt, ignoriert.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="f6b1b-277">Klicken Sie auf **-Schlüssel hinzufügen** und fügen Sie der *Schlüssel* , dass Sie bei der Erstellung der Dienstinstanz im Azure-Portal abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="f6b1b-278">Wenn derselbe Benutzer von Azure und das LUIS-Portal angemeldet sind, erhalten Sie in den Dropdownmenüs für *Mandantenname*, *Abonnementname*, und die *Schlüssel* () verwenden möchten müssen den gleichen Namen, wie Sie sich zuvor im Azure-Portal bereitgestellt ist.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="f6b1b-279">Darunter *Endpunkt*, kopieren Sie den Endpunkt, der den Schlüssel für Sie eingefügt haben, werden Sie es in Kürze in Ihrem Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="f6b1b-280">Kapitel 3 – Einrichten der Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="f6b1b-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="f6b1b-281">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="f6b1b-282">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-282">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="f6b1b-284">Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="f6b1b-285">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="f6b1b-286">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f6b1b-287">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-287">Then, click **Create project**.</span></span>

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="f6b1b-289">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f6b1b-290">Wechseln Sie zum Bearbeiten > Voreinstellungen und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f6b1b-291">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f6b1b-292">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-292">Close the **Preferences** window.</span></span>

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="f6b1b-294">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="f6b1b-296">Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="f6b1b-297">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="f6b1b-298">Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="f6b1b-299">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="f6b1b-300">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="f6b1b-301">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="f6b1b-302">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="f6b1b-303">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="f6b1b-304">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f6b1b-305">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-305">A save window will appear.</span></span>
        
            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="f6b1b-307">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="f6b1b-309">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_LuisScene**, drücken Sie dann die **speichern**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="f6b1b-311">Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="f6b1b-312">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="f6b1b-314">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="f6b1b-315">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="f6b1b-316">**Scripting Runtime Version** muss **stabile** (.NET 3.5 entspricht).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="f6b1b-317">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="f6b1b-318">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="f6b1b-320">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="f6b1b-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-321">**InternetClient**</span></span>
        2. <span data-ttu-id="f6b1b-322">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-322">**Microphone**</span></span>

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="f6b1b-324">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="f6b1b-326">Im *Buildeinstellungen* _Unity C#_  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="f6b1b-327">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="f6b1b-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="f6b1b-328">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="f6b1b-329">Kapitel 4 – Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="f6b1b-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6b1b-330">Wenn Sie, überspringen möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importieren Sie es in Ihr Projekt als eine [benutzerdefinierten Paket ](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="f6b1b-331">Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **3D-Objekt**, Hinzufügen einer **Ebene**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Erstellen Sie eine Ebene.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="f6b1b-333">Beachten Sie, wenn Sie mit der rechten Maustaste innerhalb der *Hierarchie* erneut um weitere Objekte, erstellen Sie immer noch das letzte Objekt ausgewählt haben, das ausgewählte Objekt wird das übergeordnete Element des neuen Objekts.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="f6b1b-334">Vermeiden Sie dies mit der linken Maustaste in einen leeren Bereich innerhalb der Hierarchie, und klicken Sie dann mit der rechten Maustaste.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="f6b1b-335">Wiederholen Sie das oben stehende Verfahren, um die folgenden Objekte hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="f6b1b-336">*Kugel*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-336">*Sphere*</span></span>
    2. <span data-ttu-id="f6b1b-337">*Cylinder*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-337">*Cylinder*</span></span>
    3. <span data-ttu-id="f6b1b-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-338">*Cube*</span></span>
    4. <span data-ttu-id="f6b1b-339">*3D Text*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-339">*3D Text*</span></span>

4.  <span data-ttu-id="f6b1b-340">Der resultierende Szene *Hierarchie* sollte wie in der folgenden Abbildung:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Einrichtung der Szene-Hierarchie.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="f6b1b-342">Links klicken Sie auf die **Main Camera** um diese Option auswählen, sehen Sie sich die *Inspector-Bereich* sehen Sie die Kamera-Objekt mit allen der zugehörigen Komponenten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="f6b1b-343">Klicken Sie auf die **Add Component** Schaltfläche am Ende der *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Hinzufügen von Audio-Quelle](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="f6b1b-345">Suchen Sie nach der Komponente mit dem Namen *Audio Source*, wie oben gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="f6b1b-346">Stellen Sie außerdem sicher, dass die *transformieren* Komponente von der Main-Kamera, (0,0,0) festgelegt ist, wird dies erreichen Sie durch Drücken der **Zahnradsymbol** Symbol neben der Kamera *transformieren* Komponente auswählen und **zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="f6b1b-347">Die *transformieren* Komponente sollte dann wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="f6b1b-348">*Position* nastaven NA hodnotu **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="f6b1b-349">*Drehung* nastaven NA hodnotu **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="f6b1b-350">Für die Microsoft HoloLens, müssen Sie auch Folgendes ein, ändern die sind Teil der **Kamera** -Komponente, die auf Ihre **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="f6b1b-351">**Flags zu löschen:** Volltonfarbe entspricht.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="f6b1b-352">**Hintergrund** "Schwarz, Alpha 0" – Hex-Color: #00000000.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="f6b1b-353">Klicken Sie mit der Links auf die **Ebene** um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="f6b1b-354">In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f6b1b-355">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f6b1b-356">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-356">**X**</span></span> | <span data-ttu-id="f6b1b-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-357">**Y**</span></span>                  | <span data-ttu-id="f6b1b-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-358">**Z**</span></span> |
    | <span data-ttu-id="f6b1b-359">0</span><span class="sxs-lookup"><span data-stu-id="f6b1b-359">0</span></span>     | <span data-ttu-id="f6b1b-360">-1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-360">-1</span></span>                     | <span data-ttu-id="f6b1b-361">0</span><span class="sxs-lookup"><span data-stu-id="f6b1b-361">0</span></span>     |


10. <span data-ttu-id="f6b1b-362">Klicken Sie mit der Links auf die **Kugel** um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="f6b1b-363">In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f6b1b-364">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f6b1b-365">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-365">**X**</span></span> | <span data-ttu-id="f6b1b-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-366">**Y**</span></span>                  | <span data-ttu-id="f6b1b-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-367">**Z**</span></span> |
    | <span data-ttu-id="f6b1b-368">2</span><span class="sxs-lookup"><span data-stu-id="f6b1b-368">2</span></span>     | <span data-ttu-id="f6b1b-369">1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-369">1</span></span>                      | <span data-ttu-id="f6b1b-370">2</span><span class="sxs-lookup"><span data-stu-id="f6b1b-370">2</span></span>     |

11. <span data-ttu-id="f6b1b-371">Klicken Sie mit der Links auf die **Zylinder** um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="f6b1b-372">In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f6b1b-373">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f6b1b-374">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-374">**X**</span></span> | <span data-ttu-id="f6b1b-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-375">**Y**</span></span>                  | <span data-ttu-id="f6b1b-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-376">**Z**</span></span> |
    | <span data-ttu-id="f6b1b-377">-2</span><span class="sxs-lookup"><span data-stu-id="f6b1b-377">-2</span></span>    | <span data-ttu-id="f6b1b-378">1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-378">1</span></span>                      | <span data-ttu-id="f6b1b-379">2</span><span class="sxs-lookup"><span data-stu-id="f6b1b-379">2</span></span>     |

12. <span data-ttu-id="f6b1b-380">Klicken Sie mit der Links auf die **Cube** um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="f6b1b-381">In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="f6b1b-382">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="f6b1b-383">Transformieren - *Drehung*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="f6b1b-384">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-384">**X**</span></span> | <span data-ttu-id="f6b1b-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-385">**Y**</span></span>                   | <span data-ttu-id="f6b1b-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-386">**Z**</span></span> |  \| | <span data-ttu-id="f6b1b-387">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-387">**X**</span></span> | <span data-ttu-id="f6b1b-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-388">**Y**</span></span>                  | <span data-ttu-id="f6b1b-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-389">**Z**</span></span> |
    | <span data-ttu-id="f6b1b-390">0</span><span class="sxs-lookup"><span data-stu-id="f6b1b-390">0</span></span>     | <span data-ttu-id="f6b1b-391">1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-391">1</span></span>                       | <span data-ttu-id="f6b1b-392">4</span><span class="sxs-lookup"><span data-stu-id="f6b1b-392">4</span></span>     |  \| | <span data-ttu-id="f6b1b-393">45</span><span class="sxs-lookup"><span data-stu-id="f6b1b-393">45</span></span>    | <span data-ttu-id="f6b1b-394">45</span><span class="sxs-lookup"><span data-stu-id="f6b1b-394">45</span></span>                     | <span data-ttu-id="f6b1b-395">0</span><span class="sxs-lookup"><span data-stu-id="f6b1b-395">0</span></span>     | 

13. <span data-ttu-id="f6b1b-396">Klicken Sie mit der Links auf die **neuen Text** Objekt, um es auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="f6b1b-397">In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="f6b1b-398">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="f6b1b-399">Transformieren - *skalieren*</span><span class="sxs-lookup"><span data-stu-id="f6b1b-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="f6b1b-400">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-400">**X**</span></span> | <span data-ttu-id="f6b1b-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-401">**Y**</span></span>                  | <span data-ttu-id="f6b1b-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-402">**Z**</span></span> |  \| | <span data-ttu-id="f6b1b-403">**X**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-403">**X**</span></span> | <span data-ttu-id="f6b1b-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-404">**Y**</span></span>               | <span data-ttu-id="f6b1b-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-405">**Z**</span></span> |
    | <span data-ttu-id="f6b1b-406">-2</span><span class="sxs-lookup"><span data-stu-id="f6b1b-406">-2</span></span>    | <span data-ttu-id="f6b1b-407">6</span><span class="sxs-lookup"><span data-stu-id="f6b1b-407">6</span></span>                      | <span data-ttu-id="f6b1b-408">9</span><span class="sxs-lookup"><span data-stu-id="f6b1b-408">9</span></span>     |  \| | <span data-ttu-id="f6b1b-409">0.1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-409">0.1</span></span>   | <span data-ttu-id="f6b1b-410">0.1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-410">0.1</span></span>                 | <span data-ttu-id="f6b1b-411">0.1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-411">0.1</span></span>   | 

14. <span data-ttu-id="f6b1b-412">Änderung **Schriftgrad** in die **Text Mesh** Komponente **50**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="f6b1b-413">Ändern der *Namen* von der **Text Mesh** -Objekt **Diktat Text**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![3D-Objekt Text erstellen](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="f6b1b-415">Die Struktur der Hierarchie Bereich sollte jetzt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![mesh-Text in der Szenenansicht](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="f6b1b-417">Die endgültige Szene sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-417">The final scene should look like the image below:</span></span>

    ![Die Szenenansicht.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="f6b1b-419">Kapitel 5 – Erstellen der MicrophoneManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f6b1b-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="f6b1b-420">Das erste Skript, das Sie erstellen wollen ist die *MicrophoneManager* Klasse.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="f6b1b-421">Anschluss erstellen Sie die *LuisManager*, *Verhalten* -Klasse, und zuletzt die *bestaunen* Klasse (gerne alle diese jetzt zu erstellen, wenn es Sie behandelt werden erreichen Sie jedes Kapitel).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="f6b1b-422">Die *MicrophoneManager* -Klasse ist verantwortlich für:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="f6b1b-423">Erkennen das Aufnahmegerät, die an den Kopfhörer oder die Computer, die (je nachdem, was der Standardwert ist) angefügt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="f6b1b-424">Das Audio (Sprache) und Diktat als Zeichenfolge zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="f6b1b-425">Nachdem die Stimme angehalten wurde, senden Sie die diktatfunktion, um die *LuisManager* Klasse.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="f6b1b-426">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-426">To create this class:</span></span> 

1.  <span data-ttu-id="f6b1b-427">Mit der rechten Maustaste den *Projekt Bereich*, **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="f6b1b-428">Rufen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-428">Call the folder **Scripts**.</span></span> 

    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="f6b1b-430">Mit der **Skripts** Ordner erstellt haben, doppelklicken klicken Sie darauf, zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="f6b1b-431">Klicken Sie dann in diesem Ordner mit der rechten Maustaste, **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="f6b1b-432">Nennen Sie das Skript *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="f6b1b-433">Klicken Sie mit der Doppelklicken auf *MicrophoneManager* , öffnen Sie ihn mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="f6b1b-434">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="f6b1b-435">Klicken Sie dann fügen Sie die folgenden Variablen in der *MicrophoneManager* Klasse:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="f6b1b-436">Code für *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="f6b1b-437">Diese werden aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="f6b1b-438">Jetzt Sie die Methode, die die App zum Starten benötigen verwendet und Beenden der Sprachaufnahme und übergeben Sie sie an der *LuisManager* Klasse, die Sie in Kürze erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="f6b1b-439">Hinzufügen einer *Diktat Handler* , wenn die Stimme hält aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="f6b1b-440">Diese Methode übergibt den Diktat Text, der die *LuisManager* Klasse.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="f6b1b-441">Löschen der *Update()* Methode, da diese Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="f6b1b-442">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f6b1b-443">An diesem Punkt werden Sie feststellen, einen Fehler angezeigt werden, der *Unity-Editor-Konsole Bereich*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="f6b1b-444">Dies ist, da der Code verweist auf die *LuisManager* Klasse, die im nächsten Kapitel erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="f6b1b-445">Kapitel 6: Erstellen der LUISManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f6b1b-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="f6b1b-446">Es ist Zeit für die Sie erstellen die *LuisManager* -Klasse, die den Anruf an den Azure LUIS-Dienst wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="f6b1b-447">Der Zweck dieser Klasse wird zum Empfangen von des Diktatmodus Texts aus der *MicrophoneManager* Klasse und sendet diese an die *Azure Language Understanding-API* analysiert werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="f6b1b-448">Diese Klasse deserialisiert die *JSON* Antwort, und rufen Sie die entsprechenden Methoden der der *Verhalten* Klasse um eine Aktion auszulösen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="f6b1b-449">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-449">To create this class:</span></span> 

1.  <span data-ttu-id="f6b1b-450">Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f6b1b-451">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f6b1b-452">Nennen Sie das Skript *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="f6b1b-453">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="f6b1b-454">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="f6b1b-455">Werden zunächst erstellen Sie drei Klassen **in** der *LuisManager* Klasse (innerhalb derselben Skriptdatei, über die *Start()* Methode), wird das deserialisierte darstellen JSON-Antwort von Azure.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="f6b1b-456">Fügen Sie die folgenden Variablen in der *LuisManager* Klasse:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="f6b1b-457">Stellen Sie sicher, platzieren Sie Ihr LUIS-Dienstendpunkt im (die müssen Sie von Ihrem LUIS-Portal).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="f6b1b-458">Code für die *Awake()* Methode muss jetzt hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="f6b1b-459">Diese Methode wird aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="f6b1b-460">Jetzt Sie diese Anwendung verwendet wird benötigen, um das Diktieren von empfangenen senden die Methoden der *MicrophoneManager* -Klasse *LUIS*, empfangen und Deserialisieren die Antwort.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="f6b1b-461">Wenn der Wert der Absicht und zugehörigen Entitäten ermittelt wurde, werden sie mit der Instanz von übergeben die *Verhalten* Klasse, um die beabsichtigte Aktion auslösen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="f6b1b-462">Erstellen Sie eine neue Methode namens *AnalyseResponseElements()* liest, die die resultierende *AnalysedQuery* und ermitteln Sie die Entitäten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="f6b1b-463">Nachdem diese Entitäten ermittelt wurden, werden sie mit der Instanz von übergeben die *Verhalten* Klasse, um in den Aktionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognised intent, read the entities name
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
    > <span data-ttu-id="f6b1b-464">Löschen der *Start()* und *Update()* Methoden, da diese Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="f6b1b-465">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b1b-466">An diesem Punkt werden Sie feststellen, mehrere Fehler angezeigt werden, der *Unity-Editor-Konsole Bereich*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="f6b1b-467">Dies ist, da der Code verweist auf die *Verhalten* Klasse, die im nächsten Kapitel erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="f6b1b-468">Kapitel 7 – Erstellen der Verhalten-Klasse</span><span class="sxs-lookup"><span data-stu-id="f6b1b-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="f6b1b-469">Die *Verhalten* Klasse löst die Aktionen, die mit den Entitäten, die bereitgestellt werden, indem die *LuisManager* Klasse.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="f6b1b-470">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-470">To create this class:</span></span> 

1.  <span data-ttu-id="f6b1b-471">Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f6b1b-472">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f6b1b-473">Nennen Sie das Skript *Verhalten*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="f6b1b-474">Klicken Sie mit der Doppelklicken auf das Skript aus, um sie zu öffnen *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="f6b1b-475">Klicken Sie dann fügen Sie die folgenden Variablen in der *Verhalten* Klasse:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="f6b1b-476">Hinzufügen der *Awake()* Methodencode.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="f6b1b-477">Diese Methode wird aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="f6b1b-478">Die folgenden Methoden werden aufgerufen, indem die *LuisManager* Klasse (die Sie zuvor erstellt haben), um zu bestimmen, welches Objekt das Ziel der Abfrage ist, und lösen Sie dann auf die entsprechende Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="f6b1b-479">Hinzufügen der *FindTarget()* Methode, um zu bestimmen, welche die *"gameobjects"* ist das Ziel des aktuellen Intent.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="f6b1b-480">Diese Methode wird standardmäßig das Ziel der *"gameobject"* wird "gazed", wenn keine explizite Ziel in den Entitäten definiert ist.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > <span data-ttu-id="f6b1b-481">Löschen der *Start()* und *Update()* Methoden, da diese Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="f6b1b-482">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="f6b1b-483">Kapitel 8 – erstellen Sie die Blicke-Klasse</span><span class="sxs-lookup"><span data-stu-id="f6b1b-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="f6b1b-484">Ist die letzte Klasse, die Sie zum Abschließen dieser app müssen die *bestaunen* Klasse.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="f6b1b-485">Diese Klasse aktualisiert den Verweis auf die *"gameobject"* derzeit in der visuellen Fokus des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="f6b1b-486">Zum Erstellen dieser Klasse:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-486">To create this Class:</span></span> 

1.  <span data-ttu-id="f6b1b-487">Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f6b1b-488">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f6b1b-489">Nennen Sie das Skript *bestaunen*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="f6b1b-490">Klicken Sie mit der Doppelklicken auf das Skript aus, um sie zu öffnen *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="f6b1b-491">Fügen Sie den folgenden Code für diese Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="f6b1b-492">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="f6b1b-493">Kapitel 9 – der Szene Einrichtung</span><span class="sxs-lookup"><span data-stu-id="f6b1b-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="f6b1b-494">Ziehen Sie zum Abschließen der Installation von der Szene jedes Skript, das Sie aus dem Ordner "Scripts", erstellt haben die **Main Camera** -Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="f6b1b-495">Wählen Sie die **Main Camera** und sehen Sie sich die *Inspektor Bereich*, Sie sollten jedes Skript angezeigt, die Sie hinzugefügt haben, und Sie werden feststellen, dass es Parameter für jedes Skript, die noch festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Das Festlegen der Kamera-Verweis-Ziele.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="f6b1b-497">Um diese Parameter richtig festzulegen, gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="f6b1b-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="f6b1b-499">Von der *Hierarchie Bereich*, ziehen Sie die **Diktat Text** -Objekt in der **Diktat Text** im Wertefeld des Parameters.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="f6b1b-500">*Verhalten*, aus der *Hierarchie Bereich*:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="f6b1b-501">Ziehen Sie die **Kugel** -Objekt in der *Kugel* Sie im Verweis-Ziel.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="f6b1b-502">Ziehen Sie die **Zylinder** in die *Zylinder* Sie im Verweis-Ziel.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="f6b1b-503">Ziehen Sie die **Cube** in die *Cube* Sie im Verweis-Ziel.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="f6b1b-504">*Bestaunen*:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-504">*Gaze*:</span></span>

        - <span data-ttu-id="f6b1b-505">Legen Sie die *bestaunen maximaler Abstand* zu **300** (sofern es nicht bereits der Fall ist).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="f6b1b-506">Das Ergebnis sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-506">The result should look like the image below:</span></span>

    ![Anzeigen der Ziele der Kamera-Verweis, jetzt festgelegt werden.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="f6b1b-508">Kapitel 10 – Test im Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="f6b1b-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="f6b1b-509">Testen Sie, dass die Szene Einrichtung ordnungsgemäß implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="f6b1b-510">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-510">Ensure that:</span></span>

-   <span data-ttu-id="f6b1b-511">Alle Skripts werden angefügt, um die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="f6b1b-512">Alle Felder in der *Kamera Inspector-Hauptbereich* ordnungsgemäß zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="f6b1b-513">Drücken Sie die **spielen** Schaltfläche der *Unity-Editor*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="f6b1b-514">Die App muss innerhalb der angeschlossenen, immersive Kopfhörer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="f6b1b-515">Probieren Sie einige äußerungen, z. B. ein:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="f6b1b-516">Wenn einen Fehler in der Unity-Konsole zum Ändern der Standard-Audiogeräts angezeigt wird, funktioniert die Szene möglicherweise nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="f6b1b-517">Dies ist aufgrund der Art, die das mixed Reality-Portal integrierte Mikrofone für Headsets behandelt, die sie verfügen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="f6b1b-518">Wenn Sie diese Fehlermeldung angezeigt, einfach die Szene zu beenden und neu zu starten und als funktionieren sollte erwartet.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="f6b1b-519">Kapitel 11 – Build herunter, und Laden Sie die UWP-Lösung</span><span class="sxs-lookup"><span data-stu-id="f6b1b-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="f6b1b-520">Nachdem Sie sichergestellt haben, dass die Anwendung im Unity-Editor ausgeführt wird, können Sie zum Erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="f6b1b-521">So erstellen Sie:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-521">To Build:</span></span>

1.  <span data-ttu-id="f6b1b-522">Speichern Sie durch Klicken auf die aktuelle Szene **Datei > Speichern**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="f6b1b-523">Wechseln Sie zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="f6b1b-524">Aktivieren Sie das Kontrollkästchen namens **Unity C# Projekte** (nützlich für das Anzeigen und Debuggen von Code aus, nachdem das UWP-Projekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="f6b1b-525">Klicken Sie auf **öffnen Szenen hinzufügen**, klicken Sie dann auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Fenster "Einstellungen" erstellen](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="f6b1b-527">Sie werden aufgefordert werden, um den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="f6b1b-528">Erstellen Sie eine *erstellt* Ordner, und erstellen Sie einen anderen Ordner in diesem Ordner mit einem entsprechenden Namen Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="f6b1b-529">Klicken Sie auf **Ordner auswählen** um den Build an diesem Speicherort zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="f6b1b-530">![Erstellen Sie Ordner "Builds"](images/AzureLabs-Lab3-44.png)
    ![wählen erstellt Ordner](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="f6b1b-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="f6b1b-531">Nachdem Unity die erstellen (es kann einige Zeit dauern) abgeschlossen ist, sollten sie zu öffnen eine **Datei-Explorer** Fenster am Speicherort des Builds.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="f6b1b-532">So stellen Sie auf dem lokalen Computer bereit:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="f6b1b-533">In *Visual Studio*, öffnen Sie die Projektmappendatei, die in der Erstellung der [vorhergehenden Kapitel](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="f6b1b-534">In der **Projektmappenplattform**Option **X86**, **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="f6b1b-535">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="f6b1b-536">Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f6b1b-537">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f6b1b-538">Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f6b1b-539">Stellen Sie sicher **Entwicklermodus** ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Bereitstellen der App](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="f6b1b-541">Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="f6b1b-542">Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="f6b1b-543">Nachdem gestartet, die App fordert Sie zum Autorisieren des Zugriffs auf die _Mikrofon_.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="f6b1b-544">Verwenden der *Motion-Controller*, oder *Spracheingabe*, oder die *Tastatur* , drücken die **Ja** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="f6b1b-545">Kapitel 12 – verbessern Ihr LUIS-Dienst</span><span class="sxs-lookup"><span data-stu-id="f6b1b-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="f6b1b-546">In diesem Kapitel ist außerordentlich wichtig, und möglicherweise zu durchlaufen, die auf mehrere Male auf, werden müssen, verhindern die Genauigkeit des LUIS-Diensts zu verbessern: Stellen Sie sicher, diese durchführen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="f6b1b-547">Um den Grad des Verständnisses zu, die von LUIS bereitgestellte zu verbessern, müssen Sie neue äußerungen erfassen und diese verwenden, um Ihrem LUIS-App erneut zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="f6b1b-548">Beispielsweise können Sie trainiert haben, LUIS, verstehen "Increase" und "Upsizing", aber empfehlenswert Sie nicht Ihrer app Wörter wie "Vergrößern" auch wichtig zu wissen?</span><span class="sxs-lookup"><span data-stu-id="f6b1b-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="f6b1b-549">Sobald Sie Ihre Anwendung einige Male verwendet haben, werden alle Elemente, die Sie gesagt haben, die von LUIS gesammelt und in das LUIS-PORTAL verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="f6b1b-550">Wechseln Sie zu Ihrem portalanwendung dieses [LINK](https://www.luis.ai/home), und anmelden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="f6b1b-551">Wenn Sie sich mit Ihren MS Credentials angemeldet sind, klicken Sie auf Ihre *Anwendungsnamen*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="f6b1b-552">Klicken Sie auf die **überprüfen Sie die Endpunkt-äußerungen** Schaltfläche auf der linken Seite der Seite.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Überprüfen Sie die Äußerungen](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="f6b1b-554">Ihnen wird eine Liste von Äußerungen angezeigt werden, die von Ihrer mixed Reality-Anwendung zu LUIS gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Liste von Äußerungen](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="f6b1b-556">Sie sehen einige hervorgehobene *Entitäten*.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="f6b1b-557">Durch jedes markierten Worts mit der Maus, können jede Äußerung überprüfen und bestimmen, welche die Entität wurde erkannt richtig, die Entitäten falsch sind und welche die Entitäten werden ausgelassen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="f6b1b-558">Im obigen Beispiel ergab, dass das Wort "Spear" als Ziel, daher wurden hervorgehoben hatte es notwendig, korrigieren Sie die Fehler, was durchgeführt wird, indem Sie mit dem Mauszeiger auf das Wort mit der Maus und auf **Remove Label**.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="f6b1b-559">![Überprüfen Sie die äußerungen](images/AzureLabs-Lab3-49.png)
![Bezeichnungsbilds entfernen](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="f6b1b-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="f6b1b-560">Wenn Sie Äußerungen, die völlig falsch sind finden, können Sie sie löschen mit der **löschen** Schaltfläche auf der rechten Seite des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Löschen Sie die falsche äußerungen](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="f6b1b-562">Oder wenn Sie glauben, dass LUIS korrekt der Äußerung interpretiert hat, können Sie ihn besser verstehen zu überprüfen, indem Sie mit der **hinzufügen, ausgerichtet Absicht** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Ausgerichtete Intent hinzufügen](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="f6b1b-564">Nachdem Sie alle angezeigten Äußerungen sortiert haben, versuchen Sie es aus, und Laden Sie die Seite, um festzustellen, ob mehr verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="f6b1b-565">Es ist sehr wichtig, diesen Vorgang so oft wie möglich, verbessern Ihre Kenntnisse der Anwendung zu wiederholen.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="f6b1b-566">**Viel Spass!**</span><span class="sxs-lookup"><span data-stu-id="f6b1b-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="f6b1b-567">Der fertigen LUIS integrierten Anwendung</span><span class="sxs-lookup"><span data-stu-id="f6b1b-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="f6b1b-568">Herzlichen Glückwunsch, Sie eine mixed Reality-app, die nutzt Azure Language Understanding Intelligence Service, um zu verstehen, was ein Benutzer angezeigt wird, und Nutzen dieser Informationen erstellt.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f6b1b-570">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="f6b1b-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f6b1b-571">Übung 1</span><span class="sxs-lookup"><span data-stu-id="f6b1b-571">Exercise 1</span></span>

<span data-ttu-id="f6b1b-572">Bei der Verwendung dieser Anwendungsprogramms können Sie feststellen, dass wenn Sie sich das Objekt Bodenfläche bestaunen und bitten Sie dessen Farbe zu ändern, wird es dies tun.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="f6b1b-573">Können Sie Sie, wie Sie Ihrer Anwendung ändern der Farbe Floor arbeiten?</span><span class="sxs-lookup"><span data-stu-id="f6b1b-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f6b1b-574">Übung 2</span><span class="sxs-lookup"><span data-stu-id="f6b1b-574">Exercise 2</span></span>

<span data-ttu-id="f6b1b-575">Versuchen Sie es erweitern die LUIS und App-Funktionen, zusätzliche Funktionen für Objekte in der Szene hinzugefügt; als Beispiel erstellen Sie neue Objekte an die Blicke Trefferpunkts, je nachdem was der Benutzer, sagt aus, und klicken Sie dann in der Lage, diese Objekte zusammen mit der aktuellen szeneobjekte, mit den vorhandenen Befehlen verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
