---
title: Mr und Azure 311-Microsoft Graph
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie Microsoft Graph nutzen und eine Verbindung mit den Daten herstellen, die die Produktivität innerhalb einer gemischten Reality-Anwendung steigern
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Microsoft Graph, hololens, immersive, VR
ms.openlocfilehash: 775971c4e4289d2dc963dfa2bf033192d9f3489e
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047205"
---
>[!NOTE]
><span data-ttu-id="a6240-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="a6240-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a6240-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="a6240-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a6240-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a6240-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="a6240-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a6240-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="a6240-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a6240-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="a6240-110">Mr und Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="a6240-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="a6240-111">In diesem Kurs erfahren Sie, wie Sie *Microsoft Graph* verwenden können, um sich mit der sicheren Authentifizierung in einer gemischten Reality-Anwendung bei Ihrem Microsoft-Konto anzumelden.</span><span class="sxs-lookup"><span data-stu-id="a6240-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="a6240-112">Anschließend rufen Sie geplante Besprechungen in der Anwendungs Schnittstelle ab und zeigen Sie an.</span><span class="sxs-lookup"><span data-stu-id="a6240-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="a6240-113">*Microsoft Graph* ist ein Satz von APIs, die für den Zugriff auf viele der Dienste von Microsoft entwickelt wurden.</span><span class="sxs-lookup"><span data-stu-id="a6240-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="a6240-114">Microsoft beschreibt Microsoft Graph als Matrix von Ressourcen, die über Beziehungen verbunden sind, was bedeutet, dass eine Anwendung auf alle möglichen verbundenen Benutzerdaten zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="a6240-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="a6240-115">Weitere Informationen finden Sie auf der [Seite Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="a6240-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="a6240-116">Die Entwicklung umfasst das Erstellen einer APP, in der der Benutzer aufgefordert wird, sich anzusehen und dann auf eine Kugel zu tippen, die den Benutzer auffordert, sich sicher bei einem Microsoft-Konto anzumelden.</span><span class="sxs-lookup"><span data-stu-id="a6240-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="a6240-117">Nachdem Sie sich bei Ihrem Konto angemeldet haben, wird der Benutzer in der Lage sein, eine Liste der Besprechungen für den Tag anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a6240-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="a6240-118">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality hololens-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="a6240-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="a6240-119">Tippen Sie mithilfe der TAP-Geste auf ein Objekt, das den Benutzer auffordert, sich bei einem Microsoft-Konto anzumelden (durchlaufen der APP, um sich anzumelden, und dann wieder zurück in die APP).</span><span class="sxs-lookup"><span data-stu-id="a6240-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="a6240-120">Zeigt eine Liste der Besprechungen an, die für den Tag geplant sind.</span><span class="sxs-lookup"><span data-stu-id="a6240-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="a6240-121">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="a6240-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="a6240-122">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="a6240-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="a6240-123">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="a6240-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="a6240-124">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="a6240-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a6240-125">Natürlich</span><span class="sxs-lookup"><span data-stu-id="a6240-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a6240-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a6240-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a6240-127"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="a6240-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a6240-128">Mr und Azure 311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="a6240-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="a6240-129">✔️</span><span class="sxs-lookup"><span data-stu-id="a6240-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="a6240-130">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="a6240-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a6240-131">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="a6240-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a6240-132">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018).</span><span class="sxs-lookup"><span data-stu-id="a6240-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="a6240-133">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="a6240-134">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="a6240-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a6240-135">Einen Entwicklungs-PC</span><span class="sxs-lookup"><span data-stu-id="a6240-135">A development PC</span></span>
- [<span data-ttu-id="a6240-136">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="a6240-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a6240-137">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="a6240-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a6240-138">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="a6240-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a6240-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a6240-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a6240-140">Ein [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="a6240-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a6240-141">Internet Zugriff für Azure-Setup und Microsoft Graph Datenabruf</span><span class="sxs-lookup"><span data-stu-id="a6240-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="a6240-142">Ein gültiges **Microsoft-Konto** (entweder persönlich oder Geschäfts-, Schul-oder unikonto)</span><span class="sxs-lookup"><span data-stu-id="a6240-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="a6240-143">Einige Besprechungen, die für den aktuellen Tag geplant sind, mit demselben Microsoft-Konto</span><span class="sxs-lookup"><span data-stu-id="a6240-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="a6240-144">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="a6240-144">Before you start</span></span>

1.  <span data-ttu-id="a6240-145">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="a6240-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="a6240-146">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="a6240-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="a6240-147">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="a6240-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="a6240-148">Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="a6240-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="a6240-149">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="a6240-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="a6240-150">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="a6240-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="a6240-151">Kapitel 1: Erstellen der APP im Anwendungs Registrierungs Portal</span><span class="sxs-lookup"><span data-stu-id="a6240-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="a6240-152">Zunächst müssen Sie Ihre Anwendung im **Anwendungs Registrierungs Portal**erstellen und registrieren.</span><span class="sxs-lookup"><span data-stu-id="a6240-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="a6240-153">In diesem Kapitel finden Sie auch den Dienst Schlüssel, mit dem Sie Aufrufe an *Microsoft Graph* durchführen können, um auf Ihre Konto Inhalte zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="a6240-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="a6240-154">Navigieren Sie zum [Microsoft-Anwendungs Registrierungs Portal](https://apps.dev.microsoft.com) , und melden Sie sich mit Ihrem Microsoft-Konto an.</span><span class="sxs-lookup"><span data-stu-id="a6240-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="a6240-155">Nachdem Sie sich angemeldet haben, werden Sie zum **Anwendungs Registrierungs Portal**umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="a6240-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="a6240-156">Klicken Sie im Abschnitt **eigene Anwendungen** auf die Schaltfläche **app hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="a6240-157">Das **Anwendungs Registrierungs Portal** kann anders aussehen, je nachdem, ob Sie bereits mit *Microsoft Graph*gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="a6240-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="a6240-158">Die folgenden Screenshots zeigen diese verschiedenen Versionen an.</span><span class="sxs-lookup"><span data-stu-id="a6240-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="a6240-159">Fügen Sie einen Namen für Ihre Anwendung hinzu, und klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="a6240-160">Nachdem die Anwendung erstellt wurde, werden Sie zur Hauptseite der Anwendung umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="a6240-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="a6240-161">Kopieren Sie die **Anwendungs-ID** , und stellen Sie sicher, dass Sie diesen Wert auf sichere Weise merken. Sie verwenden ihn bald in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="a6240-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="a6240-162">Vergewissern Sie sich im Abschnitt **Plattformen** , dass **native Anwendung** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a6240-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="a6240-163">Wenn Sie *nicht* auf **Plattform hinzufügen** klicken, wählen Sie **native Anwendung**aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="a6240-164">Scrollen Sie auf der gleichen Seite nach unten, und im Abschnitt **Microsoft Graph Berechtigungen** müssen Sie zusätzliche Berechtigungen für die Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a6240-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="a6240-165">Klicken Sie neben **Delegierte Berechtigungen**auf **Hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="a6240-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="a6240-166">Da Sie möchten, dass Ihre Anwendung auf den Kalender des Benutzers zugreift, aktivieren Sie das Kontrollkästchen Calendar **. Read** , und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6240-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="a6240-167">Scrollen Sie nach unten, und klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="a6240-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="a6240-168">Ihre Speicherung wird bestätigt, und Sie können sich vom **Anwendungs Registrierungs Portal**abmelden.</span><span class="sxs-lookup"><span data-stu-id="a6240-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="a6240-169">Kapitel 2: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="a6240-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="a6240-170">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="a6240-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a6240-171">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="a6240-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="a6240-172">Sie müssen einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="a6240-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="a6240-173">Fügen Sie **msgraphmr**ein.</span><span class="sxs-lookup"><span data-stu-id="a6240-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="a6240-174">Stellen Sie sicher, dass die Projektvorlage auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="a6240-175">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="a6240-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a6240-176">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="a6240-177">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a6240-178">Wechseln Sie zu**Einstellungen** **Bearbeiten** > , und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="a6240-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a6240-179">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a6240-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a6240-180">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="a6240-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="a6240-181">Wechseln Sie zu > dateibuildeinstellungen, und wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um die Auswahl</span><span class="sxs-lookup"><span data-stu-id="a6240-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="a6240-182">Stellen Sie sicher, dass in den Einstellungen für die **Datei** > **Erstellung**Folgendes angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="a6240-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="a6240-183">**Zielgerät** ist auf **hololens** festgelegt</span><span class="sxs-lookup"><span data-stu-id="a6240-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="a6240-184">Der Buildtyp ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a6240-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="a6240-185">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a6240-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="a6240-186">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a6240-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="a6240-187">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a6240-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="a6240-188">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="a6240-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="a6240-189">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a6240-190">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a6240-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="a6240-191">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene.</span><span class="sxs-lookup"><span data-stu-id="a6240-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="a6240-192">Wählen Sie die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="a6240-193">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_ComputerVisionScene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a6240-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="a6240-194">Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="a6240-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="a6240-195">Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="a6240-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="a6240-196">Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="a6240-197">Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="a6240-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="a6240-198">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="a6240-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="a6240-199">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="a6240-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a6240-200">**Skript** Erstellung Die **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung), wodurch der Editor neu gestartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="a6240-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="a6240-201">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="a6240-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="a6240-202">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="a6240-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="a6240-203">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a6240-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a6240-204">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="a6240-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="a6240-205">Überprüfen Sie weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), ob **Virtual Reality unterstützt**wird, und vergewissern Sie sich, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a6240-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="a6240-206">Wieder inden Buildeinstellungen ist *Unity C# -Projekte* nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben diesem Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="a6240-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="a6240-207">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="a6240-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="a6240-208">Speichern Sie Ihre Szene und Ihr Projekt(**Datei** > **Speichern/**  > Speichern von Dateien).</span><span class="sxs-lookup"><span data-stu-id="a6240-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="a6240-209">Kapitel 3: Importieren von Bibliotheken in Unity</span><span class="sxs-lookup"><span data-stu-id="a6240-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6240-210">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-311. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5 fortfahren. ](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="a6240-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="a6240-211">Um *Microsoft Graph* in Unity verwenden zu können, müssen Sie die **Microsoft. Identity. Client** -dll verwenden.</span><span class="sxs-lookup"><span data-stu-id="a6240-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="a6240-212">Es ist möglich, das Microsoft Graph SDK zu verwenden. Allerdings ist es erforderlich, dass ein nuget-Paket hinzugefügt wird, nachdem Sie das Unity-Projekt erstellt haben (d.h. das Bearbeiten des Projekts nach dem Build).</span><span class="sxs-lookup"><span data-stu-id="a6240-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="a6240-213">Es ist einfacher, die erforderlichen DLLs direkt in Unity zu importieren.</span><span class="sxs-lookup"><span data-stu-id="a6240-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="a6240-214">Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="a6240-215">Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="a6240-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="a6240-216">Wenn Sie *Microsoft Graph* in Ihr eigenes Projekt importieren möchten, [Laden Sie die Datei MSGraph_LabPlugins. zip herunter](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a6240-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="a6240-217">Dieses Paket wurde mit Versionen der Bibliotheken erstellt, die getestet wurden.</span><span class="sxs-lookup"><span data-stu-id="a6240-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="a6240-218">Wenn Sie mehr darüber erfahren möchten, wie Sie Ihrem Unity-Projekt benutzerdefinierte DLLs hinzufügen, [folgen Sie diesem Link](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="a6240-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="a6240-219">So importieren Sie das Paket:</span><span class="sxs-lookup"><span data-stu-id="a6240-219">To import the package:</span></span>

1.  <span data-ttu-id="a6240-220">Fügen Sie das Unity-Paket Unity mithilfe der Menüoption **Assets** > **Import Package** > **Custom Package (benutzerdefiniertes Paket** importieren).</span><span class="sxs-lookup"><span data-stu-id="a6240-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="a6240-221">Wählen Sie das soeben heruntergeladene Paket aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="a6240-222">Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und einschließlich) Plug-ins ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="a6240-223">Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a6240-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="a6240-224">Wechseln Sie im *Projekt Panel* unter Plug -in zum Ordner **MSGraph** , und wählen Sie das Plug-in mit dem Namen **Microsoft. Identity. Client**aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="a6240-225">Wenn das *Plug* -in aktiviert ist, stellen Sie sicher, dass **alle Plattformen** deaktiviert sind, und stellen Sie sicher,dass **wsaplayer** ebenfalls deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="a6240-226">Dies dient nur zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="a6240-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="a6240-227">Wenn Sie diese Plug-ins markieren, werden Sie nur im Unity-Editor verwendet.</span><span class="sxs-lookup"><span data-stu-id="a6240-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="a6240-228">Es gibt einen anderen Satz von DLLs im WSA-Ordner, der verwendet wird, nachdem das Projekt aus Unity als universelle Windows-Anwendung exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a6240-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="a6240-229">Im nächsten Schritt müssen Sie den Ordner " **WSA** " im Ordner " **MSGraph** " öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="a6240-230">Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="a6240-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="a6240-231">Wählen Sie die Datei aus, und wählen Sie dann im Inspektor Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="a6240-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="a6240-232">Stellen Sie sicher, dass **alle Plattformen** deaktiviert sind und **nur** **wsaplayer** **überprüft**wird.</span><span class="sxs-lookup"><span data-stu-id="a6240-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="a6240-233">Stellen Sie sicher, dass **SDK** auf **UWP**und **Skript** -Back-End auf **dotnet** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="a6240-234">Stellen Sie sicher, dass **nicht verarbeiten** **aktiviert**ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="a6240-235">Klicken Sie auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="a6240-236">Kapitel 4: Kamera Einrichtung</span><span class="sxs-lookup"><span data-stu-id="a6240-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="a6240-237">In diesem Kapitel richten Sie die Hauptkamera Ihrer Szene ein:</span><span class="sxs-lookup"><span data-stu-id="a6240-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="a6240-238">Wählen Sie im Bereich *Hierarchie*die **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="a6240-239">Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor* -Panel sehen.</span><span class="sxs-lookup"><span data-stu-id="a6240-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="a6240-240">Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="a6240-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="a6240-241">Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="a6240-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="a6240-242">Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a6240-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="a6240-243">**Klartext** auf voll Tonfarbe festlegen</span><span class="sxs-lookup"><span data-stu-id="a6240-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="a6240-244">Legen Sie die **Hintergrundfarbe** der Kamera Komponente auf **schwarz, Alpha 0** (hexadezimal **Code: #00000000)** fest.</span><span class="sxs-lookup"><span data-stu-id="a6240-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="a6240-245">Die endgültige Objektstruktur im *Hierarchie Panel* sollte wie die in der folgenden Abbildung gezeigt aussehen:</span><span class="sxs-lookup"><span data-stu-id="a6240-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="a6240-246">Kapitel 5: Erstellen der meetingsui-Klasse</span><span class="sxs-lookup"><span data-stu-id="a6240-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="a6240-247">Das erste Skript, das Sie erstellen müssen, ist " **meetingsui**", das für das Hosting und Auffüllen der Benutzeroberfläche der Anwendung zuständig ist (Begrüßungs Meldung, Anweisungen und Besprechungs Details).</span><span class="sxs-lookup"><span data-stu-id="a6240-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="a6240-248">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="a6240-248">To create this class:</span></span>

1.  <span data-ttu-id="a6240-249">Klicken Sie im *Projekt Panel*mit der rechten Maustaste auf den Ordner **Objekte** , und wählen Sie dann**Ordner** **Erstellen** > aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="a6240-250">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="a6240-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="a6240-251">Öffnen Sie den Ordner Skripts, und klicken Sie dann in diesem Ordner mit der rechten Maustaste auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="a6240-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="a6240-252">Benennen Sie das Skript mit " **meetingsui".**</span><span class="sxs-lookup"><span data-stu-id="a6240-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="a6240-253">Doppelklicken Sie auf das neue Skript " **meetingsui** ", um es in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="a6240-254">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="a6240-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="a6240-255">Fügen Sie in der-Klasse die folgenden Variablen ein:</span><span class="sxs-lookup"><span data-stu-id="a6240-255">Inside the class insert the following variables:</span></span>

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

6.  <span data-ttu-id="a6240-256">Ersetzen Sie anschließend die Methode " **Start ()** ", und fügen Sie eine **Awa()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="a6240-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="a6240-257">Diese werden aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="a6240-257">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="a6240-258">Fügen Sie die Methoden hinzu, die für das Erstellen der *Besprechungen der Besprechungen* verantwortlich sind, und füllen Sie Sie mit den aktuellen Besprechungen</span><span class="sxs-lookup"><span data-stu-id="a6240-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

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

8. <span data-ttu-id="a6240-259">**Löschen** Sie die **Update ()** -Methode, und **Speichern Sie die Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a6240-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="a6240-260">Kapitel 6: Erstellen der Graph-Klasse</span><span class="sxs-lookup"><span data-stu-id="a6240-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="a6240-261">Das nächste Skript, das erstellt werden soll, ist das **Graph** -Skript.</span><span class="sxs-lookup"><span data-stu-id="a6240-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="a6240-262">Dieses Skript ist dafür verantwortlich, dass die Aufrufe zum Authentifizieren des Benutzers und zum Abrufen der geplanten Besprechungen für den aktuellen Tag aus dem Kalender des Benutzers durchführen.</span><span class="sxs-lookup"><span data-stu-id="a6240-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="a6240-263">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="a6240-263">To create this class:</span></span>

1.  <span data-ttu-id="a6240-264">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a6240-265">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="a6240-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a6240-266">Benennen Sie das Skript **Diagramm**.</span><span class="sxs-lookup"><span data-stu-id="a6240-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="a6240-267">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a6240-268">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="a6240-268">Insert the following namespaces:</span></span>

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
    > <span data-ttu-id="a6240-269">Sie werden feststellen, dass Teile des Codes in diesem Skript mit [vorkompilierungs Direktiven](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)umschlossen werden, um Probleme mit den Bibliotheken beim Erstellen der Visual Studio-Projekt Mappe zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="a6240-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="a6240-270">Löschen Sie die Methoden " **Start ()** " und " **Update ()** ", da Sie nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="a6240-271">Fügen Sie außerhalb der **Graph** -Klasse die folgenden Objekte ein, die zum Deserialisieren des JSON-Objekts erforderlich sind, das die täglichen geplanten Besprechungen darstellt:</span><span class="sxs-lookup"><span data-stu-id="a6240-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

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

7.  <span data-ttu-id="a6240-272">Fügen Sie innerhalb der **Graph** -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="a6240-272">Inside the **Graph** class, add the following variables:</span></span>

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
    > <span data-ttu-id="a6240-273">Ändern Sie den **AppID** -Wert in die **App-ID** , die Sie in  **[Kapitel 1](#chapter-1---create-your-app-in-the-application-registration-portal), Schritt 4**notiert haben.</span><span class="sxs-lookup"><span data-stu-id="a6240-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="a6240-274">Dieser Wert sollte mit dem übereinstimmen, der im **Anwendungs Registrierungs Portal** auf der Seite für die Anwendungs Registrierung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a6240-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="a6240-275">Fügen Sie innerhalb der **Graph** -Klasse die Methoden **signinasync ()** und **aquiretokenasync ()** hinzu, die den Benutzer auffordern, die Anmelde Informationen einzufügen.</span><span class="sxs-lookup"><span data-stu-id="a6240-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

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

9.  <span data-ttu-id="a6240-276">Fügen Sie die folgenden beiden Methoden hinzu:</span><span class="sxs-lookup"><span data-stu-id="a6240-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="a6240-277">**Buildtodaycalendarendpoint ()** : erstellt den URI, der den Tag und die Zeitspanne angibt, in der die geplanten Besprechungen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="a6240-278">**Listmeetingsasync ()** , die geplante Besprechungen von *Microsoft Graph*anfordert.</span><span class="sxs-lookup"><span data-stu-id="a6240-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

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

10. <span data-ttu-id="a6240-279">Sie haben nun das **Graph** -Skript abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a6240-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="a6240-280">**Speichern Sie die Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a6240-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="a6240-281">Kapitel 7: Erstellen des gazeinput-Skripts</span><span class="sxs-lookup"><span data-stu-id="a6240-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="a6240-282">Nun erstellen Sie das " **gazeinput**".</span><span class="sxs-lookup"><span data-stu-id="a6240-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="a6240-283">Diese Klasse verarbeitet und verfolgt den Blick des Benutzers, indem er einen **raycast** von der **Hauptkamera**verwendet und vorwärts projiziert.</span><span class="sxs-lookup"><span data-stu-id="a6240-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="a6240-284">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="a6240-284">To create the script:</span></span>

1.  <span data-ttu-id="a6240-285">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a6240-286">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="a6240-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a6240-287">Nennen Sie das Skript " **gazeinput**".</span><span class="sxs-lookup"><span data-stu-id="a6240-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="a6240-288">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a6240-289">Ändern Sie den Namespaces-Code so, dass er mit dem folgenden übereinstimmt, und fügen Sie das " **\[System.\]serialisierbare**"-Tag oberhalb Ihrer " **gazeinput** "-Klasse hinzu, damit es serialisiert werden kann:</span><span class="sxs-lookup"><span data-stu-id="a6240-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="a6240-290">Fügen Sie in der Klasse " **gazeinput** " die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="a6240-290">Inside the **GazeInput** class, add the following variables:</span></span>

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

6.  <span data-ttu-id="a6240-291">Fügen Sie die Methode " **kreatecursor ()** " hinzu, um den hololens-Cursor in der Szene zu erstellen, und rufen Sie die Methode über die Methode " **Start ()** " auf:</span><span class="sxs-lookup"><span data-stu-id="a6240-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

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

7.  <span data-ttu-id="a6240-292">Die folgenden Methoden aktivieren den Gaze-raycast und verfolgen die Objekte mit Fokus.</span><span class="sxs-lookup"><span data-stu-id="a6240-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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

8.  <span data-ttu-id="a6240-293">**Speichern Sie die Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a6240-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="a6240-294">Kapitel 8: Erstellen der Klasse "Interaktionen"</span><span class="sxs-lookup"><span data-stu-id="a6240-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="a6240-295">Sie müssen nun das **Interaktionen** -Skript erstellen, das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="a6240-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="a6240-296">Verarbeiten der **Tap** -Interaktion und des **Kamera Blicks**, mit dem der Benutzer mit der Anmelde Schaltfläche in der Szene interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="a6240-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="a6240-297">Erstellen des Objekts "Schaltfläche" für die Anmeldung in der Szene, mit der der Benutzer interagieren soll.</span><span class="sxs-lookup"><span data-stu-id="a6240-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="a6240-298">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="a6240-298">To create the script:</span></span>

1.  <span data-ttu-id="a6240-299">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a6240-300">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="a6240-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a6240-301">Benennen Sie das Skript mit **Interaktionen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="a6240-302">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a6240-303">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="a6240-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="a6240-304">Ändern Sie die Vererbung der **Interaktions** Klasse von *monobehaviour* in **gazeinput**.</span><span class="sxs-lookup"><span data-stu-id="a6240-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="a6240-305">~~Interaktionen der öffentlichen Klasse: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="a6240-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="a6240-306">Fügen Sie die folgende Variable in die **Interaktions** Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="a6240-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="a6240-307">Ersetzen Sie die **Start** -Methode. Beachten Sie, dass es sich um eine Überschreibungs Methode handelt, die die "Base"-Klasse "" als "</span><span class="sxs-lookup"><span data-stu-id="a6240-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="a6240-308">" **Start ()** " wird aufgerufen, wenn die Klasse initialisiert, sich für die Eingabe Erkennung registriert und die Anmelde Schaltfläche in der Szene erstellt:</span><span class="sxs-lookup"><span data-stu-id="a6240-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

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

8.  <span data-ttu-id="a6240-309">Fügen Sie die Methode " **kreatesigninbutton ()** " hinzu, mit der die Anmelde Schaltfläche in der Szene instanziiert wird, und legen Sie die zugehörigen Eigenschaften fest:</span><span class="sxs-lookup"><span data-stu-id="a6240-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

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

9.  <span data-ttu-id="a6240-310">Fügen Sie die **GestureRecognizer_Tapped ()** -Methode hinzu, die für das *Tap* User-Ereignis antwortet.</span><span class="sxs-lookup"><span data-stu-id="a6240-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

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

10. <span data-ttu-id="a6240-311">**Löschen** Sie die **Update ()** -Methode, und **Speichern Sie Ihre Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a6240-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="a6240-312">Kapitel 9: Einrichten der Skript Verweise</span><span class="sxs-lookup"><span data-stu-id="a6240-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="a6240-313">In diesem Kapitel müssen Sie das **Interaktionen** -Skript auf der **Hauptkamera**platzieren.</span><span class="sxs-lookup"><span data-stu-id="a6240-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="a6240-314">Dieses Skript behandelt dann das Platzieren der anderen Skripts, wenn Sie es benötigen.</span><span class="sxs-lookup"><span data-stu-id="a6240-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="a6240-315">Ziehen Sie die Skript **Interaktionen** aus dem Ordner "Skripts" im *Projekt Panel*wie unten dargestellt auf das **Hauptkamera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="a6240-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="a6240-316">Kapitel 10: Einrichten des Tags</span><span class="sxs-lookup"><span data-stu-id="a6240-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="a6240-317">Der Code, der den Blick verarbeitet, verwendet das Tag **signinbutton** , um zu ermitteln, mit welchem Objekt der Benutzer interagieren soll, um sich bei *Microsoft Graph*anzumelden.</span><span class="sxs-lookup"><span data-stu-id="a6240-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="a6240-318">So erstellen Sie das Tag:</span><span class="sxs-lookup"><span data-stu-id="a6240-318">To create the Tag:</span></span>

1.  <span data-ttu-id="a6240-319">Klicken Sie im Unity-Editor auf die **Hauptkamera** im *Hierarchie Panel*.</span><span class="sxs-lookup"><span data-stu-id="a6240-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="a6240-320">Klicken Sie im Bereich *Inspector* auf das **maincamera** - *Tag* , um eine Dropdown Liste zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a6240-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="a6240-321">Klicken Sie auf **Tag hinzufügen...**</span><span class="sxs-lookup"><span data-stu-id="a6240-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="a6240-322">Klicken Sie auf **+** die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="a6240-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="a6240-323">Schreiben Sie den Tagnamen als **signinbutton** , und klicken Sie auf speichern.</span><span class="sxs-lookup"><span data-stu-id="a6240-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="a6240-324">Kapitel 11: Erstellen des Unity-Projekts in UWP</span><span class="sxs-lookup"><span data-stu-id="a6240-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="a6240-325">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a6240-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="a6240-326">Navigieren Sie zu *Buildeinstellungen* (**Datei*>*Erstellen von Einstellungen**).</span><span class="sxs-lookup"><span data-stu-id="a6240-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="a6240-327">Wenn dies nicht bereits geschehen ist, Tick Sie **\# Unity C-Projekte**.</span><span class="sxs-lookup"><span data-stu-id="a6240-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="a6240-328">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-328">Click **Build**.</span></span> <span data-ttu-id="a6240-329">Unity startet ein **Datei-Explorer** -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="a6240-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="a6240-330">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**".</span><span class="sxs-lookup"><span data-stu-id="a6240-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="a6240-331">Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="a6240-332">Unity startet das Projekt in den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="a6240-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="a6240-333">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="a6240-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="a6240-334">Kapitel 12: Bereitstellen in hololens</span><span class="sxs-lookup"><span data-stu-id="a6240-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="a6240-335">So stellen Sie auf hololens bereit:</span><span class="sxs-lookup"><span data-stu-id="a6240-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="a6240-336">Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus befinden.**</span><span class="sxs-lookup"><span data-stu-id="a6240-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="a6240-337">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a6240-337">To do this:</span></span>

    1.  <span data-ttu-id="a6240-338">Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.</span><span class="sxs-lookup"><span data-stu-id="a6240-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="a6240-339">Navigieren Sie zu **Netzwerk &**  > erweiterte**Wi-Fi** > -**Optionen** für das Internet.</span><span class="sxs-lookup"><span data-stu-id="a6240-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="a6240-340">Notieren Sie sich die **IPv4** -Adresse.</span><span class="sxs-lookup"><span data-stu-id="a6240-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="a6240-341">Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie die **& Sicherheit** > **für Entwickler** .</span><span class="sxs-lookup"><span data-stu-id="a6240-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="a6240-342">Legen Sie **den Entwicklermodus auf**fest.</span><span class="sxs-lookup"><span data-stu-id="a6240-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="a6240-343">Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a6240-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="a6240-344">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="a6240-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="a6240-345">Wählen Sieauf der Projektmappenplattform die Option **x86, Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="a6240-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="a6240-346">Sie werden aufgefordert, die **IP-Adresse** eines Remote Geräts (in diesem Fall die hololens) einzufügen, die Sie notiert haben.</span><span class="sxs-lookup"><span data-stu-id="a6240-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="a6240-347">Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf die hololens quer zuladen.</span><span class="sxs-lookup"><span data-stu-id="a6240-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="a6240-348">Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.</span><span class="sxs-lookup"><span data-stu-id="a6240-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="a6240-349">Ihre Microsoft Graph hololens-Anwendung</span><span class="sxs-lookup"><span data-stu-id="a6240-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="a6240-350">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Microsoft Graph nutzt, um Benutzerkalender Daten zu lesen und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a6240-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="a6240-351">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="a6240-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="a6240-352">Übung 1</span><span class="sxs-lookup"><span data-stu-id="a6240-352">Exercise 1</span></span>

<span data-ttu-id="a6240-353">Verwenden Sie Microsoft Graph, um weitere Informationen zum Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a6240-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="a6240-354">Benutzer-e-Mail/Telefonnummer/Profilbild</span><span class="sxs-lookup"><span data-stu-id="a6240-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="a6240-355">Übung 1</span><span class="sxs-lookup"><span data-stu-id="a6240-355">Exercise 1</span></span>

<span data-ttu-id="a6240-356">Implementieren Sie das Voice-Steuerelement, um die Microsoft Graph-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="a6240-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
