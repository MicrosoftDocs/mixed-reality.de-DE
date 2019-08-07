---
title: Mr und Azure 309-Application Insights
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie mit dem Azure-Anwendung Insights-Dienst Analysen bezüglich des Benutzer Verhaltens in einer gemischten Reality-Anwendung sammeln.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Application Insights, hololens, immersive, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694561"
---
>[!NOTE]
><span data-ttu-id="d4472-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="d4472-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d4472-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="d4472-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d4472-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d4472-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="d4472-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d4472-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="d4472-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d4472-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="d4472-110">Mr und Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="d4472-110">MR and Azure 309: Application insights</span></span>

![Endgültiges Produkt-Start](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="d4472-112">In diesem Kurs erfahren Sie, wie Sie Application Insights Funktionen zu einer gemischten Reality-Anwendung hinzufügen, indem Sie die Azure-Anwendung Insights-API verwenden, um Analysen bezüglich des Benutzer Verhaltens zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="d4472-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="d4472-113">Application Insights ist ein Microsoft-Dienst, der es Entwicklern ermöglicht, Analysen von Ihren Anwendungen zu sammeln und Sie über ein einfach zu verwendende Portal zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="d4472-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="d4472-114">Die Analyse kann von der Leistung bis hin zu benutzerdefinierten Informationen erfolgen, die Sie erfassen möchten.</span><span class="sxs-lookup"><span data-stu-id="d4472-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="d4472-115">Weitere Informationen finden Sie auf der [Seite Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="d4472-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="d4472-116">Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="d4472-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="d4472-117">Ermöglicht dem Benutzer das durchschauen und bewegen einer Szene.</span><span class="sxs-lookup"><span data-stu-id="d4472-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="d4472-118">Veranlassen Sie das Senden von Analysen an den *Application Insights-Dienst*, indem Sie die Verwendung von Blick und Nähe zu in-Scene-Objekten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d4472-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="d4472-119">Die APP ruft auch auf dem Dienst auf und ruft in den letzten 24 Stunden Informationen darüber ab, welches Objekt vom Benutzer am meisten kontaktiert wurde.</span><span class="sxs-lookup"><span data-stu-id="d4472-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="d4472-120">Dieses Objekt ändert seine Farbe in grün.</span><span class="sxs-lookup"><span data-stu-id="d4472-120">That object will change its color to green.</span></span>

<span data-ttu-id="d4472-121">In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus dem Application Insights-Dienst in einer Unity-basierten Beispielanwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="d4472-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="d4472-122">Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.</span><span class="sxs-lookup"><span data-stu-id="d4472-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="d4472-123">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="d4472-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d4472-124">Natürlich</span><span class="sxs-lookup"><span data-stu-id="d4472-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d4472-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d4472-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d4472-126"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="d4472-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d4472-127">Mr und Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="d4472-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="d4472-128">✔️</span><span class="sxs-lookup"><span data-stu-id="d4472-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d4472-129">✔️</span><span class="sxs-lookup"><span data-stu-id="d4472-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d4472-130">Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="d4472-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="d4472-131">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="d4472-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="d4472-132">Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.</span><span class="sxs-lookup"><span data-stu-id="d4472-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4472-133">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d4472-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d4472-134">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="d4472-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d4472-135">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018).</span><span class="sxs-lookup"><span data-stu-id="d4472-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="d4472-136">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="d4472-137">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="d4472-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d4472-138">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="d4472-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="d4472-139">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="d4472-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d4472-140">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d4472-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d4472-141">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="d4472-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d4472-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d4472-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="d4472-143">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="d4472-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="d4472-144">Eine Reihe von Kopfhörern mit einem integrierten Mikrofon (wenn das Headset nicht über eine integrierte Mic-und-sprechenden verfügt)</span><span class="sxs-lookup"><span data-stu-id="d4472-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="d4472-145">Internet Zugriff für Azure-Setup und Application Insights Datenabruf</span><span class="sxs-lookup"><span data-stu-id="d4472-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="d4472-146">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="d4472-146">Before you start</span></span>

<span data-ttu-id="d4472-147">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="d4472-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="d4472-148">Beachten Sie, dass die Daten, die *Application Insights* werden, Zeit in Rechnung stellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="d4472-149">Wenn Sie überprüfen möchten, ob der Dienst Ihre Daten empfangen hat, finden Sie in [Kapitel 14](#chapter-14---the-application-insights-service-portal)Weitere Informationen zum Navigieren im Portal.</span><span class="sxs-lookup"><span data-stu-id="d4472-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="d4472-150">Kapitel 1: Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="d4472-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="d4472-151">Um *Application Insights*verwenden zu können, müssen Sie im Azure-Portal einen *Application Insights-Dienst* erstellen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d4472-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="d4472-152">Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.</span><span class="sxs-lookup"><span data-stu-id="d4472-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4472-153">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="d4472-154">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d4472-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="d4472-155">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Application Insights*, und drücken Sie die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="d4472-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4472-156">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="d4472-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="d4472-158">Die neue Seite auf der rechten Seite enthält eine Beschreibung des *Azure-Anwendung Insights* -Dienstanbieter.</span><span class="sxs-lookup"><span data-stu-id="d4472-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="d4472-159">Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="d4472-161">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="d4472-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="d4472-162">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="d4472-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="d4472-163">Wählen Sie als **Anwendungstyp**die Option **Allgemein**aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="d4472-164">Wählen Sie ein entsprechendes **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="d4472-165">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="d4472-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d4472-166">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="d4472-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d4472-167">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="d4472-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="d4472-168">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="d4472-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="d4472-169">Wählen Sie einen **Speicherort**aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="d4472-170">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="d4472-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="d4472-171">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-171">Select **Create**.</span></span>

        ![Azure-Portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="d4472-173">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="d4472-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="d4472-174">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d4472-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="d4472-176">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="d4472-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="d4472-178">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="d4472-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d4472-179">Sie gelangen zu ihrer neuen *Application Insights Dienst* Instanz.</span><span class="sxs-lookup"><span data-stu-id="d4472-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="d4472-181">Diese Webseite offen und leicht zugänglich zu machen, wird hier wieder häufig angezeigt, um die gesammelten Daten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d4472-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d4472-182">Zum Implementieren von Application Insights müssen drei (3) spezifische Werte verwendet werden: **Instrumentierungs Schlüssel**, **Anwendungs-ID**und **API-Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="d4472-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="d4472-183">Unten sehen Sie, wie Sie diese Werte von Ihrem Dienst abrufen.</span><span class="sxs-lookup"><span data-stu-id="d4472-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="d4472-184">Achten Sie darauf, diese Werte auf einer leeren *Notepad* -Seite zu notieren, da Sie Sie bald in Ihrem Code verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="d4472-185">Um den **Instrumentierungs Schlüssel**zu suchen, müssen Sie einen Bildlauf nach unten in der Liste der Dienstfunktionen durchführen und auf **Eigenschaften**klicken. auf der angezeigten Registerkarte wird der **Dienst Schlüssel**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d4472-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="d4472-187">Unter den folgenden **Eigenschaften**finden Sie den **API-Zugriff**, auf den Sie klicken müssen.</span><span class="sxs-lookup"><span data-stu-id="d4472-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="d4472-188">Im Bereich auf der rechten Seite wird die **Anwendungs-ID** Ihrer APP bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d4472-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="d4472-190">Wenn der Bereich **Anwendungs-ID** weiterhin geöffnet ist, klicken Sie auf API- **Schlüssel erstellen**. Dadurch wird der Bereich *API-Schlüssel erstellen* geöffnet.</span><span class="sxs-lookup"><span data-stu-id="d4472-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure-Portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="d4472-192">Geben Sie im jetzt geöffneten Bereich *API-Schlüssel erstellen* eine Beschreibung ein, und klicken Sie auf **die drei Felder**.</span><span class="sxs-lookup"><span data-stu-id="d4472-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="d4472-193">Klicken Sie auf **Schlüssel generieren**.</span><span class="sxs-lookup"><span data-stu-id="d4472-193">Click **Generate Key**.</span></span> <span data-ttu-id="d4472-194">Ihr **API-Schlüssel** wird erstellt und angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d4472-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure-Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="d4472-196">Dies ist der einzige Zeitpunkt, an dem der **Dienst Schlüssel** angezeigt wird. Stellen Sie also sicher, dass Sie jetzt eine Kopie erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="d4472-197">Kapitel 2: Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="d4472-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="d4472-198">Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.</span><span class="sxs-lookup"><span data-stu-id="d4472-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d4472-199">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="d4472-199">Open *Unity* and click **New**.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="d4472-201">Sie müssen nun einen Unity-Projektnamen angeben und **\_\_Azure\_Application Insights**einfügen.</span><span class="sxs-lookup"><span data-stu-id="d4472-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="d4472-202">Stellen Sie sicher, dass die *Vorlage* auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d4472-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="d4472-203">Legen Sie den Speicherort auf einen geeigneten *Speicherort* fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="d4472-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d4472-204">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d4472-204">Then, click **Create project**.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="d4472-206">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d4472-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d4472-207">Wechseln Sie **zu \> Einstellungen bearbeiten** , und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="d4472-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d4472-208">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="d4472-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d4472-209">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="d4472-209">Close the **Preferences** window.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="d4472-211">Navigieren Sie als nächstes **zu \> dateibuildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="d4472-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="d4472-213">Wechseln Sie **zu \> dateibuildeinstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="d4472-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="d4472-214">Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d4472-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="d4472-215">Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.</span><span class="sxs-lookup"><span data-stu-id="d4472-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="d4472-216">Der Buildtyp ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d4472-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="d4472-217">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d4472-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="d4472-218">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d4472-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="d4472-219">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4472-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="d4472-220">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d4472-221">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d4472-221">A save window will appear.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="d4472-223">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und klicken Sie dann auf die Schaltfläche **neuer Ordner** , um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="d4472-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="d4472-225">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname:* Text den Text **applicationinsightsscene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d4472-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="d4472-227">Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="d4472-228">Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.</span><span class="sxs-lookup"><span data-stu-id="d4472-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="d4472-230">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="d4472-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="d4472-231">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="d4472-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d4472-232">**Skript** Erstellung Die **Lauf Zeit Version** sollte experimentell sein **(.NET 4,6-Entsprechung)** , wodurch der Editor neu gestartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="d4472-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="d4472-233">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="d4472-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="d4472-234">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="d4472-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="d4472-236">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="d4472-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="d4472-237">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="d4472-237">**InternetClient**</span></span>     

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="d4472-239">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="d4472-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="d4472-241">Wieder inden Buildeinstellungen ist **Unity C# -Projekte** nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="d4472-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="d4472-242">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="d4472-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="d4472-243">Speichern Sie Ihre Szene und Ihr Projekt (**Datei** > **Speichern/Datei** > **speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="d4472-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="d4472-244">Kapitel 3: Importieren des Unity-Pakets</span><span class="sxs-lookup"><span data-stu-id="d4472-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4472-245">Wenn Sie die *Unity-Setup* Komponenten dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-309. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)herunterladen und es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="d4472-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="d4472-246">Dies enthält auch die DLLs aus dem nächsten Kapitel.</span><span class="sxs-lookup"><span data-stu-id="d4472-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="d4472-247">Fahren Sie nach dem Import aus [**Kapitel 6**](#chapter-6---create-the-applicationinsightstracker-class)fort.</span><span class="sxs-lookup"><span data-stu-id="d4472-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4472-248">Um Application Insights in Unity verwenden zu können, müssen Sie die DLL für diese zusammen mit der newtonsoft-dll importieren.</span><span class="sxs-lookup"><span data-stu-id="d4472-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="d4472-249">Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="d4472-250">Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="d4472-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="d4472-251">Wenn Sie Application Insights in Ihr eigenes Projekt importieren möchten, stellen Sie sicher, dass Sie [das ". unitypackage" heruntergeladen haben, das die](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)Plug-Ins enthält.</span><span class="sxs-lookup"><span data-stu-id="d4472-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="d4472-252">Gehen Sie dann wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="d4472-252">Then, do the following:</span></span>

1.  <span data-ttu-id="d4472-253">Fügen Sie das **. unitypackage** zu Unity hinzu, indem Sie die Menüoption **Assets \> Import \> Package Custom Package** verwenden.</span><span class="sxs-lookup"><span data-stu-id="d4472-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="d4472-254">Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und **einschließlich) Plug** -ins ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="d4472-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="d4472-256">Klicken Sie auf die Schaltfläche **importieren** , um die Elemente Ihrem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d4472-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="d4472-257">Wechseln Sie in der Projektansicht **unter Plug** -in zum Ordner **Insights** , und wählen Sie *nur*die folgenden Plug-ins aus:</span><span class="sxs-lookup"><span data-stu-id="d4472-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="d4472-258">Microsoft. applicationinsights</span><span class="sxs-lookup"><span data-stu-id="d4472-258">Microsoft.ApplicationInsights</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="d4472-260">Wenn dieses *Plug* -in ausgewählt ist, **Stellen Sie sicher**, dass **alle Plattformen** deaktiviert **sind, und**stellen Sie sicher, dass **wsaplayer** **ebenfalls deaktiviert**ist.</span><span class="sxs-lookup"><span data-stu-id="d4472-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="d4472-261">Hierdurch wird lediglich bestätigt, dass die Dateien ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="d4472-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="d4472-263">Wenn Sie die Plug-ins wie diese markieren, werden diese so konfiguriert, dass Sie nur im Unity-Editor verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="d4472-264">Der WSA-Ordner enthält einen anderen Satz von DLLs, die nach dem Exportieren des Projekts aus Unity verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="d4472-265">Im nächsten Schritt müssen Sie den Ordner " **WSA** " im Ordner " **Insights** " öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="d4472-266">Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="d4472-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="d4472-267">Wählen Sie diese Datei aus, und vergewissern Sie sich dann im Inspektor, dass **alle Plattformen** deaktiviert sind. Stellen Sie dann sicher, dass **nur** **wsaplayer** **aktiviert**ist.</span><span class="sxs-lookup"><span data-stu-id="d4472-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="d4472-268">Klicken Sie auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="d4472-268">Click **Apply**.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="d4472-270">Nun müssen Sie die **Schritte 4-6**ausführen, aber für die *newtonsoft* -Plug-ins.</span><span class="sxs-lookup"><span data-stu-id="d4472-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="d4472-271">Sehen Sie sich den folgenden Screenshot an, um zu sehen, wie das Ergebnis aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="d4472-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="d4472-273">Kapitel 4: Einrichten der Kamera-und Benutzer Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="d4472-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="d4472-274">In diesem Kapitel richten Sie die Kamera und die Steuerelemente ein, um dem Benutzer zu ermöglichen, die Szene anzuzeigen und zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="d4472-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="d4472-275">Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, und klicken Sie dann auf**leere** **Erstellen** > .</span><span class="sxs-lookup"><span data-stu-id="d4472-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="d4472-277">Benennen Sie das neue leere gameobject in das über **geordnete**Element um.</span><span class="sxs-lookup"><span data-stu-id="d4472-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="d4472-279">Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, und klicken Sie dann auf **3D-Objekt**und dann auf **Kugel**.</span><span class="sxs-lookup"><span data-stu-id="d4472-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="d4472-280">Benennen Sie die Kugel in den **rechten**Bereich um.</span><span class="sxs-lookup"><span data-stu-id="d4472-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="d4472-281">Legen Sie die **Transformations Skala** der rechten Seite auf **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="d4472-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="d4472-283">Entfernen Sie die **Kugel-Collider** -Komponente von der rechten Seite, indem Sie auf das **Zahnrad** in der *Kugel-Collider* -Komponente klicken, und entfernen Sie dann die **Komponente**.</span><span class="sxs-lookup"><span data-stu-id="d4472-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="d4472-285">Ziehen Sie im Hierarchie Panel die **Hauptkamera** und die **Rechte Seite** auf das über **geordnete Kamera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="d4472-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="d4472-287">Legen Sie die **Transformations Position** der **Hauptkamera** und des **rechten** Objekts auf **0, 0, 0**fest.</span><span class="sxs-lookup"><span data-stu-id="d4472-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-31.png)

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="d4472-290">Kapitel 5: Einrichten der Objekte in der Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="d4472-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="d4472-291">Sie werden nun einige grundlegende Formen für Ihre Szene erstellen, mit denen der Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="d4472-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="d4472-292">Klicken Sie mit der rechten Maustaste in einen leeren Bereich im *Hierarchie Panel*, und wählen Sie dann auf dem **3D-Objekt**die Option **Ebene**aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="d4472-293">Legen Sie die **Position** der Ebene Transformation auf **0,-1, 0**fest.</span><span class="sxs-lookup"><span data-stu-id="d4472-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="d4472-294">Legen Sie für die Ebene **Transform Scale** den Wert **5, 1, 5**fest.</span><span class="sxs-lookup"><span data-stu-id="d4472-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="d4472-296">Erstellen Sie ein grundlegendes Material, das Sie mit dem **Plane** -Objekt verwenden können, damit die anderen Formen leichter zu sehen sind.</span><span class="sxs-lookup"><span data-stu-id="d4472-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="d4472-297">Navigieren Sie zum *Projekt Panel*, klicken Sie mit der rechten Maustaste, klicken Sie dann auf **Erstellen**und dann auf **Ordner**, um einen neuen Ordner zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="d4472-298">Nennen Sie es **Material**.</span><span class="sxs-lookup"><span data-stu-id="d4472-298">Name it **Materials**.</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-34.png) ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="d4472-301">Öffnen Sie den Ordner **Material** , klicken Sie mit der rechten Maustaste auf, klicken Sie auf **Erstellen**und dann auf **Material**, um ein neues Material zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="d4472-302">Nennen Sie es **Blue**.</span><span class="sxs-lookup"><span data-stu-id="d4472-302">Name it **Blue**.</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-36.png) ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="d4472-305">Wenn das neue **blaue** Material ausgewählt ist, schauen Sie sich den *Inspektor*an, und klicken Sie auf das rechteckige Fenster neben **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="d4472-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="d4472-306">Wählen Sie eine blaue Farbe aus (die folgende Abbildung **ist eine hexadezimale Farbe: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="d4472-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="d4472-307">Nachdem Sie ausgewählt haben, klicken Sie auf die Schaltfläche Schließen.</span><span class="sxs-lookup"><span data-stu-id="d4472-307">Click the close button once you have chosen.</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="d4472-309">Ziehen Sie das neue Material aus dem Ordner **Material** in die neu erstellte **Ebene**innerhalb Ihrer Szene (oder legen Sie es auf dem **Ebene** -Objekt in der *Hierarchie*ab).</span><span class="sxs-lookup"><span data-stu-id="d4472-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="d4472-311">Klicken Sie mit der rechten Maustaste auf einen leeren Bereich im *Hierarchie Panel*und dann auf **3D-Objekt, Kapsel**.</span><span class="sxs-lookup"><span data-stu-id="d4472-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="d4472-312">Wenn die **Kapsel** ausgewählt ist, ändern Sie die **Transformations** *Position* in: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="d4472-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="d4472-313">Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Bereich *Hierarchie*, und klicken Sie dann auf **3D-Objekt, Cube**.</span><span class="sxs-lookup"><span data-stu-id="d4472-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="d4472-314">Ändern Sie mit ausgewähltem **Cube** die **Transformations** *Position* in: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="d4472-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="d4472-315">Klicken Sie mit der rechten Maustaste auf einen leeren Bereich im *Hierarchie Panel*und dann auf **3D-Objekt, Kugel**.</span><span class="sxs-lookup"><span data-stu-id="d4472-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="d4472-316">Wenn die **Kugel** ausgewählt ist, ändern Sie die zugehörige **Transformations** *Position* in: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="d4472-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="d4472-318">Bei diesen *Positions* Werten handelt es sich um *Vorschläge*.</span><span class="sxs-lookup"><span data-stu-id="d4472-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="d4472-319">Sie können die Positionen der Objekte auf beliebige Weise festlegen, obwohl es für den Benutzer der Anwendung einfacher ist, wenn die Objekt Abstände nicht zu weit von der Kamera stammen.</span><span class="sxs-lookup"><span data-stu-id="d4472-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="d4472-320">Wenn die Anwendung ausgeführt wird, muss Sie in der Lage sein, die Objekte innerhalb der Szene zu identifizieren, um dies zu erreichen, müssen Sie gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="d4472-321">Wählen Sie eines der Objekte aus, und klicken Sie im *Inspektor* -Panel auf **Tag hinzufügen...** . Dadurch wird der *Inspektor* mit dem Bereich **Tags & Ebenen** ausgetauscht.</span><span class="sxs-lookup"><span data-stu-id="d4472-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="d4472-322">![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-41.png)![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="d4472-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="d4472-323">Klicken Sie auf das Symbol **+ (plus)** , und geben Sie dann den Tagnamen als **objectinscene**ein.</span><span class="sxs-lookup"><span data-stu-id="d4472-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="d4472-325">Wenn Sie einen anderen Namen für das Tag verwenden, müssen Sie sicherstellen, dass diese Änderung auch die Skripts " *datafromanalytics*", " *objecttrigger*" und " *Gaze*" erstellt, damit Ihre Objekte in Ihrer Szene gefunden und erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="d4472-326">Nachdem Sie das Tag erstellt haben, müssen Sie es auf alle drei Objekte anwenden.</span><span class="sxs-lookup"><span data-stu-id="d4472-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="d4472-327">Halten Sie in der *Hierarchie*die **UMSCHALT** Taste gedrückt, und klicken Sie dann auf die **Kapsel**, den **Cube**und die **Kugel**, und klicken Sie dann im *Inspektor*auf das Dropdown Menü neben **Tag**und dann auf *objectinscene* . Tag, das Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="d4472-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="d4472-328">![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-44.png)![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="d4472-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="d4472-329">Kapitel 6: Erstellen der applicationinsightstracker-Klasse</span><span class="sxs-lookup"><span data-stu-id="d4472-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="d4472-330">Das erste Skript, das Sie erstellen müssen, ist **applicationinsightstracker**, das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="d4472-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="d4472-331">Erstellen von Ereignissen auf der Grundlage von Benutzerinteraktionen, um Azure-Anwendung Einblicke zu senden.</span><span class="sxs-lookup"><span data-stu-id="d4472-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="d4472-332">Erstellen geeigneter Ereignis Namen, abhängig von der Benutzerinteraktion.</span><span class="sxs-lookup"><span data-stu-id="d4472-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="d4472-333">Ereignisse werden an die Application Insights-Dienst Instanz übermittelt.</span><span class="sxs-lookup"><span data-stu-id="d4472-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="d4472-334">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="d4472-334">To create this class:</span></span>

1.  <span data-ttu-id="d4472-335">Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und **Erstellen** > Sie dann den**Ordner**.</span><span class="sxs-lookup"><span data-stu-id="d4472-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="d4472-336">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="d4472-336">Name the folder **Scripts**.</span></span>

    ![Erstellen der applicationinsightstracker-Klasse](images/AzureLabs-Lab309-46.png)  ![Erstellen der applicationinsightstracker-Klasse](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="d4472-339">Doppelklicken Sie nach dem Erstellen des **Skripts** auf den Ordner, um zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="d4472-340">Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="d4472-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="d4472-341">Nennen Sie das Skript **applicationinsightstracker**.</span><span class="sxs-lookup"><span data-stu-id="d4472-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="d4472-342">Doppelklicken Sie auf das neue **applicationinsightstracker** -Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="d4472-343">Aktualisieren Sie die Namespaces oben im Skript so, dass Sie wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="d4472-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="d4472-344">Fügen Sie in der-Klasse die folgenden Variablen ein:</span><span class="sxs-lookup"><span data-stu-id="d4472-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="d4472-345">Legen Sie die Werte **instrumentationkey, ApplicationId und API_Key** entsprechend fest, indem Sie die *Dienst Schlüssel* aus dem Azure-Portal verwenden, wie in [Kapitel 1](#chapter-1---the-azure-portal), Schritt 9 weiter oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d4472-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="d4472-346">Fügen Sie dann die Methoden **Start ()** und **Awa()** hinzu, die aufgerufen werden, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="d4472-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="d4472-347">Fügen Sie die Methoden hinzu, die für das Senden der von Ihrer Anwendung registrierten Ereignisse und Metriken verantwortlich sind:</span><span class="sxs-lookup"><span data-stu-id="d4472-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="d4472-348">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d4472-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="d4472-349">Kapitel 7: Erstellen des Blick Schrift Skripts</span><span class="sxs-lookup"><span data-stu-id="d4472-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="d4472-350">Das nächste Skript, das erstellt werden soll, ist das **Gaze** -Skript.</span><span class="sxs-lookup"><span data-stu-id="d4472-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="d4472-351">Dieses Skript ist dafür verantwortlich, ein *raycast* zu erstellen, das von der *Hauptkamera*projiziert wird, um zu erkennen, welches Objekt der Benutzer untersucht.</span><span class="sxs-lookup"><span data-stu-id="d4472-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="d4472-352">In diesem Fall muss der *raycast* ermitteln, ob der Benutzer ein Objekt mit dem Objekt " **objectinscene** " prüft, und dann zählen, wie lange der *Benutzer an diesem* Objekt mitnimmt.</span><span class="sxs-lookup"><span data-stu-id="d4472-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="d4472-353">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d4472-354">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="d4472-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d4472-355">Benennen Sie das **Skript mit**dem Namen.</span><span class="sxs-lookup"><span data-stu-id="d4472-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="d4472-356">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d4472-357">Ersetzen Sie den vorhandenen Code durch folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="d4472-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="d4472-358">Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="d4472-359">Fügen Sie in der " **Blick** "-Klasse den folgenden Code in der **Update ()** -Methode hinzu, um ein *raycast* zu projizieren und den zieltreffer zu erkennen:</span><span class="sxs-lookup"><span data-stu-id="d4472-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="d4472-360">Fügen Sie die **resetfocusedobject ()** -Methode hinzu, um Daten an **Application Insights** zu senden, wenn der Benutzer ein Objekt betrachtet hat.</span><span class="sxs-lookup"><span data-stu-id="d4472-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="d4472-361">Sie haben **nun das Skript** Skript abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="d4472-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="d4472-362">Speichern Sie die Änderungen in *Visual Studio* , bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d4472-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="d4472-363">Kapitel 8: Erstellen der objecttrigger-Klasse</span><span class="sxs-lookup"><span data-stu-id="d4472-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="d4472-364">Das nächste Skript, das Sie erstellen müssen, ist **objecttrigger**, das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="d4472-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="d4472-365">Hinzufügen von Komponenten, die für die Kollision auf der Hauptkamera erforderlich sind</span><span class="sxs-lookup"><span data-stu-id="d4472-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="d4472-366">Erkennen, ob sich die Kamera in der Nähe eines Objekts befindet, das als **objectinscene**gekennzeichnet ist</span><span class="sxs-lookup"><span data-stu-id="d4472-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="d4472-367">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="d4472-367">To create the script:</span></span>

1.  <span data-ttu-id="d4472-368">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d4472-369">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="d4472-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d4472-370">Benennen Sie das Skript **objecttrigger**.</span><span class="sxs-lookup"><span data-stu-id="d4472-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="d4472-371">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="d4472-372">Ersetzen Sie den vorhandenen Code durch folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="d4472-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="d4472-373">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d4472-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="d4472-374">Kapitel 9: Erstellen der datafromanalytics-Klasse</span><span class="sxs-lookup"><span data-stu-id="d4472-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="d4472-375">Sie müssen nun das **datafromanalytics** -Skript erstellen, das für Folgendes zuständig ist:</span><span class="sxs-lookup"><span data-stu-id="d4472-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="d4472-376">Das Abrufen von Analysedaten über das Objekt, das von der Kamera am meisten angegangen wurde.</span><span class="sxs-lookup"><span data-stu-id="d4472-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="d4472-377">Mithilfe der *Dienst Schlüssel*, die die Kommunikation mit ihrer Azure-Anwendung Insights-Dienst Instanz ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="d4472-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="d4472-378">Sortieren der Objekte in der Szene, je nachdem, welche die höchste Ereignis Anzahl aufweist.</span><span class="sxs-lookup"><span data-stu-id="d4472-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="d4472-379">Ändern der Material Farbe des am häufigsten angenäherten Objekts in *grün*.</span><span class="sxs-lookup"><span data-stu-id="d4472-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="d4472-380">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="d4472-380">To create the script:</span></span>

1.  <span data-ttu-id="d4472-381">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d4472-382">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="d4472-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d4472-383">Benennen Sie das Skript " **datafromanalytics**".</span><span class="sxs-lookup"><span data-stu-id="d4472-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="d4472-384">Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d4472-385">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="d4472-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="d4472-386">Fügen Sie im Skript Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d4472-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="d4472-387">Fügen Sie innerhalb der **datafromanalytics** -Klasse direkt nach der **Start ()** -Methode die folgende Methode namens **fetchanalytics ()** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4472-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="d4472-388">Diese Methode ist für das Auffüllen der Liste der Schlüssel-Wert-Paare mit einem *gameobject-Objekt* und einer Platzhalter Ereignis Anzahl verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="d4472-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="d4472-389">Anschließend wird die " **GetWebRequest ()** "-Coroutine initialisiert.</span><span class="sxs-lookup"><span data-stu-id="d4472-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="d4472-390">Die Abfrage Struktur des aufzurufenden *Application Insights* kann in dieser Methode auch als Endpunkt der *Abfrage-URL* gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="d4472-391">Fügen Sie direkt unterhalb der **fetchanalytics ()** -Methode eine Methode namens **GetWebRequest ()** hinzu, die einen *IEnumerator*zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d4472-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="d4472-392">Diese Methode ist dafür verantwortlich, wie oft ein Ereignis, das einem bestimmten *gameobject*entspricht, in *Application Insights*aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="d4472-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="d4472-393">Wenn alle gesendeten Abfragen zurückgegeben wurden, wird die **determinewinner ()** -Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d4472-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="d4472-394">Die nächste Methode ist " **determinewinner ()** ", die die Liste der *gameobject* -und *int* -Paare entsprechend der höchsten Ereignis Anzahl sortiert.</span><span class="sxs-lookup"><span data-stu-id="d4472-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="d4472-395">Anschließend wird die Material Farbe dieses *gameobject* in *grün* geändert (als Feedback für die Anwendung mit der höchsten Anzahl).</span><span class="sxs-lookup"><span data-stu-id="d4472-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="d4472-396">Dadurch wird eine Meldung mit den Analyseergebnissen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d4472-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="d4472-397">Fügen Sie die Klassenstruktur hinzu, die zum Deserialisieren des JSON-Objekts verwendet wird, das von *Application Insights*empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="d4472-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="d4472-398">Fügen Sie diese Klassen ganz unten in der **datafromanalytics** -Klassendatei **außerhalb** der Klassendefinition hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4472-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="d4472-399">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d4472-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="d4472-400">Kapitel 10: Erstellen der Bewegungs Klasse</span><span class="sxs-lookup"><span data-stu-id="d4472-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="d4472-401">Das **Verschiebungs Skript ist** das nächste Skript, das Sie erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="d4472-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="d4472-402">Er ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="d4472-402">It is responsible for:</span></span>

- <span data-ttu-id="d4472-403">Verschieben der Hauptkamera entsprechend der Richtung, in der die Kamera aussieht.</span><span class="sxs-lookup"><span data-stu-id="d4472-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="d4472-404">Hinzufügen aller anderen Skripts zu Scene-Objekten.</span><span class="sxs-lookup"><span data-stu-id="d4472-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="d4472-405">So erstellen Sie das Skript:</span><span class="sxs-lookup"><span data-stu-id="d4472-405">To create the script:</span></span>

1.  <span data-ttu-id="d4472-406">Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d4472-407">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  .</span><span class="sxs-lookup"><span data-stu-id="d4472-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d4472-408">Benennen Sie das **Skript.**</span><span class="sxs-lookup"><span data-stu-id="d4472-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="d4472-409">Doppelklicken Sie auf das Skript, um es in *Visual Studio*zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d4472-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="d4472-410">Ersetzen Sie den vorhandenen Code durch folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="d4472-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="d4472-411">Fügen Sie innerhalb der **Movement** -Klasse *unter* der leeren **Update ()** -Methode die folgenden Methoden ein, die dem Benutzer die Verwendung des Hand Controllers zum Verschieben im virtuellen Bereich ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="d4472-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="d4472-412">Fügen Sie schließlich den Methoden aufrufin der **Update ()** -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4472-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="d4472-413">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d4472-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="d4472-414">Kapitel 11: Einrichten der Skripts Verweise</span><span class="sxs-lookup"><span data-stu-id="d4472-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="d4472-415">In diesem Kapitel müssen Sie das **Bewegungs** Skript auf der über **geordneten Kamera** platzieren und dessen Verweis Ziele festlegen.</span><span class="sxs-lookup"><span data-stu-id="d4472-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="d4472-416">Dieses Skript behandelt dann das Platzieren der anderen Skripts, wenn Sie es benötigen.</span><span class="sxs-lookup"><span data-stu-id="d4472-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="d4472-417">Ziehen Sie im Ordner "Skripts" im *Projekt Panel*das **Bewegungs** Skript in das über **geordnete Kamera** Objekt, das sich im Bereich *Hierarchie*befindet.</span><span class="sxs-lookup"><span data-stu-id="d4472-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Einrichten der Skripts Verweise in der Unity-Szene](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="d4472-419">Klicken Sie auf die über **geordnete Kamera**.</span><span class="sxs-lookup"><span data-stu-id="d4472-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="d4472-420">Ziehen Sie im Bereich *Hierarchie*das **Rechte** Objekt aus dem Bereich *Hierarchie* in das Verweis Ziel, **Controller**, im *Inspektor-Panel*.</span><span class="sxs-lookup"><span data-stu-id="d4472-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="d4472-421">Legen Sie die **Benutzer Geschwindigkeit** auf **5**fest, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d4472-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Einrichten der Skripts Verweise in der Unity-Szene](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="d4472-423">Kapitel 12: Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="d4472-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="d4472-424">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4472-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="d4472-425">Navigieren Siezu den Buildeinstellungen (dateibuildeinstellungen > ).</span><span class="sxs-lookup"><span data-stu-id="d4472-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="d4472-426">Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="d4472-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="d4472-428">Ein **Datei-Explorer** -Fenster wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort für den Build zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d4472-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="d4472-429">Erstellen Sie einen neuen Ordner (indem Sie in der oberen linken Ecke auf **neuer Ordner** klicken), und nennen Sie ihn " **BUILDS**".</span><span class="sxs-lookup"><span data-stu-id="d4472-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="d4472-431">Öffnen Sie den Ordner neue **BUILDS** , und erstellen Sie einen weiteren Ordner (mehr als einen **neuen Ordner** ), und **\_benennen\_Sie\_ihn mit Azure Application Insights**.</span><span class="sxs-lookup"><span data-stu-id="d4472-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="d4472-433">Klicken Sie bei ausgewähltem Ordner " **\_\_AzureApplicationInsights" auf Ordner auswählen.\_**</span><span class="sxs-lookup"><span data-stu-id="d4472-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="d4472-434">Es dauert eine Minute, bis das Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="d4472-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="d4472-435">Im folgenden *Build*wird der **Datei-Explorer** angezeigt, in dem der Speicherort des neuen Projekts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d4472-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a><span data-ttu-id="d4472-436">Kapitel 13: Bereitstellen der MR_Azure_Application_Insights-App auf Ihrem Computer</span><span class="sxs-lookup"><span data-stu-id="d4472-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="d4472-437">So stellen Sie **die\_Azure\_Application\_Insights** -App auf Ihrem lokalen Computer bereit:</span><span class="sxs-lookup"><span data-stu-id="d4472-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="d4472-438">Öffnen Sie die Projektmappendatei Ihrer **\_Azure\_\_Application Insights** -app in **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d4472-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="d4472-439">Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="d4472-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="d4472-440">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="d4472-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="d4472-442">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="d4472-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="d4472-443">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="d4472-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="d4472-444">Starten Sie die Mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="d4472-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="d4472-445">Bewegen Sie sich um die Szene, sehen Sie sich die Objekte an, und sehen Sie sich diese an, wenn der *Azure Insight-Dienst* genügend Ereignisdaten gesammelt hat, legt er das Objekt fest, das am höchsten grün ist.</span><span class="sxs-lookup"><span data-stu-id="d4472-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="d4472-446">Die durchschnittliche Wartezeit für die vom Dienst zu erfassenden *Ereignisse und Metriken* dauert etwa 15 Minuten, in manchen Fällen kann es jedoch bis zu einer Stunde dauern.</span><span class="sxs-lookup"><span data-stu-id="d4472-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="d4472-447">Kapitel 14: das Application Insights Service-Portal</span><span class="sxs-lookup"><span data-stu-id="d4472-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="d4472-448">Nachdem Sie die Szene gewechselt und mit mehreren Objekten zusammengeführt haben, können Sie die im *Application Insights Service* -Portal gesammelten Daten sehen.</span><span class="sxs-lookup"><span data-stu-id="d4472-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="d4472-449">Wechseln Sie zurück zu Ihrem Application Insights Service-Portal.</span><span class="sxs-lookup"><span data-stu-id="d4472-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="d4472-450">Klicken Sie auf *Metrik-Explorer*.</span><span class="sxs-lookup"><span data-stu-id="d4472-450">Click on *Metrics Explorer*.</span></span>

    ![Überprüfen der gesammelten Daten](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="d4472-452">Es wird auf einer Registerkarte geöffnet, die das Diagramm enthält, das die *Ereignisse und Metriken* für Ihre Anwendung darstellt.</span><span class="sxs-lookup"><span data-stu-id="d4472-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="d4472-453">Wie bereits erwähnt, kann es einige Zeit dauern (bis zu 1 Stunde), bis die Daten im Diagramm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d4472-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Überprüfen der gesammelten Daten](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="d4472-455">Klicken Sie auf die *Ereignis Leiste* in der *Gesamtanzahl der Ereignisse* nach Anwendungs Version, um eine detaillierte Aufschlüsselung der Ereignisse mit ihren Namen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d4472-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Überprüfen der gesammelten Daten](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="d4472-457">Ihre Application Insights Service-Anwendung wurde beendet.</span><span class="sxs-lookup"><span data-stu-id="d4472-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="d4472-458">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Application Insights-Dienst nutzt, um die Aktivität des Benutzers in Ihrer APP zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="d4472-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d4472-460">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="d4472-460">Bonus Exercises</span></span>

<span data-ttu-id="d4472-461">**Übung 1**</span><span class="sxs-lookup"><span data-stu-id="d4472-461">**Exercise 1**</span></span>

<span data-ttu-id="d4472-462">Versuchen Sie, die objectinscene-Objekte zu erstellen, anstatt Sie manuell zu erstellen, und legen Sie Ihre Koordinaten auf der Ebene innerhalb Ihrer Skripts fest.</span><span class="sxs-lookup"><span data-stu-id="d4472-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="d4472-463">Auf diese Weise könnten Sie Azure das am häufigsten verwendete Objekt (aus Blick auf das Ergebnis oder die Near-Ergebnisse) Fragen und ein *zusätzliches* von diesen Objekten erzeugen.</span><span class="sxs-lookup"><span data-stu-id="d4472-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="d4472-464">**Übung 2**</span><span class="sxs-lookup"><span data-stu-id="d4472-464">**Exercise 2**</span></span>

<span data-ttu-id="d4472-465">Sortieren Sie Ihre Application Insights Ergebnisse nach Zeit, damit Sie die relevantesten Daten erhalten, und implementieren Sie diese zeitsensiblen Daten in der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="d4472-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

