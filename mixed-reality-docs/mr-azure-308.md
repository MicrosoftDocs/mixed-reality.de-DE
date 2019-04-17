---
title: MR und Azure-308 - Geräteübergreifende Benachrichtigungen
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Notification Hubs, Azure Functions und Azure Storage und Tabellen innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorial, api, Notification, Funktionen, Tabellen, benachrichtigungshubs, Hololens, immersive vr
ms.openlocfilehash: ed56c936a0498b6e0ac804da15a2c6ec98239d0c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604784"
---
>[!NOTE]
><span data-ttu-id="db9bc-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="db9bc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="db9bc-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="db9bc-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="db9bc-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="db9bc-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="db9bc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="db9bc-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="db9bc-110">MR und Azure-308: Geräteübergreifende Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="db9bc-110">MR and Azure 308: Cross-device notifications</span></span>

![Endprodukt-starten](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="db9bc-112">In diesem Kurs lernen Sie, wie eine mixed Reality-Anwendung mit Azure Notification Hubs, Azure-Tabellen und Azure Functions Notification Hubs-Funktionen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="db9bc-113">**Azure Notification Hubs** ist ein Microsoft-Dienst, wodurch Entwicklern, gezielte und personalisierte Pushbenachrichtigungen an jede Plattform, die alle Rahmen in der Cloud zu senden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="db9bc-114">Diese kann effektiv ermöglichen es Entwicklern, für die Kommunikation mit dem Endbenutzer, oder Sie können auch die Kommunikation zwischen verschiedenen Anwendungen, je nach Szenario.</span><span class="sxs-lookup"><span data-stu-id="db9bc-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="db9bc-115">Weitere Informationen finden Sie auf die **Azure Notification Hubs** [Seite](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span><span class="sxs-lookup"><span data-stu-id="db9bc-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="db9bc-116">**Azure Functions** ist ein Microsoft-Dienst, die Entwickler kleine Teile des Codes ausgeführt werden kann, "Funktionen", in Azure.</span><span class="sxs-lookup"><span data-stu-id="db9bc-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="db9bc-117">Dadurch wird eine Möglichkeit zum Delegieren der Arbeit an Ihrer lokalen Anwendung, die viele Vorteile haben kann, anstatt die Cloud.</span><span class="sxs-lookup"><span data-stu-id="db9bc-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="db9bc-118">**Azure Functions** unterstützt verschiedene Entwicklungssprachen, darunter C\#, F\#, Node.js, Java und PHP.</span><span class="sxs-lookup"><span data-stu-id="db9bc-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="db9bc-119">Weitere Informationen finden Sie auf die **Azure Functions** [Seite](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="db9bc-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="db9bc-120">**Azure-Tabellen** wird ein Microsoft-Cloud-Dienst, der Entwickler strukturierte nicht-SQL-Daten in der Cloud speichern zu können, so problemlos eine beliebige Stelle.</span><span class="sxs-lookup"><span data-stu-id="db9bc-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="db9bc-121">Der Dienst in Kombination mit ein schemalosen Design, sodass für die Entwicklung von Tabellen, bei Bedarf bietet und somit ist sehr flexibel.</span><span class="sxs-lookup"><span data-stu-id="db9bc-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="db9bc-122">Weitere Informationen finden Sie auf die **Azure-Tabellen** [Seite](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="db9bc-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="db9bc-123">Nach Abschluss dieses Kurses, haben Sie eine mixed Reality immersive Kopfhörer-Anwendung, und eine Desktop-PC-Anwendung, die für die folgenden Aufgaben werden können:</span><span class="sxs-lookup"><span data-stu-id="db9bc-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="db9bc-124">Die app von Desktop-PC kann sich der Benutzer zum Verschieben eines Objekts in einem 2D-Bereich (X und Y), mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="db9bc-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="db9bc-125">Das Verschieben von Objekten innerhalb der PC-app in die Cloud mithilfe von JSON, die in Form einer Zeichenfolge, enthält die Objekt-ID, Typ, gesendet und Transformieren von Informationen (X- und Y-Koordinaten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="db9bc-126">Mixed Reality-app, die eine identische Szene an die desktop-app verfügt, erhalten Benachrichtigungen in Bezug auf die Bewegung des Objekts, von Notification Hubs-Dienst (die gerade von der Desktop-PC-app aktualisiert wurde).</span><span class="sxs-lookup"><span data-stu-id="db9bc-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="db9bc-127">Nach dem Empfang einer benachrichtigungs, die die Objekt-ID, Typ und Transformationsinformationen enthält, wird der mixed Reality-app die empfangene Informationen gelten für eine eigene Szene.</span><span class="sxs-lookup"><span data-stu-id="db9bc-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="db9bc-128">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="db9bc-129">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="db9bc-130">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="db9bc-131">Dieser Kurs ist eine eigenständige Tutorials, das aller anderen Mixed Reality-Labs nicht direkt betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="db9bc-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="db9bc-132">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="db9bc-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="db9bc-133">Kurs</span><span class="sxs-lookup"><span data-stu-id="db9bc-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="db9bc-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="db9bc-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="db9bc-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="db9bc-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="db9bc-136">MR und Azure-308: Geräteübergreifende Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="db9bc-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="db9bc-137">✔️</span><span class="sxs-lookup"><span data-stu-id="db9bc-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="db9bc-138">✔️</span><span class="sxs-lookup"><span data-stu-id="db9bc-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="db9bc-139">Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="db9bc-140">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="db9bc-141">Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db9bc-142">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="db9bc-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="db9bc-143">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="db9bc-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="db9bc-144">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="db9bc-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="db9bc-145">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="db9bc-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="db9bc-146">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="db9bc-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="db9bc-147">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="db9bc-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="db9bc-148">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="db9bc-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="db9bc-149">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="db9bc-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="db9bc-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="db9bc-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="db9bc-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="db9bc-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="db9bc-152">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="db9bc-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="db9bc-153">Zugriff auf das Internet für die Einrichtung von Azure und den Zugriff auf Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="db9bc-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="db9bc-154">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="db9bc-154">Before you start</span></span>

- <span data-ttu-id="db9bc-155">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="db9bc-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="db9bc-156">Sie müssen den Besitzer für Ihr Microsoft-Entwicklerportal und Ihre App-Registrierungsportal sein, andernfalls müssen Sie nicht über die Berechtigung zum Zugriff auf die app im [Kapitel 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="db9bc-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="db9bc-157">Kapitel 1: Erstellen einer Anwendung im Microsoft Developer-Portal</span><span class="sxs-lookup"><span data-stu-id="db9bc-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="db9bc-158">Verwenden der **Azure Notification Hubs** -Dienst Sie benötigen zum Erstellen einer Anwendung im Microsoft Developer-Portal, wie Ihre Anwendung registriert werden, sodass gesendet und Empfangen von Benachrichtigungen werden können, benötigen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="db9bc-159">Melden Sie sich bei der [Microsoft-Entwicklerportal](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="db9bc-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="db9bc-160">Sie müssen bei Ihrem Microsoft Account anmelden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="db9bc-161">Klicken Sie auf dem Dashboard auf **Erstellen einer neuen app**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Erstellen einer app](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="db9bc-163">Ein Popupfenster wird angezeigt, in dem Sie einen Namen für Ihre neue app reservieren möchten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="db9bc-164">Fügen Sie im Textfeld einen passenden Namen; Wenn der ausgewählte Name verfügbar ist, wird ein Tick rechts neben dem Textfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="db9bc-165">Nachdem Sie einen verfügbaren Namen eingefügt haben, klicken Sie auf die **Produktname reservieren** Schaltfläche unten links auf der das Popup.</span><span class="sxs-lookup"><span data-stu-id="db9bc-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![ein Name der Reverse-](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="db9bc-167">Während die app nun erstellt ist sind Sie bereit sind, finden Sie im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="db9bc-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="db9bc-168">Kapitel 2: Ihre neuen apps-Anmeldeinformationen abrufen</span><span class="sxs-lookup"><span data-stu-id="db9bc-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="db9bc-169">Melden Sie sich bei der App-Registrierungsportal, in dem Ihre neue app aufgeführt, und rufen Sie die Anmeldeinformationen, die für Setup verwendet werden, werden die **Notification Hubs-Dienst** innerhalb der **Azure-Portal**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="db9bc-170">Navigieren Sie zu der [App-Registrierungsportal](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="db9bc-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![App-registrierungsportal](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="db9bc-172">Sie müssen Ihr Microsoft Account, die Anmeldung verwenden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="db9bc-173">Dies **müssen** werden von der Microsoft-Account mit denen Sie in der vorherigen [Kapitel](#chapter-1---create-an-application-on-the-microsoft-developer-portal), mit dem Windows Store Developer-Portal.</span><span class="sxs-lookup"><span data-stu-id="db9bc-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="db9bc-174">Sehen Sie Ihre app unter der **meiner Anwendungen** Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="db9bc-175">Wenn Sie ihn gefunden haben, klicken Sie darauf, und Sie gelangen zu einer neuen Seite, die die app verfügt über Name und **Registrierung**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![Ihre neu registrierte app](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="db9bc-177">Führen Sie einen Bildlauf nach unten der Registrierungsseite finden Ihre **Anwendungsgeheimnisse** Abschnitt und der **Paket-SID** für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="db9bc-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="db9bc-178">Kopieren Sie beide für die Verwendung bei der Einrichtung der **Azure Notification Hubs-Dienst** im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="db9bc-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![geheimer Anwendungsschlüssel](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="db9bc-180">Kapitel 3: Einrichten von Azure-Portal: Erstellen von Notification Hubs-Dienst</span><span class="sxs-lookup"><span data-stu-id="db9bc-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="db9bc-181">Mit Ihren apps-Anmeldeinformationen abgerufen, Sie müssen zum Azure-Portal zu wechseln, in dem Sie eine Azure Notification Hubs-Dienst erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="db9bc-182">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="db9bc-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="db9bc-183">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="db9bc-184">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="db9bc-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="db9bc-185">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach **Benachrichtigungs-Hub**, und klicken Sie auf ***EINGABETASTE***.</span><span class="sxs-lookup"><span data-stu-id="db9bc-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![Suchen Sie nach der benachrichtigungs-hub](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="db9bc-187">Das Wort ***neu*** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="db9bc-188">Die neue Seite bietet eine Beschreibung der *Notification Hubs* Service.</span><span class="sxs-lookup"><span data-stu-id="db9bc-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="db9bc-189">Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Erstellen von Notification Hubs-Instanz](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="db9bc-191">Nachdem Sie auf geklickt haben ***erstellen***:</span><span class="sxs-lookup"><span data-stu-id="db9bc-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="db9bc-192">Fügen Sie dem gewünschten Namen für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="db9bc-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="db9bc-193">Geben Sie einen **Namespace** die Sie dieser app zugeordnet werden können.</span><span class="sxs-lookup"><span data-stu-id="db9bc-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="db9bc-194">Wählen Sie eine **Speicherort.**</span><span class="sxs-lookup"><span data-stu-id="db9bc-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="db9bc-195">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="db9bc-196">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="db9bc-197">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="db9bc-198">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="db9bc-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="db9bc-199">Wählen Sie einen geeigneten **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="db9bc-200">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="db9bc-201">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="db9bc-201">Select **Create**.</span></span>

        ![Geben Sie-Dienstdetails](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="db9bc-203">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="db9bc-204">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Benachrichtigung](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="db9bc-206">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="db9bc-207">Sie gelangen in die neue **Benachrichtigungs-Hub** Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="db9bc-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![zu Ressource wechseln](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="db9bc-209">Klicken Sie auf der Seite "Übersicht", in der Mitte der Seite, auf **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="db9bc-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="db9bc-210">Der Bereich auf der rechten Seite ändert sich in zeigen zwei Textfelder, die erforderlich sind Ihre **Paket-SID** und **Sicherheitsschlüssel**, aus der app, die Sie zuvor eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![neu erstellte Hubs-Dienst](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="db9bc-212">Nachdem Sie die Details in die richtigen Felder kopiert haben, klicken Sie auf **speichern**, und Sie erhalten eine Benachrichtigung auf, wenn es sich bei den Notification Hub erfolgreich aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="db9bc-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Notieren Sie sich die Informationen zur Sicherheit](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="db9bc-214">Kapitel 4: Einrichten von Azure-Portal: Erstellen der Tabellendienst</span><span class="sxs-lookup"><span data-stu-id="db9bc-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="db9bc-215">Nach dem Erstellen Ihrer Instanz von Notification Hubs-Dienst an, navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie ein Azure-Tabellen-Dienst durch Erstellen einer Speicherressource erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="db9bc-216">Wenn nicht bereits angemeldet, melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="db9bc-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="db9bc-217">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach **Speicherkonto**, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="db9bc-218">Das Wort ***neu*** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="db9bc-219">Wählen Sie **Speicherkonto – Blob, Datei, Tabelle, Warteschlange** aus der Liste.</span><span class="sxs-lookup"><span data-stu-id="db9bc-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Suchen Sie nach dem Storage-Konto](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="db9bc-221">Die neue Seite bietet eine Beschreibung der **Speicherkonto** Service.</span><span class="sxs-lookup"><span data-stu-id="db9bc-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="db9bc-222">Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Instanz dieses Diensts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="db9bc-224">Nachdem Sie auf geklickt haben **erstellen**, wird ein Panel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="db9bc-225">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz (müssen Kleinbuchstaben sein).</span><span class="sxs-lookup"><span data-stu-id="db9bc-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="db9bc-226">Für **Bereitstellungsmodell**, klicken Sie auf **RM**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="db9bc-227">Für **Kontoart**, wählen Sie im Dropdownmenü mit **Speicher (Allgemein v1)**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="db9bc-228">Wählen Sie einen geeigneten **Speicherort**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="db9bc-229">Für die **Replikation** wählen Sie im Dropdownmenü **Read-Access-georedundanter Speicher (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="db9bc-230">Für **Leistung**, klicken Sie auf **Standard**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="db9bc-231">In der **sichere Übertragung erforderlich** wählen Sie im Abschnitt **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="db9bc-232">Von der **Abonnement** im Dropdownmenü ein entsprechendes Abonnement auswählen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="db9bc-233">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="db9bc-234">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="db9bc-235">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="db9bc-236">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="db9bc-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="db9bc-237">Lassen Sie **virtuelle Netzwerke** als **deaktiviert** ist dies eine Option für Sie.</span><span class="sxs-lookup"><span data-stu-id="db9bc-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="db9bc-238">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-238">Click **Create**.</span></span>

        ![Geben Sie im Storage-details](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="db9bc-240">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="db9bc-241">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="db9bc-242">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-242">Click on the notifications to explore your new Service instance.</span></span>

    ![neue Speicher-Benachrichtigung](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="db9bc-244">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="db9bc-245">Sie werden auf Ihre neue Übersichtsseite für den Speicherdienst Instanz weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![zu Ressource wechseln](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="db9bc-247">Klicken Sie auf der Seite "Übersicht" auf der rechten Seite auf **Tabellen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="db9bc-248">Der Bereich auf der rechten Seite wird geändert, um anzugeben der **Tabellendienst** Informationen, bei dem Sie eine neue Tabelle hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="db9bc-249">Durch Klicken auf die **+** **Tabelle** Schaltfläche auf der linken oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="db9bc-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Öffnen von Tabellen](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="db9bc-251">Eine neue Seite wird angezeigt, in dem Sie eingeben müssen, eine **Tabellenname**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="db9bc-252">Dies ist der Name, den Sie verwenden, um auf die Daten in Ihrer Anwendung in späteren Kapiteln verweisen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="db9bc-253">Fügen Sie einen geeigneten Namen ein, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-253">Insert an appropriate name and click **OK**.</span></span>

    ![Erstellen einer neuen Tabelle](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="db9bc-255">Sobald die neue Tabelle erstellt wurde, Sie werden in finden Sie unter den **Tabellendienst** Seite (unten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![neue Tabelle](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="db9bc-257">Kapitel 5: Abschließen der Azure-Tabelle in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="db9bc-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="db9bc-258">Nachdem Ihre **Tabellendienst** Storage-Konto eingerichtet haben, ist es Zeit zum Hinzufügen von Daten, die zum Speichern und Abrufen von Informationen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="db9bc-259">Die Bearbeitung Ihrer Tabellen kann über erfolgen **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="db9bc-260">Open **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="db9bc-261">Klicken Sie im Menü auf **Ansicht > Cloud-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-261">From the menu, click **View > Cloud Explorer**.</span></span>

    ![Öffnen Sie den Cloud-explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="db9bc-263">Die **Cloud-Explorer** öffnet als angedockte Element (Geduld, Laden von Zeit in Anspruch).</span><span class="sxs-lookup"><span data-stu-id="db9bc-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="db9bc-264">Wenn das Abonnement, das Sie zum Erstellen verwendet Ihre *Speicherkonten* ist nicht sichtbar ist, sicherzustellen, dass Sie:</span><span class="sxs-lookup"><span data-stu-id="db9bc-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="db9bc-265">Angemeldet um dasselbe Konto wie diejenige aus, die Sie für das Azure-Portal verwendet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="db9bc-266">Ihr Abonnement aus der Konto-Verwaltungsseite (möglicherweise müssen einen Filter aus den Einstellungen Ihres Kontos anwenden) ausgewählt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Suchen Sie nach Abonnement](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="db9bc-268">Ihre Azure-Cloud-Dienste werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="db9bc-269">Suchen **Speicherkonten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Öffnen Sie Storage-Konten](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="db9bc-271">Nach der Kategorie erweitert ist, das neu erstellte **Speicherkonto** verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="db9bc-272">Klicken Sie auf den Pfeil auf der linken Seite des Speichers, und klicken Sie dann nach, die erweitert wird, finden **Tabellen** , und klicken Sie auf den Pfeil neben der, dass zum Anzeigen der **Tabelle** Sie im letzten Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="db9bc-273">Klicken Sie mit der Doppelklicken auf Ihre **Tabelle**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-273">Double click your **Table**.</span></span>

    ![Öffnen Sie die Tabelle der Szene-Objekte](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="db9bc-275">Die Tabelle wird in der Mitte des Ihrer Visual Studio-Fenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="db9bc-276">Klicken Sie auf das Tabellensymbol "mit der **+** (plus) auf.</span><span class="sxs-lookup"><span data-stu-id="db9bc-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="db9bc-278">Ein Fenster wird aufgefordert wird angezeigt, Sie *Entität hinzufügen*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="db9bc-279">Sie erstellen drei Entitäten insgesamt, jeweils mit mehreren Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="db9bc-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="db9bc-280">Sie werden feststellen, dass *PartitionKey* und *RowKey* werden soll, bereits bereitgestellt ist, als diese von der Tabelle verwendet werden, um Ihre Daten zu finden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![Partitions-und zeilenschlüssels](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="db9bc-282">Update der *Wert* von der **PartitionKey** und **RowKey** wie folgt (Beachten Sie hierzu für jede Zeile Eigenschaft Sie hinzugefügt haben, jedoch jedes Mal erhöht RowKey):</span><span class="sxs-lookup"><span data-stu-id="db9bc-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![Fügen Sie die richtigen Werte](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="db9bc-284">Klicken Sie auf **Eigenschaft hinzufügen** zum Hinzufügen von zusätzlicher Zeilen von Daten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="db9bc-285">Stellen Sie Ihre erste leere Tabelle entspricht der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="db9bc-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="db9bc-286">Klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-286">Click **OK** when you are finished.</span></span>

    ![Klicken Sie auf ok, wenn fertig](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="db9bc-288">Stellen Sie sicher, dass Sie geändert haben die **Typ** von der **X**, **Y**, und **Z**, Einträge **doppelte**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="db9bc-289">Beachten Sie, dass die Tabelle jetzt über eine Zeile mit Daten verfügt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="db9bc-290">Klicken Sie auf die **+** (Pluszeichen) erneut aus, um eine andere Entität hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![erste Zeile](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="db9bc-292">Erstellen Sie eine zusätzliche Eigenschaft, und legen Sie dann die Werte der neuen Entität mit den unten dargestellten übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Hinzufügen von Cubes](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="db9bc-294">Wiederholen Sie den letzten Schritt zum Hinzufügen einer anderen Entität.</span><span class="sxs-lookup"><span data-stu-id="db9bc-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="db9bc-295">Legen Sie die Werte für diese Entität unten dargestellt ein.</span><span class="sxs-lookup"><span data-stu-id="db9bc-295">Set the values for this entity to those shown below.</span></span>

    ![Hinzufügen von Zylinder](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="db9bc-297">Die Tabelle sollte jetzt wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-297">Your table should now look like the one below.</span></span>

    ![Tabelle](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="db9bc-299">In diesem Kapitel wurde abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-299">You have completed this Chapter.</span></span> <span data-ttu-id="db9bc-300">Stellen Sie sicher zu speichern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="db9bc-301">Kapitel 6: erstellen eine Azure-Funktions-App</span><span class="sxs-lookup"><span data-stu-id="db9bc-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="db9bc-302">Erstellen Sie eine Azure-Funktionen-App, die aufgerufen wird, von der Desktop-Anwendung zum Aktualisieren der **Tabelle** Dienst, und senden eine Benachrichtigung über die **Benachrichtigungs-Hub**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="db9bc-303">Zunächst müssen Sie eine Datei zu erstellen, mit dem Ihre Azure-Funktion, die Bibliotheken zu laden, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="db9bc-304">Open **Editor** (drücken Sie Windows-Taste und geben Sie Notepad).</span><span class="sxs-lookup"><span data-stu-id="db9bc-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Öffnen Sie Editor](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="db9bc-306">Legen Sie mit dem Editor öffnen die folgende JSON-Struktur, in es.</span><span class="sxs-lookup"><span data-stu-id="db9bc-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="db9bc-307">Sobald Sie dies getan haben, speichern Sie es auf Ihrem Desktop als **"Project.JSON"**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="db9bc-308">Es ist wichtig, dass die Benennung korrekt ist: Stellen Sie sicher, es ist **keine txt** Dateierweiterung.</span><span class="sxs-lookup"><span data-stu-id="db9bc-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="db9bc-309">Diese Datei definiert die Bibliotheken, die Ihre Funktion verwenden, die Wenn Sie die vertraut wird NuGet verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="db9bc-310">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="db9bc-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="db9bc-311">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach **Funktions-App**, drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Suchen Sie nach der Funktions-app](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="db9bc-313">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="db9bc-314">Die neue Seite bietet eine Beschreibung der **Funktions-App** Service.</span><span class="sxs-lookup"><span data-stu-id="db9bc-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="db9bc-315">Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Funktionen-app-Instanz](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="db9bc-317">Nachdem Sie auf geklickt haben **erstellen**, geben Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="db9bc-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="db9bc-318">Für **Anwendungsnamen**, fügen Sie dem gewünschten Namen für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="db9bc-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="db9bc-319">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="db9bc-320">Wählen Sie der Tarif für Sie geeignet, ist dies das erste Mal erstellen eine **-Funktion von App Service**, freier-Tarif für Sie verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="db9bc-321">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="db9bc-322">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="db9bc-323">Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="db9bc-324">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="db9bc-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="db9bc-325">Für **OS**, Windows, klicken Sie auf, da dies die angezielte Plattform ist.</span><span class="sxs-lookup"><span data-stu-id="db9bc-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="db9bc-326">Wählen Sie eine **Hostingplan** (in diesem Tutorial verwendet ein **Verbrauchstarif**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="db9bc-327">Wählen Sie eine **Speicherort** **(Wählen Sie im vorherigen Schritt am gleichen Speicherort wie der Speicher, die Sie erstellt haben)**</span><span class="sxs-lookup"><span data-stu-id="db9bc-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="db9bc-328">Für die **Storage** Abschnitt **müssen Sie den Storage-Dienst, die Sie im vorherigen Schritt erstellt haben, auswählen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="db9bc-329">Sie müssen keine *Application Insights* in dieser app können daher gerne bleibt bestehen **aus**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="db9bc-330">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-330">Click **Create**.</span></span>

        ![neue Instanz erstellen](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="db9bc-332">Nachdem Sie auf geklickt haben **erstellen** müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="db9bc-333">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Neue Benachrichtigung](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="db9bc-335">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="db9bc-336">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![zu Ressource wechseln](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="db9bc-338">Klicken Sie auf die **+** (Pluszeichen) Symbol neben dem *Funktionen*zu *neu erstellen*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Fügen Sie neue Funktion](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="db9bc-340">Klicken Sie im mittleren Bereich der **Funktion** Erstellung-Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="db9bc-341">Ignorieren Sie die Informationen in der oberen Hälfte des Bereichs, und klicken Sie auf **benutzerdefinierte Funktion**, befindet sich im unteren Bereich (im blauen Bereich, wie unten gezeigt).</span><span class="sxs-lookup"><span data-stu-id="db9bc-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="db9bc-343">Die neue Seite im Fenster zeigt die verschiedenen Funktionstypen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="db9bc-344">Scrollen Sie nach unten, um die lilafarbenen Typen anzuzeigen, und klicken Sie auf **HTTP PUT** Element.</span><span class="sxs-lookup"><span data-stu-id="db9bc-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![HTTP put-link](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="db9bc-346">Sie müssen möglicherweise weitere den nach unten scrollen der Seite (und dieses Image kann nicht genau gleich aussehen, wenn Updates für Azure-Portal ausgeführt wurden), allerdings möchten Sie für ein Element namens *HTTP PUT*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="db9bc-347">Die **HTTP PUT** Fenster angezeigt wird, müssen Sie die Funktion (siehe unten für Image) konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="db9bc-348">Für **Sprache** wählen Sie im Dropdownmenü mit C\#.</span><span class="sxs-lookup"><span data-stu-id="db9bc-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="db9bc-349">Für **Namen** Geben Sie einen geeigneten Namen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="db9bc-350">In der **Authentifizierungsebene** wählen Sie im Dropdownmenü **Funktion**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="db9bc-351">Für die **Tabellenname** Abschnitt müssen Sie den genauen Namen verwenden Sie zum Erstellen Ihrer **Tabelle** Dienst wurden (einschließlich der gleichen Groß-/Kleinschreibung).</span><span class="sxs-lookup"><span data-stu-id="db9bc-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="db9bc-352">In der **speicherkontoverbindung** Abschnitt mithilfe des Dropdownmenüs und dann Ihr Speicherkonto aus.</span><span class="sxs-lookup"><span data-stu-id="db9bc-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="db9bc-353">Wenn es ist nicht vorhanden, klicken Sie auf die **neu** links neben dem Abschnittstitel, um einen anderen Bereich anzuzeigen, in dem Ihr Speicherkonto aufgelistet werden soll.</span><span class="sxs-lookup"><span data-stu-id="db9bc-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![mit neuem Speicher](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="db9bc-355">Klicken Sie auf **erstellen** und Sie erhalten eine Benachrichtigung, dass Ihre Einstellungen wurden erfolgreich aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="db9bc-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Funktion erstellen](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="db9bc-357">Nach dem Klicken auf **erstellen**, gelangen Sie auf der Funktions-Editor.</span><span class="sxs-lookup"><span data-stu-id="db9bc-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![Aktualisieren von Funktionscode](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="db9bc-359">Fügen Sie den folgenden Code in der Funktions-Editor (ersetzen Sie den Code in der Funktion):</span><span class="sxs-lookup"><span data-stu-id="db9bc-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="db9bc-360">Verwenden den enthaltenen Bibliotheken, die Funktion erhält den Namen und Speicherort des Objekts, das verschoben wurde in der Unity-Szene (als eine C# Objekt, mit dem Namen **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="db9bc-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="db9bc-361">Dieses Objekt wird dann verwendet, um die Objektparameter in der erstellten Tabelle zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="db9bc-362">Anschluss Ruft die Funktion mit dem erstellten Notification Hub-Dienst, alle abonnierte Anwendungen darüber informiert.</span><span class="sxs-lookup"><span data-stu-id="db9bc-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="db9bc-363">Mit diesem Code, klicken Sie auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="db9bc-364">Klicken Sie anschließend die **\<** Symbol auf der rechten Seite der Seite (Pfeil).</span><span class="sxs-lookup"><span data-stu-id="db9bc-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Open-Upload-Bereich](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="db9bc-366">Ein Panel wird in der rechten Seite schieben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-366">A panel will slide in from the right.</span></span> <span data-ttu-id="db9bc-367">In diesem Bereich, klicken Sie auf **hochladen**, und einen Dateibrowser wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="db9bc-368">Navigieren Sie zu, und klicken Sie auf, die **"Project.JSON"** -Datei, die Sie in erstellt haben **Editor** zuvor, und klicken Sie dann auf die **öffnen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="db9bc-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="db9bc-369">Diese Datei definiert die Bibliotheken, die Ihre Funktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-369">This file defines the libraries that your function will use.</span></span>

    ![Hochladen von json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="db9bc-371">Wenn die Datei hochgeladen wurde, wird es im Bereich auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="db9bc-372">Klicken sie auf, öffnen sie in der **Funktion** Editor.</span><span class="sxs-lookup"><span data-stu-id="db9bc-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="db9bc-373">Es muss aussehen **genau** identisch mit der nächsten Abbildung (unter Schritt 23).</span><span class="sxs-lookup"><span data-stu-id="db9bc-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="db9bc-374">Klicken Sie dann im Bereich auf der linken Seite unter **Funktionen**, klicken Sie auf die **integrieren** Link.</span><span class="sxs-lookup"><span data-stu-id="db9bc-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![Integrieren der Funktion](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="db9bc-376">Klicken Sie auf der nächsten Seite in der oberen rechten Ecke auf **erweiterter Editor** (wie folgt).</span><span class="sxs-lookup"><span data-stu-id="db9bc-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![erweiterten Editor öffnen](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="db9bc-378">Ein **"Function.JSON"** Datei wird im mittleren Bereich, der durch den folgenden Codeausschnitt ersetzt werden muss, geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="db9bc-379">Definiert die Funktion, die Sie erstellen und die Parameter an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="db9bc-380">Als Editor sollte jetzt wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-380">Your editor should now look like the image below:</span></span>

    ![zurück zum standard-editor](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="db9bc-382">Sie werden feststellen, die Eingabeparameter, die Sie gerade eingefügt haben, entsprechen möglicherweise nicht die Details Ihres Tabellen- und, und aus diesem Grund müssen mit Ihren Informationen aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="db9bc-383">**Verwenden Sie keine hier**, wie sie als Nächstes abgedeckt wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="db9bc-384">Klicken Sie einfach auf die **Standardeditor** Link in der oberen rechten Ecke der Seite, um zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="db9bc-385">In der **Standardeditor**, klicken Sie auf **Azure Table Storage (Tabelle)** unter **Eingaben**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Eingaben für Tabellen](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="db9bc-387">Stellen Sie sicher die folgende Übereinstimmung zu **Ihre** Informationen, wie sie verschieden sein können (es gibt ein Bild auf die folgenden Schritte aus):</span><span class="sxs-lookup"><span data-stu-id="db9bc-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="db9bc-388">**Tabellenname**: der Name der Tabelle, die Sie in Ihrem Azure Storage Tables-Dienst erstellt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="db9bc-389">**Speicherkontoverbindung:** klicken Sie auf **neue**, die zusammen mit dem Dropdown-Menü angezeigt wird und ein Bereich wird angezeigt, die den rechten Rand des Fensters.</span><span class="sxs-lookup"><span data-stu-id="db9bc-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![mit neuem Speicher](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="db9bc-391">Wählen Sie Ihre **Speicherkonto**, die Sie zuvor erstellt haben, auf dem Host die **Funktions-Apps.**</span><span class="sxs-lookup"><span data-stu-id="db9bc-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="db9bc-392">Sie werden feststellen, dass die **Speicherkonto** Verbindung-Wert erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="db9bc-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="db9bc-393">Achten Sie darauf, drücken die **speichern** sobald Sie fertig sind.</span><span class="sxs-lookup"><span data-stu-id="db9bc-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="db9bc-394">Die **Eingaben** Seite sollte jetzt übereinstimmen. die unten zeigt **Ihre** Informationen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![Ausführen von Eingaben](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="db9bc-396">Klicken Sie anschließend **Azure Notification Hub (Benachrichtigung)** – unter **Ausgaben**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="db9bc-397">Stellen Sie sicher, die folgenden zugeordnet sind **Ihre** Informationen, wie sie verschieden sein können (es gibt ein Bild auf die folgenden Schritte aus):</span><span class="sxs-lookup"><span data-stu-id="db9bc-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="db9bc-398">**Notification Hub-Namen**: Dies ist der Name der Ihrer **Benachrichtigungs-Hub** Service-Instanz, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="db9bc-399">**Namespaceverbindung für Notification Hubs**: Klicken Sie auf **neue**, die zusammen mit dem Dropdown-Menü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![Überprüfen Sie die Ausgaben](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="db9bc-401">Die **Verbindung** Popupfenster wird angezeigt (siehe Abbildung unten), müssen Sie wählen die **Namespace** von der **Benachrichtigungs-Hub**, die Sie zuvor eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="db9bc-402">Wählen Sie Ihre **Benachrichtigungs-Hub** Name aus dem mittleren Dropdownmenü aus.</span><span class="sxs-lookup"><span data-stu-id="db9bc-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="db9bc-403">Legen Sie die **Richtlinie** Dropdownmenü **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="db9bc-404">Klicken Sie auf die **wählen** Schaltfläche, um zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-404">Click the **Select** button to go back.</span></span>

        ![Ausgabe aktualisieren](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="db9bc-406">Die **Ausgaben** Seite sollte jetzt entsprechen die im folgenden, jedoch mit **Ihre** Informationen stattdessen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="db9bc-407">Achten Sie darauf, drücken die **speichern**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="db9bc-408">*Bearbeiten Sie den Notification Hub-Namen nicht direkt* (Dies sollte alle erfolgen mithilfe der **Erweiterter Editor**, sofern Sie die vorherigen Schritte richtig befolgt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="db9bc-410">An diesem Punkt sollten Sie testen die Funktion, um sicherzustellen, dass sie funktioniert.</span><span class="sxs-lookup"><span data-stu-id="db9bc-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="db9bc-411">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="db9bc-411">To do this:</span></span> 

    1. <span data-ttu-id="db9bc-412">Navigieren Sie zu der Seite "Funktion" einmal an:</span><span class="sxs-lookup"><span data-stu-id="db9bc-412">Navigate to the function page once more:</span></span>

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="db9bc-414">Klicken Sie auf der Seite "Funktion" auf die **Test** Registerkarte ganz rechts neben der Seite zu öffnen der *Test* Blatt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="db9bc-416">In der **Anforderungstext** Textfeld auf dem Blatt, fügen Sie den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="db9bc-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="db9bc-417">Der Testcode vorhanden, und klicken Sie auf die **ausführen** Schaltfläche unten rechts, und der Test ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="db9bc-418">Die Ausgabeprotokolle des Tests werden im Konsolenfensterbereich unter Ihrem Funktionscode angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="db9bc-420">Wenn der oben genannten Test fehlschlägt, benötigen Sie überprüfen, dass Sie die oben genannten Schritte genau befolgt haben vor allem die Einstellungen in der **integrieren Bereich**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="db9bc-421">Kapitel 7: Einrichten von Unity-Projekt für Desktop</span><span class="sxs-lookup"><span data-stu-id="db9bc-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db9bc-422">Die Desktopanwendung, mit der Sie jetzt erstellen, **nicht** im Unity-Editor arbeiten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="db9bc-423">Es muss außerhalb des Editors, und befolgen die Erstellung von der Anwendung mithilfe von Visual Studio (oder die bereitgestellte Anwendung) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="db9bc-424">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit Unity und mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="db9bc-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="db9bc-425">Richten Sie ein und Testen Sie Ihrer mixed Reality immersive Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="db9bc-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="db9bc-426">Sie **nicht** Motion-Controller für dieses Kurses erforderlich.</span><span class="sxs-lookup"><span data-stu-id="db9bc-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="db9bc-427">Wenn Sie die Einrichtung der immersive Kopfhörer unterstützen müssen, befolgen Sie diese [Link zum Einrichten von Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="db9bc-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="db9bc-428">Open **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-428">Open **Unity** and click **New**.</span></span>

    ![Neues Unity-Projekt](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="db9bc-430">Sie benötigen, geben Sie einen Namen für die Unity-Projekt, das Einfügen **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="db9bc-431">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="db9bc-432">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="db9bc-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="db9bc-433">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-433">Then, click **Create project**.</span></span>

    ![Projekt erstellen](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="db9bc-435">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="db9bc-436">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-436">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="db9bc-437">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="db9bc-438">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="db9bc-438">Close the **Preferences** window.</span></span>

    ![externe Satz Visual Studio-tools](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="db9bc-440">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-440">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Plattform wechseln](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="db9bc-442">In der **Datei > Buildeinstellungen**, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="db9bc-442">While still in **File > Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="db9bc-443">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät**</span><span class="sxs-lookup"><span data-stu-id="db9bc-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="db9bc-444">Diese Anwendung für den Desktop, muss daher **einem beliebigen Gerät**</span><span class="sxs-lookup"><span data-stu-id="db9bc-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="db9bc-445">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="db9bc-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="db9bc-446">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="db9bc-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="db9bc-447">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="db9bc-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="db9bc-448">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="db9bc-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="db9bc-449">Hier lohnt sich die Szene speichern und mit dem Build hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="db9bc-450">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="db9bc-451">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-451">A save window will appear.</span></span>

            ![Hinzufügen von öffnen-Szenen](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="db9bc-453">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![neuen Ordner "Szenen"](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="db9bc-455">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname:** Textfeld **Notification Hub\_Desktop\_Szene**, drücken Sie dann die **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![neue NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="db9bc-457">Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="db9bc-458">Klicken Sie in demselben Fenster auf die **Playereinstellungen** Schaltfläche Dies öffnet den entsprechenden Bereich im Bereich, in dem die **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="db9bc-459">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="db9bc-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="db9bc-460">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="db9bc-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="db9bc-461">**Scripting Runtime Version** muss **experimentell (.NET 4.6 Äquivalent)**</span><span class="sxs-lookup"><span data-stu-id="db9bc-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="db9bc-462">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="db9bc-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="db9bc-463">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="db9bc-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![net-Version 4.6](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="db9bc-465">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="db9bc-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="db9bc-466">**InternetClient**</span></span>

            ![Takt-Internetclient](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="db9bc-468">Im **Buildeinstellungen** *Unity C\# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="db9bc-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="db9bc-469">Schließen der **Buildeinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="db9bc-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="db9bc-470">Speichern Sie Ihre Szene und das Projekt \**Datei > Szene speichern* / \* Datei > Speichern Projekt \*\*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-470">Save your Scene and Project \**File > Save Scene* / \*File > Save Project\*\*.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="db9bc-471">Wenn Sie, überspringen möchten die *Unity einrichten* Komponente für dieses Projekt (Desktop-App), weiterhin direkt in Code, und Sie gerne [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="db9bc-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="db9bc-472">Sie müssen weiterhin die Skriptkomponenten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="db9bc-473">Kapitel 8 – Importieren von die DLLs in Unity</span><span class="sxs-lookup"><span data-stu-id="db9bc-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="db9bc-474">Verwenden Sie Azure Storage für Unity (die wiederum nutzt das .net SDK für Azure).</span><span class="sxs-lookup"><span data-stu-id="db9bc-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="db9bc-475">Weitere Informationen führen Sie diesen [Link zu Azure Storage für Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="db9bc-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="db9bc-476">Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert.</span><span class="sxs-lookup"><span data-stu-id="db9bc-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="db9bc-477">Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="db9bc-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="db9bc-478">Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie heruntergeladen haben, die neueste Version [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) aus GitHub.</span><span class="sxs-lookup"><span data-stu-id="db9bc-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="db9bc-479">Führen Sie anschließend folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="db9bc-479">Then, do the following:</span></span>

1.  <span data-ttu-id="db9bc-480">Hinzufügen der **.unitypackage** in Unity mithilfe der **Assets \> Paket importieren \> Custom Package** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="db9bc-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="db9bc-481">In der **Unity-Paket importieren** Feld angezeigt, alles unter können Sie auswählen \*\**-Plug-Ins* \> \* Storage \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="db9bc-482">Deaktivieren Sie alles andere, da sie für diesen Kurs nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Paket importieren](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="db9bc-484">Klicken Sie auf die ***Import*** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="db9bc-485">Wechseln Sie zu der **Storage** Unterordner **-Plug-Ins** im Projekt anzuzeigen, und wählen Sie die folgenden Plug-Ins *nur*:</span><span class="sxs-lookup"><span data-stu-id="db9bc-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="db9bc-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="db9bc-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="db9bc-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="db9bc-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="db9bc-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="db9bc-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="db9bc-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="db9bc-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="db9bc-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="db9bc-490">System.Spatial</span></span>

![Deaktivieren Sie jede Plattform](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="db9bc-492">Mit *bestimmte Plug-Ins* ausgewählt, **deaktivieren** **Any Platform** und **deaktivieren** **WSAPlayer** Klicken Sie dann auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Anwenden von Plattform-dlls](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="db9bc-494">Wir markieren diese bestimmten Plug-Ins, die nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="db9bc-495">Dies ist, da es gibt verschiedene Versionen der gleichen Plug-Ins in das WSA-Ordner, der verwendet wird und nachdem das Projekt aus Unity exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="db9bc-496">In der **Storage** -Plug-in-Ordner, wählen Sie nur:</span><span class="sxs-lookup"><span data-stu-id="db9bc-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="db9bc-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="db9bc-497">Microsoft.Data.Services.Client</span></span>

        ![Gruppe nicht für DLL-Dateien verarbeiten](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="db9bc-499">Überprüfen Sie die **Don't Prozess** Feld **Plattformeinstellungen** , und klicken Sie auf ***übernehmen***.</span><span class="sxs-lookup"><span data-stu-id="db9bc-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="db9bc-501">Wir werden dieses Plug-in "Nicht verarbeiten", markieren, da die Unity-Assembly-Patcher schwierigkeiten beim Verarbeiten dieses Plug-in ist.</span><span class="sxs-lookup"><span data-stu-id="db9bc-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="db9bc-502">Das Plug-in funktioniert weiterhin, auch wenn sie nicht verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="db9bc-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="db9bc-503">Kapitel 9 – erstellen Sie die TableToScene-Klasse in der Desktop Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="db9bc-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="db9bc-504">Nun müssen Sie die Skripts, die den Code zum Ausführen dieser Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="db9bc-505">Ist das erste Skript, das Sie erstellen müssen **TableToScene**, die für verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="db9bc-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="db9bc-506">Lesen von Entitäten innerhalb der Azure-Tabelle.</span><span class="sxs-lookup"><span data-stu-id="db9bc-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="db9bc-507">Die Daten dieser Tabelle, bestimmen, welche Objekte zu erzeugen, und an welcher Position.</span><span class="sxs-lookup"><span data-stu-id="db9bc-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="db9bc-508">Ist das zweite Skript, das Sie erstellen müssen **CloudScene**, die für verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="db9bc-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="db9bc-509">Registrieren das Ereignis klicken, um dem Benutzer ermöglichen, Objekte in der Szene ziehen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="db9bc-510">Serialisieren von Daten des Objekts, von diese Unity-Szene, und sie an der Azure-Funktions-App senden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="db9bc-511">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-511">To create this class:</span></span>

1.  <span data-ttu-id="db9bc-512">Mit der rechten Maustaste den **Asset** Ordner befindet sich im Projektfenster **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-512">Right-click in the **Asset** Folder located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="db9bc-513">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-513">Name the folder **Scripts**.</span></span>

    ![Erstellen Sie Ordner "Scripts"](images/AzureLabs-Lab8-66.png)

    ![Erstellen Sie Ordner "Scripts" 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="db9bc-516">Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="db9bc-517">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-517">Right-click inside the **Scripts** folder, click **Create** **C\# Script**.</span></span> <span data-ttu-id="db9bc-518">Nennen Sie das Skript **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="db9bc-519">![neue c#-Skript](images/AzureLabs-Lab8-68.png)
    ![TableToScene umbenennen](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="db9bc-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="db9bc-520">Doppelklicken Sie auf das Skript aus, um sie in Visual Studio 2017 öffnen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="db9bc-521">Fügen Sie die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="db9bc-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="db9bc-522">Fügen Sie innerhalb der Klasse die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="db9bc-523">Ersetzen der **AccountName** Wert durch den Namen Ihres Azure Storage-Dienst und **AccountKey** Wert mit dem Schlüsselwert finden Sie in den Azure Storage-Dienst im Azure-Portal (siehe Abbildung unten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![Abrufen des kontoschlüssels](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="db9bc-525">Fügen Sie nun die **Start()** und **Awake()** Methoden zum Initialisieren der Klasse.</span><span class="sxs-lookup"><span data-stu-id="db9bc-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="db9bc-526">In der **TableToScene** Klasse, fügen Sie die Methode, die die Werte aus der Azure-Tabelle abrufen und diese verwenden, um die entsprechenden primitiven in der Szene zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="db9bc-527">Außerhalb der **TableToScene** -Klasse, müssen Sie die Klasse, die zum Serialisieren und Deserialisieren von der Anwendung verwendeten definieren die **Tabellenentitäten**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="db9bc-528">Stellen Sie sicher, dass Sie **speichern** vor dem Wechsel zurück zu Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="db9bc-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="db9bc-529">Klicken Sie auf die **Main Camera** aus der **Hierarchie** Bereich, sodass seine Eigenschaften im angezeigt werden die **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="db9bc-530">Mit der **Skripts** Ordner geöffnet ist, wählen Sie das Skript **TableToScene Datei** und ziehen Sie es auf die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="db9bc-531">Das Ergebnis sollte wie folgt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-531">The result should be as below:</span></span>

    ![Hauptkamera Skript hinzugefügt](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="db9bc-533">Kapitel 10 – erstellen Sie die CloudScene-Klasse in der Unity-Projekt für Desktop</span><span class="sxs-lookup"><span data-stu-id="db9bc-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="db9bc-534">Ist das zweite Skript, das Sie erstellen müssen **CloudScene**, die für verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="db9bc-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="db9bc-535">Registrieren das Ereignis klicken, um dem Benutzer ermöglichen, Objekte in der Szene ziehen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="db9bc-536">Serialisieren von Daten des Objekts, von diese Unity-Szene, und sie an der Azure-Funktions-App senden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="db9bc-537">So erstellen Sie das zweite Skript:</span><span class="sxs-lookup"><span data-stu-id="db9bc-537">To create the second script:</span></span>

1.  <span data-ttu-id="db9bc-538">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**, **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="db9bc-539">Nennen Sie das Skript **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="db9bc-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="db9bc-540">![neue c#-Skript](images/AzureLabs-Lab8-72.png)
    ![CloudScene umbenennen](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="db9bc-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="db9bc-541">Fügen Sie die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="db9bc-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="db9bc-542">Fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="db9bc-543">Ersetzen der **AzureFunctionEndpoint** Wert mit Ihrem Azure-Funktion-App-URL finden Sie in der Azure-Funktion App Service im Azure-Portal, wie in der folgenden Abbildung gezeigt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Funktions-URL abrufen](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="db9bc-545">Fügen Sie nun die **Start()** und **Awake()** Methoden zum Initialisieren der Klasse.</span><span class="sxs-lookup"><span data-stu-id="db9bc-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="db9bc-546">In der **Update()** -Methode, fügen Sie folgenden Code, mit denen erkannt wird, die Mauseingabe und ziehen Sie, die wiederum "gameobjects" in der Szene verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="db9bc-547">Wenn der Benutzer verfügt über Drag & Drop ein Objekt, es werden die Namen und die Koordinaten des Objekts an die Methode übergeben **UpdateCloudScene()**, ruft die den Azure-Funktions-App-Dienst, das die Azure-Tabelle und der Trigger aktualisiert die die Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="db9bc-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="db9bc-548">Fügen Sie nun die **UpdateCloudScene()** Methode, wie unten gezeigt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="db9bc-549">Speichern Sie den Code und zurück zu Unity</span><span class="sxs-lookup"><span data-stu-id="db9bc-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="db9bc-550">Ziehen Sie die **CloudScene** Skript auf die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="db9bc-551">Klicken Sie auf die **Main Camera** aus der **Hierarchie** Bereich, sodass seine Eigenschaften im angezeigt werden die **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="db9bc-552">Mit der **Skripts** geöffnet ist, wählen die **CloudScene** Skript, und ziehen Sie es auf die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="db9bc-553">Das Ergebnis sollte wie folgt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-553">The result should be as below:</span></span>

        > ![Ziehen Sie Cloud-Skript auf Hauptkamera](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="db9bc-555">Kapitel 11: Erstellen Sie das Desktopprojekt UWP</span><span class="sxs-lookup"><span data-stu-id="db9bc-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="db9bc-556">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="db9bc-557">Navigieren Sie zu **Buildeinstellungen** (**Datei > Buildeinstellungen**).</span><span class="sxs-lookup"><span data-stu-id="db9bc-557">Navigate to **Build Settings** (**File > Build Settings**).</span></span>

2.  <span data-ttu-id="db9bc-558">Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Buildprojekt](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="db9bc-560">Ein **Datei-Explorer** Fenster wird Popup, dem Sie einen Speicherort für den Build aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="db9bc-561">Erstellen Sie einen neuen Ordner (indem Sie auf **neuer Ordner** in der oberen linken Ecke), und nennen Sie sie **erstellt**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![neuen Ordner für build](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="db9bc-563">Öffnen Sie die neue **erstellt** Ordner, und erstellen Sie einen anderen Ordner (mit **neuer Ordner** einmal), und nennen Sie sie **NH\_Desktop\_App**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![Name des Ordners NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="db9bc-565">Mit der **NH\_Desktop\_App** ausgewählten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="db9bc-566">Klicken Sie auf **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-566">click **Select Folder**.</span></span> <span data-ttu-id="db9bc-567">Das Projekt wird eine Minute erstellen dauern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="db9bc-568">Nach Build **Datei-Explorer** wird angezeigt, die Sie den Standort des neuen Projekts.</span><span class="sxs-lookup"><span data-stu-id="db9bc-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="db9bc-569">Nicht erforderlich, um sie zu öffnen, aber wie müssen Sie die andere erstellt Unity Projekt zuerst in den nächsten Kapiteln werden soll.</span><span class="sxs-lookup"><span data-stu-id="db9bc-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="db9bc-570">Kapitel 12: Einrichten von Mixed Reality Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="db9bc-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="db9bc-571">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="db9bc-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="db9bc-572">Open **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-572">Open **Unity** and click **New**.</span></span>

    ![Neues Unity-Projekt](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="db9bc-574">Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="db9bc-575">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="db9bc-576">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="db9bc-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="db9bc-577">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-577">Then, click **Create project**.</span></span>

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="db9bc-579">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="db9bc-580">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-580">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="db9bc-581">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="db9bc-582">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="db9bc-582">Close the **Preferences** window.</span></span>

    ![externe-Editors in VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="db9bc-584">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="db9bc-584">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Plattform für die UWP wechseln](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="db9bc-586">Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="db9bc-586">Go to **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="db9bc-587">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät**</span><span class="sxs-lookup"><span data-stu-id="db9bc-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="db9bc-588">Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="db9bc-589">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="db9bc-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="db9bc-590">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="db9bc-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="db9bc-591">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="db9bc-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="db9bc-592">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="db9bc-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="db9bc-593">Hier lohnt sich die Szene speichern und mit dem Build hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="db9bc-594">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="db9bc-595">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-595">A save window will appear.</span></span>

            ![Hinzufügen von öffnen-Szenen](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="db9bc-597">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![neuen Ordner "Szenen"](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="db9bc-599">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname:** Textfeld **NH\_MR\_Szene**, drücken Sie dann die  **Speichern Sie**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![neue Szene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="db9bc-601">Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="db9bc-602">Klicken Sie in demselben Fenster auf die **Playereinstellungen** Schaltfläche Dies öffnet den entsprechenden Bereich im Bereich, in dem die **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Öffnen der playereinstellungen](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="db9bc-604">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="db9bc-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="db9bc-605">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="db9bc-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="db9bc-606">**Scripting Runtime Version** muss **experimentell** (.NET 4.6 Äquivalent)</span><span class="sxs-lookup"><span data-stu-id="db9bc-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="db9bc-607">**Back-End-Scripting** muss ***.NET***</span><span class="sxs-lookup"><span data-stu-id="db9bc-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="db9bc-608">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="db9bc-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![API-Kompatibilität](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="db9bc-610">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  wird hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="db9bc-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Aktualisieren der Xr-Einstellungen](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="db9bc-612">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, prüfen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="db9bc-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="db9bc-613">**InternetClient**</span></span>           

            ![Takt-Internetclient](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="db9bc-615">Im **Buildeinstellungen** *Unity C\# Projekte* ist nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="db9bc-615">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="db9bc-616">Schließen Sie mit diesen Änderungen durchgeführt, und das Build Settings-Fenster.</span><span class="sxs-lookup"><span data-stu-id="db9bc-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="db9bc-617">Speichern Sie Ihre Szene und das Projekt \**Datei* *Szene speichern*/ *Datei* \* speichern Projekt \*\*.</span><span class="sxs-lookup"><span data-stu-id="db9bc-617">Save your Scene and Project \**File* *Save Scene*/ *File* \*Save Project\*\*.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="db9bc-618">Wenn Sie, überspringen möchten der *Unity einrichten* für dieses Projekt (mixed Reality-App)-Komponente weiterhin direkt in Code, und Sie gerne [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="db9bc-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="db9bc-619">Sie müssen weiterhin die Skriptkomponenten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="db9bc-620">Kapitel 13 – Importieren von die DLLs im Unity-Projekts Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="db9bc-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="db9bc-621">Sie werden Azure Storage für Unity-Bibliothek verwenden (das das .net SDK für Azure verwendet wird).</span><span class="sxs-lookup"><span data-stu-id="db9bc-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="db9bc-622">Führen Sie dies [Link zur Verwendung von Azure Storage mit Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="db9bc-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="db9bc-623">Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert.</span><span class="sxs-lookup"><span data-stu-id="db9bc-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="db9bc-624">Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="db9bc-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="db9bc-625">Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie heruntergeladen haben, die neueste Version [.unitypackage](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="db9bc-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="db9bc-626">Führen Sie anschließend folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="db9bc-626">Then, do the following:</span></span>

1.  <span data-ttu-id="db9bc-627">Hinzufügen der .unitypackage, die Sie aus den oben genannten, in Unity mithilfe heruntergeladen der **Assets > Paket importieren > benutzerdefiniertes Paket** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="db9bc-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="db9bc-628">In der **Unity-Paket importieren** Feld angezeigt, alles unter können Sie auswählen **-Plug-in > Speicher**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin > Storage**.</span></span>

    ![Paket importieren](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="db9bc-630">Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="db9bc-631">Wechseln Sie zu der **Storage** Unterordner **-Plug-Ins** im Projekt anzuzeigen, und wählen Sie die folgenden Plug-Ins *nur*:</span><span class="sxs-lookup"><span data-stu-id="db9bc-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="db9bc-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="db9bc-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="db9bc-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="db9bc-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="db9bc-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="db9bc-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="db9bc-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="db9bc-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="db9bc-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="db9bc-636">System.Spatial</span></span>

    ![Wählen Sie-Plug-Ins](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="db9bc-638">Mit *bestimmte Plug-Ins* ausgewählt, **deaktivieren** **Any Platform** und **deaktivieren** **WSAPlayer** Klicken Sie dann auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Anwenden von plattformänderungen](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="db9bc-640">Markieren Sie diese bestimmten Plug-Ins, die nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="db9bc-641">Dies ist, da es gibt verschiedene Versionen der gleichen Plug-Ins in das WSA-Ordner, der verwendet wird und nachdem das Projekt aus Unity exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="db9bc-642">In der **Storage** -Plug-in-Ordner, wählen Sie nur:</span><span class="sxs-lookup"><span data-stu-id="db9bc-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="db9bc-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="db9bc-643">Microsoft.Data.Services.Client</span></span>

        ![Data Services-Client auswählen](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="db9bc-645">Überprüfen Sie die **Don't Prozess** Feld **Plattformeinstellungen** , und klicken Sie auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![nicht verarbeiten](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="db9bc-647">Sie werden dieses Plug-in "Nicht verarbeiten" markieren, da die Unity-Assembly-Patcher schwierigkeiten beim Verarbeiten dieses Plug-in ist.</span><span class="sxs-lookup"><span data-stu-id="db9bc-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="db9bc-648">Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet ist.</span><span class="sxs-lookup"><span data-stu-id="db9bc-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="db9bc-649">Kapitel 14: Erstellen der TableToScene-Klasse in mixed Reality Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="db9bc-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="db9bc-650">Die **TableToScene** Klasse ist identisch mit dem im erläutert [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="db9bc-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="db9bc-651">Erstellen Sie die gleiche Klasse in gemischten Unity-Projekt die gleichen Schritte, in erläutert Wirklichkeit [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="db9bc-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="db9bc-652">Nachdem Sie in diesem Kapitel, beide haben Ihre **Unity-Projekte** wird diese Klasse, die auf den Main Camera eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="db9bc-653">Kapitel 15: Erstellen der NotificationReceiver-Klasse in Mixed Reality Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="db9bc-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="db9bc-654">Ist das zweite Skript, das Sie erstellen müssen **NotificationReceiver**, die für verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="db9bc-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="db9bc-655">Beim Registrieren der app beim Notification Hub bei der Initialisierung.</span><span class="sxs-lookup"><span data-stu-id="db9bc-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="db9bc-656">Von den Notification Hub-Benachrichtigungen überwacht.</span><span class="sxs-lookup"><span data-stu-id="db9bc-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="db9bc-657">Deserialisiert die Daten des Objekts aus dem empfangenen Benachrichtigungen an.</span><span class="sxs-lookup"><span data-stu-id="db9bc-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="db9bc-658">Verschieben Sie die "gameobjects" in der Szene, basierend auf den deserialisierten Daten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="db9bc-659">Zum Erstellen der **NotificationReceiver** Skript:</span><span class="sxs-lookup"><span data-stu-id="db9bc-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="db9bc-660">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**, **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="db9bc-661">Nennen Sie das Skript **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="db9bc-662">![Erstellen Sie neue c#-Skript](images/AzureLabs-Lab8-95.png)
    ![NotificationReceiver Namen](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="db9bc-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="db9bc-663">Doppelklicken Sie auf das Skript aus, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="db9bc-664">Fügen Sie die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="db9bc-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="db9bc-665">Fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="db9bc-666">Ersetzen der **HubName** Wert durch den Namen Ihres Notification Hubs-Dienst und **HubListenEndpoint** Wert mit den Endpunktwert finden Sie in der Registerkarte "Zugriffsrichtlinien" Azure Notification Hubs-Dienst, in der Azure-Portal (siehe Abbildung unten).</span><span class="sxs-lookup"><span data-stu-id="db9bc-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Einfügen von Notification Hubs-Richtlinie-Endpunkt](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="db9bc-668">Fügen Sie nun die **Start()** und **Awake()** Methoden zum Initialisieren der Klasse.</span><span class="sxs-lookup"><span data-stu-id="db9bc-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="db9bc-669">Hinzufügen der **WaitForNotification** Methode, um die app Benachrichtigungen aus der Bibliothek der Notification Hub empfangen werden, ohne mit den Hauptthread ein Konflikt besteht zuzulassen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="db9bc-670">Die folgende Methode, **InitNotificationAsync()**, registrieren Sie die Anwendung wird mit dem Notification Hub-Dienst bei der Initialisierung.</span><span class="sxs-lookup"><span data-stu-id="db9bc-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="db9bc-671">Der Code ist auskommentiert, wie Unity nicht zum Erstellen des Projekts kann.</span><span class="sxs-lookup"><span data-stu-id="db9bc-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="db9bc-672">Sie werden die Kommentare entfernen, wenn Sie das Azure-Messaging-Nuget-Paket in Visual Studio importieren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="db9bc-673">Der folgende Handler, **Kanal\_PushNotificationReceived()**, wird jedes Mal, wenn eine Benachrichtigung empfangen wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="db9bc-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="db9bc-674">Es wird die Benachrichtigung Deserialisieren der wird die Azure Table Storage-Entität, die auf die Desktop-Anwendung verschoben wurden, und klicken Sie dann das entsprechende "gameobject" in der Szene MR an dieselbe Position verschieben.</span><span class="sxs-lookup"><span data-stu-id="db9bc-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="db9bc-675">Der Code ist auskommentiert, da der Code die Azure-Messaging-Bibliothek verweist, die Sie nach dem Erstellen des Nuget-Paket-Managers in Visual Studio mit Unity-Projekts hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="db9bc-676">Daher wird das Unity-Projekt nicht erstellen, können es sei denn, er ist auskommentiert ist. Beachten Sie, sollten Sie Ihr Projekt erstellen und anschließend zu Unity zurückgeben möchten, müssen Sie **wieder mit Kommentaren versehen** dieses Codes.</span><span class="sxs-lookup"><span data-stu-id="db9bc-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="db9bc-677">Denken Sie daran, um die Änderungen zu speichern, vor dem Wechsel zurück zu Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="db9bc-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="db9bc-678">Klicken Sie auf die **Main Camera** aus der **Hierarchie** Bereich, sodass seine Eigenschaften im angezeigt werden die **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="db9bc-679">Mit der **Skripts** geöffnet ist, wählen die **NotificationReceiver** Skript, und ziehen Sie es auf die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="db9bc-680">Das Ergebnis sollte wie folgt:</span><span class="sxs-lookup"><span data-stu-id="db9bc-680">The result should be as below:</span></span>

    ![Ziehen Sie Empfänger Benachrichtigungsskript an Kamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="db9bc-682">Wenn Sie dies für die Microsoft HoloLens entwickeln, müssen Sie zum Aktualisieren der **Main Camera**des *Kamera* -Komponente, damit:</span><span class="sxs-lookup"><span data-stu-id="db9bc-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="db9bc-683">Flags zu löschen: Volltonfarbe</span><span class="sxs-lookup"><span data-stu-id="db9bc-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="db9bc-684">Hintergrund: Schwarz</span><span class="sxs-lookup"><span data-stu-id="db9bc-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="db9bc-685">Kapitel 16 – erstellen Sie das Mixed Reality-Projekt auf UWP</span><span class="sxs-lookup"><span data-stu-id="db9bc-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="db9bc-686">In diesem Kapitel ist identisch mit der Prozess für das vorherige Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db9bc-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="db9bc-687">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.</span><span class="sxs-lookup"><span data-stu-id="db9bc-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="db9bc-688">Navigieren Sie zu **Buildeinstellungen** ( **Datei > Buildeinstellungen...**  ).</span><span class="sxs-lookup"><span data-stu-id="db9bc-688">Navigate to **Build Settings** ( **File > Build Settings...** ).</span></span>

2.  <span data-ttu-id="db9bc-689">Von der **Buildeinstellungen** Menü, stellen Sie sicher **Unity C# Projekte**\* ist (sodass Sie so bearbeiten Sie die Skripts in diesem Projekt nach dem Build).</span><span class="sxs-lookup"><span data-stu-id="db9bc-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="db9bc-690">Nachdem dies geschehen ist, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-690">After this is done, click **Build**.</span></span>

    ![Buildprojekt](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="db9bc-692">Ein **Datei-Explorer** Fenster wird Popup, dem Sie einen Speicherort für den Build aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="db9bc-693">Erstellen Sie einen neuen Ordner (indem Sie auf **neuer Ordner** in der oberen linken Ecke), und nennen Sie sie **erstellt**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Erstellen Sie Ordner "Builds"](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="db9bc-695">Öffnen Sie die neue **erstellt** Ordner, und erstellen Sie einen anderen Ordner (mit **neuer Ordner** einmal), und nennen Sie sie **NH\_MR\_App**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Erstellen Sie NH_MR_Apps-Ordner](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="db9bc-697">Mit der **NH\_MR\_App** ausgewählten.</span><span class="sxs-lookup"><span data-stu-id="db9bc-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="db9bc-698">Klicken Sie auf **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-698">click **Select Folder**.</span></span> <span data-ttu-id="db9bc-699">Das Projekt wird eine Minute erstellen dauern.</span><span class="sxs-lookup"><span data-stu-id="db9bc-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="db9bc-700">Folgen den Build, eine **Datei-Explorer** Fenster wird geöffnet, an der Position des neuen Projekts.</span><span class="sxs-lookup"><span data-stu-id="db9bc-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="db9bc-701">Kapitel 17: Hinzufügen von NuGet-Pakete der Projektmappe UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="db9bc-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="db9bc-702">Bitte denken Sie daran, dass sobald Sie die folgenden NuGet-Pakete hinzufügen (und entfernen Sie den Code in den nächsten [Kapitel](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), der Code, wenn in der Unity-Projekt erneut geöffnet werden Fehler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="db9bc-703">Wenn Sie möchten, wechseln zurück und weiter im Unity-Editor bearbeiten, müssen Sie Errosome Code kommentieren, und klicken Sie dann kommentieren es später noch Mal, wenn Sie in Visual Studio sind.</span><span class="sxs-lookup"><span data-stu-id="db9bc-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="db9bc-704">Sobald der mixed Reality-Build abgeschlossen wurde, navigieren Sie zu dem mixed Reality-Projekt, das Sie erstellt, und doppelklicken auf die Projektmappendatei (.sln) in diesem Ordner, um die Projektmappe mit Visual Studio 2017 geöffnet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="db9bc-705">Sie müssen sich jetzt hinzufügen der **WindowsAzure.Messaging.managed** NuGet-Paket; Dies ist eine Bibliothek, die zum Empfangen von Benachrichtigungen vom Notification Hub verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="db9bc-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="db9bc-706">So importieren Sie das NuGet-Paket:</span><span class="sxs-lookup"><span data-stu-id="db9bc-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="db9bc-707">In der **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf die Projektmappe</span><span class="sxs-lookup"><span data-stu-id="db9bc-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="db9bc-708">Klicken Sie auf **NuGet-Pakete verwalten**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-708">Click on **Manage NuGet Packages**.</span></span>

    ![Öffnen Sie den Nuget-manager](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="db9bc-710">Wählen Sie die ***Durchsuchen*** Registerkarte und suchen Sie nach **WindowsAzure.Messaging.managed**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![Windows Azure-messaging-Paket zu finden](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="db9bc-712">Wählen Sie das Ergebnis (wie unten gezeigt), und wählen Sie im Fenster auf der rechten Seite das Kontrollkästchen neben **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="db9bc-713">Dies wird setzen einen Teilstrich in das Kontrollkästchen neben **Projekt**, sowie das Kontrollkästchen neben der **Assembly-CSharp** und **UnityMRNotifHub** Projekt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![Aktivieren Sie alle Projekte](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="db9bc-715">Die ursprünglich bereitgestellte Version **möglicherweise nicht** mit diesem Projekt kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="db9bc-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="db9bc-716">Aus diesem Grund, klicken Sie auf das Dropdownmenü neben **Version**, und klicken Sie auf **Version 0.1.7.9**, klicken Sie dann auf **installieren**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="db9bc-717">Installieren das NuGet-Paket ist jetzt beendet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="db9bc-718">Suchen Sie den kommentierten Code, der Sie eingegeben, in haben der **NotificationReceiver** Klasse, und die Kommentare entfernen...</span><span class="sxs-lookup"><span data-stu-id="db9bc-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="db9bc-719">Kapitel 18 – bearbeiten UnityMRNotifHub-Anwendung, NotificationReceiver-Klasse</span><span class="sxs-lookup"><span data-stu-id="db9bc-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="db9bc-720">Folgende hinzugefügt haben die **NuGet-Pakete**, müssen Sie *auskommentierung* Teil des Codes in der **NotificationReceiver** Klasse.</span><span class="sxs-lookup"><span data-stu-id="db9bc-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="db9bc-721">Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="db9bc-721">This includes:</span></span>

1. <span data-ttu-id="db9bc-722">Der Namespace am Anfang:</span><span class="sxs-lookup"><span data-stu-id="db9bc-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="db9bc-723">Sämtlichen Code innerhalb der **InitNotificationsAsync()** Methode:</span><span class="sxs-lookup"><span data-stu-id="db9bc-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="db9bc-724">Der obige Code enthält einen Kommentar: Stellen Sie sicher, dass Sie nicht versehentlich haben *unkommentierten* , der Kommentar (wie der Code nicht kompiliert, wenn man!).</span><span class="sxs-lookup"><span data-stu-id="db9bc-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="db9bc-725">Und schließlich die **Channel_PushNotificationReceived** Ereignis:</span><span class="sxs-lookup"><span data-stu-id="db9bc-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="db9bc-726">Mit diesen auskommentiert werden können stellen Sie sicher, dass Sie speichern, und fahren Sie mit der im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="db9bc-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="db9bc-727">Kapitel 19: Ordnen Sie die mixed Reality-Projekt auf die Store-app</span><span class="sxs-lookup"><span data-stu-id="db9bc-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="db9bc-728">Sie müssen jetzt Zuordnen der **mixed Reality** Projekt, um die Store-App, die Sie am Anfang des Labs in erstellt.</span><span class="sxs-lookup"><span data-stu-id="db9bc-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="db9bc-729">Öffnen Sie die Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="db9bc-729">Open the solution.</span></span>

2.  <span data-ttu-id="db9bc-730">Klicken Sie mit der rechten Maustaste auf die UWP-app-Projekt im Projektmappen-Explorer-Bereich, der zum Aufrufen **Store**, und **App mit dem Store verknüpfen...** .</span><span class="sxs-lookup"><span data-stu-id="db9bc-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Öffnen Sie die Store-Verknüpfung](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="db9bc-732">Ein neues Fenster wird angezeigt namens **zuordnen Ihrer Anwendung die Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="db9bc-733">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-733">Click **Next**.</span></span>

    ![Wechseln Sie zum nächsten Bildschirm](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="db9bc-735">Es lädt alle Anwendungen, die das Konto, das Sie sich angemeldet haben zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="db9bc-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="db9bc-736">Wenn Sie nicht mit Ihrem Konto angemeldet sind, können Sie **anmelden** auf dieser Seite.</span><span class="sxs-lookup"><span data-stu-id="db9bc-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="db9bc-737">Suchen der **Store-App-Namen** , die Sie zu Beginn dieses Tutorials erstellt, und wählen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="db9bc-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="db9bc-738">Klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-738">Then click **Next**.</span></span>

    ![Suchen Sie, und wählen Sie Ihren Store-Namen](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="db9bc-740">Klicken Sie auf **zuordnen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-740">Click **Associate**.</span></span>

    ![Verknüpfen Sie die app](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="db9bc-742">Ihre App ist nun **zugeordnete** mit der Store-App.</span><span class="sxs-lookup"><span data-stu-id="db9bc-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="db9bc-743">Dies ist zum Aktivieren von Benachrichtigungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="db9bc-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="db9bc-744">Kapitel 20: UnityMRNotifHub und UnityDesktopNotifHub Anwendungen bereitstellen</span><span class="sxs-lookup"><span data-stu-id="db9bc-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="db9bc-745">In diesem Kapitel kann einfacher, mit zwei Personen sein, wie das Ergebnis enthält sowohl apps, die ausgeführt wird, eine Ausführung auf Ihrem Desktop-Computer und der andere in Ihrem immersive Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="db9bc-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="db9bc-746">Die immersive Kopfhörer app wartet darauf, um Änderungen an der Szene (Position ändert sich von der lokalen "gameobjects") zu erhalten, und die Desktop-app wird werden Änderungen an ihren lokalen Szene (Position ändert), die an die MR app gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="db9bc-747">Es sinnvoll, die app MR zuerst bereitstellen gefolgt von der Desktop-app, sodass der Empfänger lauscht beginnen kann.</span><span class="sxs-lookup"><span data-stu-id="db9bc-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="db9bc-748">Zum Bereitstellen der **UnityMRNotifHub** -app auf Ihrem lokalen Computer:</span><span class="sxs-lookup"><span data-stu-id="db9bc-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="db9bc-749">Öffnen Sie die Projektmappendatei, die von Ihrem **UnityMRNotifHub** -app in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="db9bc-750">In der **Projektmappenplattform**Option **X86, lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="db9bc-751">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![Set-Projektkonfiguration](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="db9bc-753">Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="db9bc-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="db9bc-754">Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="db9bc-755">Zum Bereitstellen der **UnityDesktopNotifHub** -app auf dem lokalen Computer:</span><span class="sxs-lookup"><span data-stu-id="db9bc-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="db9bc-756">Öffnen Sie die Projektmappendatei, die von Ihrem **UnityDesktopNotifHub** -app in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="db9bc-757">In der **Projektmappenplattform**Option **X86, lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="db9bc-758">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="db9bc-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![Set-Projektkonfiguration](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="db9bc-760">Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="db9bc-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="db9bc-761">Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="db9bc-762">Starten Sie die mixed Reality-Anwendung, und anschließend die Desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="db9bc-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="db9bc-763">Verschieben Sie mit beiden Anwendungen, die ausgeführt wird ein Objekt in der desktop Szene (mit der linken Maustaste).</span><span class="sxs-lookup"><span data-stu-id="db9bc-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="db9bc-764">Diese Änderungen mit Feldern fester Breite werden lokal vorgenommen, serialisiert und an den Funktions-App-Dienst gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="db9bc-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="db9bc-765">Der Funktions-App-Dienst wird dann in der Tabelle zusammen mit dem Notification Hub aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="db9bc-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="db9bc-766">Müssen wurde ein Update, sendet Notification Hub aktualisierte die Daten direkt an alle registrierten Anwendungen (in diesem Fall die immersive Kopfhörer-app), die dann die eingehenden Daten zu deserialisieren, und die neuen mit Feldern fester Breite Daten auf die lokalen Objekte anwenden, Verschieben sie in der Szene.</span><span class="sxs-lookup"><span data-stu-id="db9bc-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="db9bc-767">Ihre beendet die Anwendung für Azure Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="db9bc-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="db9bc-768">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die den Azure Notification Hubs-Dienst nutzt, und ermöglichen die Kommunikation zwischen apps.</span><span class="sxs-lookup"><span data-stu-id="db9bc-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![Endprodukt-Ende](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="db9bc-770">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="db9bc-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="db9bc-771">Übung 1</span><span class="sxs-lookup"><span data-stu-id="db9bc-771">Exercise 1</span></span>

<span data-ttu-id="db9bc-772">Können Sie werden verwendet, wie Sie die Farbe der "gameobjects" ändern, und senden diese Benachrichtigung an andere apps, die die Szene anzeigen?</span><span class="sxs-lookup"><span data-stu-id="db9bc-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="db9bc-773">Übung 2</span><span class="sxs-lookup"><span data-stu-id="db9bc-773">Exercise 2</span></span>

<span data-ttu-id="db9bc-774">Können Sie Ihre app MR Verschiebung von der "gameobjects" hinzu, und finden Sie in Ihrer desktop-app unter der Szene aktualisiert?</span><span class="sxs-lookup"><span data-stu-id="db9bc-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
