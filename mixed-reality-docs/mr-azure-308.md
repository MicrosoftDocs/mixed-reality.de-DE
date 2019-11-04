---
title: Mr und Azure 308-Geräte übergreifende Benachrichtigungen
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie Azure Notification Hubs, Azure Functions und Azure Storage und Tabellen in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Benachrichtigung, Funktionen, Tabellen, Notification Hubs, hololens, immersive, VR
ms.openlocfilehash: d65750f37815efecae85e7bff85318a234079af8
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438758"
---
>[!NOTE]
><span data-ttu-id="a519b-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="a519b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a519b-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="a519b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a519b-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a519b-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="a519b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a519b-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="a519b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a519b-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="a519b-110">Mr und Azure 308: Geräte übergreifende Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="a519b-110">MR and Azure 308: Cross-device notifications</span></span>

![Endgültiges Produkt-Start](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="a519b-112">In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Notification Hubs, Azure-Tabellen und Azure Functions Notification Hubs Funktionen zu einer gemischten Reality-Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="a519b-113">**Azure Notification Hubs** ist ein Microsoft-Dienst, der es Entwicklern ermöglicht, gezielte und personalisierte Pushbenachrichtigungen an jede beliebige Plattform zu senden, die alle in der Cloud betrieben wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="a519b-114">Dadurch können Entwickler in Abhängigkeit vom jeweiligen Szenario mit Endbenutzern oder sogar zwischen verschiedenen Anwendungen kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="a519b-115">Weitere Informationen finden Sie auf der [Seite](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview) **Azure Notification Hubs** .</span><span class="sxs-lookup"><span data-stu-id="a519b-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="a519b-116">**Azure Functions** ist ein Microsoft-Dienst, der Entwicklern das Ausführen von kleinen Code Elementen ("Functions") in Azure ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a519b-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="a519b-117">Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, die viele Vorteile haben kann.</span><span class="sxs-lookup"><span data-stu-id="a519b-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="a519b-118">**Azure Functions** unterstützt mehrere Entwicklungs Sprachen, wie z. b. C\#, F\#, Node. js, Java und PHP.</span><span class="sxs-lookup"><span data-stu-id="a519b-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="a519b-119">Weitere Informationen finden Sie auf der [Seite](https://docs.microsoft.com/azure/azure-functions/functions-overview)Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="a519b-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="a519b-120">**Azure-Tabellen** sind ein Microsoft-clouddienst, mit dem Entwickler strukturierte nicht-SQL-Daten in der Cloud speichern können, sodass Sie überall problemlos zugänglich sind.</span><span class="sxs-lookup"><span data-stu-id="a519b-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="a519b-121">Der Dienst verfügt über einen Schema losen Entwurf, der die Weiterentwicklung von Tabellen nach Bedarf ermöglicht und daher sehr flexibel ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="a519b-122">Weitere Informationen finden Sie auf der [Seite](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) mit den Azure-Tabellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="a519b-123">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung und eine Desktop-PC-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="a519b-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="a519b-124">Die Desktop-PC-App ermöglicht dem Benutzer das Verschieben eines Objekts im 2D-Raum (X und Y) mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="a519b-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="a519b-125">Die Verschiebung von Objekten innerhalb der PC-APP wird mithilfe von JSON an die Cloud gesendet, die in Form einer Zeichenfolge mit einer Objekt-ID, einem Typ und Transformations Informationen (X-und Y-Koordinaten) enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="a519b-126">Die Mixed Reality-APP, die über eine identische Szene mit der Desktop-App verfügt, empfängt Benachrichtigungen bezüglich der Objekt Verschiebung aus dem Notification Hubs-Dienst (der soeben von der Desktop-PC-APP aktualisiert wurde).</span><span class="sxs-lookup"><span data-stu-id="a519b-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="a519b-127">Wenn Sie eine Benachrichtigung erhalten, die die Objekt-ID, den Typ und die Transformations Informationen enthält, wendet die Mixed Reality-APP die empfangenen Informationen auf die eigene Szene an.</span><span class="sxs-lookup"><span data-stu-id="a519b-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="a519b-128">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="a519b-129">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="a519b-130">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="a519b-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="a519b-131">Dieser Kurs ist ein eigenständiges Tutorial, das sich nicht direkt mit anderen Mixed Reality-Labs befasst.</span><span class="sxs-lookup"><span data-stu-id="a519b-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="a519b-132">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="a519b-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a519b-133">Natürlich</span><span class="sxs-lookup"><span data-stu-id="a519b-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a519b-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a519b-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a519b-135"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="a519b-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a519b-136">Mr und Azure 308: Geräte übergreifende Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="a519b-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="a519b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="a519b-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a519b-138">✔️</span><span class="sxs-lookup"><span data-stu-id="a519b-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a519b-139">Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="a519b-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="a519b-140">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="a519b-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="a519b-141">Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.</span><span class="sxs-lookup"><span data-stu-id="a519b-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a519b-142">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a519b-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a519b-143">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a519b-144">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="a519b-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="a519b-145">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="a519b-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="a519b-146">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="a519b-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a519b-147">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="a519b-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a519b-148">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="a519b-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a519b-149">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="a519b-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a519b-150">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="a519b-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a519b-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a519b-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a519b-152">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="a519b-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a519b-153">Internet Zugriff für Azure-Setup und für den Zugriff auf Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="a519b-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="a519b-154">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="a519b-154">Before you start</span></span>

- <span data-ttu-id="a519b-155">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="a519b-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="a519b-156">Sie müssen der Besitzer des Microsoft-Entwickler Portals und des Anwendungs Registrierungs Portals sein. andernfalls haben Sie in [Kapitel 2](#chapter-2---retrieve-your-new-apps-credentials)keine Berechtigung für den Zugriff auf die app.</span><span class="sxs-lookup"><span data-stu-id="a519b-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="a519b-157">Kapitel 1: Erstellen einer Anwendung im Microsoft-Entwickler Portal</span><span class="sxs-lookup"><span data-stu-id="a519b-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="a519b-158">Um den **Azure Notification Hubs** -Dienst zu verwenden, müssen Sie eine Anwendung im Microsoft-Entwickler Portal erstellen, da Ihre Anwendung registriert werden muss, damit Benachrichtigungen gesendet und empfangen werden können.</span><span class="sxs-lookup"><span data-stu-id="a519b-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="a519b-159">Melden Sie sich beim [Microsoft-Entwickler Portal](https://developer.microsoft.com/dashboard)an.</span><span class="sxs-lookup"><span data-stu-id="a519b-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="a519b-160">Sie müssen sich bei Ihrem Microsoft-Konto anmelden.</span><span class="sxs-lookup"><span data-stu-id="a519b-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="a519b-161">Klicken Sie im Dashboard auf **neue APP erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Erstellen einer APP](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="a519b-163">Es wird ein Popup Fenster angezeigt, in dem Sie einen Namen für die neue APP reservieren müssen.</span><span class="sxs-lookup"><span data-stu-id="a519b-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="a519b-164">Fügen Sie im Textfeld einen entsprechenden Namen ein. Wenn der ausgewählte Name verfügbar ist, wird rechts neben dem Textfeld ein Tick angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="a519b-165">Nachdem Sie einen verfügbaren Namen eingefügt haben, klicken Sie unten links im Popup Fenster auf die Schaltfläche **Produktname reservieren** .</span><span class="sxs-lookup"><span data-stu-id="a519b-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![Umkehren eines Namens](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="a519b-167">Nachdem Sie die App erstellt haben, können Sie mit dem nächsten Kapitel fortfahren.</span><span class="sxs-lookup"><span data-stu-id="a519b-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="a519b-168">Kapitel 2: Abrufen der Anmelde Informationen für neue apps</span><span class="sxs-lookup"><span data-stu-id="a519b-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="a519b-169">Melden Sie sich beim Anwendungs Registrierungs Portal an, auf dem die neue APP aufgelistet wird, und rufen Sie die Anmelde Informationen ab, die zum Einrichten des **Notification Hubs Dienstanbieter** im **Azure-Portal**verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="a519b-170">Navigieren Sie zum [Anwendungs Registrierungs Portal](https://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a519b-170">Navigate to the [Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

    ![Anwendungs Registrierungs Portal](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="a519b-172">Sie müssen sich für die Anmeldung mit Ihrem Microsoft-Konto anmelden.</span><span class="sxs-lookup"><span data-stu-id="a519b-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="a519b-173">Dabei **muss** es sich um das Microsoft-Konto handeln, das Sie im vorherigen [Kapitel](#chapter-1---create-an-application-on-the-microsoft-developer-portal)mit dem Windows Store-Entwickler Portal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="a519b-174">Sie finden Ihre APP im Abschnitt " **meine Anwendungen** ".</span><span class="sxs-lookup"><span data-stu-id="a519b-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="a519b-175">Nachdem Sie Sie gefunden haben, klicken Sie darauf, und Sie gelangen zu einer neuen Seite, die den APP-Namen und die **Registrierung**enthält.</span><span class="sxs-lookup"><span data-stu-id="a519b-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![Ihre neu registrierte App](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="a519b-177">Scrollen Sie nach unten auf der Registrierungsseite, um den Abschnitt mit den **geheimen Anwendungen** und die **Paket-sid** für Ihre APP zu finden.</span><span class="sxs-lookup"><span data-stu-id="a519b-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="a519b-178">Kopieren Sie beide für die Verwendung mit der Einrichtung des **Azure-Notification Hubs Dienstanbieter** im nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="a519b-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![Anwendungs Geheimnisse](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="a519b-180">Kapitel 3: Einrichten des Azure-Portals: Erstellen Notification Hubs Dienstanbieter</span><span class="sxs-lookup"><span data-stu-id="a519b-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="a519b-181">Nachdem Sie die Anmelde Informationen für Ihre apps abgerufen haben, müssen Sie zum Azure-Portal wechseln, in dem Sie einen Azure Notification Hubs-Dienst erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="a519b-182">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="a519b-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="a519b-183">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a519b-184">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a519b-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="a519b-185">Nachdem Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach **Notification Hub**, und drücken Sie die ***Eingabe***Taste.</span><span class="sxs-lookup"><span data-stu-id="a519b-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![nach benachrichtigungshub suchen](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="a519b-187">Das Wort ***New*** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="a519b-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="a519b-188">Auf der neuen Seite wird eine Beschreibung des *Notification Hubs* Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a519b-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="a519b-189">Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Benachrichtigungs-Hubs-Instanz erstellen](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="a519b-191">Nachdem Sie auf ***Erstellen***geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="a519b-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="a519b-192">Fügen Sie den gewünschten Namen für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="a519b-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="a519b-193">Geben Sie einen **Namespace** an, den Sie dieser APP zuordnen können.</span><span class="sxs-lookup"><span data-stu-id="a519b-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="a519b-194">Wählen Sie einen **Speicherort aus.**</span><span class="sxs-lookup"><span data-stu-id="a519b-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="a519b-195">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="a519b-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a519b-196">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="a519b-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a519b-197">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a519b-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="a519b-198">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a519b-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="a519b-199">Wählen Sie ein entsprechendes **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="a519b-200">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="a519b-201">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-201">Select **Create**.</span></span>

        ![Dienst Details ausfüllen](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="a519b-203">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="a519b-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="a519b-204">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Benachrichtigung](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="a519b-206">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="a519b-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="a519b-207">Sie gelangen zu ihrer neuen **Notification Hub** -Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="a519b-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Gehe zu Ressource](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="a519b-209">Klicken Sie auf der Übersichtsseite in der Mitte der Seite auf **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="a519b-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="a519b-210">Der Bereich auf der rechten Seite ändert sich, um zwei Textfelder anzuzeigen, die die **Paket-sid** und den **Sicherheitsschlüssel**benötigen, von der APP, die Sie zuvor eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![neu erstellter Hubs-Dienst](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="a519b-212">Nachdem Sie die Details in die richtigen Felder kopiert haben, klicken Sie auf **Speichern**, und Sie erhalten eine Benachrichtigung, wenn der Notification Hub erfolgreich aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a519b-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Sicherheitsdetails kopieren](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="a519b-214">Kapitel 4: Einrichten des Azure-Portals: Erstellen eines Tabellen Dienstanbieter</span><span class="sxs-lookup"><span data-stu-id="a519b-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="a519b-215">Nachdem Sie Ihre Notification Hubs Dienst Instanz erstellt haben, navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie einen Azure Tables-Dienst erstellen, indem Sie eine Speicher Ressource erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="a519b-216">Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="a519b-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="a519b-217">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach **Speicherkonto**, und drücken Sie die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="a519b-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="a519b-218">Das Wort ***New*** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="a519b-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="a519b-219">Wählen Sie **Speicherkonto-BLOB, Datei, Tabelle, Warteschlange** aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Suchen nach Speicherkonto](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="a519b-221">Auf der neuen Seite wird eine Beschreibung des **Speicherkonto** Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a519b-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="a519b-222">Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="a519b-224">Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a519b-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="a519b-225">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein (nur Kleinbuchstaben).</span><span class="sxs-lookup"><span data-stu-id="a519b-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="a519b-226">Klicken Sie unter **Bereitstellungs Modell**auf **Ressourcen-Manager**.</span><span class="sxs-lookup"><span data-stu-id="a519b-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="a519b-227">Wählen Sie unter **Kontoart**im Dropdown Menü die Option **Speicher (universell v1)** aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="a519b-228">Wählen Sie einen geeigneten **Speicherort**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="a519b-229">Wählen Sie für das Dropdown Menü **Replikation** die Option **Lesezugriff georedundanter Speicher (RA-GRS)** aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="a519b-230">Klicken Sie für die **Leistung**auf **Standard**.</span><span class="sxs-lookup"><span data-stu-id="a519b-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="a519b-231">Wählen Sie im Abschnitt **sichere Übertragung erforderlich** die Option **deaktiviert**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="a519b-232">Wählen Sie im Dropdown Menü **Abonnement** ein entsprechendes Abonnement aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="a519b-233">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="a519b-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a519b-234">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="a519b-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a519b-235">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a519b-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="a519b-236">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a519b-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="a519b-237">Lassen Sie **virtuelle Netzwerke** **deaktiviert** , wenn dies eine Option für Sie ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="a519b-238">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-238">Click **Create**.</span></span>

        ![Speicher Details ausfüllen](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="a519b-240">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="a519b-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="a519b-241">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="a519b-242">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="a519b-242">Click on the notifications to explore your new Service instance.</span></span>

    ![neue Speicher Benachrichtigung](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="a519b-244">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="a519b-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="a519b-245">Sie gelangen zur Übersichtsseite der neuen Speicherdienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="a519b-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Gehe zu Ressource](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="a519b-247">Klicken Sie auf der Seite Übersicht auf die Rechte Seite, und klicken Sie auf **Tabellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="a519b-248">Der Bereich auf der rechten Seite ändert sich, um die **Tabellen Dienst** Informationen anzuzeigen, in denen Sie eine neue Tabelle hinzufügen müssen.</span><span class="sxs-lookup"><span data-stu-id="a519b-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="a519b-249">Klicken Sie hierzu auf die Schaltfläche **+** **Tabelle** in der linken oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="a519b-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Öffnen von Tabellen](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="a519b-251">Es wird eine neue Seite angezeigt, auf der Sie einen **Tabellennamen**eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="a519b-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="a519b-252">Dies ist der Name, den Sie in späteren Kapiteln verwenden, um auf die Daten in Ihrer Anwendung zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="a519b-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="a519b-253">Fügen Sie einen entsprechenden Namen ein, und klicken Sie auf **OK**</span><span class="sxs-lookup"><span data-stu-id="a519b-253">Insert an appropriate name and click **OK**.</span></span>

    ![neue Tabelle erstellen](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="a519b-255">Nachdem die neue Tabelle erstellt wurde, können Sie Sie auf der Seite **Tabellen Dienst** (unten) sehen.</span><span class="sxs-lookup"><span data-stu-id="a519b-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![neue Tabelle erstellt](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="a519b-257">Kapitel 5: Abschließen der Azure-Tabelle in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a519b-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="a519b-258">Nachdem Sie das Speicher **Dienst** -Speicherkonto eingerichtet haben, ist es an der Zeit, Daten hinzuzufügen, die zum Speichern und Abrufen von Informationen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="a519b-259">Die Bearbeitung der Tabellen kann über **Visual Studio**erfolgen.</span><span class="sxs-lookup"><span data-stu-id="a519b-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="a519b-260">Öffnen Sie **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a519b-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="a519b-261">Klicken Sie im Menü auf > **Cloud-Explorer** **anzeigen** .</span><span class="sxs-lookup"><span data-stu-id="a519b-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Cloud-Explorer öffnen](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="a519b-263">Der **Cloud-Explorer** wird als angedocktes Element geöffnet (als "Patient", da der Ladevorgang Zeit in Anspruch nehmen kann).</span><span class="sxs-lookup"><span data-stu-id="a519b-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="a519b-264">Wenn das Abonnement, das Sie zum Erstellen Ihrer *Speicher Konten* verwendet haben, nicht sichtbar ist, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="a519b-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="a519b-265">Sie sind beim gleichen Konto angemeldet, das Sie für das Azure-Portal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="a519b-266">Wählen Sie auf der Seite "Kontoverwaltung" Ihr Abonnement aus (möglicherweise müssen Sie einen Filter aus Ihren Kontoeinstellungen anwenden):</span><span class="sxs-lookup"><span data-stu-id="a519b-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Abonnement suchen](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="a519b-268">Ihre Azure-Clouddienste werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="a519b-269">Suchen Sie nach **Speicher Konten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="a519b-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Öffnen von Speicher Konten](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="a519b-271">Nach der Erweiterung sollte Ihr neu erstelltes **Speicherkonto** verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="a519b-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="a519b-272">Klicken Sie auf den Pfeil links neben dem Speicher, und wählen Sie dann nach dem Erweitern der Tabelle **Tabellen** aus, und klicken Sie auf den Pfeil daneben, um die **Tabelle** anzuzeigen, die Sie im letzten Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="a519b-273">Doppelklicken Sie auf die **Tabelle**.</span><span class="sxs-lookup"><span data-stu-id="a519b-273">Double click your **Table**.</span></span>

    ![Tabelle "Scene Objects" öffnen](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="a519b-275">Ihre Tabelle wird in der Mitte Ihres Visual Studio-Fensters geöffnet.</span><span class="sxs-lookup"><span data-stu-id="a519b-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="a519b-276">Klicken Sie auf das Symboltabelle mit dem **+** (plus).</span><span class="sxs-lookup"><span data-stu-id="a519b-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="a519b-278">Ein Fenster wird angezeigt, in dem Sie aufgefordert werden, *Entitäten hinzuzufügen*.</span><span class="sxs-lookup"><span data-stu-id="a519b-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="a519b-279">Sie erstellen insgesamt drei Entitäten mit jeweils mehreren Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="a519b-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="a519b-280">Sie werden feststellen, dass *PartitionKey* und *RowKey* bereits bereitgestellt werden, da diese von der Tabelle zum Suchen Ihrer Daten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![Partitions-und Zeilen Schlüssel](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="a519b-282">Aktualisieren Sie den *Wert* von **PartitionKey** und **RowKey** wie folgt (denken Sie daran, diesen Schritt für jede hinzu zufügende Zeilen Eigenschaft auszuführen, obwohl Sie den RowKey jedes Mal erhöhen):</span><span class="sxs-lookup"><span data-stu-id="a519b-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![korrekte Werte hinzufügen](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="a519b-284">Klicken Sie auf **Eigenschaft hinzufügen** , um zusätzliche Daten Zeilen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="a519b-285">Erstellen Sie die erste leere Tabelle mit der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="a519b-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="a519b-286">Klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a519b-286">Click **OK** when you are finished.</span></span>

    ![Klicken Sie abschließend auf OK.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="a519b-288">Stellen Sie sicher, dass Sie den **Typ** der **X**-, **Y**-und **Z**-Einträge in " **Double**" geändert haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="a519b-289">Sie werden feststellen, dass die Tabelle nun eine Daten Zeile enthält.</span><span class="sxs-lookup"><span data-stu-id="a519b-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="a519b-290">Klicken Sie erneut auf das Symbol **+** (plus), um eine weitere Entität hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![erste Zeile](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="a519b-292">Erstellen Sie eine zusätzliche Eigenschaft, und legen Sie dann die Werte der neuen Entität entsprechend den unten gezeigten fest.</span><span class="sxs-lookup"><span data-stu-id="a519b-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Cube hinzufügen](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="a519b-294">Wiederholen Sie den letzten Schritt zum Hinzufügen einer weiteren Entität.</span><span class="sxs-lookup"><span data-stu-id="a519b-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="a519b-295">Legen Sie die Werte für diese Entität auf die unten angezeigten Werte fest.</span><span class="sxs-lookup"><span data-stu-id="a519b-295">Set the values for this entity to those shown below.</span></span>

    ![Zylinder hinzufügen](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="a519b-297">Die Tabelle sollte nun wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="a519b-297">Your table should now look like the one below.</span></span>

    ![Tabelle ist fertiggestellt](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="a519b-299">Sie haben dieses Kapitel abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a519b-299">You have completed this Chapter.</span></span> <span data-ttu-id="a519b-300">Stellen Sie sicher, dass Sie speichern.</span><span class="sxs-lookup"><span data-stu-id="a519b-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="a519b-301">Kapitel 6: Erstellen eines Azure-Funktionen-App</span><span class="sxs-lookup"><span data-stu-id="a519b-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="a519b-302">Erstellen Sie eine Azure-Funktionen-APP, die von der Desktop Anwendung aufgerufen wird, um den **Tabellen** Dienst zu aktualisieren und eine Benachrichtigung über den **Notification Hub**zu senden.</span><span class="sxs-lookup"><span data-stu-id="a519b-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="a519b-303">Zunächst müssen Sie eine Datei erstellen, die es ihrer Azure-Funktion ermöglicht, die benötigten Bibliotheken zu laden.</span><span class="sxs-lookup"><span data-stu-id="a519b-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="a519b-304">Öffnen Sie **Notepad** (drücken Sie Windows-Taste, und geben Sie Notepad ein).</span><span class="sxs-lookup"><span data-stu-id="a519b-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Editor öffnen](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="a519b-306">Fügen Sie bei geöffneter Notepad die JSON-Struktur unten ein.</span><span class="sxs-lookup"><span data-stu-id="a519b-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="a519b-307">Wenn Sie dies abgeschlossen haben, speichern Sie es auf Ihrem Desktop als " **Project. JSON**".</span><span class="sxs-lookup"><span data-stu-id="a519b-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="a519b-308">Es ist wichtig, dass die Benennung korrekt ist: Stellen Sie sicher, dass Sie nicht über die Dateierweiterung " **. txt** " verfügt.</span><span class="sxs-lookup"><span data-stu-id="a519b-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="a519b-309">Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden, wenn Sie nuget verwendet haben, wird Sie vertraut aussehen.</span><span class="sxs-lookup"><span data-stu-id="a519b-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="a519b-310">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="a519b-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="a519b-311">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf " **neu** ", und suchen Sie nach **Funktionen-App**. Drücken Sie dann die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="a519b-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![nach Funktionen-App suchen](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="a519b-313">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="a519b-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="a519b-314">Auf der neuen Seite wird eine Beschreibung des **Funktionen-App** Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a519b-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="a519b-315">Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Funktionen-app-Instanz](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="a519b-317">Nachdem Sie auf **Erstellen**geklickt haben, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="a519b-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="a519b-318">Fügen Sie für **App-Name**den gewünschten Namen für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="a519b-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="a519b-319">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="a519b-320">Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen **Funktionen-App Dienst**erstellen, sollte Ihnen ein Free-Tarif zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="a519b-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="a519b-321">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="a519b-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a519b-322">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="a519b-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a519b-323">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="a519b-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="a519b-324">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a519b-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="a519b-325">Klicken Sie für **Betriebssystem**auf Windows, da dies die beabsichtigte Plattform ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="a519b-326">Wählen Sie einen **Hostingplan** aus (in diesem Tutorial wird ein **Verbrauchs Plan**verwendet.)</span><span class="sxs-lookup"><span data-stu-id="a519b-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="a519b-327">Wählen Sie einen **Standort** **aus (Wählen Sie den gleichen Speicherort wie für den Speicher aus, den Sie im vorherigen Schritt erstellt haben)** .</span><span class="sxs-lookup"><span data-stu-id="a519b-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="a519b-328">Im Abschnitt **Speicher** **müssen Sie den Speicherdienst auswählen, den Sie im vorherigen Schritt erstellt**haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="a519b-329">Sie benötigen keine *Application Insights* in dieser APP, sodass Sie Sie nicht mehr **Deaktivieren**können.</span><span class="sxs-lookup"><span data-stu-id="a519b-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="a519b-330">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-330">Click **Create**.</span></span>

        ![neue Instanz erstellen](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="a519b-332">Nachdem Sie auf " **Erstellen** " geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="a519b-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="a519b-333">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![neue Benachrichtigung](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="a519b-335">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="a519b-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="a519b-336">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="a519b-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Gehe zu Ressource](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="a519b-338">Klicken Sie neben *Functions*auf das Symbol **+** (plus), um *neu zu erstellen*.</span><span class="sxs-lookup"><span data-stu-id="a519b-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![neue Funktion hinzufügen](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="a519b-340">Im mittleren Bereich wird das Fenster für die **Funktions** Erstellung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="a519b-341">Ignorieren Sie die Informationen in der oberen Hälfte des Panels, und klicken Sie auf **benutzerdefinierte Funktion**, die sich am unteren Rand befindet (im blauen Bereich, wie unten gezeigt).</span><span class="sxs-lookup"><span data-stu-id="a519b-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="a519b-343">Die neue Seite innerhalb des Fensters zeigt verschiedene Funktionstypen.</span><span class="sxs-lookup"><span data-stu-id="a519b-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="a519b-344">Scrollen Sie nach unten, um die lila Typen anzuzeigen, und klicken Sie auf **http Put** -Element.</span><span class="sxs-lookup"><span data-stu-id="a519b-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![Link "http Put"](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="a519b-346">Möglicherweise müssen Sie nach unten auf der Seite einen Bildlauf durchführen (dieses Bild sieht möglicherweise nicht genau aus, wenn Aktualisierungen des Azure-Portals stattfinden), suchen Sie jedoch nach einem Element mit dem Namen " *http Put*".</span><span class="sxs-lookup"><span data-stu-id="a519b-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="a519b-347">Das Fenster **http Put** wird angezeigt, in dem Sie die Funktion konfigurieren müssen (siehe unten für Image).</span><span class="sxs-lookup"><span data-stu-id="a519b-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="a519b-348">Wählen Sie unter **Sprache** im Dropdown Menü die Option C-\#aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="a519b-349">Geben Sie **unter Name** einen entsprechenden Namen ein.</span><span class="sxs-lookup"><span data-stu-id="a519b-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="a519b-350">Wählen Sie im Dropdown Menü **Authentifizierungs Ebene** die Option **Funktion**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="a519b-351">Für den **Tabellennamen** Abschnitt müssen Sie den genauen Namen verwenden, den Sie zuvor verwendet haben, um den **Tabellen** Dienst zu erstellen (einschließlich desselben Buchstabens).</span><span class="sxs-lookup"><span data-stu-id="a519b-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="a519b-352">Verwenden Sie im Abschnitt **Speicherkonto Verbindung** das Dropdown Menü, und wählen Sie dann Ihr Speicherkonto aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="a519b-353">Wenn dies nicht der Fall ist, klicken Sie neben dem Abschnitts Titel auf den **neuen** Link, um ein anderes Panel anzuzeigen, in dem das Speicherkonto aufgelistet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a519b-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![neuer Speicher](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="a519b-355">Wenn Sie auf **Erstellen** klicken, erhalten Sie eine Benachrichtigung, dass die Einstellungen erfolgreich aktualisiert wurden.</span><span class="sxs-lookup"><span data-stu-id="a519b-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Create-Funktion](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="a519b-357">Nachdem Sie auf **Erstellen**geklickt haben, werden Sie zum Funktions-Editor umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="a519b-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![Funktionscode aktualisieren](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="a519b-359">Fügen Sie den folgenden Code in den Funktions-Editor ein (ersetzen Sie den Code in der Funktion):</span><span class="sxs-lookup"><span data-stu-id="a519b-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="a519b-360">Mithilfe der enthaltenen Bibliotheken empfängt die-Funktion den Namen und den Speicherort des Objekts, das in der Unity-Szene verschoben wurde C# (als ein-Objekt namens **unitygameobject**).</span><span class="sxs-lookup"><span data-stu-id="a519b-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="a519b-361">Dieses Objekt wird dann verwendet, um die Objekt Parameter in der erstellten Tabelle zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="a519b-362">Danach ruft die Funktion den erstellten Notification Hub-Dienst auf, der alle abonnierten Anwendungen benachrichtigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="a519b-363">Klicken Sie mit dem Code auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a519b-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="a519b-364">Klicken Sie anschließend auf der rechten Seite der Seite auf das Symbol **\<** (Pfeil).</span><span class="sxs-lookup"><span data-stu-id="a519b-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Uploadpanel öffnen](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="a519b-366">Ein Panel wird von rechts nach rechts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-366">A panel will slide in from the right.</span></span> <span data-ttu-id="a519b-367">Klicken Sie in diesem Bereich auf **hochladen**, und ein Datei Browser wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="a519b-368">Navigieren Sie zu, und klicken Sie auf die Datei **Project. JSON** , die Sie **zuvor im** Editor erstellt haben, und klicken Sie dann auf die Schaltfläche **Öffnen** .</span><span class="sxs-lookup"><span data-stu-id="a519b-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="a519b-369">Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-369">This file defines the libraries that your function will use.</span></span>

    ![JSON hochladen](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="a519b-371">Wenn die Datei hochgeladen wurde, wird Sie im Panel auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="a519b-372">Wenn Sie darauf klicken, wird es im **Funktions** -Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="a519b-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="a519b-373">Es muss **genau** wie das nächste Bild aussehen (unterschritt 23).</span><span class="sxs-lookup"><span data-stu-id="a519b-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="a519b-374">Klicken Sie dann im Bereich links unterhalb von **Functions**auf den Link **integrieren** .</span><span class="sxs-lookup"><span data-stu-id="a519b-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![Integration-Funktion](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="a519b-376">Klicken Sie auf der nächsten Seite in der oberen rechten Ecke auf erweiterter **Editor** (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="a519b-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![Öffnen des erweiterten Editors](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="a519b-378">Eine **Function. JSON** -Datei wird im mittleren Bereich geöffnet, der durch den folgenden Code Ausschnitt ersetzt werden muss.</span><span class="sxs-lookup"><span data-stu-id="a519b-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="a519b-379">Definiert die Funktion, die Sie entwickeln, und die Parameter, die an die Funktion übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="a519b-380">Der Editor sollte nun wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="a519b-380">Your editor should now look like the image below:</span></span>

    ![zurück zum Standard-Editor](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="a519b-382">Sie bemerken möglicherweise, dass die Eingabeparameter, die Sie gerade eingefügt haben, nicht mit den Tabellen-und Speicher Details identisch sind und daher mit ihren Informationen aktualisiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="a519b-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="a519b-383">Gehen Sie **hier nicht**wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="a519b-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="a519b-384">Klicken Sie einfach auf den Link **Standard-Editor** in der oberen rechten Ecke der Seite, um zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="a519b-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="a519b-385">Klicken Sie im **Standard-Editor**unter **Eingaben**auf **Azure Table Storage (Tabelle)** .</span><span class="sxs-lookup"><span data-stu-id="a519b-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Tabellen Eingaben](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="a519b-387">Stellen Sie sicher, dass die folgenden Informationen mit **ihren** Informationen identisch sind, da Sie unterschiedlich sein können (es gibt eine Abbildung unterhalb der folgenden Schritte):</span><span class="sxs-lookup"><span data-stu-id="a519b-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="a519b-388">**Tabellenname**: der Name der Tabelle, die Sie im Azure Storage Tabellen Dienst erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="a519b-389">**Speicherkonto Verbindung:** klicken Sie auf **neu**, das neben dem Dropdown Menü angezeigt wird, und rechts neben dem Fenster wird ein Panel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![neuer Speicher](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="a519b-391">Wählen Sie Ihr **Speicherkonto**aus, das Sie zuvor erstellt haben, um die **Funktionen-apps** zu hosten.</span><span class="sxs-lookup"><span data-stu-id="a519b-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="a519b-392">Sie werden feststellen, dass der Wert für die **Speicherkonto** Verbindung erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a519b-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="a519b-393">Stellen Sie sicher, dass Sie nach Abschluss des Vorgangs auf **Speichern** klicken.</span><span class="sxs-lookup"><span data-stu-id="a519b-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="a519b-394">Die Seite **Eingaben** sollte nun mit den unten aufgeführten Informationen identisch **sein** .</span><span class="sxs-lookup"><span data-stu-id="a519b-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![Eingaben sind beendet](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="a519b-396">Klicken Sie anschließend unter **Ausgaben**auf **Azure Notification Hub (Benachrichtigung)** .</span><span class="sxs-lookup"><span data-stu-id="a519b-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="a519b-397">Stellen Sie sicher, dass die folgenden Informationen mit **ihren** Informationen übereinstimmen, da Sie unterschiedlich sein können (es gibt eine Abbildung unterhalb der folgenden Schritte):</span><span class="sxs-lookup"><span data-stu-id="a519b-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="a519b-398">**Notification Hub-Name**: Dies ist der Name der **Notification Hub** -Dienst Instanz, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="a519b-399">**Notification Hubs-Namespace Verbindung**: Klicken Sie auf **neu**, das neben dem Dropdown Menü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![Ausgaben überprüfen](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="a519b-401">Das **Popup-** Popup Fenster wird angezeigt (siehe Abbildung unten), in dem Sie den **Namespace** des **Benachrichtigungs-Hubs**auswählen müssen, den Sie zuvor eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="a519b-402">Wählen Sie den Namen Ihres **Notification Hubs** im Dropdown Menü in der Mitte aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="a519b-403">Legen Sie das Dropdown Menü **Richtlinie** auf **defaultfullsharedaccesssignature**fest.</span><span class="sxs-lookup"><span data-stu-id="a519b-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="a519b-404">Klicken Sie auf die Schaltfläche **auswählen** , um zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="a519b-404">Click the **Select** button to go back.</span></span>

        ![Ausgabe Update](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="a519b-406">Die Seite **Ausgaben** sollte nun mit den unten angegebenen Informationen, jedoch mit ihren Informationen, identisch **sein** .</span><span class="sxs-lookup"><span data-stu-id="a519b-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="a519b-407">Stellen Sie sicher, dass Sie auf **Speichern**klicken.</span><span class="sxs-lookup"><span data-stu-id="a519b-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="a519b-408">*Bearbeiten Sie den Notification Hub-Namen nicht direkt* (Dies sollte alle mithilfe der **Erweiterter Editor**erfolgen, vorausgesetzt, Sie haben die vorherigen Schritte ordnungsgemäß befolgt.</span><span class="sxs-lookup"><span data-stu-id="a519b-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="a519b-410">An diesem Punkt sollten Sie die Funktion testen, um sicherzustellen, dass Sie funktioniert.</span><span class="sxs-lookup"><span data-stu-id="a519b-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="a519b-411">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a519b-411">To do this:</span></span> 

    1. <span data-ttu-id="a519b-412">Navigieren Sie noch einmal zur funktionsseite:</span><span class="sxs-lookup"><span data-stu-id="a519b-412">Navigate to the function page once more:</span></span>

        ![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="a519b-414">Klicken Sie auf der Seite Funktion auf die Registerkarte **Test** ganz rechts auf der Seite, um das Blatt " *Test* " zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="a519b-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="a519b-416">Fügen Sie im Textfeld **Anforderungs** Text des Blatts den folgenden Code ein:</span><span class="sxs-lookup"><span data-stu-id="a519b-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="a519b-417">Wenn der Testcode vorhanden ist, klicken Sie unten rechts auf die Schaltfläche **Ausführen** , und der Test wird ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a519b-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="a519b-418">Die Ausgabe Protokolle des Tests werden im Konsolen Bereich unterhalb Ihres Funktions Codes angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="a519b-420">Wenn der obige Test fehlschlägt, müssen Sie überprüfen, ob Sie die obigen Schritte genau befolgt haben. Dies gilt insbesondere für die Einstellungen im Bereich **integrieren**.</span><span class="sxs-lookup"><span data-stu-id="a519b-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="a519b-421">Kapitel 7: Einrichten eines Desktop-Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="a519b-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a519b-422">Die Desktop Anwendung, die Sie jetzt erstellen, funktioniert **nicht** im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="a519b-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="a519b-423">Er muss außerhalb des Editors ausgeführt werden, und zwar nach dem Anwendungs Aufbau, mithilfe von Visual Studio (oder der bereitgestellten Anwendung).</span><span class="sxs-lookup"><span data-stu-id="a519b-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="a519b-424">Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Unity und gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="a519b-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="a519b-425">Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="a519b-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="a519b-426">Für diesen Kurs benötigen Sie **keine** Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="a519b-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="a519b-427">Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, befolgen Sie diesen [Link zum Einrichten von Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="a519b-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="a519b-428">Öffnen Sie **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="a519b-428">Open **Unity** and click **New**.</span></span>

    ![neues Unity-Projekt](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="a519b-430">Sie müssen einen Unity-Projektnamen angeben und **unitydesktopnotifhub**einfügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="a519b-431">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="a519b-432">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="a519b-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a519b-433">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-433">Then, click **Create project**.</span></span>

    ![Projekt erstellen](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="a519b-435">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a519b-436">Wechseln Sie zu Edit > **Preferences (Einstellungen** **Bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="a519b-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a519b-437">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a519b-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a519b-438">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="a519b-438">Close the **Preferences** window.</span></span>

    ![Festlegen externer vs-Tools](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="a519b-440">Navigieren Sie als nächstes zu **Datei** > **Buildeinstellungen** , wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen</span><span class="sxs-lookup"><span data-stu-id="a519b-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Plattformen wechseln](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="a519b-442">Stellen Sie sicher, dass in **Datei** > **Buildeinstellungen**Folgendes sichergestellt ist:</span><span class="sxs-lookup"><span data-stu-id="a519b-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="a519b-443">Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="a519b-444">Diese Anwendung wird für Ihren Desktop verwendet, daher muss es sich um **ein beliebiges Gerät** handeln.</span><span class="sxs-lookup"><span data-stu-id="a519b-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="a519b-445">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="a519b-446">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="a519b-447">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="a519b-448">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="a519b-449">In diesem Fall lohnt es sich, die Szene zu speichern und dem Build hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="a519b-450">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a519b-451">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-451">A save window will appear.</span></span>

            ![Hinzufügen offener Szenen](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="a519b-453">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="a519b-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![neuer Szenen Ordner](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="a519b-455">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld **Dateiname:** Text den Text **NH\_Desktop\_Scene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a519b-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![neues NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="a519b-457">Die restlichen Einstellungen in den **Buildeinstellungen**sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="a519b-458">Klicken Sie im gleichen Fenster auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="a519b-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="a519b-459">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="a519b-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="a519b-460">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="a519b-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a519b-461">Die **Skript Lauf Zeit Version** sollte **experimentell sein (.NET 4,6-Entsprechung)** .</span><span class="sxs-lookup"><span data-stu-id="a519b-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="a519b-462">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="a519b-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="a519b-463">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="a519b-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4,6 NET-Version](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="a519b-465">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a519b-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a519b-466">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="a519b-466">**InternetClient**</span></span>

            ![Internet Client Tick](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="a519b-468">Zurück in **Buildeinstellungen** : *Unity C-\# Projekte* sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="a519b-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="a519b-469">Schließen Sie das Fenster mit den **Buildeinstellungen** .</span><span class="sxs-lookup"><span data-stu-id="a519b-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="a519b-470">Speichern Sie Ihre Szene und Projekt **Datei** > speichern Sie die **Szene/Datei** > speichern Sie das **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="a519b-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a519b-471">Wenn Sie die *Unity-Setup* Komponente für dieses Projekt (Desktop-App) überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann im Kapitel fortfahren. [ 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="a519b-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="a519b-472">Sie müssen weiterhin die Skript Komponenten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="a519b-473">Kapitel 8: Importieren der DLLs in Unity</span><span class="sxs-lookup"><span data-stu-id="a519b-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="a519b-474">Sie verwenden Azure Storage für Unity (das wiederum das .NET SDK für Azure nutzt).</span><span class="sxs-lookup"><span data-stu-id="a519b-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="a519b-475">Weitere Informationen finden Sie unter diesem [Link zu Azure Storage für Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="a519b-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="a519b-476">Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="a519b-477">Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="a519b-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="a519b-478">Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [ **. unitypackage**](https://aka.ms/azstorage-unitysdk) von GitHub heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="a519b-479">Gehen Sie dann wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a519b-479">Then, do the following:</span></span>

1.  <span data-ttu-id="a519b-480">Fügen Sie das **. unitypackage** zu Unity hinzu, indem Sie die Menüoption **Assets \> \> benutzerdefiniertes Paket importieren** verwenden.</span><span class="sxs-lookup"><span data-stu-id="a519b-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="a519b-481">Im Feld " **Unity-Paket importieren** ", das angezeigt wird, können Sie unter \* \**Plug* -in \> \* Storage \* \* \* die Option Alles auswählen.</span><span class="sxs-lookup"><span data-stu-id="a519b-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="a519b-482">Deaktivieren Sie alles andere, da es für diesen Kurs nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![in Paket importieren](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="a519b-484">Klicken Sie auf die Schaltfläche ***importieren*** , um dem Projekt die Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="a519b-485">Wechseln Sie in der Projektansicht **unter Plug** -in zum Ordner **Speicher** , und wählen Sie *nur*die folgenden Plug-ins aus:</span><span class="sxs-lookup"><span data-stu-id="a519b-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="a519b-486">Microsoft. Data. Edm</span><span class="sxs-lookup"><span data-stu-id="a519b-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="a519b-487">Microsoft. Data. odata</span><span class="sxs-lookup"><span data-stu-id="a519b-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="a519b-488">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="a519b-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="a519b-489">"Newtonsoft. JSON"</span><span class="sxs-lookup"><span data-stu-id="a519b-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="a519b-490">System. Spatial</span><span class="sxs-lookup"><span data-stu-id="a519b-490">System.Spatial</span></span>

![alle Plattformen deaktivieren](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="a519b-492">Wenn *Sie diese speziellen* Plug-Ins **ausgewählt haben, deaktivieren Sie** **eine beliebige Plattform** **, deaktivieren Sie** **wsaplayer** , und klicken Sie auf **anwenden**.</span><span class="sxs-lookup"><span data-stu-id="a519b-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Platt Form-DLLs anwenden](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="a519b-494">Wir markieren diese bestimmten Plug-ins, sodass Sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="a519b-495">Dies liegt daran, dass im WSA-Ordner verschiedene Versionen der gleichen Plug-ins vorhanden sind, die nach dem Exportieren des Projekts aus Unity verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="a519b-496">Wählen Sie im Ordner **Storage** -Plug-in nur die Option:</span><span class="sxs-lookup"><span data-stu-id="a519b-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="a519b-497">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="a519b-497">Microsoft.Data.Services.Client</span></span>

        !["nicht verarbeiten" für DLLs festlegen](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="a519b-499">Aktivieren Sie das Kontrollkästchen **nicht verarbeiten** unter **Platt Form Einstellungen** , und klicken Sie auf ***anwenden***.</span><span class="sxs-lookup"><span data-stu-id="a519b-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="a519b-501">Wir markieren dieses Plug-in "nicht verarbeiten", da das Unity-assemblypatcher Probleme bei der Verarbeitung dieses Plug-ins hat.</span><span class="sxs-lookup"><span data-stu-id="a519b-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="a519b-502">Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="a519b-503">Kapitel 9: Erstellen der tabledescene-Klasse im Desktop Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="a519b-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="a519b-504">Sie müssen nun die Skripts erstellen, die den Code enthalten, um diese Anwendung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a519b-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="a519b-505">Das erste Skript, das Sie erstellen müssen, ist " **tabletoiscene**", das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="a519b-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="a519b-506">Lesen von Entitäten in der Azure-Tabelle.</span><span class="sxs-lookup"><span data-stu-id="a519b-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="a519b-507">Bestimmen Sie anhand der Tabellendaten, welche Objekte zu erzeugen sind und an welcher Position.</span><span class="sxs-lookup"><span data-stu-id="a519b-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="a519b-508">Das zweite Skript, das Sie erstellen müssen, ist **cloudscene**, das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="a519b-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="a519b-509">Registrieren des Linksklick Ereignisses, um dem Benutzer das Ziehen von Objekten in die Szene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a519b-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="a519b-510">Serialisieren der Objektdaten aus dieser Unity-Szene und Senden der Daten an den Azure-Funktionen-app.</span><span class="sxs-lookup"><span data-stu-id="a519b-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="a519b-511">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="a519b-511">To create this class:</span></span>

1.  <span data-ttu-id="a519b-512">Klicken Sie im Projekt Panel mit der rechten Maustaste in den Ordner **Asset** , und **Erstellen** Sie > **Ordner**.</span><span class="sxs-lookup"><span data-stu-id="a519b-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="a519b-513">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="a519b-513">Name the folder **Scripts**.</span></span>

    ![Ordner für die Skripterstellung](images/AzureLabs-Lab8-66.png)

    ![Ordner zum Erstellen von Skripts 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="a519b-516">Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a519b-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="a519b-517">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf >  **C# Skript** **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="a519b-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a519b-518">Benennen Sie das Skript **tabledescene**.</span><span class="sxs-lookup"><span data-stu-id="a519b-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="a519b-519">![neues c#-Skript](images/AzureLabs-Lab8-68.png)
    ![Umbenennen von Table](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="a519b-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="a519b-520">Doppelklicken Sie auf das Skript, um es in Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a519b-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="a519b-521">Fügen Sie die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="a519b-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="a519b-522">Fügen Sie in der-Klasse die folgenden Variablen ein:</span><span class="sxs-lookup"><span data-stu-id="a519b-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="a519b-523">Ersetzen Sie den Wert **Accountname** durch den Namen Ihres Azure Storage dienstanamens und **accountkey** durch den Schlüsselwert im Azure-Portal (siehe Abbildung unten) im Azure Storage-Dienst.</span><span class="sxs-lookup"><span data-stu-id="a519b-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![Kontoschlüssel abrufen](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="a519b-525">Fügen Sie jetzt die Methoden **Start ()** und **Awa()** hinzu, um die-Klasse zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="a519b-526">Fügen Sie innerhalb der **tabledescene** -Klasse die Methode hinzu, die die Werte aus der Azure-Tabelle abruft, und verwenden Sie Sie, um die entsprechenden primitiven in der Szene zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="a519b-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="a519b-527">Außerhalb der **tabletoscene** -Klasse müssen Sie die Klasse definieren, die von der Anwendung verwendet wird, um die **Tabellen Entitäten**zu serialisieren und zu deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="a519b-528">Stellen Sie sicher, dass Sie **Speichern** , bevor Sie zum Unity-Editor zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a519b-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="a519b-529">Klicken Sie im **Hierarchie** Panel auf die **Hauptkamera** , damit die Eigenschaften im **Inspektor**angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="a519b-530">Wenn der Ordner **Scripts** geöffnet ist, wählen Sie die **tabletoscene** -Skriptdatei aus, und ziehen Sie Sie auf die **Hauptkamera**.</span><span class="sxs-lookup"><span data-stu-id="a519b-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="a519b-531">Das Ergebnis sollte wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="a519b-531">The result should be as below:</span></span>

    ![Skript zur Hauptkamera hinzufügen](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="a519b-533">Kapitel 10: Erstellen der cloudscene-Klasse im Desktop Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="a519b-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="a519b-534">Das zweite Skript, das Sie erstellen müssen, ist **cloudscene**, das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="a519b-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="a519b-535">Registrieren des Linksklick Ereignisses, um dem Benutzer das Ziehen von Objekten in die Szene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a519b-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="a519b-536">Serialisieren der Objektdaten aus dieser Unity-Szene und Senden der Daten an den Azure-Funktionen-app.</span><span class="sxs-lookup"><span data-stu-id="a519b-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="a519b-537">So erstellen Sie das zweite Skript:</span><span class="sxs-lookup"><span data-stu-id="a519b-537">To create the second script:</span></span>

1.  <span data-ttu-id="a519b-538">Klicken Sie mit der rechten Maustaste in den Ordner **Skripts** , und klicken Sie auf **Erstellen**, **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="a519b-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="a519b-539">Benennen des Skripts für **cloudscene**</span><span class="sxs-lookup"><span data-stu-id="a519b-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="a519b-540">![neues c#-Skript](images/AzureLabs-Lab8-72.png)
    ![cloudscene umbenennen](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="a519b-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="a519b-541">Fügen Sie die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="a519b-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="a519b-542">Fügen Sie die folgenden Variablen ein:</span><span class="sxs-lookup"><span data-stu-id="a519b-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="a519b-543">Ersetzen Sie den Wert **azurefunctionendpoint** durch ihre Azure-Funktionen-App-URL im Azure-Funktionen-APP, wie in der folgenden Abbildung gezeigt:</span><span class="sxs-lookup"><span data-stu-id="a519b-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Funktions-URL für Get](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="a519b-545">Fügen Sie jetzt die Methoden **Start ()** und **Awa()** hinzu, um die-Klasse zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="a519b-546">Fügen Sie in der **Update ()** -Methode den folgenden Code hinzu, der die Maus Eingaben und den Zieh Vorgang erkennt, die wiederum gameobjects in der Szene verschieben.</span><span class="sxs-lookup"><span data-stu-id="a519b-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="a519b-547">Wenn der Benutzer ein Objekt gezogen und abgelegt hat, übergibt es den Namen und die Koordinaten des Objekts an die Methode **updatecloudscene ()** , die den Azure Funktionen-App-Dienst aufruft, der die Azure-Tabelle aktualisiert und die Benachrichtigung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a519b-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="a519b-548">Fügen Sie nun wie unten gezeigt die **updatecloudscene ()** -Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="a519b-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="a519b-549">Speichern des Codes und zurückkehren zu Unity</span><span class="sxs-lookup"><span data-stu-id="a519b-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="a519b-550">Ziehen Sie das **cloudscene** -Skript auf die **Hauptkamera**.</span><span class="sxs-lookup"><span data-stu-id="a519b-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="a519b-551">Klicken Sie im **Hierarchie** Panel auf die **Hauptkamera** , damit die Eigenschaften im **Inspektor**angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="a519b-552">Wenn der Ordner **Scripts** geöffnet ist, wählen Sie das **cloudscene** -Skript aus, und ziehen Sie es auf die **Hauptkamera**.</span><span class="sxs-lookup"><span data-stu-id="a519b-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="a519b-553">Das Ergebnis sollte wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="a519b-553">The result should be as below:</span></span>

        > ![Ziehen Sie das cloudskript auf die Hauptkamera](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="a519b-555">Kapitel 11: Erstellen des Desktop Projekts in UWP</span><span class="sxs-lookup"><span data-stu-id="a519b-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="a519b-556">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde nun abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a519b-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="a519b-557">Navigieren Sie zu **Buildeinstellungen** (**Datei** > **Buildeinstellungen**).</span><span class="sxs-lookup"><span data-stu-id="a519b-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="a519b-558">Klicken Sie im Fenster " **Buildeinstellungen** " auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="a519b-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Projekt erstellen](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="a519b-560">Ein **Datei-Explorer** -Fenster wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="a519b-561">Erstellen Sie einen neuen Ordner (indem Sie in der oberen linken Ecke auf **neuer Ordner** klicken), und nennen Sie ihn " **BUILDS**".</span><span class="sxs-lookup"><span data-stu-id="a519b-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![neuer Ordner für Build](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="a519b-563">Öffnen Sie den Ordner neue **BUILDS** , und erstellen Sie einen weiteren Ordner (mehr als einen **neuen Ordner** ), und nennen Sie ihn **NH\_Desktop\_-App**.</span><span class="sxs-lookup"><span data-stu-id="a519b-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![Ordnername NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="a519b-565">Wenn Sie die Option " **NH\_Desktop\_** " ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="a519b-566">Klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-566">click **Select Folder**.</span></span> <span data-ttu-id="a519b-567">Es dauert eine Minute, bis das Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="a519b-568">Im folgenden Build wird der **Datei-Explorer** angezeigt, in dem der Speicherort des neuen Projekts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="a519b-569">Es muss jedoch nicht geöffnet werden, da Sie das andere Unity-Projekt zunächst in den nächsten Kapiteln erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="a519b-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="a519b-570">Kapitel 12: Einrichten des gemischten Reality-Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="a519b-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="a519b-571">Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="a519b-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a519b-572">Öffnen Sie **Unity** , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="a519b-572">Open **Unity** and click **New**.</span></span>

    ![neues Unity-Projekt](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="a519b-574">Sie müssen nun einen Unity-Projektnamen angeben und **unitymrnotifhub**einfügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="a519b-575">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="a519b-576">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="a519b-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a519b-577">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-577">Then, click **Create project**.</span></span>

    ![Name unitymrnotishub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="a519b-579">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a519b-580">Wechseln Sie zu Edit > **Preferences (Einstellungen** **Bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="a519b-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a519b-581">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a519b-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a519b-582">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="a519b-582">Close the **Preferences** window.</span></span>

    ![externen Editor auf vs festlegen](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="a519b-584">Navigieren Sie als nächstes zu **Datei** > **Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="a519b-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Plattformen zu UWP wechseln](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="a519b-586">Wechseln Sie zu **Datei** > **Build-Einstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="a519b-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="a519b-587">Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="a519b-588">Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.</span><span class="sxs-lookup"><span data-stu-id="a519b-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="a519b-589">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="a519b-590">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="a519b-591">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="a519b-592">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a519b-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="a519b-593">In diesem Fall lohnt es sich, die Szene zu speichern und dem Build hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="a519b-594">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a519b-595">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-595">A save window will appear.</span></span>

            ![Hinzufügen offener Szenen](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="a519b-597">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="a519b-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![neuer Szenen Ordner](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="a519b-599">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld **Dateiname:** Text den Text **NH\_Mr\_Scene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a519b-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![neue Szene NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="a519b-601">Die restlichen Einstellungen in den **Buildeinstellungen**sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="a519b-602">Klicken Sie im gleichen Fenster auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="a519b-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Spieler Einstellungen öffnen](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="a519b-604">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="a519b-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="a519b-605">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="a519b-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a519b-606">Die **Skript Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="a519b-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="a519b-607">**Skript** -Back-End sollte ***.net*** sein</span><span class="sxs-lookup"><span data-stu-id="a519b-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="a519b-608">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="a519b-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![API-Kompatibilität](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="a519b-610">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, wird sichergestellt, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a519b-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Aktualisieren der XR-Einstellungen](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="a519b-612">Wählen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**die folgenden Optionen aus:</span><span class="sxs-lookup"><span data-stu-id="a519b-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="a519b-613">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="a519b-613">**InternetClient**</span></span>           

            ![Internet Client Tick](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="a519b-615">Zurück in den **Buildeinstellungen**: **Unity C# -Projekte** sind nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="a519b-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="a519b-616">Nachdem Sie diese Änderungen vorgenommen haben, schließen Sie das Fenster Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="a519b-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="a519b-617">Speichern Sie Ihre Szene und Projekt **Datei** > speichern Sie die **Szene/Datei** > speichern Sie das **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="a519b-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a519b-618">Wenn Sie die *Unity-Setup* Komponente für dieses Projekt (Mixed Reality-APP) überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren und dann fortfahren [. Kapitel 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="a519b-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="a519b-619">Sie müssen weiterhin die Skript Komponenten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="a519b-620">Kapitel 13: Importieren der DLLs im Mixed Reality Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="a519b-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="a519b-621">Sie verwenden Azure Storage für die Unity-Bibliothek (in der das .NET SDK für Azure verwendet wird).</span><span class="sxs-lookup"><span data-stu-id="a519b-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="a519b-622">Folgen Sie diesem [Link zur Verwendung von Azure Storage mit Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="a519b-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="a519b-623">Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="a519b-624">Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="a519b-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="a519b-625">Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [. unitypackage](https://aka.ms/azstorage-unitysdk)heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="a519b-626">Gehen Sie dann wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a519b-626">Then, do the following:</span></span>

1.  <span data-ttu-id="a519b-627">Fügen Sie das. unitypackage, das Sie aus dem obigen Beispiel heruntergeladen haben, zu Unity hinzu, indem Sie die Menüoption **Assets** >  > **benutzerdefiniertes Paket** **importieren** verwenden</span><span class="sxs-lookup"><span data-stu-id="a519b-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="a519b-628">Im Feld " **Unity-Paket importieren** ", das angezeigt wird, können Sie unter **Plug** -in > **Speicher**alles auswählen.</span><span class="sxs-lookup"><span data-stu-id="a519b-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Paket importieren](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="a519b-630">Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a519b-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="a519b-631">Wechseln Sie in der Projektansicht **unter Plug** -in zum Ordner **Speicher** , und wählen Sie *nur*die folgenden Plug-ins aus:</span><span class="sxs-lookup"><span data-stu-id="a519b-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="a519b-632">Microsoft. Data. Edm</span><span class="sxs-lookup"><span data-stu-id="a519b-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="a519b-633">Microsoft. Data. odata</span><span class="sxs-lookup"><span data-stu-id="a519b-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="a519b-634">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="a519b-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="a519b-635">"Newtonsoft. JSON"</span><span class="sxs-lookup"><span data-stu-id="a519b-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="a519b-636">System. Spatial</span><span class="sxs-lookup"><span data-stu-id="a519b-636">System.Spatial</span></span>

    ![Plug-ins auswählen](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="a519b-638">Wenn *Sie diese speziellen* Plug-Ins **ausgewählt haben, deaktivieren Sie** **eine beliebige Plattform** **, deaktivieren Sie** **wsaplayer** , und klicken Sie auf **anwenden**.</span><span class="sxs-lookup"><span data-stu-id="a519b-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Platt Formänderungen anwenden](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="a519b-640">Sie markieren diese bestimmten Plug-ins, sodass Sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="a519b-641">Dies liegt daran, dass im WSA-Ordner verschiedene Versionen der gleichen Plug-ins vorhanden sind, die nach dem Exportieren des Projekts aus Unity verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="a519b-642">Wählen Sie im Ordner **Storage** -Plug-in nur die Option:</span><span class="sxs-lookup"><span data-stu-id="a519b-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="a519b-643">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="a519b-643">Microsoft.Data.Services.Client</span></span>

        ![Datendienst Client auswählen](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="a519b-645">Aktivieren Sie das Kontrollkästchen **nicht verarbeiten** unter **Platt Form Einstellungen** , und klicken Sie auf **anwenden**.</span><span class="sxs-lookup"><span data-stu-id="a519b-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![nicht verarbeiten](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="a519b-647">Sie Markieren dieses Plug-in "nicht verarbeiten", weil das Unity-assemblypatcher Probleme beim Verarbeiten dieses Plug-ins hat.</span><span class="sxs-lookup"><span data-stu-id="a519b-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="a519b-648">Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="a519b-649">Kapitel 14: Erstellen der tabledescene-Klasse im Mixed Reality Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="a519b-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="a519b-650">Die **tabledescene** -Klasse ist mit der in [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)erläuterten identisch.</span><span class="sxs-lookup"><span data-stu-id="a519b-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="a519b-651">Erstellen Sie dieselbe Klasse im Mixed Reality-Unity-Projekt, und befolgen Sie dabei dasselbe Verfahren, das in [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)erläutert wurde.</span><span class="sxs-lookup"><span data-stu-id="a519b-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="a519b-652">Nachdem Sie dieses Kapitel abgeschlossen haben, wird diese Klasse in beiden **Unity-Projekten** auf der Hauptkamera eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="a519b-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="a519b-653">Kapitel 15: Erstellen der notificationreceiver-Klasse im Mixed Reality Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="a519b-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="a519b-654">Das zweite Skript, das Sie erstellen müssen, ist " **notificationreceiver**", das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="a519b-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="a519b-655">Registrieren der APP beim Notification Hub bei der Initialisierung.</span><span class="sxs-lookup"><span data-stu-id="a519b-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="a519b-656">Lauschen auf Benachrichtigungen, die vom Notification Hub stammen.</span><span class="sxs-lookup"><span data-stu-id="a519b-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="a519b-657">Die Objektdaten werden aus empfangenen Benachrichtigungen deserialisiert.</span><span class="sxs-lookup"><span data-stu-id="a519b-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="a519b-658">Verschieben Sie die gameobjects in der Szene basierend auf den deserialisierten Daten.</span><span class="sxs-lookup"><span data-stu-id="a519b-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="a519b-659">So erstellen Sie das **notificationreceiver** -Skript:</span><span class="sxs-lookup"><span data-stu-id="a519b-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="a519b-660">Klicken Sie mit der rechten Maustaste in den Ordner **Skripts** , und klicken Sie auf **Erstellen**, **C\# Skript**.</span><span class="sxs-lookup"><span data-stu-id="a519b-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="a519b-661">Benennen Sie das Skript mit **notificationreceiver**.</span><span class="sxs-lookup"><span data-stu-id="a519b-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="a519b-662">![erstellen Sie ein neues c#-Skript](images/AzureLabs-Lab8-95.png)
    ![den Namen notificationreceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="a519b-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="a519b-663">Doppelklicken Sie auf das Skript, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a519b-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="a519b-664">Fügen Sie die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="a519b-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="a519b-665">Fügen Sie die folgenden Variablen ein:</span><span class="sxs-lookup"><span data-stu-id="a519b-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="a519b-666">Ersetzen Sie den Wert **hubname** durch ihren Notification Hub-Dienstnamen und den Wert von **hublistenendpoint** mit dem Endpunkt Wert auf der Registerkarte Zugriffsrichtlinien, dem Azure Notification Hub-Dienst, im Azure-Portal (siehe Abbildung unten).</span><span class="sxs-lookup"><span data-stu-id="a519b-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Endpunkt der Notification Hubs-Richtlinie einfügen](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="a519b-668">Fügen Sie jetzt die Methoden **Start ()** und **Awa()** hinzu, um die-Klasse zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="a519b-669">Fügen Sie die **waitfornotification** -Methode hinzu, damit die APP Benachrichtigungen von der Notification Hub-Bibliothek empfangen kann, ohne den Haupt Thread zu klonen:</span><span class="sxs-lookup"><span data-stu-id="a519b-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="a519b-670">Mit der folgenden Methode, **initnotificationasync ()** , wird die Anwendung bei der Initialisierung beim Notification Hub-Dienst registriert.</span><span class="sxs-lookup"><span data-stu-id="a519b-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="a519b-671">Der Code wird auskommentiert, da Unity das Projekt nicht erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="a519b-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="a519b-672">Wenn Sie das nuget-Paket Azure Messaging in Visual Studio importieren, werden die Kommentare entfernt.</span><span class="sxs-lookup"><span data-stu-id="a519b-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="a519b-673">Der folgende Handler, **Channel\_pushnotificationempfangene ()** , wird jedes Mal ausgelöst, wenn eine Benachrichtigung empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="a519b-674">Die Benachrichtigung wird deserialisiert. dabei handelt es sich um die Azure-Tabellen Entität, die in die Desktop Anwendung verschoben wurde. Anschließend wird das zugehörige gameobject in der Mr-Szene an dieselbe Position verschoben.</span><span class="sxs-lookup"><span data-stu-id="a519b-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="a519b-675">Der Code wird auskommentiert, weil der Code auf die Azure Messaging-Bibliothek verweist, die Sie nach der Erstellung des Unity-Projekts mit dem nuget-Paket-Manager in Visual Studio hinzufügen werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="a519b-676">Daher kann das Unity-Projekt nicht erstellt werden, es sei denn, es ist auskommentiert. Wenn Sie Ihr Projekt erstellen und dann zu Unity zurückkehren möchten, müssen Sie den Code **erneut kommentieren** .</span><span class="sxs-lookup"><span data-stu-id="a519b-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="a519b-677">Denken Sie daran, die Änderungen zu speichern, bevor Sie zum Unity-Editor zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a519b-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="a519b-678">Klicken Sie im **Hierarchie** Panel auf die **Hauptkamera** , damit die Eigenschaften im **Inspektor**angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="a519b-679">Wenn der Ordner **Scripts** geöffnet ist, wählen Sie das Skript **notificationreceiver** aus, und ziehen Sie es auf die **Hauptkamera**.</span><span class="sxs-lookup"><span data-stu-id="a519b-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="a519b-680">Das Ergebnis sollte wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="a519b-680">The result should be as below:</span></span>

    ![Benachrichtigungs Empfänger Skript auf Kamera ziehen](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="a519b-682">Wenn Sie diese für Microsoft hololens entwickeln, müssen Sie die *Kamera* Komponente der **Hauptkamera**aktualisieren, um Folgendes zu tun:</span><span class="sxs-lookup"><span data-stu-id="a519b-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="a519b-683">Clear Flags: Volltonfarbe</span><span class="sxs-lookup"><span data-stu-id="a519b-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="a519b-684">Hintergrund: schwarz</span><span class="sxs-lookup"><span data-stu-id="a519b-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="a519b-685">Kapitel 16: Erstellen des Projekts für gemischte Realität in UWP</span><span class="sxs-lookup"><span data-stu-id="a519b-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="a519b-686">Dieses Kapitel ist mit dem Buildprozess für das vorherige Projekt identisch.</span><span class="sxs-lookup"><span data-stu-id="a519b-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="a519b-687">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="a519b-688">Navigieren Sie zu **Buildeinstellungen** ( **Datei** > **Buildeinstellungen** ).</span><span class="sxs-lookup"><span data-stu-id="a519b-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="a519b-689">Stellen Sie im Menü **Buildeinstellungen** sicher, dass **Unity C# -Projekte**\* getickt sind (sodass Sie die Skripts in diesem Projekt nach dem Build bearbeiten können).</span><span class="sxs-lookup"><span data-stu-id="a519b-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="a519b-690">Klicken Sie anschließend auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-690">After this is done, click **Build**.</span></span>

    ![Projekt erstellen](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="a519b-692">Ein **Datei-Explorer** -Fenster wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a519b-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="a519b-693">Erstellen Sie einen neuen Ordner (indem Sie in der oberen linken Ecke auf **neuer Ordner** klicken), und nennen Sie ihn " **BUILDS**".</span><span class="sxs-lookup"><span data-stu-id="a519b-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Ordner "Builds erstellen"](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="a519b-695">Öffnen Sie den Ordner neue **BUILDS** , und erstellen Sie einen weiteren Ordner (mehr als einen **neuen Ordner** ), und nennen Sie ihn **NH\_Mr\_-App**.</span><span class="sxs-lookup"><span data-stu-id="a519b-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Ordner "NH_MR_Apps" erstellen](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="a519b-697">Wenn die Option " **NH\_Mr\_** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="a519b-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="a519b-698">Klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-698">click **Select Folder**.</span></span> <span data-ttu-id="a519b-699">Es dauert eine Minute, bis das Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="a519b-700">Nach dem Build wird ein **Datei-Explorer** -Fenster am Speicherort des neuen Projekts geöffnet.</span><span class="sxs-lookup"><span data-stu-id="a519b-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="a519b-701">Kapitel 17: Hinzufügen von nuget-Paketen zur unitymrnotifhub-Lösung</span><span class="sxs-lookup"><span data-stu-id="a519b-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="a519b-702">Beachten Sie Folgendes: Nachdem Sie die folgenden nuget-Pakete hinzugefügt haben (und die Auskommentierung des Codes im nächsten [Kapitel](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)aufheben), zeigt der Code, wenn er im Unity-Projekt wieder geöffnet wird, Fehler an.</span><span class="sxs-lookup"><span data-stu-id="a519b-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="a519b-703">Wenn Sie zurückgehen und die Bearbeitung im Unity-Editor fortsetzen möchten, benötigen Sie einen Kommentar, mit dem Code erstellt wird, und entfernen Sie den Kommentar später erneut, sobald Sie sich wieder in Visual Studio befinden.</span><span class="sxs-lookup"><span data-stu-id="a519b-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="a519b-704">Nachdem der gemischte Projektmappenbuild abgeschlossen wurde, navigieren Sie zu dem Projekt mit gemischter Realität, das Sie erstellt haben, und doppelklicken Sie auf die Projektmappendatei (. sln) in diesem Ordner, um die Projekt Mappe mit Visual Studio 2017 zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a519b-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="a519b-705">Sie müssen nun das nuget-Paket **WindowsAzure. Messaging. Managed** hinzufügen. Dabei handelt es sich um eine Bibliothek, die zum Empfangen von Benachrichtigungen vom Notification Hub verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a519b-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="a519b-706">So importieren Sie das nuget-Paket:</span><span class="sxs-lookup"><span data-stu-id="a519b-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="a519b-707">Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf Ihre Projekt Mappe.</span><span class="sxs-lookup"><span data-stu-id="a519b-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="a519b-708">Klicken Sie auf **nuget-Pakete verwalten**.</span><span class="sxs-lookup"><span data-stu-id="a519b-708">Click on **Manage NuGet Packages**.</span></span>

    ![nuget-Manager öffnen](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="a519b-710">Wählen Sie die Registerkarte ***Durchsuchen*** aus, und suchen Sie nach **WindowsAzure. Messaging. Managed**.</span><span class="sxs-lookup"><span data-stu-id="a519b-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![Windows Azure-Messaging Paket suchen](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="a519b-712">Wählen Sie das Ergebnis aus (wie unten gezeigt), und aktivieren Sie im Fenster rechts das Kontrollkästchen neben **Project**.</span><span class="sxs-lookup"><span data-stu-id="a519b-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="a519b-713">Dadurch wird ein Tick in das Kontrollkästchen neben **Project**und das Kontrollkästchen neben dem Projekt **Assembly-CSharp** und **unitymrnotifhub** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![alle Projekte über tacken](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="a519b-715">Die ursprünglich bereitgestellte Version ist **möglicherweise nicht** kompatibel mit diesem Projekt.</span><span class="sxs-lookup"><span data-stu-id="a519b-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="a519b-716">Klicken Sie daher auf das Dropdown Menü neben **Version**, und klicken Sie auf **Version 0.1.7.9**und dann auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="a519b-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="a519b-717">Die Installation des nuget-Pakets ist nun abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a519b-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="a519b-718">Suchen Sie den kommentierten Code, den Sie in die **notificationreceiver** -Klasse eingegeben haben, und entfernen Sie die Kommentare.</span><span class="sxs-lookup"><span data-stu-id="a519b-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="a519b-719">Kapitel 18: unitymrnotiehub-Anwendung bearbeiten, notificationreceiver-Klasse</span><span class="sxs-lookup"><span data-stu-id="a519b-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="a519b-720">Nachdem Sie die **nuget-Pakete**hinzugefügt haben, müssen Sie den *Kommentar* für einen Teil des Codes in der **notificationreceiver** -Klasse aufheben.</span><span class="sxs-lookup"><span data-stu-id="a519b-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="a519b-721">Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="a519b-721">This includes:</span></span>

1. <span data-ttu-id="a519b-722">Der Namespace oben:</span><span class="sxs-lookup"><span data-stu-id="a519b-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="a519b-723">Sämtlicher Code in der **initnotificationsasync ()** -Methode:</span><span class="sxs-lookup"><span data-stu-id="a519b-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="a519b-724">Der obige Code enthält einen Kommentar darin: Stellen Sie sicher, dass Sie diesen Kommentar nicht versehentlich *auskommentiert* haben (da der Code nicht kompiliert wird, wenn Sie über! verfügen).</span><span class="sxs-lookup"><span data-stu-id="a519b-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="a519b-725">Und schließlich das **Channel_PushNotificationReceived** -Ereignis:</span><span class="sxs-lookup"><span data-stu-id="a519b-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="a519b-726">Wenn Sie nicht kommentiert sind, stellen Sie sicher, dass Sie speichern, und fahren Sie dann mit dem nächsten Kapitel fort.</span><span class="sxs-lookup"><span data-stu-id="a519b-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="a519b-727">Kapitel 19: Zuordnen des Projekts für gemischte Realität zur Store-App</span><span class="sxs-lookup"><span data-stu-id="a519b-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="a519b-728">Nun müssen Sie das **gemischte Reality** -Projekt der Store-App zuordnen, die Sie in zu Beginn des Labs erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="a519b-729">Öffnen Sie die Projekt Mappe.</span><span class="sxs-lookup"><span data-stu-id="a519b-729">Open the solution.</span></span>

2.  <span data-ttu-id="a519b-730">Klicken Sie mit der rechten Maustaste auf das UWP-App-Projekt im Projektmappen-Explorer Panel, und wählen Sie dann die Option zum **Speichern**und **Zuordnen der APP zum Store..** ..</span><span class="sxs-lookup"><span data-stu-id="a519b-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Store-Zuordnung öffnen](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="a519b-732">Es wird ein neues Fenster **mit dem Namen "App dem Windows Store zuordnen**" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a519b-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="a519b-733">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="a519b-733">Click **Next**.</span></span>

    ![zum nächsten Bildschirm wechseln](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="a519b-735">Es werden alle Anwendungen geladen, die dem Konto zugeordnet sind, das Sie angemeldet haben.</span><span class="sxs-lookup"><span data-stu-id="a519b-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="a519b-736">Wenn Sie nicht bei Ihrem Konto angemeldet sind, können Sie sich auf dieser Seite **Anmelden** .</span><span class="sxs-lookup"><span data-stu-id="a519b-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="a519b-737">Suchen Sie den **Namen der Store-App** , den Sie zu Beginn dieses Tutorials erstellt haben, und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="a519b-738">Klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="a519b-738">Then click **Next**.</span></span>

    ![Suchen und Auswählen Ihres Speicher namens](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="a519b-740">Klicken Sie auf **zuordnen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-740">Click **Associate**.</span></span>

    ![Zuordnen der APP](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="a519b-742">Ihre APP ist nun der Store-App **zugeordnet** .</span><span class="sxs-lookup"><span data-stu-id="a519b-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="a519b-743">Dies ist erforderlich, um Benachrichtigungen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a519b-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="a519b-744">Kapitel 20: Bereitstellen von unitymrnotiehub-und unitydesktopnotiehub-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="a519b-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="a519b-745">Dieses Kapitel kann mit zwei Personen einfacher sein, da das Ergebnis sowohl apps, die ausgeführt werden, eine auf dem Computer Desktop und die andere in Ihrem immersiven Headset enthalten.</span><span class="sxs-lookup"><span data-stu-id="a519b-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="a519b-746">Die immersive Headset-App wartet auf den Empfang von Änderungen an der Szene (Positionsänderungen der lokalen gameobjects), und die Desktop-App nimmt Änderungen an Ihrer lokalen Szene vor (Positionsänderungen), die für die Mr-APP freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a519b-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="a519b-747">Es ist sinnvoll, zuerst die Mr-APP und anschließend die Desktop-App bereitzustellen, damit der Empfänger mit dem lauschen beginnen kann.</span><span class="sxs-lookup"><span data-stu-id="a519b-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="a519b-748">So stellen Sie die **unitymrnotifhub** -App auf Ihrem lokalen Computer bereit:</span><span class="sxs-lookup"><span data-stu-id="a519b-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="a519b-749">Öffnen Sie die Projektmappendatei Ihrer **unitymrnotilohub** -app in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a519b-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="a519b-750">Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="a519b-751">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![Projekt Konfiguration festlegen](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="a519b-753">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="a519b-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="a519b-754">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="a519b-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="a519b-755">So stellen Sie die **unitydesktopnotifhub** -App auf dem lokalen Computer bereit:</span><span class="sxs-lookup"><span data-stu-id="a519b-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="a519b-756">Öffnen Sie die **Projektmappendatei ihrer unitydesktopnotilohub** -app in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a519b-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="a519b-757">Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="a519b-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="a519b-758">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="a519b-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![Projekt Konfiguration festlegen](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="a519b-760">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="a519b-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="a519b-761">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="a519b-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="a519b-762">Starten Sie die Mixed Reality-Anwendung, gefolgt von der Desktop Anwendung.</span><span class="sxs-lookup"><span data-stu-id="a519b-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="a519b-763">Wenn beide Anwendungen ausgeführt werden, verschieben Sie ein Objekt in der Desktop Szene (mit der linken Maustaste).</span><span class="sxs-lookup"><span data-stu-id="a519b-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="a519b-764">Diese Positionsänderungen werden lokal, serialisiert und an den Funktionen-App-Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="a519b-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="a519b-765">Der Funktionen-App-Dienst aktualisiert dann die Tabelle zusammen mit dem Notification Hub.</span><span class="sxs-lookup"><span data-stu-id="a519b-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="a519b-766">Wenn Sie ein Update erhalten haben, sendet der Notification Hub die aktualisierten Daten direkt an alle registrierten Anwendungen (in diesem Fall die immersive Headset-APP), von der die eingehenden Daten deserialisiert und die neuen Positionsdaten auf die lokalen Objekte angewendet werden. Verschieben in Szene.</span><span class="sxs-lookup"><span data-stu-id="a519b-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="a519b-767">Ihre Azure Notification Hubs-Anwendung ist abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a519b-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="a519b-768">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure Notification Hubs-Dienst nutzt und die Kommunikation zwischen Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a519b-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![Endprodukt-Ende](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="a519b-770">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="a519b-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="a519b-771">Übung 1</span><span class="sxs-lookup"><span data-stu-id="a519b-771">Exercise 1</span></span>

<span data-ttu-id="a519b-772">Können Sie herausfinden, wie Sie die Farbe der gameobjects ändern und diese Benachrichtigung an andere apps, die die Szene anzeigen, senden?</span><span class="sxs-lookup"><span data-stu-id="a519b-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="a519b-773">Übung 2</span><span class="sxs-lookup"><span data-stu-id="a519b-773">Exercise 2</span></span>

<span data-ttu-id="a519b-774">Können Sie die gameobjects-Bewegung zu ihrer Mr-app hinzufügen und die aktualisierte Szene in Ihrer Desktop-App sehen?</span><span class="sxs-lookup"><span data-stu-id="a519b-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
