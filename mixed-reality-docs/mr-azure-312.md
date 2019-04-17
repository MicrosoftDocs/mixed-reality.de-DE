---
title: MR und Azure-312 - Bot-integration
description: Führen Sie diesen Kurs erfahren Sie, wie zum Erstellen und Bereitstellen von einem Bot mithilfe von Microsoft Bot Framework v4, und in einer mixed Reality-Anwendung mit ihm kommunizieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, maschinelles sehen, Hololens, immersive Vr, Microsoft Bot Framework, Version 4, Web-app-Bot, Bot Framework, Microsoft Bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604984"
---
>[!NOTE]
><span data-ttu-id="c84c6-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="c84c6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c84c6-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c84c6-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c84c6-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c84c6-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="c84c6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c84c6-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="c84c6-110">MR und Azure-312: Bot-integration</span><span class="sxs-lookup"><span data-stu-id="c84c6-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="c84c6-111">In diesem Kurs erfahren Sie, wie zum Erstellen und Bereitstellen von einem Bot mit dem Microsoft Bot Framework V4 und über eine Windows Mixed Reality-Anwendung mit ihm kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="c84c6-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="c84c6-112">Die **Microsoft Bot Framework V4** ist ein Satz von APIs konzipiert, soll Entwicklern die Tools zum Erstellen einer Bot erweiterbares und skalierbares bieten Anwendung.</span><span class="sxs-lookup"><span data-stu-id="c84c6-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="c84c6-113">Weitere Informationen finden Sie auf die [Microsoft Bot Framework-Seite](https://dev.botframework.com/) oder [V4-Git-Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="c84c6-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="c84c6-114">Nach Abschluss dieses Kurses, werden Sie eine Windows Mixed Reality-Anwendung erstellt haben die können die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="c84c6-115">Verwenden einer **Geste Tippen Sie auf** des Bots mit dem Lauschen auf der Stimme von Benutzer zu starten.</span><span class="sxs-lookup"><span data-stu-id="c84c6-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="c84c6-116">Wenn der Benutzer etwas gesagt hat, versucht den Bot, eine Antwort zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="c84c6-117">Anzeigen der Antwort des Bots als Text in der Nähe der Bot, in der Unity-Szene positioniert.</span><span class="sxs-lookup"><span data-stu-id="c84c6-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="c84c6-118">In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c84c6-119">Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="c84c6-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="c84c6-120">Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="c84c6-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c84c6-121">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="c84c6-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c84c6-122">Kurs</span><span class="sxs-lookup"><span data-stu-id="c84c6-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c84c6-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c84c6-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c84c6-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="c84c6-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c84c6-125">MR und Azure-312: Bot-integration</span><span class="sxs-lookup"><span data-stu-id="c84c6-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="c84c6-126">✔️</span><span class="sxs-lookup"><span data-stu-id="c84c6-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c84c6-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c84c6-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c84c6-128">Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c84c6-129">Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c84c6-130">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c84c6-131">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c84c6-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c84c6-132">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="c84c6-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c84c6-133">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="c84c6-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="c84c6-134">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.</span><span class="sxs-lookup"><span data-stu-id="c84c6-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="c84c6-135">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="c84c6-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c84c6-136">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="c84c6-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c84c6-137">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="c84c6-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c84c6-138">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="c84c6-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c84c6-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="c84c6-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c84c6-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c84c6-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c84c6-141">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="c84c6-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c84c6-142">Zugriff auf das Internet für Azure, und klicken Sie zum Abrufen der Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="c84c6-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="c84c6-143">Weitere Informationen [folgen Sie diesem Link](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="c84c6-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="c84c6-144">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="c84c6-144">Before you start</span></span>

1.  <span data-ttu-id="c84c6-145">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="c84c6-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c84c6-146">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c84c6-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="c84c6-147">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="c84c6-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c84c6-148">Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-app (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="c84c6-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c84c6-149">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="c84c6-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="c84c6-150">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="c84c6-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="c84c6-151">Kapitel 1 – erstellen Sie die Bot-Anwendung</span><span class="sxs-lookup"><span data-stu-id="c84c6-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="c84c6-152">Der erste Schritt ist die Erstellung von Bots als lokale ASP.Net Core-Web-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="c84c6-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="c84c6-153">Sobald Sie fertig und getestet haben, veröffentlichen Sie es auf das Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="c84c6-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="c84c6-154">Öffnen Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c84c6-154">Open Visual Studio.</span></span> <span data-ttu-id="c84c6-155">Erstellen ein neues Projekts wählen **ASP-NET-Core-Webanwendung** als Projekttyp (Sie finden es unter der Unterabschnitt .NET Core), und rufen sie **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="c84c6-156">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-156">Click **OK**.</span></span>

2.  <span data-ttu-id="c84c6-157">Im Fenster die Option erscheint **leere**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="c84c6-158">Außerdem stellen Sie sicher, dass das Ziel nastaven NA hodnotu **ASP-NET Core 2.0** und die Authentifizierung auf **keine Authentifizierung**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="c84c6-159">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-159">Click **OK**.</span></span>  

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="c84c6-161">Die Lösung wird jetzt geöffnet.</span><span class="sxs-lookup"><span data-stu-id="c84c6-161">The solution will now open.</span></span> <span data-ttu-id="c84c6-162">Mit der rechten Maustaste auf die Projektmappe **Mybot** in die **Projektmappen-Explorer** und klicken Sie auf **NuGet-Pakete für Projektmappe verwalten**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="c84c6-164">In der **Durchsuchen** Registerkarte, suchen Sie nach **Microsoft.Bot.Builder.Integration.AspNet.Core** (Stellen Sie sicher, dass **Vorabversion einschließen** aktiviert).</span><span class="sxs-lookup"><span data-stu-id="c84c6-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="c84c6-165">Wählen Sie die Paketversion **4.0.1-Preview**, und aktivieren Sie die Project-Felder.</span><span class="sxs-lookup"><span data-stu-id="c84c6-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="c84c6-166">Klicken Sie dann auf **installieren**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-166">Then click on **Install**.</span></span> <span data-ttu-id="c84c6-167">Sie haben nun die für die erforderlichen Bibliotheken installiert die **Bot Framework v4**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="c84c6-168">Schließen Sie die NuGet-Seite.</span><span class="sxs-lookup"><span data-stu-id="c84c6-168">Close the NuGet page.</span></span>

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="c84c6-170">Mit der rechten Maustaste auf Ihre *Projekt*, **MyBot**in die **Projektmappen-Explorer** und klicken Sie auf **hinzufügen** **|** **Klasse**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="c84c6-172">Nennen Sie die Klasse **MyBot** und klicken Sie auf **hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="c84c6-174">Wiederholen Sie die vorherigen Punkt, um eine weitere Klasse namens erstellen **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="c84c6-175">Mit der rechten Maustaste auf **"Wwwroot"** in die **Projektmappen-Explorer** und klicken Sie auf **hinzufügen** **|** **neues Element**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="c84c6-176">Wählen Sie **HTML-Seite** (Sie finden es unter der Unterabschnitt Web).</span><span class="sxs-lookup"><span data-stu-id="c84c6-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="c84c6-177">Nennen Sie die Datei **"default.HTML"**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-177">Name the file **default.html**.</span></span> <span data-ttu-id="c84c6-178">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-178">Click **Add**.</span></span>

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="c84c6-180">Die Liste der Klassen / Objekte in der **Projektmappen-Explorer** sollte wie in der folgenden Abbildung aussehen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="c84c6-182">Doppelklicken Sie auf die **ConversationContext** Klasse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="c84c6-183">Diese Klasse ist zuständig für die mit den Variablen, die von den Bot verwendet, um den Kontext der Konversation zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="c84c6-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="c84c6-184">Diese Konversation Kontext-Werte werden in einer Instanz dieser Klasse verwaltet, da jede Instanz der **MyBot** Klasse wird jedes Mal eine Aktivität empfangen wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="c84c6-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="c84c6-185">Fügen Sie den folgenden Code zur Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="c84c6-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="c84c6-186">Doppelklicken Sie auf die **MyBot** Klasse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="c84c6-187">Diese Klasse wird der Handler, die von einer eingehenden Aktivität aufgerufen wird, vom Kunden gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="c84c6-188">In dieser Klasse fügen Sie den Code verwendet, um die Kommunikation zwischen den Bot und den Kunden zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="c84c6-189">Wie bereits erwähnt, wird eine Instanz dieser Klasse jedes Mal initialisiert, die eine Aktivität empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="c84c6-190">Fügen Sie dieser Klasse den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="c84c6-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="c84c6-191">Doppelklicken Sie auf die **Start** Klasse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="c84c6-192">Diese Klasse wird der Bot initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-192">This class will initialize the bot.</span></span> <span data-ttu-id="c84c6-193">Fügen Sie den folgenden Code zur Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="c84c6-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="c84c6-194">Öffnen der **Programm** Klassendatei, und überprüfen Sie, ob der Code identisch wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c84c6-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="c84c6-195">Denken Sie daran, die Änderungen speichern, zu diesem Zweck zu wechseln **Datei** > **Alles speichern**, auf der Symbolleiste am oberen Rand der Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c84c6-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="c84c6-196">Kapitel 2: Erstellen der Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="c84c6-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="c84c6-197">Nun, dass Sie den Code für Ihren Bot erstellt haben, müssen Sie ihn in einer Instanz von Veröffentlichen der *Web-App-Bot* -Dienst auf dem Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="c84c6-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="c84c6-198">In diesem Kapitel erfahren Sie, wie zum Erstellen und Konfigurieren der Bot Service in Azure und veröffentlichen Sie Ihren Code dann darauf.</span><span class="sxs-lookup"><span data-stu-id="c84c6-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="c84c6-199">Melden Sie sich zunächst beim Azure-Portal (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c84c6-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="c84c6-200">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c84c6-201">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="c84c6-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c84c6-202">Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach *-Web-App-Bot*, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="c84c6-204">Die neue Seite bietet eine Beschreibung der *Web-App-Bot* Service.</span><span class="sxs-lookup"><span data-stu-id="c84c6-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="c84c6-205">Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="c84c6-207">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="c84c6-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="c84c6-208">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="c84c6-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="c84c6-209">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="c84c6-210">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c84c6-211">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c84c6-212">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="c84c6-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c84c6-213">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, [führen Sie diesen Link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="c84c6-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="c84c6-214">Bestimmen Sie den Speicherort für die Ressourcengruppe, (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="c84c6-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c84c6-215">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c84c6-216">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c84c6-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="c84c6-217">Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *Web-App-Bot* -Dienst ein freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen</span><span class="sxs-lookup"><span data-stu-id="c84c6-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="c84c6-218">**App-Namen** kann einfach bleiben identisch mit der *botname*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="c84c6-219">Lassen Sie die *Bot Vorlage* als **grundlegende (C#)**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="c84c6-220">*App Service-Plan/Standort* automatisch ausgefüllten für Ihr Konto hätte.</span><span class="sxs-lookup"><span data-stu-id="c84c6-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="c84c6-221">Legen Sie die **Azure Storage** , dass Sie zum Hosten Ihren Bot verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="c84c6-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="c84c6-222">Wenn Sie eine noch nicht, können Sie es hier erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="c84c6-223">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="c84c6-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="c84c6-224">Klicken Sie auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-224">Click Create.</span></span>
 
        ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="c84c6-226">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="c84c6-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="c84c6-227">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="c84c6-229">Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="c84c6-231">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c84c6-232">Sie werden für Ihre neue Azure-Dienstinstanz weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="c84c6-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="c84c6-234">An diesem Punkt müssen Sie ein Feature namens einrichten **Direktverbindungen** auf Ihre Clientanwendung mit diesen Bot-Dienst kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="c84c6-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="c84c6-235">Klicken Sie auf **Kanäle**, klicken Sie dann in der **fügen Sie einen ausgewählten Kanal** an, klicken Sie im Abschnitt **Direktverbindungen konfigurieren Kanal**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="c84c6-237">Auf dieser Seite finden Sie die **geheime Schlüssel** Ihre Client-app für die Authentifizierung mit dem Bot ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="c84c6-238">Klicken Sie auf die **anzeigen** Schaltfläche und kopieren Sie eines der angezeigten Schlüssel, da Sie dies später in Ihr Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="c84c6-240">Kapitel 3: Veröffentlichen des Bots mit dem Azure-Web-App-Bot-Dienst</span><span class="sxs-lookup"><span data-stu-id="c84c6-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="c84c6-241">Nun, dass Ihr Dienst bereit ist, müssen Sie Ihren Bot-Code, veröffentlichen, den Sie zuvor erstellt haben, um Ihre neu erstellte Web-App-Bot Service.</span><span class="sxs-lookup"><span data-stu-id="c84c6-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="c84c6-242">Müssen Sie Ihren Bot mit dem Azure-Dienst veröffentlichen, jedes Mal, wenn Sie die Projektmappe für Bot ändern / code.</span><span class="sxs-lookup"><span data-stu-id="c84c6-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="c84c6-243">Wechseln Sie zurück zu Visual Studio-Projektmappe, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="c84c6-244">Mit der rechten Maustaste auf Ihre **MyBot** in-Projekt die **Projektmappen-Explorer**, klicken Sie dann auf **veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="c84c6-246">Auf der *Veröffentlichungsziel* auf **App Service**, klicken Sie dann **vorhandene auswählen**, klicken Sie schließlich auf **Profil erstellen** (möglicherweise müssen Sie Klicken Sie auf den Dropdownpfeil neben der *veröffentlichen* Schaltfläche, wenn dies nicht sichtbar ist).</span><span class="sxs-lookup"><span data-stu-id="c84c6-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="c84c6-248">Wenn Sie nicht noch in Ihrem Microsoft Account angemeldet sind, müssen Sie nötig ist.</span><span class="sxs-lookup"><span data-stu-id="c84c6-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="c84c6-249">Auf der **veröffentlichen** Seite Sie sehen, Sie müssen die gleiche festlegen **Abonnement** , die Sie verwendet für die *Web-App-Bot* beim Erstellen des Diensts.</span><span class="sxs-lookup"><span data-stu-id="c84c6-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="c84c6-250">Legen Sie dann die **Ansicht** als **Ressourcengruppe** und wählen Sie in der Dropdownliste Ordnerstruktur, die **Ressourcengruppe** Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="c84c6-251">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-251">Click **OK**.</span></span> 

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="c84c6-253">Klicken Sie nun auf die **veröffentlichen** Schaltfläche, und warten Sie, bis der Bot veröffentlicht werden (es kann einige Minuten dauern).</span><span class="sxs-lookup"><span data-stu-id="c84c6-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="c84c6-255">Kapitel 4: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="c84c6-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="c84c6-256">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="c84c6-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c84c6-257">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-257">Open *Unity* and click **New**.</span></span> 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="c84c6-259">Sie müssen jetzt einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="c84c6-260">Fügen Sie **Hololens, Bot**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="c84c6-261">Stellen Sie sicher, dass die Projektvorlage nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="c84c6-262">Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="c84c6-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c84c6-263">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-263">Then, click **Create project**.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="c84c6-265">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c84c6-266">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c84c6-267">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c84c6-268">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="c84c6-268">Close the **Preferences** window.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="c84c6-270">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="c84c6-272">In der **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="c84c6-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="c84c6-273">**Geräte** nastaven NA hodnotu **Hololens**</span><span class="sxs-lookup"><span data-stu-id="c84c6-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="c84c6-274">Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="c84c6-275">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="c84c6-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="c84c6-276">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="c84c6-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="c84c6-277">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="c84c6-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="c84c6-278">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="c84c6-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="c84c6-279">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="c84c6-280">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c84c6-281">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-281">A save window will appear.</span></span>
        
            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="c84c6-283">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="c84c6-285">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **BotScene**, klicken Sie dann auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="c84c6-287">Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="c84c6-288">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="c84c6-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="c84c6-290">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="c84c6-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="c84c6-291">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="c84c6-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="c84c6-292">**Scripting Runtime Version** muss **experimentell (NET 4.6 Äquivalent)**; das Ändern dieser Eigenschaft erfordert einen Neustart des Editors.</span><span class="sxs-lookup"><span data-stu-id="c84c6-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="c84c6-293">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="c84c6-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="c84c6-294">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="c84c6-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="c84c6-296">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="c84c6-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c84c6-297">**InternetClient**</span></span>
        - <span data-ttu-id="c84c6-298">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="c84c6-298">**Microphone**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="c84c6-300">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="c84c6-302">Im *Buildeinstellungen* _Unity C#_  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="c84c6-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="c84c6-303">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="c84c6-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="c84c6-304">Speichern Sie Ihre Szene und das Projekt (**Datei > SZENE speichern / FILE > Projekt speichern**).</span><span class="sxs-lookup"><span data-stu-id="c84c6-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="c84c6-305">Kapitel 5 – kamerasetup</span><span class="sxs-lookup"><span data-stu-id="c84c6-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c84c6-306">Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 7](#chapter-7-–-create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="c84c6-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="c84c6-307">In der *Hierarchie Bereich*, wählen die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="c84c6-308">Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="c84c6-309">Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Schreibweise)</span><span class="sxs-lookup"><span data-stu-id="c84c6-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="c84c6-310">Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Schreibweise)</span><span class="sxs-lookup"><span data-stu-id="c84c6-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="c84c6-311">Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="c84c6-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="c84c6-312">Legen Sie **Kennzeichnungen löschen** zu **Volltonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="c84c6-313">Legen Sie die **Hintergrund** Farbe der Kamera-Komponente auf **Schwarz, Alpha 0 (Hex-Code: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="c84c6-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Kamera-Setup](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="c84c6-315">Kapitel 6 – Import die Newtonsoft-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c84c6-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="c84c6-316">Können Sie deserialisieren und Serialisieren von Objekten, die empfangen und an den Bot-Dienst gesendet, die Sie herunterladen müssen die **Newtonsoft** Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="c84c6-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="c84c6-317">Sehen Sie eine [kompatible Version, die bereits mit der richtigen Unity Ordnerstruktur hier organisiert](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="c84c6-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="c84c6-318">Um die Newtonsoft-Bibliothek in Ihr Projekt zu importieren, verwenden Sie das Unity-Paket, das in diesem Kurs stammt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="c84c6-319">Hinzufügen der *.unitypackage* in Unity mithilfe der **Assets** > **Paket importieren** > **Custom Package** Option des Menüs.</span><span class="sxs-lookup"><span data-stu-id="c84c6-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importieren Sie die Newtonsoft-Bibliothek](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="c84c6-321">In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="c84c6-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importieren Sie die Newtonsoft-Bibliothek](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="c84c6-323">Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="c84c6-324">Wechseln Sie zu der **Newtonsoft** Unterordner **-Plug-Ins** in der Projektansicht und die Newtonsoft-Plug-in.</span><span class="sxs-lookup"><span data-stu-id="c84c6-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="c84c6-325">Die Newtonsoft-Plug-in ausgewählt haben, stellen Sie sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **WSAPlayer** auch **deaktiviert**, Klicken Sie dann auf **übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="c84c6-326">Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="c84c6-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="c84c6-327">Markieren diese-Plug-Ins konfiguriert sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="c84c6-328">Es gibt ein anderen Satz von ihnen im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="c84c6-329">Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **Newtonsoft** Ordner.</span><span class="sxs-lookup"><span data-stu-id="c84c6-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="c84c6-330">Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="c84c6-331">Wählen Sie die Datei, und klicken Sie dann im Inspector sicher, dass</span><span class="sxs-lookup"><span data-stu-id="c84c6-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="c84c6-332">**Jede Plattform** ist **deaktiviert**</span><span class="sxs-lookup"><span data-stu-id="c84c6-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="c84c6-333">**nur** **WSAPlayer** ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="c84c6-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="c84c6-334">**Nicht verarbeiten** ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="c84c6-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="c84c6-335">Kapitel 7 – Erstellen der BotTag</span><span class="sxs-lookup"><span data-stu-id="c84c6-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="c84c6-336">Erstellen Sie ein neues **Tag** Objekt mit dem Namen **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="c84c6-337">Wählen Sie die Main-Kamera in der Szene.</span><span class="sxs-lookup"><span data-stu-id="c84c6-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="c84c6-338">Klicken Sie auf das Tag-Dropdown-Menü in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="c84c6-339">Klicken Sie auf **Tag hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-339">Click on **Add Tag**.</span></span>

    ![Kamera-Setup](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="c84c6-341">Klicken Sie auf die **+** Symbol.</span><span class="sxs-lookup"><span data-stu-id="c84c6-341">Click on the **+** symbol.</span></span> <span data-ttu-id="c84c6-342">Benennen Sie den neuen **Tag** als **BotTag**, *speichern*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Kamera-Setup](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="c84c6-344">**Nicht** gelten die **BotTag** bis zur Kamera Main.</span><span class="sxs-lookup"><span data-stu-id="c84c6-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="c84c6-345">Wenn Sie versehentlich dies getan haben, stellen Sie sicher, so ändern Sie den Tag an Main Camera *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="c84c6-346">Kapitel 8 – Erstellen der BotObjects-Klasse</span><span class="sxs-lookup"><span data-stu-id="c84c6-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="c84c6-347">Ist das erste Skript, das Sie erstellen müssen die **BotObjects** -Klasse, die eine leere Klasse erstellt, sodass eine Reihe von anderen Klassenobjekten innerhalb des gleichen Skripts gespeichert werden kann, und klicken Sie nach anderen Skripts in der Szene zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="c84c6-348">Die Erstellung von dieser Klasse ist ausschließlich eine architektonische Option, diese Objekte können stattdessen im Bot-Skript, das Sie später in diesem Kurs erstellen gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="c84c6-349">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-349">To create this class:</span></span> 

1.  <span data-ttu-id="c84c6-350">Mit der rechten Maustaste den *Projektfenster*, klicken Sie dann **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="c84c6-351">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-351">Name the folder **Scripts**.</span></span> 

    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="c84c6-353">Doppelklicken Sie auf die **Skripts** Ordner aus, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="c84c6-354">In diesem Ordner, die mit der rechten Maustaste und wählen Sie dann **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="c84c6-355">Nennen Sie das Skript **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="c84c6-356">Doppelklicken Sie auf die neue **BotObjects** Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="c84c6-357">Löschen Sie den Inhalt des Skripts aus, und Ersetzen Sie ihn durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="c84c6-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="c84c6-358">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="c84c6-359">Kapitel 9: Erstellen der GazeInput-Klasse</span><span class="sxs-lookup"><span data-stu-id="c84c6-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="c84c6-360">Die nächste Klasse, die Sie erstellen wollen ist die **GazeInput** Klasse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="c84c6-361">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="c84c6-361">This class is responsible for:</span></span>

- <span data-ttu-id="c84c6-362">Erstellen eines Cursors, der darstellt der *bestaunen* des Spielers.</span><span class="sxs-lookup"><span data-stu-id="c84c6-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="c84c6-363">Erkennen von Objekten, die durch die Blicke des Players erreicht, und verweisen auf erkannte Objekte.</span><span class="sxs-lookup"><span data-stu-id="c84c6-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="c84c6-364">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-364">To create this class:</span></span> 

1.  <span data-ttu-id="c84c6-365">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="c84c6-366">Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="c84c6-367">Rufen Sie das Skript **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="c84c6-368">Doppelklicken Sie auf die neue **GazeInput** Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="c84c6-369">Fügen Sie die folgende Zeile oben rechts auf den Namen der Klasse:</span><span class="sxs-lookup"><span data-stu-id="c84c6-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="c84c6-370">Klicken Sie dann fügen Sie die folgenden Variablen in der **GazeInput** Klasse, über die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="c84c6-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="c84c6-371">Code für **Start()** Methode hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="c84c6-372">Dies wird aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="c84c6-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="c84c6-373">Implementieren Sie eine Methode, die instanziiert und den Cursor Blicke einrichten:</span><span class="sxs-lookup"><span data-stu-id="c84c6-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="c84c6-374">Implementieren Sie die Methoden, die werden die Raycast von der Main-Kamera eingerichtet und werden mitverfolgen fokussierte Objekt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="c84c6-375">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="c84c6-376">Kapitel 10 – Erstellen der Bot-Klasse</span><span class="sxs-lookup"><span data-stu-id="c84c6-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="c84c6-377">Das Skript, das Sie erstellen wollen nun heißt **Bot**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="c84c6-378">Dies ist die Hauptklasse der Anwendung, die sie speichert:</span><span class="sxs-lookup"><span data-stu-id="c84c6-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="c84c6-379">Ihre Web-App-Bot-Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="c84c6-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="c84c6-380">Die Methode, die die User Voice-Befehle erfasst.</span><span class="sxs-lookup"><span data-stu-id="c84c6-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="c84c6-381">Die zum Initiieren Konversationen mit Ihrer Web-App-Bot-Methode</span><span class="sxs-lookup"><span data-stu-id="c84c6-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="c84c6-382">Die zum Senden von Nachrichten an Ihre Web-App-Bot-Methode</span><span class="sxs-lookup"><span data-stu-id="c84c6-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="c84c6-383">Zum Senden von Nachrichten an den Bot-Dienst, der **SendMessageToBot()** Coroutine erstellen eine Aktivität, die ein Objekt, das von Bot Framework erkannt werden, wie Daten, die vom Benutzer gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="c84c6-384">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-384">To create this class:</span></span> 

1. <span data-ttu-id="c84c6-385">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="c84c6-386">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c84c6-387">Nennen Sie das Skript **Bot**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="c84c6-388">Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="c84c6-389">Aktualisieren Sie die Namespaces, um Folgendes am Anfang entsprechen den **Bot** Klasse:</span><span class="sxs-lookup"><span data-stu-id="c84c6-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="c84c6-390">In der **Bot** Klasse fügen Sie die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="c84c6-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="c84c6-391">Stellen Sie sicher, Sie fügen Ihre **Bot Geheimschlüssel** in die **BotSecret** Variable.</span><span class="sxs-lookup"><span data-stu-id="c84c6-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="c84c6-392">Sie haben angemerkt Ihre **Bot Geheimschlüssel** am Anfang des diesem Kurs in  **[Kapitel 2](#chapter-2---create-the-azure-bot-service), Schritt 10**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="c84c6-393">Code für **Awake()** und **Start()** jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="c84c6-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="c84c6-394">Fügen Sie den zwei Handler, die von Sprachbibliotheken aufgerufen werden, wenn Sprachaufnahme beginnt und endet.</span><span class="sxs-lookup"><span data-stu-id="c84c6-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="c84c6-395">Die *DictationRecognizer* wird automatisch beendet, die Stimme des Benutzers erfassen, wenn der Benutzer die Spracheingabe beendet.</span><span class="sxs-lookup"><span data-stu-id="c84c6-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="c84c6-396">Der folgende Handler das Ergebnis der Spracheingabe des Benutzers erfasst und die Coroutine verantwortlich für das Senden der Nachricht an die Web-App-Bot-Dienst aufruft.</span><span class="sxs-lookup"><span data-stu-id="c84c6-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="c84c6-397">Die folgende Coroutine wird aufgerufen, um eine Konversation mit dem Bot zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="c84c6-398">Sie werden feststellen, sobald der Konversation-Aufruf abgeschlossen ist, aufgerufen wird die **SendMessageToCoroutine()** durch eine Reihe von Parametern, die die Aktivität, die an der Bot Service als eine leere Nachricht gesendet werden festgelegt, wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="c84c6-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="c84c6-399">Dies erfolgt, um fordert der Bot Service, um das Dialogfeld zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="c84c6-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="c84c6-400">Die folgende Coroutine wird aufgerufen, um erstellen die Aktivität, die an den Bot-Dienst gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="c84c6-401">Die folgende Coroutine wird aufgerufen, um eine Antwort nach dem Senden einer Aktivitäts mit dem Bot-Dienst anzufordern.</span><span class="sxs-lookup"><span data-stu-id="c84c6-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="c84c6-402">Die letzte Methode dieser Klasse hinzugefügt werden, ist erforderlich, die Nachricht in der Szene angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c84c6-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="c84c6-403">Sie möglicherweise ein Fehler in der Unity-Editor-Konsole über fehlende finden Sie unter den **SceneOrganiser** Klasse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="c84c6-404">Ignorieren Sie diese, wie Sie diese Klasse später in diesem Tutorial erstellen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="c84c6-405">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="c84c6-406">Kapitel 11: Erstellen der Interaktionen-Klasse</span><span class="sxs-lookup"><span data-stu-id="c84c6-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="c84c6-407">Die Klasse, die Sie erstellen wollen nun heißt **Interaktionen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="c84c6-408">Diese Klasse wird verwendet, um die HoloLens Tippen Sie auf Eingabe vom Benutzer zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="c84c6-409">Wenn der Benutzer tippt, bei der Suche auf die *Bot* -Objekt in der Szene, und der Bot ist bereit zum Abhören von Spracheingaben, die Bot-Objekt ändert die Farbe an, die **roten** und Spracheingaben lauscht.</span><span class="sxs-lookup"><span data-stu-id="c84c6-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="c84c6-410">Diese Klasse erbt von der **GazeInput** Klasse, und kann daher auf die **Start()** -Methode und Variablen von dieser Klasse, gekennzeichnet durch die Verwendung von **Basis**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="c84c6-411">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-411">To create this class:</span></span>

1.  <span data-ttu-id="c84c6-412">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c84c6-413">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c84c6-414">Nennen Sie das Skript **Interaktionen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="c84c6-415">Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="c84c6-416">Aktualisieren Sie die Namespaces und die klassenvererbung mit dem folgenden, am oberen Rand identisch sein der **Interaktionen** Klasse:</span><span class="sxs-lookup"><span data-stu-id="c84c6-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="c84c6-417">In der **Interaktionen** Klasse fügen Sie die folgende Variable hinzu:</span><span class="sxs-lookup"><span data-stu-id="c84c6-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="c84c6-418">Fügen Sie dann die **Start()** Methode:</span><span class="sxs-lookup"><span data-stu-id="c84c6-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="c84c6-419">Hinzufügen des ereignishandlers, der ausgelöst wird, wenn der Benutzer die tippbewegung vor der Kamera HoloLens ausführt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="c84c6-420">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="c84c6-421">Kapitel 12 – Erstellen der SceneOrganiser-Klasse</span><span class="sxs-lookup"><span data-stu-id="c84c6-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="c84c6-422">Die letzte Klasse erforderlich, die in dieser Übung wird aufgerufen, **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="c84c6-423">Diese Klasse wird die Szene programmgesteuert eingerichtet, von dem Main Camera-Komponenten und Skripts hinzufügen und erstellen die entsprechenden Objekte in der Szene.</span><span class="sxs-lookup"><span data-stu-id="c84c6-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="c84c6-424">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-424">To create this class:</span></span>

1.  <span data-ttu-id="c84c6-425">Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c84c6-426">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c84c6-427">Nennen Sie das Skript **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="c84c6-428">Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="c84c6-429">In der **SceneOrganiser** Klasse fügen Sie die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="c84c6-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="c84c6-430">Fügen Sie dann die **Awake()** und **Start()** Methoden:</span><span class="sxs-lookup"><span data-stu-id="c84c6-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="c84c6-431">Fügen Sie die folgende Methode, die verantwortlich für die Bot-Objekt in der Szene erstellt und die Parameter und Komponenten einrichten:</span><span class="sxs-lookup"><span data-stu-id="c84c6-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="c84c6-432">Fügen Sie die folgende Methode, die dafür verantwortlich, erstellen das UI-Objekt in der Szene, die Antworten von den Bot darstellt:</span><span class="sxs-lookup"><span data-stu-id="c84c6-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="c84c6-433">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="c84c6-434">Im Unity-Editor, ziehen Sie die **SceneOrganiser** Skript aus dem Ordner Scripts der Main-Kamera.</span><span class="sxs-lookup"><span data-stu-id="c84c6-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="c84c6-435">Die Szene Organiser für Komponente sollte jetzt in der Main Camera-Objekts angezeigt werden, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="c84c6-437">Kapitel 13 – vor dem Erstellen</span><span class="sxs-lookup"><span data-stu-id="c84c6-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="c84c6-438">Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="c84c6-439">Vor dem Ausführen, stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="c84c6-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="c84c6-440">Alle Einstellungen, die bereits erwähnt, der [ **Kapitel 4** ](#Chapter-4-–-Set-up-the-unity-project) ordnungsgemäß festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="c84c6-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="c84c6-441">Das Skript **SceneOrganiser** angefügt ist die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="c84c6-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="c84c6-442">In der **Bot** Klasse, stellen Sie sicher, dass Sie eingefügt haben Ihre **Bot Geheimschlüssel** in die **BotSecret** Variable.</span><span class="sxs-lookup"><span data-stu-id="c84c6-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="c84c6-443">Kapitel 14 – erstellen und per sideload übertragen, um die HoloLens</span><span class="sxs-lookup"><span data-stu-id="c84c6-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="c84c6-444">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.</span><span class="sxs-lookup"><span data-stu-id="c84c6-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="c84c6-445">Navigieren Sie zu **Buildeinstellungen**, **Datei > Buildeinstellungen...** .</span><span class="sxs-lookup"><span data-stu-id="c84c6-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="c84c6-446">Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Erstellen der app von Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="c84c6-448">Falls noch nicht geschehen, aktivieren Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="c84c6-449">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-449">Click **Build**.</span></span> <span data-ttu-id="c84c6-450">Unity startet eine **Datei-Explorer** Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="c84c6-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c84c6-451">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="c84c6-452">Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="c84c6-453">Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="c84c6-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="c84c6-454">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="c84c6-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="c84c6-455">Kapitel 15 – bereitstellen, um HoloLens</span><span class="sxs-lookup"><span data-stu-id="c84c6-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="c84c6-456">Für HoloLens bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c84c6-457">Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="c84c6-458">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="c84c6-458">To do this:</span></span>

    1. <span data-ttu-id="c84c6-459">Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="c84c6-460">Wechseln Sie zu **Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="c84c6-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="c84c6-461">Beachten Sie die **IPv4** Adresse.</span><span class="sxs-lookup"><span data-stu-id="c84c6-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="c84c6-462">Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit > für Entwickler**</span><span class="sxs-lookup"><span data-stu-id="c84c6-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="c84c6-463">Festlegen des Entwicklermodus auf.</span><span class="sxs-lookup"><span data-stu-id="c84c6-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="c84c6-464">Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="c84c6-465">In der **Projektmappenkonfiguration** wählen **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="c84c6-466">In der **Projektmappenplattform**Option **X86**, **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="c84c6-468">Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen**, zum querladen der Anwendung in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c84c6-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="c84c6-469">Ihre app sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="c84c6-470">Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**.</span><span class="sxs-lookup"><span data-stu-id="c84c6-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="c84c6-471">Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **Menü "Build"**, wählen *Projektmappe bereitstellen*.</span><span class="sxs-lookup"><span data-stu-id="c84c6-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="c84c6-472">Kapitel 16 – mithilfe der Anwendung auf die HoloLens</span><span class="sxs-lookup"><span data-stu-id="c84c6-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="c84c6-473">Nachdem Sie die Anwendung gestartet haben, sehen Sie den Bot als eine blaue Kugel vor Ihnen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="c84c6-474">Verwenden der **tippen Geste** während Sie auf der Kugel eine Konversation initiieren gazing sind.</span><span class="sxs-lookup"><span data-stu-id="c84c6-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="c84c6-475">Warten Sie, bis die Konversation zu starten (die Benutzeroberfläche wird eine Meldung angezeigt, wenn dies geschieht).</span><span class="sxs-lookup"><span data-stu-id="c84c6-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="c84c6-476">Wenn Sie die einleitende Meldung vom Bot erhalten haben, tippen Sie erneut auf den Bot damit beginnen, Ihre Meinung hören und rot angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c84c6-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="c84c6-477">Nachdem Sie die Kommunikation beenden, Ihre Anwendung sendet die Nachricht an den Bot, und erhalten Sie umgehend eine Antwort, die in der Benutzeroberfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c84c6-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="c84c6-478">Wiederholen Sie den Vorgang, um Ihrem bot weitere Nachrichten senden (Sie müssen jedes Mal, die Sie Sen eine Nachricht möchten, tippen Sie auf).</span><span class="sxs-lookup"><span data-stu-id="c84c6-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="c84c6-479">Diese Konversation wird veranschaulicht, wie der Bot Informationen (Ihr Name), beibehalten kann, während zugleich die bekannten Informationen (z. B. die Elemente, die auf Lager sind).</span><span class="sxs-lookup"><span data-stu-id="c84c6-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="c84c6-480">Einige Fragen zu den Bot Fragen:</span><span class="sxs-lookup"><span data-stu-id="c84c6-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="c84c6-481">Der fertigen Anwendung für die Web-App-Bot (v4)</span><span class="sxs-lookup"><span data-stu-id="c84c6-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="c84c6-482">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die nutzt die Azure-Web-App-Bot, Microsoft Bot Framework v4.</span><span class="sxs-lookup"><span data-stu-id="c84c6-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Endprodukt](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c84c6-484">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="c84c6-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c84c6-485">Übung 1</span><span class="sxs-lookup"><span data-stu-id="c84c6-485">Exercise 1</span></span>

<span data-ttu-id="c84c6-486">Die Struktur der Konversation in dieser Übung ist sehr einfach.</span><span class="sxs-lookup"><span data-stu-id="c84c6-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="c84c6-487">Nutzen Sie Microsoft LUIS, um Ihren Bot Möglichkeiten der natürlichen Sprache Grundlegendes zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c84c6-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c84c6-488">Übung 2</span><span class="sxs-lookup"><span data-stu-id="c84c6-488">Exercise 2</span></span>

<span data-ttu-id="c84c6-489">In diesem Beispiel enthält keine, eine Konversation zu beenden und neu zu starten eine neue Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="c84c6-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="c84c6-490">Machen Sie die Bot-Funktion abgeschlossen ist, versuchen, schließen Sie sich dem Gespräch zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="c84c6-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
