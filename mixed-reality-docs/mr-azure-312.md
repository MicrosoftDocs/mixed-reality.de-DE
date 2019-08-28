---
title: Mr-und Azure 312-bot-Integration
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie einen bot mit Microsoft bot Framework V4 erstellen und bereitstellen und in einer gemischten Reality-Anwendung mit ihm kommunizieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Maschinelles sehen, hololens, immersive, VR, Microsoft bot Framework V4, Web-App-bot, bot Framework, Microsoft bot
ms.openlocfilehash: 481693b5af8c946e1cb45dda5144e78a175fa771
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047231"
---
>[!NOTE]
><span data-ttu-id="2b065-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="2b065-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2b065-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="2b065-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2b065-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2b065-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="2b065-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2b065-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="2b065-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2b065-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="2b065-110">Mr und Azure 312: Bot-Integration</span><span class="sxs-lookup"><span data-stu-id="2b065-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="2b065-111">In diesem Kurs erfahren Sie, wie Sie mithilfe von Microsoft bot Framework V4 einen Bot erstellen und bereitstellen und über eine Windows Mixed Reality-Anwendung mit ihm kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="2b065-112">Das **Microsoft bot Framework V4** ist ein Satz von APIs, die Entwicklern die Tools zum Erstellen einer erweiterbaren und skalierbaren bot-Anwendung zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="2b065-113">Weitere Informationen finden Sie auf der [Microsoft bot Framework-Seite](https://dev.botframework.com/) oder im [V4-git-Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="2b065-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="2b065-114">Nachdem Sie diesen Kurs abgeschlossen haben, haben Sie eine Windows Mixed Reality-Anwendung erstellt, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="2b065-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="2b065-115">Verwenden Sie eine **Tap-Geste** , um den bot zu starten, der die Benutzer Stimme abhört.</span><span class="sxs-lookup"><span data-stu-id="2b065-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="2b065-116">Wenn der Benutzer etwas gesagt hat, versucht der bot, eine Antwort bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="2b065-117">Zeigen Sie die Bots-Antwort als Text an, der in der Nähe des bot in der Unity-Szene positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="2b065-118">In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="2b065-119">In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="2b065-120">Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="2b065-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="2b065-121">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="2b065-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2b065-122">Natürlich</span><span class="sxs-lookup"><span data-stu-id="2b065-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2b065-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2b065-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2b065-124"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="2b065-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2b065-125">Mr und Azure 312: Bot-Integration</span><span class="sxs-lookup"><span data-stu-id="2b065-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="2b065-126">✔️</span><span class="sxs-lookup"><span data-stu-id="2b065-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2b065-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2b065-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2b065-128">Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets.</span><span class="sxs-lookup"><span data-stu-id="2b065-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="2b065-129">Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="2b065-130">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="2b065-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b065-131">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="2b065-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2b065-132">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="2b065-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2b065-133">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018).</span><span class="sxs-lookup"><span data-stu-id="2b065-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="2b065-134">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="2b065-135">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="2b065-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2b065-136">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="2b065-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2b065-137">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="2b065-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2b065-138">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="2b065-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2b065-139">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="2b065-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2b065-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2b065-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="2b065-141">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="2b065-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="2b065-142">Internet Zugang für Azure und für den Azure-bot-Abruf.</span><span class="sxs-lookup"><span data-stu-id="2b065-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="2b065-143">Weitere Informationen [finden Sie unter diesem Link](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="2b065-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="2b065-144">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="2b065-144">Before you start</span></span>

1.  <span data-ttu-id="2b065-145">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="2b065-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="2b065-146">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="2b065-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="2b065-147">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="2b065-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="2b065-148">Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="2b065-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="2b065-149">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="2b065-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="2b065-150">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="2b065-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="2b065-151">Kapitel 1 – Erstellen der bot-Anwendung</span><span class="sxs-lookup"><span data-stu-id="2b065-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="2b065-152">Der erste Schritt besteht darin, den bot als lokale Webanwendung ASP.net Core zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="2b065-153">Nachdem Sie den Vorgang abgeschlossen und getestet haben, veröffentlichen Sie ihn im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="2b065-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="2b065-154">Öffnen Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2b065-154">Open Visual Studio.</span></span> <span data-ttu-id="2b065-155">Erstellen Sie ein neues Projekt, wählen Sie **ASP NET Core-Webanwendung** als Projekttyp aus (Sie finden Sie im unter Abschnitt .net Core) und nennen Sie **mybot**.</span><span class="sxs-lookup"><span data-stu-id="2b065-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="2b065-156">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b065-156">Click **OK**.</span></span>

2.  <span data-ttu-id="2b065-157">Wählen Sie im angezeigten Fenster die Option **leer**aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="2b065-158">Stellen Sie außerdem sicher, dass das Ziel auf **ASP NET Core 2,0** festgelegt ist und die Authentifizierung auf **keine Authentifizierung**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="2b065-159">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b065-159">Click **OK**.</span></span>  

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="2b065-161">Die Projekt Mappe wird jetzt geöffnet.</span><span class="sxs-lookup"><span data-stu-id="2b065-161">The solution will now open.</span></span> <span data-ttu-id="2b065-162">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Projekt Mappe **mybot** , und klicken Sie auf **nuget-Pakete für**Projekt Mappe verwalten.</span><span class="sxs-lookup"><span data-stu-id="2b065-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="2b065-164">Suchen Sie auf der Registerkarte **Durchsuchen** nach **Microsoft. bot. Builder. Integration. Aspnet. Core** (stellen Sie sicher, dass die **Vorabversion** aktiviert ist).</span><span class="sxs-lookup"><span data-stu-id="2b065-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="2b065-165">Wählen Sie die Paketversion **4.0.1-Vorschau**aus, und klicken Sie auf die Projekt Felder.</span><span class="sxs-lookup"><span data-stu-id="2b065-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="2b065-166">Klicken Sie dann auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="2b065-166">Then click on **Install**.</span></span> <span data-ttu-id="2b065-167">Sie haben nun die Bibliotheken installiert, die für **bot Framework V4**benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="2b065-168">Schließen Sie die Seite "nuget".</span><span class="sxs-lookup"><span data-stu-id="2b065-168">Close the NuGet page.</span></span>

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="2b065-170">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das *Projekt* **mybot**, und klicken Sie auf **Klasse** **Hinzufügen** **|** .</span><span class="sxs-lookup"><span data-stu-id="2b065-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="2b065-172">Benennen Sie die Klasse **mybot** , und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="2b065-174">Wiederholen Sie den vorherigen Punkt, um eine weitere Klasse mit dem Namen " **Kontexts**" zu erstellen</span><span class="sxs-lookup"><span data-stu-id="2b065-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="2b065-175">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **wwwroot** , und klicken Sie auf **Neues Element** **Hinzufügen** **|** .</span><span class="sxs-lookup"><span data-stu-id="2b065-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="2b065-176">Wählen Sie **HTML-Seite** aus (Sie finden Sie im unter Abschnitt Web).</span><span class="sxs-lookup"><span data-stu-id="2b065-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="2b065-177">Nennen Sie die Datei **default. html**.</span><span class="sxs-lookup"><span data-stu-id="2b065-177">Name the file **default.html**.</span></span> <span data-ttu-id="2b065-178">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-178">Click **Add**.</span></span>

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="2b065-180">Die Liste der Klassen/Objekte in der **Projektmappen-Explorer** sollte wie in der folgenden Abbildung aussehen.</span><span class="sxs-lookup"><span data-stu-id="2b065-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="2b065-182">Doppelklicken Sie auf die Klasse **conversationcontext** .</span><span class="sxs-lookup"><span data-stu-id="2b065-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="2b065-183">Diese Klasse ist dafür verantwortlich, die Variablen beizubehalten, die vom bot verwendet werden, um den Konversations Kontext beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="2b065-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="2b065-184">Diese Konversations Kontext Werte werden in einer Instanz dieser Klasse verwaltet, da jede Instanz der **mybot** -Klasse jedes Mal aktualisiert wird, wenn eine Aktivität empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="2b065-185">Fügen Sie der-Klasse den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="2b065-186">Doppelklicken Sie auf die **mybot** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="2b065-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="2b065-187">Diese Klasse hostet die Handler, die von allen eingehenden Aktivitäten vom Kunden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="2b065-188">In dieser Klasse fügen Sie den Code hinzu, der verwendet wird, um die Konversation zwischen dem bot und dem Kunden zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="2b065-189">Wie bereits erwähnt, wird eine Instanz dieser Klasse jedes Mal initialisiert, wenn eine Aktivität empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="2b065-190">Fügen Sie dieser Klasse den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="2b065-191">Doppelklicken Sie auf die **Startup** -Klasse.</span><span class="sxs-lookup"><span data-stu-id="2b065-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="2b065-192">Diese Klasse initialisiert den bot.</span><span class="sxs-lookup"><span data-stu-id="2b065-192">This class will initialize the bot.</span></span> <span data-ttu-id="2b065-193">Fügen Sie der-Klasse den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="2b065-194">Öffnen Sie die **Programm** Klassendatei, und überprüfen Sie, ob der Code darin identisch mit folgendem ist:</span><span class="sxs-lookup"><span data-stu-id="2b065-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="2b065-195">Denken Sie daran, die Änderungen zu speichern, und klicken Sie hierzu auf der Symbolleiste oben in Visual Studio auf **Datei** > **Alle speichern**.</span><span class="sxs-lookup"><span data-stu-id="2b065-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="2b065-196">Kapitel 2: Erstellen des Azure bot Service</span><span class="sxs-lookup"><span data-stu-id="2b065-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="2b065-197">Nachdem Sie den Code für den bot erstellt haben, müssen Sie ihn im Azure-Portal in einer Instanz des *webapp* -botdiensts veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="2b065-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="2b065-198">In diesem Kapitel erfahren Sie, wie Sie den bot-Dienst in Azure erstellen und konfigurieren und dann Ihren Code darauf veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="2b065-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="2b065-199">Melden Sie sich zunächst beim Azure-Portal an https://portal.azure.com) (.</span><span class="sxs-lookup"><span data-stu-id="2b065-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="2b065-200">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2b065-201">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2b065-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2b065-202">Nachdem Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **Ressource erstellen** , suchen Sie nach *Web-App-bot*, und **drücken**Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="2b065-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="2b065-204">Auf der neuen Seite wird eine Beschreibung des *Web-App* -botdiensts bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="2b065-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="2b065-205">Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="2b065-207">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="2b065-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="2b065-208">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="2b065-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="2b065-209">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="2b065-210">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="2b065-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="2b065-211">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="2b065-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2b065-212">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="2b065-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="2b065-213">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter [diesem Link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) .</span><span class="sxs-lookup"><span data-stu-id="2b065-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="2b065-214">Bestimmen Sie den Speicherort für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="2b065-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2b065-215">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2b065-216">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2b065-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="2b065-217">Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen *Web-App-bot* -Dienst erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="2b065-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="2b065-218">Der **Name der APP** kann nur mit dem botnamenübereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="2b065-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="2b065-219">Belassen Sie die *bot-Vorlage* als **Basic (C#)** .</span><span class="sxs-lookup"><span data-stu-id="2b065-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="2b065-220">Der *App Service-Plan/Standort* muss für Ihr Konto automatisch ausgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="2b065-221">Legen Sie die **Azure Storage** fest, die Sie zum Hosten des Bots verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="2b065-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="2b065-222">Wenn Sie noch nicht über ein solches verfügen, können Sie es hier erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="2b065-223">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="2b065-224">Klicken Sie auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-224">Click Create.</span></span>
 
        ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="2b065-226">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="2b065-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="2b065-227">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2b065-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="2b065-229">Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="2b065-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="2b065-231">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="2b065-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="2b065-232">Sie gelangen zu ihrer neuen Azure-Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="2b065-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="2b065-234">An diesem Punkt müssen Sie eine Funktion namens **Direct Line** einrichten, damit Ihre Client Anwendung mit diesem botdienst kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="2b065-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="2b065-235">Klicken Sie auf **Channels**, und klicken Sie dann im Abschnitt **Hinzufügen eines vorgestellten Kanals** auf **direkt linienchannel konfigurieren**.</span><span class="sxs-lookup"><span data-stu-id="2b065-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="2b065-237">Auf dieser Seite finden Sie die **geheimen Schlüssel** , mit denen sich Ihre Client-App bei dem bot authentifizieren kann.</span><span class="sxs-lookup"><span data-stu-id="2b065-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="2b065-238">Klicken Sie auf die Schaltfläche **anzeigen** , und nehmen Sie eine Kopie einer der angezeigten Schlüssel auf, da Sie dies später in Ihrem Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="2b065-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="2b065-240">Kapitel 3 – Veröffentlichen des Bots für den Azure-Web-App-botdienst</span><span class="sxs-lookup"><span data-stu-id="2b065-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="2b065-241">Nachdem Ihr Dienst bereit ist, müssen Sie den von Ihnen zuvor erstellten botcode in ihren neu erstellten Web-App-botdienst veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="2b065-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="2b065-242">Sie müssen ihren bot jedes Mal im Azure-Dienst veröffentlichen, wenn Sie Änderungen an der bot-Lösung/dem Code vornehmen.</span><span class="sxs-lookup"><span data-stu-id="2b065-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="2b065-243">Wechseln Sie zurück zu Ihrer Visual Studio-Projekt Mappe, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="2b065-244">Klicken Sie mit der rechten Maustaste auf das Projekt **mybot** , und klicken Sie dann im **Projektmappen-Explorer**auf **veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="2b065-246">Klicken Sie auf der Seite *Veröffentlichungsziel auswählen* auf **App Service**, wählen Sie dann **vorhandene**aus, klicken Sie schließlich auf **Profil erstellen** (möglicherweise müssen Sie neben der Schaltfläche *veröffentlichen* auf den Dropdown Pfeil klicken, wenn dies nicht angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="2b065-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="2b065-248">Wenn Sie noch nicht bei Ihrem Microsoft-Konto angemeldet sind, müssen Sie dies hier tun.</span><span class="sxs-lookup"><span data-stu-id="2b065-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="2b065-249">Auf der Seite " **veröffentlichen** " müssen Sie das gleiche **Abonnement** festlegen, das Sie für die Erstellung des *Web-App* -botdiensts verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="2b065-250">Legen Sie dann die **Ansicht** als **Ressourcengruppe** fest, und wählen Sie in der Dropdown-Ordnerstruktur die **Ressourcengruppe** aus, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="2b065-251">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b065-251">Click **OK**.</span></span> 

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="2b065-253">Klicken Sie jetzt auf die Schaltfläche "Publish" ( **veröffentlichen** ), und warten Sie, bis der bot veröffentlicht wird (es kann einige Minuten dauern).</span><span class="sxs-lookup"><span data-stu-id="2b065-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="2b065-255">Kapitel 4 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="2b065-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="2b065-256">Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="2b065-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="2b065-257">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="2b065-257">Open *Unity* and click **New**.</span></span> 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="2b065-259">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="2b065-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="2b065-260">**Hololens-bot**einfügen.</span><span class="sxs-lookup"><span data-stu-id="2b065-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="2b065-261">Stellen Sie sicher, dass die Projektvorlage auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="2b065-262">Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="2b065-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2b065-263">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-263">Then, click **Create project**.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="2b065-265">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="2b065-266">Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="2b065-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2b065-267">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="2b065-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2b065-268">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="2b065-268">Close the **Preferences** window.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="2b065-270">Navigieren Sie als nächstes zu **Datei >** Buildeinstellungen, wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen</span><span class="sxs-lookup"><span data-stu-id="2b065-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="2b065-272">In **Datei >** Buildeinstellungen, und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="2b065-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="2b065-273">**Zielgerät** ist auf **hololens** festgelegt</span><span class="sxs-lookup"><span data-stu-id="2b065-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="2b065-274">Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.</span><span class="sxs-lookup"><span data-stu-id="2b065-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="2b065-275">Der Buildtyp ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2b065-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="2b065-276">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2b065-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="2b065-277">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2b065-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="2b065-278">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2b065-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="2b065-279">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="2b065-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="2b065-280">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="2b065-281">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2b065-281">A save window will appear.</span></span>
        
            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="2b065-283">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zuerstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="2b065-285">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **botscene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="2b065-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="2b065-287">Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="2b065-288">Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="2b065-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="2b065-290">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="2b065-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="2b065-291">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="2b065-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="2b065-292">Die **Skript Lauf Zeit Version** sollte **experimentell sein (NET 4,6-Entsprechung)** ; Wenn Sie dies ändern, muss der Editor neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="2b065-293">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="2b065-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="2b065-294">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="2b065-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="2b065-296">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2b065-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="2b065-297">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="2b065-297">**InternetClient**</span></span>
        - <span data-ttu-id="2b065-298">**Tritt**</span><span class="sxs-lookup"><span data-stu-id="2b065-298">**Microphone**</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="2b065-300">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="2b065-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="2b065-302">Zurück in Buildeinstellungen: _Unity C#_  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="2b065-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="2b065-303">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="2b065-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="2b065-304">Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).</span><span class="sxs-lookup"><span data-stu-id="2b065-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="2b065-305">Kapitel 5 – Kamera Einrichtung</span><span class="sxs-lookup"><span data-stu-id="2b065-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b065-306">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-312-Package. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren und dann fortfahren [. Kapitel 7](#chapter-8--create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="2b065-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="2b065-307">Wählen Sie im Bereich *Hierarchie*die **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="2b065-308">Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor-Panel*sehen.</span><span class="sxs-lookup"><span data-stu-id="2b065-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="2b065-309">Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="2b065-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="2b065-310">Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).</span><span class="sxs-lookup"><span data-stu-id="2b065-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="2b065-311">Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="2b065-312">Legen Sie **klar Flags** auf voll Tonfarbe fest.</span><span class="sxs-lookup"><span data-stu-id="2b065-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="2b065-313">Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest.</span><span class="sxs-lookup"><span data-stu-id="2b065-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Kamera-Setup](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="2b065-315">Kapitel 6 – Importieren der newtonsoft-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="2b065-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="2b065-316">Zum Deserialisieren und Serialisieren von Objekten, die empfangen und an den bot-Dienst gesendet werden, müssen Sie die **newtonsoft** -Bibliothek herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2b065-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="2b065-317">Sie finden eine [kompatible Version, die bereits mit der richtigen Unity-Ordnerstruktur organisiert](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="2b065-318">Verwenden Sie das Unity-Paket, das in diesem Kurs verwendet wurde, um die newtonsoft-Bibliothek in Ihr Projekt zu importieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="2b065-319">Fügen Sie das *. unitypackage* zu Unity hinzu, indem Sie die Menüoption **Assets** > **Import Package** > **Custom Package** verwenden.</span><span class="sxs-lookup"><span data-stu-id="2b065-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importieren der newtonsoft-Bibliothek](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="2b065-321">Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und einschließlich) Plug-ins ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importieren der newtonsoft-Bibliothek](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="2b065-323">Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2b065-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="2b065-324">Wechseln Sie in der Projektansicht in den Ordner **Newton Soft** unter Plug-in, und wählen Sie das newtonsoft-Plug-in aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="2b065-325">Vergewissern Sie sich, dass die Option "newtonsoft" ausgewähltist, und stellen Sie sicher, dass **alle Plattformen** deaktiviert sind.stellen Sie dann sicher, dass **wsaplayer** ebenfalls deaktiviert ist</span><span class="sxs-lookup"><span data-stu-id="2b065-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="2b065-326">Dies dient nur zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="2b065-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="2b065-327">Wenn Sie diese Plug-ins markieren, werden Sie nur im Unity-Editor verwendet.</span><span class="sxs-lookup"><span data-stu-id="2b065-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="2b065-328">Im WSA-Ordner gibt es eine andere Gruppe, die verwendet wird, nachdem das Projekt aus Unity exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="2b065-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="2b065-329">Als nächstes müssen Sie den Ordner " **WSA** " im Ordner " **newtonsoft** " öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="2b065-330">Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="2b065-331">Wählen Sie die Datei aus, und vergewissern Sie sich dann im Inspektor, dass</span><span class="sxs-lookup"><span data-stu-id="2b065-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="2b065-332">**Jede Plattform** ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="2b065-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="2b065-333">**nur** **Wsaplayer** ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="2b065-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="2b065-334">"Nicht **verarbeiten** " ist **aktiviert**</span><span class="sxs-lookup"><span data-stu-id="2b065-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="2b065-335">Kapitel 7 – Erstellen des bottag</span><span class="sxs-lookup"><span data-stu-id="2b065-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="2b065-336">Erstellen Sie ein neues tagobjekt mit dem Namen **bottag**.</span><span class="sxs-lookup"><span data-stu-id="2b065-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="2b065-337">Wählen Sie die Hauptkamera in der Szene aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="2b065-338">Klicken Sie im Inspektor-Panel auf das Dropdown Menü Tag.</span><span class="sxs-lookup"><span data-stu-id="2b065-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="2b065-339">Klicken Sie auf **Tag hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-339">Click on **Add Tag**.</span></span>

    ![Kamera-Setup](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="2b065-341">Klicken Sie auf **+** das Symbol.</span><span class="sxs-lookup"><span data-stu-id="2b065-341">Click on the **+** symbol.</span></span> <span data-ttu-id="2b065-342">Nennen Sie das neue **Tag** als **bottag**, *Speichern*.</span><span class="sxs-lookup"><span data-stu-id="2b065-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Kamera-Setup](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="2b065-344">Wenden Sie das **bottag** **nicht** auf die Hauptkamera an.</span><span class="sxs-lookup"><span data-stu-id="2b065-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="2b065-345">Wenn Sie dies versehentlich abgeschlossen haben, stellen Sie sicher, dass Sie das Hauptkamera-Tag wieder in " *maincamera*" ändern.</span><span class="sxs-lookup"><span data-stu-id="2b065-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="2b065-346">Kapitel 8 – Erstellen der botobjects-Klasse</span><span class="sxs-lookup"><span data-stu-id="2b065-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="2b065-347">Das erste Skript, das Sie erstellen müssen, ist die **botobjects** -Klasse, bei der es sich um eine leere Klasse handelt, die erstellt wird, sodass eine Reihe von anderen Klassen Objekten innerhalb desselben Skripts gespeichert und von anderen Skripts in der Szene aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="2b065-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="2b065-348">Bei der Erstellung dieser Klasse handelt es sich lediglich um eine architektonische Wahl. diese Objekte könnten stattdessen in dem bot-Skript gehostet werden, das Sie später in diesem Kurs erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="2b065-349">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="2b065-349">To create this class:</span></span> 

1.  <span data-ttu-id="2b065-350">Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und erstellen Sie dann **> Ordner**.</span><span class="sxs-lookup"><span data-stu-id="2b065-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="2b065-351">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="2b065-351">Name the folder **Scripts**.</span></span> 

    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="2b065-353">Doppelklicken Sie auf den Ordner **Scripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="2b065-354">Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und wählen Sie  **C# > Skript erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="2b065-355">Benennen Sie das Skript mit dem Namen **botobjects**.</span><span class="sxs-lookup"><span data-stu-id="2b065-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="2b065-356">Doppelklicken Sie auf das neue **botobjects** -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="2b065-357">Löschen Sie den Inhalt des Skripts, und ersetzen Sie ihn durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="2b065-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="2b065-358">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2b065-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="2b065-359">Kapitel 9 – Erstellen der Klasse "gazeinput"</span><span class="sxs-lookup"><span data-stu-id="2b065-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="2b065-360">Die nächste Klasse, die Sie erstellen, ist die " **gazeinput** "-Klasse.</span><span class="sxs-lookup"><span data-stu-id="2b065-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="2b065-361">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="2b065-361">This class is responsible for:</span></span>

- <span data-ttu-id="2b065-362">Erstellen eines Cursors, der den *Blick* des Players darstellt.</span><span class="sxs-lookup"><span data-stu-id="2b065-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="2b065-363">Erkennen von Objekten, die vom Blickpunkt des Players erreicht werden, und Speichern eines Verweises auf erkannte Objekte.</span><span class="sxs-lookup"><span data-stu-id="2b065-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="2b065-364">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="2b065-364">To create this class:</span></span> 

1.  <span data-ttu-id="2b065-365">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="2b065-366">Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen Sie > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="2b065-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="2b065-367">Nennen Sie das Skript " **gazeinput**".</span><span class="sxs-lookup"><span data-stu-id="2b065-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="2b065-368">Doppelklicken Sie auf das neue **gazeinput** -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="2b065-369">Fügen Sie die folgende Zeile rechts oben in den Klassennamen ein:</span><span class="sxs-lookup"><span data-stu-id="2b065-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="2b065-370">Fügen Sie dann die folgenden Variablen in der Klasse " **gazeinput** " oberhalb der Methode " **Start ()** " hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="2b065-371">Code für die Methode " **Start ()** " sollte hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="2b065-372">Dies wird aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="2b065-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="2b065-373">Implementieren Sie eine Methode, die den Cursor Cursor instanziieren und einrichten soll:</span><span class="sxs-lookup"><span data-stu-id="2b065-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="2b065-374">Implementieren Sie die Methoden, die den raycast von der Hauptkamera einrichten, und verfolgen Sie das aktuelle fokussierte Objekt.</span><span class="sxs-lookup"><span data-stu-id="2b065-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="2b065-375">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2b065-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="2b065-376">Kapitel 10 – Erstellen der bot-Klasse</span><span class="sxs-lookup"><span data-stu-id="2b065-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="2b065-377">Das Skript, das Sie jetzt erstellen, wird als **bot**bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="2b065-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="2b065-378">Dies ist die Kern Klasse Ihrer Anwendung, die gespeichert wird:</span><span class="sxs-lookup"><span data-stu-id="2b065-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="2b065-379">Ihre Web-App-botanmelde Informationen</span><span class="sxs-lookup"><span data-stu-id="2b065-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="2b065-380">Die Methode, die die User Voice-Befehle sammelt.</span><span class="sxs-lookup"><span data-stu-id="2b065-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="2b065-381">Die erforderliche Methode zum Initiieren von Konversationen mit dem Web-App-bot</span><span class="sxs-lookup"><span data-stu-id="2b065-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="2b065-382">Die erforderliche Methode zum Senden von Nachrichten an Ihren Web-App-bot</span><span class="sxs-lookup"><span data-stu-id="2b065-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="2b065-383">Um Nachrichten an den botdienst zu senden, erstellt die **sendmessageybot ()** -Coroutine eine-Aktivität, bei der es sich um ein Objekt handelt, das vom bot Framework als vom Benutzer gesendete Daten erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="2b065-384">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="2b065-384">To create this class:</span></span> 

1. <span data-ttu-id="2b065-385">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="2b065-386">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2b065-387">Benennen Sie den Skript- **bot**.</span><span class="sxs-lookup"><span data-stu-id="2b065-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="2b065-388">Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="2b065-389">Aktualisieren Sie die Namespaces so, dass Sie am Anfang der **bot** -Klasse wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="2b065-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="2b065-390">Fügen Sie innerhalb der **bot** -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="2b065-391">Stellen Sie sicher, dass Sie Ihren botsecret- **Schlüssel** in die **botsecret** -Variable einfügen.</span><span class="sxs-lookup"><span data-stu-id="2b065-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="2b065-392">Sie haben ihren botsecret- **Schlüssel** zu Beginn dieses Kurses in  **[Kapitel 2](#chapter-2---create-the-azure-bot-service), Schritt 10**notiert.</span><span class="sxs-lookup"><span data-stu-id="2b065-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="2b065-393">Der Code für " **Awa()** " und " **Start ()** " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="2b065-394">Fügen Sie die beiden Handler hinzu, die von den Sprach Bibliotheken aufgerufen werden, wenn die sprach Erfassung beginnt und endet.</span><span class="sxs-lookup"><span data-stu-id="2b065-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="2b065-395">Der " *diktationerkenzer* " hält die Erfassung der Benutzer Stimme automatisch an, wenn der Benutzer seine Sprache stoppt.</span><span class="sxs-lookup"><span data-stu-id="2b065-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="2b065-396">Der folgende Handler sammelt das Ergebnis der User Voice-Eingabe und ruft die Coroutine auf, die für das Senden der Nachricht an den Web-App-botdienst zuständig ist.</span><span class="sxs-lookup"><span data-stu-id="2b065-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="2b065-397">Die folgende Coroutine wird aufgerufen, um eine Konversation mit dem bot zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="2b065-398">Sie werden feststellen, dass nach Abschluss des Konversations Aufrufes die **sendmessagetocoroutine ()** aufruft, indem eine Reihe von Parametern übergeben wird, die festlegen, dass die Aktivität als leere Nachricht an den botdienst gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2b065-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="2b065-399">Dadurch wird der botdienst aufgefordert, den Dialog zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="2b065-400">Die folgende Coroutine wird aufgerufen, um die Aktivität zu erstellen, die an den bot-Dienst gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2b065-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="2b065-401">Die folgende Coroutine wird aufgerufen, um nach dem Senden einer Aktivität an den bot-Dienst eine Antwort anzufordern.</span><span class="sxs-lookup"><span data-stu-id="2b065-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="2b065-402">Die letzte Methode, die dieser Klasse hinzugefügt werden soll, ist erforderlich, um die Meldung in der Szene anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="2b065-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="2b065-403">In der Unity-Editor-Konsole wird möglicherweise ein Fehler angezeigt, in dem die **sceneorganisator** -Klasse fehlt.</span><span class="sxs-lookup"><span data-stu-id="2b065-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="2b065-404">Ignorieren Sie diese Meldung, da Sie diese Klasse später in diesem Tutorial erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="2b065-405">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2b065-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="2b065-406">Kapitel 11 – Erstellen der Klasse "Interaktionen"</span><span class="sxs-lookup"><span data-stu-id="2b065-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="2b065-407">Die Klasse, die Sie jetzt erstellen, wird als **Interaktionen**bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="2b065-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="2b065-408">Diese Klasse wird zum Erkennen der hololens-Tap-Eingaben vom Benutzer verwendet.</span><span class="sxs-lookup"><span data-stu-id="2b065-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="2b065-409">Wenn der Benutzer während der Betrachtung des *bot* -Objekts in der Szene tippt und der bot bereit ist, auf Spracheingaben zu lauschen, ändert sich das bot-Objekt in **rot** und beginnt mit dem lauschen auf Spracheingaben.</span><span class="sxs-lookup"><span data-stu-id="2b065-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="2b065-410">Diese Klasse erbt von der Klasse " **gazeinput** " und kann daher auf die Methode " **Start ()** " und Variablen aus dieser Klasse verweisen, die durch die Verwendung von " **Base**" bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="2b065-411">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="2b065-411">To create this class:</span></span>

1.  <span data-ttu-id="2b065-412">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2b065-413">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2b065-414">Benennen Sie das Skript mit **Interaktionen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="2b065-415">Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="2b065-416">Aktualisieren Sie die Namespaces und die Klassen Vererbung so, dass Sie am Anfang der Klasse **Interaktionen** mit der folgenden übereinstimmen:</span><span class="sxs-lookup"><span data-stu-id="2b065-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="2b065-417">Fügen Sie innerhalb der **Interaktionen** -Klasse die folgende Variable hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="2b065-418">Fügen Sie dann die Methode " **Start ()** " hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="2b065-419">Fügen Sie den Handler hinzu, der ausgelöst wird, wenn der Benutzer die Tap-Geste vor der hololens-Kamera ausführt.</span><span class="sxs-lookup"><span data-stu-id="2b065-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="2b065-420">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2b065-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="2b065-421">Kapitel 12 – Erstellen der sceneorganisator-Klasse</span><span class="sxs-lookup"><span data-stu-id="2b065-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="2b065-422">Die letzte in dieser Übungseinheit erforderliche Klasse heißt **sceneorganisator**.</span><span class="sxs-lookup"><span data-stu-id="2b065-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="2b065-423">Diese Klasse wird die Szene Programm gesteuert einrichten, indem der Hauptkamera Komponenten und Skripts hinzugefügt werden und die entsprechenden Objekte in der Szene erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="2b065-424">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="2b065-424">To create this class:</span></span>

1.  <span data-ttu-id="2b065-425">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2b065-426">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2b065-427">Nennen Sie das Skript **sceneorganisator**.</span><span class="sxs-lookup"><span data-stu-id="2b065-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="2b065-428">Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="2b065-429">Fügen Sie innerhalb der **sceneorganisator** -Klasse die folgenden Variablen hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="2b065-430">Fügen Sie dann die Methoden " **Awa()** " und " **Start ()** " hinzu:</span><span class="sxs-lookup"><span data-stu-id="2b065-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="2b065-431">Fügen Sie die folgende Methode hinzu, die für das Erstellen des bot-Objekts in der Szene und das Einrichten der Parameter und Komponenten zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="2b065-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="2b065-432">Fügen Sie die folgende Methode hinzu, die für die Erstellung des UI-Objekts in der Szene zuständig ist und die Antworten vom bot darstellt:</span><span class="sxs-lookup"><span data-stu-id="2b065-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="2b065-433">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2b065-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="2b065-434">Ziehen Sie im Unity-Editor das Skript " **sceneorganisator** " aus dem Ordner "Scripts" auf die Hauptkamera.</span><span class="sxs-lookup"><span data-stu-id="2b065-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="2b065-435">Die Szene-Organisator-Komponente sollte nun auf dem Hauptkamera Objekt angezeigt werden, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2b065-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="2b065-437">Kapitel 13 – vor dem Aufbau</span><span class="sxs-lookup"><span data-stu-id="2b065-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="2b065-438">Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.</span><span class="sxs-lookup"><span data-stu-id="2b065-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="2b065-439">Bevor Sie vorgehen, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="2b065-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="2b065-440">Alle in [**Kapitel 4**](#chapter-4--set-up-the-unity-project) erwähnten Einstellungen sind richtig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2b065-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="2b065-441">Das Skript **sceneorganisator** ist an das **Hauptkamera** Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="2b065-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="2b065-442">Stellen Sie in der **bot** -Klasse sicher, dass Sie Ihren botsecret- **Schlüssel** in die **botsecret** -Variable eingefügt haben.</span><span class="sxs-lookup"><span data-stu-id="2b065-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="2b065-443">Kapitel 14 – erstellen und Sideload auf die hololens</span><span class="sxs-lookup"><span data-stu-id="2b065-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="2b065-444">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2b065-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="2b065-445">Navigieren Siezu Buildeinstellungen, **Datei > Buildeinstellungen...** .</span><span class="sxs-lookup"><span data-stu-id="2b065-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="2b065-446">Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="2b065-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Entwickeln der APP aus Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="2b065-448">Wenn dies nicht bereits geschehen ist, Tick **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="2b065-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="2b065-449">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-449">Click **Build**.</span></span> <span data-ttu-id="2b065-450">Unity startet ein **Datei-Explorer** -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="2b065-451">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**".</span><span class="sxs-lookup"><span data-stu-id="2b065-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="2b065-452">Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="2b065-453">Unity startet das Projekt in den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="2b065-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="2b065-454">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="2b065-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="2b065-455">Kapitel 15 – bereitstellen in hololens</span><span class="sxs-lookup"><span data-stu-id="2b065-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="2b065-456">So stellen Sie auf hololens bereit:</span><span class="sxs-lookup"><span data-stu-id="2b065-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="2b065-457">Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden.</span><span class="sxs-lookup"><span data-stu-id="2b065-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="2b065-458">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="2b065-458">To do this:</span></span>

    1. <span data-ttu-id="2b065-459">Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.</span><span class="sxs-lookup"><span data-stu-id="2b065-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="2b065-460">Navigieren Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen**</span><span class="sxs-lookup"><span data-stu-id="2b065-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="2b065-461">Notieren Sie sich die **IPv4** -Adresse.</span><span class="sxs-lookup"><span data-stu-id="2b065-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="2b065-462">Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie dann **& Sicherheits > für Entwickler** .</span><span class="sxs-lookup"><span data-stu-id="2b065-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="2b065-463">Legen Sie den Entwicklermodus auf fest.</span><span class="sxs-lookup"><span data-stu-id="2b065-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="2b065-464">Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2b065-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="2b065-465">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="2b065-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="2b065-466">Wählen Sieauf der Projektmappenplattform die Option **x86**, **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="2b065-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="2b065-468">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung**bereitstellen, um die Anwendung auf die hololens quer zuladen.</span><span class="sxs-lookup"><span data-stu-id="2b065-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="2b065-469">Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.</span><span class="sxs-lookup"><span data-stu-id="2b065-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="2b065-470">Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest.</span><span class="sxs-lookup"><span data-stu-id="2b065-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="2b065-471">Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen**die Option *Lösung*bereitstellen auswählen.</span><span class="sxs-lookup"><span data-stu-id="2b065-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="2b065-472">Kapitel 16 – verwenden der Anwendung auf den hololens</span><span class="sxs-lookup"><span data-stu-id="2b065-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="2b065-473">Nachdem Sie die Anwendung gestartet haben, sehen Sie den bot als blaue Kugel vor Ihnen.</span><span class="sxs-lookup"><span data-stu-id="2b065-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="2b065-474">Verwenden Sie die **Tap-Geste** , während Sie die Kugel in der Kugel betrachten, um eine Konversation zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="2b065-475">Warten Sie, bis die Konversation gestartet wird (die Benutzeroberfläche zeigt eine Meldung an, wenn dies geschieht).</span><span class="sxs-lookup"><span data-stu-id="2b065-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="2b065-476">Nachdem Sie die einführende Nachricht vom bot erhalten haben, tippen Sie erneut auf den bot, damit Sie rot wird und mit der Überwachung ihrer Stimme beginnt.</span><span class="sxs-lookup"><span data-stu-id="2b065-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="2b065-477">Wenn Sie nicht mehr sprechen, sendet Ihre Anwendung Ihre Nachricht an den bot, und Sie erhalten umgehend eine Antwort, die in der Benutzeroberfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b065-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="2b065-478">Wiederholen Sie den Vorgang, um weitere Nachrichten an Ihren bot zu senden (Sie müssen jedes Mal tippen, wenn Sie eine Nachricht übertragen möchten).</span><span class="sxs-lookup"><span data-stu-id="2b065-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="2b065-479">Diese Konversation veranschaulicht, wie der bot Informationen (ihren Namen) beibehalten und gleichzeitig bekannte Informationen bereitstellen kann (z. b. die Elemente, die gestockt sind).</span><span class="sxs-lookup"><span data-stu-id="2b065-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="2b065-480">Einige Fragen, um den bot zu Fragen:</span><span class="sxs-lookup"><span data-stu-id="2b065-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="2b065-481">Ihre fertige Web-App-bot-Anwendung (v4)</span><span class="sxs-lookup"><span data-stu-id="2b065-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="2b065-482">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure-Web-App-bot, Microsoft bot Framework V4, nutzt.</span><span class="sxs-lookup"><span data-stu-id="2b065-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Endgültiges Produkt](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2b065-484">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="2b065-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="2b065-485">Übung 1</span><span class="sxs-lookup"><span data-stu-id="2b065-485">Exercise 1</span></span>

<span data-ttu-id="2b065-486">Die Konversations Struktur in dieser Übungseinheit ist sehr einfach.</span><span class="sxs-lookup"><span data-stu-id="2b065-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="2b065-487">Verwenden Sie Microsoft Luis, um den bot-Funktionen für natürliche Sprache zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2b065-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="2b065-488">Übung 2</span><span class="sxs-lookup"><span data-stu-id="2b065-488">Exercise 2</span></span>

<span data-ttu-id="2b065-489">Dieses Beispiel umfasst nicht das Beenden einer Konversation und das Neustarten einer neuen Konversation.</span><span class="sxs-lookup"><span data-stu-id="2b065-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="2b065-490">Um die bot-Funktion abzuschließen, versuchen Sie, den Abschluss der Konversation zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="2b065-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
