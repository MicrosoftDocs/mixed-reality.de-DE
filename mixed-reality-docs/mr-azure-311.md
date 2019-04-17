---
title: 'MR und Azure-311: Microsoft Graph'
description: Führen Sie diesen Kurs erfahren Sie, wie Microsoft Graph nutzen, und verbinden Sie die Daten, die Produktivität, innerhalb einer mixed Reality-Anwendung steuert.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Microsoft Graph, Hololens, immersive vr
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593289"
---
>[!NOTE]
><span data-ttu-id="bec67-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="bec67-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="bec67-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="bec67-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bec67-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="bec67-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="bec67-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="bec67-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="bec67-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="bec67-110">MR und Azure-311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="bec67-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="bec67-111">In diesem Kurs erfahren Sie, wie mit *Microsoft Graph* zur Anmeldung bei Ihrem Microsoft-Konto mithilfe der sicheren Authentifizierung innerhalb einer mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="bec67-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="bec67-112">Sie werden dann abrufen und Ihre geplanten Besprechungen in der Benutzeroberfläche der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="bec67-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="bec67-113">*Microsoft Graph* ist ein Satz von APIs, um Zugriff auf viele der Dienste von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bec67-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="bec67-114">Microsoft beschreibt Microsoft Graph als einen Überblick über die Ressourcen, die über Beziehungen verbunden, was bedeutet, dass sie eine Anwendung auf alle Arten von verbundenen Benutzer zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="bec67-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="bec67-115">Weitere Informationen finden Sie auf die [Seite der Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="bec67-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="bec67-116">Entwicklung umfasst die Erstellung einer App, in denen der Benutzer angewiesen wird, bestaunen an, und tippen Sie dann auf einer Kugel, die fordert den Benutzer sicher bei einem Microsoft-Konto anmelden.</span><span class="sxs-lookup"><span data-stu-id="bec67-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="bec67-117">Wenn Sie auf ihr Konto angemeldet sind, wird der Benutzer können Sie eine Liste von Besprechungen geplant für den Tag sein.</span><span class="sxs-lookup"><span data-stu-id="bec67-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="bec67-118">Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality HoloLens-Anwendung, die für die folgenden Aufgaben werden können</span><span class="sxs-lookup"><span data-stu-id="bec67-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="bec67-119">Verwenden die tippbewegung, tippen Sie auf ein Objekt, das wird der Benutzer aufgefordert, melden Sie sich bei einem Microsoft Account (außerhalb der app zum Melden Sie sich, und klicken Sie dann wieder in die app verschieben).</span><span class="sxs-lookup"><span data-stu-id="bec67-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="bec67-120">Anzeigen einer Liste von Besprechungen geplant für den Tag.</span><span class="sxs-lookup"><span data-stu-id="bec67-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="bec67-121">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="bec67-122">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="bec67-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="bec67-123">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="bec67-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="bec67-124">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="bec67-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="bec67-125">Kurs</span><span class="sxs-lookup"><span data-stu-id="bec67-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="bec67-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="bec67-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="bec67-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="bec67-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="bec67-128">MR und Azure-311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="bec67-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="bec67-129">✔️</span><span class="sxs-lookup"><span data-stu-id="bec67-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="bec67-130">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bec67-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="bec67-131">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="bec67-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="bec67-132">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="bec67-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="bec67-133">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.</span><span class="sxs-lookup"><span data-stu-id="bec67-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="bec67-134">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="bec67-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="bec67-135">Eine Entwicklungs-PC</span><span class="sxs-lookup"><span data-stu-id="bec67-135">A development PC</span></span>
- [<span data-ttu-id="bec67-136">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="bec67-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="bec67-137">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="bec67-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="bec67-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="bec67-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="bec67-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bec67-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="bec67-140">Ein [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="bec67-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="bec67-141">Zugriff auf das Internet für die Einrichtung von Azure und Microsoft Graph-Datenabruf</span><span class="sxs-lookup"><span data-stu-id="bec67-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="bec67-142">Ein gültiger **Microsoft Account** (persönliche oder Geschäfts-oder schulkonten)</span><span class="sxs-lookup"><span data-stu-id="bec67-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="bec67-143">Einige-Besprechungen geplant für den aktuellen Tag, mit dem gleichen Microsoft-Account</span><span class="sxs-lookup"><span data-stu-id="bec67-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="bec67-144">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="bec67-144">Before you start</span></span>

1.  <span data-ttu-id="bec67-145">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="bec67-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="bec67-146">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bec67-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="bec67-147">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="bec67-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="bec67-148">Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="bec67-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="bec67-149">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="bec67-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="bec67-150">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="bec67-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="bec67-151">Kapitel 1: Erstellen Ihrer app in App-Registrierungsportal</span><span class="sxs-lookup"><span data-stu-id="bec67-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="bec67-152">Zunächst müssen Sie zum Erstellen und registrieren Ihre Anwendung in der **App-Registrierungsportal**.</span><span class="sxs-lookup"><span data-stu-id="bec67-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="bec67-153">In diesem Kapitel finden Sie außerdem den Dienstschlüssel, die Sie aufrufen können *Microsoft Graph* Zugriff auf Ihre Konto-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="bec67-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="bec67-154">Navigieren Sie zu der [Microsoft-Anwendungsregistrierungsportal](https://apps.dev.microsoft.com) und melden Sie sich mit Ihrem Microsoft Account.</span><span class="sxs-lookup"><span data-stu-id="bec67-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="bec67-155">Nachdem Sie sich angemeldet haben, werden Sie umgeleitet die **App-Registrierungsportal**.</span><span class="sxs-lookup"><span data-stu-id="bec67-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="bec67-156">In der **meiner Anwendungen** Abschnitt, klicken Sie auf die Schaltfläche mit den **fügen Sie eine app**.</span><span class="sxs-lookup"><span data-stu-id="bec67-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="bec67-157">Die **App-Registrierungsportal** sehen variieren, je nachdem, ob Sie zuvor mit gearbeitet haben *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="bec67-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="bec67-158">Die folgenden Screenshots dieser verschiedenen Versionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bec67-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="bec67-159">Fügen Sie einen Namen für Ihre Anwendung und klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="bec67-160">Nachdem die Anwendung erstellt wurde, werden Sie auf der Hauptseite der Anwendung weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="bec67-161">Kopieren der **Anwendungs-Id** und stellen Sie sicher, dass dieser Wert an einem sicheren Ort zu beachten, da Sie es in Kürze in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="bec67-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="bec67-162">In der **Plattformen** Abschnitt, stellen Sie sicher, dass **systemeigene Anwendung** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bec67-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="bec67-163">Wenn *nicht* klicken Sie auf **Plattform hinzufügen** , und wählen Sie **systemeigene Anwendung**.</span><span class="sxs-lookup"><span data-stu-id="bec67-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="bec67-164">Führen Sie einen Bildlauf nach unten aus, in der gleichen Seite und im Abschnitt **Microsoft Graph-Berechtigungen** Sie benötigen zusätzliche Berechtigungen für die Anwendung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bec67-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="bec67-165">Klicken Sie auf **hinzufügen** neben **delegierte Berechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="bec67-166">Da Sie Ihre Anwendung auf den Kalender des Benutzers zugreifen möchten, aktivieren Sie das Kontrollkästchen, die Namen **Calendars.Read** , und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bec67-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="bec67-167">Scrollen Sie nach unten, und klicken Sie auf die **speichern** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="bec67-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="bec67-168">Ihre speichern bestätigt, und Sie können melden Sie sich vom die **App-Registrierungsportal**.</span><span class="sxs-lookup"><span data-stu-id="bec67-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="bec67-169">Kapitel 2: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="bec67-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="bec67-170">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="bec67-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="bec67-171">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="bec67-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="bec67-172">Sie müssen den Namen eines Unity-Projekts angeben.</span><span class="sxs-lookup"><span data-stu-id="bec67-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="bec67-173">Fügen Sie **MSGraphMR**.</span><span class="sxs-lookup"><span data-stu-id="bec67-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="bec67-174">Stellen Sie sicher, dass die Projektvorlage nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="bec67-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="bec67-175">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="bec67-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="bec67-176">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="bec67-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="bec67-177">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="bec67-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="bec67-178">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="bec67-178">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="bec67-179">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="bec67-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="bec67-180">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="bec67-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="bec67-181">Wechseln Sie zu **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="bec67-181">Go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="bec67-182">In der **Datei > Buildeinstellungen**, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="bec67-182">While still in **File > Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="bec67-183">**Geräte** nastaven NA hodnotu **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="bec67-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="bec67-184">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="bec67-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="bec67-185">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="bec67-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="bec67-186">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="bec67-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="bec67-187">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="bec67-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="bec67-188">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="bec67-189">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="bec67-190">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bec67-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="bec67-191">Erstellen Sie einen neuen Ordner für, und alle zukünftigen, Szene ein.</span><span class="sxs-lookup"><span data-stu-id="bec67-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="bec67-192">Wählen Sie die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="bec67-193">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_ComputerVisionScene**, klicken Sie dann auf **speichern** .</span><span class="sxs-lookup"><span data-stu-id="bec67-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="bec67-194">Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen.</span><span class="sxs-lookup"><span data-stu-id="bec67-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="bec67-195">Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.</span><span class="sxs-lookup"><span data-stu-id="bec67-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="bec67-196">Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="bec67-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="bec67-197">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="bec67-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="bec67-198">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="bec67-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="bec67-199">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="bec67-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="bec67-200">**Scripting** **Laufzeitversion** muss **experimentell** (.NET 4.6 entspricht), löst der Editor neu starten müssen.</span><span class="sxs-lookup"><span data-stu-id="bec67-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="bec67-201">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="bec67-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="bec67-202">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="bec67-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="bec67-203">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="bec67-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="bec67-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="bec67-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="bec67-205">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), überprüfen Sie **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality SDK** hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="bec67-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="bec67-206">Im *Buildeinstellungen*, *Unity C# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="bec67-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="bec67-207">Schließen der *Buildeinstellungen* Fenster.</span><span class="sxs-lookup"><span data-stu-id="bec67-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="bec67-208">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern von SZENEN und Datei > Projekt speichern**).</span><span class="sxs-lookup"><span data-stu-id="bec67-208">Save your scene and project (**FILE > SAVE SCENES / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="bec67-209">Kapitel 3: Importieren von Bibliotheken in Unity</span><span class="sxs-lookup"><span data-stu-id="bec67-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bec67-210">Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="bec67-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="bec67-211">Verwendung von *Microsoft Graph* in Unity, Sie müssen, verwenden die **Microsoft.Identity.Client** DLL.</span><span class="sxs-lookup"><span data-stu-id="bec67-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="bec67-212">Es ist möglich, die Microsoft Graph SDK verwenden, allerdings muss das Hinzufügen von NuGet-Paket nach dem Erstellen des Unity-Projekts (d. h. die nach der Erstellung des Projekts bearbeiten).</span><span class="sxs-lookup"><span data-stu-id="bec67-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="bec67-213">Es wird einfacher, importieren die benötigten DLLs direkt in Unity angesehen.</span><span class="sxs-lookup"><span data-stu-id="bec67-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="bec67-214">Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert.</span><span class="sxs-lookup"><span data-stu-id="bec67-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="bec67-215">Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="bec67-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="bec67-216">So importieren Sie *Microsoft Graph* in Ihrem eigenen Projekt [Laden Sie die Datei MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="bec67-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="bec67-217">Dieses Paket wurde mit den Versionen der Bibliotheken erstellt, die getestet wurden.</span><span class="sxs-lookup"><span data-stu-id="bec67-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="bec67-218">Wenn Sie weitere Informationen zum Hinzufügen von benutzerdefinierten DLLs zu Ihres Unity-Projekts möchten [folgen Sie diesem Link](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="bec67-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="bec67-219">Zum Importieren des Pakets:</span><span class="sxs-lookup"><span data-stu-id="bec67-219">To import the package:</span></span>

1.  <span data-ttu-id="bec67-220">Hinzufügen des Unity-Pakets zu Unity mit der **Assets* > *Paket importieren* > *Custom Package** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="bec67-220">Add the Unity Package to Unity by using the **Assets* > *Import Package* > *Custom Package** menu option.</span></span> <span data-ttu-id="bec67-221">Wählen Sie das Paket, das Sie gerade heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="bec67-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="bec67-222">In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="bec67-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="bec67-223">Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bec67-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="bec67-224">Wechseln Sie zu der **MSGraph** Unterordner **-Plug-Ins** in die *Projektbereich* , und wählen Sie das Plug-in **Microsoft.Identity.Client**.</span><span class="sxs-lookup"><span data-stu-id="bec67-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="bec67-225">Mit der *-Plug-Ins* ausgewählt haben, stellen sicher, dass **Any Platform** deaktiviert ist, und klicken Sie dann sicher, dass **WSAPlayer** auch deaktiviert ist, und klicken Sie dann **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="bec67-226">Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="bec67-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="bec67-227">Markieren diese-Plug-Ins konfiguriert sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="bec67-228">Es gibt ein anderen Satz von DLLs im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity als universelle Windows-Anwendung exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="bec67-229">Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **MSGraph** Ordner.</span><span class="sxs-lookup"><span data-stu-id="bec67-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="bec67-230">Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="bec67-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="bec67-231">Wählen Sie die Datei, und klicken Sie dann im Inspektor:</span><span class="sxs-lookup"><span data-stu-id="bec67-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="bec67-232">sicherstellen, dass **Any Platform** ist **deaktiviert**, und dass **nur** **WSAPlayer** ist **überprüft**.</span><span class="sxs-lookup"><span data-stu-id="bec67-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="bec67-233">Stellen Sie sicher **SDK** nastaven NA hodnotu **UWP**, und **Scripting Back-End-** nastaven NA hodnotu **Dot Net**</span><span class="sxs-lookup"><span data-stu-id="bec67-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="bec67-234">Sicherstellen, dass **nicht verarbeiten** ist **überprüft**.</span><span class="sxs-lookup"><span data-stu-id="bec67-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="bec67-235">Klicken Sie auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="bec67-236">Kapitel 4 – Kamerasetup</span><span class="sxs-lookup"><span data-stu-id="bec67-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="bec67-237">Während der in diesem Kapitel werden Sie der Main Kamera und Ihrer Szene einrichten:</span><span class="sxs-lookup"><span data-stu-id="bec67-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="bec67-238">In der *Hierarchie Bereich*, wählen die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="bec67-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="bec67-239">Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor* Bereich.</span><span class="sxs-lookup"><span data-stu-id="bec67-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="bec67-240">Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="bec67-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="bec67-241">Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)</span><span class="sxs-lookup"><span data-stu-id="bec67-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="bec67-242">Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="bec67-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="bec67-243">Legen Sie **Kennzeichnungen löschen** zu **Volltonfarbe**</span><span class="sxs-lookup"><span data-stu-id="bec67-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="bec67-244">Legen Sie die **Hintergrundfarbe** der Kamera-Komponente auf **Schwarz, Alpha 0** **(Hex-Code: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="bec67-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="bec67-245">Die Struktur der endgültige Objekt in der *Hierarchie Bereich* sollte wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="bec67-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="bec67-246">Kapitel 5: Erstellen Sie MeetingsUI-Klasse</span><span class="sxs-lookup"><span data-stu-id="bec67-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="bec67-247">Ist das erste Skript, das Sie erstellen müssen **MeetingsUI**, die zum Hosten und Auffüllen der Benutzeroberfläche der Anwendung (Begrüßungsnachricht, Anweisungen und die Details der Besprechungen) verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="bec67-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="bec67-248">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="bec67-248">To create this class:</span></span>

1.  <span data-ttu-id="bec67-249">Mit der rechten Maustaste auf die **Assets** Ordner in der *Projektfenster*, und klicken Sie \**erstellen* > \* Ordner \*\*.</span><span class="sxs-lookup"><span data-stu-id="bec67-249">Right-click on the **Assets** folder in the *Project Panel*, then select \**Create* > \*Folder\*\*.</span></span> <span data-ttu-id="bec67-250">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="bec67-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="bec67-251">Öffnen der **Skripts** Ordner klicken Sie dann in diesem Ordner mit der rechten Maustaste, \**erstellen* > \* C\# Script \*\*.</span><span class="sxs-lookup"><span data-stu-id="bec67-251">Open the **Scripts** folder then, within that folder, right-click, \**Create* > \*C\# Script\*\*.</span></span> <span data-ttu-id="bec67-252">Nennen Sie das Skript **MeetingsUI.**</span><span class="sxs-lookup"><span data-stu-id="bec67-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="bec67-253">Doppelklicken Sie auf die neue **MeetingsUI** Skript öffnen Sie ihn mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="bec67-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="bec67-254">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="bec67-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="bec67-255">Fügen Sie in der Klasse die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="bec67-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="bec67-256">Ersetzen Sie dann die **Start()** Methode und Hinzufügen einer **Awake()** Methode.</span><span class="sxs-lookup"><span data-stu-id="bec67-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="bec67-257">Diese werden aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="bec67-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="bec67-258">Fügen Sie die Methoden, die verantwortlich für das Erstellen der *Besprechungen UI* und füllen sie mit den aktuellen treffen, wenn angefordert:</span><span class="sxs-lookup"><span data-stu-id="bec67-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="bec67-259">**Löschen Sie** der **Update()** -Methode und **speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe an Unity.</span><span class="sxs-lookup"><span data-stu-id="bec67-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="bec67-260">Kapitel 6: Erstellen Sie die Graph-Klasse</span><span class="sxs-lookup"><span data-stu-id="bec67-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="bec67-261">Ist das nächste Skript zum Erstellen der **Graph** Skript.</span><span class="sxs-lookup"><span data-stu-id="bec67-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="bec67-262">Dieses Skript ist dafür verantwortlich, dass die Aufrufe an den Benutzer authentifizieren und Abrufen der geplanten Besprechungen für den aktuellen Tag aus den Kalender des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="bec67-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="bec67-263">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="bec67-263">To create this class:</span></span>

1.  <span data-ttu-id="bec67-264">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="bec67-265">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**  >   **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="bec67-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="bec67-266">Nennen Sie das Skript **Graph**.</span><span class="sxs-lookup"><span data-stu-id="bec67-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="bec67-267">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="bec67-268">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="bec67-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="bec67-269">Sie werden feststellen, dass Teile des Codes in diesem Skript umbrochen werden [Vorkompilieren Direktiven](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), dies ist zur Vermeidung von Problemen mit den Bibliotheken, beim Erstellen der Projektmappe in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bec67-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="bec67-270">Löschen der **Start()** und **Update()** Methoden, wie sie nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="bec67-271">Außerhalb der **Graph** Klasse, legen Sie die folgenden Objekte, die beim Deserialisieren des JSON-Objekts zurück, der täglichen geplanten Besprechungen darstellt erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="bec67-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="bec67-272">In der **Graph** -Klasse verwenden, fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="bec67-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="bec67-273">Ändern der **AppId** Wert der **App-Id** , die Sie notiert haben, im  **[Kapitel 1](#chapter-1---create-your-app-in-the-application-registration-portal), Schritt 4**.</span><span class="sxs-lookup"><span data-stu-id="bec67-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="bec67-274">Dieser Wert sollte identisch, die angezeigt wird, der **App-Registrierungsportal** in Ihre Seite für die anwendungsregistrierung.</span><span class="sxs-lookup"><span data-stu-id="bec67-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="bec67-275">In der **Graph** Klasse, fügen Sie die Methoden **SignInAsync()** und **AquireTokenAsync()**, aufgefordert, die den Benutzer, die Anmeldeinformationen einzufügen.</span><span class="sxs-lookup"><span data-stu-id="bec67-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="bec67-276">Fügen Sie die folgenden zwei Methoden:</span><span class="sxs-lookup"><span data-stu-id="bec67-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="bec67-277">**BuildTodayCalendarEndpoint()**, welche builds den URI angeben, den Tag und die Zeitspanne, in dem die geplanten Besprechungen werden abgerufen.</span><span class="sxs-lookup"><span data-stu-id="bec67-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="bec67-278">**ListMeetingsAsync()**, die Anforderungen aus geplanten Besprechungen *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="bec67-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="bec67-279">Sie haben jetzt die **Graph** Skript.</span><span class="sxs-lookup"><span data-stu-id="bec67-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="bec67-280">**Speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe in Unity.</span><span class="sxs-lookup"><span data-stu-id="bec67-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="bec67-281">Kapitel 7: Erstellen Sie das Skript GazeInput</span><span class="sxs-lookup"><span data-stu-id="bec67-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="bec67-282">Erstellen Sie jetzt die **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="bec67-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="bec67-283">Diese Klasse behandelt, und verfolgt des Benutzers Blicke, mit einem **Raycast** aus der **Main Camera**, projizieren weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="bec67-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="bec67-284">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="bec67-284">To create the script:</span></span>

1.  <span data-ttu-id="bec67-285">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="bec67-286">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**  >   **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="bec67-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="bec67-287">Nennen Sie das Skript **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="bec67-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="bec67-288">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="bec67-289">Ändern Sie den Code Namespaces entsprechend folgendermaßen, sowie das Hinzufügen der "**\[System.Serializable\]**" Tag, die oben genannten Ihre **GazeInput** Klasse, sodass sie serialisiert werden kann:</span><span class="sxs-lookup"><span data-stu-id="bec67-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="bec67-290">In der **GazeInput** -Klasse verwenden, fügen Sie die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="bec67-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="bec67-291">Hinzufügen der **CreateCursor()** Methode, um die HoloLens-Cursor in der Szene erstellt, und rufen die Methode aus der **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="bec67-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="bec67-292">Die folgenden Methoden ermöglichen die Blicke Raycast und Nachverfolgen der fokussierten Objekte.</span><span class="sxs-lookup"><span data-stu-id="bec67-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="bec67-293">**Speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe in Unity.</span><span class="sxs-lookup"><span data-stu-id="bec67-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="bec67-294">Kapitel 8 – erstellen Sie die Interaktionen-Klasse</span><span class="sxs-lookup"><span data-stu-id="bec67-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="bec67-295">Sie müssen nun zum Erstellen der **Interaktionen** Skripts, die dafür verantwortlich ist:</span><span class="sxs-lookup"><span data-stu-id="bec67-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="bec67-296">Behandeln der **Tippen Sie auf** Interaktion und die **Kamera bestaunen**, wodurch den Benutzer für die Interaktion mit der Anmeldung "Button" in der Szene.</span><span class="sxs-lookup"><span data-stu-id="bec67-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="bec67-297">Erstellen das Protokoll in "Button"-Objekt in der Szene für den Benutzer für die Interaktion mit ein.</span><span class="sxs-lookup"><span data-stu-id="bec67-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="bec67-298">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="bec67-298">To create the script:</span></span>

1.  <span data-ttu-id="bec67-299">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="bec67-300">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**  >   **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="bec67-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="bec67-301">Nennen Sie das Skript **Interaktionen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="bec67-302">Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="bec67-303">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="bec67-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="bec67-304">Ändern Sie die Vererbung von der **Interaktion** -Klasse aus *"monobehaviour"* zu **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="bec67-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="bec67-305">~~öffentliche Klasse Interaktionen: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="bec67-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="bec67-306">In der **Interaktion** Klasse einfügen der folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="bec67-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="bec67-307">Ersetzen Sie die **starten** Methode; Beachten Sie, dass es eine Überschreibungsmethode, der Methode der "base" Blicke-Klasse aufruft, ist.</span><span class="sxs-lookup"><span data-stu-id="bec67-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="bec67-308">**Start()** wird aufgerufen, wenn die Klasse initialisiert die Registrierung für die Eingabe verwendet, und erstellen die Anmeldung, *Schaltfläche* in der Szene:</span><span class="sxs-lookup"><span data-stu-id="bec67-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="bec67-309">Hinzufügen der **CreateSignInButton()** -Methode, die die Anmeldung instanziiert *Schaltfläche* in der Szene und seine Eigenschaften festlegen:</span><span class="sxs-lookup"><span data-stu-id="bec67-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="bec67-310">Hinzufügen der **GestureRecognizer_Tapped()** -Methode, die werden für reagieren die *Tippen Sie auf* Benutzerereignis.</span><span class="sxs-lookup"><span data-stu-id="bec67-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="bec67-311">**Löschen Sie** der **Update()** -Methode, und klicken Sie dann **speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe an Unity.</span><span class="sxs-lookup"><span data-stu-id="bec67-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="bec67-312">Kapitel 9: Einrichten der Skriptverweise</span><span class="sxs-lookup"><span data-stu-id="bec67-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="bec67-313">In diesem Kapitel es erforderlich, die **Interaktionen** Skript auf die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="bec67-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="bec67-314">Dieses Skript behandelt platzieren den anderen Skripts, in denen sie sein müssen.</span><span class="sxs-lookup"><span data-stu-id="bec67-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="bec67-315">Von der **Skripts** Ordner in der *Projektfenster*, ziehen Sie das Skript **Interaktionen** auf die **Main Camera** -Objekts, wie unten abgebildet.</span><span class="sxs-lookup"><span data-stu-id="bec67-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="bec67-316">Kapitel 10 – das Tag einrichten</span><span class="sxs-lookup"><span data-stu-id="bec67-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="bec67-317">Der Code zum Verarbeiten der Blicke wird Nutzen des Tags **SignInButton** Objekt Identifizieren der Benutzer interagieren wird, um sich anzumelden *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="bec67-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="bec67-318">So erstellen Sie das Tag:</span><span class="sxs-lookup"><span data-stu-id="bec67-318">To create the Tag:</span></span>

1.  <span data-ttu-id="bec67-319">Klicken Sie im Unity-Editor auf die **Main Camera** in die *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="bec67-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="bec67-320">In der *Inspektor Bereich* klicken Sie auf die **MainCamera** *Tag* , das eine Dropdown-Liste zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bec67-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="bec67-321">Klicken Sie auf **Tag hinzufügen...**</span><span class="sxs-lookup"><span data-stu-id="bec67-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="bec67-322">Klicken Sie auf die **+** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="bec67-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="bec67-323">Schreiben Sie den Namen des Tags als **SignInButton** , und klicken Sie auf Speichern.</span><span class="sxs-lookup"><span data-stu-id="bec67-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="bec67-324">Kapitel 11: Erstellen Sie das Unity-Projekt auf UWP</span><span class="sxs-lookup"><span data-stu-id="bec67-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="bec67-325">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.</span><span class="sxs-lookup"><span data-stu-id="bec67-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="bec67-326">Navigieren Sie zu *Buildeinstellungen* (\**Datei* > \* Erstellen von Einstellungen \*\*).</span><span class="sxs-lookup"><span data-stu-id="bec67-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="bec67-327">Falls noch nicht geschehen, aktivieren Sie **Unity C\# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="bec67-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="bec67-328">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-328">Click **Build**.</span></span> <span data-ttu-id="bec67-329">Unity startet eine **Datei-Explorer** Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="bec67-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="bec67-330">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**.</span><span class="sxs-lookup"><span data-stu-id="bec67-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="bec67-331">Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="bec67-332">Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="bec67-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="bec67-333">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="bec67-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="bec67-334">Kapitel 12 – bereitstellen, um HoloLens</span><span class="sxs-lookup"><span data-stu-id="bec67-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="bec67-335">Für HoloLens bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="bec67-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="bec67-336">Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus.**</span><span class="sxs-lookup"><span data-stu-id="bec67-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="bec67-337">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="bec67-337">To do this:</span></span>

    1.  <span data-ttu-id="bec67-338">Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="bec67-339">Wechseln Sie zu **Netzwerk und Internet** > **Wi-Fi** > **erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="bec67-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="bec67-340">Beachten Sie die **IPv4** Adresse.</span><span class="sxs-lookup"><span data-stu-id="bec67-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="bec67-341">Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit** > **für Entwickler**</span><span class="sxs-lookup"><span data-stu-id="bec67-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="bec67-342">Legen Sie **Entwicklermodus auf**.</span><span class="sxs-lookup"><span data-stu-id="bec67-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="bec67-343">Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="bec67-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="bec67-344">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="bec67-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="bec67-345">In der **Projektmappenplattform**Option **X86, Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="bec67-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="bec67-346">Werden Sie aufgefordert, fügen Sie der **IP-Adresse** von einem Remotegerät (die HoloLens, in diesem Fall, den Sie notiert haben).</span><span class="sxs-lookup"><span data-stu-id="bec67-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="bec67-347">Wechseln Sie zu **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bec67-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="bec67-348">Ihre app sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bec67-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="bec67-349">Die Microsoft Graph HoloLens-Anwendung</span><span class="sxs-lookup"><span data-stu-id="bec67-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="bec67-350">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Microsoft Graph zum Lesen und Anzeigen von Benutzer Kalenderdaten nutzt.</span><span class="sxs-lookup"><span data-stu-id="bec67-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="bec67-351">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="bec67-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="bec67-352">Übung 1</span><span class="sxs-lookup"><span data-stu-id="bec67-352">Exercise 1</span></span>

<span data-ttu-id="bec67-353">Verwenden Sie Microsoft Graph, um weitere Informationen über den Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bec67-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="bec67-354">Benutzer-e- / Telefonnummer / profile-Bild</span><span class="sxs-lookup"><span data-stu-id="bec67-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="bec67-355">Übung 1</span><span class="sxs-lookup"><span data-stu-id="bec67-355">Exercise 1</span></span>

<span data-ttu-id="bec67-356">Implementieren Sie die Sprach-Steuerelement, um die Benutzeroberfläche von Microsoft Graph zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="bec67-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
